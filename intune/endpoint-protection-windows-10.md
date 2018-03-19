---
title: "适用于 Windows 10 的 Microsoft Intune Endpoint Protection 设置"
titlesuffix: 
description: "了解哪些 Intune 设置可用于控制 Windows 10 设备上的 Endpoint Protection 设置（例如 BitLocker）。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02a32f678b40b2b40535984e17b41e0a864d8fdf
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="create-endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>在 Microsoft Intune 中创建 适用于 Windows 10 及更高版本的 Endpoint Protection 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可通过 Endpoint Protection 配置文件控制 Windows 10 设备上的安全功能（如 BitLocker 和 Windows Defender）。

查看本文信息，了解如何创建 Endpoint Protection 配置文件。

> [!Note]
> Windows 10 家庭版和专业版不支持这些设置。

## <a name="create-an-endpoint-protection-profile"></a>创建 Endpoint Protection 配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“管理”部分下的“设备配置”边栏选项卡上，选择“配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入设备功能配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择“Windows 10 及更高版本”。
6. 在“配置文件类型”下拉列表中，选择“Endpoint Protection”。
7. 配置所需设置。 查看本文中的信息，了解每项设置的作用。 完成后，请选择“确定”。
8. 返回到“创建配置文件”边栏选项卡，然后选择“创建”。

系统将创建配置文件并在“配置文件列表”边栏选项卡上显示出来。

## <a name="windows-defender-application-guard"></a>Windows Defender 应用程序防护

应用程序防护仅适用于 Windows 10（64 位）设备。 使用此配置文件将安装用于激活应用程序防护的 Win32 组件。

- **应用程序保护** - 在 Hyper-V 虚拟化浏览容器中打开未经批准的站点。
- **剪贴板行为** - 选择允许在本地电脑和应用程序防护虚拟浏览器之间执行的复制/粘贴操作。
- **企业网站上的外部内容** - 阻止加载来自未受批准的网站的内容。
- **从虚拟浏览器打印** - 允许 PDF、XPS、本地和/或网络打印机打印虚拟浏览器中的内容。
- **收集日志** - 收集应用程序防护浏览会话内发生的事件的日志。
- **保留用户生成的浏览器数据** - 允许保存应用程序防护虚拟浏览会话期间创建的用户数据（如密码、收藏和 cookie）。
- **图形加速** - 在应用程序防护虚拟浏览会话中工作时，可通过启用对虚拟图形处理器访问，提升图形密集型网站的加载速度。


## <a name="windows-defender-firewall"></a>Windows Defender 防火墙

### <a name="global-settings"></a>全局设置

以下设置适用于所有网络类型。

- **文件传输协议** - 阻止有状态 FTP。
- **删除前的安全关联空闲时间** - 如果在 n 秒内未检测到任何网络流量，则删除安全关联。
- **预共享密钥编码** - 使用 UTF-8 对预共享密钥进行编码。
- **IPsec 免除** - 配置要从 IPsec 中免除的特定流量，包括邻居发现 IPv6 ICMP 类型代码、ICMP、路由器发现 IPv6 ICMP 类型代码以及 IPv4 和 IPv6 DHCP 网络流量。
- **证书吊销列表验证** - 设置一个值以指示如何强制执行证书吊销列表验证，包括“禁用 CRL 验证”、“仅在遇到已吊销的证书时，CRL 验证才失败”和“如果遇到任何错误，则 CRL 验证失败”。
- **适时地按每个密钥模块匹配身份验证集** - 将密钥模块设置为如果它们不支持身份验证集中的所有身份验证套件，则忽略整个身份验证集。
- **数据包排队** - 指定如何针对 IPsec 隧道网关方案为加密接收和明文转发启用接收端上的软件缩放。 这将确保数据包顺序得到保留。

### <a name="network-settings"></a>网络设置

以下设置适用于特定网络类型，包括“域(工作区)网络”、“专用(可检测)网络”和“公用(不可检测)网络”。

#### <a name="general-settings"></a>常规设置

- **Windows Defender 防火墙** - 启用此设置可阻止网络流量。
- **隐藏模式** - 阻止防火墙在隐藏模式下运行。 执行此阻止操作还可以阻止“IPsec 安全数据包免除”。
- **防护** - 启用此设置和防火墙设置后将阻止所有传入流量。
- **针对多播广播的单播响应** - 阻止针对多播广播的单播响应。 通常情况下，你无需接收针对多播或广播消息的单播响应，因为此类响应可能指示拒绝服务攻击或拒绝尝试探测已知实时计算机的攻击者。
- **入站通知** - 当阻止应用程序侦听某个端口时，阻止向用户显示通知。
- **入站连接的默认操作** - 阻止防火墙对入站连接执行的默认操作。

#### <a name="rule-merging"></a>规则合并

- **来自本地存储的已授权应用程序 Windows Defender 防火墙规则** - 应用本地存储中会被识别和被强制执行的已授权防火墙规则。
- **来自本地存储的全局端口 Windows Defender 防火墙规则** - 应用本地存储中会被识别和被强制执行的全局端口防火墙规则。
- **来自本地存储的 Windows Defender 防火墙规则** - 应用本地存储中会被识别和被强制执行的全局防火墙规则。
- **来自本地存储的 IPsec 规则** - 应用本地存储中的连接安全规则，而不考虑架构或连接安全规则版本。

## <a name="windows-defender-smartscreen-settings"></a>Windows Defender SmartScreen 设置

- **用于应用和文件的 SmartScreen** - 支持 Windows SmartScreen 用于执行文件和运行应用。
- **未经验证的文件执行** - 阻止最终用户运行尚未经 Windows SmartScreen 验证的文件。

## <a name="windows-encryption"></a>Windows 加密

### <a name="windows-settings"></a>Windows 设置

以下设置适用于Windows 10 的所有版本。

- **加密设备** - 如果启用，将提示用户启用设备加密。 此外，系统还会请求用户确认尚未启用来自另一个提供程序的加密。 如果 Windows 加密开启时另一种加密方法处于活动状态，设备可能会变得不稳定。
- **加密存储卡** - 启用此设置以对设备使用的任何可移动存储卡进行加密。


### <a name="bitlocker-base-settings"></a>BitLocker 基本设置

基本设置是适合所有数据驱动器类型的通用 BitLocker 设置。 BitLocker 组策略设置用于管理最终用户可以在所有数据驱动器类型中修改哪些驱动器加密任务或配置选项。

- **针对其他磁盘加密的警告** - 在最终用户的计算机上禁用针对其他磁盘加密的警告提示。
- “配置加密方法”- 启用此设置以配置操作系统、数据和可移动驱动器的加密算法。
    - “操作系统驱动器的加密”- 选择操作系统驱动器的加密方法。 建议使用 XTS-AES 算法。
    - “固定数据驱动器的加密”- 选择固定（内置）数据驱动器的加密方法。 建议使用 XTS-AES 算法。
    - “可移动数据驱动器的加密”- 选择可移动数据驱动器的加密方法。 如果在不运行 Windows 10 的设备上使用可移动驱动器，建议使用 AES-CBC 算法。

### <a name="bitlocker-os-drive-settings"></a>BitLocker OS 驱动器设置

以下设置仅适用于操作系统数据驱动器。

- **启动时的其他身份验证** - 配置计算机启动时的身份验证要求，包括使用受信任的平台模块 (TPM)。
    - **包含非兼容 TPM 芯片的 BitLocker**
    - **兼容的 TPM 启动** - 配置是允许、不允许还是必须要求 TPM 芯片。
    - **兼容的 TPM 启动 PIN** - 配置是允许、不允许还是必须要求使用带 TPM 芯片的启动 PIN。
    - **兼容的 TPM 启动密钥** - 配置是允许、不允许还是必须要求使用带 TPM 芯片的启动密钥。
    - **兼容的 TPM 启动密钥和 PIN** - 配置是允许、不允许还是必须要求使用带 TPM 芯片的启动密钥和 PIN。
- “最小 PIN 长度”- 启用此设置以配置 TPM 启动 PIN 的最小长度。
    - “最少字符数”- 输入启动 PIN 所需的字符数（介于 **4**-**20**）。
- **OS 驱动器恢复** - 启用此设置以控制在所需启动信息不可用时如何恢复受 BitLocker 保护的操作系统驱动器。
    - “基于证书的数据恢复代理”- 如果希望数据恢复代理能够用于受 BitLocker 保护的操作系统驱动器，则启用此设置。
    - “用户创建恢复密码”- 配置是允许、不允许还是要求用户生成 48 位数的恢复密码。
    - “用户创建恢复密钥”- 配置是允许、不允许还是要求用户生成 256 位数的恢复密钥。
    - **BitLocker 安装向导中的恢复选项** - 启用此设置以防止用户在打开 BitLocker 时看到或更改恢复选项。
    - “将 BitLocker 恢复信息保存到 AD DS”- 启用在 Active Directory 中存储 BitLocker 恢复信息。
    - **存储到 AD DS 的 BitLocker 恢复信息** - 配置 BitLocker 恢复信息的哪些部分存储在 Active Directory 中。 选择：
        - “备份恢复密码和密钥包”
        - “仅备份恢复密码”
    - **在启用 BitLocker 前将恢复信息存储于 AD DS** - 启用此设置以阻止用户启用 BitLocker，除非设备已加入域，并且 BitLocker 恢复信息已成功存储在 Active Directory 中。
- **预启动恢复消息和 URL** - 启用此设置以配置预启动密钥恢复屏幕上显示的消息和 URL。
    - “预启动恢复消息”- 配置如何向用户显示预启动恢复消息。 选择：
        - “使用默认恢复消息和 URL”
        - “使用空的恢复消息和 URL”
        - “使用自定义恢复消息”
        - “使用自定义恢复 URL”


### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 固定数据驱动器设置

- **对不受 BitLocker 保护的固定数据驱动器的写入访问权限** - 如果启用，则必须在所有固定或内置数据驱动器上启用 BitLocker 保护，才能写入它们。
- **启用固定驱动器恢复** - 启用此设置以控制在所需启动信息不可用时如何恢复受 BitLocker 保护的固定驱动器。
    - “据恢复代理”- 如果希望数据恢复代理可用于受 BitLocker 保护的固定驱动器，则启用此设置。
    - “用户创建恢复密码”- 配置是允许、不允许还是要求用户生成 48 位数的恢复密码。  
    - “用户创建恢复密钥”- 配置是允许、不允许还是要求用户生成 256 位数的恢复密钥。
    - **BitLocker 安装向导中的恢复选项** - 启用此设置以防止用户在打开 BitLocker 时看到或更改恢复选项。
    - “将 BitLocker 恢复信息保存到 AD DS”- 启用在 Active Directory 中存储 BitLocker 恢复信息。
    - **存储到 AD DS 的 BitLocker 恢复信息** - 配置 BitLocker 恢复信息的哪些部分存储在 Active Directory 中。 选择：
        - “备份恢复密码和密钥包”
        - “仅备份恢复密码”
    - **在启用 BitLocker 前将恢复信息存储于 AD DS** - 启用此设置以阻止用户启用 BitLocker，除非设备已加入域，并且 BitLocker 恢复信息已成功存储在 Active Directory 中。

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 可移动数据驱动器设置

- **对不受 BitLocker 保护的可移动数据驱动器的写入访问权限** - 指定可移动存储驱动器是否需要 BitLocker 加密。
  - **对其他组织中配置的设备的写入访问权限** - 指定是否可以写入属于其他组织的可移动数据驱动器。

## <a name="windows-defender-exploit-guard"></a>Windows Defender 攻击防护

使用 [Windows Defender 攻击防护](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard)管理和减少员工所用应用的受攻击面。

### <a name="attack-surface-reduction"></a>攻击面减少

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

#### <a name="rules-to-prevent-email-threats"></a>防止电子邮件威胁的规则

阻止以下行为以帮助防止电子邮件威胁：

- **执行从电子邮件（webmail/邮件客户端）中删除的可执行内容（exe、dll、ps、js、vbs 等）（无异常）**

#### <a name="attack-surface-reduction-exceptions"></a>攻击面减少例外情况

- **从攻击面减少规则中排除的文件和文件夹** - 导入/添加要从已配置规则中排除的位置的列表。

### <a name="controlled-folder-access"></a>受控文件夹访问权限

帮助防止重要数据受到恶意应用和威胁（如勒索软件）的攻击。

- **文件夹保护** - 防止文件和文件夹被恶意应用意外更改。 可以导入“有权访问受保护文件夹的应用的列表”或手动添加应用。 还可以通过上传来添加“需保护的其他文件夹的列表”或手动添加文件夹。

### <a name="network-filtering"></a>网络筛选

阻止从任何应用到低信誉 IP/域的出站连接。

### <a name="exploit-protection"></a>Exploit Protection

通过上传 XML 文件阻止用户编辑 Exploit Protection 界面，使用此文件可配置用于防止应用程序被不当利用的内存、控制流和策略限制。

若要启用 Exploit Protection，请创建表示所选系统和应用程序缓解措施设置的 XML 文件。 可使用以下两种方法执行此操作：

 1. PowerShell：使用一个或多个 Get-ProcessMitigation、Set-ProcessMitigation 和 ConvertTo-ProcessMitigationPolicy PowerShell cmdlet 来配置缓解设置并导出其 XML 表示形式。

 2. Windows Defender 安全中心 UI：在 Windows Defender 安全中心，单击“应用和浏览器”控件，然后向下滚动到所看到的屏幕底部，找到 Exploit Protection。 首先，使用“系统”设置和“程序”设置选项卡来配置缓解措施设置。 然后，找到屏幕底部的“导出”设置链接，导出其 XML 表示形式。

## <a name="windows-defender-application-control"></a>Windows Defender 应用程序控制

使用“应用程序控制代码完整性策略”选择需要 Windows Defender 应用程序控制来审核或其信任运行的其他应用。 自动信任 Windows 组件和来自 Windows 应用商店的所有应用运行。

在“仅审核”模式下运行时，应用程序不受阻止。 “仅审核”模式在本地客户端日志中记录所有事件。

启用“应用程序控制”后，只能通过将模式从“强制实施”更改为“仅审核”来禁用。 如果将模式从“强制实施”更改为“不配置”，则会继续在分配的设备上强制执行“应用程序控制”。

## <a name="windows-defender-security-center"></a>Windows Defender 安全中心

Windows Defender 安全中心作为独立应用或每个单项功能中的进程运行，并将通过“操作中心”显示通知。 它可以用作收集器或用作可查看状态和为每个功能执行某项配置的单独位置。 有关详细信息，请参阅 [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) 文档。

#### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender 安全中心应用和通知

阻止最终用户访问 Windows Defender 安全中心应用的各个区域。 隐藏某个部分还将阻止相关通知。

- **病毒和威胁防护**
- **设备性能和运行状况**
- **防火墙和网络保护**
- **应用和浏览器控制**
- **产品系列选项**
- **应用的显示区域中的通知** - 选择要向最终用户显示的通知。 非关键通知包括 Windows Defender 防病毒活动摘要（包括扫描完成时的通知）。 所有其他通知被视为是关键通知。

#### <a name="it-contact-information"></a>IT 联系信息

提供要在 Windows Defender 安全中心应用和应用通知中显示的 IT 联系信息。 可以选择“在应用和通知中显示”、“仅在应用中显示”、“仅在通知中显示”或“不显示”。 必须定义“IT 组织名称”以及至少定义以下一项联系人选项：

- **IT 部门的电话号码或 Skype ID**
- **IT 部门的电子邮件地址**
- **IT 支持网站 URL**

## <a name="next-steps"></a>后续步骤

如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。
