---
title: "设置移动设备管理机构"
titleSuffix: Intune on Azure
description: "了解如何在 Intune 中设置移动设备管理机构。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 449c45e0edcc0d0a33352ba154ad68fa6c4725c0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="set-the-mobile-device-management-authority"></a>设置移动设备管理机构

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

移动设备管理 (MDM) 机构设置决定了管理设备的方式。 作为 IT 管理员，必须先设置 MDM 机构，然后用户才能注册设备来进行管理。

可能的设置包括：

- **Intune 独立版** - 仅限云的管理，可使用 Azure 门户进行配置。 包括 Intune 提供的所有功能。 [在 Intune 控制台中设置 MDM 机构](#mdm-authority-set-to-intune)。

- **Intune 混合版** - 集成了 Intune 云解决方案和 System Center Configuration Manager。 可使用 Configuration Manager 控制台配置 Intune。 [在 Configuration Manager 中设置 MDM 机构](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。

- **Office 365 的移动设备管理** - 集成了 Office 365 和 Intune 云解决方案。 可在 Office 365 管理中心中配置 Intune。 包括 Intune 独立版中提供的部分功能。 在 Office 365 管理中心中设置 MDM 机构。

>[!IMPORTANT]    
在 Configuration Manager 版本 1610 或更高版本和 Microsoft Intune 版本 1705 中，你将可以更改 MDM 颁发机构，而无需联系 Microsoft 支持部门，并且无需取消注册并重新注册现有的受管理设备。 有关详细信息，请参阅[如果选择了错误的 MDM 颁发机构设置怎么办](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)。

## <a name="set-mdm-authority-to-intune"></a>将 MDM 机构设置为 Intune

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。
  ![选择用户链接的 Intune 疑难解答工作负荷的屏幕截图](media/set-mdm-auth.png)
2. 在“Intune”边栏选项卡上，选择“设备注册”，然后选择“概述”。

3. 在“开始管理设备”边栏选项卡上，选择“将 MDM 机构设置为 Intune”。 将出现一条消息，表明已成功将 MDM 机构设置为 Intune。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 证书过期后的移动设备清理

当移动设备与 Intune 服务通信时，将自动续订 MDM 证书。 如果移动设备被擦除，或者它们在一段时间内无法与 Intune 服务通信，则 MDM 证书将不会续订。 MDM 证书过期 180 天后，设备将从 Azure 门户中删除。
