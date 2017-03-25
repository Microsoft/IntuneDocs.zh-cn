---
title: "Microsoft Intune 预览版新增功能"
titleSuffix: Intune Azure preview
description: "了解 Intune Azure 预览版新增功能"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 92bb81440b9374b2b0b433b32fc0a1301998ea80
ms.lasthandoff: 03/15/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Microsoft Intune 预览版新增功能

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

随着公共预览版的不断改进，添加了更多功能，以下是相关介绍。

> [!Note]
> 此页上提供了针对 Azure 门户预览列出的更改。 但是，鉴于 Intune 服务的更新方式，所做的更改可能无法立即使用。  在新门户功能可用之前，必须按顺序更新服务的多个组件。 在本月晚些时候推出时查找这些更改。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>对 iOS 丢失模式的支持<!--431695-->

对于 iOS 9.3 和更高版本设备，Intune 增加了对**丢失模式**的支持。 现在可以锁定设备以防止所有使用并显示设备锁定屏幕的消息和联系人电话号码。

最终用户将无法解锁设备，直到管理员禁用丢失模式。 启用丢失模式后，可以使用查找设备操作在 Intune 控制台中的地图上显示该设备的地理位置。

有关详细信息，请参阅[什么是 Microsoft Intune 设备管理](/intune-azure/manage-devices/what-is)？

### <a name="improvements-to-device-actions-report---677150--"></a>改进设备操作报告<!--677150-->

改进了设备操作报告，进而改善了性能。 此外，现可按状态筛选报告。 例如，可筛选报告以仅显示“已完成”的设备操作。

### <a name="actions-for-non-compliance---730266--"></a>针对不合规的操作<!--730266-->

“针对不合规的操作”是合规性策略的新功能，允许在不合规的设备上执行操作。 可指定单个或多个操作，并指定这些操作必然会发生的时间段。 例如，可在设备变为不合规后，立即通过电子邮件通知该不合规设备的用户，或可在 3 天宽限期后，通过条件性访问阻止不合规设备访问公司资源。

### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->

现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。
请参阅[如何将应用添加到 Intune](/intune-azure/manage-apps/add-apps)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>将 LOB 应用分配给未注册设备的用户<!--748823-->

现在，无论用户的设备是否已注册 Intune，都可以从应用商店向用户分配业务线应用。 如果用户设备未注册 Intune，他们必须转到公司门户网站（而非公司门户应用）安装它。

### <a name="new-compliance-reports---846671--"></a>新符合性报告<!--846671-->

现可通过符合性报告了解设备在公司中的符合性状态，以便快速解决用户遇到的与符合性相关的问题。 可查看以下相关信息

- 设备的总体符合性状态
- 单个设置的符合性状态
- 单个策略的符合性状态

还可使用这些报告向下钻取各个设备，查看影响该设备的特定设置和策略。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->

对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。


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

### <a name="configure-windows-update-for-business-settings---776716--"></a>配置 Windows Update for Business 设置<!--776716-->

Windows 即服务是为 Windows 10 提供更新的新方式。 从 Windows 10 开始，任何新的功能更新和质量更新都将包含所有此前更新的内容。 这意味着，只要安装了最新更新，你的 Windows 10 设备将完全保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。

借助 Windows Update for Business 可以简化更新管理体验，不需要批准设备组的单个更新。 通过配置更新推出策略仍可以管理环境中的风险，并且 Windows 更新将确保在适当的时间安装更新。 Microsoft Intune 提供在设备上配置更新设置的功能，使你能够延迟更新安装。 Intune 不会存储更新，仅存储更新策略分配。 设备直接访问 Windows 更新以进行更新。使用 Intune 来配置和管理 **Windows 10 更新通道**。 更新通道包含一组设置，可配置何时以及如何安装 Windows 10 更新。 有关详细信息，请参阅[配置 Windows Update for Business 设置](/intune-azure/configure-devices/how-to-configure-windows-update-for-business)。

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

