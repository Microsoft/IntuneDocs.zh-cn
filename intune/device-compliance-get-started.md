---
title: "Intune 设备符合性策略"
titleSuffix: Azure portal
description: "通过本主题了解 Microsoft Intune 中的设备符合性"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa78383233950e342c5ab0f83095bba3c8fda1f9
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="get-started-with-intune-device-compliance-policies"></a>Intune 设备符合性策略入门

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="what-is-device-compliance-in-intune"></a>什么是 Intune 中的设备符合性？

Intune 设备符合性策略定义设备必须遵从的规则和设置，以便将设备视为符合 Intune。

这些规则包括以下内容：

- 使用密码来访问设备

- 加密

- 设备是否越狱或取得 root 权限

- 所需的最低操作系统版本

- 允许的最高操作系统版本

- 要求设备不高于移动威胁防御级别

也可使用设备符合性策略来监视设备的符合性状态。

### <a name="device-compliance-requirements"></a>设备合规性要求

合规性要求本质上是规则，如针对某个合规性策略，根据实际所需来要求是否指定设备 PIN 或加密。

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be non-compliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

##  <a name="pre-requisites"></a>先决条件

需要具有以下订阅才能使用 Intune 设备符合性策略：

- Intune EMS

- Azure AD 高级版

###  <a name="supported-platforms"></a>受支持的平台：

-   Android

-   iOS

-   macOS（预览）

-   Windows 8.1

-   Windows Phone 8.1

-   Windows 10

> [!IMPORTANT]
> 设备必须注册到 Intune 才能报告其符合性状态。

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Intune 设备符合性策略如何与 Azure AD 配合使用

当设备注册到 Intune 时，会发生 Azure AD 注册过程，这将具有更多信息的设备属性更新到 Azure AD。 其中一个关键设备信息就是设备符合性状态，条件访问策略使用该状态阻止或允许访问电子邮件和其他公司资源。

- 详细了解 [Azure AD 注册流程](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-overview)。

##  <a name="ways-to-use-device-compliance-policies"></a>使用设备符合性策略的方式

### <a name="with-conditional-access"></a>使用条件访问
可以将符合性策略与条件访问结合使用，以便只允许符合一个或多个设备符合性策略规则的设备访问电子邮件和其他公司资源。

### <a name="without-conditional-access"></a>不使用条件访问
还可以使用独立于条件访问的设备符合性策略。 独立使用合规性策略时，会评估目标设备并报告其相容性状态。 例如，你可以获取有关未加密的设备数，或哪些设备已越狱或取得 root 权限的报告。 但是独立使用合规性策略时，不会实施对公司资源的访问限制。

将合规性策略部署到用户。 将合规性策略部署到用户后，会对用户设备检查合规性。 若要了解策略部署完成后，移动设备需要多长时间获取策略，请参阅“管理设备上的设置和功能”。

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>在 Intune 经典门户与 Azure 门户中使用设备符合性策略

请注意主要区别，以帮助用户在 Azure 门户中实现过渡到新的设备符合性策略的工作流。

- 在 Azure 门户中，合规性策略是针对每个受支持的平台单独创建的。
- 在 Intune 经典门户中，一个设备符合性策略普遍适用于所有受支持的平台。

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>将设备符合性策略从 Intune 经典门户迁移到 Azure 门户

在 [Intune 经典门户](https://manage.microsoft.com)中创建的设备符合性策略不会出现在新的 [Intune Azure 门户](https://portal.azure.com)中。 但是，它们仍面向用户并且可以通过 Intune 经典门户进行管理。

如果想要利用 Azure 门户中新设备符合性相关的功能，需要在 Azure 门户中创建新的设备符合性策略。 如果在 Azure 门户中向某个用户分配新的设备符合性策略，但该用户同时还分配有 Intune 经典门户的设备符合性策略，则 Intune Azure 门户中的设备符合性策略优先于在 Intune 经典门户中创建的策略。

##  <a name="next-steps"></a>后续步骤

为以下平台创建设备符合性策略：

- [Android](compliance-policy-create-android.md)
- [Android for Work](compliance-policy-create-android-for-work.md)
- [iOS](compliance-policy-create-ios.md)
- [macOS](compliance-policy-create-mac-os.md)
- [Windows](compliance-policy-create-windows.md)
