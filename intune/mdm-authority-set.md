---
title: "设置移动设备管理机构"
titlesuffix: Azure portal
description: "了解如何在 Intune 中设置移动设备管理机构。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e042ccbc085b2cf511d3cd21f2da5e23299264a9
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="set-the-mobile-device-management-authority"></a>设置移动设备管理机构

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

移动设备管理 (MDM) 机构设置决定了管理设备的方式。 作为 IT 管理员，必须先设置 MDM 机构，然后用户才能注册设备来进行管理。

可能的设置包括：

- **Intune 独立版** - 仅限云的管理，可使用 Azure 门户进行配置。 包括 Intune 提供的所有功能。 [在 Intune 控制台中设置 MDM 机构](#set-mdm-authority-to-intune)。

- **Intune 混合版** - 集成了 Intune 云解决方案和 System Center Configuration Manager。 可使用 Configuration Manager 控制台配置 Intune。 [在 Configuration Manager 中设置 MDM 机构](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。

- **Office 365 的移动设备管理** - 集成了 Office 365 和 Intune 云解决方案。 可在 Office 365 管理中心中配置 Intune。 包括 Intune 独立版中提供的部分功能。 在 Office 365 管理中心中设置 MDM 机构。

>[!IMPORTANT]    
在 Configuration Manager 版本 1610 或更高版本和 Microsoft Intune 版本 1705 中，你将可以更改 MDM 颁发机构，而无需联系 Microsoft 支持部门，并且无需取消注册并重新注册现有的受管理设备。 有关详细信息，请参阅[如果选择了错误的 MDM 颁发机构设置怎么办](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)。

## <a name="set-mdm-authority-to-intune"></a>将 MDM 机构设置为 Intune

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”[](https://portal.azure.com)。
2. 选择橙色横幅，打开“移动设备管理机构”设置。
3. 在“移动设备管理机构”下，从以下选项中选择你的 MDM 机构：
  - Intune MDM 机构
  - Configuration Manager MDM 机构
  - **无**

  ![Intune 移动设备管理机构设置屏幕的屏幕截图](media/set-mdm-auth.png)

  将出现一条消息，表明已成功将 MDM 机构设置为 Intune。

## <a name="enable-device-enrollment"></a>启用设备注册

将 Intune 设置为 MDM 机构后，用户可以通过安装公司门户（iOS 和 Android）、添加工作凭据 (Windows) 或访问公司门户网站（iOS、Android、macOS），注册个人拥有的设备并获得对电子邮件等资源的访问权限。

要实现或简化注册，各平台的要求如下：
- iOS - （必需）[获取 Apple MDM push certificate](apple-mdm-push-certificate-get.md)，然后[启用公司拥有的 iOS 设备注册](ios-enroll.md)（可选）。
- Android -（可选）[启用 Android 工作配置文件](android-enroll.md)
- Windows -（可选）启用[自动注册](windows-enroll.md)或[批量注册](windows-bulk-enroll.md)
- macOS - 无要求


## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 证书过期后的移动设备清理

当移动设备与 Intune 服务通信时，将自动续订 MDM 证书。 如果移动设备被擦除，或者它们在一段时间内无法与 Intune 服务通信，则 MDM 证书将不会续订。 MDM 证书过期 180 天后，设备将从 Azure 门户中删除。
