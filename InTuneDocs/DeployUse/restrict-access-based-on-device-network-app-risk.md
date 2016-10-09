---
title: "使用设备威胁保护限制访问 | Microsoft Intune"
description: "根据设备、网络和应用程序风险，限制对公司资源的访问。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 550fbbf94f46eee23e77ebf7f9177148882f28e2
ms.openlocfilehash: 758e4408fa7119ed4ebb82e98b850be5b1f318b4


---

# 以设备、网络和应用程序威胁为基础，限制对公司资源的访问
可根据 Lookout 给出的风险评估，控制从移动设备访问公司资源的权限，Lookout 是与 Microsoft Intune 集成的设备威胁保护解决方案。 风险基于 Lookout 服务从设备上收集的对操作系统 (OS) 漏洞、已安装恶意软件和网络配置文件的遥测。 以风险评估为基础，可在 Intune 中配置条件访问，在设备上检测到威胁而将其判定为不合规时，允许或阻止该设备进行访问。  当前仅支持运行 **4.1 及更高版本**且在 Microsoft Intune 中注册的 **Android** 设备。  有关 Lookout 支持的平台和语言的信息，请参阅此[文章](https://personal.support.lookout.com/hc/en-us/articles/114094140253)。
## 还可以解决那些问题？
公司和组织需要针对出现的威胁保护敏感数据，包括物理的、基于应用的和基于网络的威胁以及 OS 漏洞。

长久以来，公司和组织一直在积极保护电脑免受恶意软件的攻击。 移动设备通常是未受保护的新领域。 尽管移动平台使用应用隔离和审查用户应用商店等技术内置了 OS 保护，但这些平台仍易受到复杂攻击。 越来越多的员工都在使用移动设备办公，他们可能需要访问敏感信息和有价值的信息，因此需要保护其设备免受各种复杂攻击。

使用 Intune，可根据 Lookout 等设备威胁保护解决方案提供的风险评估，控制对公司资源和数据的访问。

## Intune 和 Lookout 设备威胁保护如何帮助保护公司资源？
在移动设备上运行的 Lookout 移动应用 (Lookout for Work) 可收集（可用的）文件系统、网络堆栈以及设备和应用程序遥测，并将其发送至 Lookout 设备威胁保护云服务，从而计算出移动威胁的累积设备风险。 还可在 Lookout 控制台中更改威胁的风险等级分类以满足你的需求。  
Intune 中的合规性策略现包括 Lookout 移动威胁保护的新规则，该规则以 Lookout 设备威胁风险评估为基础。 启用此规则后，Microsoft Intune 将评估设备是否符合已启用的策略。

如果如果设备不符合合规性策略，则条件访问策略将阻止该设备访问 Exchange Online 和 SharePoint Online 等资源。 阻止访问后，将向最终用户演示如何解决问题并获取公司资源的访问权限。 此演示通过 Lookout for Work 应用启动。

## 方案示例
以下是一些常见方案：
### 来自恶意应用的威胁：
在设备上检测到恶意软件等恶意应用时，可从以下位置阻止此类设备：
* 解除威胁前，连接到企业电子邮件。
* 使用 OneDrive for Work 应用同步企业文件。
* 访问业务关键应用。

**检测到恶意应用时阻止访问：**
![ 显示条件访问策略在设备上检测到恶意软件而将其确定为不合规时阻止访问的图示](../media/mtp/malicious-apps-blocked.png)

**已取消阻止设备，可解除威胁后访问公司资源：**

![显示条件访问策略在解除威胁后将设备确定为合规时授予访问权限的图示](../media/mtp/malicious-apps-unblocked.png)
### 对网络的威胁：
检测中间人攻击等网络威胁，并基于设备风险限制 WiFi 网络访问权限。

**阻止通过 WiFi 访问网络：**
![基于网络威胁阻止 WiFi 访问的条件访问图示](../media/mtp/network-wifi-blocked.png)

**威胁解除后授予访问权限：**

![条件访问在解除威胁后允许访问的图示](../media/mtp/network-wifi-unblocked.png)
### 对网络的威胁（阻止访问 SharePoint Online）：

基于设备风险检测对网络的威胁，如中间人攻击和阻止同步企业文件。

**基于设备上检测到的网络威胁，阻止了对 SharePoint Online 的访问：**

![条件访问基于检测到的威胁阻止设备访问 SharePoint Online 的图示](../media/mtp/network-spo-blocked.png)


**威胁解除后授予访问权限：**

![条件访问在解除网络威胁后允许访问的图示](../media/mtp/network-spo-unblocked.png)

## 后续步骤
要实施此解决方案，必须执行以下几个主要步骤：
1.  [为订阅设置 Lookout 移动威胁保护](set-up-your-subscription-with-lookout-mtp.md)
2.  [在 Intune 中启用 Lookout MTP 连接](enable-lookout-mtp-connection-in-intune.md)
3.  [配置并部署 Lookout for Work 应用程序](configure-and-deploy-lookout-for-work-apps.md)
4.  [配置合规性策略](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Lookout 集成故障排除](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)



<!--HONumber=Sep16_HO4-->


