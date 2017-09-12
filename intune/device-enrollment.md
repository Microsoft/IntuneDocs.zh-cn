---
title: "什么是 Microsoft Intune 设备注册"
titlesuffix: Azure portal
description: "了解如何为 iOS 设备、Android 设备和 Windows 设备注册。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dda7108aedcc4d3878fe3743ee0b88b26fabbe6f
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="what-is-device-enrollment"></a>什么是设备注册？
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题介绍了 Intune 管理中的注册并列出了注册移动设备的不同方法。

在 Intune 中注册设备以便对其进行管理。 我们在 Intune 文档中将此功能称为移动设备管理 (MDM)。 在 Intune 中注册设备后，会向其颁发 MDM 证书，设备随后会使用这些证书与 Intune 服务进行通信。

注册设备的方式取决于设备类型、所有权和所需的管理级别。 “自带设备办公”(BYOD) 注册允许用户注册其个人电话、平板电脑或电脑。 通过公司自有设备 (COD) 注册，可实现自动注册、共享设备或预授权注册要求等管理方案。

若使用 Exchange ActiveSync（在本地或在云中托管），无需注册就可启用简单的 Intune 管理（详细信息稍后发布）。 建议将 Windows 电脑作为移动设备管理，方法如下所述。


## <a name="overview-of-device-enrollment-methods"></a>设备注册方法概述

下表概要列出了 Intune 注册的各种方法，并在后面部分对其相关功能和要求进行了说明。
**图例**

- **需要重置** - 设备在注册过程中恢复出厂设置。
- **用户关联** - 将设备与用户关联。 有关详细信息，请参阅[用户关联](device-enrollment-program-enroll-ios.md)。
- **锁定** - 防止用户取消注册设备。

**iOS 注册方法**

| **方法** |  **需要重置** |    **用户关联**   |   **锁定** | **详细信息** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | [详细信息](./apple-mdm-push-certificate-get.md)|
|**[DEM](#dem)**|   否 |否 |否  | [详细信息](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#dep)**|   是 |   可选 |  可选|[详细信息](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| 是 |   可选 |  否| [详细信息](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| 否 |    否  | 否|[详细信息](./apple-configurator-direct-enroll-ios.md)|

**Windows 注册方法**

| **方法** |  **需要重置** |    **用户关联**   |   **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否 |   是 |   否 | [详细信息](windows-enroll.md)|
|**[DEM](#dem)**|   否 |否 |否  |[详细信息](device-enrollment-manager-enroll.md)|
|**自动注册** | 否 |是 |否 | [详细信息](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**批量注册** |否 |否 |否 | [详细信息](./windows-bulk-enroll.md) |

**Android 注册方法**

| **方法** |  **需要重置** |    **用户关联**   |   **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | [详细信息](./android-enroll.md)|
|**[DEM](#dem)**|   否 |否 |否  |[详细信息](./device-enrollment-program-enroll-ios.md)|
|**Android for Work**| 否 | 是 | 否| [详细信息](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="byod"></a>BYOD
“自带设备办公”的用户需要安装并运行公司门户应用，以注册其设备。 此程序可让用户访问电子邮件等公司资源。

## <a name="corporate-owned-devices"></a>公司拥有的设备
以下是公司拥有的设备 (COD) 注册方案。 可以直接通过 Apple 提供的工具注册 iOS 设备。 管理员或经理可以使用设备注册管理器注册所有设备类型。 具有 IMEI 号码的设备也可以标识并标记为公司拥有，以实现 COD 方案。

### <a name="dem"></a>DEM
设备注册管理员 (DEM) 是一个特殊的用户帐户，用于注册和管理多个企业拥有的设备。 管理员可安装公司门户并注册多个无用户设备。 了解有关 [DEM](./device-enrollment-manager-enroll.md) 的详细信息。

### <a name="dep"></a>DEP
通过 Apple 设备注册计划 (DEP) 管理，可“无线”创建策略并将其部署到通过 DEP 购买和管理的 iOS 设备。 用户第一次开启设备并运行 iOS 设置助理时，将注册设备。 此方法支持“iOS 监管”模式，从而可以使用下列功能：

  - 锁定注册
  - 展台模式以及其他高级配置和限制

了解有关 iOS DEP 注册的详细信息：

- [选择 iOS 设备注册方式](enrollment-method-choose-ios.md)
- [使用设备注册计划注册 iOS 设备](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
IT 管理员可通过 USB 使用 Apple Configurator，手动准备每台公司拥有的设备，以便使用“设置助理”进行注册。 IT 管理员创建注册配置文件并将其导出到 Apple Configurator。 用户收到设备时，系统随后会提示其运行设备助理来注册设备。 此方法支持“iOS 监管”模式，从而可以使用下列功能：
  - 锁定注册
  - 展台模式以及其他高级配置和限制

了解有关使用“设置助理”注册 iOS Apple Configurator 的详细信息：

- [决定 iOS 设备注册方式](enrollment-method-choose-ios.md)
- [使用 Configurator 和设置助理注册 iOS 设备](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
对于直接注册，管理员必须创建注册策略并将其导出到 Apple Configurator，进而手动注册每台设备。 连接了 USB 的公司拥有的设备可直接进行注册，无需恢复出厂设置。 这些设备作为无用户设备进行管理。 它们未锁定、不受监控，且无法支持条件性访问、越狱检测或移动应用管理。

若要了解有关 iOS 注册的详细信息，请参阅：

- [决定 iOS 设备注册方式](enrollment-method-choose-ios.md)
- [使用配置器和直接注册来注册 iOS 设备](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>使用 Exchange ActiveSync 和 Intune 管理移动设备
可以使用 EAS MDM 策略，通过 Intune 管理未注册、但连接到 Exchange ActiveSync (EAS) 的移动设备。 Intune 使用 Exchange Connector 与 EAS 在本地或云托管环境中进行通信。 详细信息稍后发布。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 证书过期后的移动设备清理

当移动设备与 Intune 服务通信时，将自动续订 MDM 证书。 如果移动设备被擦除，或者它们在一段时间内无法与 Intune 服务通信，则 MDM 证书将不会续订。 MDM 证书过期 180 天后，设备将从 Azure 门户中删除。
