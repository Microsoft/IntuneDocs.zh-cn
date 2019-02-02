---
title: Microsoft Intune 对公司有何作用
titleSuffix: ''
description: Microsoft Intune 有助于解决常见业务问题。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: c8e15675beb97b396c9340e2ab3bfa86a3a43f76
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831422"
---
# <a name="what-can-intune-do-for-my-company"></a>Intune 可以为公司带来什么好处？
Microsoft Intune 是一种基于云的企业移动管理 (EMM) 服务，可帮助员工提高工作效率，同时保护企业数据。

通过 Intune，还可以：

- 管理员工用于访问公司数据的移动设备。
- 管理员工使用的移动应用。
- 通过帮助控制员工访问和共享公司信息的方式来保护公司信息。
- 确保设备和应用符合公司安全要求。

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune 可帮助解决的常见业务问题

* [保护本地电子邮件和数据以供移动设备访问](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [保护 Office 365 电子邮件和数据以供移动设备安全访问](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [向员工发放公司拥有的手机](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [为所有员工提供一个“自带设备办公”(BYOD) 或个人设备计划](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [允许员工从不受管理的公用网亭安全访问 Office 365](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [向任务工作者发放使用受限的共享平板电脑](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>快速入门

我们了解移动设备管理的最初阶段并不容易，因为你需要代表公司做出各种不同的决策。 以下快速入门帮助你开始使用 Intune，并在最短的时间内完成一些常见任务。

可使用页面左侧的目录，按照相应的快速入门顺序进行学习。

- [免费试用 Intune](free-trial-sign-up.md) - 创建免费订阅以在测试环境中试用 Intune。    
- [创建用户](quickstart-create-user.md) - 向 Intune 添加用户，使用户在移动设备上访问公司资源。
- [创建组](quickstart-create-group.md) - 将用户归组，以便更轻松地管理策略和用户对应用的访问权限。
- [设置自动注册](quickstart-setup-auto-enrollment.md) - 将 Microsoft Intune 设置为在特定用户登录到 Windows 10 设备时自动注册设备。
- [注册设备](quickstart-enroll-windows-device.md) - 使用 Intune 用户角色并将设备注册到 Microsoft Intune。 然后，返回到 Intune 并确认已注册的设备。
- [创建设备符合性策略](quickstart-set-password-length-android.md) - 创建设备符合性策略并为策略分配组。
- [向不符合要求的设备发送通知](quickstart-send-notification.md) - 通过创建和分配符合性策略，向使用不符合要求的设备的员工发送电子邮件通知。
- [添加和分配应用](quickstart-add-assign-app.md) - 添加客户端应用并将其分配给公司的员工。
- [创建和分配应用保护策略](quickstart-create-assign-app-policy.md) - 创建应用保护策略并将其分配给最终用户设备上的客户端应用。
- [创建和分配自定义角色](quickstart-create-custom-role.md) - 创建并分配具有安全操作部门的特定权限的自定义角色。 
- [创建用于 iOS 的电子邮件设备配置文件](quickstart-email-profile.md) - 创建用于 iOS 设备的电子邮件设备配置文件。

## <a name="prerequisites"></a>必备条件

在开始之前，必须激活 Intune 管理员和租户帐户。 创建免费订阅以在测试环境中[免费试用 Intune](free-trial-sign-up.md)。 当前订阅者还可以在实时租户中完成这些活动。 这些入门文章假设你在测试设备上执行操作。

为了完成所有的入门任务，还需要确保你是组织的全局管理员。

## <a name="intune-architecture"></a>Intune 体系结构

Intune 是企业移动性 + 安全性 (EMS) 的组件，可用于管理移动设备和应用。 它与 Azure Active Directory (Azure AD) 等其他 EMS 组件紧密集成以实现标识和访问控制，并与 Azure 信息保护集成以实现数据保护。 将它与 Office 365 结合使用时，员工可以在其设备上高效工作，同时保护组织的信息。

![Microsoft Intune 的高级体系结构图表](/intune/media/intunearchitecture.svg)

## <a name="next-steps"></a>后续步骤

[Azure 使用入门](get-started-azure.md) - 了解 Azure 门户的结构，以及如何更改看到的页面。

## <a name="learn-more"></a>了解详细信息

* [什么是 Intune？](introduction-intune.md)
* [什么是 Azure 门户？](what-is-intune.md)
* [设备和应用生命周期](introduction-device-app-lifecycles.md)