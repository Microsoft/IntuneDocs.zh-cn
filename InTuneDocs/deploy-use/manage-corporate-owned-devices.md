---
title: "管理公司拥有的设备 | Microsoft Docs"
description: "可采用多种方法注册企业拥有的设备。这具体取决于设备的类型、其购买方式以及组织需求。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 521a37044d6721fe905db7740329688ba2c24b35
ms.openlocfilehash: ae077d80e05b33d625285d796917f4f6c153ca3f


---

# <a name="enroll-corporate-owned-devices-by-using-intune"></a>使用 Intune 注册企业拥有的设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

可通过 Intune 采用多种方法来管理组织或公司拥有的设备 (COD)，这具体取决于设备的类型、其购买方式及组织需求。 也可安装公司门户应用，注册和管理企业拥有的设备，如“自带设备办公”(BYOD) 方案中所述。

默认情况下，适用于所有平台的设备都可在 Intune 中进行注册。 若要阻止设备注册，请使用管理员凭据登录 [Microsoft Intune 管理门户](http://manage.microsoft.com)。 选择“管理” > “移动设备管理” > “注册规则”，然后清除要阻止的平台对应的复选框。

## <a name="enroll-corporate-owned-ios-devices"></a>注册企业拥有的 iOS 设备

企业拥有的设备注册方法非常适合“选择自己的设备”(CYOD) 的情况。 在 CYOD 环境中，组织为用户选择的设备付费，且组织会管理该设备。

如果提供了 iOS 设备供用户选择，则可预配置注册，使设备自用户首次打开它时就通过 Intune 管理。 针对[直接](ios-direct-enrollment-in-microsoft-intune.md)注册或[设置助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)注册，Intune 支持通过 [Apple 设备注册计划 (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) 或使用 Mac 计算机上的 Apple 配置器工具进行注册。

了解如何[注册企业拥有的 iOS 设备](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)。

## <a name="create-a-device-enrollment-manager-account"></a>创建设备注册管理器帐户

可在 Intune 中创建单用户设备注册管理器 (DEM) 帐户，为组织管理大量移动设备。 创建 DEM 帐户后，指定的帐户管理器可注册超过 15 台设备（标准用户可注册 15 台设备）。

仅可使用 DEM 帐户注册未被单个特定用户使用的设备。 这些类型的设备非常适用于销售点或实用工具应用，但是不适用于需要访问电子邮件或公司资源的用户。

了解如何[使用 DEM 帐户注册企业拥有的设备](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)。

## <a name="enroll-corporate-owned-windows-10-enterprise-devices"></a>注册企业拥有的 Windows 10 企业版设备

如果在组织中使用 Azure Active Directory Premium 或 Microsoft 企业移动性套件，则可[注册 Windows 10 企业版设备](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)。 用户在设备上添加工作或学校帐户时，会自动将该设备标记为“企业所有”。

## <a name="import-imei-numbers"></a>导入 IMEI 号码

许多移动设备制造商在其设备上使用名为国际移动设备标识 (IMEI) 的唯一编号。 可导入组织拥有的设备的 IMEI 号码。 设备变为由 Intune 管理后，将被标记为企业拥有的设备。

了解如何[使用 IMEI 号码标记企业拥有的设备](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)。

## <a name="identify-a-device-as-corporate-owned"></a>将设备标识为“公司拥有”

以下任意条件为 true 时，Intune 会将设备识别为“公司设备”：

 - 设备[使用 DEM 帐户注册](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)（所有平台）。
 - 设备使用 [Apple DEP](ios-device-enrollment-program-in-microsoft-intune.md) 或 [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) 注册（仅限 iOS）。
 - 设备制造商[使用 IMEI 码预先声明设备](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)（所有具有 IMEI 码的平台）。
 - 设备在 [Azure Active Directory 或企业移动性套件中注册为 Windows 10 企业版设备](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)（仅限 Windows 10）。

设备标记为公司设备时，管理员控制台中该设备记录的“所有权”列会显示为“公司”。 



<!--HONumber=Jan17_HO5-->


