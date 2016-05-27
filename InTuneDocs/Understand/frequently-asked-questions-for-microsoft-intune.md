---
# required metadata

title: 常见问题 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a8126cca-9ec4-454b-a20b-dc1bb6797327

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 有关 Intune 的常见问题
本文回答有关 Intune 的一些常见问题。 如果在此处看不到你问题的答案，请[告诉我们](https://microsoftintune.uservoice.com/)

## 一般问题

-   **如何知道 Intune 服务何时已更新？**

    在 manage.microsoft.com 登录你的帐户。 在“管理概述”中选择“查看服务状态”。 租户的位置和维护计划在此处列出。 在[新增功能](/intune/deploy-use/whats-new-in-microsoft-intune)文章中了解服务更新。

-   **如果用户在公司门户应用内重命名设备，则名称会在 Intune 或配置管理器中更改吗？**

    不会，名称更改仅为了用户方便。

-   **移动设备的 Intune 中是否具有远程协助功能？**

    不，没有。 第三方应用（如 [Bomgar](http://www.bomgar.com/) 和 [TeamViewer](https://www.teamviewer.com/)）可能会非常有用。

## 帐户

-   **如果我开始评估 Intune 并创建新租户进行试用，则是否可以使用同一租户将 Office 365 添加到评估中？**

    适用。 只需使用全局管理员从现有的 Intune 帐户/订阅（如 *globaladmin@&lt;company&gt;.onmicrosoft.com*）登录

-   **如果我在试用订阅期间将 MDM 机构指定给 Intune，当我对 Intune 改变主意时，这会使切换到另一家公司的服务变得困难吗？**

    尽管很难想象你仍不坚持使用 Intune，但 MDM 机构的选择不会影响你能否迁移到另一项服务。 对选择 Intune 还是与 System Center Configuration Manager 一起使用的 Intune 是明确的。

-   **我可以对后续 Intune 帐户使用现有 Office 365 域名吗？**

    如果当你在创建 Intune 试用版或激活许可证时，使用与现有 Office 365 租户和验证过的域相关联的组织 ID 登录，则可以。

    Intune 随后将使用同一个域/用户/等作为你的 Office 365 帐户。 请注意每个 Office 365 用户需要使用 Intune 许可证启用，作为 Intune 用户。 这将不得不由管理租户的全局管理员完成。

## 注册

-   **我的用户可以从何处了解如何注册其设备？**

    你可以使用或自定义来自[面向 IT 管理员的最终用户 Intune 注册说明](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)的信息

-   **如何解决有关设备注册的问题？**

    [排查 Intune 中的设备注册问题](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune)中介绍了常见的注册问题的故障排除方法

-   **如果用户具有注册问题，如何收集注册日志？**

    按照[以下说明](http://www.microsoft.com/en-us/download/46391)操作

## 移动设备管理

-   **常规 MDM**

    -   **Intune 是否可以检测设备已越狱？**

        对于某些操作系统而言，是的。 有关如何管理已越狱设备的信息，请参阅[创建设备合规性策略](/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune.md)

    -   **是否可以有选择地擦除设备中的企业数据？**

        适用。 有关选择性擦除的信息，请参阅[使用远程擦除、远程锁定或密码重置功能帮助保护数据](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune.md)

    -   **有没有一种方法通过 Intune 阻止移动设备浏览器上的某些网站？**

        在任何平台的本机浏览器上都没有 但是，如果你已在 iOS 和 Android 设备上部署了 Intune 托管的 Web 浏览器，则可以允许或阻止 URL。 有关详细信息，请参阅[使用托管浏览器策略管理 Internet 访问](/intune/Deploy-Use/Manage-Internet-access-using-managed-browser-policies-with-Microsoft-Intune.md)

    -   **我们是否能够限制用户卸载应用？**

        通常情况下，不能。 但是，在监督的 iOS 设备上可以阻止用户卸载使用 Apple 配置器分发的应用。 

    -   **有没有一种方法来管理移动数据使用情况？**

        没有直接的办法，但你可以通过将 Wi-Fi 配置文件推送到设备，确保 Wi-Fi 是连接的首选方法，如[帮助用户使用 Wi-Fi 配置文件连接到公司网络](/intune/Deploy-Use/wi-fi-connections-in-microsoft-intune.md)所述。 此外，某些平台（例如，iOS 和 Android KNOX）可以启用控件设置（如语音和数据漫游）的功能。

    -   **有没有一种方法来防止用户取消注册设备？ 如果是公司拥有设备呢？**

        通常情况下，没有。 但是，使用自定义 Windows Phone 设置，你可以在 Windows Phone 8.1 上阻止用户注册。 此外，对于在 Apple 的设备注册程序 (DEP) 中监管和注册的 iOS 设备，则可以防止用户取消注册设备。

    -   **我可以切换我选的 MDM 机构吗？**

        你可以在某些情况下切换 MDM 机构。 为此，请联系支持部门，如[如何获取对 Microsoft Intune 的支持](/intune/Troubleshoot/How-to-get-support-for-Microsoft-Intune.md)中所述。 下表说明了哪些更改是可能的。 MDM 机构中的更改需要重新注册设备。

        **目标机构：**Intune!**目标机构：**O365|**目标机构：**带 Microsoft Intune 的 Configuration Manager
        
        **起始机构：**Intune| |是&#42;|是|



-   ****起始机构：**O365||是&#42;||是|**

    -   ****起始机构：**带 Microsoft Intune 的 Configuration Manager|是|是| |**

        *O365 和 Intune MDM 机构可以共存，因此你无需再重新注册移动设备。 Windows 我可以旁加载 Windows 应用商店应用吗？

    -   **不能旁加载公开提供的应用。**

        即使你能够下载 XAP，但你也不能将它上载到 Intune，因为它是公开的 XAP，使用开发人员的代码签名证书进行过加密和签名。 只有你使用自己的代码签名证书进行开发和签名的应用才可以进行旁加载。

    -   **是否通过公司门户分发的 Windows Phone 应用商店应用要求最终用户具有 Microsoft 帐户？**

        是的，最终用户如果没有 Microsoft 帐户，将无法获取应用。 但存在例外，旁加载的专用 LOB 应用可以在没有 Microsoft 帐户的情况下部署到设备。

        **Windows Phone 8.1 上是否需要 Microsoft 帐户，以便其能够通过 Intune 管理？**
        否。 但是，需要安装来自公用存储的大多数应用。 为什么 Windows Phone 管理需要 Symantec 证书？ Windows Phone 控制安装应用的方式。 拥有 Microsoft 帐户的任何用户都可以从 Windows Phone 应用商店中安装应用，而公司可以使用 Windows Phone 文档中所述的特殊过程来安装或旁加载其内部开发的业务线 (LOB) 应用。

        安装 LOB 应用时，Windows Phone 仅信任一种由 Symantec 颁发的特殊类型的证书。 不能使用任何其他商业证书或私人生成的证书。 该要求适用于所有移动设备管理解决方案，而不仅仅是 Intune。 Symantec 证书创建一个应用程序注册令牌 (AET)。 如果设备注册了移动设备管理，则可以将 AET 安装在该设备上，或者也可以从安全的网站或电子邮件附件带外安装。 管理员必须使用 [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=268439)中提供的工具，通过 Symantec 证书对每个 LOB 应用进行签名。 当用户尝试安装 LOB 应用时，Windows Phone 操作系统会对照应用上的签名来检查 AET 中的签名。

        -   如果签名匹配，则允许安装继续进行。

        -   如果无法验证 AET，安装将失败。

        -   如下几个原因可能导致无法验证 AET：

        从未在设备上安装过 AET

    **AET 已过期**
  AET 不是使用用于对应用进行签名的相同 Symantec 证书创建 Windows Phone 在 MDM 注册过程中不需要 AET，但在 2014 年 11 月发布前，Intune 需要 AET 和签名的 ssp.xap，因为没有在注册过程中安装 AET 和 ssp.xap 的其他方法。

      > 如何为 Intune 用户创建 AET？

    **当管理员上载其 Symantec 证书的 .pfx 文件时，Intune 将自动创建 AET 并将其部署到注册的 Windows Phone。**
       Intune 管理员无需在 Windows Phone SDK 中使用 AET 生成器工具。

       -   Intune 不支持手动创建 AET 以及对其进行带外部署。 为了降低 Symantec 证书要求，做出了哪些更改？

        -   Intune 对 2014 年 11 月 发布的版本进行了更改，以允许公司不具有 Symantec 证书的方案。 Windows Phone 8.1 公司门户可以从应用商店安装，因此不需要使用 Symantec 证书进行签名以及对照 AET 进行验证。 而是在应用商店发布过程中进行验证。

        有没有 AET 均能在手机上注册 Windows Phone 8.1 设备。 如果 AET 可用，则在首次将设备与 Intune 同步时进行安装。

        **如果没有 AET，Intune 仍可管理设备，用户可以从应用商店安装公司门户并使用公司门户的大多数功能，而无需 Symantec 证书对应用进行签名。**
        针对 Windows Phone 8 设备的 Symantec 要求没有更改。

        -   Windows Phone 8 设备在注册过程中必须有签名的 ssp.xap 和 AET，否则它们将无法注册。

        -   如果注册了 Windows Phone 8.1 设备，但没有 Symantec 证书，则支持哪些功能？

        -   如果注册了 Windows Phone 8.1 设备，但没有 Symantec 证书，你可以：

        -   创建策略并将它们推送到设备

        -   配置 IT 部门联系人信息，这些信息将显示在公司门户上

        创建可链接到应用商店的深层链接并将这些链接部署到公司门户

        > [!IMPORTANT]
        > 创建链接到网页的链接并将这些链接部署到公司门户 创建条款和条件，用户只有接受它们才可以使用公司门户

        **没有 Symantec 证书的情况下无法部署 LOB 应用。**
        Intune 软件发行者不会在你上载应用的过程中验证这些应用是否已经签名。 如果你部署未签名的应用，则当用户尝试安装它们的时候会失败。 如何用户有公司门户，但没有 Symantec 证书，用户可以做什么？

        用户在从应用商店安装公司门户之前无需注册 Windows Phone 8.1 设备。

        -   如果设备未注册，则系统会提示用户进行注册。 点击公司门户中的提示可将用户直接转至“设置/工作区”，用户可以在其中注册其设备。

        -   即使没有注册设备，用户也可以使用从应用商店安装的公司门户执行以下操作：

        -   接受或拒绝管理员配置的任何条款和条件。

        -   如果用户拒绝了条款和条件，则公司门户将关闭。

        -   查看 IT 部门的联系人信息

        查看任何已注册的设备，包括 iOS、Android 和 Windows 设备 使用链接到应用商店中的应用的深层链接 使用 web 链接以打开网页 注册设备后，用户可以查看 **“我的设备”** 列表中的设备。

        注册后，设备必须遵守任何部署的 Intune 策略。

        **若要获取 AET 并安装 LOB 应用，则必须注册设备。 尝试安装 LOB 应用的设备将被指引进行注册。**
        如果公司没有 Symantec 证书，用户只能安装管理员部署的 LOB 应用。 我们公司已拥有证书，并已注册 Windows Phone 8.1 设备。

        **既然可以在应用商店中获得公司门户，那么我需要做些其他什么操作吗？**
        从下载中心获取的当前 ssp.xap 仍可以在 Windows Phone 8.1 设备上工作。

        -   你可以继续指引用户在安装过程中注册并获得公司门户。

        -   用户从应用商店获得公司门户有哪些优缺点？

        -   优点：

        -   即使不注册 Windows Phone 8.1 设备，用户也可以获得深层链接和 Web 链接

        当 Microsoft 更新公司门户时，无需下载、签名和重新部署 ssp.xap，应用商店应用便可自动更新

        -   针对 Windows Phone 8.1、iOS、Android 和 Windows 用户的文档是一致的：“转到应用商店并安装公司门户。”

        -   用户在安装时可以查看应用并在打开时获取注册说明

        缺点：

        -   用户看到了安装**“公司中心”**的复选框，但没有任何指导说明将用户指引到设备应用列表中的公司门户。

        -   用户在打开公司门户之前无需接受自定义的条款和条件

        -   在以下情况下，你可以继续指引用户注册并在注册过程中安装 ssp.xap：

        **如果公司块从 Windows Phone 访问应用商店，则用户在安装过程中必须安装 ssp.xap。**

        -   如果用户在其 Windows Phone 上未配置 Microsoft 帐户，则他们将不能从应用商店安装公司门户。

        -   如果针对 Windows Phone 注册的现有文档告知他们首先转到设置、工作区，则进行更新以及将用户指引到应用商店可能需要一些时间。

        -   下载中心的 ssp.xap 与应用商店的应用有哪些区别？

        **应用商店的公司门户不需要 Symantec 证书签名便可安装**
        应用商店的公司门户对用户提出条款和条件，但下载中心的 ssp.xap 没有提出 应用商店的公司门户是 .appx 而不是 .xap

        -   我可以获得公司门户文件并将其推送给我的用户，而不是将它们发送到应用商店吗？

        -   是。

        -   可从下载中心为以下操作系统下载公司门户应用：

        **Windows Phone 8.1： [http://go.microsoft.com/fwlink/?LinkId=615799](http://go.microsoft.com/fwlink/?LinkId=615799)**
        Windows Phone 8.0： [http://go.microsoft.com/fwlink/?LinkId=268440](http://go.microsoft.com/fwlink/?LinkId=268440) Windows 8.1： [http://go.microsoft.com/fwlink/?LinkId=615800](http://go.microsoft.com/fwlink/?LinkId=615800) 如果公司没有 Symantec 证书，它们是否仍可以使用 Windows Phone 的 Windows Intune 试用版管理支持工具，并且仍然可以让用户从应用商店安装公司门户？

        是。

        > [!IMPORTANT]
        > 如果你需要进行概念证明，包括 LOB 应用安装、试用版管理工具与公司门户应用商店版本结合使用。 由于注册 Windows Phone 8.1 设备不再需要 Symantec 证书的 AET，但是公司可以使用链接到应用商店中的应用的深层链接来测试应用安装。

        **Windows Phone 的 Windows Intune 试用版管理支持工具仅适用于 Intune 试用订阅。**
        只能使用试用版的管理工具进行测试。 如果试用版管理工具的 Symantec 证书不再可用，或公司获得了自己的用于签名应用的 Symantec 证书，则通过该试用版管理工具的 AET 进行注册的设备必须取消注册并重新注册。 公司是否可以不使用任何 Symantec 证书开始注册，然后再添加更高版本，甚至在已经注册了 Windows Phone 8.1 设备之后？ 是。 即使已经注册了 Windows Phone 8.1 设备，你也可以获取 Symantec 证书、签名 ssp.xap、并将其和 pfx 文件上载。


-   **然后，Intune 将生成 AET。**

    -   **Windows Phone 8.1 设备会在下次同步时（至少 8 小时后）获取 AET。**

        上载 xap 和 pfx 后，至少等待八小时以后再开始部署业务线应用。

-   **Android**

    -   **加密 Android 设备需要多长时间？**

        这主要取决于设备处理器的速度以及内存的总量和使用量，并且不是 Intune 的功能。 iOS

    -   **当使用 Intune 部署 iOS 应用时，如果已上载应用程序的 IPA 和清单文件；该设备是否需要指定的 AppleID 以继续安装？**

        否。 当 Intune 提供位（IPA 已上载到 Intune）时，应用程序进行旁加载且不需要 Apple ID。

    -   **有没有一种方法可在不用获得对 Apple 应用商店的访问权限的情况下，在 iOS 上启用应用安装？**

        没有，但你可以启用应用商店，并在 iOS 上使用“允许的应用”和“阻止的应用”来留意用户的操作。

    -   **旁加载的 LOB 应用不需要 Apple 应用商店的访问权限。**

        是否通过公司门户分发的 Apple 应用商店应用要求最终用户拥有 iTunes 帐户？ 是的，最终用户没有 iTunes 帐户将无法获得应用。

## 我是否可以阻止应用商店？

-   **是，可以，但这会阻止应用商店应用的安装和更新，而不仅仅是由最终用户启动的安装和更新。**

    这意味着从 Intune 部署的任何公共应用商店应用也会失败。

-   **应用程序部署**

    如何添加建议的应用？ 在 Intune 中，这些被称为“精选应用”，并记录在[在 Microsoft Intune 中部署应用](/Intune/Deploy-Use/deploy-apps-in-microsoft-intune.md)中。

## 我是否可以为我要部署的应用获得更多云存储？

-   **适用。**

    你可以在“云存储要求”部分的[部署应用](/Intune/Deploy-Use/deploy-apps.md)中了解 安全 可以通过 Intune 强制实施 BitLocker 吗？

-   **在 Windows 8.1/RT 中，OMA-DM 代理允许你读取（获得）加密状态。**

    不能对其进行设置。 对于 Intune 和其他移动设备管理服务是这样的。 如果使用 BitLocker 加密 Windows 8 平板电脑，我是否可以在用户连续登录失败几次后，强制执行完全设备擦除？

## 对于任何移动设备管理服务（包括 Intune），Windows 8.1/RT 设备上没有完全擦除的选项。

-   **Intune 为这些设备提供了选择性擦除。**

    有关 Intune 中的擦除/选择性擦除的详细信息，请参阅[使用 Microsoft Intune 保护应用和数据](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md) Company Portal

## 我是否可以自定义我的公司门户？

-   **适用。**

    在 Intune 管理员控制台中，针对这些设置，转到“管理员”&gt;“公司门户”。 带 Configuration Manager 的 Microsoft Intune

-   **当我使用带 Intune 的 Configuration Manager 时，在何处管理我的设备？**

    从 Configuration Manager 控制台中管理所有设备，即使安装了 Intune 代理的设备将在 Intune 控制台中显示。 Intune 控制台中将不会显示移动设备。

-   **是否可以在设备上进行选择性擦除？**

    如果你正在使用带 Intune 的 System Center 2012 R2 Configuration Manager 或更高版本，则可以执行选择性擦除，删除公司数据。 有关详细信息，请参阅[使用 Microsoft Intune 保护应用和数据](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md)



<!--HONumber=May16_HO2-->


