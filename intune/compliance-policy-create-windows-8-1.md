---
title: Microsoft Intune 中的 Windows 10 教育设置 - Azure | Microsoft Docs
description: 请参阅在 Microsoft Intune 中设置适用于 Windows 8.1 和 Windows Phone 8.1 设备的合规性时，可以使用的所有设置的列表。 执行在最小值和最大操作系统上，设置密码限制和长度，符合性检查上启用加密的数据存储和的详细信息。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ed863378616f8001beab89177c642404287e7d3
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424928"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>若要将设备标记为符合或不符合使用 Intune 的 Windows 8.1 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文列出并描述了可以在 Intune 中的 Windows 8.1 设备配置的不同的符合性设置。 作为你的移动设备管理 (MDM) 解决方案的一部分，使用这些设置以阻止简单密码，设置最小值和最高操作系统版本，等等。

此功能适用于：

- Windows Phone 8.1
- Windows 8.1 及更高版本

作为 Intune 管理员，使用这些符合性设置来帮助保护组织资源。 若要了解有关符合性策略以及所有系统必备组件的详细信息，请参阅[设备符合性入门](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>在开始之前

[创建合规性策略](create-compliance-policy.md#create-the-policy)。 有关**平台**，选择**Windows Phone 8.1**或**Windows 8.1 及更高版本**。

## <a name="device-properties"></a>设备属性

- **所需的最小操作系统**： 输入允许的最低版本。 设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级其设备，然后访问公司资源。
- **允许的最高 OS 版本**： 输入的最大允许版本。 如果设备使用的 OS 版本高于在规则中输入的版本，对公司资源的访问受阻。 会要求用户联系其 IT 管理员。除非将规则更改为允许 OS 版本，否则设备无法访问组织资源。

Windows 8.1 PC 返回版本 **3**。 对于 Windows，如果操作系统版本规则设置为 Windows 8.1，则该设备将报告为不符合要求，即使该设备具有 Windows 8.1 也是如此。

## <a name="system-security"></a>系统安全

### <a name="password"></a>密码

- 需要密码才可解锁移动设备：要求用户在访问其设备之前输入密码。
- 简单密码：设置为“阻止”后，用户无法创建简单密码，如 1234 或 1111。 设置为“未配置”以允许用户创建密码，例如 1234 或 1111。
- **最短密码长度**：输入密码必须包含的最小位数或最小字符数。

  对于运行 Windows 且通过 Microsoft 帐户访问的设备，无法正确评估符合性策略：
  - 如果最短密码长度大于 8 个字符
  - 或者，如果最小字符集数超过两个

- 密码类型：选择密码是应仅包含数值字符，还是应混合使用数字和其他字符（字母数字）。
  
  - 密码中的非字母数字字符数：如果“所需的密码类型”设置为“字母数字”，此设置将指定密码必须包含的最小字符集数。 四个字符集为：
    - 小写字母
    - 大写字母
    - 符号
    - 数字

    设置的数字越大，要求用户创建的密码越复杂。 对于通过 Microsoft 帐户访问的设备，在以下情况下，无法正确评估符合性策略：

    - 如果最短密码长度大于 8 个字符
    - 或字符集数下限超过两个

- **要求提供密码之前的非活动最大分钟数**：输入用户必须重新输入其密码前的空闲时间。
- 密码过期(天)：选择密码过期之前的天数，然后必须创建一个新密码。
- **要防止重用的以前的密码数**：输入以前用过的不能使用的密码数。

### <a name="encryption"></a>加密

- 需要对移动设备进行加密：要求对设备进行加密以连接到数据存储资源。

选择“确定” > “创建”以保存所做的更改。

## <a name="next-steps"></a>后续步骤

- [添加适用于不符合要求的设备操作](actions-for-noncompliance.md)并[使用筛选器策略的作用域标记](scope-tags.md)。
- [监视符合性策略](compliance-policy-monitor.md)。
- 请参阅[合规性策略设置适用于 Windows 10 及更高版本](compliance-policy-create-windows.md)设备。