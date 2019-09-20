---
title: 使用设备注册管理员帐户注册设备
titleSuffix: Microsoft Intune
description: 使用设备注册管理器帐户在 Intune 中注册设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbfe0e30794ddfe5b2f089d50456f9cbdd031e6d
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071389"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>使用设备注册管理员帐户在 Intune 中注册设备

通过使用设备注册管理器 (DEM) 帐户，可以使用单个 Azure Active Directory 帐户注册多达 1,000 个移动设备。 DEM 是一种 Intune 权限，可以应用于 AAD 用户帐户，并允许用户最多注册 1,000 个设备。 将设备交付给设备的用户之前，使用 DEM 帐户注册和准备设备非常有用。 根据设计，Microsoft Intune 限制为 25 个设备注册管理员 (DEM) 帐户。

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>使用 DEM 帐户注册的设备限制

使用 DEM 用户帐户注册的 DEM 用户帐户和设备具有以下限制：

- 必须为 DEM 帐户用户分配 Intune 许可证。
- 无法通过公司门户进行擦除。 可以从 Azure 门户中的 Intune 擦除通过 DEM 用户帐户注册的设备。
- 公司门户应用或网站中仅显示本地设备。
- 由于应用管理的每用户 Apple ID 要求，DEM 用户帐户无法将 Apple 批量购买计划 (VPP) 应用与 Apple VPP 用户许可证一起使用。
- 如果设备具有 Apple VPP 许可证，则可以安装 VPP 应用。
- 设备出于条件访问而被阻止，Windows 10 1803+ 除外
- 向 DEM 帐户注册的每台设备都需要获得适当许可才能由 Intune 托管。 许可证可以是 Intune 用户许可证，也可以是 Intune 设备许可证。
- 如果使用 DEM 帐户[注册 Android Enterprise 工作配置文件设备](android-work-profile-enroll.md)，则每个帐户最多可注册 10 台设备。


## <a name="add-a-device-enrollment-manager"></a>添加一个设备注册管理器

1. 在 [Azure 门户中的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “设备注册管理员”   。

2. 选择“添加”  。

3. 在“添加用户”  边栏选项卡上，输入 DEM 用户的用户主体名称，并选择“添加”  。 DEM 用户将添加到 DEM 用户列表。

## <a name="permissions-for-dem"></a>DEM 的权限

需要全局管理员或 Intune 服务管理员 Azure AD 角色
- 才能为 Azure AD 用户帐户分配 DEM 权限
- 查看全部 DEM 用户

如果用户未分配到全局管理员或 Intune 服务管理员角色，但分配给他们的设备注册管理器角色启用了读取权限，则这些用户将只能查看自己创建的 DEM 用户。


## <a name="remove-device-enrollment-manager-permissions"></a>删除设备注册管理器权限

删除设备注册管理器不会影响已注册的设备。

**删除设备注册管理器**

1. 在 [Azure 门户中的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册”，然后选择“设备注册管理器”   。
2. 在“设备注册管理员”边栏选项卡上，选择 DEM 用户，然后选择“删除”   。

