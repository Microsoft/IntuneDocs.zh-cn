---
title: 设置移动设备管理机构
titlesuffix: Microsoft Intune
description: 在 Intune 中设置移动设备管理机构。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f903e9dfe5fb30f45806aac5694171814492f2e
ms.sourcegitcommit: 0f1a5d6e577915d2d748d681840ca04a0a2604dd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842265"
---
# <a name="set-the-mobile-device-management-authority"></a>设置移动设备管理机构

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

移动设备管理 (MDM) 机构设置决定了管理设备的方式。 作为 IT 管理员，必须先设置 MDM 机构，然后用户才能注册设备来进行管理。

可能的设置包括：

- **Intune 独立版** - 仅限云的管理，可使用 Azure 门户进行配置。 包括 Intune 提供的所有功能。 [在 Intune 控制台中设置 MDM 机构](#set-mdm-authority-to-intune)。

- **Intune 混合版** - 集成了 Intune 云解决方案和 System Center Configuration Manager。 可使用 Configuration Manager 控制台配置 Intune。 [在 Configuration Manager 中设置 MDM 机构](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。

- **Office 365 的移动设备管理** - 集成了 Office 365 和 Intune 云解决方案。 可在 Office 365 管理中心中配置 Intune。 包括 Intune 独立版中提供的部分功能。 在 Office 365 管理中心中设置 MDM 机构。

> [!IMPORTANT]
> 在 Configuration Manager 版本 1610 或更高版本和 Microsoft Intune 版本 1705 中，你将可以更改 MDM 颁发机构，而无需联系 Microsoft 支持部门，并且无需取消注册并重新注册现有的受管理设备。 有关详细信息，请参阅[如果选择了错误的 MDM 颁发机构设置怎么办](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)。

## <a name="set-mdm-authority-to-intune"></a>将 MDM 机构设置为 Intune

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 选择橙色横幅，打开“移动设备管理机构”设置。
4. 在“移动设备管理机构”下，从以下选项中选择你的 MDM 机构：
   - Intune MDM 机构
   - Configuration Manager MDM 机构
   - **无**

   ![Intune 移动设备管理机构设置屏幕的屏幕截图](media/set-mdm-auth.png)

   将出现一条消息，表明已成功将 MDM 机构设置为 Intune。

## <a name="enable-device-enrollment"></a>启用设备注册

将 Intune 设置为 MDM 机构后，用户可以通过安装公司门户（iOS、macOS 和 Android）、添加工作凭据 (Windows) 或访问公司门户网站（iOS、Android、macOS），注册个人拥有的设备并获得对电子邮件等资源的访问权限。

要实现或简化注册，各平台的要求如下：
- iOS - （必需）[获取 Apple MDM push certificate](apple-mdm-push-certificate-get.md)，然后[启用公司拥有的 iOS 设备注册](ios-enroll.md)（可选）。
- Android -（可选）[启用 Android 工作配置文件](android-enroll.md)
- Windows -（可选）启用[自动注册](windows-enroll.md)或[批量注册](windows-bulk-enroll.md)
- macOS - （必需）获取 [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)。

### <a name="workflow-of-intune-administration-ui"></a>Intune 管理 UI 的工作流
启用 Android 或 Apple 设备管理后，Intune 将发送设备和用户信息来与这些第三方服务集成，以便管理其各自的设备。

可以同意共享数据的场景包括：
- 启用 Android for Work 时。
- 启用并上传 Apple MDM Push Certificate 时。
- 启用任何诸如设备注册计划、School Manager 或批量采购计划等 Apple 服务时。

在每种情况下，同意都与运行移动设备管理服务严格相关，例如确认 IT 管理员已授权 Google 或 Apple 设备注册。 以下位置提供当新的工作流上线时用于查阅共享了哪些信息的文档：
- [Intune 向 Google 发送的数据](https://aka.ms/Data-intune-sends-to-google)
- [Intune 向 Apple 发送的数据](https://aka.ms/data-intune-sends-to-apple)

有关 Microsoft GDPR 符合性的详细信息，请参阅[信任中心 - 评估 GDPR 符合性](https://aka.ms/trust_center_info)。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 证书过期后的移动设备清理

当移动设备与 Intune 服务通信时，将自动续订 MDM 证书。 如果移动设备被擦除，或者它们在一段时间内无法与 Intune 服务通信，则 MDM 证书将不会续订。 MDM 证书过期 180 天后，设备将从 Azure 门户中删除。
