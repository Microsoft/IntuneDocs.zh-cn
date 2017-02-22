---
title: "如何创建适用于 Android 的合规性策略 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何创建适用于 Android 设备的合规性策略。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: 16308e61986a4354181b8b0eeace012d65769c66


---

# <a name="how-to-create-a-device-compliance-policy-for-android-devices-in-intune-azure-preview"></a>如何在 Intune Azure 预览版中创建适用于 Android 设备的设备合规性策略


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

为每个平台创建合规性策略。  可以在 Azure 门户中创建合规性策略。 若要详细了解什么是合规性策略，请参阅[什么是设备合规性](what-is-device-compliance.md)主题。 若要了解创建合规性策略之前需要解决的先决条件，请参阅[设备合规性入门](get-started-with-device-compliance.md)主题。

下表说明了将合规性策略与条件访问策略一起使用时如何管理非合规性设置。

--------------------

|**策略设置**| **Android 4.0 及更高版本、Samsung Knox 标准版 4.0 及更高版本** |
| --- | ----|
| **PIN 或密码配置** |  已隔离 |
| **设备加密** | 已隔离 |
| **已越狱或取得 root 权限的设备** | 已隔离（非设置） |
| **电子邮件配置文件** | 不适用 |
| **最低操作系统版本** | 已隔离 |
| **最高操作系统版本** |   已隔离 |
| **Windows 运行状况证明** | 不适用 |

--------------------------


**已修正** = 设备操作系统强制合规性。 （例如，强制用户设置 PIN。）

**已隔离** = 设备操作系统不会强制合规性。 （例如，Android 设备不强制用户加密设备。）当设备不合规时，进行以下操作：

- 如果条件访问策略应用到用户，则将阻止该设备。
- 公司门户会通知用户任何合规性问题。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>在 Azure 门户中创建合规性策略

1. 在“Intune”边栏选项卡中，选择“设置设备合规性”。 在“管理”下，选择“所有设备合规性策略”，然后选择“创建”。
2. 键入名称、说明，并选择要应用此策略的平台。
3. 选择“合规性要求”以指定“安全性”、“设备运行状况”和“设备属性”设置。 完成后，选择“确定”。

<!-- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.-->

## <a name="assign-user-groups"></a>分配用户组

若要为用户分配合规性策略，请选择已配置的策略。 可在“合规性 - 策略”边栏选项卡中找到现有策略。

1. 选择策略，然后选择“分配”。 此操作将打开边栏选项卡，可以在其中选择“Azure Active Directory 安全组”并将其分配给策略。
2. 选择“选择组”以打开显示 Azure AD 安全组的边栏选项卡。 可以在其中找到 Azure Active Directory 中的安全组。  可选择希望将此策略应用于的用户组，然后选择“选择”。 选择“选择”会将策略部署到用户。

你已将策略应用于用户。  将评估策略针对的用户所使用设备的合规性。

<!---##  Compliance policy settings--->

## <a name="system-security-settings"></a>系统安全设置

### <a name="password"></a>密码

- **需要密码才可解锁移动设备**：将此选项设置为“是”，以要求用户在访问其设备之前输入密码。
- **最短密码长度**：指定用户密码必须包含的最小位数或最小字符数。
- **密码质量**：此设置检测是否在设备上设置了指定的密码要求。 启用此设置可要求用户满足 Android 设备的特定密码要求。 选择：
  - **低安全性生物识别**
  - **必需**
  - **至少为数字**
  - **至少为字母**
  - **至少包含字母数字**
  - **包含符号的字母数字**
- **要求提供密码之前的非活动分钟数**：指定用户必须重新输入其密码前的空闲时间。
- **密码过期(天)**：选择密码过期之前的天数，然后必须创建一个新密码。
- **记住密码历史记录**：将此设置与“防止重用以前的密码”结合使用，以限制用户创建以前使用过的密码。
- **防止重用以前的密码**：如果选择了“记住密码历史记录”，请指定不能重用的以前用过的密码数。
- **设备从空闲状态返回时需要密码**：将此设置与“要求提供密码之前的非活动分钟数”设置一起使用。 设备在“要求提供密码之前的非活动分钟数”设置指定的时间内处于非活动状态时，将提示用户输入密码才能访问设备。

### <a name="encryption"></a>加密

- **需要对移动设备进行加密**：将此选项设置为“是”，要求对设备进行加密以连接到资源。 选择“需要密码解锁移动设备”设置时将加密设备。

## <a name="device-health-and-security-settings"></a>设备运行状况和安全设置

- **设备不得越狱或取得 root 权限**：如果启用此设置，已越狱的设备将评估为不合规。
- **要求设备阻止安装来自未知来源的应用(Android 4.0 或更高版本)**：若要阻止启用了“安全”>“未知源”的设备，请启用此设置并将其设置为“是”。

### <a name="important"></a>重要

侧加载应用程序需要启用“未知源”设置。 仅在不旁加载设备上的 Android 应用时实施此合规性策略。

- **要求禁用 USB 调试(Android 4.2 或更高版本)**：此设置指定是否要检测并确认设备上启用了 USB 调试选项。
- **要求设备已启用“扫描设备的安全威胁”(Android 4.2-4.4)**：此设置指定在设备上启用“**验证应用**”功能。
- **最低 Android 安全修补程序级别 (Android 6.0 或更高版本)**：使用此设置指定最小 Android 修补程序级别。 不满足此修补程序级别的设备将会不相容。 必须以 YYYY-MM-DD 格式来指定日期。
- **需要启用设备威胁保护**：使用此设置将 Lookout MTP 解决方案的风险评估视为合规性的条件。 从下面选择一个允许的最高威胁等级：
  - **无(安全)**：这是最安全的选项。 这意味着该设备不能具有任何威胁。 若检测到设备具有任一等级的威胁，则将其评为不合规。
  - **低**：若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
  - **中**：若设备上存在的威胁为低级或中级，则将其评为合规。 若检测到设备存在高级威胁，则将其确定为不合规。
  - **高**：这是最不安全的选项。 实际上，这允许所有威胁级别。 如果将此解决方案仅用作报告，则可能有用。

有关详细信息，请参阅[在合规性策略中启用设备威胁保护规则](https://docs.microsoft.com/en-us/intune/deploy-use/enable-device-threat-protection-rule-in-compliance-policy)。

## <a name="device-property-settings"></a>设备属性设置

- **所需的最低操作系统版本**：设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 用户可以选择升级其设备，升级后他们可以访问公司资源。
- **允许的最高操作系统版本**：设备使用的操作系统版本高于规则中指定的版本时，将阻止访问公司资源，并要求用户联系其 IT 管理员。 除非变更规则以允许该操作系统版本，否则该设备将不能用于访问公司资源。

<!--- ## Next steps

[How to monitor device compliance](monitor-device-compliance.md)--->



<!--HONumber=Feb17_HO1-->


