---
title: "设备合规性"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：通过本主题了解 Microsoft Intune 中的设备合规性"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: cddeb6bf854b9ffbbc1744d5d164c8ceea34ff49
ms.openlocfilehash: 7d5a1859ef1a373ce424dd4f351fc137c6052fb7
ms.lasthandoff: 03/10/2017


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>什么是 Intune Azure 预览版中的设备合规性？

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 中的设备符合性策略定义设备必须遵从的规则和设置，以便将设备视为符合 Intune 和 EMS 条件访问策略。 也可使用设备符合性策略来监视和修正设备的符合性问题。 

这些规则包括以下内容：

- 使用密码来访问设备
- 加密
- 设备是否越狱或取得 root 权限
- 所需的最低操作系统版本
- 允许的最高操作系统版本
- 要求设备不高于移动威胁防御级别

<!---##  Concepts
Following are some terms and concepts that are useful to understanding how to use compliance policies.

### Device compliance requirements
Compliance requirements are essentially rules like requiring a device PIN or encryption that you can specify as required or not required for a compliance policy.

### Actions for noncompliance

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

##  <a name="how-should-i-use-a-device-compliance-policy"></a>应如何使用设备合规性策略？

### <a name="using-ems-conditional-access"></a>使用 EMS 条件访问
可以将符合性策略与 EMS 条件访问结合使用，以便只允许符合一个或多个设备符合性策略规则的设备访问电子邮件和其他公司资源。

### <a name="not-using-ems-conditional-access"></a>不使用 EMS 条件访问
还可以使用独立于 EMS 条件访问的设备符合性策略。
独立使用合规性策略时，会评估目标设备并报告其相容性状态。 例如，你可以获取有关未加密的设备数，或哪些设备已越狱或取得 root 权限的报告。 但是独立使用合规性策略时，不会实施对公司资源的访问限制。

将合规性策略部署到用户。 将合规性策略部署到用户后，会对用户设备检查合规性。 若要了解策略部署完成后，移动设备需要多长时间获取策略，请参阅“管理设备上的设置和功能”。

##  <a name="intune-classic-admin-console-vs-intune-azure-preview-portal"></a>Intune 经典管理员控制台与Intune Azure 预览门户

如果你一直使用 Intune 经典管理控制台，请注意以下差异，以帮助转换到 Azure 门户中的新设备符合性策略工作流：

-   在 Azure 门户中，合规性策略是针对每个受支持的平台单独创建的。 在 Intune 管理控制台中，一个合规性策略普遍适用于所有受支持的平台。

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>后续步骤

[设备符合性策略入门](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->

