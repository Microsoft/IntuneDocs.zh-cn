---
title: Zimperium MTD 连接器与 Intune
titleSuffix: Intune on Azure
description: 了解如何将 Intune 与 Zimperium Mobile Threat Defense 相集成以控制移动设备对公司资源的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32ace832e44f1cb6d334f69a0c1f03cb41515b2f
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782042"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Zimperium 移动威胁防御连接器与 Intune

可根据 Zimperium 进行的风险评估，使用条件访问控制移动设备对公司资源的访问，Zimperium 是与 Microsoft Intune 集成的移动威胁防御 (MTD) 解决方案。 基于从运行 Zimperium 应用的设备收集的遥测评估风险。

可以基于通过注册设备的 Intune 设备合规性策略启动的 Zimperium 风险评估配置条件访问策略，从而根据检测到的威胁允许或阻止非合规设备访问公司资源。 对于未注册设备，可使用应用保护策略根据检测到的威胁强制执行阻止或选择性擦除操作。

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Intune 和 Zimperium 如何帮助你保护公司资源？

适用于 Android 或 iOS/iPadOS 的 Zimperium 应用可捕获文件系统、网络堆栈，以及设备和应用程序遥测（如果有），然后将遥测数据发送到 Zimperium 云服务，评估设备的移动威胁风险。

Intune 设备符合性策略包括基于 Zimperium 风险评估的 Zimperium 移动威胁防御规则。 启用此规则后，Intune 将评估设备是否符合已启用的策略。 如果发现设备不符合，将阻止用户访问 Exchange Online 和 SharePoint Online 等公司资源。 用户还可通过安装在设备上的 Zimperium 应用获取指导，以便解决问题并重新访问公司资源。

## <a name="sample-scenarios"></a>示例方案

将 Zimperium 与 Intune 集成时，请参阅下面的几个方案：

### <a name="control-access-based-on-threats-from-malicious-apps"></a>基于来自恶意应用的威胁来控制访问

在设备上检测到恶意应用（如恶意软件）时，可阻止设备，直到解除威胁：

- 连接到公司电子邮件

- 使用 OneDrive for Work 应用同步企业文件

- 访问公司应用

**检测到恶意应用时对其进行阻止：**

![检测到恶意应用的概念图](./media/zimperium-mobile-threat-defense-connector/Maliciousapps_blocked_Zimperium.png)

**修正后授予访问权限：**

![在修正后授予访问权限的概念图](./media/zimperium-mobile-threat-defense-connector/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>根据网络威胁控制访问权限

检测**中间人**等网络威胁，并基于设备风险保护对 WiFi 网络的访问。

**阻止通过 Wi-Fi 访问网络：**

![阻止通过 Wi-Fi 访问网络](./media/zimperium-mobile-threat-defense-connector/network_wifi_blocked_Zimperium.png)

**修正后授予访问权限：**

![威胁解除后授予访问权限](./media/zimperium-mobile-threat-defense-connector/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根据网络威胁控制对 SharePoint Online 的访问

检测**中间人**等网络威胁，根据设备风险阻止公司文件的同步。

**检测到网络威胁时阻止 SharePoint Online：**

![检测到网络威胁时阻止 SharePoint Online](./media/zimperium-mobile-threat-defense-connector/network_spo_blocked_Zimperium.png)

**修正后授予访问权限：**

![Sharepoint 的威胁解除后授予访问权限示例](./media/zimperium-mobile-threat-defense-connector/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>受支持的平台

- **Android 4.1 及更高版本**

- **iOS 8 及更高版本**

## <a name="prerequisites"></a>必备条件

- Azure Active Directory Premium

- Microsoft Intune 订阅

- Zimperium 移动威胁防御订阅

  - 有关详细信息，请访问 [Zimperium 网站](https://www.zimperium.com/zips-mobile-ips)。

## <a name="next-steps"></a>后续步骤

- [将 Zimperium 与 Intune 集成](zimperium-mtd-connector-integration.md)

- [设置 Zimperium 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [创建 Zimperium 设备符合性策略](mtd-device-compliance-policy-create.md)

- [启用 Zimperium MTD 连接器](mtd-connector-enable.md)

- [创建 MTD 应用保护策略](../protect/mtd-app-protection-policy.md)
