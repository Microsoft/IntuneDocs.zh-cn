---
title: 将托管 Google Play 应用分配到 Android 企业设备
titleSuffix: Microsoft Intune
description: 了解如何从托管的 Google Play 应用商店同步应用，以及将应用分配到 Android 企业设备。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ad07252ccf10fefdd1c753ab103eb91a2789c39
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587342"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>使用 Intune 将托管 Google Play 应用添加到 Android 企业设备

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android 企业是适用于 Android 工作配置文件设备、专用/展台设备和完全托管设备的程序。 对于 Android 工作配置文件设备，Android 企业是一组功能和服务，它将分隔个人应用和数据与工作应用和数据。 用户将其 Android 设备用于工作时，Android 企业将提供额外的管理选项和隐私。 Intune 可帮助用户将应用和设置部署到 Android 工作配置文件设备，确保将工作信息和个人信息分开。 在 Android 工作配置文件设备上安装的所有应用都来自托管 Google Play 应用商店。 可采用与将应用分配到标准 Android 设备不同的方式，将应用分配到 Android 工作配置文件设备。 登录到该商店，浏览查找所需应用，然后批准它们。 然后，该应用会显示在 Azure 门户的“许可的应用”节点中，可以像管理任何其他应用一样管理应用的分配。

此外，如果你创建了自己的业务线 (LOB) 应用，则可以按如下所示分配它们：
- 注册 Google 开发人员帐户，然后通过该帐户将应用发布到 Google Play 商店的专用区域。
- 将应用与 Intune 同步。

## <a name="before-you-start"></a>开始之前

确保已在 Azure 门户的“设备注册”工作负载中，将 Intune 和 Android 工作配置文件配置为协同工作。 有关详细信息，请参阅[注册 Android 设备](android-work-profile-enroll.md)。

>[!NOTE]
>在使用 Microsoft Intune 时，我们建议使用 Microsoft Edge 或 Google Chrome 浏览器。

## <a name="managed-google-play-app-type"></a>“托管 Google Play”应用类型
使用“托管 Google Play”应用类型，可以专门将[托管 Google Play 应用](https://play.google.com/work/search?q=microsoft&c=apps)添加到 Intune。 作为 Intune 管理员，现在可以在 Intune 中浏览、搜索、批准、同步和分配已批准的托管 Google Play 应用。  不再需要单独转到托管 Google Play 控制台，也不再需要重新进行身份验证。

> [!NOTE]
> 若要使用 Intune 同步托管 Google Play 应用，请参阅[使用 Intune 同步托管 Google Play 应用](apps-add-android-for-work.md#synchronize-a-managed-google-play-app-with-intune-alternative)

## <a name="add-a-managed-google-play-app-using-intune"></a>使用 Intune 添加托管 Google Play 应用

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。  
    Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，依次选择“客户端应用” > “应用”。
5. 在“应用”窗格中，选择“添加”。
6. 在“应用类型”下拉列表框中，选择“托管 Google Play”。
7. 选择“托管 Google Play - 批准”可打开托管的 Google Play 目录。
8. 使用搜索框搜索想要添加的应用。
9. 单击“批准”以批准托管 Google Play 中的应用，再单击“批准”以接受应用权限。
10. 选择“批准设置”窗口中的“应用请求新的权限时始终批准”，然后单击“保存”。 如果不选择此选项，将需要在应用开发人员发布更新时手动批准所有新权限。  这将导致应用安装和更新暂停，直到批准该权限。 为此，建议选择此选项以自动批准新权限。 
11. 单击“确定”以添加已批准的应用。
12. 单击“同步应用”窗格上的“同步”，以与托管 Google Play 服务同步。

## <a name="synchronize-a-managed-google-play-app-with-intune-alternative"></a>使用 Intune 同步托管 Google Play 应用（备用）
若要使用 Intune 同步托管 Google Play 应用，而不是直接使用 Intune 添加它，请按照下列步骤操作。

> [!IMPORTANT]
> 下列信息是上文所述的使用 Intune 添加托管 Google Play 应用的备用方法。

### <a name="synchronize-an-app-from-the-managed-google-play-store"></a>从托管的 Google Play 应用商店同步应用

1. 转到[托管的 Google Play 应用商店](https://play.google.com/work)。 通过用于在 Intune 与 Android 企业之间配置连接的同一个帐户进行登录。
2. 在应用商店中搜索并选择要使用 Intune 分配的应用。
3. 在显示应用的页面上，选择“批准”。  
    下面的示例选择了 Microsoft Excel 应用。

    ![托管的 Google Play 应用商店中的“批准”按钮](media/approve.png)

   一个用于该应用的窗口会打开，请你为该应用授予执行各种操作的权限。

4. 选择“批准”，接受应用权限并继续。

    ![应用权限的“批准”按钮](media/approve-app-permissions.png)

5. 选择一个选项来处理新的应用权限请求，然后选择“保存”。

    ![用于处理新应用权限请求的选项](media/approve-app-settings.png)

    应用将获得批准并显示在 IT 管理员控制台中。 接下来，可以[将 Android 工作配置文件应用与 Intune 同步](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)。

### <a name="sync-a-managed-google-play-app-with-intune"></a>将托管的 Google Play 应用与 Intune 同步

如果已从商店批准了应用，但未在“客户端应用”工作负荷的“获得许可的应用”节点中看到该应用，则按照如下所示的步骤强制立即同步：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“客户端应用”。
4. 在“客户端应用”工作负荷窗格的“设置”下，选择“托管的 Google Play”。
5. 在“托管的 Google Play”窗格中，选择“刷新”。  
    该页会更新上次同步的时间和状态。
6. 在“客户端应用”工作负荷窗格中，选择“应用”。  
    系统会显示最新可用的托管的 Google Play 应用。

## <a name="assigning-the-managed-google-play-app"></a>分配托管 Google Play 应用

如果应用显示在“客户端应用”工作负载窗格的“应用许可证”节点中，可以将应用分配到用户组，从而[分配应用，就像分配其他任何应用一样](/intune-azure/manage-apps/deploy-apps)。

分配应用之后，它会安装在目标设备上。 不会要求设备的用户批准此安装。

## <a name="manage-android-enterprise-app-permissions"></a>管理 Android 企业应用权限
Android 企业需要用户先在托管的 Google Play Web 控制台中批准应用，然后才能将应用与 Intune 同步并分配给用户。 由于 Android 企业允许以无提示方式将这些应用自动推送到用户的设备，因此必须代表所有用户接受应用权限。 用户安装应用时将不会看到任何应用权限，因此请务必了解这些权限。

当应用开发人员使用新版本的应用更新权限时，即使你批准了之前的权限，系统也不会自动接受这些权限。 运行以前版本应用的设备仍可以使用它。 但是，在新权限获得批准之前，应用不会升级。 在你批准应用的新权限之前，未安装应用的设备将不会安装应用。

### <a name="update-app-permissions"></a>更新应用权限

定期访问托管的 Google Play 控制台，查看是否有新权限。 可以将 Google Play 配置为当已批准的应用需要新权限时向你和其他人发送电子邮件。 如果分配了应用，但发现设备上未安装此应用，请执行以下步骤，检查是否有新权限：

1. 转到 [Google Play](https://play.google.com/work)。
2. 使用发布和批准应用时所用的 Google 帐户登录。
3. 选择“更新”选项卡，并检查是否有任何应用需要更新。  
    列出的所有应用都需要新权限，且在应用新权限之前不会进行分配。

或者，可将 Google Play 配置为根据每个应用的情况自动重新审批应用权限。

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>从托管的 Google Play 应用商店中使用业务线应用

1. 通过用于在 Intune 与 Android 企业之间配置连接的同一个帐户登录到 [Google Play 开发人员控制台](https://play.google.com/apps/publish)。  
    如果是首次登录，则必须注册，然后支付费用才能成为 Google 开发人员计划的成员。
2. 在控制台中，选择“添加新应用程序”。
3. 采用与将任何应用发布到 Google Play 商店相同的方式，上传应用并提供有关应用的信息。 但是，必须选择“仅使此应用程序可供我的组织使用(<组织名称>)”。

    ![使应用仅可供你的组织使用](media/restrict.png)

    此操作使应用仅可供你的组织使用。 在公共的 Google Play 应用商店中，它将不可用。

    有关上传和发布 Android 应用的详细信息，请参阅 [Google 开发人员控制台帮助](https://support.google.com/googleplay/android-developer/answer/113469)。
4. 在发布应用后，通过用于在 Intune 与 Android 企业之间配置连接的同一个帐户登录到[托管的 Google Play 应用商店](https://play.google.com/work)。
5. 在该商店的“应用”节点中，验证是否显示已发布的应用。  
    应用已自动获得批准，可与 Intune 同步。

## <a name="delete-managed-google-play-apps"></a>删除托管 Google Play 应用
必要时，可以从 Microsoft Intune 中删除托管 Google Play 应用。 若要删除托管 Google Play 应用，请在 Azure 门户中打开“Microsoft Intune”，并依次选择“客户端应用” > “应用”。 在应用列表中，选择托管 Google Play 应用右侧的省略号 (...)，再从随即显示的列表中选择“删除”。 从应用列表删除托管的 Google Play 应用时，托管的 Google Play 应用会自动变为未批准状态。

## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)
