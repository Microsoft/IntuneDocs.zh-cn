---
title: Microsoft Intune 中的设备符合性策略 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中：使用设备符合性策略的要求，状态和严重性级别概述，使用 InGracePeriod 状态，使用条件访问，处理不具有分配策略的设备，以及 Azure 门户和经典门户中的符合性的差别
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 806df8077045a4ad81cb7e221bd053059461a2fd
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199398"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Intune 中的设备符合性策略入门

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

为了有助于保护组织数据，许多移动设备管理 (MDM) 解决方案都会要求用户和设备必须符合一些要求。 在 Intune 中，此功能称为“符合性策略”。 符合性策略定义了用户和设备符合要求所必须满足的规则和设置。 通过结合使用条件访问，管理员可以阻止不符合规则的用户和设备。 例如，Intune 管理员可以要求：

- 最终用户必须使用密码，才能访问移动设备上的组织数据

- 设备不得越狱，也不得取得 root 权限

- 设备上的最低或最高操作系统版本

- 设备不高于某个威胁级别

还可以使用设备符合性策略来监视设备的符合性状态。

> [!IMPORTANT]
> Intune 对设备上的所有符合性评估遵循设备签入计划。 [详细了解设备签入计划](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)。

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="prerequisites"></a>必备条件

若要使用设备符合性策略，请务必：

- 使用以下订阅：

  - Intune
  - Azure Active Directory (AD) Premium

- 使用支持的平台：

  - Android
  - iOS
  - macOS（预览）
  - Windows 8.1
  - Windows Phone 8.1
  - Windows 10

- 在 Intune 中注册设备，以查看符合性状态

- 向一个用户设备注册，或在没有主要用户的情况下注册。 不支持向多个用户注册设备。

## <a name="how-device-compliance-policies-work-with-azure-ad"></a>设备符合性策略如何与 Azure AD 配合使用

当设备注册到 Intune 时，Azure AD 注册过程会启动，这可将设备属性更新到 Azure AD。 设备符合性状态是一项关键信息。 条件访问策略使用该符合性状态阻止或允许访问电子邮件和其他公司资源。

请参阅 [Azure AD 注册过程](https://docs.microsoft.com/azure/active-directory/device-management-introduction)了解详细信息。

## <a name="refresh-cycle-times"></a>刷新周期时间

检查符合性时，Intune 使用的刷新周期与配置文件相同。 通常情况下，刷新周期时间为：

- iOS：每 6 小时一次
- macOS：每 6 小时一次
- Android：每 8 小时一次
- 作为设备注册的 Windows 10 电脑：每 8 小时一次
- Windows Phone：每 8 小时一次
- Windows 8.1：每 8 小时一次

在设备注册后，系统便会立即更频繁地执行符合性检查。

### <a name="assign-an-ingraceperiod-status"></a>分配 InGracePeriod 状态

符合性策略的 InGracePeriod 状态是一个值。 该值由设备的宽限期和设备针对该符合性策略的实际状态共同确定。

具体而言，如果设备的已分配符合性策略为“不符合”状态，且：

- 设备未分配到宽限期，则符合性策略的指定值为“不符合”
- 设备具有已到期的宽限期，则符合性策略的指定值为“不符合”
- 设备具有将来的宽限期，则符合性策略的指定值为“InGracePeriod”

下表概述了这些情况：

|实际符合性状态|指定的宽限期的值|有效符合性状态|
|---------|---------|---------|
|不符合 |未指定宽限期 |不符合 |
|不符合 |过去的日期|不符合|
|不符合 |将来的日期|InGracePeriod|

有关监视设备符合性策略的详细信息，请参阅[监视 Intune 设备符合性策略](compliance-policy-monitor.md)。

### <a name="assign-a-resulting-compliance-policy-status"></a>分配生成的符合性策略状态

如果设备具有多个符合性策略，且该设备分配到的两个或多个符合性策略的符合性状态各不相同，则系统会分配单个生成的符合性状态。 此分配基于向每个符合性状态指定的概念严重性级别。 每个符合性状态均包含以下严重性级别：

|状态  |严重性  |
|---------|---------|
|Unknown     |1|
|不适用     |2|
|是否满足条件|3|
|InGracePeriod|4|
|不符合|5|
|错误|6|

设备具有多个符合性策略时，系统会为该设备分配所有策略中的最高严重性级别。

例如，假设设备分配到三个符合性策略：一个处于“未知”状态（严重性 = 1），一个处于“符合”状态（严重性 = 3），还有一个处于 InGracePeriod 状态（严重性 = 4）。 InGracePeriod 状态具有最高严重性级别，因此所有三个策略将具有 InGracePeriod 符合性状态。

## <a name="ways-to-use-device-compliance-policies"></a>使用设备符合性策略的方式

#### <a name="with-conditional-access"></a>使用条件访问
对于符合策略规则的设备，可为这些设备提供访问电子邮件和其他公司资源的权限。 如果设备不符合策略规则，则无法获得访问公司资源的权限。 这就是条件访问。

#### <a name="without-conditional-access"></a>不使用条件访问
还可在不使用任何条件访问的情况下使用设备符合性策略。 独立使用合规性策略时，会评估目标设备并报告其相容性状态。 例如，可以生成报告，了解未加密的设备数，或哪些设备已越狱或取得 root 权限。 如果在不使用条件访问的情况下使用符合性策略，对组织资源没有任何访问限制。

## <a name="ways-to-deploy-device-compliance-policies"></a>部署设备符合性策略的方法
可向用户组中的用户或设备组中的设备部署符合性策略。 将符合性策略部署到用户后，会对所有用户设备检查符合性。 在 Windows 10 版本 1803 和更高版本的设备上，如果主要用户未注册设备，则建议部署到设备组。 在此方案中使用设备组有助于生成符合性报告。

在所有已注册 Intune 的设备上评估一组内置的符合性策略设置（“Intune” > “设备符合性”）。 这些地方包括：

- **将未分配到符合性策略的设备标记为**：此属性有两个值：

  - **符合**：安全功能关闭
  - **不符合**（默认值）：安全功能开启

  如果设备未分配到符合性策略，则此设备被视为不符合。 默认情况下，设备将被标记为“不符合”。 如果使用条件访问，建议将设置更改为“不符合”。 如果最终用户因未分配有策略而不符合要求，公司门户会显示“`No compliance policies have been assigned`”。

- **增强型越狱检测**：启用后，此设置会导致 iOS 设备更频繁地使用 Intune 签入。 启用此属性将使用设备的位置服务，而且会影响电池的使用。 Intune 不会存储用户位置数据。

  启用此设置要求设备：
  - 在 OS 级别启用位置服务
  - 允许公司门户使用位置服务
  - 评估其越狱状态并且至少每 72 小时向 Intune 报告一次。 否则，设备将标记为“不符合”。 通过打开公司门户应用或将设备移动 500 米或更远距离来触发评估。 如果设备在 72 小时内未移动 500 米，则用户需要打开公司门户应用，以增强越狱评估。

- **符合性状态有效期(天)**：输入设备报告所有已收到符合性策略的状态的时间段。 未在此时间段内返回状态的设备将被视为“不符合”。 默认值为 30 天。

所有设备都具有“内置设备符合性策略”（“Azure 门户”>“设备符合性”>“策略符合性”）。 使用此内置策略监视这些设置。

若要了解策略部署完成后，移动设备获取策略所用的时间，请参阅[设备配置文件疑难解答](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)。

使用符合性报告是检查设备状态的有效方法。 对于相关指导，请参阅[监视符合性策略](compliance-policy-monitor.md)。

### <a name="actions-for-noncompliance"></a>对不符合设备的操作
可配置按时间顺序排列的操作序列，并将其应用到不满足符合性策略条件的设备。 这些不符合性操作可以自动完成，请参阅[自动执行不符合性操作](actions-for-noncompliance.md)中的说明。

## <a name="azure-classic-portal-vs-azure-portal"></a>Azure 经典门户与 Azure 门户

在 Azure 门户中使用设备符合性策略的主要区别：

- 在 Azure 门户中，符合性策略针对每个受支持的平台单独创建
- 在 Azure 经典门户中，一个设备符合性策略普遍适用于所有受支持的平台

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>经典门户和 Azure 门户中的设备符合性策略

在[经典门户](https://manage.microsoft.com)中创建的设备符合性策略不会出现在 [Azure 门户](https://portal.azure.com)中。 但它们仍面向用户并且可以通过经典门户进行管理。

要在 Azure 门户中使用设备符合性的相关功能，则必须在 Azure 门户中创建新的设备符合性策略。 如果在 Azure 门户中向某个用户分配设备符合性策略，但该用户同时还分配有经典门户的设备符合性策略，则 Azure 门户中的设备符合性策略优先于在经典门户中创建的策略。

## <a name="next-steps"></a>后续步骤

- 为以下平台创建设备符合性策略：

  - [Outlook Web Access (OWA)](compliance-policy-create-android.md)
  - [Android 工作配置文件](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 有关 Intune 数据仓库策略实体的信息，请参阅[策略实体引用](reports-ref-policy.md)。
