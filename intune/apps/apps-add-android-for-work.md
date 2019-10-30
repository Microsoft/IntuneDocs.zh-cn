---
title: 将托管 Google Play 应用分配到 Android Enterprise 设备
titleSuffix: Microsoft Intune
description: 了解如何从托管的 Google Play 商店同步应用，以及将应用分配到 Android Enterprise 设备。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3137db9d1ab82ebb99686f8f98aa768dae222caf
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584962"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>使用 Intune 将托管 Google Play 应用添加到 Android Enterprise 设备

托管 Google Play 是 Google 的企业应用商店，并且是适用于 Android Enterprise 的应用程序的唯一供应商。 你可以使用 Intune，通过托管 Google Play 为任何 Android Enterprise 方案（包括工作配置文件、专用和完全托管的注册）安排应用部署。 将托管 Google Play 应用添加到 Intune 的方式不同于为非 Android Enterprise 添加 Android 应用的方式。 商店应用、业务线 (LOB) 应用和 Web 应用在托管 Google Play 中获得批准或添加到托管 Google Play，然后同步到 Intune 中，以便它们显示在客户端应用列表中。 一旦它们显示在客户端应用列表中，就可以像管理任何其他应用一样管理任何托管 Google Play 应用的分配。

Intune 将自动向 Intune 管理控制台添加四个常见的与 Android Enterprise 相关的应用，以便在将 Intune 租户连接到托管 Google Play 后可以轻松配置和使用 Android Enterprise 管理。 四个应用如下：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用于 Android Enterprise 完全托管方案。 此应用在设备注册过程中自动安装到完全托管的设备。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 帮助你使用双因素身份验证登录帐户。 此应用在设备注册过程中自动安装到完全托管的设备。
- **[Intune 公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用于应用保护策略 (APP) 和 Android Enterprise 工作配置文件方案。
- **[托管的主屏幕](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** - 用于 Android Enterprise 专用多应用展台方案。 IT 管理员应创建分配，以便在将用于多应用展台方案的专用设备上安装此应用。

>[!NOTE]
>当最终用户注册其 Android Enterprise 完全托管设备时，将自动安装 Intune 公司门户应用，并且应用程序图标可能对最终用户可见。 如果最终用户尝试启动 Intune 公司门户应用，则最终用户将重定向到 Microsoft Intune 应用，随后将隐藏公司门户应用图标。

## <a name="before-you-start"></a>开始之前
- 确保已将 Intune 租户连接到托管的 Google Play。  有关详细信息，请参阅[如何将 Intune 帐户连接到托管的 Google Play 帐户](../enrollment/connect-intune-android-enterprise.md)。
- 如果打算注册工作配置文件设备，请确保已在 Azure 门户的“设备注册”工作负荷中，将 Intune 和 Android 工作配置文件配置为协同工作  。 有关详细信息，请参阅[注册 Android 设备](../enrollment/android-work-profile-enroll.md)。

>[!NOTE]
>在使用 Microsoft Intune 时，我们建议使用 Microsoft Edge 或 Google Chrome 浏览器。

## <a name="managed-google-play-app-types"></a>“托管 Google Play”应用类型
托管 Google Play 提供三种类型的应用：

- **托管的 Google Play 商店应用** - 已在 Play Store 中正式发布的公共应用。 通过浏览要管理的应用，批准它们，然后将其同步到 Intune 中，在 Intune 中管理这些应用。
- **托管的 Google Play 专用应用** - 这些是由 Intune 管理员发布到托管 Google Play 的 LOB 应用。  这些应用是专用应用，仅适用于 Intune 租户。 这是通过托管 Google Play 和 Android Enterprise 管理和部署 LOB 应用的方式。
- **托管的 Google Play Web 链接** - 包含可部署到 Android Enterprise 设备的 IT 管理员定义的图标的 Web 链接。 它们显示在设备应用列表中的设备上，就像常规应用一样。

## <a name="managed-google-play-store-apps"></a>托管的 Google Play 商店应用
有两种方式可使用 Intune 浏览和批准托管的 Google Play 商店应用：

1. 直接在 Intune 控制台中 - 在 Intune 内托管的视图中浏览和批准商店应用。 这会直接在 Intune 控制台中打开，不需要用户使用其他帐户重新进行身份验证。
1. 在托管的 Google Play 控制台中 - 可以选择直接打开托管的 Google Play 控制台并批准其中的应用。 有关详细信息，请参阅[将托管的 Google Play 应用与 Intune 同步](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)。  这需要使用将 Intune 租户连接到托管 Google Play 所用的帐户进行单独登录。


### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>直接在 Intune 控制台中添加托管的 Google Play 商店应用

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”  窗格中，依次选择“客户端应用”   > “应用”  。
5. 在“应用”窗格中，选择“添加”   。
6. 在“应用类型”  下拉列表框中，选择“托管 Google Play”  。
7. 选择“托管 Google Play - 打开”  可打开托管的 Google Play 目录。
7. 在 Google Play 目录中选择“搜索 Play Store”  。
8. 使用搜索框搜索想要管理的应用。
9. 单击“批准”  以批准托管 Google Play 中的应用，再单击“批准”  以接受应用权限。
10. 选择“批准设置”窗口中的“应用请求新的权限时始终批准”  ，然后单击“保存”  。 如果不选择此选项，将需要在应用开发人员发布更新时手动批准所有新权限。 这将导致应用安装和更新暂停，直到批准该权限。 为此，建议选择此选项以自动批准新权限。 
11. 单击“确定”  以添加已批准的应用。
12. 单击“同步应用”  窗格上的“同步”  ，以与托管 Google Play 服务同步。

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>在托管的 Google Play 控制台中添加托管的 Google Play 商店应用（替代方法）
若要使用 Intune 同步托管 Google Play 应用，而不是直接使用 Intune 添加它，请按照下列步骤操作。

> [!IMPORTANT]
> 下列信息是上文所述的使用 Intune 添加托管 Google Play 应用的备用方法。

1. 转到[托管的 Google Play 应用商店](https://play.google.com/work)。 通过用于在 Intune 与 Android Enterprise 之间配置连接的同一个帐户进行登录。
2. 在应用商店中搜索并选择要使用 Intune 分配的应用。
3. 在显示应用的页面上，选择“批准”  。  
    下面的示例选择了 Microsoft Excel 应用。

    ![托管的 Google Play 应用商店中的“批准”按钮](./media/apps-add-android-for-work/approve.png)

   一个用于该应用的窗口会打开，请你为该应用授予执行各种操作的权限。

4. 选择“批准”，接受应用权限并继续  。

    ![应用权限的“批准”按钮](./media/apps-add-android-for-work/approve-app-permissions.png)

5. 选择一个选项来处理新的应用权限请求，然后选择“保存”  。

    ![用于处理新应用权限请求的选项](./media/apps-add-android-for-work/approve-app-settings.png)

    应用将获得批准并显示在 IT 管理员控制台中。 接下来，可以[将 Android 工作配置文件应用与 Intune 同步](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)。

## <a name="managed-google-play-private-lob-apps"></a>托管 Google Play 专用 (LOB) 应用

有两种方式可将 LOB 应用添加到托管 Google Play：

1. 直接在 Intune 控制台中添加 - 这允许你通过直接在 Intune 中只提交应用 APK 和标题来添加 LOB 应用。 此方法不需要用户拥有 Google 开发人员帐户，也不需要用户支付以开发人员身份注册 Google 的费用。  此方法更简单，大大减少了步骤数，并使 LOB 应用可在 10 分钟内进行管理。
1. 在 Google Play 开发人员控制台中添加 - 如果你拥有 Google 开发人员帐户，或者想要配置仅在 Google Play 开发人员控制台中可用的高级分发功能（例如，添加其他应用屏幕截图），则可以使用 [Google Play 开发人员控制台](https://play.google.com/apps/publish)。 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>托管 Google Play 专用 (LOB) 应用直接在 Intune 控制台中发布

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”  窗格中，依次选择“客户端应用”   > “应用”  。
5. 在“应用”窗格中，选择“添加”   。
6. 在“应用类型”  下拉列表框中，选择“托管 Google Play”  。
7. 选择“托管 Google Play - 打开”  可打开托管的 Google Play 目录。
7. 在 Google Play 目录中选择“专用应用”  。
7. 单击“+”  按钮添加新应用
8. 提交应用的应用标题和 APK 包
9. 单击“创建” 
9. 如果已完成添加应用，则关闭“托管 Google Play”窗格
12. 单击“同步应用”  窗格上的“同步”  ，以与托管 Google Play 服务同步。 请注意，专用应用可能需要几分钟才能同步。如果不是第一次执行同步，请等待几分钟，然后启动新同步。

有关托管 Google Play 专用应用的详细信息（包括常见问题解答），请参阅 Google 的支持文章： https://support.google.com/googleplay/work/answer/9146439

>[!NOTE]
>使用此方法添加的专用应用永远不能变成公共应用。 仅当你确定此应用将始终专用于你的组织时，才使用此发布选项。
  

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>托管 Google Play 专用 (LOB) 应用使用 Google 开发人员控制台发布

1. 通过用于在 Intune 与 Android Enterprise 之间配置连接的同一个帐户登录到 [Google Play 开发人员控制台](https://play.google.com/apps/publish)。  
    如果是首次登录，则必须注册，然后支付费用才能成为 Google 开发人员计划的成员。
2. 在控制台中，选择“添加新应用程序”  。
3. 采用与将任何应用发布到 Google Play 商店相同的方式，上传应用并提供有关应用的信息。 但是，必须选择“仅使此应用程序可供我的组织使用(<组织名称>)”   。

    ![使应用仅可供你的组织使用](./media/apps-add-android-for-work/restrict.png)

    此操作使应用仅可供你的组织使用。 在公共的 Google Play 应用商店中，它将不可用。

    有关上传和发布 Android 应用的详细信息，请参阅 [Google 开发人员控制台帮助](https://support.google.com/googleplay/android-developer/answer/113469)。
4. 在发布应用后，通过用于在 Intune 与 Android Enterprise 之间配置连接的同一个帐户登录到[托管的 Google Play 商店](https://play.google.com/work)。
5. 在该商店的“应用”  节点中，验证是否显示已发布的应用。  
    应用已自动获得批准，可与 Intune 同步。

## <a name="managed-google-play-web-links"></a>托管的 Google Play Web 链接

与其他 Android 应用一样，托管的 Google Play Web 链接可进行安装和管理。 当安装在设备上时，它们将与其所安装的其他应用一起显示在用户的应用列表中。 点击后，它们将在设备的浏览器中启动。

Web 链接将使用 Microsoft Edge 或你选择部署的任何其他浏览器应用打开。 请务必将至少一个浏览器应用部署到设备，以便 Web 链接能够正常打开。 但是，可用于 Web 链接的所有显示选项（全屏、独立和最小 UI）仅适用于 Chrome 浏览器  。 

> [!IMPORTANT]
> 在发布本文档时，存在一个已知的 Google bug，该 bug 会阻止在无 Chrome 浏览器的设备上打开 Web 链接。 Google 已承诺修复此 bug。  当 Microsoft 确认 Google 已发布其修补程序时，将删除此通知。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”  窗格中，依次选择“客户端应用”   > “应用”  。
5. 在“应用”窗格中，选择“添加”   。
6. 在“应用类型”  下拉列表框中，选择“托管 Google Play”  。
7. 选择“托管 Google Play - 打开”  可打开托管的 Google Play 目录。
7. 在 Google Play 目录中选择“Web 应用”  。
7. 单击“+”  按钮添加新应用
7. 输入所需信息，然后单击“创建”  。
7. 如果已完成添加应用，则关闭“托管 Google Play”窗格
12. 单击“同步应用”  窗格上的“同步”  ，以与托管 Google Play 服务同步。 请注意，专用应用可能需要几分钟才能同步。如果不是第一次执行同步，请等待几分钟，然后启动新同步。

## <a name="sync-a-managed-google-play-app-with-intune"></a>将托管的 Google Play 应用与 Intune 同步

如果已从商店批准了应用，但未在“客户端应用”工作负荷中看到该应用，则按照如下所示的步骤强制立即同步  ：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格中，选择“客户端应用”   。
4. 在“客户端应用”工作负荷窗格的“设置”下，选择“托管的 Google Play”    。
5. 在“托管的 Google Play”窗格中，选择“刷新”   。  
    该页会更新上次同步的时间和状态。
6. 在“客户端应用”工作负荷窗格中，选择“应用”   。  
    系统会显示最新可用的托管的 Google Play 应用。

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>将托管 Google Play 应用分配到 Android Enterprise 工作配置文件设备

如果应用显示在“客户端应用”  工作负荷窗格的“应用许可证”  节点中，可以将应用分配到用户组，从而[分配应用，就像分配其他任何应用一样](/intune-azure/manage-apps/deploy-apps)。

分配应用之后，它会安装（或可安装）在用户的目标设备上。 不会要求设备的用户批准此安装。 有关 Android Enterprise 工作配置文件设备的详细信息，请参阅[设置 Android Enterprise 工作配置文件设备的注册](../enrollment/android-work-profile-enroll.md)。 

> [!NOTE] 
> 对于最终用户，在托管的 Google Play 商店中仅显示已分配的应用。 因此，在使用托管 Google Play 设置应用时，管理员需要执行此步骤。

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>将托管 Google Play 应用分配到 Android Enterprise 完全托管设备

[Android Enterprise 完全托管设备](../enrollment/android-fully-managed-enroll.md)是与单个用户关联的企业自有设备，它们专门用于工作而非个人用途。 完全托管设备上的用户可以从其设备上的托管 Google Play 应用中获取其可用的公司应用。

默认情况下，Android Enterprise 完全托管设备不允许员工安装组织未批准的任何应用。 此外，员工将无法根据策略删除任何已安装的应用。 如果希望允许用户访问完整的 Google Play 商店来安装应用，而不只是有权访问托管 Google Play 商店中已批准的应用，则可以将“允许访问 Google Play 商店中的所有应用”设置为“允许”   。 使用此设置，用户可以使用其公司帐户访问 Google Play 商店中的所有应用，但购买可能会受到限制。 你可以通过允许用户将新帐户添加到设备来删除有限的购买限制。 这样一来，最终用户就可以使用个人帐户从 Google Play 商店中购买应用，还可以进行应用内购买。 有关详细信息，请参阅[便于使用 Intune 允许或限制功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md)。 

> [!NOTE]
> 在载入过程中，Microsoft Intune 应用和 Microsoft Authenticator 应用将作为必需的应用安装到所有完全托管的设备上。 自动安装这些应用会提供条件访问支持，Microsoft Intune 应用用户可以查看和解决符合性问题。 

## <a name="manage-android-enterprise-app-permissions"></a>管理 Android Enterprise 应用权限
Android Enterprise 需要用户先在托管的 Google Play Web 控制台中批准应用，然后才能将应用与 Intune 同步并分配给用户。 由于 Android Enterprise 允许以无提示方式将这些应用自动推送到用户的设备，因此必须代表所有用户接受应用权限。 用户安装应用时将不会看到任何应用权限，因此请务必了解这些权限。

当应用开发人员使用新版本的应用更新权限时，即使你批准了之前的权限，系统也不会自动接受这些权限。 运行以前版本应用的设备仍可以使用它。 但是，在新权限获得批准之前，应用不会升级。 在你批准应用的新权限之前，未安装应用的设备将不会安装应用。 

### <a name="update-app-permissions"></a>更新应用权限

定期访问托管的 Google Play 控制台，查看是否有新权限。 可以将 Google Play 配置为当已批准的应用需要新权限时向你和其他人发送电子邮件。 如果分配了应用，但发现设备上未安装此应用，请执行以下步骤，检查是否有新权限：

1. 转到 [Google Play](https://play.google.com/work)。
2. 使用发布和批准应用时所用的 Google 帐户登录。
3. 选择“更新”  选项卡，并检查是否有任何应用需要更新。  
    列出的所有应用都需要新权限，且在应用新权限之前不会进行分配。

或者，可将 Google Play 配置为根据每个应用的情况自动重新审批应用权限。

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Android Enterprise 工作配置文件设备的其他托管 Google Play 应用报告

对于部署到 Android Enterprise 工作配置文件设备的托管 Google Play 应用，可以使用 Intune 查看设备上安装的应用的状态和版本号。 

## <a name="delete-managed-google-play-apps"></a>删除托管 Google Play 应用
必要时，可以从 Microsoft Intune 中删除托管 Google Play 应用。 若要删除托管 Google Play 应用，请在 Azure 门户中打开“Microsoft Intune”，并依次选择“客户端应用”   > “应用”  。 在应用列表中，选择托管 Google Play 应用右侧的省略号 (...)，再从随即显示的列表中选择“删除”  。 从应用列表删除托管的 Google Play 应用时，托管的 Google Play 应用会自动变为未批准状态。

## <a name="android-enterprise-system-apps"></a>Android 企业系统应用

你可以为 [Android Enterprise 专用设备](../enrollment/android-kiosk-enroll.md)或[完全托管设备](../enrollment/android-fully-managed-enroll.md)启用 Android Enterprise 系统应用。 有关添加 Android Enterprise 系统应用的详细信息，请参阅[将 Android Enterprise 系统应用添加到 Microsoft Intune](apps-ae-system.md)。

## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)
