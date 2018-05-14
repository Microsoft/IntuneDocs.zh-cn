---
title: 在 Microsoft Intune 中对 Windows 10 添加 Endpoint Protection - Azure | Microsoft Docs
description: 在 Windows 10 设备上，使用或配置 Endpoint Protection 设置，以在 Microsoft Intune 中对本地设备启用 Windows Defender 功能，包括应用程序防护、防火墙、SmartScreen、加密和 BitLocker、攻击防护、应用程序控制、安全中心和安全性。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 22eceb7792aee714fb728d64d8bec2ae8db4167c
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Intune 中适用于 Windows 10 及更高版本的 Endpoint Protection 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

可通过 Endpoint Protection 配置文件控制 Windows 10 设备上的安全功能（如 BitLocker 和 Windows Defender）。

查看本文信息，了解如何创建 Endpoint Protection 配置文件。

> [!NOTE]
> Windows 10 家庭版和专业版不支持这些设置。

## <a name="windows-defender-application-guard"></a>Windows Defender 应用程序防护

使用 Microsoft Edge 时，Windows Defender 应用程序防护可保护环境免受组织不信任的站点的影响。 当用户访问隔离网络边界中未列出的站点时，这些站点将在 Hyper-V 的虚拟浏览会话中打开。 受信任的站点由可以在设备配置中配置的网络边界定义。 

应用程序防护仅适用于 Windows 10（64 位）设备。 使用此配置文件将安装用于激活应用程序防护的 Win32 组件。

- 应用程序防护：在 Hyper-V 虚拟化浏览容器中打开未经批准的站点。
- 剪贴板行为：选择允许在本地电脑和应用程序防护虚拟浏览器之间执行的复制/粘贴操作。
- 企业网站上的外部内容：阻止加载来自未受批准的网站的内容。
- ：允许 PDF、XPS、本地和/或网络打印机打印虚拟浏览器中的内容。
- 收集日志：收集应用程序防护浏览会话内发生的事件的日志。
- 保留用户生成的浏览器数据：保存应用程序防护虚拟浏览会话期间创建的用户数据（如密码、收藏和 cookie）。
- 图形加速：在应用程序防护虚拟浏览会话中工作时，提升图形密集型网站的加载速度。 通过启用对虚拟图形处理单元的访问提升网站的加载速度。
- 将文件下载到主机文件系统：允许用户从虚拟化浏览器将文件下载到主机操作系统。

## <a name="windows-defender-firewall"></a>Windows Defender 防火墙

### <a name="global-settings"></a>全局设置

以下设置适用于所有网络类型。

- 文件传输协议：阻止有状态 FTP。
- 删除前的安全关联空闲时间：如果在 n 秒内未检测到任何网络流量，则删除安全关联。
- 预共享密钥编码：使用 UTF-8 对预共享密钥进行编码。
- IPsec 免除：配置要从 IPsec 中免除的特定流量，包括邻居发现 IPv6 ICMP 类型代码、ICMP、路由器发现 IPv6 ICMP 类型代码以及 IPv4 和 IPv6 DHCP 网络流量。
- 证书吊销列表验证：设置一个值以指示如何强制执行证书吊销列表验证，包括“禁用 CRL 验证”、“仅在遇到已吊销的证书时，CRL 验证才失败”和“如果遇到任何错误，则 CRL 验证失败”。
- 适时地按每个密钥模块匹配身份验证集：将密钥模块设置为如果它们不支持身份验证集中的所有身份验证套件，则忽略整个身份验证集。
- 数据包排队：指定如何针对 IPsec 隧道网关方案为加密接收和明文转发启用接收端上的软件缩放。 此设置可确保数据包顺序得到保留。

### <a name="network-settings"></a>网络设置

以下设置适用于特定网络类型，包括“域(工作区)网络”、“专用(可检测)网络”和“公用(不可检测)网络”。

#### <a name="general-settings"></a>常规设置

- Windows Defender 防火墙：启用此设置可阻止网络流量。
- 隐藏模式：阻止防火墙在隐藏模式下运行。 阻止隐藏模式还可以阻止“IPsec 安全数据包免除”。
- 防护：启用此设置和防火墙设置后将阻止所有传入流量。
- 针对多播广播的单播响应：阻止针对多播广播的单播响应。 通常，你不希望接收针对多播或广播消息的单播响应。 这些响应可能表示拒绝服务 (DOS) 攻击，或试图探测已知实时计算机的攻击者。
- 入站通知：当阻止应用程序侦听某个端口时，阻止向用户显示通知。
- 入站连接的默认操作：阻止防火墙对入站连接执行的默认操作。

#### <a name="rule-merging"></a>规则合并

- 来自本地存储的已授权应用程序 Windows Defender 防火墙规则：应用本地存储中会被识别和被强制执行的已授权防火墙规则。
- 来自本地存储的全局端口 Windows Defender 防火墙规则：应用本地存储中会被识别和被强制执行的全局端口防火墙规则。
- 来自本地存储的 Windows Defender 防火墙规则：应用本地存储中会被识别和被强制执行的全局防火墙规则。
- 来自本地存储的 IPsec 规则：应用本地存储中的连接安全规则，而不考虑架构或连接安全规则版本。

## <a name="windows-defender-smartscreen-settings"></a>Windows Defender SmartScreen 设置

- 用于应用和文件的 SmartScreen：支持 Windows SmartScreen 用于执行文件和运行应用。
- 未经验证的文件执行：阻止最终用户运行尚未经 Windows SmartScreen 验证的文件。

## <a name="windows-encryption"></a>Windows 加密

### <a name="windows-settings"></a>Windows 设置

以下两个设置适用于 Windows 10 的所有版本：

- 加密设备：如果启用，将提示用户启用设备加密。 此外，系统还会请求用户确认尚未启用来自另一个提供程序的加密。 如果 Windows 加密开启时另一种加密方法处于活动状态，设备可能会变得不稳定。
- 加密存储卡：启用此设置以对设备使用的任何可移动存储卡进行加密。


### <a name="bitlocker-base-settings"></a>BitLocker 基本设置

基本设置是适合所有数据驱动器类型的通用 BitLocker 设置。 BitLocker 组策略设置用于管理最终用户可以在所有数据驱动器类型中修改哪些驱动器加密任务或配置选项。

- 针对其他磁盘加密的警告：在最终用户的计算机上禁用针对其他磁盘加密的警告提示。
- ：启用此设置以配置操作系统、数据和可移动驱动器的加密算法。
  - 操作系统驱动器的加密：选择操作系统驱动器的加密方法。 建议使用 XTS-AES 算法。
  - 固定数据驱动器的加密：选择固定（内置）数据驱动器的加密方法。 建议使用 XTS-AES 算法。
  - 可移动数据驱动器的加密：选择可移动数据驱动器的加密方法。 如果在不运行 Windows 10 的设备上使用可移动驱动器，建议使用 AES-CBC 算法。

### <a name="bitlocker-os-drive-settings"></a>BitLocker OS 驱动器设置

以下设置仅适用于操作系统数据驱动器。

- 启动时的其他身份验证：配置计算机启动时的身份验证要求，包括使用受信任的平台模块 (TPM)。
  - **包含非兼容 TPM 芯片的 BitLocker**
  - 兼容的 TPM 启动：选择是允许、不允许还是要求使用 TPM 芯片。
  - 兼容的 TPM 启动 PIN：选择是允许、不允许还是要求使用带有 TPM 芯片的启动 PIN。
  - 兼容的 TPM 启动密钥：选择是允许、不允许还是要求使用带有 TPM 芯片的启动密钥。
  - 兼容的 TPM 启动密钥和 PIN：选择是允许、不允许还是要求使用带有 TPM 芯片的启动密钥和 PIN。
- 最小 PIN 长度：启用此设置以配置 TPM 启动 PIN 的最小长度。
  - 最少字符数：输入启动 PIN 所需的字符数（介于 4-20）。
- OS 驱动器恢复：启用此设置以控制在所需启动信息不可用时如何恢复受 BitLocker 保护的操作系统驱动器。
  - 基于证书的数据恢复代理：如果希望数据恢复代理能够用于受 BitLocker 保护的操作系统驱动器，则启用此设置。
  - 用户创建恢复密码：选择是允许、要求还是不允许用户生成 48 位数的恢复密码。
  - 用户创建恢复密钥：选择是允许、要求还是不允许用户生成 256 位数的恢复密钥。
  - BitLocker 安装向导中的恢复选项：启用此设置以防止用户在打开 BitLocker 时看到或更改恢复选项。
  - 将 BitLocker 恢复信息保存到 AD DS：启用在 Active Directory 中存储 BitLocker 恢复信息。
  - 存储到 AD DS 的 BitLocker 恢复信息：配置 BitLocker 恢复信息的哪些部分存储在 Active Directory 中。 选择：
    - “备份恢复密码和密钥包”
    - “仅备份恢复密码”
  - 在启用 BitLocker 前将恢复信息存储在 AD DS 中：启用此设置以阻止用户启用 BitLocker，除非设备已加入域，并且 BitLocker 恢复信息已成功存储在 Active Directory 中。
- 预启动恢复消息和 URL：启用此设置以配置预启动密钥恢复屏幕上显示的消息和 URL。
  - 预启动恢复消息：配置如何向用户显示预启动恢复消息。 选择：
    - “使用默认恢复消息和 URL”
    - “使用空的恢复消息和 URL”
    - “使用自定义恢复消息”
    - “使用自定义恢复 URL”

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 固定数据驱动器设置

- 对不受 BitLocker 保护的固定数据驱动器的写入访问权限：如果启用，则必须在所有固定或内置数据驱动器上启用 BitLocker 保护，才能写入它们。
- 固定驱动器恢复：启用此设置以控制在所需启动信息不可用时如何恢复受 BitLocker 保护的固定驱动器。
  - 数据恢复代理：如果希望数据恢复代理可用于受 BitLocker 保护的固定驱动器，则启用此设置。
  - 用户创建恢复密码：配置是允许、要求还是不允许用户生成 48 位数的恢复密码。  
  - 用户创建恢复密钥：配置是允许、要求还是不允许用户生成 256 位数的恢复密钥。
  - BitLocker 安装向导中的恢复选项：启用此设置以防止用户在打开 BitLocker 时看到或更改恢复选项。
  - 将 BitLocker 恢复信息保存到 AD DS：启用在 Active Directory 中存储 BitLocker 恢复信息。
  - 存储到 AD DS 的 BitLocker 恢复信息：配置 BitLocker 恢复信息的哪些部分存储在 Active Directory 中。 选择：
    - “备份恢复密码和密钥包”
    - “仅备份恢复密码”
  - 在启用 BitLocker 前将恢复信息存储在 AD DS 中：启用此设置以阻止用户启用 BitLocker，除非设备已加入域，并且 BitLocker 恢复信息已成功存储在 Active Directory 中。

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 可移动数据驱动器设置

- 对不受 BitLocker 保护的可移动数据驱动器的写入访问权限：指定可移动存储驱动器是否需要 BitLocker 加密。
  - 对其他组织中配置的设备的写入访问权限：指定是否可以写入属于其他组织的可移动数据驱动器。

## <a name="windows-defender-exploit-guard"></a>Windows Defender 攻击防护

使用 [Windows Defender 攻击防护](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard)管理和减少员工所用应用的受攻击面。

### <a name="attack-surface-reduction"></a>攻击面减少

- **标记从 Windows 本地安全机构子系统窃取的凭据**

帮助[防止操作和应用](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard)（通常被寻找漏洞的恶意软件所利用）感染计算机。

#### <a name="rules-to-prevent-office-macro-threats"></a>防止 Office 宏威胁的规则

阻止 Office 应用执行下列操作：

- **Office 应用插入其他进程（无异常）**
- **Office 应用/宏创建可执行内容**
- **Office 应用启动子进程**
- **Win32 从 Office 宏代码导入**

#### <a name="rules-to-prevent-script-threats"></a>防止脚本威胁的规则

阻止以下内容以帮助防止脚本威胁：

- **不确定的 js/vbs/ps/宏代码**
- **js/vbs 执行从 Internet 下载的有效负载（无异常）**
- **来自 PSExec 和 WMI 命令的进程创建**
- **从 USB 运行的不受信任和未签名的进程**
- **不符合普及程度、年龄或信任列表条件的可执行文件**

#### <a name="rules-to-prevent-email-threats"></a>防止电子邮件威胁的规则

阻止以下行为以帮助防止电子邮件威胁：

- **执行从电子邮件（webmail/邮件客户端）中删除的可执行内容（exe、dll、ps、js、vbs 等）（无异常）**

#### <a name="rules-to-protect-against-ransomware"></a>预防勒索软件的规则
- **高级勒索软件防护**

> [!TIP]
> 有关这些规则的详细信息，请参阅 [（利用 Windows Defender 攻击防护缩小攻击面）](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard)。

#### <a name="attack-surface-reduction-exceptions"></a>攻击面减少例外情况

- 从攻击面减少规则中排除的文件和文件夹：导入/添加要从已配置规则中排除的位置的列表。

### <a name="controlled-folder-access"></a>受控文件夹访问权限

帮助防止重要数据受到恶意应用和威胁（如勒索软件）的攻击。

- 文件夹保护：防止文件和文件夹被恶意应用意外更改。 可以导入“有权访问受保护文件夹的应用的列表”或手动添加应用。 还可以通过上传来添加“需保护的其他文件夹的列表”或手动添加文件夹。

### <a name="network-filtering"></a>网络筛选

阻止从任何应用到低信誉 IP/域的出站连接。

### <a name="exploit-protection"></a>Exploit Protection

通过上传允许配置内存、控制流和策略限制的 XML 文件，阻止用户编辑攻击防护界面。 XML 文件中的设置可用于阻止应用程序遭受攻击。

若要启用 Exploit Protection，请创建表示所选系统和应用程序缓解措施设置的 XML 文件。 可使用以下两种方法执行此操作：

 1. PowerShell：使用一个或多个 Get-ProcessMitigation、Set-ProcessMitigation 和 ConvertTo-ProcessMitigationPolicy PowerShell cmdlet。 这些 cmdlet 配置缓解设置并导出它们的 XML 表示形式。

 2. Windows Defender 安全中心 UI：在 Windows Defender 安全中心，单击“应用和浏览器”控件，然后向下滚动到所看到的屏幕底部，找到 Exploit Protection。 首先，使用“系统”设置和“程序”设置选项卡来配置缓解措施设置。 然后，找到屏幕底部的“导出”设置链接，导出其 XML 表示形式。

## <a name="windows-defender-application-control"></a>Windows Defender 应用程序控制

使用“应用程序控制代码完整性策略”选择需要 Windows Defender 应用程序控制来审核或其信任运行的其他应用。 自动信任 Windows 组件和来自 Windows 应用商店的所有应用运行。

在“仅审核”模式下运行时，应用程序不受阻止。 “仅审核”模式在本地客户端日志中记录所有事件。

启用“应用程序控制”后，只能通过将模式从“强制实施”更改为“仅审核”来禁用。 如果将模式从“强制实施”更改为“不配置”，则会继续在分配的设备上强制执行“应用程序控制”。

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard
Windows Defender Credential Guard 可防止凭据盗窃攻击。 它可隔离密码，以便仅特权系统软件才可以进行访问。

Credential Guard 设置包括：

- 禁用：远程关闭 Credential Guard（如果之前已使用“无 UEFI 锁启用”选项启用）。
- 使用 UEFI 锁启用：可确保 Credential Guard 不能使用注册表项或使用组策略远程禁用。

    > [!NOTE]
    > 如果使用此设置，并且稍后想要禁用 Credential Guard，必须将组策略设置为“禁用”。 并且，从每台计算机以物理方式清除 UEFI 配置信息。 只要 UEFI 配置仍然存在，Credential Guard 就会保持启用状态。

- 无 UEFI 锁启用：允许使用组策略远程禁用 Credential Guard。 使用此设置的设备必须运行 Windows 10 1511 及更新的版本。

启用 Credential Guard 时，还会启用以下必需的功能：

- 基于虚拟化的安全性 (VBS)：在下次重新启动时打开。 基于虚拟化的安全性使用 Windows 虚拟机监控程序提供对安全服务的支持。
- 通过目录内存访问的安全启动：通过“安全启动”和直接内存访问 (DMA) 保护启用 VBS。 DMA 保护需要硬盘支持并且将仅在正确配置的设备上启用。

## <a name="windows-defender-security-center"></a>Windows Defender 安全中心

Windows Defender 安全中心应用作为独立应用或每个单项功能中的进程运行。 它通过“操作中心”显示通知。 它可以用作收集器或用作可查看状态和为每个功能执行某项配置的单独位置。 有关详细信息，请参阅 [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) 文档。

#### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender 安全中心应用和通知

阻止最终用户访问 Windows Defender 安全中心应用的各个区域。 隐藏某个部分还将阻止相关通知。

- **病毒和威胁防护**
- **设备性能和运行状况**
- **防火墙和网络保护**
- **应用和浏览器控制**
- **产品系列选项**
- 应用的显示区域中的通知：选择要向最终用户显示的通知。 非关键通知包括 Windows Defender 防病毒活动摘要（包括扫描完成时的通知）。 所有其他通知被视为是关键通知。

#### <a name="it-contact-information"></a>IT 联系信息

提供要在 Windows Defender 安全中心应用和应用通知中显示的 IT 联系信息。 可以选择“在应用和通知中显示”、“仅在应用中显示”、“仅在通知中显示”或“不显示”。 必须输入“IT 组织名称”以及至少定义以下一项联系人选项：

- **IT 部门的电话号码或 Skype ID**
- **IT 部门的电子邮件地址**
- **IT 支持网站 URL**

## <a name="local-device-security-options"></a>本地设备安全选项

使用这些选项可配置 Windows 10 设备上的本地安全设置。

### <a name="accounts"></a>帐户

- 添加新的 Microsoft 帐户：阻止用户在此计算机上添加新 Microsoft 帐户。
- 不使用密码远程登录：启用不受密码保护的本地帐户从物理设备以外的位置登录。

#### <a name="admin"></a>管理员

- 本地管理员帐户：确定本地管理员帐户是启用还是禁用。
- 重命名管理员帐户：定义与管理员帐户的安全标识符 (SID) 关联的其他帐户名称。

#### <a name="guest"></a>Guest

- 来宾帐户：确定是启用还是禁用来宾帐户。
- 重命名来宾帐户：定义与来宾帐户的安全标识符 (SID) 关联的其他帐户名称。

### <a name="devices"></a>设备

- 免登录移除设备：防止免登录移除便携式计算机。
- 为共享打印机安装打印机驱动程序：仅限管理员才能在连接到共享打印机的过程中安装打印机驱动程序。
- 限制对本地活动用户的 CD-ROM 访问：启用此设置可以仅允许登录用户以交互方式访问 CD-ROM 媒体
- 格式化和弹出可移动媒体：定义可以格式化和弹出可移动 NTFS 媒体的用户：
  - 未配置
  - **管理员和超级用户**
  - **管理员和交互式用户**

### <a name="interactive-logon"></a>交互式登录

- 激活屏幕保护程序前，锁定屏幕保持不活动状态的分钟数：定义在屏幕保护程序运行之前，交互式桌面的登录屏幕保持不活动状态的最长分钟数。
- 需要使用 CTRL+ALT+DEL 登录：在用户登录之前需要同时按 CTRL+ALT+DEL。
- 智能卡移除行为：确定从智能卡读卡器中移除登录用户的智能卡时发生的情况。
[LocalPoliciesSecurity 选项](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior)提供更多详细信息。

#### <a name="display"></a>显示

- 锁定屏幕上的用户信息：配置会话锁定时显示的用户信息。 如果未配置，则显示用户显示名称、域和用户名。
  - **仅限用户显示名称**
  - **不显示用户信息**
  - 未配置：用户显示名称、域和用户名
- 隐藏上次登录的用户：不显示最后一个登录此设备的用户的用户名。
- 在登录时隐藏用户名：输入凭据后，在显示设备桌面之前，不显示登录该设备的用户的用户名。
- 登录消息标题：设置试图登录的用户的消息标题。
- 登录消息文本：设置试图登录的用户的消息文本。

### <a name="network-access-and-security"></a>网络访问和安全性

- 匿名访问命名管道和共享：限制对共享和命名管道设置的匿名访问。 适用于可以匿名访问的设置。
- SAM 帐户匿名枚举：允许匿名用户枚举 SAM 帐户。 Windows 允许匿名用户枚举域帐户和网络共享名称。
- SAM 帐户和共享匿名枚举：可以阻止 SAM 帐户和共享的匿名枚举。 Windows 允许匿名用户枚举域帐户和网络共享的名称。
- 密码更改时存储的 LAN Manager 哈希值：在下次密码更改时，选择是否存储新密码的 LAN Manager (LM) 哈希值。 默认不存储该值。
- PKU2U 身份验证请求：阻止该设备的 PKU2U 身份验证请求以使用在线身份。
- 将远程 RPC 连接限制为 SAM：编辑默认的安全描述符定义语言字符串以允许或拒绝用户和组对 SAM 进行远程调用。
- **安全描述符**

### <a name="recovery-console-and-shutdown"></a>恢复控制台和关闭

- 在关闭时清除虚拟内存页面文件：在设备关机时清除虚拟内存页面文件。
- 免登录关机：阻止从 Windows 登录屏幕关闭计算机的选项。 在这种情况下，用户必须能够成功登录到计算机，然后才可以执行系统关闭。

### <a name="user-account-control"></a>用户帐户控制

- 无安全位置的 UIA 完整性：启用来自文件系统中不安全位置的应用，以使用 UIAccess 完整性级别运行。
- 将文件和注册表写入错误虚拟化到每用户位置：确定是否将应用写入错误重定向到定义的注册表和文件系统位置。 否则会导致应用失败。
- 只提升签名并验证的可执行文件：在允许给定的可执行文件运行之前，强制对其执行 PKI 证书路径验证。

#### <a name="uia-elevation-prompt-behavior-settings"></a>UIA 提升提示行为设置

- 管理员的提升提示：在管理员批准模式下定义管理员的提升提示行为：
  - 不提示，直接提升
  - 在安全桌面上提示凭据
  - 在安全桌面上同意提示
  - 提示凭据
  - 同意提示
  - 未配置：非 Windows 二进制文件的同意提示
- 标准用户的提升提示：定义标准用户的提升提示行为：
  - 自动拒绝提升请求
  - 在安全桌面上提示凭据
  - 未配置：提示提供凭据
- 将提升提示路由到用户的交互式桌面：启用所有提升请求以转到交互式用户的桌面，而不是安全桌面。 使用针对管理员和标准用户的提示行为策略设置。
- 应用安装的提升提示：需要提升权限的应用安装会提示输入管理员凭据。
- 无安全桌面的 UIA 提升权限提示：允许 UIAccess 应用在不使用安全桌面的情况下提示提升。

#### <a name="admin-approval-mode-settings"></a>管理员批准模式设置

- 内置管理员的管理员批准模式：定义内置管理员帐户是使用管理员批准模式还是以完全管理员权限运行所有应用。
- 以管理员批准模式运行所有管理员：定义是否启用管理员批准模式和所有 UAC 策略设置。

### <a name="microsoft-network-client"></a>Microsoft 网络客户端

- 对通信进行数字签名(如果服务器允许)：确定 SMB 客户端是否尝试协商 SMB 数据包签名。 启用（默认设置）时，Microsoft 网络客户端请求服务器在设置会话时执行 SMB 数据包签名。 如果在服务器上启用了数据包签名，则会协商数据包签名。 如果禁用此策略，则 SMB 客户端绝不会协商 SMB 数据包签名。
- 将未加密的密码发送到第三方 SMB 服务器：启用后，允许服务器消息块 (SMB) 重定向程序将明文密码发送给在身份验证期间不支持密码加密的非 Microsoft SMB 服务器。

### <a name="microsoft-network-server"></a>Microsoft 网络服务器

- 对通信进行数字签名(如果客户端允许)：确定 SMB 服务器是否与请求它的客户端协商 SMB 数据包签名。 启用后，Microsoft 网络服务器会根据客户端的请求协商 SMB 数据包签名。 也就是说，如果在客户端上启用了数据包签名，则会协商数据包签名。 禁用（默认设置）后，SMB 客户端绝不会协商 SMB 数据包签名。
- 对通信进行数字签名(始终)：确定 SMB 服务器组件是否需要数据包签名。 启用后，Microsoft 网络服务器不会与 Microsoft 网络客户端通信，除非该客户端允许执行 SMB 数据包签名。 禁用（默认设置）后，客户端和服务器之间会协商 SMB 数据包签名。

## <a name="next-steps"></a>后续步骤

要向组分配此配置文件，请参阅[如何分配设备配置文件](device-profile-assign.md)。
