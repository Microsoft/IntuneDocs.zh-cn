---
title: 配置 PFX 证书基础结构 |Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 05/16/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: vinaybha
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:


---
# 配置证书基础结构
本主题介绍创建和部署证书配置文件所需具备的条件。

若要在组织中执行任何基于证书的身份验证，你需要企业证书颁发机构。

若要使用 .PFX 证书配置文件，除了企业证书颁发机构，你还需要：

-   可以与证书颁发机构进行通信的计算机，或可以使用证书颁发机构计算机本身。

 -  Intune 证书连接器，它在可以与证书颁发机构进行通信的计算机上运行。

## 本地基础结构说明


-    **Active Directory 域**：本部分列出的所有服务器（Web 应用程序代理服务器除外）必须加入你的 Active Directory 域。

-  **证书颁发机构** (CA)：在 Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。 有关如何设置证书颁发机构的说明，请参阅 [安装证书颁发机构](http://technet.microsoft.com/library/jj125375.aspx)。
    如 CA 运行的是 Windows Server 2008 R2，则必须 [安装修补程序 KB2483564](http://support.microsoft.com/kb/2483564/)。

 -  **可以与证书颁发机构进行通信的计算机**：或者，使用证书颁发机构计算机本身。
-  **Microsoft Intune 证书连接器**：使用 Intune 管理控制台下载**证书连接器**安装程序 (**ndesconnectorssetup.exe**)。 随后可以在想要安装证书连接器的计算机上运行 **ndesconnectorssetup.exe** 。 对于 .PFX 证书配置文件，请在与证书颁发机构进行通信的计算机上安装证书连接器。
-  **Web 应用程序代理服务器**（可选）：你可以使用运行 Windows Server 2012 R2 或更高版本的服务器作为 Web 应用程序代理 (WAP) 服务器。 该配置：
    -  允许设备使用 Internet 连接接收证书。
    -  是设备通过 Internet 连接接收和续订证书时的安全建议。

 > [!NOTE]           
> -    承载 WAP 的服务器 [必须安装此更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) 以支持网络设备注册服务所使用的长 URL。 该更新包括在 [2014 年 12 月的更新汇总中](http://support.microsoft.com/kb/3013769)，或单独更新自 [KB3011135](http://support.microsoft.com/kb/3011135)。
>-  此外，托管 WAP 的服务器必须具有与要向外部客户端发布的名称相匹配的 SSL 证书，并且信任 NDES 服务器上使用的 SSL 证书。 这些证书使 WAP 服务器可以终止来自客户端的 SSL 连接，并创建至 NDES 服务器的新 SSL 连接。
有关 WAP 证书的信息，请参阅[计划使用 Web 应用程序代理发布应用程序](https://technet.microsoft.com/library/dn383650.aspx)的“计划证书”部分。 有关 WAP 服务器的一般信息，请参阅 [Working with Web Application Proxy](http://technet.microsoft.com/library/dn584113.aspx)（使用 Web 应用程序代理）。|


### 证书和模板

|对象|详细信息|
|----------|-----------|
|**证书模板**|在发证 CA 上配置此模板。|
|**受信任的根 CA 证书**|你可以从发证 CA 或信任该发证 CA 的任何设备中将其导出为 **.cer** 文件，并通过使用可信 CA 证书配置文件将其部署至设备。<br /><br />你可以在每个操作系统平台上使用一个受信任的根 CA 证书，并将其与你创建的每个受信任的根证书配置文件相关联。<br /><br />你可以在需要时使用其它受信任的根 CA 证书。 例如，你可以这样做来信任为 Wi-Fi 访问点的服务器身份验证证书签名的 CA。|


## 配置你的基础结构
在可以配置证书配置文件之前，必须完成以下需要 Windows Server 2012 R2 和 Active Directory Certificate Services (ADCS) 知识的任务：

**任务 1** — 配置证书颁发机构上的证书模板**任务 2** - 启用、安装和配置 Intune 证书连接器

### 任务 1 - 配置证书颁发机构上的证书模板
在该任务中，需发布证书模板

##### 配置证书颁发机构

1.  在发证 CA 上，使用证书模板管理单元创建新的自定义模板，或复制现有模板然后编辑现有模板（与用户模板相似）以与 .pFX 配合使用。

    模板必须进行以下配置：

    -   为模板指定一个友好的 **“模板显示名称”** 。

    -   在 **“使用者名称”** 选项卡上，选择 **“在请求中提供”**。 （由用于 NDES 的 Intune 策略模块强制实施安全性）。

    -   在 **“扩展”** 选项卡上，确保 **“应用程序策略描述”** 包括了 **“客户端身份验证”**。

        > [!IMPORTANT] 对于 iOS 和 Mac OS X 证书模板，在**扩展**选项卡上编辑**密钥用法**并确保未选择**数字签名为原件的证明**。


3.  在模板的 **“常规”** 选项卡上查看 **“有效期”** 。 默认情况下，Intune 使用在模板中配置的值。 但是，你可以选择配置 CA 以允许请求者指定不同的值，随后你也能够在 Intune 管理员控制台设置该值。 如果你想要一直使用模板中的值，跳过该步骤的其余部分即可。

    > [!IMPORTANT] 无论你所做出的其他配置是什么，iOS 和 Mac OS X 平台都始终使用模板中设置的值。

    若要配置 CA 以允许请求者指定有效期，请在 CA 上运行以下命令：

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  在发证 CA 上，使用证书颁发机构管理单元发布证书模板。

    1.  选择**证书模板**节点，单击**操作**-&gt;**新建**&gt;**要颁发的证书模板**，然后选择你在步骤 2 中创建的模板。

    2.  通过查看 **“证书模板”** 文件夹下已发布的模板来对它进行验证。

5.  在 CA 计算机上，确保托管 Intune 证书连接器的计算机具有注册权限，以便它可以访问在创建 .PFX 配置文件时使用的模板。 在 CA 计算机属性的“安全性”  选项卡上设置该权限。

### 任务 2 - 启用、安装和配置 Intune 证书连接器
在此任务中，你将：

下载、安装和配置证书连接器

##### 启用对证书连接器的支持

1.  打开“Intune 管理控制台”[](https://manage.microsoft.com)，单击**管理**&gt;**证书连接器**。

2.  单击**配置本地证书连接器**。

3.  选择“启用证书连接器” ，然后单击“确定” 。

##### 下载、安装和配置证书连接器

1.  打开“Intune 管理控制台”[](https://manage.microsoft.com)，然后单击**管理** &gt;**移动设备管理**&gt;**证书连接器**&gt;**下载证书连接器**。

2.  下载完成之后，运行下载的安装程序 (**ndesconnectorssetup.exe**)：

  在能够与证书颁发机构连接的计算机上运行安装程序。 选择“.PFX 分发”选项，然后单击“安装”。 安装完成后，如[配置证书配置文件](configure-intune-certificate-profiles.md)中所述，继续创建证书配置文件。

   <!-- Not sure about step 3 below -->

3.  提示输入证书连接器的客户端证书时，单击**选择**，然后选择任务 3 中安装的**客户端身份验证**证书。

    选择客户端身份验证证书后，你将返回到“Microsoft Intune 证书连接器的客户端证书”  处。 尽管你选择的证书不会显示，但可以单击 **“下一步”** 查看该证书的属性。 然后单击 **“下一步”**，再单击 **“安装”**。

4.  向导完成后，关闭向导前，单击“启动证书连接器 UI” 。

    > [!TIP] 如果在启动证书连接器 UI 前关闭了向导，你可以通过运行以下命令重新打开它：
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  在“证书连接器”  UI 中：

    单击“登录”并输入你的 Intune 服务管理员凭据或具有全局管理权限的租户管理员的凭据。

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    选择 **“高级”** 选项卡，然后提供具有在证书颁发机构 **“颁发和管理证书”** 的权限的帐户凭据，然后单击 **“应用”**。

    你现在可以关闭证书连接器 UI。

6.  打开命令提示符并键入 **services.msc**，然后按 **Enter**，右键单击 **Intune 连接器服务**，再单击**重启**。

若要验证服务是否正在运行，打开浏览器然后输入以下 URL 将返回 **“403”** 错误：

**http:// &lt;NDES 服务器的 FQDN&gt;/certsrv/mscep/mscep.dll**

### 后续步骤
你现在可以像[配置证书配置文件](Configure-Intune-certificate-profiles.md)中所述的那样配置证书配置文件了。


<!--HONumber=Jun16_HO1-->


