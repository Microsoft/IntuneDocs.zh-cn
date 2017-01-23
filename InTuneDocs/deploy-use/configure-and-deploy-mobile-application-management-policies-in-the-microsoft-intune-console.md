---
title: "在 Intune 控制台中配置 MAM 策略 | Microsoft Docs"
description: "Microsoft Intune 中的移动应用管理策略让你可以修改你所部署的应用的功能，以帮助它们符合你的公司合规性和安全策略。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: f7504657f5fb2d73242f25f2f059c8c4e7ab1547


---

# <a name="configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console"></a>配置和部署 Microsoft Intune 控制台中的移动应用程序管理策略

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 中的移动应用管理 (MAM) 策略让你可以修改你所部署的应用的功能，以帮助它们符合你的公司合规性和安全策略。 例如，你可以限制在托管的应用内进行剪切、复制和粘贴操作，或配置应用以在托管的浏览器内打开所有 Web 链接。

移动应用管理策略支持：

-   运行 Android 4 和更高版本的设备。

-   运行 iOS 8.0 及更高版本的设备。

> [!TIP]
> 移动应用程序管理策略支持向 Intune 注册的设备。
>
> 如果你正在查找有关如何为不受 Intune 管理的设备创建应用管理策略的信息，请参阅[通过 Microsoft Intune 使用移动应用管理策略保护应用数据](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。

与其他 Intune 策略不同，你不会直接部署移动应用程序管理策略。 而是将该策略与你想要进行限制的应用相关联。 当应用部署并安装在设备上时，你指定的设置将起作用。

若要将限制应用到应用，该应用必须包含 Microsoft Intune App SDK。 可通过三种方法获取此类应用：

-   **使用策略托管的应用**。 策略托管应用内置了应用 SDK。 要添加此类型的应用，你可以从 iTunes 应用商店或 Google Play 等应用商店指定应用的链接。 对于此类应用，无需进一步的处理。 有关详细信息，请参阅 [list of apps that you can use with Microsoft Intune mobile application management policies](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps)（可配合 Microsoft Intune 移动应用管理策略使用的应用的列表）。

-   **使用已包装的应用**。 已包装的应用 – 使用 Microsoft Intune App Wrapping Tool 对应用进行重新封装，以将应用 SDK 包括在内。 该工具通常用于处理公司内部开发的应用。 无法用于处理从应用商店下载的应用。 有关详细信息，请参阅[使用 Microsoft Intune App Wrapping Tool 为移动应用管理准备 iOS 应用](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)和[使用 Microsoft Intune App Wrapping Tool 为移动应用管理准备 Android 应用](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)。

- **编写自己的应用，其中包含 Intune App SDK**。 Intune App SDK 允许你将应用管理功能合并到你正在编写的应用。 有关详细信息，请参阅 [Intune App SDK 概述](/intune/develop/intune-app-sdk)。

有关是要选择 App Wrapping Tool 还是 Intune App SDK 的帮助信息，请参阅[决定如何使用 Microsoft Intune 为移动应用管理准备应用](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)。

某些托管应用（比如用于 iOS 和 Android 的 Outlook 应用）支持*多身份*。 这意味着 Intune 仅对公司帐户或应用中的数据应用管理设置。

例如，使用 Outlook 应用：

-   如果用户配置公司和个人电子邮件帐户，则 Intune 仅对公司帐户应用管理设置，并不管理个人帐户。

-   如果设备已停用或已取消注册，则仅从设备中删除公司的 Outlook 数据。

-   公司帐户必须与用于向 Intune 注册设备的帐户相同。

> [!TIP]
> 如果要将 Intune 与 Configuration Manager 结合使用，请参阅[如何使用 Configuration Manager 中的移动应用程序管理策略控制应用](https://technet.microsoft.com/library/mt131414.aspx)。

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>创建和部署具有移动应用程序管理策略的应用

-   **步骤 1：**获取指向策略托管应用的链接、创建已包装的应用，或使用 Intune App SDK 编写已启用 MAM 的应用。

-   **步骤 2：** 将应用发布到你的云存储空间。

-   **步骤 3：** 创建移动应用程序管理策略。

-   **步骤 4：** 将应用与移动应用管理策略相关联，然后部署该应用。

-   **步骤 5：** 监视应用部署。

## <a name="step-1-get-the-link-to-a-policy-managed-app-create-a-wrapped-app-or-use-the-intune-app-sdk-to-write-a-mam-enabled-app"></a>步骤 1：获取指向策略托管应用的链接、创建已包装的应用，或使用 Intune App SDK 编写已启用 MAM 的应用

从应用商店查找并记录你想要部署的策略托管应用的 URL。 例如，Microsoft Word for iPad 应用 的 URL 是 **https://itunes.apple.com/cn/app/microsoft-word-for-ipad/id586447913?mt=8**。


## <a name="step-2-publish-the-app-to-your-cloud-storage-space"></a>步骤 2：将应用发布到你的云存储空间
发布托管的应用时，过程有所差异，具体取决于你发布的是策略托管的应用，还是使用 Microsoft Intune App Wrapping Tool for iOS 进行处理的应用。

#### <a name="to-publish-a-policy-managed-app"></a>若要发布策略托管的应用

1.  当你准备好将应用上传到云存储空间时，请按照[在 Microsoft Intune 中为移动设备添加应用](add-apps-for-mobile-devices-in-microsoft-intune.md)中的说明进行操作。

2.  对于 iOS 应用，在“**选择如何将此软件提供给设备**”下选择“**应用商店的托管 iOS 应用**”。

    对于 Android 应用。选择 **“外部链接”**。

3.  在 **“指定 URL”**下，输入你之前记录的托管应用的 URL。

上载完成后，你会看到已上载的应用的“**软件属性**”页面上的“**应用管理策略**”为“**是**”。

验证应用上载成功后，继续步骤 3。

#### <a name="to-publish-an-app-that-was-processed-through-the-microsoft-intune-app-wrapping-tool"></a>发布通过 Microsoft Intune App Wrapping Tool 处理的应用

1.  当你准备好将应用上传到云存储空间时，请按照[在 Microsoft Intune 中为移动设备添加应用](add-apps-for-mobile-devices-in-microsoft-intune.md)中的说明进行操作。

2.  选择“**选择如何将此软件提供给设备**”下的“**软件安装程序**”。

3.  选择“软件安装程序文件类型”下的“iOS 应用包（*.ipa 文件）”。

上载完成后，你会看到已上载的应用的“**软件属性**”页面上的“**应用管理策略**”为“**是**”。

验证应用上载成功后，继续步骤 3。

## <a name="step-3-create-a-mobile-application-management-policy"></a>步骤 3：创建移动应用程序管理策略

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)，选择“策略”&gt;“概述”&gt;“添加策略”。

2.  配置并部署以下“**软件**”策略之一，这取决于你想要为其配置应用的设备类型：

    -   **移动应用程序管理策略 （Android 4 和更高版本）**

    -   **移动应用程序管理策略（iOS 8.0 及更高版本）**

    你可以使用建议的设置，或对设置进行自定义。 有关详细信息，请参阅[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  根据需要配置下列设置。 该选项可能有所差异，这取决于你配置策略的设备类型。

|设置名|详细信息|
    |---------|--------------------|
    |**Name**|为此策略指定名称。|
    |**描述**|（可选）为此策略指定描述。|
    |**限制显示在企业托管浏览器内的 Web 内容**|如果启用此设备，应用内的任何链接都将在托管浏览器中打开。 要使此选项起作用，你必须将此应用部署到设备。|
    |**“阻止 Android 备份”** 或 **“阻止 iTunes 和 iCloud 备份”**|此设置禁止从应用备份任何信息。|
    |**允许应用向其他应用传送数据**|此设置指定该应用可以发送数据的应用。 你可以选择不允许将数据传输到任何应用、仅允许传输到其他托管的应用或允许传输到任何应用。 <br /><br />例如，不允许数据传输时，即把数据传输限制为短信发送、分配图片到联系人以及发布到 Facebook 或 Twitter 等服务。<br /><br />对于 iOS 设备，若要防止在托管和非托管应用之间传输文档，你也必须配置并部署禁用 **“允许在其他非托管应用中使用托管文档”**设置的移动设备安全策略。 如果你选择仅允许传输到其他托管的应用，则 Intune PDF 和图像查看器（如果已部署）将用于打开各自类型的内容。<br /><br />此外，如果你将此选项设置为“策略托管应用”或“无”，则将阻止允许 Spotlight Search 在应用内搜索数据的 iOS 9 功能。<br><br>此设置不控制移动设备上的“打开方式”功能的使用。 要管理“打开方式”，请参阅[使用 Microsoft Intune 管理 iOS 应用之间的数据传输](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)。|
    |**允许应用从其他应用接收数据**|此设置指定此应用可以接收其数据的应用。 你可以选择不允许从任何应用进行数据传输，仅允许从其他托管应用进行传输或允许从任何应用进行传输。<br /><br />当用户从不受移动应用管理策略管理的应用访问数据时，数据将被视为公司数据并受策略保护。 这适用于支持多身份的 iOS 应用（其中 Intune 仅将管理设置应用于公司帐户或应用中的数据）。 或者，这适用于已应用移动应用管理策略的已注册设备。|
    |**防止“另存为”**|此设置禁止使用“**另存为**”选项将数据保存到使用此策略的任何应用中的个人云存储位置（例如 OneDrive 或 Dropbox）。|
    |**限制剪切、复制和粘贴到其他应用程序**|此设置指定应用使用剪切、复制和粘贴操作的方法。 选择：<br /><br />**已阻止**。 不允许在此应用和其他应用间进行剪切、复制和粘贴操作。<br /><br />**策略托管应用**。 仅允许在此应用和其他托管的应用之间进行剪切、复制和粘贴操作。<br /><br />**带粘贴的策略托管应用**。 仅允许从此应用剪切或复制的数据粘贴到其他托管应用。 允许将剪切或复制自任何应用的数据粘贴至此应用。<br /><br />**任何应用**。 不限制针对此应用执行的剪切、复制和粘贴操作。<br /><br />若要在托管的应用之间复制和粘贴数据，那么两个应用必须都配置了“**策略托管的应用**”或“**带粘贴的策略托管应用**”设置。|
    |**访问需要简单 PIN**|此设置要求用户输入他们指定 PIN 以使用此应用。 将会要求用户在首次运行该应用时进行设置。|
    |**重置 PIN 前的尝试次数**|指定输入 PIN 码的尝试次数，达到该次数后用户必须重置 PIN。|
    |**访问需要公司凭据**|此设置要求用户在访问应用前必须输入他们的公司登录信息。|
    |**访问要求设备符合公司策略**|此设置仅允许设备在未越狱或获取根权限时使用此应用。|
    |**在一定时间后重新检查访问要求（分钟）**|在“**超时**”字段中，指定应用打开后重新检查应用访问要求前的时间段。|
    |**脱机宽限期**|如果设备离线，指定应用重新检查访问要求前的时间段。|
    |**加密应用数据**|此设置指定与此应用相关的所有数据均将加密。 这包括外部存储的数据，如在 SD 卡中的数据。<br /><br />**适用于 iOS 的加密**<br /><br />对于与 Intune 移动应用管理策略关联的应用，通过 OS 提供的设备级加密对静态数据进行加密。 通过由 IT 管理员设置的设备 PIN 策略启用。 需要 PIN 时，数据将根据移动应用管理策略的设置进行加密。 正如 Apple 文档所述，[iOS 所使用的模块经过了 FIPS 140-2 的认证](http://support.apple.com/en-us/HT202739)。<br /><br />**适用于 Android 的加官**<br /><br />对于与 Intune 移动应用管理策略关联的应用，加密由 Microsoft 提供。 数据在文件 I/O 操作期间同步加密。  设备存储中的内容将始终被加密。 加密方法没有获得 FIPS 140-2 认证。|
    |**“阻止屏幕捕捉”** （仅限于 Android 设备）|此设置指定在使用该应用时，阻止设备的屏幕捕捉功能。|

4. 完成后，请选择“保存策略”。

新的策略将在“**策略**”工作区的“**配置策略**”节点处显示。

## <a name="step-4-associate-the-app-with-a-mobile-application-management-policy-and-then-deploy-the-app"></a>步骤 4：将应用与移动应用管理策略相关联，然后部署该应用
确保你选择“**管理部署**”对话框的“**移动应用管理**”页面上的移动应用管理策略，以关联策略和应用。

有关详细信息，请参阅[在 Microsoft Intune 中部署应用](deploy-apps.md)。

> [!IMPORTANT]
> 如果从 Intune 取消注册设备，则策略不会从应用中删除。 在卸载并重新安装了该应用后，应用了策略的任何应用均将保留策略设置。

### <a name="what-to-do-when-an-app-is-already-deployed-on-devices"></a>应用已部署在设备上时应该如何操作
也存在这样一种情况：当你部署应用时，目标用户或设备之一已经安装了非托管版本的应用。 例如，用户从应用商店安装了 Microsoft Word。

在这种情况下，必须要求用户手动卸载非托管的版本，才能安装所配置的托管版本。

但是，对于运行 iOS 9 及更高版本的设备，Intune 将自动要求用户提供许可以接管现有应用。 如果用户同意，则应用将由 Intune 管理，并将应用与该应用关联的任何移动应用管理策略。

> [!TIP]
> 如果设备处于监督模式，则 Intune 无需要求用户提供许可即可接管现有应用。

## <a name="step-5-monitor-the-app-deployment"></a>步骤 5：监视应用部署
创建并部署与某移动应用管理策略关联的应用后，使用以下步骤监视应用并解决任何策略冲突的问题。

#### <a name="to-view-the-status-of-the-deployment"></a>若要查看订阅的状态

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“组”&gt;“概述”。

2.  执行以下步骤之一：

    -   选择“**所有用户**”，然后双击你想要检查其设备的用户。 在“**用户属性**”页面上，选择“**设备**”，然后双击你想要检查的设备。

    -   选择“所有设备”&gt;“所有移动设备”。 在“**设备组属性**”页面上，选择“**设备**”，然后双击你想要检查的设备。

3.  在“移动设备属性”页中选择“策略”以查看已部署至设备的移动应用程序管理策略列表。

4.  选择你想要查看的移动应用程序管理策略的状态。 你可以在底部窗格查看策略详细信息，并展开其节点以显示其设置。

5.  在各个移动应用管理策略的“**状态**”列下，将显示“**符合**”、“**符合(待定)**”或“**错误**”。 如果所选择的策略有一项或多项冲突设置，将会在该字段中显示“**错误**”。

6.  发现了冲突后，你可以将冲突策略设置修改为使用相同设置，或对应用和用户仅部署一个策略。

### <a name="how-policy-conflicts-are-resolved"></a>如何解决策略冲突
如果在第一次部署到用户或设备时出现移动应用管理策略冲突，则冲突中指定的设置值将从部署到应用的策略中删除。 应用将使用内置冲突值。

如果在后续部署到应用或用户时出现移动应用管理策略冲突，则冲突的指定设备值将不会更新到部署到应用的移动应用管理策略。 应用将使用该设置的现有值。

如果设备或用户收到两个冲突策略，则适用以下行为：

-   如果策略已经部署到设备，则现有策略设置不会被覆盖。

-   如果尚无策略部署到设备，并且两个冲突设置已经部署，则将使用设备内的默认设置。



<!--HONumber=Dec16_HO5-->


