---
title: 什么是 Microsoft Intune 设备注册
titleSuffix: Microsoft Intune
description: 了解 iOS/iPadOS 设备、Android 设备和 Windows 设备注册。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7955c91a33edef37b86f5bd8f29dfb681d28030e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415349"
---
# <a name="what-is-device-enrollment"></a>什么是设备注册？
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 可让你管理员工的设备和应用，以及他们访问公司数据的方式。 要使用此移动设备管理 (MDM)，必须先在 Intune 服务中注册设备。 设备注册后，系统会向其颁发 MDM 证书。 此证书可用于与 Intune 服务进行通信。

如你在下表中所见，可通过几种方法来注册员工的设备。 每种方法取决于设备的所有权（个人或公司）、设备类型（iOS、Windows、Android）和管理需求（重置、关联、锁定）。

默认情况下，所有平台的设备都可在 Intune 中进行注册。 但是，可[可按平台限制设备](enrollment-restrictions-set.md#create-a-device-type-restriction)。

## <a name="iosipados-enrollment-methods"></a>iOS/iPadOS 注册方法

| **方法** | **需要重置** | [**用户关联**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) | **Locked** | **详细信息** |
|:---:|:---:|:---:|:---:|:---:|
| | 设备在注册过程中被擦除。 | 将每个设备与用户关联。| 如果“是”，则用户无法取消注册设备。 | |
|**[BYOD](#bring-your-own-device)** | 否| 是 | 否 | [详细信息](apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| 否 |否 |否 | [详细信息](device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**| 是 | 可选 | 可选|[详细信息](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| 是 | 可选 | 否| [详细信息](apple-configurator-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| 否 | 否 | 否|[详细信息](apple-configurator-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>macOS 注册方法
| **方法** |  **需要重置** |  **用户关联** | **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 否| 是 | 否 | [详细信息](macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 否 |否 |否  | [详细信息](device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**| 是 | 可选 | 可选|[详细信息](device-enrollment-program-enroll-macos.md)|

## <a name="windows-enrollment-methods"></a>Windows 注册方法

| **方法** | **需要重置** | **用户关联** | **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 否 | 是 | 否 | [详细信息](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 否 |否 |否 |[详细信息](device-enrollment-manager-enroll.md)|
|**自动注册** | 否 |是 |否 | [详细信息](windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |是 |是 |否 | [详细信息](enrollment-autopilot.md)
|**批量注册** |否 |否 |否 | [详细信息](windows-bulk-enroll.md) |
|**共同管理** |否 |是 |否 | [详细信息](https://docs.microsoft.com/configmgr/core/clients/manage/co-management-overview)
|**GPO** |否 |是 |否 | [详细信息](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)

## <a name="android-enrollment-methods"></a>Android 注册方法

| 个人  | **注册方法** | **需要重置** | **用户关联** | **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android 设备管理**|**用户通过公司门户启动** | 否 | 是 | 否 | [详细信息](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Android Enterprise 工作配置文件**|**用户通过公司门户启动**| 否 | 是 | 否 | [详细信息](android-work-profile-enroll.md)|


| **公司** | **注册方法** | **需要重置** | **用户关联** | **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android 设备管理**|[DEM](#device-enrollment-manager) 通过公司门户启动 | 否 | 否 | 否 |[详细信息](device-enrollment-manager-enroll.md)|
|**Android 设备管理**|**（预声明的 IMEI 或 SN）用户通过公司门户启动**| 否 | 是 | 否 | [详细信息](./../corporate-identifiers-add.md)|
|**带有 Zebra Mobility Extensions 的 Android 设备管理**|用户或 [DEM](#device-enrollment-manager) 通过公司门户启动 | 否 | 如果用户启动，则为是；如果 [DEM](#device-enrollment-manager) 启动，则为否 | 否 | [详细信息](../configuration/android-zebra-mx-overview.md)|
|**Android Enterprise 专用**|**NFC、令牌、QR 代码、Zero Touch**| 是 | 否 | 可通过策略进行配置 | [详细信息](android-kiosk-enroll.md)|
|**Android Enterprise 完全托管设备**|**NFC、令牌、QR 代码、Zero Touch**| 是 | 是 | 可通过策略进行配置 | [详细信息](android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>自带设备办公
自带设备办公 (BYOD) 指代的设备包括个人拥有的电话、平板电脑和电脑。 用户安装并运行公司门户应用，以注册 BYOD。 此程序可让用户访问电子邮件等公司资源。

## <a name="corporate-owned-device"></a>公司拥有的设备
[公司拥有的设备 (COD)](corporate-identifiers-add.md) 包括组织拥有并分发给员工的电话、平板电脑和电脑。 COD 注册支持多种方案，例如自动注册、共享设备或预授权注册需求。 管理员或经理注册 COD 的常用方法是使用设备注册管理器 (DEM)。 可直接通过 Apple 提供的设备注册计划 (DEP) 工具注册 iOS/iPadOS 设备。 也可识别具有 IMEI 号码的设备并将其标记为“公司拥有”。

### <a name="device-enrollment-manager"></a>设备注册管理器
设备注册管理员 (DEM) 是一个特殊的用户帐户，用于注册和管理多个企业拥有的设备。 此管理器可以安装公司门户和注册多个无用户设备。 这些类型的设备非常适用于销售点或实用工具应用，但是不适用于需要访问电子邮件或公司资源的用户。 详细了解 [DEM](device-enrollment-manager-enroll.md)。

### <a name="apple-device-enrollment-program"></a>Apple 设备注册计划
通过 Apple 设备注册计划 (DEP) 管理，可“无线”创建策略并将其部署到通过 DEP 购买和管理的 iOS/iPadOS 和 macOS 设备。 用户第一次开启设备并运行设置助理时，将注册设备。 此方法支持 iOS/iPadOS 受监督模式，该模式允许设备配置特定功能。

了解有关 iOS/iPadOS DEP 注册的详细信息：

- [选择 iOS/iPadOS 设备的注册方式](ios-enroll.md)
- [使用设备注册计划注册 iOS/iPadOS 设备](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
IT 管理员可通过 USB 使用 Apple Configurator，手动准备每台公司拥有的设备，以便使用“设置助理”进行注册。 IT 管理员创建注册配置文件并将其导出到 Apple Configurator。 用户收到设备时，系统随后会提示其运行设备助理来注册设备。 此方法支持“iOS 受监督”模式，从而可以使用下列功能  ：
- 锁定的注册
- 展台模式以及其他高级配置和限制

了解有关使用“设置助理”注册 iOS/iPadOS Apple Configurator 的详细信息：

- [决定 iOS/iPadOS 设备的注册方式](ios-enroll.md)
- [使用 Configurator 和设置助理注册 iOS/iPadOS 设备](apple-configurator-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
对于直接注册，管理员必须创建注册策略并将其导出到 Apple Configurator，进而手动注册每台设备。 连接了 USB 的公司拥有的设备可直接进行注册，无需进行擦除。 这些设备作为无用户设备进行管理。 它们未锁定、不受监控，且无法支持条件访问、越狱检测或移动应用管理。

若要了解有关 iOS/iPadOS 注册的详细信息，请参阅：

- [决定 iOS/iPadOS 设备的注册方式](ios-enroll.md)
- [使用 Configurator 和直接注册来注册 iOS/iPadOS 设备](apple-configurator-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 证书过期后的移动设备清理

当移动设备与 Intune 服务通信时，将自动续订 MDM 证书。 如果移动设备被擦除，或者它们在一段时间内无法与 Intune 服务通信，则不会续订 MDM 证书。 MDM 证书过期 180 天后，设备将从 Azure 门户中删除。
