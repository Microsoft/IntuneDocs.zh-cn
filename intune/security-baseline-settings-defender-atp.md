---
title: 用于 Microsoft Defender 高级威胁防护的 Intune 安全基线设置
titleSuffix: Microsoft Intune
description: Intune 支持用于管理 Microsoft Defender 高级威胁防护的安全基线设置
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/17/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b4acb5c4e79ba6895849d28c4f44766132d4daf
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65733439"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Intune 的 Microsoft Defender 高级威胁防护基线设置

查看 Microsoft Intune 支持的 Microsoft Defender 高级威胁防护（以前称为 Windows Defender 高级威胁防护）基线设置。 本文中的默认值表示 Intune 的默认基线配置。 这些默认值表示 Intune 的推荐配置，可能与 Windows 默认值不匹配。

> [!NOTE]  
> WDATP 基线设置处于预览状态。 在预览状态下，可用设置的列表，以及此内容呈现这些设置的顺序可能与门户中提供的内容不匹配。 
>
> 当基线设置不处于预览状态后，此内容将更新以反映 Intune 支持的安全基线设置的当前列表。

## <a name="application-guard"></a>应用程序防护  
有关详细信息，请参阅 Windows 文档中的 [WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp)。  

使用 Microsoft Edge 时，Microsoft Defender 应用程序防护可保护环境免受组织不信任的站点的影响。 用户访问独立网络边界中未列出的站点时，这些站点将在 Hyper-V 虚拟浏览会话中打开。 受信任的站点由网络边界定义。  

- **应用程序防护** - *Settings/AllowWindowsDefenderApplicationGuard*  
  选择“是”可打开此功能，在 Hyper-V 虚拟化浏览容器中打开不受信任的站点。 设置为“未配置”时，可以在该设备上（而不是在虚拟化容器中）打开任何站点（受信任和不受信任）。  

  **默认值**：是
 
  - **企业站点上的外部内容** - *Settings/BlockNonEnterpriseContent*  
    选择“是”可阻止加载未经批准的网站中的内容。 设置为“未配置”时，可以在该设备上打开非企业站点。 
 
    **默认值**：是

  - **剪贴板行为** - *Settings/ClipboardSettings*  
    选择允许在本地电脑和应用程序防护虚拟浏览器之间执行的复制和粘贴操作。  选项包括：
    - *未配置*  
    - *阻止两者* - 无法在电脑和虚拟浏览器之间传输数据。  
    - *阻止主机到容器* - 无法将数据从电脑传输到虚拟浏览器中。
    - *阻止容器到主机* - 无法将数据从虚拟浏览器传输到主机电脑中。
    - *均不阻止* - 不阻止任何内容。  

    **默认值**：阻止两者  

- **Windows 网络隔离策略 - 企业网络域名**  
  有关详细信息，请参阅 Windows 文档中的 [Policy CSP - NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation)（策略 CSP - NetworkIsolation）。
  
  将企业资源的列表指定为应用程序防护将其视为企业站点的云中托管的域、IP 地址范围和网络边界。  

  **默认值**：securitycenter.windows.com

## <a name="application-reputation"></a>应用程序信誉  

有关详细信息，请参阅 Windows 文档 [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen)（策略 CSP - SmartScreen）。

- **阻止未经验证的文件**  
    阻止用户运行未经验证的文件。 设置为“未配置”时，员工可以忽略 SmartScreen 警告并运行恶意文件。 设置为“是”时，员工不可忽略 SmartScreen 警告并运行恶意文件。  
  
    **默认值**：是

- **要求对应用和文件使用 SmartScreen**  
  设置为“是”可启用适用于 Windows 的 SmartScreen。  

  **默认值**：是

## <a name="attach-surface-reduction"></a>攻击面减少  

- **Office 应用启动子进程类型**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 设置为“阻止”时，不会允许 Office 应用创建子进程。 Office 应用包括 Word、Excel、PowerPoint、OneNote 和 Access。 创建子进程是典型的恶意软件行为，尤其是在基于宏的攻击中，该行为试图使用 Office 应用启动或下载恶意可执行文件。  

  **默认值**：阻止

- **脚本下载有效负载执行类型**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) - 指定可能不需要下载或尝试安装的应用程序的检测级别。  

  **默认值**：阻止 

- **防止凭据窃取类型**  
  设置为“启用”可[使用 Credential Guard 保护派生的域凭据](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard)。 Windows Defender 凭据保护使用基于虚拟化的安全性来隔离密钥，以便只有特权系统软件可以访问它们。 未经授权的访问这些密钥可能会导致凭据被盗攻击，如哈希传递或票证传递。 Windows Defender 凭据保护可通过保护 NTLM 密码哈希、Kerberos 票证授予票证和由应用程序存储为域凭据的凭据来防止这些攻击。  

  **默认值**：启用

- **电子邮件内容执行类型**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 设置为“阻止”时，此规则可以阻止从 Microsoft Outlook 或 Webmail （如 Gmail.com 或 Outlook.com）的电子邮件中运行或启动以下文件类型：  

  - 可执行文件（如 .exe、.dll 或 .scr）  
  - 脚本文件（如 PowerShell .ps、VisualBasic .vbs 或 JavaScript .js 文件）  
  - 脚本存档文件  

  **默认值**：阻止

- **Adobe Reader 在子进程中启动**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 设置为“启用”时，此规则可阻止 Adobe Reader 创建子进程。 通过社会工程或攻击，恶意软件可以下载并启动其他有效负载并中断 Adobe Reader。  

  **默认值**：启用

- **脚本混淆的宏代码类型**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 恶意软件和其他威胁可能会尝试在某些脚本文件中混淆或隐藏其恶意代码。 此规则可阻止运行混淆的脚本。  
    
  **默认值**：阻止

- **不受信任的 USB 进程类型**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 设置为“阻止”时，无法运行 USB 可移动驱动器和 SD 卡中的未签名或不受信任的可执行文件。

  可执行文件包括：
  - 可执行文件（如 .exe、.dll 或 .scr）
  - 脚本文件（如 PowerShell .ps、VisualBasic .vbs 或 JavaScript .js 文件）  

  **默认值**：阻止

- **Office 应用其他进程注入类型**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 设置为“阻止”时，Office 应用（包括 Word、Excel、PowerPoint 和 OneNote）无法将代码注入到其他进程中。 恶意软件通常会使用代码注入来运行恶意代码，试图对防病毒扫描引擎隐藏活动。  

  **默认值**：阻止

- **Office 宏代码运行 Win32 导入类型**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 设置为“阻止”时，此规则可尝试阻止包含可导入 Win32 DLL 的宏代码的 Office 文件。 Office 文件包括 Word、Excel、PowerPoint 和 OneNote。 恶意软件可以在 Office 文件中使用宏代码来导入和加载 Win32 DLL，然后使用这些 DLL 进行 API 调用，以在整个系统中实现进一步感染。  

  **默认值**：阻止

- **Office 通信应用在子进程中启动**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 设置为“启用”时，此规则可阻止 Outlook 创建子进程。 通过阻止创建子进程，此规则可防止社会工程攻击，并防止攻击代码滥用 Outlook 中的漏洞。  

  **默认值**：启用

- **Office 应用可执行内容创建或启动类型**  
  [攻击面减少规则](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - 设置为“阻止”时，Office 应用无法创建可执行文件内容。 Office 应用包括 Word、Excel、PowerPoint、OneNote 和 Access。  

  此规则针对创建或启动可执行文件的可疑和恶意外接程序和脚本（扩展）使用的典型行为。 这是典型的恶意软件技术。 将阻止 Office 应用使用扩展。 这些扩展通常使用 Windows Scripting Host（.wsh 文件）来运行脚本，自动执行某些任务或提供用户创建的外接程序功能。

  **默认值**：阻止

## <a name="bitlocker"></a>BitLocker  

有关详细信息，请参阅 Windows 文档中的 [BitLocker 组策略设置](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)。  

- **加密设备**  
  选择“是”可启用 BitLocker 设备加密。 根据设备硬件和 Windows 的版本，可能会要求设备用户确认设备上没有第三方加密。 如果在第三方加密处于活动状态时启用 Windows 加密，将导致设备不稳定。  

   **默认值**：是

- **Bit locker 可移动驱动器策略**  
  此策略的值确定 BitLocker 用于加密可移动驱动器的密码强度。 企业可以控制加密级别，增强安全性（AES-256 强于 AES-128）。 如果选择“是” 来启用此设置，可以为固定的数据驱动器、操作系统驱动器和可移动数据驱动器单独配置加密算法和密钥加密强度。 对于固定的驱动器和操作系统驱动器，建议使用 XTS-AES 算法。 对于可移动驱动器，如果驱动器用于非运行 Windows 10（版本 1511 或更高版本）的其他设备，则应使用 AES-CBC 128 位或 AES-CBC 256 位。 如果驱动器已加密或正在进行加密，更改加密方法不会产生任何影响。 在这些情况下，将忽略此策略设置。 

  对于 Bit locker 可移动驱动器策略，配置以下设置：

    - **需要为写入权限进行加密**  
      **默认值**：是

    - **加密方法**  
      **默认值**：AES 128 位 CBC

- **Bit locker 固定驱动器策略**  
  此策略的值确定 BitLocker 用于加密固定驱动器的密码强度。 企业可以控制加密级别，增强安全性（AES-256 强于 AES-128）。 如果启用此设置，可以为固定的数据驱动器、操作系统驱动器和可移动数据驱动器单独配置加密算法和密钥加密强度。 对于固定的驱动器和操作系统驱动器，建议使用 XTS-AES 算法。 对于可移动驱动器，如果驱动器用于非运行 Windows 10（版本 1511 或更高版本）的其他设备，则应使用 AES-CBC 128 位或 AES-CBC 256 位。 如果驱动器已加密或正在进行加密，更改加密方法不会产生任何影响。 在这些情况下，将忽略此策略设置。

  对于 Bit locker 固定驱动器策略，配置以下设置：

    - **需要为写入权限进行加密**  
      **默认值**：是

    - **加密方法**  
      **默认值**：AES 128 位 XTS

- **Bit locker 系统驱动器策略**  
  此策略的值确定 BitLocker 用于加密系统驱动器的密码强度。 企业可能想要控制加密级别，增强安全性（AES-256 强于 AES-128）。 如果启用此设置，可以为固定的数据驱动器、操作系统驱动器和可移动数据驱动器单独配置加密算法和密钥加密强度。 对于固定的驱动器和操作系统驱动器，建议使用 XTS-AES 算法。 对于可移动驱动器，如果驱动器用于非运行 Windows 10（版本 1511 或更高版本）的其他设备，则应使用 AES-CBC 128 位或 AES-CBC 256 位。 如果驱动器已加密或正在进行加密，更改加密方法不会产生任何影响。 在这些情况下，将忽略此策略设置。  

  对于 Bit locker 系统驱动器策略，配置以下设置：  

  - **加密方法**  
    **默认值**：AES 128 位 XTS

## <a name="device-control"></a>设备控制  

- **完全扫描期间扫描可移动驱动器**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) - 设置为“是”时，Defender 将在完全扫描期间扫描可移动驱动器（如闪存驱动器）中的恶意软件和不需要的软件。 Defender 防病毒软件将先扫描 USB 设备上的所有文件，然后才能运行 USB 设备上的文件。

  此列表中的相关设置：Defender/AllowFullScanOnMappedNetworkDrives  

  **默认值**：是

- **与内核 DMA 保护不兼容的外部设备的枚举**  
   请参阅 [Policy CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)（策略 CSP - DmaGuard）中的 *DmaGuard/DeviceEnumerationPolicy*

  此策略旨在针对支持 DMA 的外部设备提供额外的安全保障。 有了它，可更大程度地控制与 DMA 设备内存隔离和沙盒不兼容但支持 DMA 的外部设备的枚举。

  仅当内核 DMA 保护受到支持且已由系统固件启用时，此策略才有效。 内核 DMA 保护是一项平台功能，它不可通过策略或由设备用户控制。 制造时系统必须支持此功能。 

  要查看系统是否支持内核 DMA 保护，请在系统上运行 MSINFO32.exe，并查看“摘要”页中的“内核 DMA 保护”字段。  

  选项包括： 
  - *设备默认值* - 登录或解锁屏幕后，将允许随时枚举具有 DMA 重新映射兼容驱动程序的设备。 仅在用户解锁屏幕后枚举具有 DMA 重新映射不兼容驱动程序的设备
  - *全部允许* - 将随时枚举所有支持 DMA 的外部 PCIe 设备
  - *全部阻止* - 将允许随时枚举具有 DMA 重新映射兼容驱动程序的设备。 从不允许具有 DMA 重新映射不兼容驱动程序的设备随时启动并执行 DMA。

  **默认值**：设备默认值

- **按设备标识符安装硬件设备**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) - 使用此策略，可以指定禁止 Windows 安装的设备的即插即用硬件 ID 和兼容 ID 的列表。 此策略设置优先于任何其他允许 Windows 安装设备的策略设置。 如果启用此策略设置（设置为“阻止安装硬件设备”），则禁止 Windows 安装你所创建的列表中列出了其硬件 ID 或兼容 ID 的设备。 如果在某个远程桌面服务器上启用了此策略设置，则此策略会影响指定设备从远程桌面客户端到该远程桌面服务器的重定向。 如果禁用或未配置此策略设置（设置为“允许安装硬件设备”），则设备可以根据其他策略设置来允许或阻止安装和更新。  

  **默认值**：阻止安装硬件设备  

  选择“阻止安装硬件设备”时，以下设置将可用。
  - **删除匹配的硬件设备**  
    仅“按设备标识符安装硬件设备”设置为“阻止安装硬件设备”时，此设置才可用。  

    **默认值**：无默认配置

  - **已阻止的硬件设备标识符**  
    仅“按设备标识符安装硬件设备”设置为“阻止安装硬件设备”时，此设置才可用。 若要配置此设置，请展开该选项，选择“+ 添加”，然后指定要阻止的硬件设备标识符。  

    **默认值**：不阻止任何设备  

- **阻止直接内存访问**  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) - 使用此策略设置可以阻止设备上的所有热插拔 PCI 下游端口进行直接内存访问 (DMA)，直到用户登录 Windows。 用户登录后，Windows 会枚举连接到热插拔 PCI 端口的 PCI 设备。 用户每次锁定计算机都会阻止无子设备的热插拔 PCI 端口进行 DMA，直到用户再次登录。 已在计算机解锁时枚举的设备继续工作，直到拔出。 

  只在启用了 BitLocker 或设备加密时才执行此策略设置。  

  **默认值**：是


- **按安装程序类安装硬件设备**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) - 使用此策略可以指定禁止 Windows 安装的设备驱动程序的设备安装程序类全局唯一标识符 (GUID) 列表。 此策略设置优先于任何其他允许 Windows 安装设备的策略设置。 如果启用此策略设置（设置为“阻止安装硬件设备”），则禁止 Windows 安装或更新你所创建的列表中列出了其设备安装程序类 GUID 的设备驱动程序。 如果在某个远程桌面服务器上启用了此策略设置，则此策略设置会影响指定设备从远程桌面客户端到该远程桌面服务器的重定向。 如果禁用或未配置此策略设置（设置为“允许安装硬件设备”），则 Windows 可以根据其他策略设置来允许或阻止安装和更新设备。  

  **默认值**：阻止安装硬件设备

  选择“阻止安装硬件设备”时，以下设置将可用。  

  - **删除匹配的硬件设备**  
    仅“按安装程序类安装硬件设备”设置为“阻止硬件设备安装”时，此设置才可用。  
 
    **默认值**：无默认配置  

  - **已阻止的硬件设备标识符**  
    仅“按安装程序类安装硬件设备”设置为“阻止硬件设备安装”时，此设置才可用。 若要配置此设置，请展开该选项，选择“+ 添加”，然后指定要阻止的硬件设备标识符。  
 
    **默认值**：不阻止任何设备

## <a name="endpoint-detection-and-response"></a>终结点检测和响应  
有关详细信息，请参阅 Windows 文档中的 [WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp)。  

- **提高遥测报告频率** - *Configuration/TelemetryReportingFrequency*  

  提高 Microsoft Defender 高级威胁防护遥测报告频率。  

  **默认值**：是

- **所有文件的示例共享** - *Configuration/SampleSharing*  

  返回或设置 Microsoft Defender 高级威胁防护示例共享配置参数。  

  **默认值**：是

## <a name="exploit-protection"></a>Exploit Protection  

- **Exploit protection XML**  
  有关详细信息，请参阅 Windows 文档中的[导入、导出和部署 exploit protection 配置](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml)。  

  使 IT 管理员能够将表示所需系统和应用程序缓解选项的配置推送到组织中的所有设备。 配置由 XML 表示。 

  应用 Exploit Protection，可帮助保护设备免受利用攻击进行传播的恶意软件的侵袭。 使用 Windows 安全性应用或 PowerShell 来创建一组缓解方案（称为配置）。 然后，可将此配置导出为 XML 文件，并与网络中的多台计算机共享，使其全部拥有相同的一组缓解设置。
 
  此外，还可将现有的 EMET 配置 XML 文件转换为和导入到 Exploit Protection 配置 XML。

- **阻止 exploit protection 替代**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) - 设置为“是”可阻止用户更改 Windows Defender 安全中心的 exploit protection 设置区域。 如果禁用或未配置此设置，本地用户可以在 exploit protection 设置区域中进行更改。  
  **默认值**：是  

- **受控文件夹访问权限**  
  请参阅 [Defender/ControlledFolderAccessAllowedApplications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessallowedapplications) 和 [Defender/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders) 
  
   阻止不友好应用对文件和文件夹进行未经授权的更改。

  **默认值**：审核模式

## <a name="web-network-protection"></a>Web 网络保护  

- **网络保护类型**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) - 此策略可用于在 Windows Defender 攻击防护中启用或禁用网络保护。 网络保护是 Windows Defender 攻击防护的一项功能，可阻止员工使用任何应用访问 Internet 上的钓鱼邮件、攻击宿主站点和恶意内容。 这包括阻止第三方浏览器连接到危险站点。  

  设置为“启用”或“审核模式”时，用户无法禁用网络保护，但可以使用 Windows Defender 安全中心查看有关连接尝试的信息。  
 
  - “启用”将阻止用户和应用连接到危险的域。  
  - “审核模式”不会阻止用户和应用连接到危险的域。  

  设置为“用户定义”时，不会阻止用户和应用连接到危险的域，并且 Windows Defender 安全中心不会提供有关连接的信息。  

  **默认值**：审核模式

- **Microsoft Edge SmartScreen**  
  [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) - 默认情况下，Microsoft Edge 使用 Windows Defender SmartScreen（已启用）防止用户受潜在网络钓鱼诈骗和恶意软件侵袭。 默认情况下，此策略处于启用状态（设置为“是”），启用时可阻止用户关闭 Windows Defender SmartScreen。  设备的有效策略为未配置时，用户可以关闭 Windows Defender SmartScreen，这使设备不受保护。  

  **默认值**：是
  
- **阻止恶意网站访问**  
  [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) - 默认情况下，Microsoft Edge 允许用户绕过（忽略）有关潜在恶意站点的 Windows Defender SmartScreen 警告，以便用户继续访问该站点。 启用此策略（设置为“是”）时，Microsoft Edge 可阻止用户绕过警告，并阻止他们继续访问该站点。  

  **默认值**：是

- **阻止下载未经验证的文件**  
  [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) - 默认情况下，Microsoft Edge 允许用户绕过（忽略）有关潜在恶意文件的 Windows Defender SmartScreen 警告，以便他们继续下载未经验证的文件。 启用此策略（设置为“是”）时，将阻止用户绕过警告，并且无法下载未经验证的文件。  

  **默认值**：是

## <a name="windows-defender-anti-virus----settings-review-pending-for-this-section"></a>Windows Defender 防病毒软件 [此部分的设置查看挂起]

有关详细信息，请参阅 Windows 文档 [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)（策略 CSP - Defender）。

- **扫描 Microsoft Web 浏览器中加载的脚本**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) - 设置为“是”可允许 Windows Defender 脚本扫描功能。  

  **默认值**：是

- **扫描传入的电子邮件**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) - 设置为“是”可允许 Windows Defender 扫描电子邮件。  

  **默认值**：是

- **Defender 示例提交同意类型**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) - 检查 Windows Defender 中用户的同意级别是否可发送数据。 如果已获取所需同意，Windows Defender 会将其提交。 如果未获取（且用户已指定绝不要求），则发送数据前启动 UI 申请获取用户同意（当“云提供的保护”设置为“是”时）。  

  **默认值**：自动发送安全示例

- **网络检查系统 (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) - 阻止由网络检查系统 (NIS) 中的签名检测到的恶意流量。  
 
  **默认值**：是

- **签名更新间隔（小时）**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) - 指定设备检查新的 Defender 签名更新的频率（以小时为单位）。  
 
  **默认值**：4

- **配置计划扫描的低 CPU 优先级**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) - 设置为“是”时，扫描的 CPU 优先级将设置为低。 设置为“未配置”时，不会更改计划扫描的 CPU 优先级。  

    **默认值**：是

- **Defender 阻止访问时保护**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) - 设置为“是”时，将启用 Windows Defender 访问时保护。  

  **默认值**：是

- **要执行的系统扫描类型**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) - Defender 扫描类型。  

  **默认值**：快速扫描

- **扫描所有下载**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) - 设置为“是”时，Defender 会扫描所有下载的文件和附件。  

  **默认值**：是

- **删除隔离的恶意软件之前的天数**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) - 指定系统上的隔离区项目在自动删除之前的保留天数。 设置为零时，将永远不会自动删除隔离区中的项目。  

  **默认值**：0

- **计划扫描开始时间**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) - 计划一天中 Defender 扫描设备的时间。 
  
  此列表中的相关选项：Defender/ScheduleScanDay   

  **默认值**：上午 2 点

- **云提供的保护**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) - 设置为“是”时，Windows Defender 会向 Microsoft 发送有关找到的任何问题的信息。 Microsoft 会分析该信息，详细了解影响你和其他客户的问题，并提供改进的解决方案。

  将此策略设置为“是”时，可以使用“Defender 示例提交同意类型”给予用户从其设备发送信息的控制权。  

  **默认值**：是

- **Defender 可能不需要的应用操作**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) - Windows Defender 防病毒软件可以识别和阻止在网络中的终结点下载和安装可能不需要的应用程序 (PUA)。 
 
  - 设置为“阻止”时，Windows Defender 会阻止 PUA，并将其与其他威胁一起列在历史记录中。
  - 设置为“审核”时，Windows defender 会检测到 PUA，但不会阻止它们。 可以通过搜索由事件查看器中的 Windows Defender 创建的事件找到有关 Windows Defender 要对其执行操作的应用程序的信息。  
  - 设置为“设备默认值”时，PUA 保护处于关闭状态。  
 
  **默认值**：阻止

- **Defender 云扩展超时**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) - 指定等待云返回结果时，Windows Defender 防病毒软件应阻止文件的最长延长时间。 Windows Defender 等待的基本时间为 10 秒。 在此处指定的任意延长时间（最多 50 秒）已添加到这 10 秒之后。 大多数情况下，扫描所需的时间少于最大值。 延长时间可使云对可疑文件进行全面调查。  

  默认情况下，扩大的时间值为 0（禁用）。 Intune 建议启用此设置，并至少指定 20 秒的延长时间。  
 
  **默认值**：0

- **扫描存档文件**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) - 设置为“是”可使 Windows Defender 扫描存档文件。  

  **默认值**：是

- **Defender 系统扫描计划**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) - 计划 Defender 扫描设备的日期。 
 
  此列表中的相关选项：Defender/ScheduleScanTime

  **默认值**：用户定义

- **行为监视**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) - 设置为“是”可打开 Windows Defender 行为监视功能。 Windows Defender 行为监视传感器内嵌于 Windows 10，收集并处理来自操作系统的行为信号，并将该传感器数据发送至 Microsoft Defender ATP 的专用独立云实例。  

  **默认值**：是

- **扫描从网络文件夹中打开的文件**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) - 设置为“是”可使 Windows Defender 扫描网络上的文件。 用户无法删除只读文件中检测到的恶意软件。  

  **默认值**：是

- **Defender 云阻止级别**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) - 使用此策略确定 Windows Defender 防病毒软件在阻止和扫描可疑文件时的攻击程度如何。 选项包括：

  - 高 - 主动阻止未知文件，同时针对客户端性能进行优化（误报的可能性更大）
  - 超高 - 主动阻止未知文件，并应用额外的保护措施（可能影响客户端的性能）
  - 零容差 - 阻止所有未知的可执行文件

  **默认值**：未配置

- **实时监视**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) - 设置为“是”可允许 Windows Defender 实时监视。  

  **默认值**：是

- **扫描期间 CPU 使用率限制**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) - 指定 Windows Defender 可在扫描期间使用的最大平均 CPU 使用率 (%)。  

  **默认值**：50

- **在完全扫描期间扫描映射的网络驱动器**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) - 设置为“是”可使 Windows Defender 扫描网络上的文件。 用户无法删除只读文件中检测到的恶意软件。

  此列表中的相关设置：Defender/AllowScanningNetworkFiles

  **默认值**：是

- **阻止最终用户访问 Defender**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) - 设置为“是”可阻止最终用户访问其设备上的 Windows Defender UI。  

  **默认值**：是

- **快速扫描开始时间**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) - 计划一天中 Defender 运行快速扫描的时间。  

  **默认值**：上午 2 点

## <a name="windows-defender-firewall"></a>Windows Defender 防火墙
有关详细信息，请参阅 Windows 文档中的 [Firewall CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)（防火墙 CSP）。

- **删除前的安全关联空闲时间** - *MdmStore/Global/SaIdleTime*   
  如果在此秒数内未检测到任何网络流量，则删除安全关联。  
  **默认值**：300

- **文件传输协议** - *MdmStore/Global/DisableStatefulFtp*   
  阻止有状态文件传输协议 (FTP)。  
  **默认值**：是

- **数据包排队** - *MdmStore/Global/EnablePacketQueue*    
  指定如何针对 IPsec 隧道网关方案为加密接收和明文转发启用接收端上的软件缩放。 这将确保数据包顺序得到保留。  
  **默认值**：设备默认值

- **防火墙配置文件域** - *FirewallRules/FirewallRuleName/Profiles*  
  指定规则所属的配置文件：域、专用、公用。 此值表示连接到域的网络的配置文件。  

  可用设置：  
  - **需要针对多播广播的单播响应**  
    **默认值**：是

  - **已合并来自组策略的已授权的应用程序规则**  
    **默认值**：是

  - **已阻止入站通知**  
    **默认值**：是

  - **已合并来自组策略的全局端口规则**  
    **默认值**：是

  - **已阻止隐藏模式**  
    **默认值**：是

  - **防火墙已启用**  
    **默认值**：允许

  - **未合并来自组策略的连接安全规则**  
    **默认值**：是

  - **未合并来自组策略的策略规则**  
    **默认值**：是

- **防火墙配置文件公用** - *FirewallRules/FirewallRuleName/Profiles*  
  指定规则所属的配置文件：域、专用、公用。 此值表示公用网络的配置文件。 这些网络由服务器主机中的管理员分类为公用。 主机首次连接到网络时会进行分类。 通常，这些网络位于网络中的对等方或网络管理员不被信任的机场、咖啡店和其他公共场所。  

  可用设置：

  - **已阻止入站连接**  
    **默认值**：是 

  - **需要针对多播广播的单播响应**  
    **默认值**：是  

  - **需要隐藏模式**  
    **默认值**：是 
 
  - **需要出站连接**  
    **默认值**：是  

  - **已合并来自组策略的已授权的应用程序规则**  
    **默认值**：是  

  - **已阻止入站通知**  
    **默认值**：是  

  - **已合并来自组策略的全局端口规则**  
    **默认值**：是

  - **已阻止隐藏模式**  
    **默认值**：是

  - **防火墙已启用**  
    **默认值**：允许  

  - **未合并来自组策略的连接安全规则**  
    **默认值**：是  

  - **需要传入流量**  
    **默认值**：是

  - **未合并来自组策略的策略规则**  
    **默认值**：是  

- **防火墙配置文件专用** - *FirewallRules/FirewallRuleName/Profiles*  
  指定规则所属的配置文件：域、专用、公用。 此值表示专用网络的配置文件。  

  可用设置： 

  - **已阻止入站连接**  
    **默认值**：是

  - **需要针对多播广播的单播响应**  
    **默认值**：是

  - **需要隐藏模式**  
    **默认值**：是

  - **需要出站连接**  
    **默认值**：是

  - **已阻止入站通知**  
    **默认值**：是

  - **已合并来自组策略的全局端口规则**  
    **默认值**：是

  - **已阻止隐藏模式**  
    **默认值**：是  

  - **防火墙已启用**  
    **默认值**：允许

  - **未合并来自组策略的已授权的应用程序规则**  
    **默认值**：是

  - **未合并来自组策略的连接安全规则**  
    **默认值**：是

  - **需要传入流量**  
    **默认值**：是

  - **未合并来自组策略的策略规则**  
    **默认值**：是  

- **防火墙预共享密钥编码方法**  
  **默认值**：UTF8

- **证书吊销列表验证**  
  **默认值**：设备默认值

## <a name="windows-hello-for-business"></a>Windows Hello 企业版  

有关详细信息，请参阅 Windows 文档中的 [PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp)。

- **配置 Windows Hello 企业版** - *TenantId/Policies/UsePassportForWork*    
  Windows Hello 企业版是一种取代密码、智能卡和虚拟智能卡登录 Windows 的替代方法。  

  如果启用或未配置此策略设置，设备将预配 Windows Hello 企业版。 如果禁用此策略设置，设备不会为任何用户预配 Windows Hello 企业版。

  Intune 不支持禁用 Windows Hello。 相反，可以配置策略以启用 Windows Hello 企业版（“是”），或不直接配置 Windows Hello（“未配置”）。 如果未配置，设备可以通过其他策略接收配置，这样可能会启用或禁用此功能。  

  **默认值**：是  

- **要求 PIN 中含有小写字母** - *TenantId/Policies/PINComplexity/LowercaseLetters*  
  **默认值**：允许  

- **要求 PIN 中含有特殊字符** - *TenantId/Policies/PINComplexity/SpecialCharacters*  
  **默认值**：允许  

- **要求 PIN 中含有大写字母** - *TenantId/Policies/PINComplexity/UppercaseLetters*   
  **默认值**：允许  

