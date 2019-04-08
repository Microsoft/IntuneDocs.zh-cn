---
title: 防止非受管理设备上的数据泄露
titleSuffix: Microsoft Intune
description: 允许使用 Microsoft Intune 在设备上访问公司数据并防止数据泄漏。
keywords: 数据保护 防止泄漏 设备 O365 Office 365
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 324187db4951ffb6b80e9cc488a2a0fb59f40a9a
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799365"
---
# <a name="prevent-data-leaks-on-non-managed-devices-using-microsoft-intune"></a>使用 Microsoft Intune 防止非受管理设备上的数据泄露

如果允许访问由 Office 365 托管的公司数据，可控制用户如何共享和保存数据，而规避有意或意外数据泄露的风险。 Microsoft Intune 提供应用保护策略，设置这些策略，可在用户拥有的设备上保护公司数据。 不需要在 Intune 服务中注册设备。 

使用 Intune 设置的应用保护策略在不由 Microsoft 设备管理解决方案管理的设备上也有效。 不会涉及设备上的个人数据；只有公司数据由 IT 部门管理。 

可在运行 Windows、iOS 或 Android 的设备上为 Office 移动应用设置应用保护策略，以保护公司数据。 通过这些策略，设可以置基于应用的 PIN 或公司数据加密等策略，或更高级的设置，以限制用户能否在托管和非托管应用间使用剪切、复制、粘贴和另存为功能。 而且无需用户注册设备，即可远程擦除公司数据。 

Intune 应用保护策略独立于设备管理。 通过应用保护策略，可管理在托管设备和由 Intune 或非 Microsoft MDM 解决方案管理的设备上的 Office 移动应用。 

## <a name="before-you-begin"></a>在开始之前

满足以下要求，可使用以下操作计划：
* 你的公司已准备好安全转换到云。
* 你的公司使用 Office 365 Exchange Online、SharePoint Online、OneDrive for Business 或 Yammer。
* 你的公司拥有 Microsoft 365、企业移动性 + 安全性 (EMS) 或 Azure 信息保护的许可证。
* 你的公司允许用户从公司拥有或个人拥有的 Windows、iOS 或 Android 设备访问公司数据。 
* 你的公司不会要求在设备管理服务中注册个人拥有的设备。 

## <a name="action-plan"></a>操作计划

对于 iOS 和 Android 设备： 

1. 了解[应用保护策略](app-protection-policy.md)的工作原理。
2. 了解如何为 Office 移动应用[创建和部署应用保护策略](app-protection-policies.md)。 
3. [监视你创建和部署的应用保护策略](app-protection-policies-monitor.md)。 

对于 Windows 10 设备： 

1. 了解 [Windows 信息保护 (WIP) 的工作原理](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip)。 
2. 准备好配置[面向 Windows 10 的应用保护策略](app-protection-policies-configure-windows-10.md)
3. [通过 Intune 创建和部署 WIP 应用保护策略](windows-information-protection-policy-create.md)

## <a name="what-to-tell-employees-and-students"></a>应告知员工和学生的事项

根据需要，共享以下链接以提供额外信息： 
* [iOS 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-ios.md)
* [Android 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-android.md) 

## <a name="next-steps"></a>后续步骤

需要有关启用此方案或者其他 EMS 或 Office 365 方案的帮助？ 对于 Microsoft 365、企业移动性 + 安全性或 Azure Active Directory Premium，如果你拥有至少 150 个许可证，请使用 [FastTrack 权益](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program)。 
