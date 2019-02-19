---
title: 适用于 Intune 的 Windows 安全基线设置
titleSuffix: Microsoft Intune
description: Intune 支持的 Windows 安全基线设置
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91a8364927667bbc910d86dc3e95f447eb5cf93a
ms.sourcegitcommit: 77c63ddb51ffd5258f4ea0e68672c2eb011b83e1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905809"
---
# <a name="windows-security-baseline-settings-for-intune"></a>适用于 Intune 的 Windows 安全基线设置  

请查看 Microsoft Intune 支持的 [Windows 安全基线设置](security-baselines.md)。  

> [!NOTE]  
> Windows 安全基线设置处于预览状态。 在预览状态下，可用设置的列表，以及此内容呈现这些设置的顺序会因门户中提供的内容而有所不同。  
>  
> 当基线设置不处于预览状态后，此内容将随 Intune 支持的安全基线设置的非预览列表更新。  

## <a name="above-lock"></a>锁定时  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock)。  

- **阻止显示 toast 通知**  
  使用此策略设置，可以阻止应用通知显示在锁定屏幕中。 如果启用此策略设置，则锁定屏幕不会显示任何应用通知。 如果禁用或不配置此策略设置，用户可以选择哪些应用在锁定屏幕上显示通知。
  - **默认值**：是  

## <a name="app-runtime"></a>应用运行时    
有关详细信息，请参阅 Windows 文档中的[策略 CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
)。  

- **Windows 应用商店应用的可选 Microsoft 帐户**  
  使用此策略设置，可以控制：对于需要帐户进行登录的 Windows 应用商店应用，Microsoft 帐户是否可选。 此策略仅影响支持它的 Windows 应用商店应用。 如果启用此策略设置，则通常需要 Microsoft 帐户登录的 Windows 应用商店应用将允许用户改为使用企业帐户登录。 如果禁用或不配置此策略设置，则用户需要使用 Microsoft 帐户登录。  
  - **默认值**：启用  

## <a name="application-management"></a>应用程序管理   
有关详细信息，请参阅 Windows 文档中的[策略 CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement)。  

- **阻止游戏 DVR（仅限桌面版）**  
  配置是否允许游戏的录制和广播。
  - **默认值**：是  

## <a name="auto-play"></a>自动播放   
有关详细信息，请参阅 Windows 文档中的[策略 CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay
)。  

- **自动播放默认自动运行行为**  
  此设置影响 Autorun 命令的默认行为。 Autorun 命令存储在 autorun.inf 文件中，可以启动安装程序或其他例程。 如果设置为“启用”，管理员可在运行 Windows Vista 或更高版本的设备上更改默认的自动运行行为。 行为可设置为：a) 彻底禁用自动运行命名，或 b) 还原到早于 Windows Vista 的自动执行自动运行命令的行为。 如果设置为“禁用”或“未配置”，则运行 Windows Vista 或更高版本的设备将提示用户是否应该运行自动运行命令。
  - **默认值**：不执行  
  
- **自动播放模式**  
  此策略设置允许关闭自动播放功能。 驱动器中插入媒体后，自动播放开始从驱动器中读取数据。 程序安装文件和音频媒体中的音乐立即启动。 在 Windows XP SP2 之前，在可移动驱动器上，如软盘驱动器（但不是 CD-ROM 驱动器）和网络驱动器上，会默认禁用自动播放。 从 Windows XP SP2 开始，也为可移动驱动器（包括 Zip 驱动器和某些 USB 大容量存储设备）启用了自动播放。 如果启用此策略设置，将在 CD-ROM 和可移动媒体驱动器上禁用自动播放，或在所有驱动器上禁用此功能。 此策略设置禁用其他类型驱动器上的自动播放。 不能使用此设置在默认禁用自动播放的驱动器上启用自动播放。 如果禁用或不配置此策略设置，则启用自动播放。 注意：此策略设置将同时显示在计算机配置和用户配置文件夹中。 如果策略设置相互冲突，计算机配置中的策略设置优先于用户配置中的策略设置。
  - **默认值**：已禁用

- **阻止非卷设备的自动播放**  
  此策略设置不允许在照相机或手机等 MTP 设备上进行自动播放。 如果启用此策略设置，则照相机或手机等 MTP 设备上将禁止自动播放。 如果禁用或不配置此策略设置，则对非卷设备启用自动播放。
  - **默认值**：启用  

## <a name="bitlocker"></a>Bitlocker    
有关详细信息，请参阅 Windows 文档中的[策略 CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
)。  

- **Bit locker 可移动驱动器策略**  
  此策略设置用于控制加密方法和密码长度。 此策略的值确定 BitLocker 用于加密的密码强度。 企业可能想要控制加密级别，增强安全性（AES-256 强于 AES-128）。 如果启用此设置，可以为固定的数据驱动器、操作系统驱动器和可移动数据驱动器单独配置加密算法和密钥加密强度。 对于固定的驱动器和操作系统驱动器，建议使用 XTS-AES 算法。 对于可移动驱动器，如果驱动器将用于非运行 Windows 10（版本 1511 或更高版本）的其他设备，则应使用 AES-CBC 128 位或 AES-CBC 256 位。 如果驱动器已加密或正在进行加密，更改加密方法不会产生任何影响。 在这些情况下，将忽略此策略设置。

    - **需要为写入权限进行加密**
      - **默认值**：是  

    - **加密方法**
      - **默认值**：AES 256bit CBC  

- **Bit locker 固定驱动器策略**  
  此策略设置用于控制加密方法和密码长度。 此策略的值确定 BitLocker 用于加密的密码强度。 企业可能想要控制加密级别，增强安全性（AES-256 强于 AES-128）。 如果启用此设置，可以为固定的数据驱动器、操作系统驱动器和可移动数据驱动器单独配置加密算法和密钥加密强度。 对于固定的驱动器和操作系统驱动器，建议使用 XTS-AES 算法。 对于可移动驱动器，如果驱动器将用于非运行 Windows 10（版本 1511 或更高版本）的其他设备，则应使用 AES-CBC 128 位或 AES-CBC 256 位。 如果驱动器已加密或正在进行加密，更改加密方法不会产生任何影响。 在这些情况下，将忽略此策略设置。  
 
  - **加密方法**
    - **默认值**：AES 256bit XTS  

- **Bit locker 系统驱动器策略**  
  此策略设置用于控制加密方法和密码长度。 此策略的值确定 BitLocker 用于加密的密码强度。 企业可能想要控制加密级别，增强安全性（AES-256 强于 AES-128）。 如果启用此设置，可以为固定的数据驱动器、操作系统驱动器和可移动数据驱动器单独配置加密算法和密钥加密强度。 对于固定的驱动器和操作系统驱动器，建议使用 XTS-AES 算法。 对于可移动驱动器，如果驱动器将用于非运行 Windows 10（版本 1511 或更高版本）的其他设备，则应使用 AES-CBC 128 位或 AES-CBC 256 位。 如果驱动器已加密或正在进行加密，更改加密方法不会产生任何影响。 在这些情况下，将忽略此策略设置。  

  - **加密方法**  
    - **默认值**：AES 256bit XTS  

## <a name="browser"></a>浏览器  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser)。  

- **Microsoft Edge SmartScreen**  
  默认情况下，Microsoft Edge 使用 Windows Defender SmartScreen（已启用）防止用户受潜在网络钓鱼诈骗和恶意软件侵袭。 此外，默认情况下，用户不能禁用（关闭）Windows Defender SmartScreen。 启用此策略将关闭 Windows Defender SmartScreen，并阻止用户将其打开。 请勿配置此策略，以允许用户选择打开或关闭 Windows Defender SmartScreen。  
  - **默认值**：是  
  
- **阻止恶意网站访问**  
  默认情况下，Microsoft Edge 允许用户绕过（忽略）有关潜在恶意站点的 Windows Defender SmartScreen 警告，以便他们继续访问该站点。 但是使用此策略，可配置 Microsoft Edge，阻止用户绕过警告，并阻止他们继续访问该站点。
  - **默认值**：是  
  
- **阻止下载未经验证的文件**  </br>
  默认情况下，Microsoft Edge 允许用户绕过（忽略）有关潜在恶意文件的 Windows Defender SmartScreen 警告，以便他们继续下载未经验证的文件。 启用此策略可防止用户绕过警告，阻止他们下载未经验证的文件。
  - 默认值：是  
  
- **阻止使用密码管理器**  </br>
  默认情况下，Microsoft Edge 自动使用密码管理器，从而允许用户在本地管理密码。 禁用此策略可限制 Microsoft Edge 使用密码管理器。 如果想要让用户选择使用密码管理器在本地保存和管理密码，请勿配置此策略。
  - 默认值：是  
  
- **防止覆盖证书错误**  </br>
  此策略设置可阻止用户忽略 Internet Explorer 中那些中断浏览的安全套接字层/传输层安全性 (SSL/TLS)证书错误（如“过期”、“吊销”或“名称不匹配”错误）。 如果启用此策略设置，则用户无法继续浏览。 如果禁用或未配置此策略设置，则用户可以选择忽略证书错误并继续浏览。
  - 默认值：是  

## <a name="connectivity"></a>连接性  
有关详细信息，请参阅 Windows 文档 [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity)（策略 CSP - Connectivity）。  

- **阻止 Web 发布和在线订购向导的 Internet 下载**  
  此策略设置可指定 Windows 是否应下载 Web 发布和在线订购向导的提供商列表。 这些向导允许用户从提供在线存储和照片打印等服务的公司列表中进行选择。 默认情况下，除了注册表中指定的提供商外，Windows 还会显示从 Windows 网站下载的提供商。 如果启用此设置，Windows 将不会下载提供商，只会显示在本地注册表中缓存的服务提供商。 如果禁用或未配置此设置，则在用户使用 Web 发布或在线订购向导时，将会下载服务提供商列表。 请参阅 Web 发布和在线订购向导的文档了解详细信息，包括有关在注册表中指定服务提供商的详细信息。  
  - 默认值：启用  

- **阻止通过 HTTP 下载打印驱动程序**  
  此策略可指定是否允许此客户端通过 HTTP 下载打印机驱动程序包。 要设置 HTTP 打印，需要通过 HTTP 下载产品盒中未提供的驱动程序。 注意：此设置不阻止客户端通过 HTTP 打印到 Intranet 或 Internet 上的打印机。 它仅禁止下载本地尚未安装的驱动程序。 如果启用此策略设置，则无法通过 HTTP 下载打印机驱动程序。 如果禁用或未配置此设置，则用户可通过 HTTP 下载打印机驱动程序。
  - 默认值：启用  

## <a name="credentials-delegation"></a>凭据委派  
有关详细信息，请参阅 Windows 文档 [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
)（策略 CSP - CredentialsDelegation）。  

- **远程主机不可导出的凭据委派**  
  远程主机允许委派不可导出的凭据。 使用凭据委派功能时，设备向远程主机提供一个可导出版本的凭据。 这会使用户面临被位于远程主机上的攻击者盗用凭据的风险。 如果启用此策略设置，主机支持“受限管理”或“远程 Credential Guard”模式。 如果禁用或未配置此策略设置，则不支持“受限管理”和“远程 Credential Guard”模式。 用户始终需要将其凭据传递给主机。  

  - 默认值：启用  

## <a name="credentials-ui"></a>凭据 UI  
有关详细信息，请参阅 Windows 文档 [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui)（策略 CSP - CredentialsUI）。  

- **枚举管理员**    
  此策略设置控制当用户尝试提升正在运行的应用程序时是否会显示管理员帐户。 默认情况下，用户尝试提升正在运行的应用程序时，不会显示管理员帐户。 如果启用此策略设置，则会显示电脑上的所有本地管理员帐户，以便用户可以从中选择一个账户并输入正确的密码。 如果禁用此策略设置，则系统始终要求用户在进行提升时键入用户名和密码。  

  - 默认值：已禁用  

## <a name="data-protection"></a>数据保护  
有关详细信息，请参阅 Windows 文档 [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
)（策略 CSP - DataProtection）。  

- **阻止直接内存访问**   
  此策略设置允许你阻止所有热插拔 PCI 下游端口进行直接内存访问 (DMA)，直到用登录 Windows。 用户登录后，Windows 会枚举连接到热插拔 PCI 端口的 PCI 设备。 用户每次锁定计算机都会阻止无子设备的热插拔 PCI 端口进行 DMA，直到用户再次登录。 已在计算机解锁时枚举的设备继续工作，直到拔出。 只在启用了 BitLocker 或设备加密时才执行此策略设置。
  
  - 默认值：是  

## <a name="device-guard"></a>Device Guard  
有关详细信息，请参阅 Windows 文档 [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
)（策略 CSP - DeviceGuard）。  

- **Credential Guard**  
  此设置可让用户通过基于虚拟化的安全打开 Credential Guard，帮助在下次重启时保护凭据。
  
  - 默认值：使用 UEFI 锁启用 

- **启用基于虚拟化的安全性**  </br>
  在下次重启时打开基于虚拟化的安全性 (VBS)。 基于虚拟化的安全性使用 Windows 虚拟机监控程序提供对安全服务的支持。
  - 默认值：是  

<!-- not yet available 
- **Enable secure boot with DMA**  
  Among the commands that follow, you can choose settings for Secure Boot and Secure Boot with DMA. In most situations, we recommend that you choose Secure Boot. This option provides Secure Boot with as much protection as is supported by a given computer’s hardware. A computer with input/output memory management units (IOMMUs) will have Secure Boot with DMA protection. A computer without IOMMUs will simply have Secure Boot enabled. In contrast, with Secure Boot with DMA, the setting will enable Secure Boot—and VBS itself—only on a computer that supports DMA, that is, a computer with IOMMUs. With this setting, any computer without IOMMUs will not have VBS or HVCI protection, although it can still have WDAC enabled.
  
  - **Default**: Yes  
  -->
- **启动 System Guard**  
  - 默认值：启用  

## <a name="device-installation"></a>设备安装  
有关详细信息，请参阅 Windows 文档 [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation)（策略 CSP - DeviceInstallation）。  

- **按设备标识符安装硬件设备**  
  使用此策略设置可以指定禁止 Windows 安装的设备的即插即用硬件 ID 和兼容 ID 的列表。 此策略设置优先于任何其他允许 Windows 安装设备的策略设置。 如果启用此策略设置，则禁止 Windows 安装你所创建的列表中列出了其硬件 ID 或兼容 ID 的设备。 如果在某个远程桌面服务器上启用了此策略设置，则此策略设置会影响指定设备从远程桌面客户端到该远程桌面服务器的重定向。 如果禁用或未配置此策略设置，则根据其他允许或禁止策略设置来安装和更新设备。
  - 默认值：阻止安装硬件设备  
  
    - **删除匹配的硬件设备**  
      仅“按设备标识符安装硬件设备”设置为“阻止安装硬件设备”时，此设置才可用。
      - 默认值：是
  
    - **已阻止的硬件设备标识符**  </br>
      仅“按设备标识符安装硬件设备”设置为“阻止安装硬件设备”时，此设置才可用。
      - 默认值：是  
  
- **按安装程序类安装硬件设备**  
  使用此策略设置可以指定禁止 Windows 安装的设备驱动程序的设备安装程序类全局唯一标识符 (GUID) 列表。 此策略设置优先于任何其他允许 Windows 安装设备的策略设置。 如果启用此策略设置，则禁止 Windows 安装或更新你所创建的列表中列出了其设备安装程序类 GUID 的设备驱动程序。 如果在某个远程桌面服务器上启用了此策略设置，则此策略设置会影响指定设备从远程桌面客户端到该远程桌面服务器的重定向。 如果禁用或未配置此策略设置，则 Windows 根据其他允许或禁止策略设置来安装和更新设备。
  - 默认值：阻止安装硬件设备  
  
    - **删除匹配的硬件设备**  </br>
      仅“按安装程序类安装硬件设备”设置为“阻止硬件设备安装”时，此设置才可用。
      - **默认值**：无默认配置  
  
    - **已阻止的硬件设备标识符**  </br>
      仅“按安装程序类安装硬件设备”设置为“阻止硬件设备安装”时，此设置才可用。
      - **默认值**：*无默认配置*  

## <a name="device-lock"></a>设备锁定  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock)（策略 CSP - DeviceLock）。  

- **阻止使用摄像头**  
  禁用“电脑设置”中的锁屏界面摄像头切换开关，并阻止在锁定屏幕上调用摄像头。 默认情况下，用户可以在锁屏界面上启用可用摄像头的调用。 如果启用此设置，用户将无法再在“电脑设置”中启用或禁用锁屏界面摄像头访问，并且无法在锁屏界面上调用摄像头。  
  - **默认值**：启用  

- **需要密码**  
  指定是否启用设备锁定。
  - **默认值**：是  
  
  - **密码最小字符集数**  
    强 PIN 或密码所需的复杂元素类型（大写和小写字母、数字和标点符号）的数量。 PIN 会对桌面设备和移动设备强制执行以下行为：1 - 仅数字 2 - 必须为数字和小写字母 3 - 必须为数字、小写字母和大写字母。 在桌面 Microsoft 帐户和域帐户中不支持。 4 - 必须为数字、小写字母、大写字母和特殊字符。 在桌面中不支持。 默认值为 1。 
    - **默认值**：3  
  
  - **擦除设备前的登录失败次数**  
    擦除设备之前允许的身份验证失败次数。 值为 0 会禁用设备擦除功能。
    - **默认值**：10  
  
  - **密码过期（天数）**  
    “最长密码期限”策略设置确定在系统要求用户更改密码之前可以使用密码的时间（以天数为单位）。 可将密码设置为在天数（1 至 999）之后过期，也可通过将天数设置为 0 来指定密码永不过期。 如果最长密码期限是介于 1 到 999 天之间，最短密码期限必须小于最长密码期限。 如果最长密码期限设置为 0，最短密码期限可以是介于 0 和 998 天之间的任意值。
    - **默认值**：60  
  
  - **所需的密码类型**  
    确定所需的 PIN 或密码类型。
    - **默认值**：字母数字  
  
  - **最短密码长度**  
    “最小密码长度”策略设置确定可以组成用户帐户密码的最少字符数。 可以设置的值介于 1 到 14 个字符之间，也可以通过将字符数设置为 0 来确定不需要密码。
    - **默认值**：8  
  
  - **禁止使用简单密码**  
    指定是否允许使用 PIN 或“1111”或“1234”等密码。 对桌面版，还可以控制图片密码的使用。
    - **默认值**：是  
       设置为“是”可防止使用简单密码。 

  - **防止重用以前的密码**  
    指定可以在历史记录中存储的无法使用的密码数。 该值包括用户的当前密码。 这意味着设置为 1 时，用户在选择新密码时无法重复使用当前密码，而设置为 5 则表示用户无法将其新密码设置为当前密码或前四个密码中的某个密码。
    - **默认值**：24  

- **阻止幻灯片放映**  
  禁用“电脑设置”中的锁屏界面幻灯片放映设置，并阻止在锁屏界面上播放幻灯片放映。 默认情况下，用户可以启用在计算机锁定后运行的幻灯片放映。 如果启用此设置，用户将无法修改“电脑设置”中的幻灯片放映设置，也无法启动幻灯片放映。
  - **默认值**：启用  
    设置为“启用”会阻止运行幻灯片放映。 

- **密码最短期限（以天为单位）**  
  “最短密码期限”策略设置确定用户在更改密码之前必须使用的时间（以天为单位）。 可以将值设置为 1 至 998 天，也可以通过将天数设置为 0 来允许立即更改密码。 除非将密码最长期限设置为 0（表示密码永不过期），否则最短密码期限必须小于最长密码期限。 如果最长密码期限设置为 0，最短密码期限可以设置为介于 0 和 998 天之间的任意值。
  - **默认值**：1  

## <a name="event-log-service"></a>事件日志服务  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice)（策略 CSP - EventLogService）。  

- **安全日志的最大文件大小 (KB)**  
  此策略设置指定日志文件的最大大小 (KB)。 如果启用此策略设置，则可将最大日志文件大小配置为 1 MB (1024 KB) 至 2 TB (2147483647 KB) 之间（以千字节递增）。 如果禁用或未配置此策略设置，则日志文件的最大大小将设置为本地配置的值。 本地管理员可以使用“日志属性”对话框更改此值（默认值为 20 MB）。
  - **默认值**：196608  

- **系统日志的最大文件大小 (KB)**  
  此策略设置指定日志文件的最大大小 (KB)。 如果启用此策略设置，则可将最大日志文件大小配置为 1 MB (1024 KB) 至 2 TB (2147483647 KB) 之间（以千字节递增）。 如果禁用或未配置此策略设置，则日志文件的最大大小将设置为本地配置的值。 本地管理员可以使用“日志属性”对话框更改此值（默认值为 20 MB）。
  - **默认值**：32768  

- **应用程序日志的最大文件大小 (KB)**  
  此策略设置指定日志文件的最大大小 (KB)。 如果启用此策略设置，则可将最大日志文件大小配置为 1 MB (1024 KB) 至 2 TB (2147483647 KB) 之间（以千字节递增）。 如果禁用或未配置此策略设置，则日志文件的最大大小将设置为本地配置的值。 本地管理员可以使用“日志属性”对话框更改此值（默认值为 20 MB）。
  - **默认值**：32768  

## <a name="experience"></a>体验  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)（策略 CSP - 体验）。  

- **阻止 Windows 聚焦**  
  允许 IT 管理员关闭所有 Windows 聚焦功能 - 锁屏界面上的 Windows 聚焦、Windows 提示、Microsoft 使用者功能和其他相关的功能。
  - **默认值**：是  
  
  - **阻止 Windows 聚焦中的第三方建议**  
    指定是否允许第三方软件发布者在 Windows 屏幕聚焦功能（例如，锁屏界面聚焦、“开始”菜单中的建议应用和 Windows 提示）中提供应用和内容建议。 用户仍可以看到有关 Microsoft 功能、应用和服务的建议。
     - **默认值**：是  
  - **阻止使用者特定功能**  
    允许 IT 管理员启用通常只面向使用者的体验，例如“入门”建议、成员资格通知、OOBE 后应用安装和重定向磁贴。
    - **默认值**：是  


## <a name="exploit-guard"></a>攻击防护  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard)（策略 CSP - ExploitGuard）。  

- **Exploit protection XML**  
  使 IT 管理员能够将表示所需系统和应用程序缓解选项的配置推送到组织中的所有设备。 配置由 XML 表示。 应用 Exploit Protection，可帮助保护设备免受利用攻击进行传播的恶意软件的侵袭。 使用 Windows 安全性应用或 PowerShell 来创建一组缓解方案（称为配置）。 然后，可将此配置导出为 XML 文件，并与网络中的多台计算机共享，使其全部拥有相同的一组缓解设置。 此外，还可将现有的 EMET 配置 XML 文件转换为和导入到 Exploit Protection 配置 XML。
  - **默认值**：*已提供示例 xml* 
 
## <a name="file-explorer"></a>文件资源浏览器  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer)。  

- **阻止“数据执行保护”**  
  禁用数据执行保护可允许某些旧插件应用程序在不终止资源管理器的情况下正常运行。
  - **默认值**：已禁用  
   
- **阻止“损坏时堆终止”**  
  禁用“损坏时堆终止”可允许某些旧的插件应用程序在不立即终止资源管理器的情况下正常运行，但资源管理器稍后仍可能意外终止。
  - **默认值**：已禁用  
    

## <a name="internet-explorer"></a>Internet Explorer  
有关详细信息，请参阅 Windows 文档[策略 CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer)。  
<!-- not yet available 
- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  - **Default**: Disabled  
  
- **Office apps launch child process type**  
  Office apps will not be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  - **Default**: Disable  
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  - **Default**: Disable  
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  - **Default**: Disabled  
 -->
- **Internet Explorer 对数据源的 Internet 区域访问权限**  
  通过此策略设置，可控制 Internet Explorer 是否可以使用 Microsoft XML 分析程序 (MSXML) 或 ActiveX 数据对象 (ADO) 访问另一个安全区域的数据。 如果启用此策略设置，用户可以在区域中加载页面，该页面使用 MSXML 或 ADO 访问区域中其他站点的数据。 如果在下拉列表框中选择“提示”，将会提示用户选择是否允许在区域中加载页面，该页面使用 MSXML 或 ADO 访问区域中其他站点的数据。 如果禁用此策略设置，则用户无法在区域中加载使用 MSXML 或 ADO 访问区域中其他站点数据的页面。 如果不配置此策略设置，则用户无法在区域中加载使用 MSXML 或 ADO 访问区域中其他站点数据的页面。
  - 默认值：禁用  
  
- **Internet Explorer 限制在 Windows 内的不同域之间拖动内容**  
  使用此策略设置，可以设置选项，用于在源和目标位于同一窗口时将内容从一个域拖到另一个域。 如果启用此策略设置并单击“启用”，用户可以在源和目标位于同一窗口时将内容从一个域拖到另一个域。 用户无法更改此设置。 如果启用此策略设置并单击“禁用”，则用户无法在源和目标位于同一窗口时将内容从一个域拖到另一个域。 用户无法在 Internet 选项对话框中更改此设置。 在 Internet Explorer 10 中，如果禁用此策略设置或未配置它，则用户无法在源和目标位于同一窗口时将内容从一个域拖到另一个域。 用户可以在 Internet 选项对话框中更改此设置。 在 Internet Explorer 9 或较早版本中，如果禁用或未配置此策略设置，用户可以在源和目标位于同一窗口时将内容从一个域拖到另一个域。 用户无法在 Internet 选项对话框中更改此设置。
  - **默认值**：已禁用
  
- **Internet Explorer 证书地址不匹配警告**  
  使用此策略设置，能够启用证书地址不匹配安全性警告。 启用此策略设置后，用户在访问安全 HTTP (HTTPS) 网站时，如果其中显示的是为其他网址颁发的证书，用户会收到警告。 此警告有助于防止欺骗攻击。 如果启用此策略设置，会一直显示证书地址不匹配警告。 如果禁用或不配置此策略设置，用户可以选择是否显示证书地址不匹配警告（通过使用 Internet 控制面板中的“高级”页）。
  - **默认值**：启用 
  
- **Internet Explorer 限制区域低权限网站**  
  使用此策略设置，可以控制权限较低的区域的网站（如 Internet 站点）是否能够导航到此区域。 如果启用此策略设置，低权限区域的网站可在此区域中打开新窗口，或导航到此区域。 安全区域运行时将不具有由“区域提升保护”安全功能提供的额外一层安全性。 如果在下拉列表框中选择“提示”，则会在将要发生可能有风险的导航时向用户发出警告。 如果禁用此策略设置，将阻止可能有害的导航。 Internet Explorer 安全功能将在此区域中启用，如“区域提升保护”功能控件中所设置的那样。 如果不配置此策略设置，将阻止可能有害的导航。 Internet Explorer 安全功能将在此区域中启用，如“区域提升保护”功能控件中所设置的那样。
  - **默认值**：禁用  
  
- **Internet Explorer 限制区域自动提示文件下载**  </br>
  此策略设置决定系统是否会就非用户启动的文件下载提示用户。 无论此设置如何，用户都将收到用户启动的下载的文件下载对话框。 如果启用此设置，用户将收到针对自动下载尝试的文件下载对话框。 如果禁用或未配置此设置，系统将阻止非用户启动的文件下载，并且用户将看到“通知”栏而非文件下载对话框。 然后，用户可以单击通知栏，允许文件显示下载提示。
  - **默认值**：已禁用
  
- **Internet Explorer Internet 区域 .NET Framework 相关组件**  
  使用此策略，可以控制未使用验证码签名的 .NET Framework 组件是否可以在 Internet Explorer 中执行。 这些组件包括从对象标记中引用的托管控件和从链接中引用的托管可执行文件。 如果启用此策略设置，Internet Explorer 将执行未签名的托管组件。 如果在下拉列表框中选择“提示”，Internet Explorer 将提示用户决定是否执行未签名的托管组件。 如果禁用此策略设置，Internet Explorer 将不执行未签名的托管组件。 如果未配置此策略设置，Internet Explorer 将执行未签名的托管组件。
  - **默认值**：禁用 
  
- **Internet Explorer internet 区域仅允许批准的域使用 tdc ActiveX 控件**  </br>
  此策略设置控制是否允许用户在网站上运行 TDC ActiveX 控件。 如果启用此策略设置，则 TDC ActiveX 控件不会从此区域中的网站运行。 如果禁用此策略设置，TDC ActiveX 控件会从此区域中的所有站点运行。
  - 默认值：启用 
  
- **Internet Explorer 限制区域脚本启动窗口**  
  使用此设置，可以管理针对脚本启动的弹出窗口和包含标题和状态栏的窗口的限制。 如果启用此策略设置，则不会在此区域中应用 Windows 限制安全。 安全区域运行时将不具有此功能提供的额外一层安全性。 如果禁用此策略设置，则脚本启动的弹出窗口和含标题和状态栏的窗口中包含的可能有害的操作将无法运行。 此区域中将启用此 Internet Explorer 安全功能，如进程的“脚本化 Windows 安全限制”功能控件设置所规定的那样。 如果未配置此策略设置，则脚本启动的弹出窗口和含标题和状态栏的窗口中包含的可能有害的操作将无法运行。 此区域中将启用此 Internet Explorer 安全功能，如进程的“脚本化 Windows 安全限制”功能控件设置所规定的那样。
  - 默认值：已禁用 
  
- **Internet Explorer 将文件上传到服务器时，Internet 区域包含本地路径**  </br>
  使用此策略设置，可控制用户通过 HTML 窗体上传文件时是否会发送本地路径信息。 如果发送本地路径信息，则无意中可能向服务器泄露部分信息。 例如，从用户桌面发送的文件可能包含用户名，作为路径的一部分。 如果启用此策略设置，则在用户通过 HTML 窗体上传文件时会发送路径信息。 如果禁用此策略设置，则在用户通过 HTML 窗体上传文件时删除路径信息。 如果不配置此策略设置，则用户可以在通过 HTML 窗体上传文件时选择是否发送路径信息。 默认情况下，发送路径信息。
  - **默认值**：已禁用 
  
- **Internet Explorer 在增强保护模式下禁用进程**  
  此策略设置确定在 64 位版本的 Windows 上以增强保护模式运行时，Internet Explorer 11 是使用 64 位进程（以获得更高安全性）还是使用 32 位进程（以获得更高兼容性）。 重要提示：使用 64 位进程时，某些 ActiveX 控件和工具栏可能不可用。 如果启用此策略设置，则在 64 位版本的 Windows 上以增强保护模式运行时，Internet Explorer 11 将使用 64 位选项卡进程。 如果禁用此策略设置，则在 64 位版本的 Windows 上以增强保护模式运行时，Internet Explorer 11 将使用 32 位选项卡进程。 如果未配置此策略设置，则用户可使用 Internet Explorer 设置启用或禁用此功能。 默认情况下，此功能处于禁用状态。
  - **默认值**：启用 
  
- **Internet Explorer 忽略证书错误**  </br>
  此策略设置可阻止用户忽略中断 Internet Explorer 浏览的安全套接字层/传输层安全性 (SSL/TLS) 证书错误（例如“已过期”，“撤消”或“名称不匹配”错误）。 如果启用此策略设置，则用户无法继续浏览。 如果禁用或未配置此策略设置，则用户可以选择忽略证书错误并继续浏览。
  - **默认值**：已禁用 
  
- **Internet Explorer Internet 区域加载 XAML 文件**  
  利用此策略设置，可管理 Extensible Application Markup Language (XAML) 文件的加载。 XAML 是基于 XML 的声明性标记语言，通常用于创建可充分利用 Windows Presentation Foundation 的丰富用户界面和图形。 如果启用此策略设置，并将下拉列表框设置为“启用”，则会自动在 Internet Explorer 中自动加载 XAML 文件。 用户无法更改此行为。 如果将下拉列表框设为“提示”，系统则会提示用户加载 XAML 文件。 如果禁用此策略设置，则不会在 Internet Explorer 中加载 XAML 文件。 用户无法更改此行为。 如果未配置此策略设置，则用户可以决定是否在 Internet Explorer 中加载 XAML 文件。
  - **默认值**：禁用 
  
- **Internet Explorer Internet 区域自动提示文件下载**  </br>
  此策略设置决定系统是否会就非用户启动的文件下载提示用户。 无论此设置如何，用户都将收到用户启动的下载的文件下载对话框。 如果启用此设置，用户将收到针对自动下载尝试的文件下载对话框。 如果禁用或未配置此设置，系统将阻止非用户启动的文件下载，并且用户将看到“通知”栏而非文件下载对话框。 然后，用户可以单击通知栏，允许文件显示下载提示。
  - **默认值**：启用  
  
- **Internet Explorer 受限制区域对潜在不安全文件的安全警告**  
  此策略设置控制在用户尝试打开可执行文件或其他潜在不安全文件（例如，使用“文件资源管理器”从 Intranet 文件共享中获取）时，是否出现“打开文件 - 安全警告”消息。 如果启用此策略设置并且将下拉框设置为“启用”，则打开这些文件时不显示安全警告。 如果将下拉框设置为“提示”，则打开文件之前显示安全警告。 如果禁用此策略设置，则无法打开这些文件。 如果未配置此策略设置，则用户可以配置计算机处理这些文件的方式。 默认情况下，这些文件在受限制区域中设置为阻止，在 Intranet 和本地计算机区域中设置为启用，在 Internet 和受信任区域中设置为提示。
  - **默认值**：禁用  
  
- **Internet Explorer Internet 区域跨站点脚本筛选器**  
  此策略控制跨站点脚本 (XSS) 筛选器是否检测和阻止跨站点脚本注入此区域中的网站。 如果启用此策略设置，则对此区域中的站点启用 XSS 筛选，并且 XSS 筛选尝试阻止跨站脚本注入。 如果禁用此策略设置，则对此区域中的站点禁用 XSS 筛选，并且 Internet Explorer 允许跨站点脚本注入。
  - **默认值**：启用 
  
- **Internet Explorer 回退到 SSL3**  
  利用此策略设置，可阻止 SSL 3.0 的不安全回退。 启用此策略后，当 TLS 1.0 或更高版本失败时，Internet Explorer 将尝试使用 SSL 3.0 或更低版本连接到站点。 建议禁用不安全回退，以防止中间人攻击。 此策略不会影响启用的安全协议。 如果禁用此策略，将使用系统默认值。
  - **默认值**：没有站点 
  
- **Internet Explorer 已锁定 Internet 区域的 SmartScreen**  
  此策略设置用于控制 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 如果启用此策略设置，则 SmartScreen 筛选器会扫描此区域中的页面来查找恶意内容。 如果禁用此策略设置，则 SmartScreen 筛选器不会扫描此区域中的页面来查找恶意内容。 如果未配置此策略设置，则用户可以选择 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 注意：在 Internet Explorer 7 中，此策略设置控制钓鱼网站筛选器是否扫描此区域中的页面来查找恶意内容。
  - **默认值**：启用 
  
- **Internet Explorer 受限制区域在 iFrame 中启动应用程序和文件**  
  利用此策略设置，可以管理是否可以运行应用程序以及是否可以从此区域中页面的 HTML 中的 IFRAME 引用下载文件。 如果启用此策略设置，则用户无需干预就可以从此区域中页面上的 IFRAME 运行应用程序和下载文件。 如果在下拉框中选择了“提示”，则会询问用户选择是否从此区域中页面上的 IFRAME 运行应用程序以及下载文件。 如果禁用此策略设置，则阻止用户在此区域中的页面上运行应用程序以及从 IFRAME 下载文件。 如果未配置此策略设置，则会阻止用户在此区域中的页面上运行应用程序以及从 IFRAME 下载文件。
  - **默认值**：禁用 
  
- **Internet Explorer 绕过 SmartScreen 中不常见文件的警告** 此策略设置确定用户是否可以绕过 SmartScreen 筛选器中的警告。 有关 Internet Explorer 用户通常不从 Internet 下载的可执行文件，SmartScreen 筛选器会警告用户。 如果启用此策略设置，则 SmartScreen 筛选器警告会阻止用户。 如果禁用或未配置此策略设置，则用户可以绕过 SmartScreen 筛选器警告。
  - **默认值**：已禁用  
  
- **Internet Explorer Internet 区域弹出窗口阻止程序**  
  利用此策略设置，可管理是否显示不需要的弹出窗口。 不会阻止最终用户单击链接时打开的弹出窗口。 如果启用此策略设置，将阻止显示大多数不需要的弹出窗口。 如果禁用此策略设置，则不会阻止显示弹出窗口。 如果未配置此策略设置，将阻止显示大多数不需要的弹出窗口。
  - **默认值**：启用  
  
- **Internet Explorer 进程一致的 MIME 处理**  
  Internet Explorer 包含封装其所附加的 HTML 元素的特定功能的动态二进制行为组件。 此策略设置控制是否阻止或允许二进制行为安全限制设置。 如果启用此策略设置，则阻止文件资源管理器和 Internet Explorer 进程的二进制行为。 如果禁用此策略设置，则允许文件资源管理器和 Internet Explorer 进程的二进制行为。 如果不配置此策略设置，则阻止文件资源管理器和 Internet Explorer 进程的二进制行为。
  - **默认值**：启用  
  
- **Internet Explorer 受限制区域 java 权限** 利用此策略设置，可以管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。
  - **默认值**：禁用 java  
    
  
- **Internet Explorer Active X 控件处于保护模式**  
  启用增强保护模式时，此策略设置可阻止 ActiveX 控件在保护模式下运行。 用户安装了与增强保护模式不兼容的 ActiveX 控件且网站试图加载该控件时，Internet Explorer 会通知用户并提供以常规保护模式运行网站的选项。 此策略设置禁用此通知，并强制所有网站以增强保护模式运行。 增强保护模式通过在 64 位版本的 Windows 上使用 64 位进程，提供更多的保护来防范恶意网站。 对于至少运行 Windows 8 的计算机，增强保护模式还限制 Internet Explorer 可从注册表和文件系统中进行读取的位置。 启用了增强保护模式，并且用户遇到试图加载与增强保护模式不兼容的 ActiveX 控件的网站时，Internet Explorer 会通知用户并为该特定网站提供禁用增强保护模式选项。 如果启用此策略设置，Internet Explorer 将不为用户提供禁用增强保护模式的选项。 所有保护模式的网站都将以增强保护模式运行。 如果禁用或未配置此策略设置，Internet Explorer 会通知用户，并提供以常规保护模式运行不兼容 ActiveX 控件的网站的选项。 此为默认行为。
  - **默认值**：已禁用  
  
- **Internet Explorer 受限制区域加载 XAML 文件**  
  利用此策略设置，可管理 Extensible Application Markup Language (XAML) 文件的加载。 XAML 是基于 XML 的声明性标记语言，通常用于创建可充分利用 Windows Presentation Foundation 的丰富用户界面和图形。 如果启用此策略设置，并将下拉列表框设置为“启用”，则会自动在 Internet Explorer 中自动加载 XAML 文件。 用户无法更改此行为。 如果将下拉列表框设为“提示”，系统则会提示用户加载 XAML 文件。 如果禁用此策略设置，则不会在 Internet Explorer 中加载 XAML 文件。 用户无法更改此行为。 如果未配置此策略设置，则用户可以决定是否在 Internet Explorer 中加载 XAML 文件。
  - **默认值**：禁用  
  
- **Internet Explorer 进程脚本化窗口的安全限制**  
  Internet Explorer 允许脚本以编程方式打开、重设大小以及重新定位各种类型的窗口。 Window 限制的安全功能可限制弹出窗口、禁止脚本显示用户看不到标题和状态栏的窗口，或混淆其他 Windows 的标题和状态栏。 如果启用此策略设置，则会限制所有进程的脚本化窗口。 如果禁用或不配置此策略设置，则不限制脚本化窗口。
  - **默认值**：启用   
  
- **Internet Explorer 受限制区域运行 Active X 控件和插件**  
  利用此策略设置，可以管理是否可以在指定区域的页面上运行 ActiveX 控件和插件。 如果启用此策略设置，控件和插件则无需用户干预即可运行。 如果在下拉列表框中选择“提示”，系统将询问用户选择是否允许控件或插件运行。 如果禁用此策略设置，则将阻止控件和插件运行。 如果不配置此策略设置，则将阻止控件和插件运行。
  - **默认值**：禁用  
  
- **Internet Explorer 受限制区域脚本化标记为安全脚本的 Active X 控件**  
  利用此策略设置，可管理标记为安全脚本的 ActiveX 控件是否可以与脚本交互。 如果启用此策略设置，则无需用户干预即可自动进行脚本交互。 如果在下拉列表框中选择“提示”，系统会询问用户选择是否允许脚本交互。 如果禁用此策略设置，则将阻止进行脚本交互。 如果未配置此策略设置，则将阻止进行脚本交互。
  - **默认值**：禁用  
  
- **Internet Explorer 受限制区域登录选项**  
  利用此策略设置，可以管理登录选项的设置。 如果启用此策略设置，则可以从以下登录选项中进行选择。 匿名登录以禁用 HTTP 身份验证，并仅为 Common Internet File System (CIFS) 协议使用来宾帐户。 提示输入用户名和密码，以询问用户的用户 ID 和密码。 查询用户后，这些值可以以无提示的方式用于会话的其余部分。 仅在 Intranet 区域中自动登录，以查询用户在其他区域中的用户 ID 和密码。 查询用户后，这些值可以以无提示的方式用于会话的其余部分。 使用当前用户名和密码自动登录，以便使用 Windows NT 质询响应（也称为 NTLM 身份验证）尝试登录。 如果服务器支持 Windows NT 质询响应，则登录将使用用户的网络用户名和密码进行登录。 如果服务器不支持 Windows NT 质询响应，则要求用户提供用户名和密码进行登录。 如果禁用此策略设置，则登录设置为仅在 Intranet 区域中自动登录。 如果不配置此策略设置，则将登录设置为提示输入用户名和密码。
  - **默认值**：Anonymous (匿名)  
  
- **Internet Explorer 受信任区域初始化和脚本化未标记为安全的 Active X 控件**  
  利用此策略设置，可管理未标记为安全的 ActiveX 控件。 如果启用此策略设置，则无需为不受信任的数据或脚本设置对象安全即可运行、带参数加载和脚本化 ActiveX 控件。 不建议使用此设置，除非是安全的托管区域。 此设置忽略“脚本化标记为可安全脚本化的 ActiveX 控件”选项，导致对不安全的和安全的控件均进行初始化和脚本化。 如果启用此策略设置并在下拉框中选择“提示”，则将询问用户是否允许带参数加载或脚本化控件。 如果禁用此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。 如果未配置此策略设置，系统会询问用户是否允许带参数加载或脚本化该控件。
  - **默认值**：禁用  
  
- **Internet Explorer 检查服务器证书吊销**  
  利用此策略设置，可以管理 Internet Explorer 是否将检查服务器证书的吊销状态。 证书已泄露或不再有效时，将吊销证书。此选项保护用户不向可能具有欺骗性或不安全的网站提交机密数据。 如果启用此策略设置，Internet Explorer 将检查以查看是否已吊销服务器证书。 如果禁用此策略设置，Internet Explorer 将不会检查服务器证书，查看是否已吊销该证书。 如果未配置此策略设置，Internet Explorer 将不会检查服务器证书，查看是否已吊销该证书。
  - **默认值**：启用 
  
- **Internet Explorer Internet 区域低权限站点**  
  使用此策略设置，可以管理来自低特权区域的网站（如受限制的站点）是否可以导航到此区域。 如果启用此策略设置，低权限区域的网站可在此区域中打开新窗口，或导航到此区域。 安全区域运行时将不具有由“区域提升保护”安全功能提供的额外一层安全性。 如果在下拉列表框中选择“提示”，则会在将要发生可能有风险的导航时向用户发出警告。 如果禁用此策略设置，将阻止可能有害的导航。 Internet Explorer 安全功能将在此区域中启用，如“区域提升保护”功能控件中所设置的那样。 如果未配置此策略设置，低权限区域的站点可在此区域中打开新窗口，或导航到此区域。
  - **默认值**：禁用  

- **Internet Explorer 受限制区域文件下载**  </br>
  利用此策略设置，可以管理是否允许从该区域下载文件。 此选项由包含下载链接的页面区域确定，而不是由传送文件的区域确定。 如果启用此策略设置，则可以从该区域下载文件。 如果禁用此策略设置，则阻止从该区域下载文件。 如果未配置此策略设置，则阻止从该区域下载文件。
  - **默认值**：禁用  
  
- **Internet Explorer Internet 区域运行使用验证码签名的 .NET Framework 相关组件**  
  利用此策略设置，可管理用验证码签名的 .NET 框架组件是否可以从 Internet Explorer 执行。 这些组件包括从对象标记中引用的托管控件和从链接中引用的托管可执行文件。 如果启用此策略设置，则 Internet Explorer 将执行已签名的托管组件。 如果在下拉框中选择“提示”，则 Internet Explorer 将提示用户确定是否执行签名的托管组件。 如果禁用此策略设置，则 Internet Explorer 不执行已签名的托管组件。 如果未配置此策略设置，则 Internet Explorer 不执行已签名的托管组件。
  - **默认值**：禁用  
  
- **Internet Explorer 阻止每个用户安装 Active X 控件**  </br>
  利用此策略设置，可阻止基于每个用户安装 ActiveX 控件。 如果启用此策略设置，则无法基于每个用户安装 ActiveX 控件。 如果禁用或未配置此策略设置，则可以基于每个用户安装 ActiveX 控件。
  - **默认值**：启用  
  
- **Internet Explorer 阻止管理 SmartScreen 筛选器**  </br>
  此策略设置阻止用户管理 SmartScreen 筛选器，如果已知所访问的网站试图通过“钓鱼”骗取个人信息，或已知含有恶意软件，则该筛选器向用户发出警告。 如果启用此策略设置，则系统不会提示用户打开 SmartScreen 筛选器。 不在筛选器允许列表上的所有网站地址都会自动发送给 Microsoft 而不提示用户。 如果禁用或未配置此策略设置，则系统会在首次运行体验过程中提示用户确定是否要打开 SmartScreen 筛选器。
  - 默认值：启用  
  
- **Internet Explorer 进程 MIME 探查安全功能**  
  此策略设置确定 Internet Explorer MIME 探查是否会阻止将某种类型的文件提升为更危险的文件类型。 如果启用此策略设置，则 MIME 探查决不会将某种类型的文件提升为更危险的文件类型。 如果禁用此策略设置，则 Internet Explorer 进程会允许 MIME 探查将某种类型的文件提升为更危险的文件类型。 如果未配置此策略设置，则 MIME 探查决不会将某种类型的文件提升为更危险的文件类型。
  - 默认值：启用  
  
- **Internet Explorer 受限区域下载已签名的 ActiveX 控件**  </br>
  利用此策略设置，可管理用户是否可以从此区域中的页面下载已签名的 ActiveX 控件。 如果启用此策略，则用户无需干预即可下载已签名的控件。 如果在下拉框中选择“提示”，则会询问用户是否下载由不受信任的发布者签名的控件。 将自动下载由受信任的发行者签名的代码。 如果禁用此策略设置，则无法下载已签名的控件。 如果未配置此策略设置，则会询问用户是否下载由不受信任的发行者签名的控件。 将自动下载由受信任的发行者签名的代码。
  - 默认值：禁用  
  
- **Internet Explorer 自动完成**  </br>
  此“自动完成”功能可以记忆和建议表单上的用户名和密码。 如果启用此设置，则用户无法更改“表单上的用户名和密码”或“提示我保存密码”。 将启用“表单上的用户名和密码”的“自动完成”功能。 必须确定是否选择“提示我保存密码”。 如果禁用此设置，则用户无法更改“表单上的用户名和密码”或“提示我保存密码”。 将关闭“表单上的用户名和密码”的“自动完成”功能。 用户也无法选择得到保存密码的提示。 如果未配置此设置，则用户有权利启用“表单上的用户名和密码”的“自动完成”和提示保存密码的选项。 若要显示此选项，请用户打开“Internet 选项”对话框，依次单击“内容”选项卡和“设置”按钮。
  - 默认值：禁用  
  
- **Internet Explorer internet 区域允许运行 VBscript**  </br>
  使用此策略设置，可确定 VBScript 是否可以在特定 Internet Explorer 区域的页面中运行。 如果启用此策略设置（默认），则还必须从“选项”框中选取以下选项之一：启用。 VBScript 在特定区域的页面上运行，无需任何交互。 提示。 系统提示员工是否允许 VBScript 在该区域中运行。 禁用。 阻止 VBScript 在该区域运行。 如果禁用或未配置此策略设置，则 VBScript 可以在指定区域运行，且无需任何交互
  - 默认值：禁用  
  
- **Internet Explorer 受限区域仅允许已批准的域使用 TDC ActiveX 控件**  </br>
  此策略设置控制是否允许用户在网站上运行 TDC ActiveX 控件。 如果启用此策略设置，则 TDC ActiveX 控件不会从此区域中的网站运行。 如果禁用此策略设置，TDC ActiveX 控件会从此区域中的所有站点运行。
  - 默认值：启用  
  
- **Internet Explorer 受信任区域不针对 ActiveX 控件运行反恶意软件**   </br>
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。
  - 默认值：已禁用 
  
- **Internet Explorer 本地计算机区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，则无法运行 Java 小程序。 如果未配置此策略设置，则权限设置为“安全级 - 中”。
  - 默认值：禁用 java 
  
- **Internet Explorer intranet 区域不针对 ActiveX 控件运行反恶意软件**  </br>
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。
  - 默认值：已禁用  

- **Internet Explorer 受限区域 Scriptlet**  
  使用此策略设置，可以管理用户是否可以运行 Scriptlet。 如果启用此策略设置，则用户可以运行 Scriptlet。 如果禁用此策略设置，则用户无法运行 Scriptlet。 如果未配置此策略设置，则用户可以启用或禁用 Scriptlet。
  - 默认值：已禁用  
  
- **Internet Explorer 进程通知栏**  </br>  
  使用此策略设置，可以管理在文件或代码的安装受限制时是否为 Internet Explorer 进程显示通知栏。 默认情况下，为 Internet Explorer 进程显示通知栏。 如果启用此策略设置，则为 Internet Explorer 进程显示通知栏。 如果禁用此策略设置，则不会为 Internet Explorer 进程显示通知栏。 如果未配置此策略设置，则为 Internet Explorer 进程显示通知栏。
  - 默认值：启用  
  
- **Internet Explorer internet 区域下载已签名的 ActiveX 控件**  </br>
  利用此策略设置，可管理用户是否可以从此区域中的页面下载已签名的 ActiveX 控件。 如果启用此策略，则用户无需干预即可下载已签名的控件。 如果在下拉框中选择“提示”，则会询问用户是否下载由不受信任的发布者签名的控件。 将自动下载由受信任的发行者签名的代码。 如果禁用此策略设置，则无法下载已签名的控件。 如果未配置此策略设置，则会询问用户是否下载由不受信任的发行者签名的控件。 将自动下载由受信任的发行者签名的代码。
  - 默认值：禁用  
  
- **Internet Explorer 受限区域智能屏幕**  
  此策略设置控制 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 如果启用此策略设置，则 SmartScreen 筛选器会扫描此区域中的页面来查找恶意内容。 如果禁用此策略设置，则 SmartScreen 筛选器不会扫描此区域中的页面来查找恶意内容。 如果未配置此策略设置，则用户可以选择 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 注意：在 Internet Explorer 7 中，此策略设置控制钓鱼网站筛选器是否扫描此区域中的页面来查找恶意内容。
  - **默认值**：启用  
  
- **Internet Explorer 删除过时 ActiveX 控件的“运行这一次”按钮**  </br>
  使用此策略设置，可以阻止用户查看，以及在 Internet Explorer 中运行特定的过时 ActiveX 控件。 如果启用此策略设置，则 Internet Explorer 阻止过时的 ActiveX 控件时显示的警告消息中不会向用户显示“运行这一次”按钮。 如果禁用或未配置此策略设置，则 Internet Explorer 阻止过时的 ActiveX 控件时显示的警告消息中会向用户显示“运行这一次”按钮。 单击此按钮允许用户运行一次过时的 ActiveX 控件。 有关详细信息，请参阅 Internet Explorer TechNet 库中的“过时的 ActiveX 控件”。
  - 默认值：启用 
  
- **Internet Explorer internet 区域在 iFrame 中启动应用程序和文件**  
  利用此策略设置，可管理是否可以从此区域中页面的 HTML 中的一个 IFRAME 引用运行应用程序和下载文件。 如果启用此策略设置，则用户无需干预就可以从此区域中页面上的 IFRAME 运行应用程序和下载文件。 如果在下拉框中选择了“提示”，则会询问用户选择是否从此区域中页面上的 IFRAME 运行应用程序以及下载文件。 如果禁用此策略设置，则会阻止用户从此区域中页面上的 IFRAME 运行应用程序以及下载文件。 如果未配置此策略设置，则会询问用户选择是否从此区域中页面上的 IFRAME 运行应用程序以及下载文件
  - 默认值：禁用 
  
- **Internet Explorer 受限区域跨不同域导航窗口和框架**  </br>
  当来源和目标位于不同的窗口时，此策略设置可用于设置用来将内容从一个域拖动到另一个域的选项。 如果启用此策略设置并单击“启用”，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。 如果启用此策略设置并单击“禁用”，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户无法更改此设置。 在 Internet Explorer 10 中，如果禁用或未配置此策略设置，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户可以在“Internet 选项”对话框中更改此设置。 在 Internet Explorer 9 及更早版本中，如果禁用或未配置此策略，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。
  - 默认值：禁用  
  
- **Internet Explorer internet 区域智能屏幕**  
  此策略设置控制 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 如果启用此策略设置，则 SmartScreen 筛选器会扫描此区域中的页面来查找恶意内容。 如果禁用此策略设置，则 SmartScreen 筛选器不会扫描此区域中的页面来查找恶意内容。 如果未配置此策略设置，则用户可以选择 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 注意：在 Internet Explorer 7 中，此策略设置控制钓鱼网站筛选器是否扫描此区域中的页面来查找恶意内容。
  - **默认值**：启用  
  
- **Internet Explorer 锁定受信任的区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。
  - **默认值**：禁用 java 
  
- **Internet Explorer 检查已下载程序的签名**  
  利用此策略设置，可管理 Internet Explorer 是否要在下载可执行程序之前检查用户计算机上的数字签名（用于标识已签名软件的发行者并验证是否未对其进行过修改或篡改）。 如果启用此策略设置，则在将可执行程序下载到用户计算机之前，Internet Explorer 会检查可执行程序的数字签名并显示其标识。 如果禁用此策略设置，则在将可执行程序下载到用户计算机之前，Internet Explorer 不会检查可执行程序的数字签名，也不显示其标识。 如果未配置此策略，则在将可执行程序下载到用户计算机之前，Internet Explorer 不会检查可执行程序的数字签名，也不显示其标识。
  - 默认值：启用  
  
- **Internet Explorer Web 浏览器控件的受限区域脚本编写**  
  此策略设置控制页面是否可以通过脚本控制嵌入的 WebBrowser 控件。 如果启用此策略设置，则允许脚本访问 WebBrowser 控件。 如果禁用此策略设置，则不允许脚本访问 WebBrowser 控件。 如果不配置此策略设置，则用户可以启用或禁用对 WebBrowser 控件的脚本访问。 默认情况下，只有在本地计算机和 Intranet 区域中才允许脚本访问 WebBrowser 控件。
  - **默认值**：已禁用  
  
- **Internet Explorer 受限区域跨站点脚本筛选**  
  此策略控制跨站点脚本 (XSS) 筛选是否会检测并阻止跨站点脚本注入此区域中的网站。 如果启用此策略设置，则对此区域中的站点启用 XSS 筛选，并且 XSS 筛选尝试阻止跨站脚本注入。 如果禁用此策略设置，则对此区域中的站点禁用 XSS 筛选，并且 Internet Explorer 允许跨站点脚本注入。
  - **默认值**：启用  
  
- **Internet Explorer 受限区域二进制文件和脚本行为**  
  使用此策略设置，可以管理动态二进制文件和脚本行为：用于为相应 HTML 元素封装特定功能的组件（组件附加到这些 HTML 元素）。 如果启用此策略设置，则二进制文件和脚本行为都可用。 如果在下拉框中选择了“管理员批准”，则只有在“二进制文件行为安全限制”策略下的“管理员批准的行为”中列出的行为才可用。 如果禁用此策略设置，除非应用程序已实现自定义安全管理器，否则二进制文件和脚本行为都不可用。 如果未配置此策略设置，除非应用程序已实现自定义安全管理器，否则二进制文件和脚本行为都不可用。
  - 默认值：禁用  
  
- **Internet Explorer 安全设置检查**  </br>
  此策略设置关闭安全设置检查功能，该功能检查 Internet Explorer 安全设置，以确定这些设置将 Internet Explorer 置于不安全状态的时间。 如果启用此策略设置，则关闭该功能。 如果禁用或未配置此策略设置，则启用该功能。
  - 默认值：启用  
  
- **Internet Explorer internet 区域对潜在不安全文件的安全警告**  
  此策略设置控制当用户尝试打开可执行文件或其他可能不安全的文件（例如，使用文件资源管理器从 Intranet 文件共享）时是否显示“打开文件 - 安全警告”消息。 如果启用此策略设置并且将下拉框设置为“启用”，则打开这些文件时不显示安全警告。 如果将下拉框设置为“提示”，则打开文件之前显示安全警告。 如果禁用此策略设置，则无法打开这些文件。 如果未配置此策略设置，则用户可以配置计算机处理这些文件的方式。 默认情况下，这些文件在受限制区域中设置为阻止，在 Intranet 和本地计算机区域中设置为启用，在 Internet 和受信任区域中设置为提示。
  - 默认值：提示  
  
- **Internet Explorer intranet 区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，则无法运行 Java 小程序。 如果未配置此策略设置，则权限设置为“安全级 - 中”。
  - 默认值：安全级 - 高 
  
- **Internet Explorer 阻止过时 ActiveX 控件**  </br>
  此策略设置可确定 Internet Explorer 是否会阻止特定的过时 ActiveX 控件。 过时的 ActiveX 控件在 Intranet 区域中不受阻止。 如果启用此策略，则 Internet Explorer 会停止阻止过时的 ActiveX 控件。 如果禁用或未配置此策略设置，则 Internet Explorer 会继续阻止特定的过时 ActiveX 控件。 有关详细信息，请参阅 Internet Explorer TechNet 库中的“过时的 ActiveX 控件”。
  - 默认值：启用  
  
- **Internet Explorer 受限区域弹出窗口阻止程序**  
  利用此策略设置，可管理是否显示不需要的弹出窗口。 不会阻止最终用户单击链接时打开的弹出窗口。 如果启用此策略设置，将阻止显示大多数不需要的弹出窗口。 如果禁用此策略设置，则不会阻止显示弹出窗口。 如果未配置此策略设置，将阻止显示大多数不需要的弹出窗口。
  - **默认值**：启用  
  
- **Internet Explorer 进程 MK 协议安全限制**  
  MK 协议安全限制策略设置通过阻止 MK 协议来减少攻击外围应用。 MK 协议上托管的资源将失败。 如果启用此策略设置，则将阻止文件资源管理器和 Internet Explorer 的 MK 协议，并且 MK 协议上托管的资源将失败。 如果禁用此策略设置，应用程序可以使用 MK 协议 API。 MK 协议上托管的资源将适用于文件资源管理器和 Internet Explorer 进程。 如果未配置此策略设置，则将阻止文件资源管理器和 Internet Explorer 的 MK 协议，并且 MK 协议上托管的资源将失败。
  - **默认值**：启用  
  
- **Internet Explorer 受信任区域 java 权限**  </br>
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则权限设置为“低安全性”。
  - **默认值**：高安全性  
  
- **Internet Explorer 受限区域的 java 小程序脚本编写**  
  利用此策略设置，可管理是否将小程序公开到该区域内的脚本中。 如果启用此策略设置，脚本可以在无需用户干预的情况下自动访问小程序。 如果在下拉列表框中选择“提示”，系统会询问用户选择是否允许脚本访问小程序。 如果禁用此策略设置，将阻止脚本访问小程序。 如果未配置此策略设置，将阻止脚本访问小程序。
  - **默认值**：禁用  
  
- **Internet Explorer 已锁定受限制区域 java 的权限**  </br>
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。
  - **默认值**：禁用 java 
  
- **Internet Explorer Tnternet 区域仅允许已批准的域使用 ActiveX 控件**  </br>
  此策略设置控制系统是否提示用户允许 ActiveX 控件在安装 ActiveX 控件的网站以外的网站上运行。 如果启用此策略设置，系统会在 ActiveX 控件可以在此区域中的网站上运行之前提示用户。 用户可以选择允许控件在当前站点或所有站点上运行。 如果禁用此策略设置，用户不会看到每个站点上的 ActiveX 提示，并且 ActiveX 控件可以在此区域中的所有站点上运行。
  - **默认值**：启用  
  
- **Internet Explorer 包括所有网络路径**  
  Internet Explorer 包括所有网络路径
  - **默认值**：已禁用 
  
- **Internet Explorer Internet 区域保护模式**  
  此策略设置允许启用保护模式。 保护模式通过减少 Internet Explorer 可在注册表和文件系统中写入的位置，帮助保护 Internet Explorer 不受攻击。 如果启用此策略设置，将启用保护模式。 用户无法关闭保护模式。 如果禁用此策略设置，将关闭保护模式。 用户无法启用保护模式。 如果未配置此策略设置，则用户可以启用或关闭保护模式。
  - **默认值**：启用 
  
- **Internet Explorer Intranet 区域初始化和脚本化未标记为安全的 ActiveX 控件**  
  利用此策略设置，可管理未标记为安全的 ActiveX 控件。 如果启用此策略设置，则无需为不受信任的数据或脚本设置对象安全即可运行、带参数加载和脚本化 ActiveX 控件。 不建议使用此设置，除非是安全的托管区域。 此设置忽略“脚本化标记为可安全脚本化的 ActiveX 控件”选项，导致对不安全的和安全的控件均进行初始化和脚本化。 如果启用此策略设置并在下拉框中选择“提示”，则将询问用户是否允许带参数加载或脚本化控件。 如果禁用此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。 如果未配置此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。
  - **默认值**：禁用 
  
- **Internet Explorer 已锁定受限制区域的 Smart Screen**  </br>
  此策略设置用于控制 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 如果启用此策略设置，则 SmartScreen 筛选器会扫描此区域中的页面来查找恶意内容。 如果禁用此策略设置，则 SmartScreen 筛选器不会扫描此区域中的页面来查找恶意内容。 如果未配置此策略设置，则用户可以选择 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 注意：在 Internet Explorer 7 中，此策略设置控制钓鱼网站筛选器是否扫描此区域中的页面来查找恶意内容。
  - **默认值**：启用  
  
- **Internet Explorer 故障检测**  
  利用此策略设置，可管理附加组件管理的故障检测功能。 如果启用此策略设置，Internet Explorer 中出现的故障将显示 Windows XP Professional Service Pack 1 及更早版本中出现的行为，即调用 Windows 错误报告。 Windows 错误报告的所有策略设置继续应用。 如果禁用或未配置此策略设置，则附加组件管理的故障检测功能将正常运行。
  - **默认值**：已禁用  
  
- **Internet Explorer internet 区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则权限设置为“高安全性”。
  - **默认值**：禁用 java  
  
- **Internet Explorer 受限制区域的活动脚本编制**  
  利用此策略设置，可管理区域中页面上的脚本代码是否运行。 如果启用此策略设置，则区域中页面上的脚本代码可自动运行。 如果在下拉列表框中选择“提示”，系统会询问用户选择是否允许区域中页面上的脚本代码运行。 如果禁用此策略设置，则会阻止区域中页面上的脚本代码运行。 如果未配置此策略设置，则会阻止区域中页面上的脚本代码运行。
  - 默认值：禁用  
  
- **Internet Explorer internet 区域登录选项**  
  利用此策略设置，可管理登录选项的设置。 如果启用此策略设置，则可以从下列登录选项中进行选择。 匿名登录，以禁用 HTTP 验证并只为通用 Internet 文件系统 (CIFS) 协议使用来宾帐户。 提示用户名和密码以询问用户的用户 ID 和密码。 询问用户后，可在会话的剩余阶段中自动使用这些值。 仅在 Intranet 区域中自动登录，以询问用户在其他区域中的用户 ID 和密码。 询问用户后，可在会话的剩余阶段中自动使用这些值。 用当前用户名和密码自动登录，以尝试使用 Windows NT 质询响应进行登录（也称为 NTLM 验证）。 如果服务器支持 Windows NT 质询响应，则登录使用用户的网络用户名和密码来登录。 如果服务器不支持 Windows NT 质询响应，则询问用户的用户名和密码。 如果禁用此策略设置，则登录设置为“仅在 Intranet 区域中自动登录”。 如果未配置此策略设置，则登录设置为“仅在 Intranet 区域中自动登录”。
  - 默认值：提示  
  
- **Internet Explorer 受限区域允许脚本运行**  </br>  
  使用此策略设置，可以管理是否可以从 Internet Explorer 中指定区域的页面运行 VBScript。 如果在下拉框中选择“启用”，则 VBScript 无须用户干预即可运行。 如果在下拉框中选择“提示”，则会询问用户选择是否允许 VBScript 运行。 如果在下拉框中选择“禁用”，则会阻止 VBScript 运行。 如果未配置或禁用此策略设置，则会阻止 VBScript 运行。
  - 默认值：禁用  
  
- **Internet Explorer internet 区域在多个窗口之间拖动不同域中的内容**  
  当来源和目标位于不同的窗口时，此策略设置可用于设置用来将内容从一个域拖动到另一个域的选项。 如果启用此策略设置并单击“启用”，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。 如果启用此策略设置并单击“禁用”，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户无法更改此设置。 在 Internet Explorer 10 中，如果禁用或未配置此策略设置，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户可以在“Internet 选项”对话框中更改此设置。 在 Internet Explorer 9 及更早版本中，如果禁用或未配置此策略，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。
  - 默认值：已禁用 
  
- **Internet Explorer intranet 区域初始化和脚本化未标记为安全的 ActiveX 控件**  
  利用此策略设置，可管理未标记为安全的 ActiveX 控件。 如果启用此策略设置，则无需为不受信任的数据或脚本设置对象安全即可运行、带参数加载和脚本化 ActiveX 控件。 不建议使用此设置，除非是安全的托管区域。 此设置忽略“脚本化标记为可安全脚本化的 ActiveX 控件”选项，导致对不安全的和安全的控件均进行初始化和脚本化。 如果启用此策略设置并在下拉框中选择“提示”，则将询问用户是否允许带参数加载或脚本化控件。 如果禁用此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。 如果未配置此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。
  - **默认值**：禁用 
  
- **Internet Explorer 下载附件**  
  此策略设置可阻止用户将源中的附件（文件附件）下载到用户的计算机。 如果启用此策略设置，则用户无法通过“源属性”页设置源同步引擎来下载附件。 开发人员无法通过源 API 更改下载设置。 如果禁用或未配置此策略设置，则用户可以通过“源属性”页设置源同步引擎来下载附件。 开发人员可以通过源 API 更改下载设置。
  - 默认值：已禁用  
  
- **Internet Explorer 受限区域下载未签名的 ActiveX 控件**  </br>
  利用此策略设置，可管理用户是否可以从此区域中下载未签名的 ActiveX 控件。 这样的代码有潜在危险，特别是在代码来自不受信任的区域的情况下。 如果启用此策略设置，则用户无需干预即可运行未签名的控件。 如果在下拉框中选择“提示”，则会询问用户选择是否允许运行未签名的控件。 如果禁用此策略设置，则用户无法运行未签名的控件。 如果未配置此策略设置，则用户无法运行未签名的控件。
  - 默认值：禁用  
  
- **Internet Explorer internet 区域在窗口内拖动不同域中的内容**  
  利用此策略设置，可管理用户是否可以从此区域中下载未签名的 ActiveX 控件。 这样的代码有潜在危险，特别是在代码来自不受信任的区域的情况下。 如果启用此策略设置，则用户无需干预即可运行未签名的控件。 如果在下拉框中选择“提示”，则会询问用户选择是否允许运行未签名的控件。 如果禁用此策略设置，则用户无法运行未签名的控件。 如果未配置此策略设置，则用户无法运行未签名的控件。
  - 默认值：已禁用  
  
- **Internet Explorer 进程限制 ActiveX 安装**  </br>
  此策略设置使托管 Web 浏览器控件的应用程序能够阻止 ActiveX 控件安装的自动提示。 如果启用此策略设置，则 Web 浏览器控件阻止所有进程的 ActiveX 控件安装的自动提示。 如果禁用或未配置此策略设置，则 Web 浏览器控件不会阻止所有进程的 ActiveX 控件安装的自动提示。
  - 默认值：启用  
  
- **Internet Explorer internet 区域 Scriptlet** 使用此策略设置，可以管理用户是否可以运行 Scriptlet。 如果启用此策略设置，则用户可以运行 Scriptlet。 如果禁用此策略设置，则用户无法运行 Scriptlet。 如果未配置此策略设置，则用户可以启用或禁用 Scriptlet。
  - 默认值：禁用  
  
- **Internet Explorer 受限区域拖放或复制和粘贴文件**  
  利用此策略设置，可管理用户是否可以从此区域中的一个源拖动文件或复制和粘贴文件。 如果启用此策略设置，则用户可以自动从此区域拖动文件或复制和粘贴文件。 如果在下拉框中选择“提示”，则会询问用户选择是否从该区域拖动或复制文件。 如果禁用此策略设置，则会阻止用户从该区域拖动文件或者复制和粘贴文件。 如果未配置此策略设置，则会询问用户选择是否从该区域拖动或复制文件。
  - 默认值：禁用  
  
- **Internet Explorer 签名无效的软件** </br>
  利用此策略设置，可管理即使在签名失效的情况下，用户是否仍然可以安装或运行软件（例如 ActiveX 控件和文件下载）。 签名无效可能表示有人篡改过文件。 如果启用此策略设置，则提示用户安装或运行带有失效签名的文件。 如果禁用此策略设置，则用户无法运行或安装带有无效签名的文件。 如果未配置此策略，则用户可以选择运行或安装带有无效签名的文件。
  - 默认值：已禁用  
  
- **Internet Explorer 受限区域通过脚本复制和粘贴** </br> 使用此策略设置，可以管理脚本是否可以在指定区域中执行剪贴板操作（例如，剪切、复制和粘贴）。 如果启用此策略设置，则脚本可以执行剪贴板操作。 如果在下拉框中选择“提示”，则会询问用户是否执行剪贴板操作。 如果禁用此策略设置，则脚本无法执行剪贴板操作。 如果未配置此策略设置，则脚本无法执行剪贴板操作。
  - 默认值：禁用  
  
- **Internet Explorer 受限区域在多个窗口之间拖动不同域中的内容**  
  当来源和目标位于不同的窗口时，此策略设置可用于设置用来将内容从一个域拖动到另一个域的选项。 如果启用此策略设置并单击“启用”，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。 如果启用此策略设置并单击“禁用”，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户无法更改此设置。 在 Internet Explorer 10 中，如果禁用或未配置此策略设置，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户可以在“Internet 选项”对话框中更改此设置。 在 Internet Explorer 9 及更早版本中，如果禁用或未配置此策略，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。
  - 默认值：已禁用  
  
- **Internet Explorer 用户添加站点**  
  阻止用户在安全区域添加或删除站点。 安全区域是一组具有相同安全级别的网站。 如果启用此策略，将禁用安全区域的站点管理设置。 （若要了解安全区域的站点管理设置，请在“Internet 选项”对话框中单击“安全”选项卡，然后单击“站点”按钮。）如果禁用或未配置此策略，则用户可以在“受信任的站点”和“受限制的站点”区域中添加或删除网站，还可以修改“本地 Intranet”区域的设置。 此策略阻止用户更改由管理员建立的安全区域的站点管理设置。 注意：“禁用安全页”策略（位于“\用户配置\管理模板\Windows 组件\Internet Explorer\Internet 控制面板”中）可将“安全”选项卡从界面上删除，它优先于此策略。 如果已启用该策略，则会忽略此策略。 另请参阅“安全区域：仅使用计算机设置”策略。
  - **默认值**：已禁用  
  
- **Internet Explorer internet 区域脚本启动窗口**  
  利用此策略设置，可以管理对由脚本启动的弹出窗口和包括标题栏和状态栏的窗口的限制。 如果启用此策略设置，则不会在此区域中应用 Windows 限制安全。 安全区域运行时将不具有此功能提供的额外一层安全性。 如果禁用此策略设置，则脚本启动的弹出窗口和含标题和状态栏的窗口中包含的可能有害的操作将无法运行。 此区域中将启用此 Internet Explorer 安全功能，如进程的“脚本化 Windows 安全限制”功能控件设置所规定的那样。 如果未配置此策略设置，则脚本启动的弹出窗口和含标题和状态栏的窗口中包含的可能有害的操作将无法运行。 此区域中将启用此 Internet Explorer 安全功能，如进程的“脚本化 Windows 安全限制”功能控件设置所规定的那样。
  - 默认值：已禁用  
  
- **Internet Explorer 安全区域仅使用计算机设置**  
  将安全区域信息应用于同一台计算机的所有用户。 安全区域是一组具有相同安全级别的网站。 如果启用此策略，则用户对安全区域所做的更改将应用于该计算机的所有用户。 如果禁用或未配置此策略，则同一台计算机的用户可以建立各自的安全区域设置。 此策略用于确保将安全区域设置统一地应用于同一台计算机，不会因用户的不同而产生差异。 另请参阅“安全区域：禁止用户更改策略”策略。
  - 默认值：启用  
  
- **Internet Explorer 锁定的本地计算机区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，则无法运行 Java 小程序。 如果未配置此策略设置，则会禁用 Java 小程序
  - 默认值：禁用 java 
  
- **Internet Explorer 受限区域不针对 ActiveX 控件运行反恶意软件**  </br>
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。
  - 默认值：已禁用  
  
- **Internet Explorer 受限区域运行用验证码签名的依赖于 .NET Framework 的组件**  
  利用此策略设置，可管理用验证码签名的 .NET 框架组件是否可以从 Internet Explorer 执行。 这些组件包括从对象标记中引用的托管控件和从链接中引用的托管可执行文件。 如果启用此策略设置，则 Internet Explorer 将执行已签名的托管组件。 如果在下拉框中选择“提示”，则 Internet Explorer 将提示用户确定是否执行签名的托管组件。 如果禁用此策略设置，则 Internet Explorer 不执行已签名的托管组件。 如果未配置此策略设置，则 Internet Explorer 不执行已签名的托管组件。
  - **默认值**：禁用  
  
- **Internet Explorer 受限区域访问数据源**  
  利用此策略设置，可管理 Internet Explorer 是否可以使用 Microsoft XML Parser (MSXML) 或 ActiveX 数据对象 (ADO) 访问其他安全区域的数据。 如果启用此策略设置，用户可以在区域中加载页面，该页面使用 MSXML 或 ADO 访问区域中其他站点的数据。 如果在下拉列表框中选择“提示”，将会提示用户选择是否允许在区域中加载页面，该页面使用 MSXML 或 ADO 访问区域中其他站点的数据。 如果禁用此策略设置，则用户无法在区域中加载使用 MSXML 或 ADO 访问区域中其他站点数据的页面。 如果不配置此策略设置，则用户无法在区域中加载使用 MSXML 或 ADO 访问区域中其他站点数据的页面。
  - 默认值：禁用 
  
- **Internet Explorer internet 区域不针对 ActiveX 控件运行反恶意软件**  </br>
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。
  - 默认值：已禁用  
  
- **Internet Explorer internet 区域通过脚本复制和粘贴** </br> 使用此策略设置，可以管理脚本是否可以在指定区域中执行剪贴板操作（例如，剪切、复制和粘贴）。 如果启用此策略设置，则脚本可以执行剪贴板操作。 如果在下拉框中选择“提示”，则会询问用户是否执行剪贴板操作。 如果禁用此策略设置，则脚本无法执行剪贴板操作。 如果未配置此策略设置，则脚本可执行剪贴板操作。
  - 默认值：禁用  
  
- **Internet Explorer 使用 ActiveX 安装程序服务**  </br>
  使用此策略设置，可以指定如何安装 ActiveX 控件。 如果启用此策略设置，则仅在提供 ActiveX 安装程序服务且配置为允许安装 ActiveX 控件的情况下安装 ActiveX 控件。 如果禁用或未配置此策略设置，则通过标准安装过程安装 ActiveX 控件（包括每用户控件）。
  - 默认值：启用  
  
- **Internet Explorer 进程防止区域提升**  
  Internet Explorer 对它打开的每一个网页施加限制。 这些限制取决于网页的位置（Internet、Intranet、本地计算机区域等）。 例如，本地计算机上的网页具有的安全限制最少，并且这些网页位于本地计算机区域中，这使本地计算机安全区域成为恶意用户的主要攻击目标。 如果启用此策略设置，则对于所有进程，将保护任何区域不会进行区域提升。 如果禁用或未配置此策略设置，则除了 Internet Explorer 或进程列表中的进程以外，其他进程都不会受到这种保护。
  - 默认值：启用  
  
- **Internet Explorer internet 区域下载未签名的 ActiveX 控件**  </br>
  利用此策略设置，可管理用户是否可以从此区域中下载未签名的 ActiveX 控件。 这样的代码有潜在危险，特别是在代码来自不受信任的区域的情况下。 如果启用此策略设置，则用户无需干预即可运行未签名的控件。 如果在下拉框中选择“提示”，则会询问用户选择是否允许运行未签名的控件。 如果禁用此策略设置，则用户无法运行未签名的控件。 如果未配置此策略设置，则用户无法运行未签名的控件。
  - 默认值：禁用  
  
- **Internet Explorer Internet 区域跨不同域导航窗口和框架**  </br>
  使用此策略设置，可以控制在不同域中打开窗口和框架的操作以及应用程序的访问。 如果启用此策略设置，用户可以打开其他域的窗口和框架，并访问其他域的应用程序。 如果在下拉列表框中选择“提示”，会询问用户是否允许窗口和框架访问其他域的应用程序。 如果启用此策略设置，则用户无法打开其他域的窗口和框架，并访问其他域的应用程序。 如果未配置此策略设置，则用户可以打开其他域的窗口和框架，并访问其他域的应用程序。
  - **默认值**：禁用  
  
- **Internet ExplorerI Internet 区域通过脚本更新状态栏**  
  使用此策略设置，可以控制是否允许脚本在区域中更新状态栏。 如果启用此策略设置，则允许脚本更新状态栏。 如果禁用或未配置此策略设置，则不允许脚本更新状态栏。
  - **默认值**：已禁用  
  
- **Internet Explorer 限制区域在文件上传到服务器时包含本地路径**  </br> 使用此策略设置，可控制用户通过 HTML 窗体上传文件时是否会发送本地路径信息。 如果发送本地路径信息，则无意中可能向服务器泄露部分信息。 例如，从用户桌面发送的文件可能包含用户名，作为路径的一部分。 如果启用此策略设置，则在用户通过 HTML 窗体上传文件时会发送路径信息。 如果禁用此策略设置，则在用户通过 HTML 窗体上传文件时删除路径信息。 如果不配置此策略设置，则用户可以在通过 HTML 窗体上传文件时选择是否发送路径信息。 默认情况下，发送路径信息。
  - **默认值**：已禁用  
  
- **Internet Explorer 进程限制文件下载**  </br> 使用此策略设置，托管 Web 浏览器控件的应用程序能够阻止自动提示非用户发起的文件下载。 如果启用此策略设置，Web 浏览器控件将针对所有进程，阻止自动提示非用户发起的文件下载。 如果禁用此策略设置，Web 浏览器控件不会针对所有进程，阻止自动提示非用户发起的文件下载。
  - **默认值**：启用  
  
- **Internet Explorer 限制区域仅允许已批准的域使用 ActiveX 控件**  </br>
  此策略设置控制系统是否提示用户允许 ActiveX 控件在安装 ActiveX 控件的网站以外的网站上运行。 如果启用此策略设置，系统会在 ActiveX 控件可以在此区域中的网站上运行之前提示用户。 用户可以选择允许控件在当前站点或所有站点上运行。 如果禁用此策略设置，用户不会看到每个站点上的 ActiveX 提示，并且 ActiveX 控件可以在此区域中的所有站点上运行。
  - **默认值**：启用  
  
- **Internet Explorer 限制区域对非标记为安全的 Active X 控件进行初始化和编制脚本**  
  利用此策略设置，可管理未标记为安全的 ActiveX 控件。 如果启用此策略设置，则无需为不受信任的数据或脚本设置对象安全即可运行、带参数加载和脚本化 ActiveX 控件。 不建议使用此设置，除非是安全的托管区域。 此设置忽略“脚本化标记为可安全脚本化的 ActiveX 控件”选项，导致对不安全的和安全的控件均进行初始化和脚本化。 如果启用此策略设置并在下拉框中选择“提示”，则将询问用户是否允许带参数加载或脚本化控件。 如果禁用此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。 如果未配置此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。
  - **默认值**：禁用  
  
- **Internet Explorer 用户更改策略**  
    防止用户更改安全区域设置。 安全区域是一组安全级别相同的网站。 如果启用此策略，将禁用 Internet 选项对话框中“安全”选项卡上的“自定义级别”和安全级别滑块。 如果禁用或不配置此策略，用户可以更改安全区域的设置。 此策略可防止用户更改管理员创建的安全区域设置。 注意：“禁用安全页”策略（位于 \用户配置\管理模板\Windows 组件\Internet Explorer\Internet 控制面板）优先于此策略，前者从控制面板的 Internet Explorer 中删除“安全”选项卡。 如果启用前者，则忽略此策略。 另请参阅“安全区域：仅使用计算机设置”策略。
    - **默认值**：已禁用  
  
- **Internet Explorer 限制区域保护模式**  
  此策略设置允许启用保护模式。 保护模式通过减少 Internet Explorer 可在注册表和文件系统中写入的位置，帮助保护 Internet Explorer 不受攻击。 如果启用此策略设置，将启用保护模式。 用户无法关闭保护模式。 如果禁用此策略设置，将关闭保护模式。 用户无法启用保护模式。 如果未配置此策略设置，则用户可以启用或关闭保护模式。
  - **默认值**：启用  
  
- **Internet Explorer Internet 区域用户数据暂留**  
  使用此策略设置，可以管理后列位置中的信息保存：浏览器的历史记录、收藏夹、XML 存储或保存到磁盘的网页。 如果已适当配置此策略设置，则当用户返回暂留页面时，可还原页面的状态。 如果启用此策略设置，则用户可以在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。 如果禁用此策略设置，则用户无法在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。 如果未配置此策略设置，则用户可以在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。
  - **默认值**：已禁用  
  
- **Internet Explorer Internet 区域 Web 浏览器控件脚本编写**  
 
  此策略设置决定页面是否可以通过脚本控制嵌入的 WebBrowser 控件。 如果启用此策略设置，则允许脚本访问 WebBrowser 控件。 如果禁用此策略设置，则不允许脚本访问 WebBrowser 控件。 如果不配置此策略设置，则用户可以启用或禁用对 WebBrowser 控件的脚本访问。 默认情况下，只有在本地计算机和 Intranet 区域中才允许脚本访问 WebBrowser 控件。
  - **默认值**：已禁用  
  
- **Internet Explorer 限制区域用户数据暂留**  
    使用此策略设置，可以管理后列位置中的信息保存：浏览器的历史记录、收藏夹、XML 存储或保存到磁盘的网页。 如果已适当配置此策略设置，则当用户返回暂留页面时，可还原页面的状态。 如果启用此策略设置，则用户可以在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。 如果禁用此策略设置，则用户无法在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。 如果未配置此策略设置，则用户无法在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。  
  - **默认值**：已禁用  
  
- **Internet Explorer 锁定 Intranet 区域 Java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。
  - **默认值**：禁用 Java  
  
- **Internet Explorer 增强保护模式**  
  增强保护模式通过在 64 位版本的 Windows 上使用 64 位进程，提供更多的保护来防范恶意网站。 对于至少运行 Windows 8 的计算机，增强保护模式还限制 Internet Explorer 可从注册表和文件系统中进行读取的位置。 如果启用此策略设置，将启用增强保护模式。 已启用保护模式的任何区域都将使用增强保护模式。 用户无法禁用增强保护模式。 如果禁用此策略设置，将关闭增强保护模式。 任何已启用“保护模式”的区域都将使用 Internet Explorer 7 中为 Windows Vista 引入的保护模式版本。 如果未配置此策略，用户将能够在“Internet 选项”对话框的“高级”选项卡上启用或禁用增强保护模式。
  - **默认值**：启用  
  
- **Internet Explorer 绕过 SmartScreen 警告**  
  此策略设置确定用户是否可绕过 SmartScreen 筛选器发出的警告。 有关 Internet Explorer 用户通常不从 Internet 下载的可执行文件，SmartScreen 筛选器会警告用户。 如果启用此策略设置，则 SmartScreen 筛选器警告会阻止用户。 如果禁用或未配置此策略设置，则用户可以绕过 SmartScreen 筛选器警告。
  - **默认值**：已禁用  
  
- **Internet Explorer 受限制区域的 meta 刷新**  
  如果网页的创建者使用 Meta 刷新设置（标记）将浏览器重定向到其他网页，则可通过此策略设置管理是否可以将用户的浏览器重定向到其他网页。 如果启用此策略设置，则可将加载包含活动 Meta 刷新设置页面的用户的浏览器重定向到其他网页。 如果禁用此策略设置，则无法将加载包含活动 Meta 刷新设置页面的用户的浏览器重定向到其他网页。 如果未配置此策略设置，则无法将加载包含活动 Meta 刷新设置页面的用户的浏览器重定向到其他网页。
  - **默认值**：已禁用  
  
## <a name="local-policies-security-options"></a>本地策略安全选项
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions)（策略 CSP - LocalPoliciesSecurityOptions）。 

- **限制对命名管道和共享的匿名访问**  
  启用该选项后，此安全设置会将对共享和管道的匿名访问限制为以下内容的设置：(1) 可以匿名访问的命名管道 (2) 可以匿名访问的共享
  - **默认值**：是  
  
- **基于 NTLM SSP 的服务器的最低会话安全性**  
  此安全设置允许服务器要求对 128 位加密和/或 NTLMv2 会话安全性进行协商。 这些值取决于 LAN Manager 身份验证级别安全设置值。 选项包括：需要 NTLMv2 会话安全性：如果未协商消息完整性，则连接将失败。 需要 128 位加密。 如果未协商强加密（128 位），则连接将失败。
  - **默认值**：需要 NTLM V2 和 128 位加密  
  
- **激活屏幕保护程序前锁屏界面保持不活动状态的分钟数**  
  Windows 会注意登录会话的非活动；如果非活动时间量超过非活动限制，则屏幕保护程序将运行，从而锁定会话。
  - **默认值**：15
  
- **需要客户端始终对通信进行数字签名** 此安全设置确定是否必须对域成员发起的所有安全通道流量进行签名或加密。 当计算机加入域时，将创建计算机帐户。 稍后，当系统启动时，将使用计算机帐户密码为其域创建具有域控制器的安全通道。 此安全通道用于执行 NTLM 传递身份验证、LSA SID/名称查找等操作。此设置确定由域成员发起的所有安全通道流量是否满足最低安全要求。 具体而言，确定是否必须对域成员发起的所有安全通道流量进行签名或加密。 如果启用此策略，除非协商对所有安全通道流量的签名或加密，否则将不会建立安全通道。 如果禁用此策略，则将与域控制器协商所有安全通道流量的加密和签名，在这种情况下，签名和加密级别取决于域控制器的版本和以下两种策略的设置：域成员：对安全通道数据进行数字加密（如果可能）域成员：对安全通道数据进行数字签名（如果可能）
  - **默认值**：是
  
- **身份验证级别**  
  此安全设置确定用于网络登录的质询/响应身份验证协议。 此选择会影响客户端使用的身份验证协议级别、协商的会话安全性级别以及服务器接受的身份验证级别，如下所示：发送 LM 和 NTLM 响应：客户端使用 LM 和 NTLM 身份验证，从不使用 NTLMv2 会话安全性；域控制器接受 LM、NTLM 和 NTLMv2 身份验证。 发送 LM 和 NTLM - 如果进行协商，请使用 NTLMv2 会话安全性：客户端使用 LM 和 NTLM 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器接受 LM、NTLM 和 NTLMv2 身份验证。 仅发送 NTLM 响应：客户端仅使用 NTLM 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器接受 LM、NTLM 和 NTLMv2 身份验证。 仅发送 NTLMv2 响应：客户端仅使用 NTLMv2 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器接受 LM、NTLM 和 NTLMv2 身份验证。 仅发送 NTLMv2 响应或拒绝 LM：客户端仅使用 NTLMv2 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器拒绝 LM（只接受 NTLM 和 NTLMv2 身份验证）。 仅发送 NTLMv2 响应或拒绝 LM 和 NTLM：客户端仅使用 NTLMv2 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器拒绝 LM 和 NTLM（只接受 NTLMv2 身份验证）。
  - **默认值**：仅发送 NTLMv2 响应。 拒绝 LM 和 NTLM
  
- **阻止客户端向第三方 SMB 服务器发送未加密的密码**  
  如果启用此安全设置，则允许服务器消息块 (SMB) 重定向程序将明文密码发送给在身份验证期间不支持密码加密的非 Microsoft SMB 服务器。 发送未加密的密码是一种安全风险。
  - **默认值**：是
  
- **禁用服务器始终进行数字签名通信**  
  此安全设置确定 SMB 客户端是否尝试协商进行 SMB 数据包签名。 服务器消息块 (SMB) 协议为 Microsoft 文件和打印共享以及许多其他网络操作（如远程 Windows 管理）提供了基础。 为了防止在传输中修改 SMB 数据包的中间人攻击，SMB 协议支持对 SMB 数据包进行数字签名。 此策略设置确定 SMB 客户端组件在连接到 SMB 服务器时是否尝试协商 SMB 数据包签名。 如果启用此设置，Microsoft 网络客户端将请求服务器在会话设置时执行 SMB 数据包签名。 如果在服务器上启用了数据包签名，则会协商数据包签名。 如果禁用此策略，则 SMB 客户端绝不会协商 SMB 数据包签名。
  - **默认值**：是
  
- **管理员提升权限提示行为**  
  此策略设置控制针对管理员的提升权限提示的行为。 选项包括：0 - 不提示，直接提升权限：允许特权帐户执行不需要同意或凭据就进行提升的操作。 注意：此选项仅用在大多数受限制的环境中。 1 - 在安全桌面上提示提供凭据：当某个操作需要特权提升时，系统将在安全桌面上提示用户输入有权限的用户名和密码。 如果用户输入有效的凭据，则该操作将使用用户的最高可用权限继续执行。 2 - 在安全桌面上提示同意：当某个操作需要特权提升时，系统将在安全桌面上提示用户选择“允许”或“拒绝”。 如果用户选择“允许”，则该操作将使用用户的最高可用权限继续执行。 3 - 提示提供凭据：当某个操作需要特权提升时，系统将提示用户输入管理用户名和密码。 如果用户输入有效的凭据，则该操作将使用适用的权限继续执行。 4 - 同意提示：当某个操作需要特权提升时，系统将提示用户选择“允许”或“拒绝”。 如果用户选择“允许”，则该操作将使用用户的最高可用权限继续执行。 5 - 非 Windows 二进制文件的同意提示：（默认值）当非 Microsoft 应用程序的某个操作需要特权提升时，系统将在安全桌面上提示用户选择“允许”或“拒绝”。 如果用户选择“允许”，则该操作将使用用户的最高可用权限继续执行
  - **默认值**：在安全桌面上提示同意
  
- **基于 NTLM SSP 的客户端的最低会话安全性**  
  此安全设置允许客户端要求对 128 位加密和/或 NTLMv2 会话安全性进行协商。 这些值取决于 LAN Manager 身份验证级别安全设置值。 选项包括：需要 NTLMv2 会话安全性：如果未协商 NTLMv 2 协议，则连接将失败。 需要 128 位加密：如果未协商强加密（128 位），则连接将失败。
  - **默认值**：需要 NTLM V2 128 加密
  
- **智能卡移除行为**  
  此安全设置确定从智能卡读卡器中取下登录用户的智能卡时发生的情况。 选项包括：无操作；锁定工作站；强制注销；如果是远程桌面服务会话，则断开连接。如果在此策略的“属性”对话框中单击“锁定工作站”，则取下智能卡时将锁定工作站，用户可离开该区域，随身携带智能卡，并仍可维护受保护的会话。 如果单击此策略的“属性”对话框中的“强制注销”，则在取下智能卡时将自动注销用户。 如果单击“如果是远程桌面服务会话，则断开连接”，则取下智能卡将断开会话，但不会注销用户。 用户可通过该选项稍后插入智能卡并恢复会话，或者在另一台配备智能卡读卡器的计算机上恢复会话，而无需再次登录。 如果是本地会话，则此策略与“锁定工作站”的功能相同。
  - **默认值**：锁定工作站
  
- **阻止匿名枚举软件资产管理帐户和共享**  
  此安全设置确定是否允许匿名枚举软件资产管理帐户和共享。 Windows 允许匿名用户执行某些操作，例如枚举域帐户和网络共享的名称。 该操作非常方便，例如，管理员想要授予对不维护相互信任的受信任域中的用户的访问权限。 如果不希望允许匿名枚举软件资产管理帐户和共享，请启用此策略。
  - **默认值**：是
  
- **用空白密码阻止远程登录**  
  此安全设置确定没有密码保护的本地帐户是否可用于从物理计算机控制台以外的位置登录。 如果启用该设置，没有密码保护的本地帐户将仅能够在计算机的键盘上登录。 警告：物理上不在安全位置的计算机应始终对所有本地用户帐户强制实施强密码策略。 否则，任何对计算机具有物理访问权限的人都可以使用没有密码的用户帐户登录。 这对于便携式计算机尤其重要。 如果将此安全策略应用于 Everyone 组，则没有人能够通过远程桌面服务登录。 此设置不影响使用域帐户进行登录。 使用远程交互登录的应用程序可以绕过此设置。
  - **默认值**：是
  
- **标准用户提升权限提示行为**  
  此策略设置控制标准用户的提升权限提示行为。 0 - 自动拒绝提升请求：当某个操作需要特权提升时，将显示可配置的访问被拒错误消息。 以标准用户身份运行桌面的企业可以选择此设置来减少技术支持呼叫次数。 1 - 在安全桌面上提示提供凭据：当某个操作需要特权提升时，系统将在安全桌面上提示用户输入不同的用户名和密码。 如果用户输入有效的凭据，则该操作将使用适用的权限继续执行。 3（默认）- 提示提供凭据：当某个操作需要特权提升时，系统将提示用户输入管理用户名和密码。 如果用户输入有效的凭据，则该操作将使用适用的权限继续执行。
  - **默认值**：自动拒绝提升请求
  
- **需要管理员的管理员批准模式**  
  此策略设置控制计算机的所有用户帐户控制 (UAC) 策略设置的行为。 如果您更改此策略设置，则必须重新启动计算机。 选项包括：0 - 禁用：禁用管理员批准模式以及所有相关的 UAC 策略设置。 注意：如果禁用此策略设置，则安全中心将通知您操作系统的整体安全性已降低。 1 - 启用：（默认）启用管理员批准模式。 必须启用此策略，并且还必须对相关的 UAC 策略设置进行了适当设定，才能允许内置 Administrator 帐户以及所有其他属于管理员组成员的用户在管理员批准模式下运行。
  - **默认值**：是
  
- **阻止匿名枚举软件资产管理帐户**  
  此安全设置确定授予匿名连接到计算机的附加权限。 Windows 允许匿名用户执行某些操作，例如枚举域帐户和网络共享的名称。 该操作非常方便，例如，管理员想要授予对不维护相互信任的受信任域中的用户的访问权限。 此安全选项允许对匿名连接设置以下附加限制：已启用：不允许枚举软件资产管理帐户。 此选项将资源的安全权限中的 Everyone 替换为经过身份验证的用户。 已禁用：没有其他限制。 依赖于默认权限。 工作站上的默认值：已启用。 服务器上的默认值：已启用。
  - **默认值**：是
  
- **允许远程调用安全帐户管理器**  
  此策略设置可以将远程 rpc 连接限制为软件资产管理。 如果未选中该设置，将使用默认安全描述符。
  - **默认值**：O:BAG:BAD:(A;;RC;;;BA)

- **使用管理员批准模式**  
  此策略设置控制内置 Administrator 帐户的管理员批准模式行为。 选项包括：• 启用：内置 Administrator 帐户使用管理员批准模式。 默认情况下，任何需要提升权限的操作都将提示用户批准该操作。 • 禁用：（默认值）内置管理员帐户使用完全管理权限运行所有应用程序。
  - **默认值**：是
  
- **允许 UI 访问安全位置的应用程序**  
  此策略控制用户界面辅助功能（UIAccess 或 UIA）程序是否可以自动禁用标准用户使用提升权限提示的安全桌面。 已启用：UIA 程序（包括 Windows 远程协助）自动禁用用于提升权限提示的安全桌面。 如果不禁用“用户帐户控制：提示提升权限时切换到安全桌面”策略设置，则会在交互式用户桌面而不是安全桌面上出现提示。 已禁用：（默认值）安全桌面只能由交互式桌面的用户禁用，或通过禁用“用户帐户控制：提示提升权限时切换到安全桌面”策略设置来禁用。
  - **默认值**：是

- **检测应用程序安装和提示提升权限**  
  此策略设置控制计算机应用程序安装检测的行为。 选项包括：已启用：（默认值）当检测到某个应用程序安装包需要特权提升时，系统将提示用户输入管理用户名和密码。 如果用户输入有效的凭据，则该操作将使用适用的权限继续执行。 已禁用：不检测应用程序安装包和提示提升权限。 运行标准用户桌面并使用组策略软件安装或系统管理服务器 (SMS) 等委派安装技术的企业应该禁用此策略设置。 在这种情况下，安装程序检测是没有必要的。
  - **默认值**：是
  
- **在下一次更改密码时不存储 LAN 管理器哈希值**  
  此安全设置确定在下次更改密码时是否存储新密码的 LAN Manager (LM) 哈希值。 与更强大的加密 Windows NT 哈希相比，LM 哈希相对较弱且容易受到攻击。 由于 LM 哈希存储在安全数据库中的本地计算机上，如果安全数据库受到攻击，可能会泄漏密码。
  - **默认值**：是

- **将文件和注册表写入错误虚拟化到每用户位置**  
  此策略设置控制应用程序写入失败是否重定向到定义的注册表和文件系统位置。 此策略设置将缓和以管理员身份运行的应用程序，并将运行时应用程序数据写入 %ProgramFiles%、%Windir%、%Windir%\system32 或 HKLM\Software。
  - **默认值**：是

## <a name="ms-security-guide"></a>MS 安全指南  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide)（策略 CSP - MSSecurityGuide）。  

- **在网络登录时将 UAC 限制应用于本地帐户**  
    - **默认值**：启用
  
- **SMB v1 客户端驱动程序启动配置**  
  - **默认值**：已禁用的驱动程序
  
- **SMB v1 服务器**  
  - **默认值**：已禁用
  
- **摘要式身份验证**  
  - **默认值**：已禁用
  
- **结构化的异常处理覆盖保护**  
  - **默认值**：启用
  
## <a name="mss-legacy"></a>MSS 旧版  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy)（策略 CSP - MSSLegacy）。  

- **网络 IP 源路由保护级别**  
  - **默认值**：最高级别的保护 
  
- **网络忽略除 WINS 服务器之外的 NetBIOS 名称发布的请求**  
  - **默认值**：启用
  
- **网络 IPv6 源路由保护级别**  
  - **默认值**：最高级别的保护

- **网络 ICMP 重定向替代生成的 OSPF**  
  - **默认值**：已禁用
  
## <a name="power"></a>电源  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power)（策略 CSP - 电源）。  

- **接通电源时需要密码才能唤醒**  
  此策略设置指定在系统从睡眠状态恢复时是否提示用户输入密码。 如果启用或未配置此策略设置，系统从睡眠状态恢复时将提示用户输入密码。 如果禁用此策略设置，系统从睡眠状态恢复时不会提示用户输入密码。
  - **默认值**：启用
  
- **电池处于睡眠时的待机状态**  
  此策略设置控制计算机进入睡眠状态时是否允许 Windows 使用待机状态。 如果启用或不配置此策略设置，则 Windows 使用待机状态，将计算机置于睡眠状态。 如果禁用此策略设置，则不允许使用待机状态 (S1-S3)。
  - **默认值**：已禁用
  
- **计算机接通电源且处于睡眠状态时的待机状态**  
  此策略设置控制计算机进入睡眠状态时是否允许 Windows 使用待机状态。 如果启用或不配置此策略设置，则 Windows 使用待机状态，将计算机置于睡眠状态。 如果禁用此策略设置，则不允许使用待机状态 (S1-S3)。
  - **默认值**：已禁用
  
- **使用电池时需要密码才能唤醒**  
  此策略设置指定在系统从睡眠状态恢复时是否提示用户输入密码。 如果启用或未配置此策略设置，系统从睡眠状态恢复时将提示用户输入密码。 如果禁用此策略设置，系统从睡眠状态恢复时不会提示用户输入密码。
  - **默认值**：启用
  
## <a name="remote-desktop-services"></a>远程桌面服务  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices)。  

- **阻止密码保存**  
  控制是否可以通过远程桌面连接在此计算机上保存密码。 如果启用此设置，将禁用远程桌面连接中的密码保存复选框，且用户不再能够保存密码。 当用户使用远程桌面连接打开 RDP 文件并保存其设置时，此前 RDP 文件中存在的所有密码将被删除。 如果禁用此设置，或不对其进行配置，则用户将能够使用远程桌面连接保存密码。
  - **默认值**：启用
  
- **安全 RPC 通信**  
  指定远程桌面会话主机服务器是要求与所有客户端建立安全 RPC 通信，还是允许存在不安全的通信。 可以使用此设置，通过仅允许经身份验证和加密的请求，增强与客户端 RPC 通信的安全性。 如果状态设置为“启用”，远程桌面服务会接受来自支持安全请求的 RPC 客户端的请求，且不允许与不受信任的客户端建立不安全通信。 如果状态设置为“禁用”，远程桌面服务将始终要求保障所有 RPC 通信的安全性。 但是，允许不响应请求的 RPC 客户端存在不安全的通信。 如果状态设置为“未配置”，则允许不安全的通信。 注意：RPC 接口用于管理和配置远程桌面服务。
  - **默认值**：启用
  
- **阻止驱动器重定向**  
  此策略设置指定是否阻止映射远程桌面服务会话中的客户端驱动器（驱动器重定向）。 默认情况下，RD 会话主机服务器将在连接时自动映射客户端驱动器。 映射的驱动器将显示在文件资源管理器或计算机中的会话文件夹树中，并采用\<计算机名称>上的\<驱动器号>。 此策略设置可用于重写此行为。 如果启用此策略设置，则远程桌面服务会话中不允许客户端驱动器重定向，并且运行 Windows 2003、Windows 8 和 Windows XP 的计算机上不允许剪贴板文件副本重定向。 如果禁用此策略设置，则始终允许客户端驱动器重定向。 此外，如果允许剪贴板重定向，则始终允许剪贴板文件副本重定向。 如果不配置此策略设置，则不会在组策略级别指定客户端驱动器重定向和剪贴板文件副本重定向。
  - **默认值**：启用
  
- **连接时提示输入密码**  
  此策略设置指定远程桌面服务是否始终提示在连接时输入客户端密码。 可使用此设置，对登录远程桌面服务的用户强制实施密码提示，即便他们已在远程桌面连接客户端中提供密码也是如此。 默认情况下，远程桌面服务允许用户通过在远程桌面连接客户端中输入密码自动登录。 如果启用此策略设置，则用户无法通过在远程桌面连接客户端中提供其密码自动登录到远程桌面服务。 系统将提示输入密码进行登录。 如果禁用此策略设置，则用户始终可以通过在远程桌面连接客户端中提供其密码自动登录到远程桌面服务。 如果不配置此策略设置，则不会在组策略级别指定自动登录。 
  - **默认值**：启用
  
- **远程桌面服务客户端连接加密级别**  
  指定是否需要使用特定的加密级别，在远程桌面协议 (RDP) 连接期间保护客户端计算机与 RD 会话主机服务器之间的通信。 此策略仅当使用本机 RDP 加密时才适用。 但不建议使用本机 RDP 加密（相对于 SSL 加密）。 此策略不适用于 SSL 加密。 如果启用此策略设置，则远程连接期间客户端和 RD 会话主机服务器之间的所有通信都必须使用此设置中指定的加密方法。 默认情况下，加密级别设置为“高”。 可采用以下加密方法：  
  - *高*：“高”设置使用强 128 位加密对往返客户端与服务器之间的数据进行加密。 在仅包含 128 位客户端（例如，运行远程桌面连接的客户端）的环境中使用此加密级别。 不支持此加密级别的客户端无法连接到 RD 会话主机服务器。  
  - *客户端兼容*：“客户端兼容”设置采用客户端支持的最大密钥强度对客户端和服务器之间的数据进行加密。 在包含不支持 128 位加密的客户端的环境中使用此加密级别。  
  - *低*：“低”设置仅对从客户端发送到服务器的数据使用 56 位加密。  
  
  如果禁用或不配置此设置，则不会通过组策略强制执行用于远程连接到 RD 会话主机服务器的加密级别。 可以通过系统加密配置重要的 FIPS 符合性。 将 FIPS 兼容算法用于“组策略”（位于计算机配置\Windows 设置\安全设置\本地策略\安全选项）中的加密、哈希和签名设置。FIPS 兼容设置通过美国联邦信息处理标准 (FIPS) 140 加密算法，使用 Microsoft 加密模块，对往返发送于客户端与服务器之间的数据进行加密和解密。 如果客户端和 RD 会话主机服务器之间的通信需要最高级别加密，则使用此加密级别。
  - **默认值**：高
  
## <a name="remote-management"></a>远程管理  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement)。  

- **阻止存储运行方式凭据**  
  客户端基本身份验证
  - **默认值**：启用
  
- **基本身份验证**  
  使用此策略设置，可以控制 Windows 远程管理 (WinRM) 服务是否接受来自远程客户端的基本身份验证。 如果启用此策略设置，则 WinRM 服务将接受来自远程客户端的基本身份验证。 如果禁用或未配置此策略设置，则 WinRM 服务将不接受来自远程客户端的基本身份验证。
  - **默认值**：已禁用
  
- **阻止客户端摘要式身份验证**  
  使用此策略设置，可以控制 Windows 远程管理 (WinRM) 客户端是否使用摘要式身份验证。 如果启用此策略设置，则 WinRM 客户端不使用摘要式身份验证。 如果禁用或未配置此策略设置，则 WinRM 客户端将使用摘要式身份验证。
  - **默认值**：启用
  
- **未加密的流量**  
  使用此策略设置，可以控制 Windows 远程管理 (WinRM) 服务是否通过网络发送和接收未经加密的消息。 如果启用此策略设置，则 WinRM 客户端将通过网络发送和接收未经加密的消息。 如果禁用或不配置此策略设置，则 WinRM 客户端将仅通过网络发送或接收经过加密的消息。  
  - **默认值**：已禁用
  
- **客户端未加密的流量**  
  使用此策略设置，可以管理 Windows 远程管理 (WinRM) 客户端是否通过网络发送和接收未加密的消息。 如果启用此策略设置，则 WinRM 客户端将通过网络发送和接收未经加密的消息。 如果禁用或不配置此策略设置，则 WinRM 客户端将仅通过网络发送或接收经过加密的消息。
  - **默认值**：已禁用
  
- **客户端基本身份验证**  
  使用此策略设置，可以控制 Windows 远程管理 (WinRM) 客户端是否使用基本身份验证。 如果启用此策略设置，则 WinRM 客户端将使用基本身份验证。 如果 WinRM 配置为使用 HTTP 传输，则通过网络以明文形式发送用户名和密码。 如果禁用或不配置此策略设置，WinRM 客户端则不使用基本身份验证。
  - **默认值**：已禁用
  

## <a name="remote-procedure-call"></a>远程过程调用  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall)。  

- **RPC 未经身份验证的客户端选项**  
  此策略设置控制 RPC 服务器运行时如何处理连接到 RPC 服务器的未经验证的 RPC 客户端。 此策略设置影响所有 RPC 应用程序。 在域环境中，应小心使用此策略设置，因为其可能会影响很多功能（包括组策略处理本身）。 恢复对此策略设置的更改可能要求手动干预每个受影响的计算机。 永远不应将此策略设置应用于域控制器。 如果禁用此策略设置，则 RPC 服务器运行时在 Windows 客户端上使用“已验证”值，而在支持此策略设置的 Windows Server 版本上使用值“无”。 如果未配置此策略设置，则会禁用该策略设置。 RPC 服务器运行时的行为就如同启用了此策略设置一样，将“已验证”值用于 Windows 客户端，而将“无”值用于支持此策略设置的服务器 SKU。 如果启用此策略设置，则它指导 RPC 服务器运行时限制未经验证的 RPC 客户端连接到计算机上运行的 RPC 服务器。 如果客户端使用命名管道与服务器通信或使用 RPC 安全，则该客户端将被认为是未经验证的客户端。 特别请求可以由未经验证的客户端访问的 RPC 接口可能在此限制之外，具体取决于为此策略设置选取的值。  
  - “无”允许所有 RPC 客户端连接到应用该策略设置的计算机上运行的 RPC 服务器。 
  - “已验证”仅允许经过验证的 RPC 客户端（依据上述定义）连接到应用该策略设置的计算机上运行的 RPC 服务器。 对请求例外的接口授予例外。 
  - “已验证并且无例外”仅允许经过验证的 RPC 客户端（依据上述定义）连接到应用该策略的计算机上运行的 RPC 服务器。 不允许例外。 注意：只有在重启系统后才可以应用此策略设置。  

  - 默认值：经过身份验证

## <a name="search"></a>搜索 
有关详细信息，请参阅 Windows 文档 [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search)（策略 CSP - Search）。  

- **禁用索引加密项**  
  允许或不允许项的索引。 此开关适用于 Windows Search 索引器，用于控制是否索引加密项，如受 Windows 信息保护 (WIP) 保护的文件。 启用策略后，即会索引受 WIP 保护的项，且相关元数据存储在未加密位置。 元数据包括文件路径和修改日期等。 禁用策略后，不会索引受 WIP 保护的项，也不会在 Cortana 或文件资源管理器的结果中显示这些项。 如果设备上存在许多受 WIP 保护的媒体文件，可能还会对照片和 Groove 应用产生性能影响。
  - 默认值：是
  
## <a name="smart-screen"></a>智能屏幕  
有关详细信息，请参阅 Windows 文档 [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen)（策略 CSP - SmartScreen）。  

- **阻止未经验证的文件**  
  阻止用户运行未经验证的文件。 0 - 员工可忽略 SmartScreen 警告并运行恶意文件。 1 - 员工不可忽略 SmartScreen 警告并运行恶意文件。
  - 默认值：是

- **阻止下载未经验证的文件**  
  默认情况下，Microsoft Edge 允许用户绕过（忽略）有关潜在恶意文件的 Windows Defender SmartScreen 警告，以便他们继续下载未经验证的文件。 启用此策略可防止用户绕过警告，阻止他们下载未经验证的文件。
  - 默认值：是
  
- **要求对应用和文件使用 SmartScreen**  
  允许 IT 管理员配置 Windows 适用的 SmartScreen。
  - 默认值：是
  
## <a name="system"></a>System (系统)  
有关详细信息，请参阅 Windows 文档 [olicy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system)（策略 CSP - System）。  

- **系统引导启动驱动程序初始化**  
  使用此策略设置，可以根据提前启动反恶意软件引导启动驱动程序所确定的分类来指定要初始化哪些引导启动驱动程序。 提前启动反恶意软件引导启动驱动程序可为每个引导启动驱动程序返回以下分类：- 好：驱动程序已签名且未被篡改。  
  - 差 - 驱动程序被标识为恶意软件。 建议不允许初始化已知的差驱动程序。 - 差，但启动需要：驱动程序被标识为恶意软件，但不加载此驱动程序计算机就无法成功启动。 
  - 未知 - 驱动程序未经恶意软件检测应用程序证明，且未经提前启动反恶意软件引导启动驱动程序分类。  

  如果启用此策略设置，则能够选择下次启动计算机时要初始化的引导启动驱动程序。 如果禁用或未配置此策略设置，则初始化被确定为“好”、“未知”或“差，但启动关键”的引导启动驱动程序，而跳过初始化被确定为“差”的驱动程序。 如果恶意软件检测应用程序不包括提前启动反恶意软件引导启动驱动程序，或者提前启动反恶意软件引导启动驱动程序已禁用，则此设置无效，所有引导启动驱动程序都会被初始化。  
  - 默认值：“好”、“未知”和“差，但关键”

## <a name="wi-fi"></a>Wi-Fi  
有关详细信息，请参阅 Windows 文档 [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)（策略 CSP - Wifi）。  

- **Wi-Fi**  
  指定可否在设备上进行 Internet 共享。
  - 默认值：是  

- **阻止自动连接到 Wi-Fi 热点**  
  允许或不允许设备自动连接到 Wi-Fi 热点。  
  - 默认值：是  
  
## <a name="windows-connection-manager"></a>Windows 连接管理器  
有关详细信息，请参阅 Windows 文档 [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager)（策略 CSP - WindowsConnectionManager）。  

- **阻止连接到非域网络**  
  此策略设置阻止计算机同时连接到基于域的网络和并非基于域的网络。 如果启用此策略设置，则计算机可基于以下情况响应自动和手动网络连接尝试： 
  - 自动连接尝试：当计算机已连接到基于域的网络时，将阻止所有对非域网络的自动连接尝试。 当计算机已连接到并非基于域的网络时，将阻止所有对基于域的网络的自动连接尝试。 
  - 手动连接尝试：当计算机已通过除以太网以外的介质连接到并非基于域的网络或基于域的网络，并且用户尝试违反此策略设置，创建到其他网络的手动连接时，将断开现有网络连接将，并允许手动连接。 当计算机已通过以太网连接到并非基于域的网络或基于域的网络，并且用户尝试违反此策略设置，创建到其他网络的手动连接时，将保持现有以太网连接，并阻止手动连接尝试。  

  如果未配置或禁用此策略设置，则计算机可以同时连接到域网络和非域网络。
  - 默认值：启用
  
## <a name="windows-defender"></a>Windows Defender  
有关详细信息，请参阅 Windows 文档 [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)（策略 CSP - Defender）。  

- **扫描传入的电子邮件**  
  允许或不允许扫描电子邮件。
  - 默认值：是  

- **Office 应用启动子进程类型**  
  Office 应用将无法创建子进程。 包括 Word、Excel、PowerPoint、OneNote 和 Access。 这是典型的恶意软件行为，尤其是在基于宏的攻击中，该行为试图使用 Office 应用启动或下载恶意可执行文件。
  - 默认值：阻止
  
- **Defender 示例提交同意类型**  
  检查 Windows Defender 中用户的同意级别是否可发送数据。 如果已授予所需同意，则 Windows Defender 将提交它们。 如果没有（并且用户已指定从不询问），则系统会先启动 UI 征得用户同意（允许 Defender/AllowCloudProtection 时），然后才发送数据。
  - 默认值：自动发送安全示例 
  
- **签名更新间隔（小时）**  
  Defender 签名更新间隔（小时）
  - 默认值：4
  
- **脚本下载有效负载执行类型**  
  脚本下载有效负载执行类型
  - 默认值：阻止
  
- **防止凭据窃取类型**  
  Windows Defender 凭据保护使用基于虚拟化的安全性来隔离密钥，以便只有特权系统软件可以访问它们。 未经授权的访问这些密钥可能会导致凭据被盗攻击，如哈希传递或票证传递。 Windows Defender 凭据保护可通过保护 NTLM 密码哈希、Kerberos 票证授予票证和由应用程序存储为域凭据的凭据来防止这些攻击。
  - 默认值：启用

- **电子邮件内容执行类型**  
  此规则可阻止以从 Microsoft Outlook 或 Webmail （如 Gmail.com 或 Outlook.com）的电子邮件中运行或启动以下文件类型：可执行文件（例如 .exe、.dll 或 .scr）、脚本文件（如 PowerShell.ps、VisualBasic.vbs 或 JavaScript.js 文件）、脚本存档文件。
  - 默认值：阻止
  
- **网络保护类型**  
  此策略可用于在 Windows Defender 攻击防护中启用或禁用网络保护（阻止/审核）。 网络保护是 Windows Defender 攻击防护的一项功能，可阻止员工使用任何应用访问 Internet 上的钓鱼邮件、攻击宿主站点和恶意内容。 这包括阻止第三方浏览器连接到危险站点。 值类型为整数。 如果启用此设置，则会启用网络保护，且员工无法将其禁用。 可通过以下选项控制其行为：阻止和审核。 如果启用此策略并使用“阻止”选项，则会阻止用户/应用连接到危险的域。 可在 Windows Defender 安全中心看到此活动。 如果启用此策略并使用“审核”选项，则不会阻止用户/应用连接到危险的域。 但是，仍可在 Windows Defender 安全中心看到此活动。 如果禁用此策略，则不会阻止用户/应用连接到危险的域。 无法在 Windows Defender 安全中心看到任何网络活动。 如果未配置此策略，则默认禁用网络阻止。
  - 默认值：启用
  
- **Defender 计划扫描日期**  
  Defender 计划扫描日期。
  - 默认值：每天
  
- **云提供的保护**  
  为了更好地保护你的电脑，Windows Defender 会将所发现的任何问题的相关信息发送到 Microsoft。 Microsoft 会分析该信息，详细了解影响你和其他客户的问题，并提供改进的解决方案。
  - 默认值：是  

- **Defender 可能不需要的应用操作**  
  Windows Defender 防病毒中的可能不需要的应用程序 (PUA) 保护功能可以识别和阻止在网络中的终结点上下载和安装 PUA。 这些应用程序不被视为病毒、恶意软件或其他类型的威胁，但可能在终结点上执行对性能或使用产生不利影响的操作。 PUA 也指视为信誉不佳的应用程序。 典型 PUA 行为包括：各种类型的软件捆绑 广告注入到 Web 浏览器 检测问题、要求付费修复错误但始终保留在终结点上且不会进行任何更改或优化的驱动程序和注册表优化程序（也称为“流氓防病毒”程序） 这些应用程序可能会增加网络受到恶意软件感染的风险、增加恶意软件感染的识别难度，而清理这些应用程序也会造成 IT 资源的浪费。  
  - 默认值：阻止  

- **脚本混淆的宏代码类型**  
  恶意软件和其他威胁可能会尝试在某些脚本文件中混淆或隐藏其恶意代码。 此规则可阻止运行混淆的脚本。
  - 默认值：阻止
  
- **完全扫描期间扫描可移动驱动器**  
  允许 Windows Defender 在完全扫描期间扫描可移动驱动器（例如闪存驱动器）中的恶意软件和不需要的软件。 Windows Defender 防病毒软件将在执行前扫描 USB 设备上的所有文件。
  - 默认值：是  
  
- **扫描存档文件**  
  Defender 扫描存档文件。
  - 默认值：是
  
- **行为监视**  
  允许或不允许 Windows Defender 行为监视功能。这些传感器内嵌于 Windows 10，收集并处理来自操作系统的行为信号，并将该传感器数据发送至 Windows Defender ATP 的专用独立云实例。
  - 默认值：是

- **扫描从网络文件夹中打开的文件**  
  如果文件为只读，则用户无法删除任何检测到的恶意软件。
  - 默认值：是

- **不受信任的 USB 进程类型**  
  使用此规则，管理员可以防止从 USB 可移动驱动器（包括 SD 卡）运行未签名或不受信任的可执行文件。
  - 默认值：阻止
  
- **Office 应用其他进程注入类型**  
  Office 应用（包括 Word、Excel、PowerPoint 和 OneNote）无法将代码注入其他进程。 恶意软件通常会使用此方法来运行恶意代码，试图对防病毒扫描引擎隐藏活动。
  - 默认值：阻止
  
- **Office 宏代码运行 Win32 导入类型**  
  恶意软件可以在 Office 文件中使用宏代码来导入和加载 Win32 DLL，然后可以使用此 DLL 进行 API 调用，以在整个系统中实现进一步感染。 此规则会尝试阻止所含宏代码支持导入 Win32 DLL 的 Office 文件。 这包括 Word、Excel、PowerPoint 和 OneNote。
  - 默认值：阻止  
  
- **Defender 云阻止级别**  
  Defender 云阻止级别。
  - 默认值：未配置

- **实时监视**  
  Defender 要求实时监视。
  - 默认值：是
  
- **Office 应用可执行内容创建或启动类型**  
  此规则针对创建或启动可执行文件的可疑和恶意外接程序和脚本（扩展）使用的典型行为。 这是典型的恶意软件技术。 将阻止 Office 应用使用扩展。 这些扩展通常使用 Windows Scripting Host（.wsh 文件）来运行脚本，自动执行某些任务或提供用户创建的外接程序功能
  - 默认值：阻止

## <a name="windows-ink-workspace"></a>Windows Ink 工作区  
有关详细信息，请参阅 Windows 文档 [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)（策略 CSP - WindowsInkWorkspace）。  

- **Ink 工作区**  
  指定是否允许用户访问 Ink 工作区。 0 - 禁止访问 Ink 工作区。 该功能处于禁用状态。 1 - 已启用 Ink 工作区（功能处于启用状态），但用户无法在锁屏界面上访问它。 2（默认）- 已启用 Ink 工作区（功能处于启用状态），且允许用户在锁屏界面上使用它。
  - 默认值：启用
 
## <a name="windows-powershell"></a>Windows PowerShell  
有关详细信息，请参阅 Windows 文档 [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell)（策略 CSP - WindowsPowerShell）。  

- **Power shell shell 脚本块日志记录**  
  使用此策略设置，可以将所有的 PowerShell 脚本输入记录到 Microsoft-Windows-PowerShell/Operational 事件日志中。 如果启用此策略设置，则 Windows PowerShell 将记录命令、脚本块、函数和脚本的处理，无论是以交互方式调用还是通过自动方式处理。 如果禁用此策略设置，则将禁止记录 PowerShell 脚本输入。 如果启用脚本块调用日志记录，则 PowerShell 在调用命令、脚本块、函数或脚本启动或停止时还会记录事件。 启用调用日志记录时会生成大量事件日志。 注意：此策略设置存在于组策略编辑器中“计算机配置”和“用户配置”的下方。 “计算机配置”策略设置优先于“用户配置”策略设置。
  - 默认值：启用
 
