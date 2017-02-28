---
title: "Microsoft Intune 预览版新增功能 | Intune Azure 预览版 | Microsoft Docs"
description: "了解 Intune Azure 预览版新增功能"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9852fdb9d1bfeede4931f0ead2fa0898dfcacb0b
ms.openlocfilehash: a05c7464b3f2fbca467d44218904671529320dda
ms.lasthandoff: 02/15/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Microsoft Intune 预览版新增功能

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

随着公共预览版的不断改进，添加了更多功能，以下是相关介绍。

## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制移动设备注册的功能<!--747600, 795782-->
Intune 新增了注册限制，可控制允许注册的移动设备平台。 Intune 将移动设备平台分为 iOS、macOS，Android、Windows 和 Windows Mobile。

* 限制移动设备注册不会限制电脑客户端注册。  
* 阻止个人自有设备的注册有一个附加选项，该选项仅适用于 iOS 和 Android。

Intune 将所有新设备都标记为个人所有，除非 IT 管理员将设备标记为公司所有，如[本文](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)所述。

### <a name="view-all-actions-on-managed-devices---677150--"></a>查看托管设备上的所有操作<!--677150-->
新添加的__设备操作__报表显示了在设备上执行远程操作（如出厂重置）的操作者，还额外显示了该操作的状态。 请参阅 [What is device management?](https://docs.microsoft.com/intune-azure/manage-devices/what-is)（什么是设备管理？）。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>非托管设备可访问已分配的应用<!--664691-->
公司门户网站上的设计更改之一是，iOS 和 Android 用户能够在其非托管设备上安装分配到的“可用且无需注册”设备。 用户可使用其 Intune 凭据登录到公司门户网站，并查看分配到的应用列表。 “可用且无需注册”应用的应用包可通过公司门户网站进行下载。 需要注册才能安装的应用不受此更改影响，如果用户想安装这类应用，则会提示用户注册其设备。

### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->
现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。
请参阅[如何将应用添加到 Intune](/intune-azure/manage-apps/add-apps)。

### <a name="display-device-categories---814654--"></a>显示设备类别<!--814654-->
现在可以将设备类别作为设备列表中的一列进行查看。 并且还可以在设备属性边栏选项卡的属性部分编辑该类别。 请参阅[如何将应用添加到 Intune](/intune-azure/manage-apps/add-apps)。 

## <a name="january-2017"></a>2017 年 1 月

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>分配业务线应用（无论设备是否注册）<!--748823-->
现在，无论用户的设备是否已注册 Intune，都可以从应用商店向用户分配业务线和应用。 如果用户设备未注册 Intune，他们必须转到公司门户网站（而非公司门户应用）安装它。 请参阅[什么是应用管理](/intune-azure/manage-apps/what-is-app-management)。

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>解决 iOS 设备处于非活动状态，或管理控制台不能与其通信的问题
如果用户的设备失去与 Intune 的联系，可向其提供新的故障排除步骤，帮助他们重新获得公司资源的访问权限。 请参阅[设备处于非活动状态，或管理控制台不能与其通信](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)。

## <a name="december-2016-initial-release"></a>2016 年 12 月（初始版本）

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 门户公开预览版中的电信费用管理集成<!--747605-->
现在，我们将开始在 Azure 门户中预览与第三方电信费用管理 (TEM) 服务的集成。 可以使用 Intune 强制实施对国内和漫游数据使用的限制。 我们将使用 [Saaswedo](http://www.saaswedo.com) 开始这些集成。 若要在试用租户中启用此功能，请[联系 Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

- 将应用从应用商店部署到 iOS、Android 和 Windows 设备并对其进行管理
- 将业务线 (LOB) 应用部署到 iOS、Android 和 Windows 设备并对其进行管理
- 将批量购买应用部署到 iOS 和 Windows 设备并对其进行管理
- 部署和管理适用于 Android、iOS 和 Windows 设备的 Web 应用
- iOS 托管应用配置描述文件
- 配置应用保护策略，并将业务线应用部署到未向 Intune 注册的设备
- VPN 配置文件、每个应用 VPN、Wi-Fi、电子邮件和证书配置文件
- 相容性策略
- Azure AD 的条件性访问
- 本地 Exchange 的条件性访问
- 设备注册
- 基于角色的访问控制

## <a name="deprecated-features-in-the-azure-portal"></a>Azure 门户中的弃用功能

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>支持逐行查看硬件标识符
对于 IMEI 号码和 Apple 序列号，Azure 门户不支持逐行查看硬件标识符。 在经典 Intune 控制台中，可以从逗号分隔值 (.csv) 文件导入详细信息，然后覆盖单个硬件标识符的现有详细信息。 Azure 门户提供一种单一、简化的选项，此选项可自动覆盖所有硬件标识符的详细信息，或忽略现有标识符的新详细信息。

#### <a name="how-this-affects-you"></a>此更改的影响
在 Azure 门户中，你将无法逐行决定要更新哪些国际移动设备标识 (IMEI) 设备。 经典 Intune 控制台将继续支持此功能。

#### <a name="how-to-get-ready-for-this-change"></a>如何针对此更改做好准备
我们提前提供此信息，如果此更改将对你产生影响，你可以提醒支持管理员注意。 预计在 2017 年上半年向 Azure 门户迁移时将继续使用此更改。


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>支持 Apple DEP 中默认的企业设备注册配置文件
Azure 门户不支持 Apple 设备注册计划 (DEP) 设备序列号的“默认”公司设备注册配置文件。 经典 Intune 控制台中提供的此功能将停用，以防止无意中分配配置文件。 在 Azure 门户中，从 Apple DEP 帐户同步的序列号最初将不会分配公司设备注册配置文件。

#### <a name="how-this-affects-you"></a>此更改的影响
在 Azure 门户中，你将无法跨所有 Apple 设备设置默认配置文件策略。 经典 Intune 控制台将继续支持此功能。

#### <a name="how-to-get-ready-for-this-change"></a>如何针对此更改做好准备
我们提前提供此信息，如果此更改将对你产生影响，你可以提醒支持管理员注意。 预计在 2017 年上半年向 Azure 门户迁移时将继续使用此更改。

