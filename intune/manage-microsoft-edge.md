---
title: 结合使用 Microsoft Edge 和 Microsoft Intune 来管理 Web 访问
titleSuffix: ''
description: 结合使用 Intune 应用保护策略和 Microsoft Edge，确保公司的网站始终在安全措施到位的情况下被访问。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ad8a3298a801b07e021b84bd5eea9c91f01f1a2
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044879"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>结合使用 Microsoft Edge 和 Microsoft Intune 来管理 Web 访问

结合使用 Intune 应用保护策略和 Microsoft Edge，可确保公司的网站始终在安全措施到位的情况下被访问。 提供了 Intune 策略启用的以下 Microsoft Edge 企业功能。 这些企业功能包括：

1.  **双重标识** - 用户可以同时添加工作帐户以及个人帐户以进行浏览。 两个标识完全独立，这类似于 Office 365 和 Outlook 中的体系结构和体验。 Intune 管理员将能够为工作帐户中受保护的浏览体验设置所需的策略。
2.  **Intune 应用保护策略集成** - 由于 Microsoft Edge 已与 Intune SDK 集成，因此可以应用保护策略为目标，确保实现数据丢失保护。 这些功能包括控制剪切、复制和粘贴，阻止屏幕捕获，以及确保用户选择的链接仅在其他托管应用中打开。
3.  **Azure 应用程序代理集成** - 可控制对 SaaS 应用和 Web 应用的访问，帮助确保仅在安全的 Microsoft Edge 浏览器中运行基于浏览器的应用，不论最终用户是从公司网络连接还是从 Internet 连接。
4.  **应用程序配置** - 可利用应用程序配置设置来加强组织的安全状况，并为最终用户配置易用功能。 例如，可定义书签、主页快捷方式、允许/阻止的站点、Azure 应用程序代理等。
Microsoft Edge 的 Microsoft Intune 保护策略有助于保护组织的数据和资源。 结合使用这些策略和 Microsoft Edge，可确保公司的资源不仅在本机安装的应用中受保护，而且还在通过 Web 浏览器访问时受保护。

## <a name="getting-started"></a>开始使用

你与你的最终用户可从公共应用商店下载 Microsoft Edge 供组织使用。 浏览器策略的操作系统要求：
- Android 4 及更高版本，或
- iOS 8.0 及更高版本

## <a name="application-protection-policies-for-microsoft-edge"></a>Microsoft Edge 的应用程序保护策略

由于 Microsof Edge 已与 Intune SDK 集成，因此你可向其应用应用保护策略，包括：
- 控制剪切、复制和粘贴操作的使用。
- 防止发生屏幕捕获。
- 确保仅在托管应用和浏览器中打开公司链接。

有关详细信息，请参阅“什么是应用保护策略？”
可将这些设置应用于：
- 已向 Intune 注册的设备
- 注册了其他 MDM 产品的设备
- 非托管设备

如果 Microsoft Edge 不是 Intune 策略的目标，用户就无法使用它来访问其他 Intune 托管应用（如 Office 应用）中的数据。 

## <a name="conditional-access-for-microsoft-edge"></a>Microsoft Edge 的条件访问

可利用 Azure AD 条件访问重定向用户，使其只能通过 Microsoft Edge 访问公司内容。 这将移动浏览器对 Azure AD 连接的 Web 应用的访问限制在受策略保护的 Microsoft Edge，并阻止从任何其他不受保护的浏览器（如 Safari 或 Chrome）进行访问。 条件访问可应用于 Azure 资源（如 Exchange Online 和 SharePoint Online）、Microsoft 365 管理中心，甚至本地站点（这些站点已通过 [Azure AD 应用程序代理](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)向外部用户公开）。

若要将 Azure AD 连接的 Web 应用限制为在 iOS 和 Android 上使用 Microsoft Edge，请执行以下步骤：
1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 Intune 节点下，选择“条件访问”   > “新建策略”  。
3. 接下来，从选项卡的“访问控制”部分选择“授予”   。
4. 单击“需要核准的客户端应用”  。
5. 在“授予”边栏选项卡上单击“选择”   。 必须将此策略分配给希望只由 Intune Managed Browser 应用访问的云应用。

    ![条件访问策略 - 授予](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. 在“分配”部分，选择“条件”>“客户端应用”。 随即显示“客户端应用”边栏选项卡。
7. 单击“配置”下的“是”，将策略应用到特定客户端应用。
8. 确认“浏览器”已被选为客户端应用。

    ![条件访问策略 - 选择客户端应用](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > 若要限制可访问这些云应用程序的本机应用（非浏览器应用），还可以选择“移动应用和桌面客户端”  。

9. 在“分配”部分，选择“用户和组”，然后选择要向其分配此策略的用户或组   。

    > [!NOTE]
    > 还必须使用 Intune 应用保护策略选择目标用户，以便接收应用配置策略。 有关创建 Intune 应用保护策略的详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)

10. 在“分配”部分，选择“云应用”，选择要使用此策略保护的应用   。

配置以上策略后，会强制要求用户使用 Microsoft Edge 访问已通过此策略保护的 Azure AD 连接的 Web 应用。 如果用户尝试在此情况下使用非管理的浏览器，他们会看到一条消息，指示他们必须使用 Microsoft Edge。

> [!TIP]
> 条件访问是一项 Azure Active Directory (Azure AD) 技术。 从 Intune 访问的条件访问节点与从 Azure AD 访问的节点相同。

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>在受策略保护的浏览器中单一登录到 Azure AD 连接的 Web 应用

iOS 和 Android 上的 Microsoft Edge 可利用到 Azure AD 连接的所有 Web 应用（SaaS 和本地）的 SSO。 SSO 允许用户通过 Microsoft Edge 访问 Azure AD 连接的 Web 应用，而无需重新输入其凭据。

SSO 要求设备通过 Microsoft Authenticator 应用（iOS 设备）或 Intune 公司门户（Android）进行注册。 在用户有 Authenticator 应用或 Intune 公司门户的情况下，若设备尚未进行注册，则当用户在受策略保护的浏览器中导航到一个 Azure AD 连接的 Web 应用时，系统会提示他们注册其设备。 使用 Intune 管理的用户帐户注册设备后，该帐户将为 Azure AD 连接的 Web 应用启用 SSO。

> [!NOTE]
> 设备注册是 Azure AD 服务的简单签入。 不需要完整的设备注册，并且不会向 IT 提供设备上的任何其他权限。

## <a name="create-a-protected-browser-app-configuration"></a>创建受保护的浏览器应用配置

对于要应用的应用配置，用户的受保护浏览器或设备上的其他应用必须已由 [Intune 应用保护策略](app-protection-policy.md)托管。

使用以下步骤创建受保护的浏览器应用配置：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“客户端应用”   > “应用配置策略”   > “添加”  。
3. 在“添加配置策略”边栏选项卡上，输入应用配置设置的“名称”和可选“描述”    。
4. 对于“设备注册”类型，选择“托管应用”   。
5. 选择“选择所需应用”  ，然后在“目标应用”  边栏选项卡上，选择适用于 iOS 或适用于 Android（或适用于两者）的“Managed Browser”  和/或“Microsoft Edge”  。
6. 选择“确定”，返回“添加配置策略”边栏选项卡   。
7. 选择“配置设置”  。 在“配置”  边栏选项卡上，定义键值对来为 Microsoft Edge 提供配置。 请参阅本文的后续部分，了解可以定义的不同键值对。

    > [!NOTE]
    > Microsoft Edge 使用与 Managed Browser 相同的键值对。 

8.  完成后，请单击“确定”  。
9.  在“添加配置策略”边栏选项卡上，选择“添加”   。<br>
    创建新配置后，其显示在“应用配置”  边栏选项卡上。

## <a name="assign-the-configuration-settings-you-created"></a>分配已创建的配置设置 

将这些设置分配到 Azure AD 用户组。 如果用户安装了受保护的目标浏览器应用，则应用将按指定的设置进行管理。

1. 在 Intune 移动应用程序管理仪表板的“客户端应用”边栏选项卡上，选择“应用配置策略”   。
2. 在应用配置列表中，选择一个想要分配的配置。
3. 在下一个边栏选项卡上，选择“分配”  。
4. 在“分配”边栏选项卡上，选择想要将应用配置分配到的 Azure AD 组，然后选择“确定”   。

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>如何为受保护的浏览器配置应用程序代理设置

Microsoft Edge 和 [Azure AD 应用程序代理](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)可以一起使用，使用户能够在其移动设备上访问 Intranet 站点。 

以下是 AD 应用程序代理支持的一些场景示例： 

- 一个用户使用受 Intune 保护的 Outlook 移动应用。 然后，该用户单击电子邮件中的一个指向 Intranet 站点的链接，Microsoft Edge 识别出该站点已通过应用程序代理向用户公开。 将通过应用程序代理对用户进行自动路由，以便在进入 Intranet 站点前进行任何适用的多重身份验证和条件性访问。 用户现在甚至可以在其移动设备上访问内部网站，而 Outlook 中的链接也如预期一样正常运行。
- 用户在其 iOS 或 Android 设备上打开 Microsoft Edge。 如果 Microsoft Edge 受 Intune 保护，并且应用程序代理已启用，则用户可使用其习惯使用的内部 URL 导航到 Intranet 站点。 Microsoft Edge 识别出此 Intranet 站点已通过应用程序代理向用户公开，且用户自动通过应用程序代理进行路由，以在进入该 Intranet 站点之前进行身份验证。 

### <a name="before-you-start"></a>开始之前

- 通过 Azure AD 应用程序代理设置内部应用程序。
    - 要配置应用程序代理和发布应用程序，请参阅[设置文档](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。
- Microsoft Edge 应用必须分配 [Intune 应用保护策略](app-protection-policy.md)。

> [!NOTE]
> 更新的应用程序代理重定向数据最长可能需要 24 小时才能在 Managed Browser 和 Microsof Edge 中生效。

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>步骤 1：从 Outlook 启用指向受保护的浏览器的自动重定向
Outlook 必须配置有应用保护策略，该策略启用“使用策略托管浏览器共享 Web 内容”  设置。

![应用保护策略 - 使用策略托管浏览器共享 Web 内容](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>步骤 2：设置应用配置设置以启用应用代理
使用以下键/值对将 Microsoft Edge 作为目标，为 Microsoft Edge 启用应用程序代理：

|    Key    |    值    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

若要深入了解 Microsoft Edge 和 Azure AD 应用程序代理如何相继配合使用，以实现本地 Web 应用的无缝（和受保护）访问，请参阅“企业移动性 + 安全性”博客文章[更好地协作：配合使用 Intune 和 Azure Active Directory，改善用户访问](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access)。 此博客文章参考了 Intune Managed Browser，但该内容也适用于 Microsoft Edge。

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>如何为 Microsoft Edge 配置主页快捷方式

通过此设置可为 Microsoft Edge 配置主页快捷方式。  在 Microsoft Edge 中打开一个新选项卡时，配置的主页快捷方式将显示为搜索栏下的第一个图标。 用户无法在其托管上下文中编辑或删除此快捷方式。 主页快捷方式将显示组织的名称以便进行区分。 

使用以下键/值对来配置主页快捷方式：

|    Key    |    值    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    指定有效 URL。 将阻止错误的 URL，这是一项安全措施。<br>示例：  `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>如何为 Microsoft Edge 配置托管书签

为了便于访问，可配置希望用户在使用 Microsoft Edge 时可用的书签。 下面是一些详细信息：

- 这些书签仅在用户使用企业模式的 Microsoft Edge 时才会显示。 
- 用户无法删除或修改这些书签。
- 这些书签显示在列表顶部。 用户创建的任何书签显示在这些书签下方。
- 如果已启用应用代理重定向，可以使用应用代理 Web 应用的内部或外部 URL 添加应用。

使用以下键/值对来配置托管书签：

|    Key    |    值    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    此配置的值是一个书签列表。 每个书签都由书签标题和书签 URL 组成。 用字符 `|` 分隔标题和 URL。      **示例：**<br>`Microsoft Bing|https://www.bing.com`<p>若要配置多个书签，可使用双字符 `||` 分隔每对书签。<p>**示例：**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>如何在 Microsoft Edge 书签内显示 MyApps

默认情况下，用户可在 Microsoft Edge 书签内的某个文件夹中看到为他们配置的 MyApps 站点。 该文件夹标有你的组织的名称。

|    Key    |    值    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True**：在 Microsoft Edge 书签内显示 MyApps。<p>**False**：在 Microsoft Edge 书签内隐藏 MyApps。    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>如何为 Microsoft Edge 指定允许或阻止的站点列表
可使用应用配置来定义用户在使用其工作配置文件时可访问的站点。 如果你使用允许列表，用户只能访问已显式列出的站点。 如果你使用阻止列表，用户能够访问除已显式阻止的站点以外的所有站点。 应仅使用一个允许列表或一个阻止列表，而不能同时使用两者。 如果同时对设备使用两者，将优先使用允许列表。  

可使用以下键/值对为 Microsoft Edge 配置一个允许或阻止站点列表。 有关有效的 URL 格式的详细信息，请继续阅读。 

|    Key    |    值    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    选择：<p>1.指定允许的 URL（仅允许这些 URL；无法访问其他站点）：<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2.指定阻止的 URL（可访问其他所有站点）：<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    键的对应值是 URL 列表。 将要允许或阻止的所有 URL 作为单个值输入，并用竖线 `|` 字符分隔。<p>**示例：**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>允许的和阻止的站点列表的 URL 格式 
可使用多种 URL 格式来构建允许/阻止的站点列表。 下表详细介绍了这些允许的模式。 开始之前，请注意以下几点： 
- 在将 URL 输入列表时，确保对所有 URL 添加 **“http”** 或 **“https”** 作为前缀。
- 可以根据以下允许模式列表中的规则使用通配符 (*)。
- 可以在地址中指定端口号。 如果未指定端口号，则使用以下值：
    - 对于 http，使用端口 80
    - 对于 https，使用端口 443
- 不支持对端口号使用通配符  。 例如，不支持 `http://www.contoso.com:*` 和 `http://www.contoso.com:*/`。

    |    URL    |    详细信息    |    匹配    |    不匹配    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    匹配单个页面    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    匹配单个页面    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    匹配以 `www.contoso.com` 开头的所有 URL    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    匹配 `contoso.com` 下的所有子域    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    匹配单个文件夹    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    匹配单个页面（使用端口号）    |    http://www.contoso.com:80    |         |
    |    `https://www.contoso.com`    |    匹配单个安全页面    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    匹配单个文件夹和所有子文件夹    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- 以下是一些你不能指定的输入的示例：
    - `*.com`
    - `*.contoso/*`
    - `www.contoso.com/*images`
    - `www.contoso.com/*images*pigs`
    - `www.contoso.com/page*`
    - IP 地址
    - `https://*`
    - `http://*`
    - `http://www.contoso.com:*`
    - `http://www.contoso.com: /*`
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>定义用户尝试访问阻止的站点时的行为

借助内置于 Microsoft Edge 的双重标识模型，可为最终用户提供更灵活的体验，而这在 Intune Managed Browser 中是不可能实现的。 当用户在 Microsoft Edge 中访问阻止的站点时，系统会提示他们在个人上下文（而非工作上下文中）中打开链接，这使他们能够持续受到保护，同时保证公司资源的安全。 例如，如果通过 Outlook 向用户发送新闻文章的链接，用户可以在个人上下文或 InPrivate 选项卡中（而非工作上下文中，工作上下文中不允许新闻网站）打开该链接。 默认情况下，这些转换是允许的。

使用以下键/值对来配置是否允许这些软转换：

|    Key    |    值    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True**：允许 Microsoft Edge 将用户转换到其个人上下文以打开阻止的站点<p>**阻止**：阻止 Microsoft Edge 转换用户，用户只会看到一条消息，指示他们尝试访问的站点被阻止。    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>将用户定向到 Microsoft Edge，而不是 Intune Managed Browser 

现在，Intune Managed Browser 和 Microsoft Edge 都可用作受策略保护的浏览器。 若要确保将用户定向为使用正确的浏览器应用，请使用以下配置设置将所有 Intune 托管应用（例如，Outlook 和 OneDrive）设为目标：

|    Key    |    值    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    若值为 `true`，则将用户定向为使用 Microsoft Edge。<p>若值为 `false`，则将用户定向为使用 Intune Managed Browser。    |

如果未设置此应用配置值，以下逻辑将定义打开企业链接所使用的浏览器。

在 Android 上：
- 如果用户已在设备上同时下载 Intune Managed Browser 和 Microsoft Edge，则会启动 Intune Managed Browser。 
- 如果设备上只下载了 Microsoft Edge，并且目标是 Intune 策略，则会打开 Microsoft Edge。
- 如果设备上只有 Managed Browser 且目标是 Intune 策略，则会打开 Managed Browser。

在 iOS 上，对于已经集成了针对 iOS v. 9.0.9+ 的 Intune SDK 的应用：
- 如果设备上同时存在 Managed Browser 和 Microsoft Edge，则会启动 Intune Managed Browser。  
- 如果设备上只有 Microsoft Edge，并且目标是 Intune 策略，则会启动 Microsoft Edge。
- 如果设备上只有 Managed Browser 且目标是 Intune 策略，则会启动 Managed Browser。

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>在 iOS 上使用 Microsoft Edge 访问托管的应用日志 

在 iOS 设备上安装了 Microsoft Edge 的最终用户可查看所有 Microsoft 已发布应用的管理状态。 他们还可针对托管 iOS 应用的疑难问题发送日志。
1. 在 iOS 设备上打开 Microsoft Edge。
2. 在地址框中键入 `about:intunehelp`。 
3. 故障排除模式将从 Microsoft Edge 内部启动。

对于应用日志中存储的设置列表，请参阅[在 Managed Browser 中查看应用保护日志](app-protection-policy-settings-log.md)。

若要了解如何在 Android 设备上查看日志，请参阅[通过电子邮件将日志发送给 IT 管理员](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。 

## <a name="security-and-privacy-for-microsoft-edge"></a>Microsoft Edge 的安全和隐私

Microsoft Edge 的其他安全和隐私注意事项：

- Microsoft Edge 不使用用户在其设备上为本机浏览器设置的设置，因为 Microsoft Edge 无法访问这些设置。
- 如果配置与 Microsoft Edge 关联的一个应用保护策略中的选项“访问需要简单 PIN”  或“访问需要公司凭据”  ，且用户选择了身份验证页面上的帮助链接，那么无论是否已将这些用户添加到策略中的阻止列表中，他们都可以浏览任何 Internet 站点。
- Microsoft Edge 仅能在用户直接访问站点时阻止访问。 使用中间服务（例如翻译服务）访问站点时，该策略则不会阻止访问。
- 若要允许身份验证和访问 Intune 文档，请从允许或阻止列表设置中移除 *.microsoft.com  。 始终允许。
禁用使用情况数据。Microsoft 会自动收集有关性能和 Managed Browser 使用情况的匿名数据，以改进 Microsoft 产品和服务。 用户可通过使用设备上的**使用情况数据**设置关闭数据收集。 不具有对此数据的收集的控制。 在 iOS 设备上，如果用户访问的网站的证书已过期或不受信任，则无法打开该网站。

## <a name="next-steps"></a>后续步骤

- [什么是应用保护策略？](app-protection-policy.md) 
