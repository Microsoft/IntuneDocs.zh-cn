---
title: 通过 Intune 启用 Better Mobile Threat Defense 连接器
titleSuffix: Intune on Azure
description: 使用 Intune 设置 Better Mobile Threat Defense 连接器。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 7/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.openlocfilehash: 25a6c892284b6014fc3090b3e673c6385ccbad13
ms.sourcegitcommit: 973a06f4a35b74314fece2bae17dd6885b4211c3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42823270"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>通过 Intune 启用 Better Mobile Threat Defense 连接器

可根据 Better Mobile 进行的风险评估，使用条件访问控制移动设备对公司资源的访问，Better Mobile 是与 Microsoft Intune 集成的 Mobile Threat Defense (MTD) 解决方案。 基于从运行 Better Mobile 应用的设备收集的遥测评估风险。

可以基于通过 Intune 设备符合性策略启动的 Better Mobile 风险评估配置条件访问策略，从而根据检测到的威胁允许或阻止不符合设备访问公司资源。

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Intune 和 Better Mobile 如何帮助你保护公司资源？

在移动设备上安装并运行 Better Mobile 应用。 此应用可捕获文件系统、网络堆栈、设备和应用程序遥测（如果有），然后将数据发送到 Better Mobile 云服务，以评估设备的移动威胁风险。

Intune 设备符合性策略包括基于 Better Mobile 风险评估的 Mobile Threat Defense 规则。 启用此规则后，Intune 将评估设备是否符合已启用的策略。 如果发现设备不符合，将阻止用户访问 Exchange Online 和 SharePoint Online 等公司资源。 用户还可通过安装在设备上的 Better Mobile 应用获取指导，以便解决问题并重新访问公司资源。

## <a name="sample-scenarios"></a>示例方案

以下是一些常见方案。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>基于来自恶意应用的威胁来控制访问

在设备上检测到恶意应用（如恶意软件）时，可阻止进行以下操作，直到解决威胁：

-   连接到公司电子邮件

-   使用 OneDrive for Work 应用同步企业文件

-   访问公司应用

**检测到恶意应用时对其进行阻止：**

![检测到恶意应用](./media/better_mobile_maliciousapps_blocked.png)

**修正后授予访问权限：**

![检测到恶意应用，授予访问权限](./media/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>基于对网络的威胁来控制访问

检测“中间人”攻击等网络威胁，并基于设备风险保护对 WiFi 网络的访问。

**阻止通过 Wi-Fi 访问网络：**

![阻止通过 Wi-Fi 访问网络](./media/better_mobile_network_wifi_blocked.png)

**修正后授予访问权限：**

![威胁解除后授予访问权限](./media/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>基于对网络的威胁来控制对 SharePoint Online 的访问

基于设备风险检测对网络的威胁，如“中间人”攻击和阻止同步企业文件。

**检测到网络威胁时阻止 SharePoint Online：**

![检测到网络威胁时阻止 SharePoint Online](./media/better_mobile_network_spo_blocked.png)

**修正后授予访问权限：**

![Sharepoint 的威胁解除后授予访问权限示例](./media/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>受支持的平台

-   **Android 4.1 及更高版本**

-   **iOS 8.0 及更高版本**

## <a name="prerequisites"></a>必备条件

-   Azure Active Directory Premium

-   Microsoft Intune 订阅

-   Better Mobile Threat Defense 订阅

    -   有关详细信息，请参阅[网站](https://www.better.mobi/)。

## <a name="next-steps"></a>后续步骤

- [将 Better Mobile 与 Intune 集成](better-mobile-mtd-connector-integration.md)

- [设置 Better Mobile 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [创建 Better Mobile 设备符合性策略](mtd-device-compliance-policy-create.md)

- [启用 Better Mobile MTD 连接器](mtd-connector-enable.md)