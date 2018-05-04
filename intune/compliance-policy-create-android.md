---
title: 在 Microsoft Intune 中创建 Android 设备符合性策略 - Azure | Microsoft Docs
description: 创建或配置适用于 Android 设备的 Microsoft Intune 设备符合性策略。 选择允许使用已越狱设备、设置可接受的威胁级别、查看 Google Play、输入最低和最高操作系统版本、选择密码要求并允许旁加载应用程序。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: afc8edb38b667d744bb586d1ed5c82df8ab10f49
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>在 Intune 中添加适用于 Android 设备的设备符合性策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

适用于 Android 的 Intune 设备符合性策略指定 Android 设备必须遵循的规则和设置，确保符合性。 可以将这些策略与条件访问结合使用，从而允许或阻止访问公司资源。 还可获取设备报表并针对非符合性采取措施。 可在 Intune Azure 门户中创建每个平台的设备符合性策略。 若要了解有关符合性策略以及所有系统必备组件的详细信息，请参阅[设备符合性入门](device-compliance-get-started.md)。

下表说明了将符合性策略与条件访问策略一起使用时如何管理非符合性设置。

--------------------

|**策略设置**| **Android 4.0 及更高版本、Samsung Knox 标准版 4.0 及更高版本** |
| --- | ----|
| **PIN 或密码配置** |  已隔离 |
| **设备加密** | 已隔离 |
| **已越狱或取得 root 权限的设备** | 已隔离（非设置） |
| **电子邮件配置文件** | “不适用” |
| **最低操作系统版本** | 已隔离 |
| **最高操作系统版本** |   已隔离 |
| **Windows 运行状况证明** | “不适用” |

--------------------------

**已修正** = 设备操作系统强制合规性。 （例如，强制用户设置 PIN。）

**已隔离** = 设备操作系统不会强制合规性。 （例如，Android 设备不强制用户加密设备。）设备不符合时，系统将进行以下操作：

- 如果条件访问策略应用到用户，则将阻止该设备。
- 公司门户会通知用户任何合规性问题。

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. 对于“平台”，请选择“Android”。 选择“设置配置”，然后依次输入“设备运行状况”、“设备属性”和“系统安全”设置。 完成后，请选择“确定”，然后选择“创建”。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

<!---##  Compliance policy settings--->

## <a name="device-health"></a>Device health

- 取得 root 权限的设备：如果启用此设置，已越狱设备将被评估为不符合策略。
- 要求设备不高于设备威胁级别：使用此设置将 Lookout MTP 解决方案的风险评估视为符合性条件。 选择允许的最大威胁级别：
  - 安全：此选项是最安全的，设备不能具有任何威胁。 如果设备被检测到具有任一等级的威胁，则会被评估为不符合要求。
  - **低**：若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
  - 中：如果设备上存在的威胁为低级或中级，设备也将被评估为符合策略。 若检测到设备存在高级威胁，则将其确定为不合规。
  - 高：此选项是最不安全的，允许所有威胁级别。 如果将此解决方案仅用作报告目的，则可能有用。
- 配置 Google Play Services：要求安装并启用 Google Play Services 应用。 可通过 Google Play Services 进行安全更新，它是已获得认证的 Google 设备上的很多安全功能的基本依赖项。
- 最新的安全提供程序：要求最新的安全提供程序可以保护设备免受已知漏洞的攻击。
- 对应用进行威胁扫描：要求启用 Android“验证应用”功能。

  > [!NOTE]
  > 在旧版 Android 平台上，此功能是符合性设置。 Intune 只能检查在设备级别是否启用了此设置。 在具有工作配置文件 (Android for Work) 的设备上，此设置可以作为配置策略设置找到。 这允许管理员为设备启用此设置。

  如果企业使用 Android 工作配置文件，则可以为已注册的设备启用“对应用进行威胁扫描”。 建立设备配置文件，并且需要进行系统安全设置。 有关详细信息，请参阅 [Intune 中的 Android for Work 设备限制设置](device-restrictions-android-for-work.md)。

- SafetyNet 设备证明：输入必须满足的 [SafetyNet 证明](https://developer.android.com/training/safetynet/attestation.html)级别。 选项包括：
  - 未配置
  - 检查基本完整性
  - 检查基本完整性和已认证的设备

## <a name="device-property-settings"></a>设备属性设置

- 最低操作系统版本：设备不满足最低 OS 版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级其设备，然后访问公司资源。
- 最高操作系统版本：设备使用的操作系统版本高于规则中指定的版本时，会阻止访问公司资源。 会要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则设备不能访问公司资源。

## <a name="system-security-settings"></a>系统安全设置

### <a name="password"></a>密码

- 需要密码才可解锁移动设备：要求用户在访问其设备之前输入密码。
- 最短密码长度：输入用户密码必须包含的最小位数或最小字符数。
- 所需密码类型：选择密码是应仅包含数值字符，还是应混合使用数字和其他字符。 选择：
  - 设备默认值
  - **低安全性生物识别**
  - **至少为数字**
  - 复杂数字
  - **至少为字母**
  - **至少包含字母数字**
  - **至少为字母数字与符号**
- **要求提供密码之前的非活动最大分钟数**：输入用户必须重新输入其密码前的空闲时间。
- 密码过期(天)：选择密码过期之前的天数，然后必须创建一个新密码。
- 要防止重用的以前的密码数：输入最近用过的不能重用的密码数。 使用此设置限制用户创建以前用过的密码。

### <a name="encryption"></a>加密

- 设备（Android 4.0 及更高版本，或 KNOX 4.0 及更高版本）上的数据存储加密：选择“需要”加密设备上的数据存储。 选择“需要密码解锁移动设备”设置时将加密设备。

### <a name="device-security"></a>设备安全

- 阻止来自未知源的应用：选择此选项以阻止启用了“安全>未知源”源中的设备 (Android 4.0 – Android 7.x。 在 Android 8.0 及更高版本中不受支持）。 若要旁加载应用，必须允许未知源。 如果没有旁加载 Android 应用，则启用此符合性策略。

  > [!IMPORTANT]
  > 旁加载应用程序需要启用“阻止来自未知源的应用”设置。 仅在不旁加载设备上的 Android 应用时实施此合规性策略。

- 公司门户应用运行时完整性：检查公司门户应用是否安装了默认运行时环境、是否已正确签名、是否不处于调试模式以及是否从已知源安装。
- 在设备上阻止 USB 调试（Android 4.2 或更高版本）：选择以阻止设备使用 USB 调试功能。
- 最低安全修补程序级别（Android 6.0 或更高版本）：选择设备可具有的最旧的安全修补程序级别。 不满足此修补程序级别的设备将不符合要求。 输入的日期格式必须为 `YYYY-MM-DD`。

## <a name="assign-user-groups"></a>分配用户组

1. 选择已配置的策略。 现有策略位于“设备符合性” > “策略”中。
2. 选择策略，然后选择“分配”。 可以包括或排除 Azure Active Directory (AD) 安全组。
3. 选择“所选组”查看 Azure AD 安全组。 选择想要应用此策略的用户组，并选择“保存”向用户部署该策略。

你已将策略应用于用户。 将评估策略针对的用户所使用设备的符合性。

## <a name="next-steps"></a>后续步骤
[为不符合的设备自动发送电子邮件和添加操作](actions-for-noncompliance.md)  
[监视 Intune 设备符合性策略](compliance-policy-monitor.md)