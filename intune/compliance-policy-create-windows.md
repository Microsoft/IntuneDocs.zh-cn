---
title: 检查 Microsoft Intune 中的 Windows 设备是否符合要求 - Azure | Microsoft Docs
description: 为 Windows Phone 8.1、Windows 8.1 和更高版本以及 Windows 10 和更高版本的设备创建或配置 Microsoft Intune 设备符合性策略。 检查最低和最高操作系统的符合性，设置密码限制和长度，要求启用 BitLocker，检查第三方 AV 解决方案，设置可接受的威胁级别以及启用对数据存储的加密，包括 Surface Hub 和 Windows Holographic for Business。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6e82e24f051e64d07487d915ac6fd0848727ecf
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566805"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>在 Intune 中添加适用于 Windows 设备的设备符合性策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 设备符合性策略包括设备符合要求所必须满足的规则和设置。 结合使用这些策略与条件访问，可以允许或阻止对组织资源的访问。 还可获取设备报表并针对非符合性采取措施。

若要了解有关符合性策略以及所有系统必备组件的详细信息，请参阅[设备符合性入门](device-compliance-get-started.md)。

下表说明了将符合性策略与条件访问策略一起使用时如何管理非符合性设置。

---------------------------

| **策略设置** | **Windows 8.1 及更高版本** | **Windows Phone 8.1 及更高版本** |
|----| ----| --- |
| **PIN 或密码配置** | 已修正 | 已修正 |   
| **设备加密** | 不适用 | 已修正 |   
| **已越狱或取得 root 权限的设备** | “不适用” | “不适用” |  
| **电子邮件配置文件** | “不适用” | “不适用” |   
| **最低操作系统版本** | 已隔离 | 已隔离 |   
| **最高操作系统版本** | 已隔离 | 已隔离 |   
| **Windows 运行状况证明** | 已隔离：Windows 10 和 Windows 10 移动版|不适用：Windows 8.1 |

-------------------------------

**已修正** = 设备操作系统强制合规性。 （例如，强制用户设置 PIN。）

**已隔离** = 设备操作系统不会强制合规性。 （例如，Android 设备不强制用户加密设备。）设备不符合时，系统将进行以下操作：

- 如果条件访问策略应用到用户，则将阻止该设备。
- 公司门户会通知用户任何合规性问题。

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. 对于“平台”，请选择“Windows Phone 8.1”、“Windows 8.1 及更高版本”或“Windows 10 及更高版本”。
6. 选择“设置配置”，然后依次输入“设备运行状况”、“设备属性”和“系统安全”设置。 完成后，请选择“确定”，然后选择“创建”。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Windows 8.1 设备策略设置

这些策略设置适用于运行以下平台的设备：

- Windows Phone 8.1
- Windows 8.1 及更高版本

### <a name="device-properties"></a>设备属性

- 所需的最低操作系统版本：设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级其设备，然后访问公司资源。
- **允许的最高操作系统版本**：设备使用的操作系统版本高于规则中指定的版本时，会阻止访问公司资源。 会要求用户联系其 IT 管理员。除非将规则更改为允许 OS 版本，否则设备无法访问组织资源。

Windows 8.1 PC 返回版本 **3**。 对于 Windows，如果操作系统版本规则设置为 Windows 8.1，则该设备将报告为不符合要求，即使该设备具有 Windows 8.1 也是如此。

### <a name="system-security"></a>系统安全

#### <a name="password"></a>密码

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

#### <a name="encryption"></a>加密

- 需要对移动设备进行加密：要求对设备进行加密以连接到数据存储资源。

## <a name="windows-10-and-later-policy-settings"></a>Windows 10 和更高版本的策略设置

### <a name="device-health"></a>Device health

- 需要启用 BitLocker：如果启用了 BitLocker，在系统关闭或进入休眠状态时，设备能够保护存储在驱动器上的数据免受未经授权的访问。 Windows BitLocker 驱动器加密可以加密所有存储在 Windows 操作系统卷上的数据。 BitLocker 使用 TPM 来帮助保护 Windows 操作系统和用户数据。 此外，它还有助于确认计算机不被篡改，即使它处于无人参与、丢失或被盗状态，也不例外。 如果计算机装有兼容的 TPM，BitLocker 将使用 TPM 来锁定保护数据的加密密钥。 因此，仅当 TPM 验证计算机状态后，才能访问密钥。
- 需要在设备上启用安全启动：启用安全启动后，系统会被强制启动到出厂信任状态。 此外，启用安全启动后，用于启动设备的核心组件必须具有制造设备的组织所信任的正确加密签名。 UEFI 固件会在允许设备启动前确认签名。 如果有任何文件被篡改，从而破坏了签名，系统将不会启动。

  > [!NOTE]
  > 一些 TPM 1.2 和 2.0 设备支持“需要在设备上启用安全启动”设置。 对于不支持 TPM 2.0 或更高版本的设备，Intune 中的策略状态显示为“不符合”。 有关受支持版本的详细信息，请参阅[设备运行状况证明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)。

- 要求启用代码完整性 - 代码完整性是这样一项功能，它在每次将驱动程序或系统文件加载到内存时验证其完整性。 代码完整性功能检测是否要将未签名的驱动程序文件或系统文件加载到内核中。 此外，它还检测系统文件是否已被具有管理员特权的用户帐户运行的恶意软件修改。

有关 HAS 服务工作方式的详细信息，请参阅[运行状况证明 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)。

### <a name="device-properties"></a>设备属性

- 最低操作系统版本：以 major.minor.build.CU 数字格式输入所允许的最低版本。 要获取正确的值，请打开命令提示符，然后键入 `ver`。 `ver` 命令返回以下格式的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  如果设备的 OS 版本低于你输入的版本，它会被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级自己的设备。 升级后，他们可以访问公司资源。

- 最高操作系统版本：以 major.minor.build.revision 数字格式输入所允许的最高版本。 要获取正确的值，请打开命令提示符，然后键入 `ver`。 `ver` 命令返回以下格式的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  如果设备的 OS 版本高于在规则中输入的版本，不仅对公司资源的访问受阻，而且用户还被要求联系 IT 管理员。除非将规则更改为允许 OS 版本，否则设备无法访问公司资源。

- 移动设备所需的最低操作系统版本：以 major.minor.build 数字格式输入所允许的最低版本。

  如果设备的 OS 版本低于你输入的版本，它会被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级自己的设备。 升级后，他们可以访问公司资源。

- 移动设备所需的最高操作系统版本：以 major.minor.build 数字格式输入所允许的最高版本。

  如果设备的 OS 版本高于你输入的版本，不仅对公司资源的访问受阻，而且用户还被要求联系 IT 管理员。除非将规则更改为允许 OS 版本，否则设备无法访问公司资源。

- 有效的操作系统版本：输入可接受的操作系统版本的范围，包括最小值和最大值。 还可以导出这些可接受的 OS 生成号的逗号分隔值 (CSV) 文件列表。

### <a name="configuration-manager-compliance"></a>Configuration Manager 符合性

仅适用于运行 Windows 10 及更高版本的共同管理设备。 仅 Intune 设备返回不可用状态。

- **要求设备符合性从 System Center Configuration Manager**： 选择**需要**若要强制在 System Center Configuration Manager 以符合要求的所有设置 （配置项目）。 

  例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任意计划处于未知状态，此设备在 Intune 中不符合要求。
  
  如果你选择“未配置”，Intune 不会检查是否符合任何 Configuration Manager 设置要求。

### <a name="system-security-settings"></a>系统安全设置

#### <a name="password"></a>密码

- 需要密码才可解锁移动设备：要求用户在访问其设备之前输入密码。
- 简单密码：设置为“阻止”后，用户无法创建简单密码，如 1234 或 1111。 设置为“未配置”以允许用户创建密码，例如 1234 或 1111。
- 密码类型：选择密码是应仅包含数值字符，还是应混合使用数字和其他字符（字母数字）。

  - 密码中的非字母数字字符数：如果“所需的密码类型”设置为“字母数字”，此设置将指定密码必须包含的最小字符集数。 四个字符集为：
    - 小写字母
    - 大写字母
    - 符号
    - 数字

    设置的数字越大，要求用户创建的密码越复杂。

- **最短密码长度**：输入密码必须包含的最小位数或最小字符数。
- **要求提供密码之前的非活动最大分钟数**：输入用户必须重新输入其密码前的空闲时间。
- 密码过期(天)：选择密码过期之前的天数，然后必须创建一个新密码。
- **要防止重用的以前的密码数**：输入以前用过的不能使用的密码数。
- 设备从空闲状态返回时需要输入密码（仅限移动版和全息版）：每次设备从空闲状态返回时强制用户输入密码。

#### <a name="encryption"></a>加密

- 设备上的数据存储加密：选择“需要”加密设备上的数据存储。

  > [!NOTE]
  > 设备上的数据存储加密设置通常会检查设备上是否存在加密。 为获取更可靠的加密设置，请考虑使用“需要 BitLocker”，它利用 Windows 设备运行状况证明来验证 TPM 级别的 Bitlocker 状态。

#### <a name="device-security"></a>设备安全

- **防病毒**：当设置为“需要”时，可使用在 [Windows 安全中心](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)注册的防病毒解决方案（如 Symantec 和 Windows Defender）来检查符合性。 当“未配置”时，Intune 不会检查设备上安装的任何 AV 解决方案。
- **反间谍软件**：当设置为“需要”时，可使用在 [Windows 安全中心](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)注册的反间谍软件解决方案（如 Symantec 和 Windows Defender）来检查符合性。 当“未配置”时，Intune 不会检查设备上安装的任何反间谍软件解决方案。

### <a name="windows-defender-atp"></a>Windows Defender ATP

- 要求设备不超过计算机风险评分：使用此设置将防御威胁服务的风险评估视为符合性的条件。 选择允许的最大威胁级别：
  - 清除：此选项是最安全的，因为设备不能具有任何威胁。 如果设备被检测到具有任一等级的威胁，就会被评估为不符合要求。
  - **低**：若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
  - 中：如果设备上存在的威胁为低级或中级，设备也将被评估为符合策略。 如果设备被检测到存在高级威胁，则会被确定为不符合要求。
  - 高：此选项是最不安全的，允许所有威胁级别。 如果将此解决方案仅用作报告目的，则可能有用。
  
  要将 Windows Defender ATP（高级威胁防护）设置为防御威胁服务，请参阅[启用使用条件访问权限的 Windows Defender ATP](advanced-threat-protection.md)。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business 使用 Windows 10 及更高版本的平台。 Windows Holographic for Business 支持以下设置：

- “系统安全” > ”加密” > ”设备上的数据存储加密”。

若要对 Microsoft HoloLens 验证设备加密，请参阅[验证设备加密](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)。

## <a name="surface-hub"></a>Surface Hub
Surface Hub 使用 Windows 10 及更高版本的平台。 支持将 Surface Hub 用于符合性和条件访问。 若要在 Surface Hub 上启用这些功能，建议在 Intune 中[启用 Windows 10 自动注册](windows-enroll.md)（还需要 Azure Active Directory (Azure AD)），并将 Surface Hub 设备用作目标设备组。 Surface Hub 必须加入 Azure AD，这样符合性和条件访问策略才能正常运行。

请参阅[设置 Windows 设备的注册](windows-enroll.md)获取指导。

## <a name="assign-user-or-device-groups"></a>分配用户或设备组

1. 选择已配置的策略。 现有策略位于“设备符合性” > “策略”中。
2. 选择策略，然后选择“分配”。 可以包括或排除 Azure AD 安全组。
3. 选择“所选组”查看 Azure AD 安全组。 选择要应用此策略的用户或设备组，然后选择“保存”部署策略。

你已应用此策略。 需对策略目标用户所用的设备进行符合性评估。

## <a name="next-steps"></a>后续步骤
[为不符合的设备自动发送电子邮件和添加操作](actions-for-noncompliance.md)  
[监视 Intune 设备符合性策略](compliance-policy-monitor.md)
