---
title: "适用于 Windows 设备的合规性策略设置"
description: "本主题描述了可为 Windows 设备的合规性策略配置的规则和设置。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f996842c-e9a4-4819-acb4-ee66e8fb35b8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1c9a59fa97c11794ff8ad0a0eaa41630bfdf847e
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="compliance-policy-settings-for-windows-devices-in-microsoft-intune"></a>Microsoft Intune 中的适用于 Windows 设备的合规性策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题中描述的策略设置适用于运行 Windows 操作系统的设备。 以下各部分描述了支持的 Windows 版本。

如果要查找有关其他平台的信息，请选择其中之一：
> [!div class="op_single_selector"]
- [适用于 iOS 设备的合规性策略设置](ios-compliance-policy-settings-in-microsoft-intune.md)
- [适用于 Android 设备的合规性策略设置](android-compliance-policy-settings-in-microsoft-intune.md)
- [适用于 Android for Work 的合规性策略设置](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="compliance-policy-settings-for-windows-phone-devices"></a>适用于 Windows Phone 设备的合规性策略设置
本节中列出的设置支持 Windows Phone 8.1 及更高版本。

### <a name="system-security-settings"></a>系统安全设置
#### <a name="password"></a>Password
- **需要密码才可解锁移动设备**：将此选项设置为“是”，要求用户在访问其设备之前输入密码。

- **允许简单密码**：将此选项设置为“是”，允许用户创建简单密码，如 **1234** 或 **1111**。

-  **最短密码长度**：指定用户密码必须包含的最小位数或最小字符数。
- **所需的密码类型**：指定用户必须创建“字母数字”密码还是“数字”密码。

  对于运行 Windows 且通过 Microsoft 帐户访问的设备，如果最短密码长度超过 8 个字符或者最小字符集数大于 2，则将无法正确评估合规性策略。

- **最小字符集数**：如果“所需的密码类型”设置为“字母数字”，此设置将指定密码必须包含的最小字符集数。 四个字符集为：
  -   小写字母
  -   大写字母
  -   符号
  -   数字

  设置的数字越大，要求用户创建的密码越复杂。 对于运行 Windows 且通过 Microsoft 帐户访问的设备，如果最短密码长度超过 8 个字符或者最小字符集数大于 2，则将无法正确评估合规性策略。

- **要求提供密码之前的非活动分钟数**：此设置指定用户必须重新输入其密码前的空闲时间。

- **密码过期 (天)**：选择用户密码过期而必须创建新密码之前的天数。

- **记住密码历史记录：**将此设置与“防止重用旧密码”结合使用，限制用户使用以前创建的密码。

- **防止重用以前的密码**：如果选择了“记住密码历史记录”，请指定不能重用的以前用过的密码数量。
- **设备从空闲状态返回时需要密码**：与“要求提供密码之前的非活动分钟数”设置一起使用此设置。 设备在“要求提供密码之前的非活动分钟数”设置指定的时间内处于非活动状态时，将提示用户输入密码才能访问设备。

  > [!NOTE]
  > 此设置适用于 Windows 10 移动版设备。

#### <a name="encryption"></a>加密
- **需要对移动设备进行加密**：将此选项设置为“是”，要求对移动设备进行加密以连接到资源。

### <a name="device-health-settings"></a>设备运行状况设置
- **要求设备被报告为正常**：可以在新的或现有的合规性策略中设置规则，要求 **Windows 10 移动版**设备必须被报告为正常。  如果启用此设置，将通过运行状况证明服务 (HAS) 评估 Windows 10 设备的这些数据点：
  -  **启用 BitLocker**：Bitlocker 打开的情况下，当系统关闭或进入休眠状态时，设备可保护存储在驱动器上的数据，防止未经授权的访问。 Windows BitLocker 驱动器加密可以加密所有存储在 Windows 操作系统卷上的数据。 BitLocker 使用 TPM 来帮助保护 Windows 操作系统和用户数据。 BitLocker 还有助于确保计算机不被篡改，即使它无人管理、丢失或被盗。 如果计算机装有兼容的 TPM，BitLocker 将使用 TPM 来锁定帮助保护数据的加密密钥。 这样，在 TPM 验证计算机状态之前则无法访问密钥。
  -  **启用代码完整性**：代码完整性是一种功能，可用于在每次将驱动程序或系统文件载入内存时，验证它们的完整性。 代码完整性检测是否正在将未签名的驱动程序或系统文件加载到内核中。 它还检测系统文件是否已被具有管理员权限的用户帐户运行的恶意软件进行了修改。
  - **启用安全启动**：启用安全启动后，系统会被强制启动到出厂信任状态。 此外，启用安全启动后，用于启动设备的核心组件必须具有制造设备的组织所信任的正确加密签名。 UEFI 固件会在允许设备启动前确认这一点。 如果有任何文件被篡改或破坏了签名，系统将不会启动。

  > [!IMPORTANT]
  > Windows 设备不支持作为设备运行状况证明的一部分安装的第三方**开机初期启动的反恶意软件** (ELAM)。

  有关 HAS 服务工作方式的信息，请参阅[运行状况证明 CSP](https://msdn.microsoft.com/library/dn934876.aspx)。
###  <a name="device-property-settings"></a>设备属性设置
- **所需的最低操作系统版本**：设备不满足最低操作系统版本要求时，它将被报告为不符合要求。
    将显示一个链接，链接中包含有关如何升级的信息。 用户可以选择升级其设备，然后他们可以访问公司资源。

- **允许的最高操作系统版本**：设备使用的操作系统版本高于规则中指定的版本时，将阻止访问公司资源，并要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则该设备将不能用于访问公司资源。


## <a name="compliance-policy-settings-for-windows-pcs"></a>适用于 Windows PC 的合规性策略设置
此节中列出的设置在 Windows PC 上受支持。
### <a name="system-security-settings"></a>系统安全设置
#### <a name="password"></a>Password
- **最短密码长度**：在 Windows 8.1 上受支持。

  指定用户密码必须包含的最小位数或最小字符数。

  对于通过 Microsoft 帐户访问的设备，如果“最短密码长度”超过 8 个字符或者“最小字符集数”大于 2 个字符，则将无法正确评估合规性策略。

- **所需密码类型**：在 Windows RT、Windows RT 8.1 和 Windows 8.1 上受支持。

  指定用户必须创建“字母数字”密码还是“数字”密码。

- **最小字符集数**：在 Windows RT、Windows RT 8.1 和 Windows 8.1 上受支持。

  如果“所需的密码类型”设置为“字母数字”，此设置指定密码必须包含的字符集的最小数字。 四个字符集为：
  -   小写字母
  -   大写字母
  -   符号
  -   数字     

  设置的数字越大，要求用户创建的密码越复杂。 对于通过 Microsoft 帐户访问的设备，如果“最短密码长度”超过 8 个字符或者“最小字符集数”大于 2 个字符，则将无法正确评估合规性策略。

- **要求提供密码之前的非活动状态分钟数**：在 Windows RT、Windows RT 8.1 和 Windows 8.1 上受支持。

  指定用户必须重新输入密码前的空闲时间。

- **密码过期 (天数)**：在 Windows RT、Windows RT 8.1 和 Windows 8.1 上受支持。

  选择用户密码过期而必须创建新密码之前的天数。

- **记住密码历史记录**：在 Windows RT、Windows RT 和 Windows 8.1 上受支持。

  将此设置与“防止重用旧密码”结合使用，以限制用户使用以前创建的密码。

- **防止重用以前的密码**：在 Windows RT、Windows RT 8.1 和 Windows 8.1 上受支持。

  如果选择了“记住密码历史记录”，请指定不能重用的以前用过的密码数量。

### <a name="device-health-settings"></a>设备运行状况设置
- **需要设备被报告为正常**：在 Windows 10 设备上受支持。
可以在新的或现有的合规性策略中设置规则，要求 Windows 10 设备必需被报告为正常。 如果启用此设置，将通过运行状况证明服务 (HAS) 评估 Windows 10 设备的这些数据点：
  -  **启用 BitLocker**：Bitlocker 打开的情况下，当系统关闭或进入休眠状态时，设备可保护存储在驱动器上的数据，防止未经授权的访问。 Windows BitLocker 驱动器加密可以加密所有存储在 Windows 操作系统卷上的数据。 BitLocker 使用 TPM 来帮助保护 Windows 操作系统和用户数据。 BitLocker 还有助于确保计算机不被篡改，即使它无人管理、丢失或被盗。 如果计算机装有兼容的 TPM，BitLocker 将使用 TPM 来锁定帮助保护数据的加密密钥。 这样，在 TPM 验证计算机状态之前则无法访问密钥。
  -  **启用代码完整性**：代码完整性是一种功能，可用于在每次将驱动程序或系统文件载入内存时，验证它们的完整性。 代码完整性检测是否正在将未签名的驱动程序或系统文件加载到内核中。 它还检测系统文件是否已被具有管理员权限的用户帐户运行的恶意软件进行了修改。
  - **启用安全启动**：启用安全启动后，系统会被强制启动到出厂信任状态。 此外，启用安全启动后，用于启动设备的核心组件必须具有制造设备的组织所信任的正确加密签名。 UEFI 固件会在允许设备启动前确认这一点。 如果有任何文件被篡改或破坏了签名，系统将不会启动。
  - **启用开机初期启动的反恶意软件**：开机初期启动的反恶意软件 (ELAM) 在计算机启动时和第三方驱动器初始化之前，对网络中的计算机提供保护。

  有关 HAS 服务工作方式的信息，请参阅[运行状况证明 CSP](https://msdn.microsoft.com/library/dn934876.aspx)。

### <a name="device-property-settings"></a>设备属性设置
- **所需的最低操作系统**：在 Windows 8.1 和 Windows 10 上受支持。

  在此处指定 major.minor.build 编号。 版本号必须与 **winver** 命令返回的版本一致。

  如果设备的操作系统版本比指定的版本低，它将被报告为不兼容。 将显示一个链接，链接中包含有关如何升级的信息。 用户可以选择升级其设备，然后他们可以访问公司资源。

- **允许的最高操作系统版本**：在 Windows 8.1 和 Windows 10 上受支持。

  当设备使用的操作系统版本高于规则中指定的版本时，将阻止访问公司资源，并要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则该设备将不能用于访问公司资源。

若要查找要用于**所需的最低操作系统**和**允许的最高操作系统版本**设置的操作系统版本，请从命令提示符处运行 **winver** 命令。 **Winver** 命令返回报告的操作系统版本。

- Windows 8.1 PC 返回版本 **6.3**。 对于 Windows，如果操作系统版本规则设置为 Windows 8.1，则该设备将报告为不符合要求，即使该设备具有 Windows 8.1 也是如此。

- 对运行 Windows 10 的电脑，版本应设置为 **10.0** + **winver** 命令返回的 OS 内部版本号。 例如，它可能类似于 10.0.10586。
> ![“关于Windows”对话框中突出显示的操作系统内部版本号](./media/ca_win10-os-version.png)
