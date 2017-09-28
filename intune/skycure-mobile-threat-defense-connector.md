---
title: "使用 Intune 的 Skycure 连接器"
titlesuffix: Azure portal
description: "将 Skycure 连接器与 Intune 集成。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47df2c4a909c397ac5a6c0f736d11344de44736e
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2017
---
# <a name="skycure-mobile-threat-defense-connector"></a>Skycure 移动威胁防御连接器

可根据 Skycure 给出的风险评估，使用条件访问控制移动设备对公司资源的访问，Skycure 是与 Microsoft Intune 集成的移动威胁防御解决方案。 风险评估基于从运行 Skycure 的设备收集的遥测，包括：

-   物理防御

-   网络防御

-   应用程序防御

-   漏洞防御

可以基于通过 Intune 设备符合性策略启动的 Skycure 风险评估配置条件访问策略，从而根据检测到的威胁允许或阻止不符合要求的设备访问公司资源。

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>Intune 和 Skycure 如何帮助你保护公司资源？

适用于 Android 或 iOS 的 Skycure 移动应用可捕获文件系统、网络堆栈以及设备和应用程序遥测（如果有），然后将其发送到 Skycure 云服务，评估设备的移动威胁风险。

Intune 设备符合性策略包括基于 Skycure 风险评估的 Skycure 移动威胁防御规则。 启用此规则后，Intune 将评估设备是否符合已启用的策略。

如果发现设备不符合策略，将阻止对 Exchange Online 和 SharePoint Online 等资源的访问。 被阻止的设备上的用户可从 Skycure 移动应用接收指导来解决此问题，并重新获得对公司资源的访问权限。

Intune 支持与 Skycure 集成的两种模式：

-   **基本设置**为只读模式，Intune 中的设备在该模式下对 Skycure 可见。

-   **完全集成**允许 Skycure 向 Intune 报告设备风险和安全事件的详细信息。

## <a name="sample-scenarios"></a>示例方案

以下是一些常见方案：

### <a name="control-access-based-on-threats-from-malicious-apps"></a>基于来自恶意应用的威胁来控制访问

在设备上检测到恶意应用（如恶意软件）时，可阻止设备，直到解除威胁：

-   连接到公司电子邮件

-   使用 OneDrive for Work 应用同步企业文件

-   访问公司应用

**检测到恶意应用时对其进行阻止：**

![检测到恶意应用](./media/skycure-arch-1.png)

**威胁解除后授予访问权限：**

![检测到恶意应用，授予访问权限](./media/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>基于对网络的威胁来控制访问

检测**中间人**等网络威胁，并基于设备风险保护对 WiFi 网络的访问。

**阻止通过 Wi-Fi 访问网络：**

![阻止通过 Wi-Fi 访问网络](./media/skycure-arch-3.png)

**威胁解除后授予访问权限：**

![威胁解除后授予访问权限](./media/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>基于对网络的威胁来控制对 SharePoint Online 的访问

检测**中间人**等网络威胁，根据设备风险阻止公司文件的同步。

**检测到网络威胁时阻止 SharePoint Online：**

![检测到网络威胁时阻止 SharePoint Online](./media/skycure-arch-5.png)

**威胁解除后授予访问权限：**

![Sharepoint 的威胁解除后授予访问权限示例](./media/skycure-arch-6.png)

## <a name="supported-platforms"></a>受支持的平台

-   **Android 4.1 及更高版本**

-   **iOS 8 及更高版本**

## <a name="pre-requisites"></a>先决条件

-   Azure Active Directory Premium

-   Microsoft Intune 订阅

-   Skycure 移动威胁防御订阅

有关详细信息，请参阅 [Skycure 网站](https://www.skycure.com/skycure-microsoft-integration/)。

## <a name="next-steps"></a>后续步骤

以下是将 Intune 与 Skycure 集成需要完成的步骤：

- [使用 Intune 设置 Skycure 集成](skycure-mtd-connector-integration.md)

- [添加并分配 Skycure 应用、Microsoft Authenticator 和 iOS 应用配置策略](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [使用 Intune 创建 Skycure 设备符合性策略](mtd-device-compliance-policy-create.md)

- [在 Intune 中启用 Skycure MTD 连接器](mtd-connector-enable.md)
