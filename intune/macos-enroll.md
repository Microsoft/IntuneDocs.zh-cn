---
title: 设置 macOS 设备注册
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中设置 macOS 设备注册。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d23d03169cdbf3c88be257cafe6aa84dc8c5257f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236750"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>在 Intune 中设置 macOS 设备注册

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 可以管理 macOS 设备以允许用户访问公司电子邮件和应用。

作为 Intune 管理员，可以为公司拥有的 macOS 设备和个人拥有的 macOS 设备（“自带设备办公”或 BYOD）设置注册。 

## <a name="prerequisites"></a>必备条件

设置 macOS 设备注册之前请先完成以下先决条件：

- [配置域](custom-domain-name-configure.md)
- [设置 MDM 机构](mdm-authority-set.md)
- [创建组](groups-add.md)
- [配置公司门户](company-portal-app.md)
- 在 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)中分配用户许可证
- [获取 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>用户拥有的 macOS 设备 (BYOD)

可以让用户注册其个人设备用于 Intune 管理，这称为“自带设备办公”或 BYOD。 完成先决条件和分配的用户许可证后，用户可以通过以下方式注册其设备：
- 转到[公司门户网站](https://portal.manage.microsoft.com)或
- 下载公司门户应用。
还可以向他们发送联机注册步骤链接：[在 Intune 中注册 macOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)。

有关其他最终用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](end-user-educate.md)
- [通过 Intune 使用 macOS 设备](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>公司拥有的 macOS 设备
对于为用户购买设备的组织，Intune 还支持以下公司自有的 macOS 设备注册方法：
- [Apple 设备注册计划 (DEP)](device-enrollment-program-enroll-macos.md)：组织可以通过 Apple 设备注册计划 (DEP) 购买 macOS 设备。 DEP 允许用户通过“无线方式”部署注册配置文件以对设备进行管理。
- [设备注册管理员 (DEM)](device-enrollment-manager-enroll.md)：最多可以使用 DEM 帐户注册 1,000 台设备。

## <a name="block-macos-enrollment"></a>阻止 macOS 注册
默认情况下，Intune 允许注册 macOS 设备。 若要阻止 macOS 注册设备，请参阅[设置设备类型限制](enrollment-restrictions-set.md)。

## <a name="enroll-virtual-macos-machines-for-testing"></a>注册用于测试的虚拟 macOS 计算机

> [!NOTE]
> macOS 虚拟机只支持用于测试。 不应将 macOS 虚拟机用作最终用户的生产设备。 

可以使用 Parallels Desktop 或 VMware Fusion 注册用于测试的 macOS 虚拟机。 

对于 Parallels Desktop，需要设置虚拟机的硬件类型和序列号，使 Intune 能够识别它们。 按照 Parallels 的设置硬件类型和[序列号](http://kb.parallels.com/123455)说明进行操作，设置测试所必需的设置。 建议运行虚拟机的设备的硬件类型与要创建的虚拟机的硬件类型相匹配。 可通过“Apple 菜单” > “关于此 Mac” > “系统报告” > “模型标识符”找到此硬件类型。 

对于 VMware Fusion，需要[编辑 .vmx 文件](https://kb.vmware.com/s/article/1014782)，设置虚拟机的硬件模型和序列号。 建议运行虚拟机的设备的硬件类型与要创建的虚拟机的硬件类型相匹配。 可通过“Apple 菜单” > “关于此 Mac” > “系统报告” > “模型标识符”找到此硬件类型。 

## <a name="user-approved-enrollment"></a>用户已批准注册

用户批准的 MDM 注册是一种可用于管理某些安全敏感设置的 macOS 注册类型。 有关详细信息，请参阅 [Apple 的支持文档](https://support.apple.com/HT208019)。

要使用户获得批准，最终用户必须在使用 macOS 公司门户注册后，使用系统首选项手动提供批准。 macOS 公司门户为 macOS 10.13.2 和更高版本的用户提供了执行此操作的说明。

要确定设备是否为用户批准的，请转至 Intune 门户，然后选择“设备” > “所有设备”>“选择设备”>“硬件”。 检查“用户已批准”字段。

## <a name="next-steps"></a>后续步骤

注册 macOS 设备后，可[为 macOS 设备创建自定义设置](custom-settings-macos.md)。
