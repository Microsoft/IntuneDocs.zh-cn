---
title: "设备合规性 | Intune Azure 预览版 | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: a4254503e4e6b86079f862966dee2727934f1ee6


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>什么是 Intune Azure 预览版中的设备合规性？


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

若要帮助保护公司数据，则需确保用于访问公司应用和数据的设备符合特定规则。 这些规则可能包括使用 PIN 访问设备和加密存储在设备上的数据。 一组这样的规则就称为**合规性策略**。

##  <a name="how-should-i-use-a-device-compliance-policy"></a>应如何使用设备合规性策略？
可以将合规性策略与条件访问结合使用，以便只允许符合合规性策略规则的设备访问电子邮件和其他服务。

还可以使用独立于条件访问的合规性策略。
独立使用合规性策略时，会评估目标设备并报告其相容性状态。 例如，你可以获取有关未加密的设备数，或哪些设备已越狱或取得 root 权限的报告。 但是独立使用合规性策略时，不会实施对公司资源的访问限制。

将合规性策略部署到用户。 将合规性策略部署到用户后，会对用户设备检查合规性。 若要了解策略部署完成后，移动设备需要多长时间获取策略，请参阅“管理设备上的设置和功能”。

##  <a name="concepts"></a>概念
以下是一些有助于理解如何使用合规性策略的术语和概念。

### <a name="compliance-requirements"></a>合规性要求
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

##  <a name="differences-between-the-classic-intune-admin-console-and-intune-in-the-azure-portal"></a>Azure 门户中经典 Intune 管理控制台和 Intune 之间的差异


如果你以前一直使用经典 Intune 管理控制台，请注意以下差异，以帮助转换到 Azure 门户中的新设备合规性工作流：


-   在 Azure 门户中，合规性策略是针对每个受支持的平台单独创建的。 在 Intune 管理控制台中，一个合规性策略普遍适用于所有受支持的平台。


<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>后续步骤

[合规性策略入门](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->



<!--HONumber=Feb17_HO1-->


