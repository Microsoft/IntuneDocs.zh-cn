---
# required metadata

title: 设备合规性策略 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的设备合规性策略
## 什么是合规性策略？
为了保护公司数据，需要确保用于访问公司应用和数据的设备符合特定规则（如使用 PIN 访问设备，以及对设备上存储的数据进行加密）。 一组这类规则称为合规性策略。

## 应如何使用合规性策略？
可以将合规性策略与条件性访问策略结合使用，以将访问限制为符合合规性策略规则的设备。 阅读[限制对电子邮件和 O365 服务的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)一文以了解如何将这两种策略结合使用。

还可以使用独立于条件性访问的合规性策略。 独立使用时，会评估目标设备并报告其合规性状态。 例如，你可能要报告未加密的设备数，或哪些设备已越狱或取得 root 权限。 但是，独立使用，不会实施对公司资源的访问限制。

将合规性策略部署到用户。 将合规性策略部署到用户后，会对用户设备检查合规性。

下表列出了合规性策略支持的设备类型，也列出了当该策略与条件访问策略一起使用时托管不符合合规性的设置的方式。

--------------

|策略设置| Windows 8.1 及更高版本| Windows Phone 8.1 及更高版本| iOS 6.0 及更高版本|Android 4.0 及更高版本<br/>Samsung KNOX 标准版 4.0 和更高版本|
|-----|----|----|----|
|**PIN 或密码配置** |已修正|已修正|已修正|已隔离|
|**设备加密**|不适用|已修正|已修正（通过设置 PIN）|已隔离|
|**已越狱或取得 root 权限的设备**|不适用|不适用|已隔离（非设置）|已隔离（非设置）|
|**电子邮件配置文件**|不适用|不适用|已隔离|不适用|
|**最低操作系统版本**|已隔离|已隔离|已隔离|已隔离|
|**最高操作系统版本**|已隔离| 已隔离| 已隔离| 已隔离|
|**Windows 运行状况证明**|Windows 10 和 Windows 10 移动版已被隔离。<br /><br />设置不适用于 Windows 8.1|不适用|不适用|不适用|
--------------
**已修正** = 合规性操作由设备操作系统强制执行（例如，强制用户设置 PIN）。  设置永远不会不合规。

**已隔离** = 设备操作系统并不强制执行合规性操作（例如，Android 设备不强制用户加密设备）。 当设备不合规时，进行以下操作：

-   如果条件访问策略将用户作为目标，则会阻止设备。

-   公司门户会通知用户任何合规性问题。

## 后续步骤
[创建设备合规性策略](create-a-device-compliance-policy-in-microsoft-intune.md)

[部署和监视设备合规性策略](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### 另请参阅
[限制对电子邮件和 O365 服务的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


