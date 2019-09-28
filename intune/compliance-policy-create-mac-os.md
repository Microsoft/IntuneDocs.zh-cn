---
title: Microsoft Intune 中的 macOS 设备符合性设置 - Azure | Microsoft Docs
description: 查看在 Microsoft Intune 中为 macOS 设备设置符合性时可以使用的所有设置的列表。 要求使用 Apple 的系统完整性保护，设置密码限制，要求使用防火墙，允许网关守卫等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0e3164c84c9a4088068fcf920903c6bb76cd30a
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "71305071"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune 将设备标记为符合或不符合的 macOS 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文列出并描述了在 Intune 中可针对 macOS 设备配置的不同符合性设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置来设置最低和最高操作系统版本，设置要过期的密码等。

此功能适用于：

- macOS

作为 Intune 管理员，请使用这些符合性设置来帮助保护组织资源。 若要详细了解符合性策略及其作用，请参阅[设备符合性入门](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>在开始之前

[创建合规性策略](create-compliance-policy.md#create-the-policy)。 对于“平台”  ，选择“macOS”  。

## <a name="device-health"></a>设备运行状况

- **需要系统完整性保护**：“需要”macOS 设备启用[系统完整性保护](https://support.apple.com/HT204899)（打开 Apple 的网站）  。 设置为“未配置”（默认）时，不会评估此设置的符合性和不符合性  。

## <a name="device-properties"></a>设备属性

-  最低操作系统版本：设备不满足最低 OS 版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级其设备，然后访问公司资源。
-  最高操作系统版本：设备使用的操作系统版本高于规则中指定的版本时，会阻止访问公司资源。 会要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则设备不能访问公司资源。
- **最低 OS 内部版本**：当 Apple 发布安全更新时，通常会更新内部版本号，而非 OS 版本。 使用此功能可在设备上输入允许的最低内部版本号。
- **最高 OS 内部版本**：当 Apple 发布安全更新时，通常会更新内部版本号，而非 OS 版本。 使用此功能可在设备上输入允许的最高内部版本号。

## <a name="system-security-settings"></a>系统安全设置

### <a name="password"></a>密码

-  需要密码才可解锁移动设备：要求  用户在访问其设备之前输入密码。
-  简单密码：设置为“阻止”  后，用户无法创建简单密码，如 1234  或 1111  。 设置为“未配置”  以允许用户创建密码，例如 1234  或 1111  。
- **最短密码长度**：输入密码必须包含的最小位数或最小字符数。
-  密码类型：  选择密码是应仅包含数值字符，还是应混合使用数字和其他字符（字母数字）  。
- **密码中的非字母数字字符数**：输入密码中必须包含的最小特殊字符（如 `&`、`#`、`%`、`!` 等）数。

    设置的数字越大，要求用户创建的密码越复杂。

- **要求提供密码之前的非活动最大分钟数**：输入用户必须重新输入其密码前的空闲时间。
-  密码过期(天)：选择密码过期之前的天数，然后必须创建一个新密码。
- **要防止重用的以前的密码数**：输入以前用过的不能使用的密码数。

    > [!IMPORTANT]
    > 当 macOS 设备上的密码要求发生更改时，直到用户下次更改密码时此更改才会生效。 例如，如果将密码长度限制设置为 8 位数，而 macOS 设备当前使用的是 6 位数密码，则在用户下次更新设备上的密码前，该设备将仍保持符合状态。

### <a name="encryption"></a>加密

-  设备上的数据存储加密：选择“需要”  加密设备上的数据存储。

### <a name="device-security"></a>设备安全

防火墙保护设备免受未经授权的网络访问。 可以使用防火墙控制基于每个应用程序的连接。 

- **防火墙**：选择“启用”可帮助保护设备免受未经授权的访问  。 启用此功能，可以处理传入的 Internet 连接，并使用隐藏模式。 “未配置”（默认）使防火墙保持关闭状态，允许网络流量（未阻止）  。
- **传入连接**：“阻止”所有传入网络连接，DHCP、Bonjour 和 IPSec 等基本 Internet 服务需要的连接除外  。 此设置还会阻止所有共享服务，包括屏幕共享、远程访问、iTunes 音乐共享等。 “未配置”（默认）允许传入连接和共享服务  。
- **隐藏模式**：“启用”隐藏模式以防止设备响应可能由恶意用户发出的探测请求  。 启用后，设备会继续响应授权应用的传入请求。 “未配置”（默认）使隐藏模式保持关闭状态  。

### <a name="gatekeeper"></a>网关守卫

有关详细信息，请参阅 [macOS 上的网关守卫](https://support.apple.com/HT202491)（打开 Apple 的网站）。

**允许从这些位置下载应用**：允许在不同位置的设备上安装支持的应用程序。 位置选项包括：

- **未配置**：默认。 网关守卫选项对于符合性或不符合性无影响。 
- **Mac App Store**：仅安装 Mac App Store 的应用。 不能从第三方或由未确认的开发人员安装应用。 如果用户选择网关守卫来安装 Mac App Store 外部的应用，则该设备将被视为不符合。
- **Mac App Store 和已确认的开发人员**：安装 Mac App Store 的应用并由已确认的开发人员安装应用。 macOS 检查开发人员的身份，并执行一些其他检查，以验证应用的完整性。 如果用户选择网关守卫来安装这些选项外部的应用，则该设备会被视为不符合。
- **任意位置**：应用可以从任何地方以及由任何开发人员安装。 此选项最不安全。

选择“确定”   > “创建”  以保存所做的更改。

## <a name="next-steps"></a>后续步骤

- [为不符合要求的设备添加操作](actions-for-noncompliance.md)并[使用范围标记来筛选策略](scope-tags.md)。
- [监视符合性策略](compliance-policy-monitor.md)。
- 请参阅[适用于 iOS 设备的符合性策略设置](compliance-policy-create-ios.md)。