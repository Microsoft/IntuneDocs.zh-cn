---
title: Pradeo 移动威胁防御连接器与 Intune
titleSuffix: Intune on Azure
description: 使用 Intune 设置 Pradeo 移动威胁防御连接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.openlocfilehash: f565697d9c76f8a2990074b072ed43547284c29b
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816882"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>Pradeo 移动威胁防御连接器与 Intune

可根据 Pradeo 给出的风险评估，使用条件访问控制移动设备对公司资源的访问，Pradeo 是与 Microsoft Intune 集成的移动威胁防御 (MTD) 解决方案。 基于从运行 Pradeo 应用的设备收集的遥测评估风险。

可以基于通过 Intune 设备符合性策略启动的 Pradeo 风险评估配置条件访问策略，从而根据检测到的威胁允许或阻止不符合设备访问公司资源。

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>Intune 和 Pradeo 如何帮助保护公司资源？

适用于 Android 或 iOS 的 Pradeo 应用可捕获文件系统、网络堆栈、设备和应用程序遥测（如果有），然后将遥测数据发送到 Pradeo 云服务，评估设备的移动威胁风险。

Intune 设备符合性策略包括基于 Pradeo 风险评估的 Pradeo 移动威胁防御规则。 启用此规则后，Intune 将评估设备是否符合已启用的策略。 如果发现设备不符合，将阻止用户访问 Exchange Online 和 SharePoint Online 等公司资源。 用户还可通过安装在设备上的 Pradeo 应用获取指导，以便解决问题并重新访问公司资源。

## <a name="sample-scenarios"></a>示例方案

以下是一些常见方案。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>基于来自恶意应用的威胁来控制访问

在设备上检测到恶意应用（如恶意软件）时，可阻止进行以下操作，直到解决威胁：

-   连接到公司电子邮件

-   使用 OneDrive for Work 应用同步企业文件

-   访问公司应用

**检测到恶意应用时对其进行阻止：**

![检测到恶意应用的概念图](./media/pradeo_maliciousapps_blocked.png)

**修正后授予访问权限：**

![检测到恶意应用，授予访问权限](./media/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>根据网络威胁控制访问权限

检测“中间人”攻击等网络威胁，并基于设备风险保护对 WiFi 网络的访问。

**阻止通过 Wi-Fi 访问网络：**

![阻止通过 Wi-Fi 访问网络](./media/pradeo_network_wifi_blocked.png)

**修正后授予访问权限：**

![在修正时授予访问权限的概念图](./media/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根据网络威胁控制对 SharePoint Online 的访问

基于设备风险检测对网络的威胁，如“中间人”攻击和阻止同步企业文件。

**检测到网络威胁时阻止 SharePoint Online：**

![检测到网络威胁时阻止 SharePoint Online](./media/pradeo_network_spo_blocked.png)

**修正后授予访问权限：**

![Sharepoint 的威胁解除后授予访问权限示例的概念图](./media/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>受支持的平台

-   **Android 4.0.3 和更高版本**

-   **iOS 7 及更高版本**

## <a name="prerequisites"></a>必备条件

-   Azure Active Directory Premium

-   Microsoft Intune 订阅

-   用于移动威胁防御的 Pradeo Security 订阅

    -   有关详细信息，请参阅 [Pradeo 网站](https://www.pradeo.com/en-US/mobile-threat-protection)。

## <a name="next-steps"></a>后续步骤

- [将 Pradeo 与 Intune 集成](pradeo-mtd-connector-integration.md)

- [设置 Pradeo 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [创建 Pradeo 设备符合性策略](mtd-device-compliance-policy-create.md)

- [启用 Pradeo MTD 连接器](mtd-connector-enable.md)