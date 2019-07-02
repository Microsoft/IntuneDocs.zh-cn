---
title: Microsoft Intune 中的 Windows Hello 企业版设置 - Azure | Microsoft Docs
description: 查看用于在 Microsoft Intune 中的 Windows 10 设备上使用和配置 Windows Hello 企业版的标识保护配置文件中的所有 PIN、生物识别和反欺骗设置的列表。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 1cbf45fc337cbe7d7a45081a3b9e05002ca126d8
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402930"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>在 Intune 中启用 Windows Hello 企业版的 Windows 10 设备设置

本文列出并介绍了可以在 Intune 中的 Windows 10 设备上控制的 Windows Hello 企业版设置。 Intune 管理员可以配置这些设置并将其分配给 Windows 10 设备，作为移动设备管理 (MDM) 解决方案的一部分。 

可以在 WIndows Hello 文档的[配置 Windows Hello 企业版策略设置](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings)中找到有关这些设置的其他信息。


若要详细了解 Intune 中的 Windows Hello 企业版配置文件，请参阅[配置标识保护](identity-protection-configure.md)。

## <a name="before-you-begin"></a>在开始之前

[创建配置文件](identity-protection-configure.md#create-the-device-profile)。

## <a name="windows-hello-for-business"></a>Windows Hello 企业版
- **配置 Windows Hello 企业版**：
  - 未配置 - 如果不想使用 Intune 来控制 Windows Hello 企业版设置，请选择此设置。 Windows 10 设备上的任何现有 Windows Hello 企业版设置不会更改。 窗格中的所有其他设置将不可用。

  - 禁用 - 如果不想要使用 Windows Hello 企业版，请选择此设置。 屏幕上的所有其他设置将不可用。
  - 启用 - 如果想要配置 Windows Hello 企业版设置，请选择此设置。  
  
  **默认值**：未配置

  如果设置为*已启用*，有下列设置：

    - **最小 PIN 长度**  
     指定最小 PIN 长度对于设备，以帮助安全登录。 Windows 设备的默认值为六个字符，但此设置可以强制执行最少 4 到 127 个字符。 
  
      **默认值**：未配置

    - **最大 PIN 长度**  
    指定最大 PIN 长度对于设备，以帮助安全登录。 Windows 设备的默认值为六个字符，但此设置可以强制执行最少 4 到 127 个字符。  

      **默认值**：未配置  

    - **PIN 中的小写字母**  
      可以要求最终用户添加小写字母，从而强制实施安全系数更高的 PIN。 选项包括：

      - 不允许 - 禁止用户在 PIN 中使用小写字母。 如果未配置这项设置，也会出现此行为。
      - 允许 - 允许用户在 PIN 中使用小写字母，但不是必须使用。
      - 必需 - 用户必须至少在 PIN 中使用一个小写字母。 例如，常见的做法是要求包含至少一个大写字母和一个特殊字符。

    - **PIN 中的大写字母**  
    可以要求最终用户添加大写字母，从而强制实施安全系数更高的 PIN。 选项包括：

      - 不允许 - 禁止用户在 PIN 中使用大写字母。 如果未配置这项设置，也会出现此行为。
      - 允许 - 允许用户在 PIN 中使用大写字母，但不是必须使用。
      - 必需 - 用户必须至少在 PIN 中使用一个大写字母。 例如，常见的做法是要求包含至少一个大写字母和一个特殊字符。

    - **PIN 中的特殊字符**  
    可以要求最终用户添加特殊字符，从而强制实施安全系数更高的 PIN。 特殊字符包括：`! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`  
 
      选项包括：
      - 不允许 - 禁止用户在 PIN 中使用特殊字符。 如果未配置这项设置，也会出现此行为。
      - 允许 - 允许用户在 PIN 中使用大写字母，但不是必须使用。
      - 必需 - 用户必须至少在 PIN 中使用一个大写字母。 例如，常见的做法是要求包含至少一个大写字母和一个特殊字符。

      **默认**： 不允许

  - **PIN 有效期(天)**  
      比较好的一种做法是指定 PIN 的有效期，在超过此期限后，最终用户必须更改该 PIN。 Windows 设备默认值为 41 天。

    **默认值**：未配置

  - **记住 PIN 历史记录**  
    限制重复使用以前用过的 PIN。 Windows 设备默认情况下阻止重复使用的最后五个 Pin。  

    **默认值**：未配置  

  - **启用 PIN 恢复**   
    允许用户使用 Windows hello 企业版 PIN 恢复服务。 
    
    - **启用**-PIN 恢复密码存储在该设备和用户可以根据需要更改其 PIN。  
    - **已禁用**-恢复密钥不是创建或存储。

    **默认值**：未配置

  - **使用受信任的平台模块(TPM)**   
    TPM 芯片额外提供了一层数据安全。  

    - 启用 - 仅具有可访问 TPM 的设备可预配 Windows Hello 企业版。
    - 未配置 - 首次尝试使用 TPM 的设备。 如果不可用，他们可以使用软件加密。
    
    **默认值**：未配置

  - **允许生物识别身份验证**  
     启用面部识别或指纹等生物识别身份验证作为 Windows Hello 企业版 PIN 的替代方法。 如果生物识别身份验证失败，则用户仍必须配置工作 PIN。 选择：

    - 启用 - Windows Hello 企业版允许进行生物识别身份验证。
    - 未配置 - Windows Hello 企业版将阻止生物识别身份验证（对于所有帐户类型）。

    **默认值**：未配置

  - **使用增强型反欺骗(若有)**  
    配置是否在支持 Windows Hello 反电子欺骗功能的设备上使用该功能（例如，检测面部照片而非真实的面部）。  
    - 启用 - Windows 将在支持反电子欺骗技术时要求所有用户对面部识别功能使用此技术。
    - 未配置 - Windows 遵循设备上的反欺骗配置。

    **默认值**：未配置

  - **用于本地资源的证书**  

    - 启用 - 允许 Windows Hello 企业版使用证书对本地资源进行身份验证。
    - 未配置 - 阻止 Windows Hello 企业版使用证书对本地资源进行身份验证。 相反，设备使用密钥信任本地身份验证的默认行为。 有关详细信息，请参阅 Windows Hello 文档中的[用于本地身份验证的用户证书](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication)。  

  **默认值**：未配置

- **使用安全密钥进行登录**  
  此设置是适用于运行 Windows 10 版本 1903年或更高版本的设备。 使用它来管理对使用 Windows Hello 安全密钥来提供单一登录的支持。  

  - **启用**-用户可以使用 Windows Hello 安全密钥，因为此策略的目标 Pc 的登录凭据。 
  - **禁用**-禁用安全密钥和用户不能使用它们来登录到 Pc。   

  **默认值**：未配置

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
