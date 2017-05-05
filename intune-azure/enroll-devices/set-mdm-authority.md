---
title: "设置移动设备管理机构"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何在 Intune 中设置移动设备管理机构。 "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: dc08ba96eeea0ce2aad78e4d6ca0d94e709d885d
ms.openlocfilehash: 6cf7c56924091713f55fe8824fb11e522825b98f
ms.lasthandoff: 04/21/2017

---

# <a name="set-the-mobile-device-management-authority"></a>设置移动设备管理机构

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

移动设备管理 (MDM) 机构设置决定了管理设备的方式。 作为 IT 管理员，必须先设置 MDM 机构，然后用户才能注册设备来进行管理。

可能的设置包括：

- **Intune 独立版** - 仅限云的管理，可使用 Azure 门户进行配置。 包括 Intune 提供的所有功能。 [在 Intune 控制台中设置 MDM 机构](#set-mdm-authority-to-Intune)。

- **Intune 混合版** - 集成了 Intune 云解决方案和 System Center Configuration Manager。 可使用 Configuration Manager 控制台配置 Intune。 [在 Configuration Manager 中设置 MDM 机构](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。

- **Office 365 的移动设备管理** - 集成了 Office 365 和 Intune 云解决方案。 可在 Office 365 管理中心中配置 Intune。 包括 Intune 独立版中提供的部分功能。 在 Office 365 管理中心中设置 MDM 机构。

>[!IMPORTANT]
>移动设备管理机构一旦设定，若要进行更改，必须联系 [Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)，所以请谨慎选择。

## <a name="set-mdm-authority-to-intune"></a>将 MDM 机构设置为 Intune

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。
  ![选择用户链接的 Intune 疑难解答工作负荷的屏幕截图](media/set-mdm-auth.png)
2. 在“Intune”边栏选项卡上，选择“设备注册”，然后选择“概述”。

3. 在“开始管理设备”边栏选项卡上，选择“将 MDM 机构设置为 Intune”。 将出现一条消息，表明已成功将 MDM 机构设置为 Intune。

