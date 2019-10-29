---
title: Microsoft Intune 中的 Windows 8.1 符合性设置 - Azure | Microsoft Docs
description: 查看在 Microsoft Intune 中为 Windows 8.1 和 Windows Phone 8.1 设备设置符合性时可以使用的所有设置的列表。 检查最小和最大操作系统的符合性，设置密码限制和长度，启用数据存储加密等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e074d922078a9772ca67a6ebd99948bc3e64601
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813213"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune 将设备标记为符合或不符合的 Windows 8.1 设置

本文列出并描述了在 Intune 中可对 Windows 8.1 设备配置的不同符合性设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置来阻止简单密码，设置最低和最高操作系统版本等。

此功能适用于：

- Windows Phone 8.1
- Windows 8.1 及更高版本

作为 Intune 管理员，请使用这些符合性设置来帮助保护组织资源。 若要详细了解符合性策略及其作用，请参阅[设备符合性入门](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>在开始之前

[创建合规性策略](create-compliance-policy.md#create-the-policy)。 对于“平台”，请选择“Windows Phone 8.1”或“Windows 8.1 及更高版本”    。

## <a name="device-properties"></a>设备属性

### <a name="operating-system-version"></a>操作系统版本

**Windows Phone 8.1 及更高版本**
- **移动设备的最低操作系统版本**：  
  输入允许的最低版本。 设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 设备用户可以选择升级其设备，然后访问公司资源。

- **移动设备的最高操作系统版本**：  
  输入允许的最大版本。 当设备使用的操作系统版本高于在规则中输入的版本时，将阻止对组织资源的访问。 系统会要求设备用户联系其 IT 管理员。 除非将规则更改为允许操作系统版本，否则设备无法访问组织资源。

**Windows 8.1 及更高版本**
- **最低操作系统版本**：  
  输入允许的最低版本。 设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 设备用户可以选择升级其设备，然后访问公司资源。

- **最高操作系统版本**：  
  输入允许的最大版本。 当设备使用的操作系统版本高于在规则中输入的版本时，将阻止对组织资源的访问。 系统会要求设备用户联系其 IT 管理员。 除非将规则更改为允许操作系统版本，否则设备无法访问组织资源。

Windows 8.1 PC 返回版本 **3**。 对于 Windows，如果操作系统版本规则设置为 Windows 8.1，则该设备将报告为不符合要求，即使该设备具有 Windows 8.1 也是如此。

## <a name="system-security"></a>系统安全

### <a name="password"></a>密码

- **需要密码才可解锁移动设备**：  
  - **未配置**（默认）- 不会评估此设置的符合性和不符合性  。
  - **必需** - 用户必须输入密码后才能访问其设备。

- **简单密码**：  
  - **未配置**（*默认*）-用户可以创建简单的密码，例如**1234**或**1111**。
  - **阻止** - 用户无法创建简单密码，如 1234 或 1111。    

- **最短密码长度**：  
  输入密码必须包含的最小位数或最小字符数。

  对于运行 Windows 并使用 Microsoft 帐户进行访问的设备，如果满足以下任一条件，则符合性策略将无法正确评估：  
  - 最短密码长度大于 8 个字符
  - 字符集数下限超过两个

- **密码类型**：  
  选择密码是应仅包含数值字符，还是应混合使用数字和其他字符（字母数字）   。

  如果设置为 "*字母数字*"，则可以使用以下设置。  

  - **密码中的非字母数字字符数**：  
    当 "*密码类型*" 设置为 "**字母数字**" 时，指定密码必须包含的最小字符集数。 选项包括**0**到**4 个**集，默认值为**1**。
    
    四个字符集为：
    - 小写字母
    - 大写字母
    - 符号
    - 数字

    设置的数字越大，要求用户创建的密码越复杂。 对于使用 Microsoft 帐户访问的设备，如果满足以下任一条件，则符合性策略将无法正确评估：

    - 最短密码长度大于 8 个字符
    - 字符集数下限超过两个

- **需要提供密码之前处于非活动状态的最大分钟数**：  
  输入用户必须重新输入密码前的空闲时间。

- **密码过期(天)** ：  
  选择密码过期之前的天数，然后用户必须创建一个新密码。

- **阻止重用的曾用密码数**：  
  输入之前使用但无法使用的密码的数量。

### <a name="encryption"></a>加密

- **加密设备上的数据存储**：  
  - **未配置**（默认） 
  - **必需** - 使用“必需”加密设备上的数据存储。 


<!-- not on phone   
- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.
--> 

## <a name="next-steps"></a>后续步骤

- [为不符合要求的设备添加操作](actions-for-noncompliance.md)并[使用范围标记来筛选策略](../fundamentals/scope-tags.md)。
- [监视符合性策略](compliance-policy-monitor.md)。
- 请参阅[适用于 Windows 10 及更高版本设备的符合性策略设置](compliance-policy-create-windows.md)。