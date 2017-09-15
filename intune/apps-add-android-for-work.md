---
title: "将应用分配到 Android for Work 设备"
titlesuffix: Azure portal
description: "使用本主题可从 Google Play for Work 商店同步应用，然后将应用分配到 Android for Work 设备。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 803f1475a220e52a0f7d8a41d58f0a5337ff6555
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>如何使用 Intune 将应用分配到 Android for Work 设备

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可采用与将应用分配到标准 Android 设备不同的方式，将应用分配到 Android for Work 设备。 为 Android for Work 安装的所有应用都来自 Google Play for Work 商店。 登录到该商店，浏览查找所需应用，然后批准它们。
应用随后会出现在 Azure 门户的“获得许可的应用”节点中。 在这里，可以采用与分配任何其他应用相同的方式管理应用的分配。

此外，如果你创建了自己的业务线 (LOB) 应用，则可以按照如下所示分配它们：
- 注册 Google 开发人员帐户，然后通过该帐户将应用发布到 Google Play 商店的专用区域。
- 将应用与 Intune 同步。

## <a name="before-you-start"></a>开始之前

确保已在 Azure 门户的“设备注册”工作负载中，将 Intune 和 Android for Work 配置为协同工作。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>从 Google Play for Work 商店同步应用

1. 转到 [Google Play for Work 商店](https://play.google.com/work)。 通过用于在 Intune 与 Android for Work 之间配置连接的同一个帐户进行登录。
2. 在商店中搜索要使用 Intune 分配的应用。
3. 在所选应用的页面上，选择“批准”。 在此示例中，你选择了 Microsoft Excel 应用。<br>
  ![批准应用示例](media/approve.png)
4. 一个用于该应用的窗口会打开，请你为该应用授予执行各种操作的权限。 选择“批准”才能继续。<br>
  ![批准应用权限示例](media/approve-app-permissions.png)
5. 应用将获得批准并显示在 IT 管理员控制台中。

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>从 Google Play for Work 商店发布，然后同步业务线应用

1. 转到 Google Play 开发人员控制台 [play.google.com/apps/publish](https://play.google.com/apps/publish)。
2. 通过用于在 Intune 与 Android for Work 之间配置连接的同一个帐户进行登录。 如果是首次登录，则必须注册，然后支付费用以成为 Google 开发人员计划的成员。
3. 在控制台中，选择**“添加新应用程序”**。
4. 采用与将任何应用发布到 Google Play 商店相同的方式，上传应用并提供有关应用的信息。 但是，你必须选择设置“仅使此应用程序可供我的组织(<组织名称>)使用”**：<br>
  ![用于仅使此应用可供你的组织使用的选项](media/restrict.png)<br>
此操作可确保应用只能供你的组织使用，而在公开的 Google Play 商店中不可用。
有关如何上传和发布 Android 应用的详细信息，请参阅 [Google 开发人员控制台帮助](https://support.google.com/googleplay/android-developer/answer/113469)。
5. 发布了应用之后，请转到 [Google Play for Work 商店](https://play.google.com/work)。 通过用于在 Intune 与 Android for Work 之间配置连接的同一个帐户进行登录。
6. 在该商店的**“应用”**节点中，验证你是否可以看到已发布的应用。 应用已自动获得批准，可与 Intune 同步。

## <a name="assign-an-android-for-work-app"></a>分配 Android for Work 应用

如果已从该商店批准了应用，但未在“移动应用”工作负荷的“获得许可的应用”节点中看到它，则按照如下所示的步骤强制立即同步：

1. 登录到 Azure 门户中。
2. 在“Intune”边栏选项卡上，选择“移动应用”。
3. 在“移动应用”工作负荷中，选择“设置” > “Android for Work”。
4. 在“Android for Work”边栏选项卡上，选择“立即同步”。
5. 该页还会显示上次同步的时间和状态。

当应用显示在“移动应用”工作负荷的“获得许可的应用”节点中时，你可以[像分配任何其他应用一样分配该应用](/intune-azure/manage-apps/deploy-apps)。 只能将应用分配到用户组。

分配应用之后，它会安装在目标设备上。 不会要求设备的用户批准此安装。

## <a name="manage-android-for-work-app-permissions"></a>管理 Android for Work 应用权限
Android for Work 需要你先在 Google 的托管 Play Web 控制台中批准应用，然后才能将应用同步到 Intune 并分配给用户。  由于 Android for Work 允许以无提示方式将这些应用自动推送到用户的设备，因此你必须代表所有用户接收应用的权限。  最终用户安装应用时将不会看到任何应用权限，因此，你必须阅读并理解这些权限。

当应用开发人员将新版本的应用与更新权限一起发布时，即使你批准了之前的权限，这些权限仍不会被自动接受。 运行旧版本应用的设备仍可以使用它。 但是，在新权限获得批准之前，应用不会升级。 在你批准应用的新权限之前，未安装应用的设备将不会安装应用。

### <a name="how-to-update-app-permissions"></a>如何更新应用权限

定期访问托管的 Google Play 控制台，查看是否有新权限。 可以将 Google Play 配置为当已批准的应用需要新权限时向你和其他人发送电子邮件。 如果分配了应用，但发现设备上未安装此应用，请按照以下步骤检查是否有新权限：

1. 访问 http://play.google.com/work
2. 使用发布和批准应用时所用的 Google 帐户登录。
3. 访问“更新”选项卡，查看是否有应用需要更新。  列出的所有应用都需要新权限，且在应用新权限之前不会进行分配。  

或者，可将 Google Play 配置为自动根据每个应用的情况重新审批应用权限。 



