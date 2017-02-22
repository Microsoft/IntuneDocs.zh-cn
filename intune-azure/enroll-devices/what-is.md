---
title: "什么是 Microsoft Intune 设备注册 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何为 iOS 设备、Android 设备和 Windows 设备注册。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/26/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 10cf9980468eff912557747c31994747c17a3ab4
ms.openlocfilehash: 01bf32ef874385019ea4b0fb0ce278554459287d


---

# <a name="what-is-device-enrollment"></a>什么是设备注册？
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

本主题介绍了 Intune 管理中的注册并列出了注册移动设备的不同方法。

在 Intune 中注册设备（包括 Windows 电脑）以便对其进行管理。 我们在 Intune 文档中将此功能称为移动设备管理 (MDM)。 设备注册为移动设备（而不是电脑）时，会向其颁发 MDM 证书，设备随后会使用这些证书与 Intune 服务进行通信。 

注册设备的方式取决于设备类型、所有权和所需的管理级别。 “自带设备办公”(BYOD) 注册允许用户注册其个人电话、平板电脑或电脑。 通过公司自有设备 (COD) 注册，可实现自动注册、共享设备或预授权注册要求等管理方案。

若使用 Exchange ActiveSync（在本地或在云中托管），无需注册就可启用简单的 Intune 管理（详细信息稍后发布）。 建议将 Windows 电脑作为移动设备管理，方法如下所述。 也可以使用 [Intune 客户端软件](https://docs.microsoft.com/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)将其作为电脑管理。


## <a name="overview-of-device-enrollment-methods"></a>设备注册方法概述

下表列出了 Intune 注册方法、支持的功能以及每个方法的要求。 功能和要求如下所述。 表中使用以下术语：

- **擦除** - 指示是否需要擦除设备后才使用户可注册设备。 术语“擦除”意味着对设备恢复出厂设置，这将删除所有数据。 有关详细信息，请参阅[在设备上使用完全擦除或选择性擦除](/intune-azure/manage-devices/use-full-or-selective-wipe-on-devices-using-microsoft-intune)。
- **关联** - 将设备与用户关联。 对于移动应用程序管理 (MAM) 和公司数据的条件访问是必需的。 有关详细信息，请参阅[用户关联](enroll-ios-devices-using-device-enrollment-program.md)。
- **锁定** - 指示是否阻止用户从管理取消注册其设备。 用户可使用公司门户应用在所有平台上取消注册其设备。 用户不能使用本机操作系统菜单来取消注册。


**iOS 注册方法**

| **方法** |  **需要擦除？** |    **相关性**    |   **锁定** | **详细信息** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | 详细信息稍后发布|
|**[DEM](#dem)**|   否 |否 |否  | [详细信息](enroll-ios-devices-using-device-enrollment-program.md)|
|**[DEP](#dep)**|   是 |   可选 |  可选|[详细信息](enroll-ios-devices-using-device-enrollment-program.md)|
|**[USB-SA](#usb-sa)**| 是 |   可选 |  否| [详细信息](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)|
|**[USB-Direct](#usb-direct)**| 否 |    否  | 否|[详细信息](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)|



**Windows 注册方法**

| **方法** |  **需要擦除？** |    **相关性**    |   **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 是|   是 |   否 | 详细信息稍后发布|
|**[DEM](#dem)**|   否 |否 |否  |[详细信息](enroll-devices-using-device-enrollment-manager.md)|

**Android 注册方法**

| **方法** |  **需要擦除？** |    **相关性**    |   **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | 详细信息稍后发布|
|**[DEM](#dem)**|   否 |否 |否  |[详细信息](enroll-ios-devices-using-device-enrollment-program.md)|


## <a name="byod"></a>BYOD
“自带设备办公”用户安装公司门户应用并注册其设备。 这让用户可连接到公司网络，并加入该域或 Azure Active Directory。 对于大多数平台，需要为许多 COD 方案启用 BYOD 注册。

## <a name="corporate-owned-devices"></a>企业持有设备
可以使用 Azure 门户管理公司拥有的设备 (COD)。 可以直接通过 Apple 提供的工具注册 iOS 设备。 管理员或经理可以使用设备注册管理器注册所有设备类型。 具有 IMEI 号码的设备也可以标识并标记为公司拥有，以实现 COD 方案。

### <a name="dem"></a>DEM
设备注册管理员是一个特殊的用户帐户，用于注册和管理多个企业持有设备。 管理员可安装公司门户并注册多个无用户设备。 了解有关 [DEM](enroll-devices-using-device-enrollment-manager.md) 的详细信息。 （[返回到表](#overview-of-device-enrollment-methods)）

### <a name="dep"></a>DEP
通过 Apple 设备注册计划 (DEP) 管理，可“无线”创建策略并将其部署到通过 DEP 购买和管理的 iOS 设备。 用户第一次开启设备并运行 iOS 设置助理时，将注册设备。 此方法支持 **iOS 监督**模式，此模式又允许：

  - 锁定注册
  - 展台模式以及其他高级配置和限制

若要了解有关 iOS 注册的详细信息，请参阅：

- [选择 iOS 设备注册方式](choose-ios-enrollment-method.md)
- [使用设备注册计划注册 iOS 设备](enroll-ios-devices-using-device-enrollment-program.md)。 
- [返回到上表](#overview-of-device-enrollment-methods)

### <a name="usb-sa"></a>USB-SA
IT 管理员通过 USB 使用 Apple Configurator 手动准备每台公司自有设备，以便使用设备助理进行注册。 IT 管理员创建注册配置文件并将其导出到 Apple Configurator。 用户收到设备时，系统随后会提示其运行设备助理来注册设备。 此方法支持 **iOS 监督**模式，此模式又允许：
  - 锁定注册
  - 展台模式以及其他高级配置和限制

若要了解有关 iOS 注册的详细信息，请参阅：

- [决定 iOS 设备注册方式](choose-ios-enrollment-method.md)
- [使用配置器和设置助理注册 iOS 设备](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)。 

### <a name="usb-direct"></a>USB-Direct
对于直接注册，管理员必须创建注册策略并将其导出到 Apple Configurator，进而手动注册每台设备。 连接了 USB 的公司拥有的设备可直接进行注册，无需恢复出厂设置。 这些设备作为无用户设备进行管理。 它们未锁定、不受监控，且无法支持条件性访问、越狱检测或移动应用管理。 

若要了解有关 iOS 注册的详细信息，请参阅：

- [决定 iOS 设备注册方式](choose-ios-enrollment-method.md)
- [使用配置器和直接注册来注册 iOS 设备](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>使用 Exchange ActiveSync 和 Intune 管理移动设备
可以使用 EAS MDM 策略，通过 Intune 管理未注册、但连接到 Exchange ActiveSync (EAS) 的移动设备。 Intune 使用 Exchange Connector 与 EAS 在本地或云托管环境中进行通信。 详细信息稍后发布。


## <a name="windows-pc-management-with-intune"></a>使用 Intune 管理 Windows 电脑  
还可以使用 Microsoft Intune 管理使用 Intune 客户端软件的 Windows 电脑。 使用 Intune 客户端管理的电脑可以：

 - 报告软件和硬件清单
 - 安装桌面应用程序（例如 .exe 和 .msi 文件）
 - 管理防火墙设置

使用 Intune 客户端软件管理的电脑不能完全擦除，但可以选择性擦除。 使用 Intune 软件客户端管理的电脑不能利用许多 Intune 管理功能，如条件访问、VPN 和 Wi-Fi 设置或证书和电子邮件配置的部署。 详细信息稍后发布。

## <a name="supported-device-platforms-and-browsers"></a>支持的设备平台和浏览器

请参阅 [Intune 支持的设备和浏览器](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 证书过期后的移动设备清理

当移动设备与 Intune 服务通信时，将自动续订 MDM 证书。 如果移动设备（不是电脑）被擦除，或者它们在一段时间内无法与 Intune 服务通信，则 MDM 证书将不会续订。 MDM 证书过期 180 天后，设备将从 Azure 门户中删除。



<!--HONumber=Feb17_HO1-->


