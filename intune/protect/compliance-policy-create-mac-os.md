---
title: Microsoft Intune 中的 macOS 设备符合性设置 - Azure | Microsoft Docs
description: 查看在 Microsoft Intune 中为 macOS 设备设置符合性时可以使用的所有设置的列表。 要求使用 Apple 的系统完整性保护，设置密码限制，要求使用防火墙，允许网关守卫等。
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
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813497"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune 将设备标记为符合或不符合的 macOS 设置

本文列出并描述了在 Intune 中可针对 macOS 设备配置的不同符合性设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置来设置最低和最高操作系统版本，设置要过期的密码等。

此功能适用于：

- macOS

作为 Intune 管理员，请使用这些符合性设置来帮助保护组织资源。 若要详细了解符合性策略及其作用，请参阅[设备符合性入门](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>在开始之前

[创建合规性策略](create-compliance-policy.md#create-the-policy)。 对于“平台”  ，选择“macOS”  。

## <a name="device-health"></a>设备运行状况

- **需要系统完整性保护**：  
  - **未配置**（默认）- 不会评估此设置的符合性和不符合性  。
  - **要求**-要求 macOS 设备启用[系统完整性保护](https://support.apple.com/HT204899)（打开 Apple 的网站）。  

## <a name="device-properties"></a>设备属性

- **所需的最低操作系统**：  
  设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 设备用户可以选择升级其设备。 此后，他们可访问组织资源。

- **允许的最高操作系统版本**：  
  当设备使用的操作系统版本高于输入的版本时，将阻止对组织资源的访问。 系统会要求设备用户联系其 IT 管理员。 除非将规则更改为允许操作系统版本，否则设备无法访问组织资源。

- **最低操作系统内部版本**：  
  当 Apple 发布安全更新时，通常会更新内部版本号，而非操作系统版本。 使用此功能可在设备上输入允许的最低内部版本号。

- **最高操作系统内部版本**：  
  当 Apple 发布安全更新时，通常会更新内部版本号，而非操作系统版本。 使用此功能可在设备上输入允许的最高内部版本号。

## <a name="system-security-settings"></a>系统安全设置

### <a name="password"></a>密码

- **需要密码才可解锁移动设备**：  
  - **未配置**（默认） 
  - **必需** - 用户必须输入密码后才能访问其设备。

- **简单密码**：  
  - **未配置**（*默认*）-用户可以创建简单的密码，例如**1234**或**1111**。
  - **阻止** - 用户无法创建简单密码，如 1234 或 1111。  

- **最短密码长度**：  
  输入密码必须包含的最小位数或最小字符数。

-  密码类型：  选择密码是应仅包含数值字符，还是应混合使用数字和其他字符（字母数字）  。

- **密码中的非字母数字字符数**：  
  输入密码中必须包含的最小特殊字符（如 `&`、`#`、`%`、`!` 等）数。

  设置的数字越大，要求用户创建的密码越复杂。

- **需要提供密码之前处于非活动状态的最大分钟数**：  
  输入用户必须重新输入密码前的空闲时间。

- **密码过期(天)** ：  
  选择密码过期之前的天数，然后必须创建一个新密码。

- **阻止重用的曾用密码数**：  
  输入之前使用但无法使用的密码的数量。
> [!IMPORTANT]
> 当 macOS 设备上的密码要求发生更改时，直到用户下次更改密码时此更改才会生效。 例如，如果将密码长度限制设置为 8 位数，而 macOS 设备当前使用的是 6 位数密码，则在用户下次更新设备上的密码前，该设备将仍保持符合状态。

### <a name="encryption"></a>加密

- **加密设备上的数据存储**：  
  - **未配置**（默认） 
  - **必需** - 使用“必需”加密设备上的数据存储。 

### <a name="device-security"></a>设备安全

防火墙保护设备免受未经授权的网络访问。 可以使用防火墙控制基于每个应用程序的连接。 

- **防火墙**：  
  - **未配置**（默认）- 此设置使防火墙保持关闭状态，允许网络流量（未阻止）。 
  - **启用** - 使用“启用”可帮助保护设备免受未经授权的访问  。 启用此功能，可以处理传入的 Internet 连接，并使用隐藏模式。 

- **传入连接**：  
  - **未配置**（默认）- 允许传入连接和共享服务。 
  - **阻止** - “阻止”所有传入网络连接，DHCP、Bonjour 和 IPSec 等基本 Internet 服务需要的连接除外。 此设置还会阻止所有共享服务，包括屏幕共享、远程访问、iTunes 音乐共享等。  

- **隐藏模式**：  
  - **未配置**（*默认值*）-此设置使隐藏模式处于关闭状态。
  - **启用** - 打开隐藏模式以防止设备响应可能由恶意用户发出的探测请求。 启用后，设备会继续响应授权应用的传入请求。  

### <a name="gatekeeper"></a>网关守卫

有关详细信息，请参阅 [macOS 上的网关守卫](https://support.apple.com/HT202491)（打开 Apple 的网站）。

**允许从这些位置下载应用**：允许在不同位置的设备上安装支持的应用程序。 位置选项包括：

- **未配置**（*默认*）-"网关" 选项不影响符合性或不符合性。  
- **Mac App Store** - 仅安装 Mac App Store 的应用。 不能从第三方或由未确认的开发人员安装应用。 如果用户选择网关守卫来安装 Mac App Store 外部的应用，则该设备将被视为不符合。
- **Mac App Store 和已确认的开发人员** - 安装 Mac App Store 的应用并由已确认的开发人员安装应用。 macOS 检查开发人员的身份，并执行一些其他检查，以验证应用的完整性。 如果用户选择网关守卫来安装这些选项外部的应用，则该设备会被视为不符合。
- **任意位置** - 应用可以从任何地方以及由任何开发人员安装。 此选项最不安全。
 

## <a name="next-steps"></a>后续步骤

- [为不符合要求的设备添加操作](actions-for-noncompliance.md)并[使用范围标记来筛选策略](../fundamentals/scope-tags.md)。
- [监视符合性策略](compliance-policy-monitor.md)。
- 请参阅[适用于 iOS 设备的符合性策略设置](compliance-policy-create-ios.md)。