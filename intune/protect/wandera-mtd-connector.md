---
title: 使用 Intune 设置 Wandera 移动安全性
titleSuffix: Intune on Azure
description: 如何使用 Microsoft Intune 设置 Wandera 移动安全性以控制移动设备对公司资源的访问。
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
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f82a64cdb66528e3e1d3a81fd6119c4a99dff504
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782263"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>使用 Intune 的 Wandera 移动威胁防御连接器  

使用基于 Wandera 执行的风险评估的条件访问控制移动设备对公司资源的访问。 Wandera 是与 Microsoft Intune 集成的移动威胁防御 (MTD) 解决方案。  基于通过 Wandera 服务从设备收集的遥测评估风险，包括：
- 操作系统漏洞
- 安装的恶意应用
- 恶意网络配置文件
- 加密劫持

可基于通过 Intune 设备符合性策略启用的 Wandera 风险评估配置条件访问  策略。 风险评估策略可以根据检测到的威胁，允许或阻止不符合要求的设备访问企业资源。  

> [!NOTE]
> 未注册的设备不支持此移动威胁防御供应商。

## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Intune 和 Wandera 移动威胁防御如何帮助保护公司资源？  

Wandera 移动应用使用 Microsoft Intune 无缝安装。 此应用可捕获文件系统、网络堆栈以及设备和应用程序遥测（如果有）。 此信息同步到 Wandera 云服务，用于评估设备的移动威胁风险。 可以在 Wandera 控制台 RADAR 中配置这些风险级别分类以满足你的需求。

Intune 中的符合性策略包括基于 Wandera 风险评估的 MTD 规则。 启用此规则后，Intune 将评估设备是否符合已启用的策略。

对于不符合要求的设备，可以阻止其访问 Office 365 等资源。 被阻止的设备上的用户可从 Wandera 应用接收指导来解决此问题，并重新获得访问权限。

## <a name="supported-platforms"></a>受支持的平台  

在 Intune 中注册时，Wandera 支持以下平台：

- Android 5.0 及更高版本  
- iOS 10.2 及更高版本  

有关平台和设备的详细信息，请参阅 [Wandera 网站](https://www.wandera.com/mobile-threat-defense/)。

## <a name="prerequisites"></a>必备条件  

- Microsoft Intune 订阅  
- Azure Active Directory  
- Wandera 移动威胁防御（以前称为 Wandera Secure）  

有关详细信息，请参阅 [Wandera 移动安全性](https://www.wandera.com/mobile-security/)。
 
## <a name="sample-scenarios"></a>示例方案

以下是结合使用 Wandera MTD 与 Intune 的常见情形。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>基于来自恶意应用的威胁来控制访问  

在设备上检测到恶意应用（如恶意软件）时，可从常用工具阻止设备，直到解决威胁。 常见阻止情形包括：  
- 连接到公司电子邮件  
- 使用 OneDrive for Work 应用同步企业文件  
- 访问公司应用  

**检测到恶意应用时对其进行阻止**：

![检测到恶意应用的概念图](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**威胁解除后授予访问权限**： 

![在修正后授予访问权限的概念图](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>根据网络威胁控制访问权限  

检测中间人攻击等网络威胁，并基于设备风险保护对 Wi-Fi 网络的访问。  

**阻止通过 Wi-Fi 访问网络**：  

![阻止通过 Wi-Fi 访问网络](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**威胁解除后授予访问权限**：  

![修正后授予访问权限](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根据网络威胁控制对 SharePoint Online 的访问

检测到中间人攻击等网络威胁时，根据设备风险阻止对公司文件进行同步。

**检测到网络威胁时阻止 SharePoint Online**：  

![检测到网络威胁时阻止 SharePoint Online](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**威胁解除后授予访问权限**：  

![SharePoint 的威胁解除后授予访问权限示例](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>后续步骤

- [将 Wandera 与 Intune 集成](wandera-mtd-connector-integration.md)
- [设置 Wandera 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [创建 Wandera 设备符合性策略](mtd-device-compliance-policy-create.md)
- [启用 Wandera MTD 连接器](mtd-connector-enable.md)
