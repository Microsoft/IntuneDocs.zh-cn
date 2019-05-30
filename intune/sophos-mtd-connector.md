---
title: 使用 Intune 设置 Sophos Mobile 集成
titleSuffix: Intune on Azure
description: 如何使用 Microsoft Intune 设置 Sophos Mobile 解决方案以控制移动设备对公司资源的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4363bb4feba52c15b8918a7c6ea02fa2917a00de
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044942"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>通过 Intune 启用 Sophos Mobile Threat Defense 连接器
可以根据 Sophos Mobile（与 Microsoft Intune 集成的 Mobile Threat Defense (MTD) 解决方案）进行的风险评估，使用条件访问控制移动设备对公司资源的访问。 风险是基于从运行 Sophos Mobile 应用的设备收集到的遥测进行评估的。
可以基于通过 Intune 设备符合性策略启用的 Sophos Mobile 风险评估配置条件访问策略，从而根据检测到的威胁允许或阻止不符合的设备访问公司资源。

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Intune 和 Sophos Mobile 如何帮助你保护公司资源？
适用于 Android 和 iOS 的 Sophos Mobile 应用可以捕获文件系统、网络堆栈、设备和应用程序遥测（如果有），然后将遥测数据发送到 Sophos Mobile 云服务以评估设备的移动威胁风险。
Intune 设备符合性策略包括基于 Sophos Mobile 风险评估的 Sophos Mobile Threat Defense 规则。 启用此规则后，Intune 将评估设备是否符合已启用的策略。 如果发现设备不符合，将阻止用户访问 Exchange Online 和 SharePoint Online 等公司资源。 用户还可以通过安装在其设备上的 Sophos Mobile 应用获取指导以解决问题并重新访问公司资源。  

## <a name="sample-scenarios"></a>示例方案
以下是一些常见方案。  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>基于来自恶意应用的威胁来控制访问
在设备上检测到恶意应用（如恶意软件）时，可阻止进行以下操作，直到解决威胁：
- 连接到公司电子邮件
- 使用 OneDrive for Work 应用同步企业文件
- 访问公司应用

**检测到恶意应用时对其进行阻止**：
 
![检测到恶意应用的概念图](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**威胁解除后授予访问权限**：  
![在威胁解除后授予访问权限的概念图](./media/sophos-mtd-connector/sophos_malicious_apps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>根据网络威胁控制访问权限  
检测中间人攻击等网络威胁，并基于设备风险保护对 Wi-Fi 网络的访问。  

**阻止通过 Wi-Fi 访问网络**：  
![阻止通过 Wi-Fi 访问网络](./media/sophos-mtd-connector/sophos_network_wifi_blocked.png)

**威胁解除后授予访问权限**：   
![威胁解除后授予访问权限](./media/sophos-mtd-connector/sophos_network_wifi_unblocked.png)  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根据网络威胁控制对 SharePoint Online 的访问  
检测中间人攻击等网络威胁，并基于设备风险阻止对公司文件进行同步。  

**检测到网络威胁时阻止 SharePoint Online**：   
![检测到网络威胁时阻止 SharePoint Online](./media/sophos-mtd-connector/sophos_network_spo_blocked.png)  

**威胁解除后授予访问权限**：  
![SharePoint 的威胁解除后授予访问权限示例](./media/sophos-mtd-connector/sophos_network_spo_unblocked.png)  

## <a name="supported-platforms"></a>受支持的平台  
- Android 5.0 及更高版本
- iOS 11.0 及更高版本

## <a name="prerequisites"></a>必备条件  
- Azure Active Directory Premium
- Microsoft Intune 订阅 
- Sophos Mobile Threat Defense 订阅

有关详细信息，请参阅 [Sophos 网站](https://www.sophos.com/products/mobile-control)。  

## <a name="next-steps"></a>后续步骤  
- [将 Sophos 与 Intune 相集成](sophos-mtd-connector-integration.md)
- [设置 Sophos 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [创建 Sophos 设备符合性策略](mtd-device-compliance-policy-create.md)
- [启用 Sophos MTD 连接器](mtd-connector-enable.md)
