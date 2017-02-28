---
title: "管理来自适用于企业的 Windows 应用商店的应用 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何从适用于企业的 Windows 应用商店将应用同步到 Intune，并对其进行分配和跟踪。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: b213fcaae8f17af412687d01df6ea27b39b3edb9
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理从适用于企业的 Windows 应用商店中购买的应用

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


你可以在[适用于企业的 Windows 应用商店](https://www.microsoft.com/business-store)中为你的组织查找和购买应用，可以购买单个或批量购买。 通过将此应用商店连接到 Microsoft Intune，你可以在 Intune 门户中管理批量购买的应用。 例如：
* 你可以将从应用商店中购买的应用列表与 Intune 同步。
* Intune 管理控制台中将显示已同步的应用，可以像分配所有其他应用那样分配这些应用。
* 你可以跟踪可用许可证的数量以及正在 Intune 管理控制台中使用的许可证数量。
* 如果可用许可证数量不足，则 Intune 将阻止应用的部署和安装。

## <a name="before-you-start"></a>开始之前
从适用于企业的 Windows 应用商店同步并部署应用之前，请查看以下信息：
* 你必须将 Intune 配置为你的组织的移动设备管理机构。
* 必须已在适用于企业的 Windows 应用商店中注册帐户。
* 一旦将适用于企业的 Windows 应用商店帐户与 Intune 关联，将来你将无法更改为其他帐户。
* 无法在 Intune 中手动添加或删除从应用商店购买的应用。 这些应用只能与适用于企业的 Windows 应用商店同步。
* Intune 只同步你已从适用于企业的 Windows 应用商店中购买的联机已授权应用。
* 设备必须已加入 Active Directory 域服务或工作区才可使用此功能。
* 已注册的设备必须使用 Windows 10 的 1511 版本或更高版本。

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>将适用于企业的 Windows 应用商店帐户与 Intune 相关联
在 Intune 控制台中启用同步之前，必须将你的应用商店帐户配置为将 Intune 作为一种管理工具使用：
1. 确保使用与登录 Intune 相同的租户帐户登录企业应用商店。
2. 在企业应用商店中，选择**设置** > **管理工具**。
3. 在“管理工具”页上选择“添加管理工具”，然后选择“Microsoft Intune”。

> [!NOTE]
> 使用多个管理工具部署适用于企业的 Windows 应用商店时，以前只能将一个管理工具与适用于企业的 Windows 应用商店相关联。 现在可以将多个管理工具与应用商店相关联，例如 Intune 和 Configuration Manager。

现在可以继续，并在 Intune 控制台中设置同步。

## <a name="configure-synchronization"></a>配置同步

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
1. 在“移动应用”边栏选项卡上，选择“设置” > “适用于企业的 Windows 应用商店”。
2. 单击“启用”。
3. 如果尚未这样做，请单击适用于企业的 Windows 应用商店的注册链接，并按之前详述的步骤关联帐户。
5. 在“语言”下拉列表中，选择适用于企业的 Windows 应用商店的应用在 Intune 门户中显示时使用的语言。 无论以何种语言显示，都会以最终用户的语言（如果有）进行安装。
6. 单击“同步”，将从 Windows 应用商店购买的应用同步到 Intune。

## <a name="synchronize-apps"></a>同步应用

1. 在“管理应用”工作负荷中，选择“设置” > “适用于企业的 Windows 应用商店”。
2. 单击“同步”，将从 Windows 应用商店购买的应用同步到 Intune。

## <a name="assign-apps"></a>分配应用

分配应用商店中应用的方式与分配任何其他 Intune 应用的方式相同。 有关详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](deploy-apps.md)。 但是，不是从“所有应用”页面分配应用，而是从“获得许可的应用”页面分配应用。

分配适用于企业的 Windows 应用商店的应用时，安装此应用的每个用户都会使用&1; 个许可证。 如果使用了部署应用的所有可用许可证，则你将无法再部署任何副本。 必须执行下列操作之一：
* 从一些设备上卸载应用。
* 减小当前部署的范围，仅针对具有足够许可证的用户。
* 从适用于企业的 Windows 应用商店中购买应用的更多副本。

> [!Important]
> 已部署的应用程序仅可用于最初注册了该设备的用户。 其他用户不能访问该应用。

