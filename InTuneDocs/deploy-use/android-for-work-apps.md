---
title: "将应用部署到 Android for Work 设备 | Microsoft Docs"
description: "使用本主题可从 Google Play for Work 商店同步应用，然后将应用部署到 Android for Work 设备。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 3b608d42f04b9fce457b6b61587d05ab5d59bb0a
ms.lasthandoff: 03/10/2017


---

# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>如何使用 Intune 将应用部署到 Android for Work 设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

可采用与将应用部署到标准 Android 设备不同的方式，将应用部署到 Android for Work 设备。 为 Android for Work 安装的所有应用都来自 Google Play for Work 商店。 登录到该商店，浏览查找所需应用，然后批准它们。
应用随后会出现在 Intune 控制台的“批量采购的应用”节点中。 在这里，可以采用与部署任何其他应用相同的方式管理应用的部署。

此外，如果你创建了自己的业务线 (LOB) 应用，则可以部署它们。 若要执行该操作，你需要注册 Google 开发人员帐户，该帐户使你可以将应用发布到 Google Play 商店中的专用区域存储，然后将它们与 Intune 同步。

## <a name="before-you-start"></a>开始之前

1. 确保在 Intune 控制台的“管理员”选项卡中将 Intune 和 Android for Work 配置为协同工作。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>从 Google Play for Work 商店同步应用


1. 转到 [Google Play for Work 商店](https://play.google.com/work)。 通过用于在 Intune 与 Android for Work 之间配置连接的同一个帐户进行登录。
2. 在商店中搜索要使用 Intune 部署的应用。
3. 在所选应用的页面上，选择“批准”。 在此示例中，你选择了 Microsoft Excel 应用。<br>
  ![批准应用示例](media/approve.png)
4. 一个用于该应用的窗口会打开，请你为该应用授予执行各种操作的权限。 必须选择“批准”才能继续。<br>
  ![批准应用权限示例](media/approve-app-permissions.png)
5. 片刻之后，你会看到一个确认消息，指示应用已获批准，可在你的 IT 管理员控制台中使用。

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>从 Google Play for Work 商店发布，然后同步业务线应用

1. 转到 Google Play 开发人员控制台 [play.google.com/apps/publish](https://play.google.com/apps/publish)。
2. 通过用于在 Intune 与 Android for Work 之间配置连接的同一个帐户进行登录。 如果是首次登录，则必须注册，然后支付费用以成为 Google 开发人员计划的成员。
3. 在控制台中，选择“添加新应用程序”。
4. 采用与将任何应用发布到 Google Play 商店相同的方式，上传应用并提供有关应用的信息。 但是，你必须选择设置“仅使此应用程序可供我的组织(< *组织名称 *>)使用”****，如下所示。<br>
  ![用于仅使此应用可供你的组织使用的选项](media/restrict.png)<br>
这可确保应用只能供你的组织使用，而在公开的 Google Play 商店中不可用。
有关如何上传和发布 Android 应用的详细信息，请参阅 [Google 开发人员控制台帮助](https://support.google.com/googleplay/android-developer/answer/113469)。
5. 发布了应用之后，请转到 [Google Play for Work 商店](https://play.google.com/work)。 通过用于在 Intune 与 Android for Work 之间配置连接的同一个帐户进行登录。
6. 在该商店的“应用”节点中，验证你是否可以看到已发布的应用。 请注意，它已自动获得批准，可与 Intune 同步。

## <a name="deploy-an-android-for-work-app"></a>部署 Android for Work 应用

如果已从该商店批准了应用，但尚未在“应用”工作区的“批量采购的应用”节点中看到它，则可以强制立即同步，如下所示：

1. 在 [Intune 管理员控制台](https://manage.microsoft.com)中，选择“管理员” > “移动设备管理” > “Android for Work”。
2. 在“Android for Work 移动设备管理安装程序”页上，选择“立即同步”。
3. 该页还会显示上次同步的时间和状态。

当应用显示在“应用”工作区的“批量采购的应用”节点中时，你可以[如同任何其他应用一样部署它](deploy-apps-in-microsoft-intune.md)。 只能将应用部署到用户组。 当前，只能选择“必需”和“卸载”操作。

利用新的分组和目标设定体验，可将应用部署为**可用**。 新预配的 Intune 服务帐户在此功能发布后即可使用它。 现有的 Intune 客户在其租户迁移到 Intune Azure 门户后即可使用此功能。 欢迎现有用户在租户迁移之前创建试用 Intune 帐户来规划和测试此功能。

部署应用之后，它会安装在目标设备上。 不会要求设备的用户进行批准。

## <a name="manage-app-permissions"></a>管理应用权限
Android for Work 需要你先在 Google 的托管 Play Web 控制台中批准应用，然后才能将应用同步到 Intune 并部署给用户。  由于 Android for Work 允许以无提示方式将这些应用自动推送到用户的设备，因此你必须代表所有用户接收应用的权限。  最终用户安装应用时将不会看到任何应用权限，因此你必须阅读并理解这些权限。

当应用开发人员将新版本的应用与更新权限一起发布时，即使你批准了之前的权限，这些权限仍不会被自动接受。 运行旧版本应用的设备仍可使用应用，但在批准新权限前将无法升级应用。 在你批准应用的新权限之前，未安装应用的设备将无法安装应用。

### <a name="how-to-update-app-permissions"></a>如何更新应用权限

需定期访问托管的 Google Play 控制台，查看是否有新权限。 如果部署了应用，但发现设备上未安装此应用，请按照以下步骤检查是否有新权限：

1. 访问 http://play.google.com/work
2. 使用发布和批准应用时所用的 Google 帐户登录。
3. 访问“更新”选项卡，查看是否有应用需要更新。  列出的所有应用都需要新权限，且在无新权限之前不会部署。  

