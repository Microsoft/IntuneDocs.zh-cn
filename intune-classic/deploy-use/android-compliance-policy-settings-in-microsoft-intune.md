---
title: "适用于 Android 的合规性策略设置 | Microsoft Docs"
description: "本主题介绍适用于 Android 设备的设备合规性策略设置。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 06996ca5d6c330357d6fdee19963d425bc353070
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---


# <a name="compliance-policy-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Android 设备的合规性策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题中描述的策略设置适用于运行 Android 4.0 及更高版本或 Samsung KNOX 4.0 及更高版本的设备。

如果要查找关于其他平台的信息，请选择以下选项之一：
> [!div class="op_single_selector"]
- [适用于 iOS 设备的合规性策略设置](ios-compliance-policy-settings-in-microsoft-intune.md)
- [适用于 Windows 设备的合规性策略设置](windows-compliance-policy-settings-in-microsoft-intune.md)
- [适用于 Android for Work 设备的合规性策略设置](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>系统安全设置
### <a name="password"></a>Password
- **需要密码才可解锁移动设备**：将此选项设置为“是”，以要求用户在访问其设备之前输入密码。

-  **最短密码长度**：指定用户密码必须包含的最小位数或最小字符数。

- **密码质量**：此设置检测是否在设备上设置了指定的密码要求。 启用此设置可要求用户满足 Android 设备的特定密码要求。 选择：

  -   **低安全性生物识别**
  -   **必需**
  -   **至少为数字**
  -   **至少为字母**
  -   **至少包含字母数字**
  -   **包含符号的字母数字**

- **需要提供密码之前处于非活动状态的分钟数：**指定用户必须重新输入其密码前的空闲时间。

- **密码过期（天）**：选择用户密码过期之前的天数，然后必须创建一个新的密码。

- **记住密码历史记录**：将此设置与“防止重用以前的密码”结合使用，以限制用户使用以前创建的密码。

- **防止重用以前的密码：**如果选择了“记住密码历史记录”，请指定不能重用的以前用过的密码数量。

- **设备从空闲状态返回时需要密码**：与“要求提供密码之前的非活动分钟数”设置一起使用。 设备在“需要提供密码之前处于非活动状态的分钟数”设置指定的时间内处于非活动状态时，会提示用户输入密码才能访问设备。

### <a name="encryption"></a>加密
- **需要对移动设备进行加密**：将此选项设置为“是”，要求对移动设备进行加密以连接到资源。 当你配置“需要密码解锁移动设备”设置时将加密设备。

## <a name="device-health-and-security-settings"></a>设备运行状况和安全设置

- **设备不得越狱或取得 root 权限**：如果启用此设置，已越狱的设备将评估为不符合要求。
- **要求设备阻止安装来自未知来源的应用(Android 4.0 或更高版本)**：若要阻止启用了“安全”>“未知源”的设备，启用此设置并将其设置为“是”。  

>[!IMPORTANT]
>旁加载应用程序需要启用“**未知源**”设置。 仅在不旁加载设备上的 Android 应用时实施此合规性策略。

- **要求禁用 USB 调试(Android 4.2 或更高版本)**：指定是否要检测设备上是否启用了 USB 调试选项。
- **要求设备已启用“扫描设备的安全威胁”(Android 4.2-4.4)**：指定在设备上启用“验证应用”功能。
- **最低 Android 安全修补程序级别 (Android 6.0 或更高版本)**：指定最小 Android 修补程序级别。  不满足此修补程序级别的设备将会不相容。 必须以 YYYY-MM-DD 格式来指定日期。
- **需要启用设备威胁保护**：使用此设置将 Lookout MTP 解决方案的风险评估视为合规性的条件。 从下面选择一个允许的最高威胁等级：

  - **无（安全）**这是最安全的选项。 这意味着该设备不能具有任何威胁。 若检测到设备具有任何威胁，则将其评为不合规。
  - **低：**若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
  - **中：**若设备上存在的威胁为低级或中级，则将其评为合规。 若检测到设备存在高级威胁，则将其确定为不合规。
  - **高：**这是最不安全的选项。 本质上而言，此选项允许所有威胁等级，可能仅在将此解决方案用于报告时有用。

  有关详细信息，请参阅[创建 Lookout 设备符合性策略](create-lookout-device-compliance-policy.md)。

## <a name="device-property-settings"></a>设备属性设置

- **所需的最低 OS 版本：**设备不满足最低 OS 版本要求时，它将被报告为不符合要求。
  将显示一个链接，链接中包含有关如何升级的信息。 用户可以选择升级其设备，升级后他们可以访问公司资源。

- **允许的最高 OS 版本：**设备使用的 OS 版本高于规则中指定的版本时，将阻止访问公司资源，并要求用户联系其 IT 管理员。 除非变更规则以允许该 OS 版本，否则此设备将不能用于访问公司资源。

