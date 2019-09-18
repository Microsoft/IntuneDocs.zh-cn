---
title: 查找 Microsoft Intune 设备的主要用户。
titleSuffix: ''
description: 查找 Intune 设备的主要用户（或用户设备相关性）。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7c0947438b42f4a2fa5ccae8e9cab07a60167ae
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071684"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>查找 Intune 设备的主要用户

主要用户（也称为用户设备相关性）是每个 Intune 设备的属性。 Intune 设备可以分配有零个或一个主要用户。 如果未分配主要用户，则设备称为“共享设备”。

## <a name="how-to-find-a-devices-primary-user"></a>如何查找设备的主要用户

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备”  > 选择一台设备。
3. 在“概述”  页上，选择“查看更多”  ，则会看到列出的主要用户。

## <a name="what-is-the-primary-user"></a>什么是主要用户？
主要用户属性用于将许可的 Intune 用户映射到以下位置的设备：
- 公司门户应用
- 最终用户网站
- IT 专业人员体验（例如 Azure 门户中的故障排除页面）。 这些页面通过使用主要用户将用户帐户映射到设备。    

### <a name="company-portal-app"></a>公司门户应用
公司门户应用要求登录到公司门户的用户帐户是该设备的主要用户。 如果已将另一个用户分配为主要用户，则公司门户会显示一条警告：

“设备已分配给组织中的某人。 就如何成为主要设备用户联系公司支持人员。 你可以继续使用公司门户，但功能将受到限制。”

如果 Intune 设备未分配主要用户，则公司门户应用会将其视为共享设备。 共享设备可通过设备磁贴上显示的“共享”标签直观识别。 在此模式下，公司门户仍可用于请求和安装可用应用。 但是，自助服务操作（重置/重命名/停用）不可用。  

若要显示在共享设备上的公司门户中，必须将可用应用分配给用户组。 它们将安装在系统上下文或用户上下文中，具体取决于 IT 管理员配置应用的方式。 有关应用上下文的详细信息，请参阅[在 Windows 10 设备上安装应用](apps-windows-10-app-deploy.md#installing-apps-on-windows-10-devices)。 此功能要求使用公司门户版本 10.3.4651.0 或更高版本。


## <a name="who-is-assigned-as-the-primary-user"></a>谁被分配为主要用户？
Intune 会在注册过程中或不久后自动将主要用户添加到设备。 注册方法可确定何时将主要用户添加到设备。

| 平台 | 注册方法 | 已分配主要用户 | 已分配主要用户 |
| ---- | ---- | ---- | ---- |
| Windows | 添加工作或学校（用户驱动） | 注册用户 | 在注册过程中 |   
| Windows | 现代应用登录（用户驱动） | 注册用户 | 在注册过程中 | 
| Windows | 仅注册 MDM（用户驱动） | 注册用户 | 在注册过程中 | 
| Windows | Azure AD 联接（全新安装体验） | 注册用户 | 在注册过程中 | 
| Windows | Azure AD 联接（Autopilot 全新安装体验） | 注册用户 | 在注册过程中 | 
| Windows | 仅注册 MDM | 注册用户 | 在注册过程中 | 
| Windows | 混合 AADJ + 自动注册 GPO | 登录到 Windows 的第一个用户 | 当第一个用户登录到 Windows 时| 
| Windows | 共同管理 | 登录到 Windows 的第一个用户 | 当第一个用户登录到 Windows 时 | 
| Windows | Azure AD 联接（批量注册令牌） | 无 | “不适用” | 
| Windows | Azure AD 联接（Autopilot 自部署模式） | 无 | “不适用” | 
| 跨平台 | 使用公司门户应用进行用户驱动的注册 | 注册用户 | 在注册过程中 |
| 跨平台 | 设备注册管理员 (DEM) | 注册 DEM 用户 | 在注册过程中 |
| iOS、macOS | Apple 自动设备注册（具有用户关联的 DEP） | 注册用户 | 在注册过程中 |
| iOS、macOS | Apple 自动设备注册（没有用户关联的 DEP） | 无 | “不适用” |
| Android | Android 公司拥有的专用设备 | 无 | “不适用” |

## <a name="primary-user-and-azure-ad-device-owner"></a>主要用户和 Azure AD 设备所有者
在某些情况下，Intune 主要用户可能与 Azure AD 设备的“所有者”  属性（可在“设备”   > “Azure AD 设备”  下查看）不同。 在将设备注册到 Azure Active Directory 过程中会添加Azure AD 设备所有者。

## <a name="next-steps"></a>后续步骤
[管理 Intune 设备。](device-management.md)
