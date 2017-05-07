---
title: "使用 Intune 配置和管理 PKCS 证书"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何配置基础结构，然后使用 Intune 创建和分配 PKCS 证书。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e189ebd1-6ca1-4365-9d5d-fab313b7e979
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: a981b0253f56d66292ce77639faf4beba8832a9e
ms.openlocfilehash: 0c378fe6ed26bafb5a78daf36b9326771fdd287b
ms.lasthandoff: 04/19/2017



---
# <a name="configure-your-microsoft-intune-certificate-infrastructure-for-pkcs"></a>为 PKCS 配置 Microsoft Intune 证书基础结构
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

本主题说明如何配置基础结构，然后使用 Intune 创建和分配 PKCS 证书配置文件。

若要在组织中执行任何基于证书的身份验证，你需要企业证书颁发机构。

若要使用 PKCS 证书配置文件，除了企业证书颁发机构，还需要：

-   可以与证书颁发机构进行通信的计算机，或可以使用证书颁发机构计算机本身。

-  Intune 证书连接器，它在可以与证书颁发机构进行通信的计算机上运行。

## <a name="important-terms"></a>重要术语


-    **Active Directory 域**：本部分列出的所有服务器（Web 应用程序代理服务器除外）必须加入你的 Active Directory 域。

-  **证书颁发机构**：在 Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。 有关如何设置证书颁发机构的说明，请参阅 [安装证书颁发机构](http://technet.microsoft.com/library/jj125375.aspx)。
    如 CA 运行的是 Windows Server 2008 R2，则必须 [安装修补程序 KB2483564](http://support.microsoft.com/kb/2483564/)。

-  **可以与证书颁发机构进行通信的计算机**：或者，使用证书颁发机构计算机本身。
-  **Microsoft Intune 证书连接器**：从 Azure 门户，下载**证书连接器**安装程序 (**ndesconnectorssetup.exe**)。 随后可以在想要安装证书连接器的计算机上运行 **ndesconnectorssetup.exe** 。 对于 .PKCS 证书配置文件，请在与证书颁发机构进行通信的计算机上安装证书连接器。
-  **Web 应用程序代理服务器**（可选）：你可以使用运行 Windows Server 2012 R2 或更高版本的服务器作为 Web 应用程序代理 (WAP) 服务器。 该配置：
    -  允许设备使用 Internet 连接接收证书。
    -  是设备通过 Internet 连接接收和续订证书时的安全建议。

 > [!NOTE]           
> -    承载 WAP 的服务器 [必须安装此更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) 以支持网络设备注册服务 (NDES) 所使用的长 URL。 该更新包括在 [2014 年 12 月的更新汇总中](http://support.microsoft.com/kb/3013769)，或单独更新自 [KB3011135](http://support.microsoft.com/kb/3011135)。
>-  此外，托管 WAP 的服务器必须具有与要向外部客户端发布的名称相匹配的 SSL 证书，并且信任 NDES 服务器上使用的 SSL 证书。 这些证书使 WAP 服务器可以终止来自客户端的 SSL 连接，并创建至 NDES 服务器的新 SSL 连接。
    有关 WAP 证书的信息，请参阅[计划使用 Web 应用程序代理发布应用程序](https://technet.microsoft.com/library/dn383650.aspx)的“计划证书”部分。 有关 WAP 服务器的一般信息，请参阅 [Working with Web Application Proxy](http://technet.microsoft.com/library/dn584113.aspx)（使用 Web 应用程序代理）。|


## <a name="certificates-and-templates"></a>证书和模板

|对象|详细信息|
|----------|-----------|
|**证书模板**|在发证 CA 上配置此模板。|
|**受信任的根 CA 证书**|你可以从发证 CA 或信任该发证 CA 的任何设备中将其导出为 **.cer** 文件，并通过使用受信任的 CA 证书配置文件将其部署至设备。<br /><br />你可以在每个操作系统平台上使用一个受信任的根 CA 证书，并将其与你创建的每个受信任的根证书配置文件相关联。<br /><br />你可以在需要时使用其它受信任的根 CA 证书。 例如，你可以这样做来信任为 Wi-Fi 访问点的服务器身份验证证书签名的 CA。|


## <a name="configure-your-infrastructure"></a>配置你的基础结构
在配置证书配置文件前，必须完成以下步骤。 完成这些步骤需要 Windows Server 2012 R2 和 Active Directory 证书服务 (ADCS) 方面的知识：

- **步骤 1** - 配置证书颁发机构上的证书模板。
- **步骤 2** - 启用、安装和配置 Intune 证书连接器。

## <a name="step-1---configure-certificate-templates-on-the-certification-authority"></a>步骤 1 - 配置证书颁发机构上的证书模板

### <a name="to-configure-the-certification-authority"></a>配置证书颁发机构

1.  对于发证 CA，使用证书模板管理单元创建新的自定义模板，或复制并编辑现有模板（与用户模板相似）以与 PKCS 配合使用。

    该模板必须包括下列操作：

    -   为模板指定一个友好的 **“模板显示名称”** 。

    -   在 **“使用者名称”** 选项卡上，选择 **“在请求中提供”**。 （由用于 NDES 的 Intune 策略模块强制实施安全性）。

    -   在 **“扩展”** 选项卡上，确保 **“应用程序策略描述”** 包括了 **“客户端身份验证”**。

        > [!IMPORTANT]
        > 对于 iOS 和 macOS 证书模板，在“**扩展**”选项卡上编辑“**密钥用法**”，并确保未选择“**数字签名为原件的证明**”。

2.  在模板的 **“常规”** 选项卡上查看 **“有效期”** 。 默认情况下，Intune 使用在模板中配置的值。 但是，你可以选择配置 CA 以允许请求者指定不同的值，随后你也能够在 Intune 管理员控制台设置该值。 如果你想要一直使用模板中的值，跳过该步骤的其余部分即可。

    > [!IMPORTANT]
    > 无论你所做出的其他配置是什么，iOS 和 macOS 都始终使用模板中设置的值。

    若要配置 CA 以允许请求者指定有效期，请在 CA 上运行以下命令：

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b。  **net stop certsvc**

    c.  **net start certsvc**

3.  在发证 CA 上，使用证书颁发机构管理单元发布证书模板。

    a.  选择“证书模板”节点，单击“操作”-&gt;“新建”&gt;“要颁发的证书模板”，然后选择步骤 2 中创建的模板。

    b。  通过查看 **“证书模板”** 文件夹下已发布的模板来对它进行验证。

4.  在 CA 计算机上，确保托管 Intune 证书连接器的计算机具有注册权限，以便它可以访问在创建 PKCS 证书配置文件时使用的模板。 在 CA 计算机属性的“安全性”  选项卡上设置该权限。

## <a name="step-2---enable-install-and-configure-the-intune-certificate-connector"></a>步骤 2 - 启用、安装和配置 Intune 证书连接器
在本步骤中，你将要：

- 启用对证书连接器的支持
- 下载、安装和配置证书连接器。

### <a name="to-enable-support-for-the-certificate-connector"></a>启用对证书连接器的支持

1.  登录到 Azure 门户中。
2.  选择“更多服务” > “其他” > “Intune”。
3.  在“Intune”边栏选项卡上，选择“配置设备”。
2.  在“设备配置”边栏选项卡上，选择“设置” > “证书颁发机构”。
2.  在“步骤 1”中，选择“启用”。

### <a name="to-download-install-and-configure-the-certificate-connector"></a>下载、安装和配置证书连接器

1.  在“配置设备”边栏选项卡上，选择“设置” > “证书颁发机构”。
2.  选择“下载证书连接器”。
2.  下载完成之后，运行下载的安装程序 (**ndesconnectorssetup.exe**)。
  在能够与证书颁发机构连接的计算机上运行安装程序。 选择“PKCS (PFX) 分发”选项，然后选择“安装”。 安装完成后，如同[如何配置证书配置文件](how-to-configure-certificates.md)中所述，继续创建证书配置文件。

3.  提示输入证书连接器的客户端证书时，选取“选择”，然后选择已安装的**客户端身份验证**证书。

    选择客户端身份验证证书后，你将返回到“Microsoft Intune 证书连接器的客户端证书”  处。 尽管你选择的证书不会显示，但可以选择“**下一步**”以查看该证书的属性。 然后依次选择“**下一步**”和“**安装**”。

4.  向导完成后，关闭向导前，单击“启动证书连接器 UI” 。

    > [!TIP]
    > 如果在启动证书连接器 UI 前关闭了向导，你可以通过运行以下命令重新打开它：
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  在“证书连接器”  UI 中：

    a. 选择“**登录**”并输入你的 Intune 服务管理员凭据或具有全局管理权限的租户管理员的凭据。

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b。 选择“**高级**”选项卡，然后提供具有在证书颁发机构“**颁发和管理证书**”的权限的帐户凭据。

    c. 选择“**应用**”。

    你现在可以关闭证书连接器 UI。

6.  打开命令提示符并键入 **services.msc**。 然后按 **Enter** 键，右键单击“**Intune 连接器服务**”后选择“**重新启动**”。

若要验证服务是否正在运行，打开浏览器然后输入以下 URL 将返回 **“403”** 错误：

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**


### <a name="how-to-create-a-pkcs-certificate-profile"></a>如何创建 PKCS 证书配置文件

在 Azure 门户中，选择“配置设备”工作负荷。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在“配置文件”边栏选项卡上，单击“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入 PKCS 证书配置文件的“名称”和“说明”。
5. 从“平台”下拉列表的以下项中，为此 PKCS 证书选择设备平台：
    - **Android**
    - **Android for Work**
    - **iOS**
    - **Windows 10 及更高版本**
6. 从“配置文件”类型下拉列表中，选择“PKCS 证书”。
7. 在“PKCS 证书”边栏选项卡上，配置下列设置：
    - **续订阈值(%)** - 指定设备请求证书续订之前剩余的证书有效期限的百分比。
    - **证书有效期** - 如果对发证 CA 运行允许自定义有效期的 **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** 命令，则可以指定证书过期之前剩余的时间量。<br>你可以指定比指定证书模板中的有效期小的值，但不能指定较大的值。 例如，证书模板中的证书有效期为 2 年，则你可以指定值 1 年，但不能指定值 5 年。 该值还必须小于发证 CA 证书的剩余有效期。
    - **密钥存储提供程序(KSP)** (Windows 10) - 指定将存储证书密钥的位置。 可以选择下列值之一：
        - **如果存在受信任的平台模块(TPM) KSP 则注册到它；否则注册到软件 KSP**
        - **注册到受信任的平台模块(TPM) KSP，否则失败**
        - **注册到 Passport，否则失败(Windows 10 及更高版本)**
        - **注册到软件 KSP**
    - **证书颁发机构** - 在 Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。 有关如何设置证书颁发机构的说明，请参阅 [安装证书颁发机构](http://technet.microsoft.com/library/jj125375.aspx)。 如 CA 运行的是 Windows Server 2008 R2，则必须 [安装修补程序 KB2483564](http://support.microsoft.com/kb/2483564/)。
    - **证书颁发机构名称** - 输入你的证书颁发机构的名称。
    - **证书模板名称** - 输入网络设备注册服务配置为使用并且已添加到颁发 CA 的证书模板的名称。
    确保该名称与运行网络设备注册服务的服务器的注册表中所列证书模板名称之一完全匹配。 确保指定证书模板名称，而不是证书模板显示名称。 
    若要查找证书模板的名称，请浏览到以下项：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP。 你将看到作为 **EncryptionTemplate**、 **GeneralPurposeTemplate**和 **SignatureTemplate**的值而列出的证书模板。 默认情况下，所有三个证书模板的值为“IPSECIntermediateOffline”，映射为模板显示名称“IPSec (脱机请求)”。 
    - “使用者名称格式” - 从列表中，选择 Intune 如何自动创建证书请求中的使用者名称。 如果证书用于用户，还可包含使用者名称中的用户电子邮件地址。 选择：
        - **不配置**
        - **公用名**
        - **包括电子邮件的公用名**
        - **公用名为电子邮件**
    - “使用者可选名称” - 指定 Intune 如何在证书请求中为使用者可选名称 (SAN) 自动创建值。 例如，你选择了用户证书类型，则可以在使用者可选名称中包括用户主体名称 (UPN)。 如果将使用客户端证书向网络策略服务器进行验证，则必须将使用者可选名称设置为 UPN。
    - **扩展的密钥使用情况** (Android) - 选择“添加”为证书的预期目的添加值。 大多数情况下，证书将需要“客户端身份验证”  以便用户或设备能够向服务器进行验证。 但，你可以根据需要添加任何其他密钥用法。 
    - **根证书** (Android) - 选择之前配置并分配到用户或设备的根 CA 证书配置文件。 此 CA 证书必须是将颁发在此证书配置文件中配置的证书的 CA 的根证书。 这是你之前创建的受信任的证书配置文件。
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。

## <a name="how-to-assign-the-certificate-profile"></a>如何分配证书配置文件

将证书配置文件分配给组之前，考虑以下事项：

- 将证书配置文件分配给组时，将在设备上安装受信任的 CA 证书配置文件的证书文件。 设备使用 PKCS 证书配置文件来创建设备需要的证书。
- 证书配置文件仅安装在运行你创建配置文件时使用的平台的设备上。
- 你可以对用户集或对设备集分配证书配置文件。
- 若要在设备注册后将证书快速发布到设备，请将证书配置文件分配到用户组（而不是部署到设备组）。 如果分配到设备组，则需要在设备接收策略前进行完整的设备注册。
- 尽管单独分配每个配置文件，但仍需分配受信任的根 CA 和 PKCS 配置文件。 否则，PKCS 证书策略将失败。

有关如何分配配置文件的信息，请参阅[如何分配设备配置文件](how-to-assign-device-profiles.md)。

