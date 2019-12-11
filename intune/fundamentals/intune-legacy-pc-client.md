---
title: 旧版 Intune PC 客户端和 Azure 上的 Intune
description: 在 Azure 上使用 Intune 管理组织的 Windows 设备时的注意事项。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 1f104923-12df-453c-9c20-942ef65a0945
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ab1be3d34d52e824d1ff06124e28206fb7b07a1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510188"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Azure 控制台上的 Intune 和旧版 Intune PC 客户端

Intune 使用基于 Azure 的 SaaS 应用程序服务体系结构。 Azure 在缩放、容量和性能方面得到了显著的提升。 这为 Azure 门户提供了增强的 Intune 管理体验和优化的工作流。 

在 Azure 上使用 Intune 管理组织的 Windows 设备时，请考虑以下几点：

## <a name="manage-windows-10-devices-by-using-mdm"></a>使用 MDM 管理 Windows 10 设备

我们建议使用[移动设备管理 (MDM) 来管理 Windows 10 设备](../configuration/device-restrictions-windows-10.md)，而不是使用旧 Intune PC 客户端进行管理。 Azure 门户上的 Intune 提供了通过 MDM 管理 Windows 10 的功能。 Windows 10 MDM 提供了许多旧 Intune PC 客户端没有的新的管理和安全功能。

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>旧 PC 客户端功能仅适用于 Silverlight 控制台

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune PC 客户端管理工作流使用[基于 Silverlight 的 Intune 管理控制台](https://manage.microsoft.com/)，这造成了以下结果：

- 对于使用 Intune PC 客户端的所有非分组管理任务，必须使用 Silverlight 控制台。
- 在管理组时，必须使用 [Azure 门户上的 Intune](https://portal.azure.com/)。 存在这一要求的原因是，Intune 现在使用 Azure AD 组，而不是旧 Intune 组。 

由于切换到 Azure AD 组，因此 Silverlight 控制台仪表板中的“基于组”的筛选也略有更改。 若要在更新的 Silverlight UI 中进行筛选，请执行以下步骤：

1. 选择一个视图。
2. 在“筛选器”  框中，输入想要进行筛选的组的名称，然后按 Enter。 该操作将对该特定组中设备的列表视图进行筛选。

   ![筛选未选择的下拉输入](./media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>继续使用旧 Intune PC 客户端管理 Windows 7

对于不能通过使用 MDM 进行管理的 Windows 7，我们将仅在 Silverlight 控制台中继续支持现有 Intune PC 客户端功能。 当升级到 Windows 10 后，请考虑迁移到 MDM 管理。

## <a name="mdm-capabilities"></a>MDM 功能

有关 PC 客户端和 MDM 功能之间的详细比较，请参阅[对比作为计算机或移动设备管理 Windows 电脑](pc-management-comparison.md)。 MDM 更新将继续为注册 MDM 的 Windows 10 设备带来新的管理功能，其中包括评估 Win 32 应用的选项。 查看[新增功能](whats-new.md)以了解添加到服务的最新版本。

## <a name="switch-from-pc-client-to-mdm"></a>从 PC 客户端切换到 MDM

若要从使用 Intune PC 客户端管理 Windows 10 设备切换到使用 MDM 进行管理，请执行以下步骤：

1. 在 Silverlight 控制台中，执行选择性擦除  以从 PC 客户端中取消注册设备。
  ![警告 popup，并选中 "选择性擦除设备" 单选按钮](./media/intune-legacy-pc-client/image02.png)
2. 通过使用 [MDM（和/或 Azure AD 加入）](../enrollment/windows-enroll.md)重新注册设备。

## <a name="next-steps"></a>后续步骤
[注册 Windows 设备](../enrollment/windows-enroll.md)
