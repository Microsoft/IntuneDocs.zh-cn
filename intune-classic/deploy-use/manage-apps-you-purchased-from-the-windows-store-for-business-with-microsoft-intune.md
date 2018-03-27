---
title: 管理适用于企业的 Microsoft 应用商店应用
description: 如果要从 Intune 控制台对批量购买的应用进行管理和部署，请将 Microsoft Intune 连接到适用于企业的 Microsoft 应用商店
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 02/02/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 50fc27efc34ab6c13fad714e41be0d87c5ab0df9
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>使用 Microsoft Intune 管理从适用于企业的 Microsoft 应用商店中购买的应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

可在[适用于企业的 Microsoft 应用商店](https://www.microsoft.com/business-store)中为组织查找和购买应用（单个或批量）。 通过将此应用商店连接到 Microsoft Intune，你可以在 Intune 控制台管理批量购买的应用。 例如：
* 你可以将从应用商店中购买的应用列表与 Intune 同步。
* Intune 管理控制台中将显示已同步的应用，你可以像部署所有其他应用那样部署这些应用。
* 你可以跟踪可用许可证的数量以及正在 Intune 管理控制台中使用的许可证数量。
* 如果可用许可证数量不足，则 Intune 将阻止应用的部署和安装。

## <a name="before-you-start"></a>开始之前
从适用于企业的 Microsoft 应用商店同步并部署应用之前，请查看以下信息：
* 你必须将 Intune 配置为你的组织的移动设备管理机构。 有关详细信息，请参阅[在 Microsoft Intune 中注册设备的先决条件](prerequisites-for-enrollment.md)。
* 必须已在适用于企业的 Microsoft 应用商店中注册帐户。
* 一旦将适用于企业的 Windows 应用商店帐户与 Intune 关联，将来你将无法更改为其他帐户。
* 无法在 Intune 中手动添加或删除从应用商店购买的应用。 这些应用只能与适用于企业的 Microsoft 应用商店同步。
* Intune 只同步已从适用于企业的 Microsoft 应用商店中购买的联机已授权应用。
* 设备必须已加入 Active Directory 域服务或工作区才可使用此功能。
* 已注册的设备必须使用 Windows 10 的 1511 版本。

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>将适用于企业的 Microsoft 应用商店帐户与 Intune 关联
在 Intune 控制台中启用同步之前，必须将你的应用商店帐户配置为将 Intune 作为一种管理工具使用：
1. 确保使用与登录 Intune 相同的租户帐户登录企业应用商店。
2. 在企业应用商店中，选择**设置** > **管理工具**。
3. 在“管理工具”页上选择“添加管理工具”，然后选择“Microsoft Intune”。

> [!NOTE]
> 使用多个管理工具部署适用于企业的 Microsoft 应用商店时，以前只能将一个管理工具与适用于企业的 Microsoft 应用商店关联。 现在可将多种管理工具与该应用商店关联，例如 Intune 和 Configuration Manager。

现在可以继续，并在 Intune 控制台中设置同步。

## <a name="configure-synchronization"></a>配置同步

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“管理员”。
2. 在“管理”工作区中，展开“移动设备管理” > “Windows”，然后选择“适用于企业的应用商店”。
3. 在“适用于企业的 Microsoft 应用商店”页上，执行以下操作：
 * 如果尚未这样做，请单击适用于企业的 Microsoft 应用商店的注册链接。
 * 注册后，请选择“配置同步”。
4. 在“配置适用于企业的 Microsoft 应用商店的应用同步”对话框中，选择“启用适用于企业的 Microsoft 应用商店同步”。
5. 在“语言”下拉列表中，选择适用于企业的 Microsoft 应用商店的应用在 Intune 控制台中显示时使用的语言。 无论以何种语言显示，都会以最终用户的语言（如果有）进行安装。
6. 单击“确定”。

## <a name="synchronize-apps"></a>同步应用

1. 在“适用于企业的 Microsoft 应用商店”页上，选择“立即同步”，将从应用商店购买的应用与 Intune 同步。
2. 在“应用”工作区中，选择“应用” > “批量采购的应用”查看可部署的应用，并验证是否已正确导入已购买的应用。 该节点中的应用还将显示你所拥有的许可证总数，以及你拥有的可用许可证数。
例如，可从适用于企业的 Microsoft 应用商店购买公司门户应用（联机许可），将其同步到 Intune 控制台，然后作为要求的应用部署到 Windows 10 设备中。 


## <a name="deploy-apps"></a>部署应用

部署应用商店中应用的方式与部署任何其他 Intune 应用的方式相同。 有关详细信息，请参阅[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)。
部署适用于企业的 Microsoft 应用商店的应用时，安装此应用的每个用户都会使用一个许可证。 如果使用了部署应用的所有可用许可证，则你将无法再部署任何副本。 必须执行下列操作之一：
* 从一些设备上卸载应用。
* 减小当前部署的范围，仅针对具有足够许可证的用户。
* 从适用于企业的 Microsoft 应用商店中购买应用的更多副本。

> [!Important]
> 已部署的应用程序仅可用于最初注册了该设备的用户。 其他任何用户都无法访问该应用。


### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中为移动设备添加应用](add-apps-for-mobile-devices-in-microsoft-intune.md)
