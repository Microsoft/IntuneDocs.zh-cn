---
title: Microsoft Intune 中的 Windows 10 符合性设置 - Azure | Microsoft Docs
description: 查看在 Microsoft Intune 中为 Windows 10、Windows Holographic 和 Surface Hub 设备设置符合性时可以使用的所有设置的列表。 检查最小和最大操作系统的符合性，设置密码限制和长度，检查合作伙伴防病毒 (AV) 解决方案，启用数据存储加密等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2e427fe0889dcfb51ba5be322ed4db566cc29e9d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502462"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune 将设备标记为符合或不符合的 Windows 10 及更高版本设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文列出并描述了在 Intune 中可对 Windows 10 及更高版本设备配置的不同符合性设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置来要求使用 BitLocker，设置最小和最大操作系统，使用 Microsoft Defender 高级威胁防护 (ATP) 设置风险级别等。

此功能适用于：

- Windows 10 及更高版本
- Windows Holographic for Business
- Surface Hub

作为 Intune 管理员，请使用这些符合性设置来帮助保护组织资源。 若要详细了解符合性策略及其作用，请参阅[设备符合性入门](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>在开始之前

[创建合规性策略](create-compliance-policy.md#create-the-policy)。 在“平台”中，选择“Windows 10 及更高版本”   。

## <a name="device-health"></a>Device health

- **需要启用 BitLocker**：设置为“需要”时，在系统关闭或处于休眠状态时，设备能够保护存储在驱动器上的数据免受未经授权的访问  。 Windows BitLocker 驱动器加密可以加密所有存储在 Windows 操作系统卷上的数据。 BitLocker 使用 TPM 来帮助保护 Windows 操作系统和用户数据。 此外，它还有助于确认计算机不被篡改，即使它处于无人参与、丢失或被盗状态，也不例外。 如果计算机装有兼容的 TPM，BitLocker 将使用 TPM 来锁定保护数据的加密密钥。 因此，仅当 TPM 验证计算机状态后，才能访问密钥。

  设置为“未配置”（默认）时，不会评估此设置的符合性和不符合性  。

- **需要在设备上启用安全启动**：设置为“需要”时，系统会被强制启动到出厂受信任状态  。 启用时，用于启动设备的核心组件必须具有制造设备的组织所信任的正确加密签名。 UEFI 固件会在允许设备启动前确认签名。 如果有任何文件被篡改，从而破坏了签名，系统将不会启动。

  设置为“未配置”（默认）时，不会评估此设置的符合性和不符合性  。

  > [!NOTE]
  > 一些 TPM 1.2 和 2.0 设备支持“需要在设备上启用安全启动”设置  。 对于不支持 TPM 2.0 或更高版本的设备，Intune 中的策略状态显示为“不符合”  。 有关受支持版本的详细信息，请参阅[设备运行状况证明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)。

-  要求启用代码完整性 - 代码完整性是这样一项功能，它在每次将驱动程序或系统文件加载到内存时验证其完整性。 设置为“需要”时，代码完整性功能检测是否要将未签名的驱动程序文件或系统文件加载到内核中  。 此外，它还检测系统文件是否已被具有管理员特权的用户帐户运行的恶意软件更改。

  设置为“未配置”（默认）时，不会评估此设置的符合性和不符合性  。

更多资源：

- 有关 HAS 服务工作方式的详细信息，请参阅[运行状况证明 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)。
- [支持提示：将设备运行状况证明设置用作 Intune 符合性策略的一部分](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>设备属性

- 最低操作系统版本：以 major.minor.build.CU 数字格式输入所允许的最低版本   。 要获取正确的值，请打开命令提示符，然后键入 `ver`。 `ver` 命令返回以下格式的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  如果设备的 OS 版本低于你输入的版本，它会被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级自己的设备。 升级后，他们可以访问公司资源。

- 最高操作系统版本：以 major.minor.build.revision 数字格式输入所允许的最高版本   。 要获取正确的值，请打开命令提示符，然后键入 `ver`。 `ver` 命令返回以下格式的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  当设备使用的操作系统版本高于输入的版本时，将阻止对组织资源的访问。 系统会要求最终用户联系其 IT 管理员。 除非将规则更改为允许操作系统版本，否则设备无法访问组织资源。

-  移动设备所需的最低操作系统版本：以 major.minor.build 数字格式输入所允许的最低版本。

  如果设备的 OS 版本低于你输入的版本，它会被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级自己的设备。 升级后，他们可以访问公司资源。

-  移动设备所需的最高操作系统版本：以 major.minor.build 数字格式输入所允许的最高版本。

  当设备使用的操作系统版本高于输入的版本时，将阻止对组织资源的访问。 系统会要求最终用户联系其 IT 管理员。 除非将规则更改为允许该操作系统版本，否则设备无法访问组织资源。

-  有效的操作系统版本：输入可接受的操作系统版本的范围，包括最小值和最大值。 还可以导出  这些可接受的 OS 生成号的逗号分隔值 (CSV) 文件列表。

## <a name="configuration-manager-compliance"></a>Configuration Manager 符合性

仅适用于运行 Windows 10 及更高版本的共同管理设备。 仅 Intune 设备返回不可用状态。

- **要求 System Center Configuration Manager 设备合规性**：选择“需要”，强制 System Center Configuration Manager 中的所有设置（配置项目）符合要求  。 

  例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任意计划处于未知状态，此设备在 Intune 中不符合要求。
  
  如果你选择“未配置”  ，Intune 不会检查是否符合任何 Configuration Manager 设置要求。

## <a name="system-security"></a>系统安全

### <a name="password"></a>密码

-  需要密码才可解锁移动设备：要求  用户在访问其设备之前输入密码。 如果**未配置**，Intune 不会评估设备是否符合密码设置。
-  简单密码：设置为“阻止”  后，用户无法创建简单密码，如 1234  或 1111  。 设置为“未配置”  以允许用户创建密码，例如 1234  或 1111  。
- **密码类型**：选择所需的密码或 PIN 类型。 选项包括：

  - **设备默认值**：需要密码、数字 pin 或字母数字 pin
  - **数值**：需要密码或数字 PIN
  - **字母数字**：要求输入密码，或使用字母数字 PIN。 还要选择**密码复杂性**： 
    
    - **要求数字和小写字母**
    - **需要数字、小写字母和大写字母**
    - **需要数字、小写字母、大写字母和特殊字符**

    > [!TIP]
    > 字母数字密码策略可能会很复杂。 建议管理员阅读 Csp 获取详细信息：
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **最短密码长度**：输入密码必须包含的最小位数或最小字符数。
- **要求提供密码之前的非活动最大分钟数**：输入用户必须重新输入其密码前的空闲时间。
- **密码过期(天)** ：输入密码过期之前的天数（1 - 730 天），然后必须创建一个新密码。
- **要防止重用的以前的密码数**：输入以前用过的不能使用的密码数。
-  设备从空闲状态返回时需要输入密码（仅限移动版和全息版）：每次设备从空闲状态返回时强制用户输入密码。

  > [!IMPORTANT]
  > 当 Windows 桌面的密码要求更改时，用户下次登录时会受到影响，因为此时设备从空闲状态变为活动状态。 密码满足要求的用户仍然会被提示更改密码。

### <a name="encryption"></a>加密

-  设备上的数据存储加密：选择“需要”  加密设备上的数据存储。

  > [!NOTE]
  > 设备上的数据存储加密设置通常会检查设备上是否存在加密  。 为获取更可靠的加密设置，请考虑使用“需要 BitLocker”，它利用 Windows 设备运行状况证明来验证 TPM 级别的 Bitlocker 状态  。

### <a name="device-security"></a>设备安全

- **防火墙**：设置为 "**需要**启用 Microsoft Defender 防火墙"，并阻止用户关闭。 **未配置**（默认）不控制 Microsoft Defender 防火墙，也不更改现有设置。

  [防火墙 CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > 如果设备在重新启动后立即同步，或立即同步从睡眠状态唤醒，则此设置可能会报告为**错误**。 此方案可能不影响整体设备符合性状态。 若要重新评估符合性状态，请手动[同步设备](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)。

- **受信任的平台模块（TPM）** ：当设置为 "必需" 时，Intune 将检查版本是否符合**要求**。 如果 TPM 芯片版本大于0（零），则设备是合规的。 如果设备上没有 TPM 版本，则设备不合规。 如果**未配置**，Intune 不会检查设备的 TPM 芯片版本。

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion 节点](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **防病毒**：当设置为“需要”时，可使用在 [Windows 安全中心](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)注册的防病毒解决方案（如 Symantec 和 Microsoft Defender）来检查符合性  。 当“未配置”时，Intune 不会检查设备上安装的任何 AV 解决方案  。
- **反间谍软件**：当设置为“需要”时，可使用在 [Windows 安全中心](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)注册的反间谍软件解决方案（如 Symantec 和 Microsoft Defender）来检查符合性  。 当“未配置”时，Intune 不会检查设备上安装的任何反间谍软件解决方案  。

### <a name="defender"></a>Defender

- **Microsoft Defender 反恶意软件**：设置为**需要**启用 microsoft defender 反恶意软件服务，并阻止用户将其关闭。 **未配置**（默认）不控制服务，也不更改现有设置。
- **Microsoft Defender 反恶意软件最低版本**：输入 microsoft defender 反恶意软件服务的最小允许版本。 例如，输入 `4.11.0.0`。 留空时，可以使用任何版本的 Microsoft Defender 反恶意软件服务。
- **Microsoft Defender 反恶意软件安全智能最**新：控制设备上的 Windows 安全病毒和威胁防护更新。 **要求**强制 Microsoft Defender 安全智能处于最新状态。 **未配置**（默认）不强制任何要求。

  [Microsoft Defender 防病毒和其他 microsoft 反恶意软件的安全智能更新](https://www.microsoft.com/en-us/wdsi/defenderupdates)包含有关安全智能的详细信息。

- **实时保护**：**需要**启用实时保护，这会扫描恶意软件、间谍软件和其他不需要的软件。 **未配置**（默认）不控制此功能，也不更改现有设置。

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

- 要求设备不超过计算机风险评分：使用此设置将防御威胁服务的风险评估视为符合性的条件  。 选择允许的最大威胁级别：

  - 清除：此选项是最安全的，因为设备不能具有任何威胁  。 如果设备被检测到具有任一等级的威胁，就会被评估为不符合要求。
  - **低**：若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
  -  中：如果设备上存在的威胁为低级或中级，设备也将被评估为符合策略。 如果检测到设备存在高级威胁，则会确定为不符合要求。
  -  高：此选项是最不安全的，允许所有威胁级别。 如果将此解决方案仅用作报告目的，则可能有用。
  
  要将 Microsoft Defender ATP（高级威胁防护）设置为防御威胁服务，请参阅[启用使用条件访问权限的 Microsoft Defender ATP](advanced-threat-protection.md)。

选择“确定”   > “创建”  以保存所做的更改。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business 使用 Windows 10 及更高版本  的平台。 Windows Holographic for Business 支持以下设置：

-  “系统安全” > ”加密”   >   ”设备上的数据存储加密”。

若要对 Microsoft HoloLens 验证设备加密，请参阅[验证设备加密](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)。

## <a name="surface-hub"></a>Surface Hub

Surface Hub 使用  Windows 10 及更高版本的平台。 支持将 Surface Hub 用于符合性和条件访问。 若要在 Surface Hub 上启用这些功能，建议在 Intune 中[启用 Windows 10 自动注册](../enrollment/windows-enroll.md)（需要 Azure Active Directory (Azure AD)），并将 Surface Hub 设备用作目标设备组。 Surface Hub 必须加入 Azure AD，这样符合性和条件访问策略才能正常运行。

请参阅[设置 Windows 设备的注册](../enrollment/windows-enroll.md)获取指导。

## <a name="next-steps"></a>后续步骤

- [为不符合要求的设备添加操作](actions-for-noncompliance.md)并[使用范围标记来筛选策略](../fundamentals/scope-tags.md)。
- [监视符合性策略](compliance-policy-monitor.md)。
- 请参阅[适用于 Windows 8.1 设备的符合性策略设置](compliance-policy-create-windows-8-1.md)。
