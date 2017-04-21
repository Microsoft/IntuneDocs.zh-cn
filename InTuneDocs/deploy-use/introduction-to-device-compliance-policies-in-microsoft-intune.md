---
title: "设备合规性策略 | Microsoft Docs"
description: "本主题介绍了设备合规性策略的涵义及其工作原理。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 2de9a7d639ee667ee195ded2875a8ac8e478fffb
ms.lasthandoff: 04/14/2017


---

# <a name="device-compliance-policies-in-microsoft-intune"></a>Microsoft Intune 中的设备合规性策略

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="what-is-a-compliance-policy"></a>什么是合规性策略？
若要帮助保护公司数据，则需确保用于访问公司应用和数据的设备符合特定规则。 这些规则可能包括使用 PIN 访问设备和加密存储在设备上的数据。 一组这样的规则就称为合规性策略。

## <a name="how-should-i-use-compliance-policies"></a>应如何使用合规性策略？
可以将合规性策略与条件性访问策略结合使用，以便只允许符合合规性策略规则的设备访问电子邮件和其他服务。 若要了解如何将这两种策略结合使用，请阅读[限制对电子邮件和 O365 服务的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。

还可以使用独立于条件性访问的合规性策略。 独立使用合规性策略时，会评估目标设备并报告其相容性状态。 例如，你可能要报告未加密的设备数，或哪些设备已越狱或取得 root 权限。 但是独立使用合规性策略时，不会实施对公司资源的访问限制。

将合规性策略部署到用户。 将合规性策略部署到用户后，会对用户设备检查合规性。
若要了解策略部署完成后，移动设备需要多长时间获取策略，请参阅[管理设备上的设置和功能](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies)。

下表列出了合规性策略支持的设备类型。 该表还说明了结合使用合规性策略和条件访问策略时如何管理非合规性设置。

-----------------------------

|策略设置| Windows 8.1 及更高版本| Windows Phone 8.1 及更高版本| iOS 8.0 及更高版本|Android 4.0 及更高版本<br/>Samsung Knox 标准版 4.0 及更高版本|
|-----|----|----|----|----|
|**PIN 或密码配置** |已修正|已修正|已修正|已隔离|
|**设备加密**|不适用|已修正|已修正（通过设置 PIN）|已隔离|
|**已越狱或取得 root 权限的设备**|不适用|不适用|已隔离（非设置）|已隔离（非设置）|
|**电子邮件配置文件**|不适用|不适用|已隔离|不适用|
|**最低操作系统版本**|已隔离|已隔离|已隔离|已隔离|
|**最高操作系统版本**|已隔离|已隔离|已隔离|已隔离|
|**Windows 运行状况证明**|已隔离：Windows 10 和 Windows 10 移动版<br /><br />不适用：Windows 8.1|不适用|不适用|不适用|

------------------------------

**已修正** = 设备操作系统强制合规性。 （例如，强制用户设置 PIN。）

**已隔离** = 设备操作系统不会强制合规性。 （例如，Android 设备不强制用户加密设备。）当设备不合规时，进行以下操作：

-   如果条件访问策略应用到用户，则将阻止该设备。

-   公司门户会通知用户任何合规性问题。

## <a name="next-steps"></a>后续步骤
[创建设备合规性策略](create-a-device-compliance-policy-in-microsoft-intune.md)

[部署和监视设备合规性策略](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>另请参阅
[限制对电子邮件和 O365 服务的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)

