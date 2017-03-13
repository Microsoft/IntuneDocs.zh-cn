---
title: "Lookout 移动威胁防御连接器 | Microsoft Docs"
description: "根据设备、网络和应用程序风险，通过 Lookout 移动威胁防御连接器和 Intune 保护对公司资源的访问。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6f78150b6c3821f6e9822ccfa905ac367bd359ad
ms.openlocfilehash: 9e00e60472c8ba9f10a6071c42a53f58dcc00a08
ms.lasthandoff: 03/02/2017


---

# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Lookout 移动威胁防御连接器与 Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

可根据 Lookout 给出的风险评估，控制移动设备对公司资源的访问，Lookout 是与 Microsoft Intune 集成的设备威胁防护解决方案。 基于通过 Lookout 服务从设备收集的遥测评估风险，包括：
- 操作系统漏洞
- 安装的恶意应用
- 恶意网络配置文件

可基于通过 Intune 合规性策略启用的 Lookout 风险评估配置条件性访问策略。 基于检测到的威胁，通过设置允许或阻止不符合要求的设备。

## <a name="how-do-intune-and-lookout-device-threat-protection-help-protect-company-resources"></a>Intune 和 Lookout 设备威胁保护如何帮助保护公司资源？
在移动设备上安装并运行 Lookout 移动应用 **Lookout for work**。 此应用可捕获文件系统、网络堆栈以及设备和应用程序遥测（如果有），然后将其发送到 Lookout 云服务，评估设备的移动威胁风险。 可在 Lookout 控制台中更改威胁的风险等级分类以满足你的需求。  

Intune 中的合规性策略包括用于 Lookout 移动威胁防护的新规则，该规则以 Lookout 风险评估为基础。 启用此规则后，Intune 将评估设备是否符合已启用的策略。

如果发现设备不合规，将阻止对 Exchange Online 和 SharePoint Online 等资源的访问。 被阻止的设备上的用户会收到相关步骤来解决此问题，重新获得访问权限。 从 Lookout for Work 应用启动指南。

## <a name="supported-platforms"></a>受支持的平台：
在 Intune 中注册时，Lookout 支持以下平台：
* **Android 4.1 及更高版本**
* **iOS 8 及更高版本** 有关平台和语言支持的其他相关信息，请访问 [Lookout 网站](https://personal.support.lookout.com/hc/en-us/articles/114094140253)。

## <a name="prerequisites"></a>先决条件：
* Microsoft Intune 订阅
* Azure Active Directory
* Lookout Mobile EndPoint Security 企业订阅  

有关详细信息，请参阅 [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>示例方案
以下是一些常见方案：

### <a name="control-access-based-on-threats-from-malicious-apps"></a>基于来自恶意应用的威胁来控制访问
在设备上检测到恶意应用（如恶意软件）时，可阻止进行以下操作，直到解决威胁：
* 连接到公司电子邮件
* 使用 OneDrive for Work 应用同步企业文件
* 访问公司应用

**检测到恶意应用时阻止：**
![显示条件访问策略在设备上检测到恶意软件，而将其确定为不合规时阻止访问的图示](../media/mtp/malicious-apps-blocked.png)

**威胁解除后授予访问权限：**

![显示条件访问策略在解除威胁后将设备确定为合规时授予访问权限的图示](../media/mtp/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>基于对网络的威胁来控制访问
检测中间人攻击等网络威胁，并基于设备风险保护对 WiFi 网络的访问。

**阻止通过 WiFi 的网络访问：**
![基于网络威胁阻止 WiFi 访问的条件访问图示](../media/mtp/network-wifi-blocked.png)

**威胁解除后授予访问权限：**

![条件访问在解除威胁后允许访问的图示](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>基于对网络的威胁来控制对 SharePoint Online 的访问

基于设备风险检测对网络的威胁，如中间人攻击和阻止同步企业文件。

**检测到网络威胁时阻止 SharePoint Online：**

![条件访问基于检测到的威胁阻止设备访问 SharePoint Online 的图示](../media/mtp/network-spo-blocked.png)


**威胁解除后授予访问权限：**

![条件访问在解除网络威胁后允许访问的图示](../media/mtp/network-spo-unblocked.png)

## <a name="next-steps"></a>后续步骤
要实施此解决方案，必须执行以下几个主要步骤：
1.    [为订阅设置设备威胁防护功能](device-threat-protection-subscription-setup.md)
2.    [在 Intune 中实现设备威胁防护连接](device-threat-protection-enable.md)
3.  [配置和部署设备威胁防护应用](device-threat-protection-apps.md)
4.    [配置设备威胁防护合规性策略](device-threat-protection-policy.md)
5.    [排除设备威胁防护集成方面的故障](http://docs.microsoft.com/intune/troubleshoot/device-threat-protection-troubleshooting)

