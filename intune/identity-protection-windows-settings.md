---
title: Microsoft Intune 中的 Windows Hello 企业版设置 - Azure | Microsoft Docs
description: 查看用于在 Microsoft Intune 中的 Windows 10 设备上使用和配置 Windows Hello 企业版的标识保护配置文件中的所有 PIN、生物识别和反欺骗设置的列表。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9bbdb56770c154a482ad004f1f3f980809424caf
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848502"
---
# <a name="windows-10-and-newer-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Intune 中用于启用 Windows Hello 企业版的 Windows 10（及更高版本）设备设置

本文列出并介绍了可以在 Intune 中的 Windows 10 设备上控制的 Windows Hello 企业版设置。 作为移动设备管理 (MDM) 解决方案的一部分，请通过这些设置来使用 PIN 或指纹等方法登录。

作为 Intune 管理员，可以创建这些设置，并将它们分配到 Windows 10 及更高版本设备。

若要详细了解 Intune 中的 Windows Hello 企业版配置文件，请参阅[配置标识保护](identity-protection-configure.md)。

## <a name="before-you-begin"></a>在开始之前

[创建配置文件](identity-protection-configure.md#create-the-device-profile)。

## <a name="windows-hello-for-business"></a>Windows Hello 企业版

- **配置 Windows Hello 企业版**：若要使用此功能并配置它的设置，请选择“启用”。
- **最小 PIN 长度**：输入要在设备上允许的最小 PIN 长度。 默认 PIN 长度为六 (6) 个字符。 最小 PIN 长度为四 (4) 个字符。
- **最大 PIN 长度**：输入要在设备上允许的最大 PIN 长度。 默认 PIN 长度为六 (6) 个字符。 最大 PIN 长度为 127 个字符。  
- **PIN 中的小写字母**：可以要求最终用户添加小写字母，从而强制实施安全系数更高的 PIN。 选项包括：

  - **不允许**（默认）：禁止用户在 PIN 中使用小写字母。 如果未配置这项设置，也会出现此行为。
  - **允许**：允许用户在 PIN 中使用小写字母，但不是必须使用。
  - **必需**：用户至少必须在 PIN 中添加一个小写字母。 例如，常见的做法是要求包含至少一个大写字母和一个特殊字符。

- **PIN 中的大写字母**：可以要求最终用户添加大写字母，从而强制实施安全系数更高的 PIN。 选项包括：

  - **不允许**（默认）：禁止用户在 PIN 中使用大写字母。 如果未配置这项设置，也会出现此行为。
  - **允许**：允许用户在 PIN 中使用特殊字符，但不是必须使用。
  - **必需**：用户至少必须在 PIN 中添加一个特殊字符。 例如，常见的做法是要求包含至少一个大写字母和一个特殊字符。

- **PIN 中的特殊字符**：可以要求最终用户添加特殊字符，从而强制实施安全系数更高的 PIN。 选项包括：

  - **不允许**（默认）：禁止用户在 PIN 中使用特殊字符。 如果未配置这项设置，也会出现此行为。
    特殊字符包括：`! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **允许**：允许用户在 PIN 中使用特殊字符，但不是必须使用。
  - **必需**：用户至少必须在 PIN 中添加一个特殊字符。 例如，常见的做法是要求包含至少一个大写字母和一个特殊字符。

- **PIN 有效期(天)**：比较好的一种做法是指定 PIN 的有效期，在超过此期限后，最终用户必须更改该 PIN。 默认值为 41 天。

- **记住 PIN 历史记录**：限制重复使用以前用过的 PIN。 默认情况下，最后 5 个 PIN 无法重用。  
- **启用 PIN 恢复**：允许用户使用 Windows Hello 企业版 PIN 恢复服务来更改 PIN。

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **使用受信任的平台模块(TPM)**：TPM 芯片额外提供了一层数据安全。 选择下列值之一：  
  - **启用**：仅限可访问 TPM 的设备预配 Windows Hello 企业版。
  - **未配置**：所有设备都可预配 Windows Hello 企业版，即使没有可用 TPM 也是如此。 设备将首先尝试使用 TPM，但如果 TPM 不可用，设备可使用软件加密。  

- **允许生物识别身份验证**：启用面部识别或指纹等生物识别身份验证作为 Windows Hello 企业版 PIN 的替代方法。 如果生物识别身份验证失败，则用户仍必须配置工作 PIN。 选择：

  - **启用**：Windows Hello 企业版允许进行生物识别身份验证。
  - **未配置**（默认）：Windows Hello 企业版阻止生物识别身份验证（适用于所有帐户类型）。

- **使用增强型反欺骗(若有)**：选择是否在支持 Windows Hello 的反欺骗功能的设备上使用这些功能。 例如，检测人脸照片，而不是真实人脸。

  - **启用**：Windows 将在支持反电子欺骗技术时要求所有用户对面部识别功能使用此技术。  
  - **未配置**（默认）：Windows 尊重设备上的反电子欺骗配置。

- **用于本地资源的证书**： 

  - **启用**：允许 Windows Hello 企业版使用证书对本地资源进行身份验证。
  - **未配置**（默认）：阻止 Windows Hello 企业版使用证书对本地资源进行身份验证。  

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
