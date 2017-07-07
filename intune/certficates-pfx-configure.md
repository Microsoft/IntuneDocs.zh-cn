---
title: "使用 Intune 配置和管理 PKCS 证书"
titleSuffix: Intune on Azure
description: "了解如何配置基础结构，然后使用 Intune 创建并分配 PKCS 证书。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e189ebd1-6ca1-4365-9d5d-fab313b7e979
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 305a4d79aa81bd599369e72bc0cb307fdf452643
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>使用 Intune 配置和管理 PKCS 证书
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题介绍了如何配置基础结构，然后使用 Intune 创建并分配 PKCS 证书配置文件。

必须有企业证书颁发机构，才能在组织中实施任何基于证书的身份验证。

若要使用 PKCS 证书配置文件，除了要有企业证书颁发机构外，还需要有：

-   可以与证书颁发机构进行通信的计算机，或可以使用证书颁发机构计算机本身。

-  Intune 证书连接器，它在可以与证书颁发机构进行通信的计算机上运行。

## <a name="important-terms"></a>重要术语


-    **Active Directory 域**：此部分中列出的所有服务器（Web 应用程序代理服务器除外）都必须加入 Active Directory 域。

-  **证书颁发机构**：Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。 有关如何设置证书颁发机构的说明，请参阅[安装证书颁发机构](http://technet.microsoft.com/library/jj125375.aspx)。
    如果 CA 是在 Windows Server 2008 R2 上运行，必须[安装 KB2483564 中的修补程序](http://support.microsoft.com/kb/2483564/)。

-  **可以与证书颁发机构进行通信的计算机**：也可以使用证书颁发机构计算机本身。
-  **Microsoft Intune 证书连接器**：从 Azure 门户中下载“证书连接器”安装程序 (**ndesconnectorssetup.exe**)。 然后，可以在要安装证书连接器的计算机上运行 **ndesconnectorssetup.exe**。 对于 PKCS 证书配置文件，请在与证书颁发机构进行通信的计算机上安装证书连接器。
-  **Web 应用程序代理服务器**（可选）：可以将运行 Windows Server 2012 R2 或更高版本的服务器用作 Web 应用程序代理 (WAP) 服务器。 该配置：
    -  允许设备使用 Internet 连接接收证书。
    -  是设备通过 Internet 连接接收和续订证书时的安全建议。

 > [!NOTE]           
> -    托管 WAP 的服务器[必须安装更新程序](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx)，以支持网络设备注册服务 (NDES) 使用的长 URL。 此更新程序包括在 [2014 年 12 月更新汇总](http://support.microsoft.com/kb/3013769)中，或单独包括在 [KB3011135](http://support.microsoft.com/kb/3011135) 中。
>-  此外，托管 WAP 的服务器还必须具有与将要向外部客户端发布的名称相匹配的 SSL 证书，并且信任 NDES 服务器上使用的 SSL 证书。 这些证书使 WAP 服务器可以终止来自客户端的 SSL 连接，并创建至 NDES 服务器的新 SSL 连接。
    若要了解 WAP 证书，请参阅[规划使用 Web 应用程序代理发布应用程序](https://technet.microsoft.com/library/dn383650.aspx)的**规划证书**部分。 有关 WAP 服务器的常规信息，请参阅[使用 Web 应用程序代理](http://technet.microsoft.com/library/dn584113.aspx)。|


## <a name="certificates-and-templates"></a>证书和模板

|对象|详细信息|
|----------|-----------|
|**证书模板**|在发证 CA 上配置此模板。|
|**受信任的根 CA 证书**|可以从发证 CA 或信任发证 CA 的任何设备中将此证书导出为 **.cer** 文件，并通过使用受信任的 CA 证书配置文件将其分配给设备。<br /><br />你可以在每个操作系统平台上使用一个受信任的根 CA 证书，并将其与你创建的每个受信任的根证书配置文件相关联。<br /><br />你可以在需要时使用其它受信任的根 CA 证书。 例如，你可以这样做来信任为 Wi-Fi 访问点的服务器身份验证证书签名的 CA。|


## <a name="configure-your-infrastructure"></a>配置你的基础结构
必须先完成以下步骤，然后才能配置证书配置文件。 必须具备 Windows Server 2012 R2 和 Active Directory 证书服务 (ADCS) 方面的知识，才能执行下面这些步骤：

- **第 1 步** - 在证书颁发机构上配置证书模板。
- **第 2 步** - 启用、安装和配置 Intune 证书连接器。

## <a name="step-1---configure-certificate-templates-on-the-certification-authority"></a>第 1 步 - 在证书颁发机构上配置证书模板

### <a name="to-configure-the-certification-authority"></a>配置证书颁发机构

1.  在发证 CA 上，使用证书模板管理单元新建自定义模板，或复制并编辑现有模板（与用户模板相似）以与 PKCS 配合使用。

    证书模板必须包含下列内容：

    -   为模板指定易记“模板显示名称”。

    -   在“使用者名称”选项卡上，选择“在请求中提供”。 （由适用于 NDES 的 Intune 策略模块强制实施安全措施）。

    -   在“扩展”选项卡上，确保“应用策略描述”中包括“客户端身份验证”。

        > [!IMPORTANT]
        > 对于 iOS 和 macOS 证书模板，在“扩展”选项卡上，编辑“密钥用法”，并确保未选择“数字签名为原件的证明”。

2.  在模板的“常规”选项卡上，查看“有效期”。 默认情况下，Intune 使用模板中配置的值。 不过，可以视需要将 CA 配置为允许申请者指定其他值，随后便能够在 Intune 管理员控制台中设置此值。 如果你想要一直使用模板中的值，跳过该步骤的其余部分即可。

    > [!IMPORTANT]
    > iOS 和 macOS 始终使用模板中设置的值，无论你设置的其他配置如何。

    若要将 CA 配置为允许申请者指定有效期，请在 CA 上运行下列命令：

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  在发证 CA 上，使用证书颁发机构管理单元发布证书模板。

    a.  选择“证书模板”节点，依次单击“操作”-&gt;“新建”&gt;“要颁发的证书模板”，然后选择在第 2 步中创建的模板。

    b.  通过查看“证书模板”文件夹下的已发布模板来进行验证。

4.  在 CA 计算机上，确保托管 Intune 证书连接器的计算机拥有注册权限，以便它可以访问用于创建 PKCS 证书配置文件的模板。 在 CA 计算机属性的“安全性”选项卡上设置相应权限。

## <a name="step-2---enable-install-and-configure-the-intune-certificate-connector"></a>第 2 步 - 启用、安装和配置 Intune 证书连接器
在这一步中，你将：

- 启用对证书连接器的支持
- 下载、安装和配置证书连接器。

### <a name="to-enable-support-for-the-certificate-connector"></a>如何启用对证书连接器的支持

1.  登录到 Azure 门户中。
2.  选择“更多服务” > “监视 + 管理” > “Intune”。
3.  在“Intune”边栏选项卡上，选择“配置设备”。
2.  在“设备配置”边栏选项卡上，依次选择“设置” > “证书颁发机构”。
2.  在“第 1 步”下，选择“启用”。

### <a name="to-download-install-and-configure-the-certificate-connector"></a>如何下载、安装和配置证书连接器

1.  在“配置设备”边栏选项卡上，依次选择“设置” > “证书颁发机构”。
2.  选择“下载证书连接器”。
2.  下载完毕后，运行下载的安装程序 (**ndesconnectorssetup.exe**)。
  在能够连接证书颁发机构的计算机上运行安装程序。 依次选择“PKCS (PFX) 发行版本”选项和“安装”。 安装完成后，请按[如何配置证书配置文件](certificates-configure.md)中的说明操作，继续创建证书配置文件。

3.  在系统提示输入证书连接器的客户端证书时，依次选择“选择”和安装的“客户端身份验证”证书。

    选择客户端身份验证证书后，将返回“Microsoft Intune 证书连接器的客户端证书”区域。 选择“下一步”查看相应证书的属性，尽管选择的证书不会显示。 然后，依次选择“下一步”和“安装”。

4.  在向导完成后，先单击“启动证书连接器 UI”，然后再关闭向导。

    > [!TIP]
    > 如果在启动证书连接器 UI 前关闭了向导，你可以通过运行以下命令重新打开它：
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  在“证书连接器”UI 中：

    a. 选择“登录”，然后输入 Intune 服务管理员凭据或拥有全局管理权限的租户管理员的凭据。

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b. 选择“高级”选项卡，然后输入在证书颁发机构上拥有“颁发和管理证书”权限的帐户的凭据。

    c. 选择“应用”。

    你现在可以关闭证书连接器 UI。

6.  打开命令提示符，然后键入“services.msc”。 然后，按 Enter 键，右键单击“Intune 连接器服务”，然后选择“重启”。

若要验证服务是否在运行，请打开浏览器，然后输入以下 URL（应返回“403”错误）：

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**


### <a name="how-to-create-a-pkcs-certificate-profile"></a>如何创建 PKCS 证书配置文件

在 Azure 门户中，选择“配置设备”工作负载。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在“配置文件”边栏选项卡上，单击“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入 PKCS 证书配置文件的“名称”和“说明”。
5. 在“平台”下拉列表中，选择要向其应用此 PKCS 证书的设备平台：
    - **Outlook Web Access (OWA)**
    - **Android for Work**
    - **Android**
    - Windows 10 及更高版本
6. 在“配置文件类型”下拉列表中，选择“PKCS 证书”。
7. 在“PKCS 证书”边栏选项卡上，配置以下设置：
    - **续订阈值 (%)** - 指定设备请求续订证书之前剩余的证书生存期的百分比。
    - 证书有效期 - 如果在发证 CA 上运行允许自定义有效期的 **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** 命令，可以指定在剩余多长时间后证书到期。<br>你可以指定比指定证书模板中的有效期小的值，但不能指定较大的值。 例如，证书模板中的证书有效期为 2 年，则你可以指定值 1 年，但不能指定值 5 年。 该值还必须小于发证 CA 证书的剩余有效期。
    - 密钥存储提供程序(KSP) (Windows 10) - 指定证书密钥的存储位置。 可以选择下列值之一：
        - 注册到受信任的平台模块(TPM) KSP (若有); 否则，注册到软件 KSP
        - 注册到受信任的平台模块(TPM) KSP，否则失败
        - 注册到 Passport，否则失败(Windows 10 及更高版本)
        - 注册到软件 KSP
    - 证书颁发机构 - Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。 有关如何设置证书颁发机构的说明，请参阅[安装证书颁发机构](http://technet.microsoft.com/library/jj125375.aspx)。 如果 CA 是在 Windows Server 2008 R2 上运行，必须[安装 KB2483564 中的修补程序](http://support.microsoft.com/kb/2483564/)。
    - 证书颁发机构名称 - 输入证书颁发机构的名称。
    - 证书模板名称 - 输入配置使用网络设备注册服务且已添加到发证 CA 的证书模板的名称。
    请确保此名称与运行网络设备注册服务的服务器的注册表中所列证书模板名称之一完全匹配。 确保指定证书模板名称，而不是证书模板显示名称。 
    若要查找证书模板的名称，请浏览到以下项：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP。 你将看到作为 **EncryptionTemplate**、**GeneralPurposeTemplate**和 **SignatureTemplate** 的值而列出的证书模板。 默认情况下，所有三个证书模板的值均为“IPSECIntermediateOffline”，映射到模板显示名称“IPSec (脱机请求)”。 
    - 使用者名称格式 - 在列表中，选择 Intune 如何在证书请求中自动创建使用者名称。 如果证书用于用户，还可包含使用者名称中的用户电子邮件地址。 选择：
        - 未配置
        - 公用名称
        - 包含电子邮件地址的公用名称
        - 作为电子邮件地址的公用名称
    - 使用者可选名称 - 指定 Intune 如何在证书请求中自动创建使用者可选名称 (SAN) 的值。 例如，你选择了用户证书类型，则可以在使用者可选名称中包括用户主体名称 (UPN)。 如果使用客户端证书向“网络策略服务器”进行身份验证，则要将使用者可选名称设置为 UPN。 
    另外，也可以选择“自定义 Azure AD 属性”。 选择此选项后，将会显示另一个下拉字段。 在“自定义 Azure AD 属性”下拉字段中，有一个选项：“部门”。 选择此选项后，如果 Azure AD 中未标识部门，则不会颁发证书。 若要解决此问题，请标识部门并保存更改。 在设备下次签入时，问题将得到解决并将颁发证书。 ASN.1 是此字段使用的表示法。 
    - 扩展密钥用法 (Android) - 选择“添加”，添加证书的使用目的值。 大多数情况下，证书将需要“客户端身份验证”以便用户或设备能够向服务器进行验证。 但，你可以根据需要添加任何其他密钥用法。 
    - 根证书 (Android) - 选择之前配置并分配给用户或设备的根 CA 证书配置文件。 此 CA 证书必须是将颁发在此证书配置文件中配置的证书的 CA 的根证书。 这是之前创建的受信任的证书配置文件。
8. 完成后，返回“创建配置文件”边栏选项卡，然后单击“创建”。

系统将创建配置文件并在“配置文件列表”边栏选项卡上显示。

## <a name="how-to-assign-the-certificate-profile"></a>如何分配证书配置文件

将证书配置文件分配给组之前，请注意以下几点：

- 将证书配置文件分配给组时，将在设备上安装受信任的 CA 证书配置文件的证书文件。 设备使用 PKCS 证书配置文件来创建设备需要的证书。
- 仅在运行创建配置文件时使用的平台的设备上安装证书配置文件。
- 可以向用户集合或设备集合分配证书配置文件。
- 若要在注册设备后向设备快速发布证书，请将证书配置文件分配给用户组（而不是设备组）。 如果分配给设备组，那么必须进行完整的设备注册，然后设备才能接收策略。
- 尽管是单独分配每个配置文件，但仍需分配受信任的根 CA 和 PKCS 配置文件。 否则，PKCS 证书策略将失败。

若要了解如何分配配置文件，请参阅[如何分配设备配置文件](device-profile-assign.md)。
