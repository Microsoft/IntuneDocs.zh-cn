---
title: "Check Point SandBlast Mobile 连接器与 Intune"
titleSuffix: Intune on Azure
description: "Check Point SandBlast 与 Intune 集成"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e722411e7eea11a604cdd2c6f7f818053d0ffbb0
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2017
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Check Point SandBlast 移动威胁防御连接器与 Intune

可根据 Check Point SandBlast Mobile 给出的风险评估，使用条件访问控制移动设备对公司资源的访问，Check Point SandBlast Mobile 是与 Microsoft Intune 集成的移动威胁防御解决方案。 基于从运行 Check Point SandBlast Mobile 应用的设备收集的遥测评估风险。

可以基于通过 Intune 设备符合性策略启用的 Check Point SandBlast Mobile 风险评估配置条件访问策略，从而根据检测到的威胁允许或阻止不符合要求的设备访问公司资源。

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>Intune 和 Check Point SandBlast Mobile 如何帮助你保护公司资源？

适用于 Android 或 iOS 的 Check Point Sandblast Mobile 应用可捕获文件系统、网络堆栈，以及设备和应用程序遥测（如果有），然后将遥测数据发送到 Check Point Sandblast 云服务，评估设备的移动威胁风险。

Intune 设备符合性策略包括基于 Check Point SandBlast 风险评估的 Check Point SandBlast Mobile 威胁防御规则。 启用此规则后，Intune 将评估设备是否符合已启用的策略。 如果发现设备不符合策略，将阻止对 Exchange Online 和 SharePoint Online 等公司资源的访问。 用户还可通过安装在设备上的 Check Point Sandblast Mobile 应用获取指导，以便解决问题并重新访问公司资源。

<!-- ## Sample scenarios

Here are some common scenarios:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

-   Connecting to corporate e-mail

-   Syncing corporate files with the OneDrive for Work app

-   Accessing company apps

**Block when malicious apps are detected:**

![Check Point MTD block when malicious apps are detected](./media/checkpoint-MTD-2.PNG)

**Access granted on remediation:**

![Check Point MTD access granted](./media/checkpoint-MTD-3.PNG)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

**Block network access through Wi-Fi:**

![Check Point MTD block network access through Wi-Fi](./media/checkpoint-MTD-4.PNG)

**Access granted on remediation:**

![Check Point MTD Wi-Fi access granted](./media/checkpoint-MTD-5.PNG)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

**Block SharePoint Online when network threats are detected:**

![Check Point MTD block SharePoint Online access](./media/checkpoint-MTD-6.PNG)

**Access granted on remediation:**

![Check Point MTD SharePoint Online access granted](./media/checkpoint-MTD-7.PNG)

## Supported platforms

-   **Android 4.1 and later**

-   **iOS 8 and later**

## Pre-requisites

-   Azure Active Directory Premium

-   Microsoft Intune subscription

-   Check Point SandBlast Mobile Threat Defense subscription
    -   See [CheckPoint SandBlast website](https://www.checkpoint.com/) for more information.

## Next steps

[Set up CheckPoint SandBlast Mobile app](mtd-apps-ios-app-configuration-policy-add-assign.md)

[Integrate CheckPoint SandBlast with Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

[Enable CheckPoint SandBlast Mobile MTD connector](mtd-connector-enable.md)

[Create CheckPoint SandBlast Mobile device compliance policy](mtd-device-compliance-policy-create.md)
