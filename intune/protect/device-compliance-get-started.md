---
title: Microsoft Intune 中的设备符合性策略 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中：开始使用设备符合性策略，状态和严重性级别概述，使用 InGracePeriod 状态，使用条件访问，处理不具有分配策略的设备，以及 Azure 门户和经典门户中的符合性的差别
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 967bf9937c71ff3ca7277f43fd969291eb5af6de
ms.sourcegitcommit: c2e62f1ebdf75599c8e544287123c602f0f15f2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72749173"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>在设备上设置规则以允许使用 Intune 访问组织中的资源

为了有助于保护组织数据，许多移动设备管理 (MDM) 解决方案都会要求用户和设备必须符合一些要求。 在 Intune 中，此功能称为“符合性策略”。 符合性策略定义了用户和设备符合要求所必须满足的规则和设置。 通过结合使用条件访问，管理员可以阻止不符合规则的用户和设备。

例如，Intune 管理员可以要求：

- 最终用户必须使用密码，才能访问移动设备上的组织数据
- 设备不得越狱，也不得取得 root 权限
- 设备上的最低或最高操作系统版本
- 设备不高于某个威胁级别

还可以使用此功能来监视组织中设备的符合性状态。

> [!IMPORTANT]
> Intune 对设备上的所有符合性评估遵循设备签入计划。 [策略和配置文件刷新周期](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)列出了估计的刷新时间。

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>设备符合性策略与 Azure AD 配合使用

Intune 使用 Azure Active Directory (AD) [条件访问](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)（将打开另一个 Docs 网站）来帮助强制执行符合性。 当设备注册到 Intune 时，Azure AD 注册过程会启动，并且设备信息会更新到 Azure AD。 设备符合性状态是一项关键信息。 条件访问策略使用该符合性状态阻止或允许访问电子邮件和其他组织资源。

- [什么是 Azure Active Directory 中的设备管理](https://docs.microsoft.com/azure/active-directory/device-management-introduction)是有关在 Azure AD 中注册设备的原因和方式的不错资源。

- [条件访问](conditional-access.md)和[条件访问的常见使用方式](conditional-access-intune-common-ways-use.md)介绍了此功能，因为它与 Intune 相关。

## <a name="ways-to-use-device-compliance-policies"></a>使用设备符合性策略的方式

### <a name="with-conditional-access"></a>使用条件访问

对于符合策略规则的设备，可为这些设备提供访问电子邮件和其他组织资源的权限。 如果设备不符合策略规则，则无法获得访问组织资源的权限。 这就是条件访问。

### <a name="without-conditional-access"></a>不使用条件访问

还可在不使用任何条件访问的情况下使用设备符合性策略。 独立使用符合性策略时，会评估目标设备并报告其符合性状态。 例如，可以生成报告，了解未加密的设备数，或哪些设备已越狱或取得 root 权限。 如果在不使用条件访问的情况下使用符合性策略，对组织资源没有任何访问限制。

## <a name="ways-to-deploy-device-compliance-policies"></a>部署设备符合性策略的方法

可向用户组中的用户或设备组中的设备部署符合性策略。 将符合性策略部署到用户后，会对所有用户设备检查符合性。 在 Windows 10 版本 1803 和更高版本的设备上，  如果主要用户未注册设备，则建议部署到设备组。 在此方案中使用设备组有助于生成符合性报告。

Intune 还包括一组内置的符合性策略设置。 以下内置策略在已注册到 Intune 的所有设备上进行评估：

- **将未分配到符合性策略的设备标记为**：此属性有两个值：

  - **符合**（默认值）：安全功能关闭 
  - **不符合**：安全功能开启

  如果设备未分配到符合性策略，则此设备在默认情况下被视为符合。 如果结合使用条件访问和符合性策略，建议将默认设置更改为“不符合”  。 如果最终用户因未分配有策略而不符合要求，[公司门户](../apps/company-portal-app.md)会显示“`No compliance policies have been assigned`”。

- **增强型越狱检测**：启用后，此设置会导致 iOS 设备更频繁地使用 Intune 签入。 启用此属性将使用设备的位置服务，而且会影响电池的使用。 Intune 不会存储用户位置数据。

  启用此设置要求设备：
  - 在 OS 级别启用位置服务。
  - 允许公司门户使用位置服务。
  - 评估其越狱状态并且至少每 72 小时向 Intune 报告一次。 否则，设备将标记为“不符合”。 打开公司门户应用或将设备移动 500 米或更远距离会触发评估。 如果设备在 72 小时内未移动 500 米，则用户需要打开公司门户应用，以增强越狱评估。

- **符合性状态有效期(天)** ：输入设备报告所有已收到符合性策略的状态的时间段。 未在此时间段内返回状态的设备将被视为“不符合”。 默认值为 30 天。

可以使用这些内置策略来监视这些设置。 Intune 还会按不同时间间隔[刷新或检查更新](create-compliance-policy.md#refresh-cycle-times)，具体取决于设备平台。 [Microsoft Intune 中设备策略和配置文件的常见疑问、问题和解决方案](../configuration/device-profile-troubleshoot.md)是不错的资源。

使用符合性报告是检查设备状态的有效方法。 [监视符合性策略](compliance-policy-monitor.md)包括一些指导。

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>不同平台上的不符合和条件访问

下表说明了将符合性策略与条件访问策略一起使用时如何管理非符合性设置：

---------------------------

|**策略设置**| **平台** |
| --- | ----|
| **PIN 或密码配置** | - **Android 4.0 及更高版本**：已隔离<br>- **Samsung Knox 标准版 4.0 及更高版本**：已隔离<br>- **Android Enterprise**：已隔离  <br>  <br>- **iOS 8.0 及更高版本**：已修正<br>- **macOS 10.11 及更高版本**：已修正  <br>  <br>- **Windows 8.1 及更高版本**：已修正<br>- **Windows Phone 8.1 及更高版本**：已修正|
| **设备加密** | - **Android 4.0 及更高版本**：已隔离<br>- **Samsung Knox 标准版 4.0 及更高版本**：已隔离<br>- **Android Enterprise**：已隔离<br><br>- **iOS 8.0 及更高版本**：已修正（通过设置 PIN）<br>- **macOS 10.11 及更高版本**：已修正（通过设置 PIN）<br><br>- **Windows 8.1 及更高版本**：“不适用”<br>- **Windows Phone 8.1 及更高版本**：已修正 |
| **已越狱或取得 root 权限的设备** | - **Android 4.0 及更高版本**：已隔离（非设置）<br>- **Samsung Knox 标准版 4.0 及更高版本**：已隔离（非设置）<br>- **Android Enterprise**：已隔离（非设置）<br><br>- **iOS 8.0 及更高版本**：已隔离（非设置）<br>- **macOS 10.11 及更高版本**：“不适用”<br><br>- **Windows 8.1 及更高版本**：“不适用”<br>- **Windows Phone 8.1 及更高版本**：“不适用” |
| **电子邮件配置文件** | - **Android 4.0 及更高版本**：“不适用”<br>- **Samsung Knox 标准版 4.0 及更高版本**：“不适用”<br>- **Android Enterprise**：“不适用”<br><br>- **iOS 8.0 及更高版本**：已隔离<br>- **macOS 10.11 及更高版本**：已隔离<br><br>- **Windows 8.1 及更高版本**：“不适用”<br>- **Windows Phone 8.1 及更高版本**：“不适用” |
| **最低操作系统版本** | - **Android 4.0 及更高版本**：已隔离<br>- **Samsung Knox 标准版 4.0 及更高版本**：已隔离<br>- **Android Enterprise**：已隔离<br><br>- **iOS 8.0 及更高版本**：已隔离<br>- **macOS 10.11 及更高版本**：已隔离<br><br>- **Windows 8.1 及更高版本**：已隔离<br>- **Windows Phone 8.1 及更高版本**：已隔离 |
| **最高操作系统版本** | - **Android 4.0 及更高版本**：已隔离<br>- **Samsung Knox 标准版 4.0 及更高版本**：已隔离<br>- **Android Enterprise**：已隔离<br><br>- **iOS 8.0 及更高版本**：已隔离<br>- **macOS 10.11 及更高版本**：已隔离<br><br>- **Windows 8.1 及更高版本**：已隔离<br>- **Windows Phone 8.1 及更高版本**：已隔离 |
| **Windows 运行状况证明** | - **Android 4.0 及更高版本**：“不适用”<br>- **Samsung Knox 标准版 4.0 及更高版本**：“不适用”<br>- **Android Enterprise**：“不适用”<br><br>- **iOS 8.0 及更高版本**：“不适用”<br>- **macOS 10.11 及更高版本**：“不适用”<br><br>- **Windows 10 和 Windows 10 移动版**：已隔离<br>- **Windows 8.1 及更高版本**：已隔离<br>- **Windows Phone 8.1 及更高版本**：“不适用” |

---------------------------

**已修正**：设备操作系统强制执行符合性。 例如，强制用户设置 PIN。

**已隔离**：设备操作系统不会强制执行符合性。 例如，Android 和 Android Enterprise 设备不强制用户加密设备。 设备不符合时，系统将进行以下操作：

- 如果对用户应用了条件访问策略，设备将被阻止。
- 公司门户应用会就任何符合性问题通知用户。

## <a name="azure-classic-portal-vs-azure-portal"></a>Azure 经典门户与 Azure 门户

在 Azure 门户中使用设备符合性策略的主要区别：

- 在 Azure 门户中，符合性策略针对每个受支持的平台单独创建
- 在 Azure 经典门户中，一个设备符合性策略普遍适用于所有受支持的平台

<!--- - In the Azure portal, you have the ability to specify actions and notifications that are initiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

- In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

在[经典门户](https://manage.microsoft.com)中创建的设备符合性策略不会出现在 [Azure 门户](https://portal.azure.com)中。 但它们仍面向用户并且可以通过经典门户进行管理。

要在 Azure 门户中使用设备符合性的相关功能，则必须在 Azure 门户中创建新的设备符合性策略。 如果在 Azure 门户中向某个用户分配设备符合性策略，但该用户同时还分配有经典门户的设备符合性策略，则 Azure 门户中的设备符合性策略优先于在经典门户中创建的策略。

## <a name="next-steps"></a>后续步骤

- [创建策略](create-compliance-policy.md)并查看先决条件。
- 请查看不同设备平台的符合性设置：

  - [Android
](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows Phone 8.1](compliance-policy-create-windows-8-1.md)
  - [Windows 8.1 及更高版本](compliance-policy-create-windows-8-1.md)
  - [Windows 10 及更高版本](compliance-policy-create-windows.md)

- [策略实体引用](../reports-ref-policy.md)包含有关 Intune 数据仓库策略实体的信息。
