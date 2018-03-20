---
title: "管理来自适用于企业的 Microsoft 应用商店的应用"
titlesuffix: Microsoft Intune
description: "了解如何从适用于企业的 Microsoft Store 将应用同步到 Intune，并对其进行分配和跟踪。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa5e3b5559c5c17ea726b26f1c1f56ef37cfe0ae
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理从适用于企业的 Microsoft 应用商店中购买的应用

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


可在[适用于企业的 Microsoft 应用商店](https://www.microsoft.com/business-store)中为组织查找和购买应用（单个或批量）。 通过将此应用商店与 Microsoft Intune 相连，可以在 Azure 门户中管理批量购买的应用。 例如：
* 你可以将从应用商店中购买的应用列表与 Intune 同步。
* Intune 管理控制台中将显示已同步的应用，可以像分配所有其他应用那样分配这些应用。
* 你可以跟踪可用许可证的数量以及正在 Intune 管理控制台中使用的许可证数量。
* 如果可用许可证数量不足，Intune 将阻止应用的分配和安装。
* 用户离开企业或管理员删除用户和用户设备时，由适用于企业的 Microsoft Store 托管的应用会自动撤销许可证。

## <a name="before-you-start"></a>开始之前

从适用于企业的 Microsoft 应用商店同步并分配应用之前，请查看以下信息：

- 将 Intune 配置为组织的移动设备管理机构。
- 必须已在适用于企业的 Microsoft 应用商店中注册帐户。
- 将适用于企业的 Microsoft Store 帐户与 Intune 关联后，该帐户将来无法更改为其他帐户。
- 无法在 Intune 中手动添加或删除从应用商店购买的应用。 这些应用只能与适用于企业的 Microsoft 应用商店同步。
- 从适用于企业的 Microsoft Store 中购买的联机和脱机授权应用都会同步到 Intune 门户。 然后，可以将这些应用部署到设备组或用户组。 
- 在线应用安装由应用商店管理。
- 免费的脱机应用也可同步到 Intune。 这些应用由 Intune 安装，而不是由应用商店安装。
- 设备必须已加入 Active Directory 域服务或工作区才可使用此功能。
- 已注册的设备必须使用 Windows 10 的 1511 版本或更高版本。

此外，从适用于企业的 Microsoft Store 同步的相关集和脱机授权应用现在会合并到 UI 的单个应用条目中。 各个包中的所有部署详细信息都会迁移到单个条目。 要在 Azure 门户中查看相关集，请从“移动应用”边栏选项卡中选择“应用许可证”。

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>将适用于企业的 Microsoft 应用商店帐户与 Intune 关联
在 Intune 控制台中启用同步之前，必须将你的应用商店帐户配置为将 Intune 作为一种管理工具使用：
1. 确保使用与登录 Intune 相同的租户帐户登录企业应用商店。
2. 在企业应用商店中，选择**设置** > **管理工具**。
3. 在“管理工具”页上选择“添加管理工具”，然后选择“Microsoft Intune”。

> [!NOTE]
> 以前只能将一个用于分配应用的管理工具关联到适用于企业的 Microsoft 应用商店。 现在可以将多个管理工具与应用商店相关联，例如 Intune 和 Configuration Manager。

现在可以继续，并在 Intune 控制台中设置同步。

## <a name="configure-synchronization"></a>配置同步

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在 Intune 窗格中，选择“移动应用”。
1. 在“移动应用”窗格上，选择“设置” > “适用于企业的 Microsoft Store”。
2. 单击“启用”。
3. 如果尚未这样做，请单击适用于企业的 Microsoft 应用商店的注册链接，并按之前详述的步骤关联帐户。
5. 在“语言”下拉列表中，选择适用于企业的 Microsoft Store 中的应用在 Azure 门户中的显示语言。 无论以何种语言显示，都会以最终用户的语言（如果有）进行安装。
6. 单击“同步”，将从 Microsoft 应用商店购买的应用同步到 Intune。

## <a name="synchronize-apps"></a>同步应用

1. 在“移动应用”工作负荷中，选择“设置” > “适用于企业的 Microsoft 应用商店”。
2. 单击“同步”，将从 Microsoft 应用商店购买的应用同步到 Intune。

## <a name="assign-apps"></a>分配应用

分配应用商店中应用的方式与分配任何其他 Intune 应用的方式相同。 有关详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。 但是，不是从“所有应用”页面分配应用，而是从“获得许可的应用”页面分配应用。

脱机应用可面向用户组、设备组或同时具有用户和设备的组。
可为设备上的特定用户或所有用户安装脱机应用。 


分配适用于企业的 Microsoft 应用商店的应用时，安装此应用的每个用户都会使用一个许可证。 如果使用了分配应用的所有可用许可证，则无法再分配任何副本。 请执行下列操作之一：
* 从一些设备上卸载应用。
* 减小当前分配的范围，仅针对具有足够许可证的用户。
* 从适用于企业的 Microsoft 应用商店中购买应用的更多副本。


