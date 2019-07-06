---
title: 适用于 Windows 10 的 Intune 安全基线设置
titleSuffix: Microsoft Intune
description: 用于管理 Windows 10 的 Intune 安全基线设置
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8fa5589f62900027b90659b8f570e7caa10b1cd8
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549065"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>适用于 Intune 的 MDM 安全基线设置  

查看支持由 Microsoft Intune 的设备的运行 Windows 10 或更高版本的 MDM 安全基准设置。 此基线中的设置的默认值表示为合适的设备，建议的配置，可能与从其他安全基准的基线默认值不匹配。  

最新基线版本是**MDM 安全基线 Spring 2019 更新 （19 小时 1）**  

若要了解什么与此基线的最新版本中前一版本，请参阅[中的新模板的更改内容](#whats-changed-in-the-new-template)。  

> [!NOTE]  
> 在 2019 年 6 月预览 MDM 安全基线已被取代的版本*MDM Spring 2019 更新 （19 小时 1） 的安全基线*模板，为 generaly 可用 （未处于预览状态）。 提供之前创建的配置文件*MDM Spring 2019 更新 （19 小时 1） 的安全基线*基线不会更新以反映的设置和 Spring 2019 更新 （19 小时 1 MDM 安全基线中的值) 版本。  尽管不能创建新的配置文件基于预览版模板，但可以编辑并继续使用以前创建的基于预览版模板的配置文件。   
  
若要了解如何使用 Intune 的安全基准，请参阅[使用安全基线](security-baselines.md)。  


   
## <a name="above-lock"></a>锁定时  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock)。  

- **阻止显示 toast 通知**  
  使用此策略设置，可以阻止应用通知显示在锁定屏幕中。 如果启用此策略设置，则锁定屏幕不会显示任何应用通知。 如果禁用或不配置此策略设置，用户可以选择哪些应用在锁定屏幕上显示通知。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **默认值**：是  

- **语音激活锁定屏幕中的应用**  

  **默认值**：已禁用

## <a name="app-runtime"></a>应用运行时    
有关详细信息，请参阅 Windows 文档中的[策略 CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
)。  

- **Windows 应用商店应用的可选 Microsoft 帐户**  
  使用此策略设置，可以控制：对于需要帐户进行登录的 Windows 应用商店应用，Microsoft 帐户是否可选。 此策略仅影响支持它的 Windows 应用商店应用。 如果启用此策略设置，则通常需要 Microsoft 帐户登录的 Windows 应用商店应用将允许用户改为使用企业帐户登录。 如果禁用或不配置此策略设置，则用户必须使用 Microsoft 帐户登录。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **默认值**：已启用  

## <a name="application-management"></a>应用程序管理   
有关详细信息，请参阅 Windows 文档中的[策略 CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement)。  

- **阻止用户对安装进行控制**  
  此策略设置允许用户更改通常是仅供系统管理员的安装选项。 如果启用此策略设置，会绕过某些 Windows 安装程序的安全功能。 它允许完成安装，由于安全冲突而被终止。 如果禁用或未配置此策略设置，Windows 安装程序的安全功能阻止用户更改安装选项通常保留为系统管理员，例如，指定安装文件的目录。 如果 Windows 安装程序检测到一个安装包已允许用户更改受保护的选项，它将停止安装，并显示一条消息。 仅当运行安装程序中具有对用户的目录的访问特权的安全上下文中运行安全功能。 此策略设置适用于限制较少的环境中。 可以使用它来避免阻止安装软件的安装程序错误。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **默认值**：是

- **使用提升的权限的块 MSI 应用安装**  
  当 Windows Installer 在系统上安装任何程序时，此策略设置将指示它使用提升的权限。  
  - *如果启用此策略设置*，权限扩展到所有程序。 这些权限通常仅供被分配给用户 （在桌面上提供），分配给计算机 （自动安装） f，或在控制面板中进行添加或删除程序中提供程序。 此配置文件设置允许用户安装程序需要对用户可能没有权限查看或更改，包括高度受限计算机上的目录的目录的访问。
  - *如果禁用或未配置此策略设置*，系统会在安装的系统管理员不分发或提供程序应用当前用户的权限。 注意：此策略设置将同时显示在“计算机配置”和“用户配置”文件夹中。 若要使此策略设置生效，必须在这两个文件夹中启用它。 注意： 熟练的用户可以利用的权限的此策略设置授予用来更改其权限并获得对受限制的文件和文件夹的永久访问权限。 请注意，此策略设置的用户配置版本不一定是安全的。  
  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **默认值**：是

- **阻止游戏 DVR（仅限桌面版）**  
  配置是否允许游戏的录制和广播。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **默认值**：是  

## <a name="auto-play"></a>自动播放   
有关详细信息，请参阅 Windows 文档中的[策略 CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay)。  

- **自动播放默认自动运行行为**  
  此设置影响 Autorun 命令的默认行为。 Autorun 命令存储在 autorun.inf 文件中，可以启动安装程序或其他例程。 如果设置为“启用”，管理员可在运行 Windows Vista 或更高版本的设备上更改默认的自动运行行为  。 行为可设置为：a) 彻底禁用自动运行命名，或 b) 还原到早于 Windows Vista 的自动执行自动运行命令的行为。 如果设置为“禁用”或“未配置”，则运行 Windows Vista 或更高版本的设备将提示用户是否应该运行自动运行命令   。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **默认值**：不执行  
  
- **自动播放模式**  
  此策略设置允许关闭自动播放功能。 驱动器中插入媒体后，自动播放开始从驱动器中读取数据。 程序安装文件和音频媒体中的音乐立即启动。 在 Windows XP SP2 之前，在可移动驱动器上，如软盘驱动器（但不是 CD-ROM 驱动器）和网络驱动器上，会默认禁用自动播放。 从 Windows XP SP2 开始，也为可移动驱动器（包括 Zip 驱动器和某些 USB 大容量存储设备）启用了自动播放。 如果启用此策略设置，将在 CD-ROM 和可移动媒体驱动器上禁用自动播放，或在所有驱动器上禁用此功能。 此策略设置禁用其他类型驱动器上的自动播放。 不能使用此设置在默认禁用自动播放的驱动器上启用自动播放。 如果禁用或不配置此策略设置，则启用自动播放。 注意：此策略设置将同时显示在计算机配置和用户配置文件夹中。 如果策略设置相互冲突，计算机配置中的策略设置优先于用户配置中的策略设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **默认值**：已禁用

- **阻止非卷设备的自动播放**  
  此策略设置不允许在照相机或手机等 MTP 设备上进行自动播放。 如果启用此策略设置，则照相机或手机等 MTP 设备上将禁止自动播放。 如果禁用或不配置此策略设置，则对非卷设备启用自动播放。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **默认值**：已启用  

## <a name="bitlocker"></a>Bitlocker    
有关详细信息，请参阅 Windows 文档中的[策略 CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
)。  

- **Bit locker 可移动驱动器策略**  
  此策略设置用于控制加密方法和密码长度。 此策略的值确定 BitLocker 用于加密的密码强度。 企业可能想要控制加密级别，增强安全性（AES-256 强于 AES-128）。 如果启用此设置，将能够为固定的数据驱动器、操作系统驱动器和可移动数据驱动器单独配置加密算法和密钥加密强度。 对于固定的驱动器和操作系统驱动器，建议使用 XTS-AES 算法。 对于可移动驱动器，如果驱动器用于非运行 Windows 10（版本 1511 或更高版本）的其他设备，则应使用 AES-CBC 128 位或 AES-CBC 256 位。 如果驱动器已加密或正在进行加密，更改加密方法不会产生任何影响。 在这些情况下，将忽略此策略设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067140) 

  对于 Bit locker 可移动驱动器策略，配置以下设置：

    - **需要为写入权限进行加密**  
      **默认值**：是  
  

## <a name="browser"></a>浏览器  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser)。  

- **Microsoft Edge SmartScreen**  
  默认情况下，Microsoft Edge 使用 Windows Defender SmartScreen（已启用）防止用户受潜在网络钓鱼诈骗和恶意软件侵袭。 此外，默认情况下，用户不能禁用（关闭）Windows Defender SmartScreen。 启用此策略将关闭 Windows Defender SmartScreen，并阻止用户将其打开。 请勿配置此策略，以允许用户选择打开或关闭 Windows Defender SmartScreen。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **默认值**：是  
  
- **阻止恶意网站访问**  
  默认情况下，Microsoft Edge 允许用户绕过（忽略）有关潜在恶意站点的 Windows Defender SmartScreen 警告，以便他们继续访问该站点。 但是使用此策略，可配置 Microsoft Edge，阻止用户绕过警告，并阻止他们继续访问该站点。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **默认值**：是  
  
- **阻止下载未经验证的文件**  
  默认情况下，Microsoft Edge 允许用户绕过（忽略）有关潜在恶意文件的 Windows Defender SmartScreen 警告，以便他们继续下载未经验证的文件。 启用此策略可防止用户绕过警告，阻止他们下载未经验证的文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **默认值**：是  
  
- **阻止使用密码管理器**  
  默认情况下，Microsoft Edge 自动使用密码管理器，从而允许用户在本地管理密码。 禁用此策略可限制 Microsoft Edge 使用密码管理器。 如果想要让用户选择使用密码管理器在本地保存和管理密码，请勿配置此策略。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **默认值**：是  
  
- **防止覆盖证书错误**  
  此策略设置可阻止用户忽略 Internet Explorer 中那些中断浏览的安全套接字层/传输层安全性 (SSL/TLS)证书错误（如“过期”、“吊销”或“名称不匹配”错误）。 如果启用此策略设置，则用户无法继续浏览。 如果禁用或未配置此策略设置，则用户可以选择忽略证书错误并继续浏览。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **默认值**：是  

## <a name="connectivity"></a>连接性  
有关详细信息，请参阅 Windows 文档 [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity)（策略 CSP - Connectivity）。  

- **阻止 Web 发布和在线订购向导的 Internet 下载**  
  此策略设置可指定 Windows 是否应下载 Web 发布和在线订购向导的提供商列表。 这些向导允许用户从提供在线存储和照片打印等服务的公司列表中进行选择。 默认情况下，除了注册表中指定的提供商外，Windows 还会显示从 Windows 网站下载的提供商。 如果启用此设置，Windows 将不会下载提供商，只会显示在本地注册表中缓存的服务提供商。 如果禁用或未配置此设置，则在用户使用 Web 发布或在线订购向导时，将会下载服务提供商列表。 请参阅 Web 发布和在线订购向导的文档了解详细信息，包括有关在注册表中指定服务提供商的详细信息。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **默认值**：已启用  

- **阻止通过 HTTP 下载打印驱动程序**  
  此策略可指定是否允许此客户端通过 HTTP 下载打印机驱动程序包。 要设置 HTTP 打印，需要通过 HTTP 下载产品盒中未提供的驱动程序。 注意：此设置不阻止客户端通过 HTTP 打印到 Intranet 或 Internet 上的打印机。 它仅禁止下载本地尚未安装的驱动程序。 如果启用此策略设置，则无法通过 HTTP 下载打印机驱动程序。 如果禁用或未配置此设置，则用户可通过 HTTP 下载打印机驱动程序。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **默认值**：已启用  

## <a name="credentials-delegation"></a>凭据委派  
有关详细信息，请参阅 Windows 文档 [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
)（策略 CSP - CredentialsDelegation）。  

- **远程主机不可导出的凭据委派**  
  远程主机允许委派不可导出的凭据。 使用凭据委派功能时，设备将向远程机提供一个可导出版本的凭据，这会使用户面临被位于远程机端的攻击者盗用凭据的风险。 如果启用此策略设置，主机支持“受限管理”或“远程 Credential Guard”模式。 如果禁用或未配置此策略设置，则不支持“受限管理”和“远程 Credential Guard”模式。 用户始终需要将其凭据传递给主机。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **默认值**：已启用  

## <a name="credentials-ui"></a>凭据 UI  
有关详细信息，请参阅 Windows 文档 [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui)（策略 CSP - CredentialsUI）。  

- **枚举管理员**此策略设置控制当用户尝试提升正在运行的应用程序时是否会显示管理员帐户。 默认情况下，用户尝试提升正在运行的应用程序时，不会显示管理员帐户。 如果启用此策略设置，则会显示电脑上的所有本地管理员帐户，以便用户可以从中选择一个账户并输入正确的密码。 如果禁用此策略设置，则系统始终要求用户在进行提升时键入用户名和密码。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **默认值**：已禁用  

## <a name="data-protection"></a>数据保护  
有关详细信息，请参阅 Windows 文档 [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
)（策略 CSP - DataProtection）。  

- **阻止直接内存访问**  
  此策略设置允许你阻止所有热插拔 PCI 下游端口进行直接内存访问 (DMA)，直到用登录 Windows。 用户登录后，Windows 会枚举连接到热插拔 PCI 端口的 PCI 设备。 用户每次锁定计算机都会阻止无子设备的热插拔 PCI 端口进行 DMA，直到用户再次登录。 已在计算机解锁时枚举的设备继续工作，直到拔出。 只在启用了 BitLocker 或设备加密时才执行此策略设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **默认值**：是  

## <a name="device-guard"></a>Device Guard  
有关详细信息，请参阅 Windows 文档 [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
)（策略 CSP - DeviceGuard）。  

- **Credential Guard**  
  此设置可让用户通过基于虚拟化的安全打开 Credential Guard，帮助在下次重启时保护凭据。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **默认值**：使用 UEFI 锁启用 

- **启用基于虚拟化的安全性**   
  在下次重启时打开基于虚拟化的安全性 (VBS)。 基于虚拟化的安全性使用 Windows 虚拟机监控程序提供对安全服务的支持。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **默认值**：是  


- **启动 System Guard**    
  **默认值**：已启用  

## <a name="device-installation"></a>设备安装  
有关详细信息，请参阅 Windows 文档 [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation)（策略 CSP - DeviceInstallation）。  

- **按设备标识符安装硬件设备**  
  使用此策略设置可以指定禁止 Windows 安装的设备的即插即用硬件 ID 和兼容 ID 的列表。 此策略设置优先于任何其他允许 Windows 安装设备的策略设置。 如果启用此策略设置，则禁止 Windows 安装你所创建的列表中列出了其硬件 ID 或兼容 ID 的设备。 如果在某个远程桌面服务器上启用了此策略设置，则此策略设置会影响指定设备从远程桌面客户端到该远程桌面服务器的重定向。 如果禁用或未配置此策略设置，则设备可以根据其他策略设置来允许或阻止安装和更新。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
  **默认值**：阻止安装硬件设备  

    选择“阻止安装硬件设备”  时，以下设置将可用。
  
    - **删除匹配的硬件设备**   
    仅“按设备标识符安装硬件设备”设置为“阻止安装硬件设备”时，此设置才可用   。
      
      **默认值**：是
  
    - **已阻止的硬件设备标识符**  
       仅“按设备标识符安装硬件设备”设置为“阻止安装硬件设备”时，此设置才可用   。
      
      **默认值**：是  
  
- **按安装程序类安装硬件设备**  
  使用此策略设置可以指定禁止 Windows 安装的设备驱动程序的设备安装程序类全局唯一标识符 (GUID) 列表。 此策略设置优先于任何其他允许 Windows 安装设备的策略设置。 如果启用此策略设置，则禁止 Windows 安装或更新你所创建的列表中列出了其设备安装程序类 GUID 的设备驱动程序。 如果在某个远程桌面服务器上启用了此策略设置，则此策略设置会影响指定设备从远程桌面客户端到该远程桌面服务器的重定向。 如果禁用或未配置此策略设置，则 Windows 可以根据其他策略设置来允许或禁止安装和更新设备。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **默认值**：阻止安装硬件设备  

    选择“阻止安装硬件设备”  时，以下设置将可用。
    - **删除匹配的硬件设备**    
    仅“按安装程序类安装硬件设备”设置为“阻止硬件设备安装”时，此设置才可用   。  

      **默认值**：无默认配置   
  
    - **已阻止的硬件设备标识符**  
      仅“按安装程序类安装硬件设备”设置为“阻止硬件设备安装”时，此设置才可用   。
      
      **默认值**：无默认配置   

## <a name="device-lock"></a>设备锁定  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock)（策略 CSP - DeviceLock）。  

- **阻止使用摄像头**  
  禁用“电脑设置”中的锁屏界面摄像头切换开关，并阻止在锁定屏幕上调用摄像头。 默认情况下，用户可以在锁屏界面上启用可用摄像头的调用。 如果启用此设置，用户将无法再在“电脑设置”中启用或禁用锁屏界面摄像头访问，并且无法在锁屏界面上调用摄像头。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **默认值**：已启用  

- **需要密码**  
  指定是否启用设备锁定。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **默认值**：是  
  
    将“需要密码”  设置为“是”  时，以下设置将可用。

    - **密码最小字符集数**  
      强 PIN 或密码所需的复杂元素类型（大写和小写字母、数字和标点符号）的数量。 PIN 会对桌面设备和移动设备强制执行以下行为：1 - 仅数字 2 - 必须为数字和小写字母 3 - 必须为数字、小写字母和大写字母。 在桌面 Microsoft 帐户和域帐户中不支持。 4 - 必须为数字、小写字母、大写字母和特殊字符。 在桌面中不支持。 默认值为 1。  
      [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067055)  
      
      **默认值**：3  
  
    - **擦除设备前的登录失败次数**  
      擦除设备之前允许的身份验证失败次数。 值为 0 会禁用设备擦除功能。  
      [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067030)  
        
      **默认值**：10  
  
    - **密码过期（天数）**  
      “最长密码期限”策略设置确定在系统要求用户更改密码之前可以使用密码的时长（以天数为单位）。 可将密码设置为在天数（1 至 999）之后过期，也可通过将天数设置为 0 来指定密码永不过期。 如果最长密码期限是介于 1 到 999 天之间，最短密码期限必须小于最长密码期限。 如果最长密码期限设置为 0，最短密码期限可以是介于 0 和 998 天之间的任意值。  
      [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067028)  
      
      **默认值**：60  
  
    - **所需的密码类型**  
      确定所需的 PIN 或密码类型。  
      [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067027)  
      
      **默认值**：字母数字  
  
    - **最短密码长度**  
      “最小密码长度”策略设置确定可以组成用户帐户密码的最少字符数。 可以设置的值介于 1 到 14 个字符之间，也可以通过将字符数设置为 0 来确定不需要密码。  
      [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067024)  
      
      **默认值**：8  
  
    - **禁止使用简单密码**  
      指定是否允许使用 PIN 或“1111”或“1234”等密码。 对桌面版，还可以控制图片密码的使用。  
      [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067127) 
      
      **默认值**：是  
        设置为“是”可防止使用简单密码  。 

  - **防止重用以前的密码**  
    指定可以在历史记录中存储的无法使用的密码数。 该值包括用户的当前密码。 例如，如果设置为 1  ，则在选择新密码时，用户不能重用其当前密码。 设置为 5  意味着用户不能将其新密码设置为当前密码或以前四个密码中的任何一个。  
    [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **默认值**：24  

- **阻止幻灯片放映**  
  禁用“电脑设置”中的锁屏界面幻灯片放映设置，并阻止在锁屏界面上播放幻灯片放映。 默认情况下，用户可以启用在计算机锁定后运行的幻灯片放映。 如果启用此设置，用户将无法修改“电脑设置”中的幻灯片放映设置，也无法启动幻灯片放映。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **默认值**：已启用  
  设置为“启用”会阻止运行幻灯片放映。  

- **密码最短期限（以天为单位）**  
  “最短密码期限”策略设置确定用户在更改密码之前必须使用的时间（以天为单位）。 可以将值设置为 1 至 998 天，也可以通过将天数设置为 0 来允许立即更改密码。 除非将密码最长期限设置为 0（表示密码永不过期），否则最短密码期限必须小于最长密码期限。 如果最长密码期限设置为 0，最短密码期限可以设置为介于 0 和 998 天之间的任意值。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **默认值**：1  

## <a name="dma-guard"></a>DMA 保护  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard)。
- **与内核 DMA 保护不兼容的外部设备的枚举**  
  此策略旨在提供额外的安全性外部 DMA 支持的设备。 它让用户能够更好地控制与 DMA 重新映射/设备内存隔离和沙盒不兼容但支持 DMA 的外部设备的枚举。 仅当内核 DMA 保护受到支持且已由系统固件启用时，此策略才有效。 内核 DMA 保护是一种平台功能，通过策略或最终用户无法控制。 制造时系统必须支持此功能。 若要检查系统是否支持内核 DMA 保护，请检查 MSINFO32.exe 的摘要页中的内核 DMA 保护字段。  
  [了解详细信息](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **默认值**：阻止所有   

## <a name="event-log-service"></a>事件日志服务  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice)（策略 CSP - EventLogService）。  

- **安全日志的最大文件大小 (KB)**  
  此策略设置指定日志文件的最大大小 (KB)。 如果启用此策略设置，则可将最大日志文件大小配置为 1 MB (1024 KB) 至 2 TB (2147483647 KB) 之间（以千字节递增）。 如果禁用或未配置此策略设置，则日志文件的最大大小会设置为本地配置的值。 本地管理员可以使用“日志属性”对话框更改此值（默认值为 20 MB）。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **默认值**：196608  

- **系统日志的最大文件大小 (KB)**  
  此策略设置指定日志文件的最大大小 (KB)。 如果启用此策略设置，则可将最大日志文件大小配置为 1 MB (1024 KB) 至 2 TB (2147483647 KB) 之间（以千字节递增）。 如果禁用或未配置此策略设置，则日志文件的最大大小会设置为本地配置的值。 本地管理员可以使用“日志属性”对话框更改此值（默认值为 20 MB）。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **默认值**：32768  

- **应用程序日志的最大文件大小 (KB)**  
  此策略设置指定日志文件的最大大小 (KB)。 如果启用此策略设置，则可将最大日志文件大小配置为 1 MB (1024 KB) 至 2 TB (2147483647 KB) 之间（以千字节递增）。 如果禁用或未配置此策略设置，则日志文件的最大大小会设置为本地配置的值。 本地管理员可以使用“日志属性”对话框更改此值（默认值为 20 MB）。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **默认值**：32768  

## <a name="experience"></a>体验  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)（策略 CSP - 体验）。  

- **阻止 Windows 聚焦**  
  允许 IT 管理员关闭所有 Windows 聚焦功能 - 锁屏界面上的 Windows 聚焦、Windows 提示、Microsoft 使用者功能和其他相关的功能。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **默认值**：是  

  将“阻止 Windows 聚焦”  设置为“是”  时，以下设置将可用。
  
  - **阻止 Windows 聚焦中的第三方建议**  
    指定是否允许第三方软件发布者在 Windows 屏幕聚焦功能（例如，锁屏界面聚焦、“开始”菜单中的建议应用和 Windows 提示）中提供应用和内容建议。 用户仍可以看到有关 Microsoft 功能、应用和服务的建议。  
    [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **默认值**：是  
  - **阻止使用者特定功能**  
    允许 IT 管理员启用通常只面向使用者的体验，例如“入门”建议、成员资格通知、OOBE 后应用安装和重定向磁贴。  
    [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **默认值**：是  

## <a name="exploit-guard"></a>攻击防护  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard)（策略 CSP - ExploitGuard）。  

- **Exploit protection XML**  
  使 IT 管理员能够将表示所需系统和应用程序缓解选项的配置推送到组织中的所有设备。 配置由 XML 表示。 Exploit Protection 有助于保护设备免受利用攻击进行传播的恶意软件的侵袭。 使用 Windows 安全性应用或 PowerShell 来创建一组缓解方案（称为配置）。 然后，可将此配置导出为 XML 文件，并与网络中的多台计算机共享，使其全部拥有相同的一组缓解设置。 此外，还可将现有的 EMET 配置 XML 文件转换为和导入到 Exploit Protection 配置 XML。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **默认值**：已提供示例 xml  
 
## <a name="file-explorer"></a>文件资源浏览器  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer)。  

- **阻止“数据执行保护”**  
  禁用数据执行保护可允许某些旧插件应用程序在不终止资源管理器的情况下正常运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **默认值**：已禁用  
   
- **阻止“损坏时堆终止”**  
  禁用“损坏时堆终止”可允许某些旧的插件应用程序在不立即终止资源管理器的情况下正常运行，但资源管理器稍后仍可能意外终止。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **默认值**：已禁用  
    

## <a name="internet-explorer"></a>Internet Explorer  
有关详细信息，请参阅 Windows 文档[策略 CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer)。  

- **Internet ExplorerI 限制区域通过脚本更新状态栏**  
  使用此策略设置，可以控制是否允许脚本在区域中更新状态栏。 
  - 如果启用此策略设置  ，则允许脚本更新状态栏。
  - 如果禁用或未配置此策略设置  ，则不允许脚本更新状态栏。  

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **默认值**：已禁用

- **Internet Explorer Internet 区域拖放或复制和粘贴文件**  
  利用此策略设置，可管理用户是否可以从此区域中的一个源拖动文件或复制和粘贴文件。 如果启用此策略设置，则用户可以自动从此区域拖动文件或复制和粘贴文件。 如果在下拉框中选择“提示”，则会询问用户选择是否从该区域拖动或复制文件。 如果禁用此策略设置，则会阻止用户从该区域拖动文件或者复制和粘贴文件。 如果未配置此策略设置，则用户可以自动从此区域拖动文件或复制和粘贴文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **默认值**：禁用

- **Internet Explorer 限制区域 .NET Framework 相关组件**    
  使用此策略，可以控制未使用验证码签名的 .NET Framework 组件是否可以在 Internet Explorer 中执行。 这些组件包括从对象标记中引用的托管控件和从链接中引用的托管可执行文件。 如果启用此策略设置，Internet Explorer 将执行未签名的托管组件。 如果在下拉列表框中选择“提示”，Internet Explorer 将提示用户决定是否执行未签名的托管组件。 如果禁用此策略设置，Internet Explorer 将不执行未签名的托管组件。 如果未配置此策略设置，Internet Explorer 将不执行未签名的托管组件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067077)

  **默认值**：禁用


- **Internet Explorer 本地计算机区域不针对 ActiveX 控件运行反恶意软件**  
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067152)

  **默认值**：已禁用

- **Internet Explorer 对数据源的 Internet 区域访问权限**  
  通过此策略设置，可控制 Internet Explorer 是否可以使用 Microsoft XML 分析程序 (MSXML) 或 ActiveX 数据对象 (ADO) 访问另一个安全区域的数据。 如果启用此策略设置，用户可以在区域中加载页面，该页面使用 MSXML 或 ADO 访问区域中其他站点的数据。 如果在下拉列表框中选择“提示”，将会提示用户选择是否允许在区域中加载页面，该页面使用 MSXML 或 ADO 访问区域中其他站点的数据。 如果禁用此策略设置，则用户无法在区域中加载使用 MSXML 或 ADO 访问区域中其他站点数据的页面。 如果不配置此策略设置，则用户无法在区域中加载使用 MSXML 或 ADO 访问区域中其他站点数据的页面。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **默认值**：禁用  
  
- **Internet Explorer 限制在 Windows 内的不同域之间拖动内容**  
  使用此策略设置，可以设置选项，用于在源和目标位于同一窗口时将内容从一个域拖到另一个域。 如果启用此策略设置并单击“启用”，用户可以在源和目标位于同一窗口时将内容从一个域拖到另一个域。 用户无法更改此设置。 如果启用此策略设置并单击“禁用”，则当源和目标位于同一窗口中时，用户无法将内容从一个域拖动到另一个域。 用户无法在“Internet 选项”对话框中更改此设置。 在 Internet Explorer 10 中，如果禁用或未配置此策略设置，则用户无法在源和目标位于同一窗口时将内容从一个域拖到另一个域。 用户可以在“Internet 选项”对话框中更改此设置。 在 Internet Explorer 9 或较早版本中，如果禁用或未配置此策略设置，用户可以在源和目标位于同一窗口时将内容从一个域拖到另一个域。 用户无法在“Internet 选项”对话框中更改此设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **默认值**：已禁用
  
- **Internet Explorer 证书地址不匹配警告**  
  使用此策略设置，能够启用证书地址不匹配安全性警告。 启用此策略设置后，用户在访问安全 HTTP (HTTPS) 网站时，如果其中显示的是为其他网址颁发的证书，用户会收到警告。 此警告有助于防止欺骗攻击。 如果启用此策略设置，会一直显示证书地址不匹配警告。 如果禁用或不配置此策略设置，用户可以选择是否显示证书地址不匹配警告（通过使用 Internet 控制面板中的“高级”页）。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **默认值**：已启用 
  
- **Internet Explorer 限制区域低权限网站**  
  使用此策略设置，可以控制权限较低的区域的网站（如 Internet 站点）是否能够导航到此区域。 如果启用此策略设置，低权限区域的网站可在此区域中打开新窗口，或导航到此区域。 安全区域运行时将不具有由“区域提升保护”安全功能提供的额外一层安全性。 如果在下拉列表框中选择“提示”，则会在将要发生可能有风险的导航时向用户发出警告。 如果禁用此策略设置，将阻止可能有害的导航。 Internet Explorer 安全功能在此区域中处于启用状态，如“区域提升保护”功能控件中所设置的那样。 如果不配置此策略设置，将阻止可能有害的导航。 Internet Explorer 安全功能在此区域中处于启用状态，如“区域提升保护”功能控件中所设置的那样。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **默认值**：禁用  
  
- **Internet Explorer 限制区域自动提示文件下载**  
  此策略设置决定系统是否会就非用户启动的文件下载提示用户。 无论此设置如何，用户都将收到用户启动的下载的文件下载对话框。 如果启用此设置，用户将收到针对自动下载尝试的文件下载对话框。 如果禁用或未配置此设置，系统将阻止非用户启动的文件下载，并且用户将看到“通知”栏而非文件下载对话框。 然后，用户可以单击通知栏，允许文件显示下载提示。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **默认值**：已禁用
  
- **Internet Explorer Internet 区域 .NET Framework 相关组件**  
  利用此策略设置，可管理是否可以从 Internet Explorer 执行未使用验证码签名的 .NET 框架组件。 这些组件包括从对象标记中引用的托管控件和从链接中引用的托管可执行文件。 如果启用此策略设置，Internet Explorer 将执行未签名的托管组件。 如果在下拉列表框中选择“提示”，Internet Explorer 将提示用户决定是否执行未签名的托管组件。 如果禁用此策略设置，Internet Explorer 将不执行未签名的托管组件。 如果未配置此策略设置，Internet Explorer 将执行未签名的托管组件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **默认值**：禁用 
  
- **Internet Explorer internet 区域仅允许批准的域使用 tdc ActiveX 控件**  
  此策略设置控制用户是否可以在网站上运行 TDC ActiveX 控件。 如果启用此策略设置，则 TDC ActiveX 控件不会从此区域中的网站运行。 如果禁用此策略设置，TDC ActiveX 控件会从此区域中的所有站点运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **默认值**：已启用 
  
- **Internet Explorer 限制区域脚本启动窗口**  
  使用此设置，可以管理针对脚本启动的弹出窗口和包含标题和状态栏的窗口的限制。 如果启用此策略设置，则不会在此区域中应用 Windows 限制安全。 安全区域运行时将不具有此功能提供的额外一层安全性。 如果禁用此策略设置，则脚本启动的弹出窗口和含标题和状态栏的窗口中包含的可能有害的操作将无法运行。 此区域中会启用此 Internet Explorer 安全功能，如进程的“脚本化 Windows 安全限制”功能控件设置所规定的那样。 如果未配置此策略设置，则脚本启动的弹出窗口和含标题和状态栏的窗口中包含的可能有害的操作将无法运行。 此区域中会启用此 Internet Explorer 安全功能，如进程的“脚本化 Windows 安全限制”功能控件设置所规定的那样。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **默认值**：已禁用 
  
- **Internet Explorer 将文件上传到服务器时，Internet 区域包含本地路径**  
  使用此策略设置，可控制用户通过 HTML 窗体上传文件时是否会发送本地路径信息。 如果发送本地路径信息，则无意中可能向服务器泄露部分信息。 例如，从用户桌面发送的文件可能包含用户名，作为路径的一部分。 如果启用此策略设置，则在用户通过 HTML 窗体上传文件时会发送路径信息。 如果禁用此策略设置，则在用户通过 HTML 窗体上传文件时删除路径信息。 如果不配置此策略设置，则用户可以在通过 HTML 窗体上传文件时选择是否发送路径信息。 默认情况下，发送路径信息。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **默认值**：已禁用 
  
- **Internet Explorer 在增强保护模式下禁用进程**  
  此策略设置确定在 64 位版本的 Windows 上以增强保护模式运行时，Internet Explorer 11 是使用 64 位进程（以获得更高安全性）还是使用 32 位进程（以获得更高兼容性）。 重要事项：使用 64 位进程时，某些 ActiveX 控件和工具栏可能不可用。 如果启用此策略设置，则在 64 位版本的 Windows 上以增强保护模式运行时，Internet Explorer 11 将使用 64 位选项卡进程。 如果禁用此策略设置，则在 64 位版本的 Windows 上以增强保护模式运行时，Internet Explorer 11 将使用 32 位选项卡进程。 如果未配置此策略设置，则用户可使用 Internet Explorer 设置启用或禁用此功能。 默认情况下，此功能处于禁用状态。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **默认值**：已启用 
  
- **Internet Explorer 忽略证书错误**  
  此策略设置可阻止用户忽略 Internet Explorer 中那些中断浏览的安全套接字层/传输层安全性 (SSL/TLS)证书错误（如“过期”、“吊销”或“名称不匹配”错误）。 如果启用此策略设置，则用户无法继续浏览。 如果禁用或未配置此策略设置，则用户可以选择忽略证书错误并继续浏览。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **默认值**：已禁用 
  
- **Internet Explorer Internet 区域加载 XAML 文件**  
  利用此策略设置，可管理 Extensible Application Markup Language (XAML) 文件的加载。 XAML 是基于 XML 的声明性标记语言，通常用于创建可充分利用 Windows Presentation Foundation 的丰富用户界面和图形。 如果启用此策略设置，并将下拉列表框设置为“启用”，则会自动在 Internet Explorer 中自动加载 XAML 文件。 用户无法更改此行为。 如果将下拉列表框设为“提示”，系统则会提示用户加载 XAML 文件。 如果禁用此策略设置，则不会在 Internet Explorer 中加载 XAML 文件。 用户无法更改此行为。 如果未配置此策略设置，则用户可以决定是否在 Internet Explorer 中加载 XAML 文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **默认值**：禁用 
  
- **Internet Explorer Internet 区域自动提示文件下载**  
  此策略设置决定系统是否会就非用户启动的文件下载提示用户。 无论此设置如何，用户都将收到用户启动的下载的文件下载对话框。 如果启用此设置，用户将收到针对自动下载尝试的文件下载对话框。 如果禁用或未配置此设置，系统将阻止非用户启动的文件下载，并且用户将看到“通知”栏而非文件下载对话框。 然后，用户可以单击通知栏，允许文件显示下载提示。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 受限制区域对潜在不安全文件的安全警告**  
  此策略设置控制在用户尝试打开可执行文件或其他潜在不安全文件（例如，使用“文件资源管理器”从 Intranet 文件共享中获取）时，是否出现“打开文件 - 安全警告”消息。 如果启用此策略设置并且将下拉框设置为“启用”，则打开这些文件时不显示安全警告。 如果将下拉框设置为“提示”，则打开文件之前显示安全警告。 如果禁用此策略设置，则无法打开这些文件。 如果未配置此策略设置，则用户可以配置计算机处理这些文件的方式。 默认情况下，这些文件在受限制区域中设置为阻止，在 Intranet 和本地计算机区域中设置为启用，在 Internet 和受信任区域中设置为提示。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **默认值**：禁用  
  
- **Internet Explorer Internet 区域跨站点脚本筛选器**  
  此策略控制跨站点脚本 (XSS) 筛选是否会检测并阻止跨站点脚本注入此区域中的网站。 如果启用此策略设置，则对此区域中的站点启用 XSS 筛选，并且 XSS 筛选尝试阻止跨站脚本注入。 如果禁用此策略设置，则对此区域中的站点禁用 XSS 筛选，并且 Internet Explorer 允许跨站点脚本注入。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **默认值**：已启用 
  
- **Internet Explorer 回退到 SSL3**  
  利用此策略设置，可阻止 SSL 3.0 的不安全回退。 启用此策略后，当 TLS 1.0 或更高版本失败时，Internet Explorer 将尝试使用 SSL 3.0 或更低版本连接到站点。 建议禁用不安全回退，以防止中间人攻击。 此策略不会影响启用的安全协议。 如果禁用此策略，则使用系统默认值。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **默认值**：没有站点  

- **Internet Explorer 加密支持**  
  此策略设置允许你关闭浏览器中对传输层安全 (TLS) 1.0、 TLS 1.1，TLS 1.2、 安全套接字层 (SSL) 2.0 中或 SSL 3.0 支持。 TLS 和 SSL 协议，可帮助保护在浏览器和目标服务器之间的通信。 当浏览器尝试设置目标服务器与受保护的通信时，在浏览器和服务器协商的协议和要使用的版本。 在浏览器和服务器成功与彼此的列表的受支持的协议和版本中，匹配时，他们选择优先级最高的匹配项。 如果启用此策略设置，浏览器进行协商，或通过从下拉列表中选择的加密方法中不协商的加密隧道。 如果禁用或未配置此策略设置，则用户可以选择加密方法在浏览器支持。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067057)

  **默认**: 2 个项目： TLS 1.1 版和 TLS v1.2  
  *选择向下箭头以显示可以选择此设置的选项。*
  
- **Internet Explorer 已锁定 Internet 区域的 SmartScreen**  
  此策略设置用于控制 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 如果启用此策略设置，则 SmartScreen 筛选器会扫描此区域中的页面来查找恶意内容。 如果禁用此策略设置，则 SmartScreen 筛选器不会扫描此区域中的页面来查找恶意内容。 如果未配置此策略设置，则用户可以选择 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 注意：在 Internet Explorer 7 中，此策略设置控制钓鱼网站筛选器是否扫描此区域中的页面来查找恶意内容。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **默认值**：已启用 
  
- **Internet Explorer 受限制区域在 iFrame 中启动应用程序和文件**  
  利用此策略设置，可以管理是否可以运行应用程序以及是否可以从此区域中页面的 HTML 中的 IFRAME 引用下载文件。 如果启用此策略设置，则用户无需干预就可以从此区域中页面上的 IFRAME 运行应用程序和下载文件。 如果在下拉框中选择了“提示”，则会询问用户选择是否从此区域中页面上的 IFRAME 运行应用程序以及下载文件。 如果禁用此策略设置，则会阻止用户从此区域中页面上的 IFRAME 运行应用程序以及下载文件。 如果未配置此策略设置，则会阻止用户在此区域中的页面上运行应用程序以及从 IFRAME 下载文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **默认值**：禁用 
  
- **Internet Explorer 绕过 SmartScreen 中不常见文件的警告**  
  此策略设置确定用户是否可绕过 SmartScreen 筛选器发出的警告。 有关 Internet Explorer 用户通常不从 Internet 下载的可执行文件，SmartScreen 筛选器会警告用户。 如果启用此策略设置，则 SmartScreen 筛选器警告会阻止用户。 如果禁用或未配置此策略设置，则用户可以绕过 SmartScreen 筛选器警告。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **默认值**：已禁用  
  
- **Internet Explorer Internet 区域弹出窗口阻止程序**  
  利用此策略设置，可管理是否显示不需要的弹出窗口。 不会阻止最终用户单击链接时打开的弹出窗口。 如果启用此策略设置，将阻止显示大多数不需要的弹出窗口。 如果禁用此策略设置，则不会阻止显示弹出窗口。 如果未配置此策略设置，将阻止显示大多数不需要的弹出窗口。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **默认值**：启用  
  
- **Internet Explorer 进程一致的 MIME 处理**  
  Internet Explorer 包含封装其所附加的 HTML 元素的特定功能的动态二进制行为组件。 此策略设置控制是否阻止或允许二进制行为安全限制设置。 如果启用此策略设置，则阻止文件资源管理器和 Internet Explorer 进程的二进制行为。 如果禁用此策略设置，则允许文件资源管理器和 Internet Explorer 进程的二进制行为。 如果不配置此策略设置，则阻止文件资源管理器和 Internet Explorer 进程的二进制行为。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **默认值**：已启用  
  
- **Internet Explorer 受限制区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **默认值**：禁用 java  
    
  
- **Internet Explorer Active X 控件处于保护模式**  
  启用增强保护模式时，此策略设置可阻止 ActiveX 控件在保护模式下运行。 用户安装了与增强保护模式不兼容的 ActiveX 控件且网站试图加载该控件时，Internet Explorer 会通知用户并提供以常规保护模式运行网站的选项。 此策略设置禁用此通知，并强制所有网站以增强保护模式运行。 增强保护模式通过在 64 位版本的 Windows 上使用 64 位进程，提供更多的保护来防范恶意网站。 对于至少运行 Windows 8 的计算机，增强保护模式还限制 Internet Explorer 可从注册表和文件系统中进行读取的位置。 启用了增强保护模式，并且用户遇到试图加载与增强保护模式不兼容的 ActiveX 控件的网站时，Internet Explorer 会通知用户并为该特定网站提供禁用增强保护模式选项。 如果启用此策略设置，Internet Explorer 将不为用户提供禁用增强保护模式的选项。 所有保护模式的网站都将以增强保护模式运行。 如果禁用或未配置此策略设置，Internet Explorer 会通知用户，并提供以常规保护模式运行不兼容 ActiveX 控件的网站的选项。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 受限制区域加载 XAML 文件**  
  利用此策略设置，可管理 Extensible Application Markup Language (XAML) 文件的加载。 XAML 是基于 XML 的声明性标记语言，通常用于创建可充分利用 Windows Presentation Foundation 的丰富用户界面和图形。 如果启用此策略设置，并将下拉列表框设置为“启用”，则会自动在 Internet Explorer 中自动加载 XAML 文件。 用户无法更改此行为。 如果将下拉列表框设为“提示”，系统则会提示用户加载 XAML 文件。 如果禁用此策略设置，则不会在 Internet Explorer 中加载 XAML 文件。 用户无法更改此行为。 如果未配置此策略设置，则用户可以决定是否在 Internet Explorer 中加载 XAML 文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **默认值**：禁用  
  
- **Internet Explorer 进程脚本化窗口的安全限制**  
  Internet Explorer 允许脚本以编程方式打开、重设大小以及重新定位各种类型的窗口。 Window 限制的安全功能可限制弹出窗口、禁止脚本显示用户看不到标题和状态栏的窗口，或混淆其他 Windows 的标题和状态栏。 如果启用此策略设置，则会限制所有进程的脚本化窗口。 如果禁用或不配置此策略设置，则不限制脚本化窗口。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **默认值**：已启用   
  
- **Internet Explorer 受限制区域运行 Active X 控件和插件**  
  利用此策略设置，可以管理是否可以在指定区域的页面上运行 ActiveX 控件和插件。 如果启用此策略设置，控件和插件则无需用户干预即可运行。 如果在下拉列表框中选择“提示”，系统将询问用户选择是否允许控件或插件运行。 如果禁用此策略设置，则将阻止控件和插件运行。 如果不配置此策略设置，则将阻止控件和插件运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **默认值**：禁用  
  
- **Internet Explorer 受限制区域脚本化标记为安全脚本的 Active X 控件**  
  利用此策略设置，可管理标记为安全脚本的 ActiveX 控件是否可以与脚本交互。 如果启用此策略设置，则无需用户干预即可自动进行脚本交互。 如果在下拉列表框中选择“提示”，系统会询问用户选择是否允许脚本交互。 如果禁用此策略设置，则将阻止进行脚本交互。 如果未配置此策略设置，则将阻止进行脚本交互。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **默认值**：禁用  
  
- **Internet Explorer 受限制区域登录选项**  
  利用此策略设置，可以管理登录选项的设置。 如果启用此策略设置，则可以从下列登录选项中进行选择。 
  - *匿名登录* - 使用匿名登录以禁用 HTTP 身份验证并只为通用 Internet 文件系统 (CIFS) 协议使用来宾帐户。 
  - *提示* - 使用提示输入用户名和密码以询问用户的用户 ID 和密码。 询问用户后，可在会话的其余部分中以无提示方式这些值。 
  - *仅在 Intranet 区域中自动登录* - 使用此选项询问用户在其他区域中的用户 ID 和密码。 询问用户后，可在会话的其余部分中以无提示方式这些值。 
  - *使用当前用户名和密码自动登录* - 使用此选项尝试使用 Windows NT 质询响应进行登录（也称为 NTLM 验证）。 如果服务器支持 Windows NT 质询响应，将使用用户的网络用户名和密码进行登录。 如果服务器不支持 Windows NT 质询响应，则要求用户提供用户名和密码。 

  如果禁用此策略设置，则登录设置为“仅在 Intranet 区域中自动登录”  。 如果不配置此策略设置，则将登录设置为提示输入用户名和密码  。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **默认值**：匿名  
  
- **Internet Explorer 受信任区域初始化和脚本化未标记为安全的 Active X 控件**  
  利用此策略设置，可管理未标记为安全的 ActiveX 控件。 如果启用此策略设置，则无需为不受信任的数据或脚本设置对象安全即可运行、带参数加载和脚本化 ActiveX 控件。 除安全区域和管理区域外，不建议使用此设置。 此设置忽略“脚本化标记为可安全脚本化的 ActiveX 控件”选项，导致对不安全的和安全的控件均进行初始化和脚本化。 如果启用此策略设置并在下拉框中选择“提示”，则将询问用户是否允许带参数加载或脚本化控件。 如果禁用此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。 如果未配置此策略设置，系统会询问用户是否允许带参数加载或脚本化该控件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **默认值**：禁用  
  
- **Internet Explorer 检查服务器证书吊销**  
  利用此策略设置，可以管理 Internet Explorer 是否将检查服务器证书的吊销状态。 证书已泄露或不再有效时，将吊销证书。此选项保护用户不向可能具有欺骗性或不安全的网站提交机密数据。 如果启用此策略设置，Internet Explorer 将检查以查看是否已吊销服务器证书。 如果禁用此策略设置，Internet Explorer 将不会检查服务器证书，查看是否已吊销该证书。 如果不配置此策略设置，Internet Explorer 将不会检查服务器证书，查看是否已吊销该证书。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **默认值**：已启用 
  
- **Internet Explorer Internet 区域低权限站点**  
  使用此策略设置，可以管理来自低特权区域的网站（如受限制的站点）是否可以导航到此区域。 如果启用此策略设置，低权限区域的网站可在此区域中打开新窗口，或导航到此区域。 安全区域运行时将不具有由“区域提升保护”安全功能提供的额外一层安全性。 如果在下拉列表框中选择“提示”，则会在将要发生可能有风险的导航时向用户发出警告。 如果禁用此策略设置，将阻止可能有害的导航。 Internet Explorer 安全功能在此区域中处于启用状态，如“区域提升保护”功能控件中所设置的那样。 如果未配置此策略设置，低权限区域的站点可在此区域中打开新窗口，或导航到此区域。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **默认值**：禁用  
  
- **Internet Explorer 受限制区域文件下载**  
  利用此策略设置，可以管理是否允许从该区域下载文件。 此选项由包含下载链接的页面区域确定，而不是由传送文件的区域确定。 如果启用此策略设置，则可以从该区域下载文件。 如果禁用此策略设置，则阻止从该区域下载文件。 如果未配置此策略设置，则阻止从该区域下载文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **默认值**：禁用  
  
- **Internet Explorer Internet 区域运行使用验证码签名的 .NET Framework 相关组件**  
  利用此策略设置，可管理用验证码签名的 .NET 框架组件是否可以从 Internet Explorer 执行。 这些组件包括从对象标记中引用的托管控件和从链接中引用的托管可执行文件。 如果启用此策略设置，则 Internet Explorer 将执行已签名的托管组件。 如果在下拉框中选择“提示”，则 Internet Explorer 将提示用户确定是否执行签名的托管组件。 如果禁用此策略设置，Internet Explorer 将不执行已签名的托管组件。 如果未配置此策略设置，Internet Explorer 将不执行已签名的托管组件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **默认值**：禁用  
  
- **Internet Explorer 阻止每个用户安装 Active X 控件**  
  利用此策略设置，可阻止基于每个用户安装 ActiveX 控件。 如果启用此策略设置，则无法基于每个用户安装 ActiveX 控件。 如果禁用或未配置此策略设置，则可以基于每个用户安装 ActiveX 控件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **默认值**：已启用  
  
- **Internet Explorer 阻止管理 SmartScreen 筛选器**  
  此策略设置阻止用户管理 SmartScreen 筛选器，如果已知用户访问的网站以欺诈方式试图通过“钓鱼”骗取个人信息，或已知含有恶意软件，则该筛选器向用户发出警告。 如果启用此策略设置，则系统不会提示用户打开 SmartScreen 筛选器。 不在筛选器允许列表上的所有网站地址都会自动发送给 Microsoft 而不提示用户。 如果禁用或未配置此策略设置，则系统会在首次运行体验过程中提示用户确定是否要打开 SmartScreen 筛选器。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **默认值**：启用  
  
- **Internet Explorer 进程 MIME 探查安全功能**  
  此策略设置确定 Internet Explorer MIME 探查是否会阻止将某种类型的文件提升为更危险的文件类型。 如果启用此策略设置，则 MIME 探查决不会将某种类型的文件提升为更危险的文件类型。 如果禁用此策略设置，则 Internet Explorer 进程会允许 MIME 探查将某种类型的文件提升为更危险的文件类型。 如果未配置此策略设置，则 MIME 探查决不会将某种类型的文件提升为更危险的文件类型。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **默认值**：已启用  
  
- **Internet Explorer 受限区域下载已签名的 ActiveX 控件**  
  利用此策略设置，可管理用户是否可以从此区域中的页面下载已签名的 ActiveX 控件。 如果启用此策略，则用户无需干预即可下载已签名的控件。 如果在下拉框中选择“提示”，则会询问用户是否下载由不受信任的发布者签名的控件。 将自动下载由受信任的发行者签名的代码。 如果禁用此策略设置，则无法下载已签名的控件。 如果未配置此策略设置，则会询问用户是否下载由不受信任的发行者签名的控件。 将自动下载由受信任的发行者签名的代码。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **默认值**：禁用  
  
- **Internet Explorer 自动完成**  
  此“自动完成”功能可以记忆和建议表单上的用户名和密码。 如果启用此设置，则用户无法更改“表单上的用户名和密码”或“提示我保存密码”。 “表单上的用户名和密码”的“自动完成”功能已启用。 必须确定是否选择“提示我保存密码”。 如果禁用此设置，则用户无法更改“表单上的用户名和密码”或“提示我保存密码”。 将关闭“表单上的用户名和密码”的“自动完成”功能。 用户也无法选择得到保存密码的提示。 如果未配置此设置，则用户有权利启用“表单上的用户名和密码”的“自动完成”和提示保存密码的选项。 若要显示此选项，请用户打开“Internet 选项”对话框，依次单击“内容”选项卡和“设置”按钮。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **默认值**：已禁用  
  
- **Internet Explorer internet 区域允许运行 VBscript**  
  使用此策略设置，可确定 VBScript 是否可以在特定 Internet Explorer 区域的页面中运行。 选项包括： 
  - 启用  - VBScript 在特定区域的页面上运行，无需任何交互。 
  - 提示  - 系统提示员工是否允许 VBScript 在该区域中运行。 
  - 禁用  - 阻止 VBScript 在该区域运行。 如果禁用或未配置此策略设置，则 VBScript 可以在指定区域运行，且无需任何交互。    

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **默认值**：禁用  
  
- **Internet Explorer 受限区域仅允许已批准的域使用 TDC ActiveX 控件**  
  此策略设置控制用户是否可以在网站上运行 TDC ActiveX 控件。 如果启用此策略设置，则 TDC ActiveX 控件不会从此区域中的网站运行。 如果禁用此策略设置，TDC ActiveX 控件会从此区域中的所有站点运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **默认值**：已启用  
  
- **Internet Explorer 受信任区域不针对 Active X 控件运行反恶意软件**  
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **默认值**：已禁用 
  
- **Internet Explorer 本地计算机区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则权限设置为“安全级 - 中”。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **默认值**：禁用 java 
  
- **Internet Explorer intranet 区域不针对 ActiveX 控件运行反恶意软件**  
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **默认值**：已禁用  

- **Internet Explorer 受限区域 Scriptlet**  
  使用此策略设置，可以管理用户是否可以运行 Scriptlet。 如果启用此策略设置，则用户可以运行 Scriptlet。 如果禁用此策略设置，则用户无法运行 Scriptlet。 如果未配置此策略设置，则用户可以启用或禁用 Scriptlet。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 进程通知栏**  
  使用此策略设置，可以管理在文件或代码的安装受限制时是否为 Internet Explorer 进程显示通知栏。 默认情况下，为 Internet Explorer 进程显示通知栏。 如果启用此策略设置，则会显示 Internet Explorer 进程的通知栏。 如果禁用此策略设置，则不会显示 Internet Explorer 进程的通知栏。 如果未配置此策略设置，则不会显示 Internet Explorer 进程的通知栏。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **默认值**：已启用  
  
- **Internet Explorer internet 区域下载已签名的 ActiveX 控件**  
  利用此策略设置，可管理用户是否可以从此区域中的页面下载已签名的 ActiveX 控件。 如果启用此策略，则用户无需干预即可下载已签名的控件。 如果在下拉框中选择“提示”，则会询问用户是否下载由不受信任的发布者签名的控件。 将自动下载由受信任的发行者签名的代码。 如果禁用此策略设置，则无法下载已签名的控件。 如果未配置此策略设置，则会询问用户是否下载由不受信任的发行者签名的控件。 将自动下载由受信任的发行者签名的代码。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **默认值**：禁用  
  
- **Internet Explorer 受限区域智能屏幕**  
  此策略设置控制 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 如果启用此策略设置，则 SmartScreen 筛选器会扫描此区域中的页面来查找恶意内容。 如果禁用此策略设置，则 SmartScreen 筛选器不会扫描此区域中的页面来查找恶意内容。 如果未配置此策略设置，则用户可以选择 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 注意：在 Internet Explorer 7 中，此策略设置控制钓鱼网站筛选器是否扫描此区域中的页面来查找恶意内容。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **默认值**：已启用  
  
- **Internet Explorer 删除过时 ActiveX 控件的“运行这一次”按钮**  
  使用此策略设置，可以阻止用户查看，以及在 Internet Explorer 中运行特定的过时 ActiveX 控件。 如果启用此策略设置，则 Internet Explorer 阻止过时的 ActiveX 控件时显示的警告消息中不会向用户显示“运行这一次”按钮。 如果禁用或未配置此策略设置，则 Internet Explorer 阻止过时的 ActiveX 控件时显示的警告消息中会向用户显示“运行这一次”按钮。 单击此按钮允许用户运行一次过时的 ActiveX 控件。 有关详细信息，请参阅 Internet Explorer TechNet 库中的“过时的 ActiveX 控件”。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **默认值**：已启用 
  
- **Internet Explorer internet 区域在 iFrame 中启动应用程序和文件**  
  利用此策略设置，可管理是否可以从此区域中页面的 HTML 中的一个 IFRAME 引用运行应用程序和下载文件。 如果启用此策略设置，则用户无需干预就可以从此区域中页面上的 IFRAME 运行应用程序和下载文件。 如果在下拉框中选择了“提示”，则会询问用户选择是否从此区域中页面上的 IFRAME 运行应用程序以及下载文件。 如果禁用此策略设置，则会阻止用户从此区域中页面上的 IFRAME 运行应用程序以及下载文件。 如果未配置此策略设置，则会询问用户选择是否从此区域中页面上的 IFRAME 运行应用程序以及下载文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **默认值**：禁用 
  
- **Internet Explorer 受限区域跨不同域导航窗口和框架**  
  当来源和目标位于不同的窗口时，此策略设置可用于设置用来将内容从一个域拖动到另一个域的选项。 如果启用此策略设置并单击“启用”，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。 如果启用此策略设置并单击“禁用”，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户无法更改此设置。 在 Internet Explorer 10 中，如果禁用或未配置此策略设置，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户可以在“Internet 选项”对话框中更改此设置。 在 Internet Explorer 9 及更早版本中，如果禁用或未配置此策略，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **默认值**：禁用  
  
- **Internet Explorer internet 区域智能屏幕**  
  此策略设置控制 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 如果启用此策略设置，则 SmartScreen 筛选器会扫描此区域中的页面来查找恶意内容。 如果禁用此策略设置，则 SmartScreen 筛选器不会扫描此区域中的页面来查找恶意内容。 如果未配置此策略设置，则用户可以选择 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 注意：在 Internet Explorer 7 中，此策略设置控制钓鱼网站筛选器是否扫描此区域中的页面来查找恶意内容。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **默认值**：已启用  
  
- **Internet Explorer 锁定受信任的区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **默认值**：禁用 java 
  
- **Internet Explorer 检查已下载程序的签名**  
  利用此策略设置，可管理 Internet Explorer 是否要在下载可执行程序之前检查用户计算机上的数字签名（用于标识已签名软件的发行者并验证是否未对其进行过修改或篡改）。 如果启用此策略设置，则在将可执行程序下载到用户计算机之前，Internet Explorer 会检查可执行程序的数字签名并显示其标识。 如果禁用此策略设置，则在将可执行程序下载到用户计算机之前，Internet Explorer 不会检查可执行程序的数字签名，也不显示其标识。 如果未配置此策略，则在将可执行程序下载到用户计算机之前，Internet Explorer 不会检查可执行程序的数字签名，也不显示其标识。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **默认值**：已启用  
  
- **Internet Explorer Web 浏览器控件的受限区域脚本编写**  
  此策略设置控制页面是否可以通过脚本控制嵌入的 WebBrowser 控件。 如果启用此策略设置，则允许脚本访问 WebBrowser 控件。 如果禁用此策略设置，则不允许脚本访问 WebBrowser 控件。 如果不配置此策略设置，则用户可以启用或禁用对 WebBrowser 控件的脚本访问。 默认情况下，只有在本地计算机和 Intranet 区域中才允许脚本访问 WebBrowser 控件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 受限区域跨站点脚本筛选**  
  此策略控制跨站点脚本 (XSS) 筛选是否会检测并阻止跨站点脚本注入此区域中的网站。 如果启用此策略设置，则对此区域中的站点启用 XSS 筛选，并且 XSS 筛选尝试阻止跨站脚本注入。 如果禁用此策略设置，则对此区域中的站点禁用 XSS 筛选，并且 Internet Explorer 允许跨站点脚本注入。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **默认值**：已启用  
  
- **Internet Explorer 受限区域二进制文件和脚本行为**  
  使用此策略设置，可以管理动态二进制文件和脚本行为：用于为相应 HTML 元素封装特定功能的组件（组件附加到这些 HTML 元素）。 如果启用此策略设置，则二进制文件和脚本行为都可用。 如果在下拉框中选择了“管理员批准”，则只有在“二进制文件行为安全限制”策略下的“管理员批准的行为”中列出的行为才可用。 如果禁用此策略设置，除非应用程序已实现自定义安全管理器，否则二进制文件和脚本行为都不可用。 如果未配置此策略设置，除非应用程序已实现自定义安全管理器，否则二进制文件和脚本行为都不可用。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **默认值**：禁用  
  
- **Internet Explorer 安全设置检查**  
  此策略设置关闭安全设置检查功能，该功能检查 Internet Explorer 安全设置，以确定这些设置将 Internet Explorer 置于不安全状态的时间。 如果启用此策略设置，则关闭该功能。 如果禁用或未配置此策略设置，则启用该功能。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **默认值**：已启用  
  
- **Internet Explorer internet 区域对潜在不安全文件的安全警告**  
  此策略设置控制在用户尝试打开可执行文件或其他潜在不安全文件（例如，使用“文件资源管理器”从 Intranet 文件共享中获取）时，是否出现“打开文件 - 安全警告”消息。 如果启用此策略设置并且将下拉框设置为“启用”，则打开这些文件时不显示安全警告。 如果将下拉框设置为“提示”，则打开文件之前显示安全警告。 如果禁用此策略设置，则无法打开这些文件。 如果未配置此策略设置，则用户可以配置计算机处理这些文件的方式。 默认情况下，这些文件在受限制区域中设置为阻止，在 Intranet 和本地计算机区域中设置为启用，在 Internet 和受信任区域中设置为提示。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **默认值**：提示  
  
- **Internet Explorer intranet 区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则权限设置为“安全级 - 中”。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **默认值**：高安全性 
  
- **Internet Explorer 阻止过时 ActiveX 控件**   
  此策略设置可确定 Internet Explorer 是否会阻止特定的过时 ActiveX 控件。 过时的 ActiveX 控件在 Intranet 区域中不受阻止。 如果启用此策略，则 Internet Explorer 会停止阻止过时的 ActiveX 控件。 如果禁用或未配置此策略设置，则 Internet Explorer 会继续阻止特定的过时 ActiveX 控件。 有关详细信息，请参阅 Internet Explorer TechNet 库中的“过时的 ActiveX 控件”。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **默认值**：已启用  
  
- **Internet Explorer 受限区域弹出窗口阻止程序**  
  利用此策略设置，可管理是否显示不需要的弹出窗口。 不会阻止最终用户单击链接时打开的弹出窗口。 如果启用此策略设置，将阻止显示大多数不需要的弹出窗口。 如果禁用此策略设置，则不会阻止显示弹出窗口。 如果未配置此策略设置，将阻止显示大多数不需要的弹出窗口。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **默认值**：启用  
  
- **Internet Explorer 进程 MK 协议安全限制**  
  MK 协议安全限制策略设置通过阻止 MK 协议来减少攻击外围应用。 MK 协议上托管的资源将失败。 如果启用此策略设置，则将阻止文件资源管理器和 Internet Explorer 的 MK 协议，并且 MK 协议上托管的资源将失败。 如果禁用此策略设置，应用程序可以使用 MK 协议 API。 MK 协议上托管的资源将适用于文件资源管理器和 Internet Explorer 进程。 如果未配置此策略设置，则将阻止文件资源管理器和 Internet Explorer 的 MK 协议，并且 MK 协议上托管的资源将失败。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **默认值**：已启用  
  
- **Internet Explorer 受信任区域 java 权限**   
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则权限设置为“低安全性”。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **默认值**：高安全性  
  
- **Internet Explorer 受限区域的 java 小程序脚本编写**  
  利用此策略设置，可管理是否将小程序公开到该区域内的脚本中。 如果启用此策略设置，脚本可以在无需用户干预的情况下自动访问小程序。 如果在下拉列表框中选择“提示”，系统会询问用户选择是否允许脚本访问小程序。 如果禁用此策略设置，将阻止脚本访问小程序。 如果未配置此策略设置，将阻止脚本访问小程序。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **默认值**：禁用  
  
- **Internet Explorer 已锁定限制区域的 java 权限**   
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **默认值**：禁用 java 
  
- **Internet Explorer Internet 区域仅允许已批准的域使用 ActiveX 控件**   
  此策略设置控制系统是否提示用户允许 ActiveX 控件在安装 ActiveX 控件的网站以外的网站上运行。 如果启用此策略设置，系统会在 ActiveX 控件可以在此区域中的网站上运行之前提示用户。 用户可以选择允许控件在当前站点或所有站点上运行。 如果禁用此策略设置，用户不会看到每个站点上的 ActiveX 提示，并且 ActiveX 控件可以在此区域中的所有站点上运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **默认值**：已启用  
  
- **Internet Explorer 包括所有网络路径**  
  Internet Explorer 包括所有网络路径。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **默认值**：已禁用 
  
- **Internet Explorer Internet 区域保护模式**  
  此策略设置允许启用保护模式。 保护模式通过减少 Internet Explorer 可在注册表和文件系统中写入的位置，帮助保护 Internet Explorer 不受攻击。 如果启用此策略设置，将启用保护模式。 用户无法关闭保护模式。 如果禁用此策略设置，将关闭保护模式。 用户无法启用保护模式。 如果未配置此策略设置，则用户可以启用或关闭保护模式。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **默认值**：启用 
  
- **Internet Explorer Intranet 区域初始化和脚本化未标记为安全的 ActiveX 控件**  
  利用此策略设置，可管理未标记为安全的 ActiveX 控件。 如果启用此策略设置，则无需为不受信任的数据或脚本设置对象安全即可运行、带参数加载和脚本化 ActiveX 控件。 除安全区域和管理区域外，不建议使用此设置。 此设置忽略“脚本化标记为可安全脚本化的 ActiveX 控件”选项，导致对不安全的和安全的控件均进行初始化和脚本化。 如果启用此策略设置并在下拉框中选择“提示”，则将询问用户是否允许带参数加载或脚本化控件。 如果禁用此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。 如果未配置此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **默认值**：禁用 
  
- **Internet Explorer 已锁定限制区域的 Smart Screen**   
  此策略设置用于控制 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 如果启用此策略设置，则 SmartScreen 筛选器会扫描此区域中的页面来查找恶意内容。 如果禁用此策略设置，则 SmartScreen 筛选器不会扫描此区域中的页面来查找恶意内容。 如果未配置此策略设置，则用户可以选择 SmartScreen 筛选器是否扫描此区域中的页面来查找恶意内容。 注意：在 Internet Explorer 7 中，此策略设置控制钓鱼网站筛选器是否扫描此区域中的页面来查找恶意内容。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **默认值**：已启用  
  
- **Internet Explorer 故障检测**  
  利用此策略设置，可管理附加组件管理的故障检测功能。 如果启用此策略设置，Internet Explorer 中出现的故障将显示 Windows XP Professional Service Pack 1 及更早版本中出现的行为，即调用 Windows 错误报告。 Windows 错误报告的所有策略设置继续应用。 如果禁用或未配置此策略设置，则附加组件管理的故障检测功能将正常运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **默认值**：已禁用  
  
- **Internet Explorer internet 区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则权限设置为“高安全性”。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **默认值**：禁用 java  
  
- **Internet Explorer 受限制区域的活动脚本编制**  
  利用此策略设置，可管理区域中页面上的脚本代码是否运行。 如果启用此策略设置，则区域中页面上的脚本代码可自动运行。 如果在下拉列表框中选择“提示”，系统会询问用户选择是否允许区域中页面上的脚本代码运行。 如果禁用此策略设置，则会阻止区域中页面上的脚本代码运行。 如果未配置此策略设置，则会阻止区域中页面上的脚本代码运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **默认值**：禁用  
  
- **Internet Explorer internet 区域登录选项**  
  利用此策略设置，可以管理登录选项的设置。 如果启用此策略设置，则可以从下列登录选项中进行选择。 匿名登录，以禁用 HTTP 验证并只为通用 Internet 文件系统 (CIFS) 协议使用来宾帐户。 提示用户名和密码以询问用户的用户 ID 和密码。 询问用户后，可在会话的剩余阶段中自动使用这些值。 仅在 Intranet 区域中自动登录，以询问用户在其他区域中的用户 ID 和密码。 询问用户后，可在会话的其余部分中以无提示方式这些值。 用当前用户名和密码自动登录，以尝试使用 Windows NT 质询响应进行登录（也称为 NTLM 验证）。 如果服务器支持 Windows NT 质询响应，将使用用户的网络用户名和密码登录。 如果服务器不支持 Windows NT 质询响应，则要求用户提供用户名和密码。 如果禁用此策略设置，则登录设置为“仅在 Intranet 区域中自动登录”。 如果不配置此策略设置，则登录设置为“仅在 Intranet 区域中自动登录”。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **默认值**：提示  
  
- **Internet Explorer 限制区域允许 vbscript 运行**   
  使用此策略设置，可以管理是否可以从 Internet Explorer 中指定区域的页面运行 VBScript。 如果在下拉框中选择“启用”，则 VBScript 无须用户干预即可运行。 如果在下拉框中选择“提示”，则会询问用户选择是否允许 VBScript 运行。 如果在下拉框中选择“禁用”，则会阻止 VBScript 运行。 如果未配置或禁用此策略设置，则会阻止 VBScript 运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **默认值**：禁用  
  
- **Internet Explorer internet 区域在多个窗口之间拖动不同域中的内容**  
  当来源和目标位于不同的窗口时，此策略设置可用于设置用来将内容从一个域拖动到另一个域的选项。 如果启用此策略设置并单击“启用”，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。 如果启用此策略设置并单击“禁用”，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户无法更改此设置。 在 Internet Explorer 10 中，如果禁用或未配置此策略设置，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户可以在“Internet 选项”对话框中更改此设置。 在 Internet Explorer 9 及更早版本中，如果禁用或未配置此策略，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **默认值**：已禁用 
  
- **Internet Explorer intranet 区域初始化和脚本化未标记为安全的 ActiveX 控件**  
  利用此策略设置，可管理未标记为安全的 ActiveX 控件。 如果启用此策略设置，则无需为不受信任的数据或脚本设置对象安全即可运行、带参数加载和脚本化 ActiveX 控件。 除安全区域和管理区域外，不建议使用此设置。 此设置忽略“脚本化标记为可安全脚本化的 ActiveX 控件”选项，导致对不安全的和安全的控件均进行初始化和脚本化。 如果启用此策略设置并在下拉框中选择“提示”，则将询问用户是否允许带参数加载或脚本化控件。 如果禁用此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。 如果未配置此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **默认值**：禁用 
  
- **Internet Explorer 下载附件**  
  此策略设置可阻止用户将源中的附件（文件附件）下载到用户的计算机。 如果启用此策略设置，则用户无法通过“源属性”页设置源同步引擎来下载附件。 开发人员无法通过源 API 更改下载设置。 如果禁用或未配置此策略设置，则用户可以通过“源属性”页设置源同步引擎来下载附件。 开发人员可以通过源 API 更改下载设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 受限区域下载未签名的 ActiveX 控件**  
  利用此策略设置，可管理用户是否可以从此区域中下载未签名的 ActiveX 控件。 这样的代码有潜在危险，特别是在代码来自不受信任的区域的情况下。 如果启用此策略设置，则用户无需干预即可运行未签名的控件。 如果在下拉框中选择“提示”，则会询问用户选择是否允许运行未签名的控件。 如果禁用此策略设置，则用户无法运行未签名的控件。 如果未配置此策略设置，则用户无法运行未签名的控件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **默认值**：禁用  
  
- **Internet Explorer internet 区域在窗口内拖动不同域中的内容**  
  利用此策略设置，可管理用户是否可以从此区域中下载未签名的 ActiveX 控件。 这样的代码有潜在危险，特别是在代码来自不受信任的区域的情况下。 如果启用此策略设置，则用户无需干预即可运行未签名的控件。 如果在下拉框中选择“提示”，则会询问用户选择是否允许运行未签名的控件。 如果禁用此策略设置，则用户无法运行未签名的控件。 如果未配置此策略设置，则用户无法运行未签名的控件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 进程限制 ActiveX 安装**   
  此策略设置使托管 Web 浏览器控件的应用程序能够阻止 ActiveX 控件安装的自动提示。 如果启用此策略设置，则 Web 浏览器控件阻止所有进程的 ActiveX 控件安装的自动提示。 如果禁用或未配置此策略设置，则 Web 浏览器控件不会阻止所有进程的 ActiveX 控件安装的自动提示。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **默认值**：已启用  
  
- **Internet Explorer internet 区域 scriptlet**  
  使用此策略设置，可以管理用户是否可以运行 Scriptlet。 如果启用此策略设置，则用户可以运行 Scriptlet。 如果禁用此策略设置，则用户无法运行 Scriptlet。 如果未配置此策略设置，则用户可以启用或禁用 Scriptlet。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **默认值**：禁用  
  
- **Internet Explorer 受限区域拖放或复制和粘贴文件**  
  利用此策略设置，可管理用户是否可以从此区域中的一个源拖动文件或复制和粘贴文件。 如果启用此策略设置，则用户可以自动从此区域拖动文件或复制和粘贴文件。 如果在下拉框中选择“提示”，则会询问用户选择是否从该区域拖动或复制文件。 如果禁用此策略设置，则会阻止用户从该区域拖动文件或者复制和粘贴文件。 如果未配置此策略设置，则会询问用户选择是否从该区域拖动或复制文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **默认值**：禁用  
  
- **Internet Explorer 签名无效的软件**  
  利用此策略设置，可管理即使在签名失效的情况下，用户是否仍然可以安装或运行软件（例如 ActiveX 控件和文件下载）。 签名无效可能表示有人篡改过文件。 如果启用此策略设置，则提示用户安装或运行带有失效签名的文件。 如果禁用此策略设置，则用户无法运行或安装带有无效签名的文件。 如果未配置此策略，则用户可以选择运行或安装带有无效签名的文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **默认值**：已禁用  
  
- **Internet Explorer 受限区域通过脚本复制和粘贴**  
  使用此策略设置，可以管理脚本是否可以在指定区域中执行剪贴板操作（例如，剪切、复制和粘贴）。 如果启用此策略设置，则脚本可以执行剪贴板操作。 如果在下拉框中选择“提示”，则会询问用户是否执行剪贴板操作。 如果禁用此策略设置，则脚本无法执行剪贴板操作。 如果未配置此策略设置，则脚本无法执行剪贴板操作。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **默认值**：禁用  
  
- **Internet Explorer 受限区域在多个窗口之间拖动不同域中的内容**  
  当来源和目标位于不同的窗口时，此策略设置可用于设置用来将内容从一个域拖动到另一个域的选项。 如果启用此策略设置并单击“启用”，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。 如果启用此策略设置并单击“禁用”，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户无法更改此设置。 在 Internet Explorer 10 中，如果禁用或未配置此策略设置，则当来源和目标位于不同的窗口时，用户无法将内容从一个域拖动到另一个域。 用户可以在“Internet 选项”对话框中更改此设置。 在 Internet Explorer 9 及更早版本中，如果禁用或未配置此策略，则当来源和目标位于不同的窗口时，用户可以将内容从一个域拖动到另一个域。 用户无法更改此设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **默认值**：已禁用  
  
- **Internet Explorer 用户添加站点**  
  阻止用户在安全区域添加或删除站点。 安全区域是一组具有相同安全级别的网站。 如果启用此策略，将禁用安全区域的站点管理设置。 （若要了解安全区域的站点管理设置，请在“Internet 选项”对话框中单击“安全”选项卡，然后单击“站点”按钮。）如果禁用或未配置此策略，则用户可以在“受信任的站点”和“受限制的站点”区域中添加或删除网站，还可以修改“本地 Intranet”区域的设置。 此策略阻止用户更改由管理员建立的安全区域的站点管理设置。 注意：“禁用安全页”策略（位于“\用户配置\管理模板\Windows 组件\Internet Explorer\Internet 控制面板”中）可将“安全”选项卡从界面上删除，它优先于此策略。 如果启用该策略，则忽略此策略。 另请参阅“安全区域：仅使用计算机设置”策略。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **默认值**：已禁用  
  
- **Internet Explorer internet 区域脚本启动窗口**  
  使用此设置，可以管理针对脚本启动的弹出窗口和包含标题和状态栏的窗口的限制。 如果启用此策略设置，则不会在此区域中应用 Windows 限制安全。 安全区域运行时将不具有此功能提供的额外一层安全性。 如果禁用此策略设置，则脚本启动的弹出窗口和含标题和状态栏的窗口中包含的可能有害的操作将无法运行。 此区域中会启用此 Internet Explorer 安全功能，如进程的“脚本化 Windows 安全限制”功能控件设置所规定的那样。 如果未配置此策略设置，则脚本启动的弹出窗口和含标题和状态栏的窗口中包含的可能有害的操作将无法运行。 此区域中会启用此 Internet Explorer 安全功能，如进程的“脚本化 Windows 安全限制”功能控件设置所规定的那样。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 安全区域仅使用计算机设置**  
  将安全区域信息应用于同一台计算机的所有用户。 安全区域是一组具有相同安全级别的网站。 如果启用此策略，则用户对安全区域所做的更改将应用于该计算机的所有用户。 如果禁用或未配置此策略，则同一台计算机的用户可以建立各自的安全区域设置。 使用此策略确保将安全区域设置统一地应用于同一台计算机，不会因用户的不同而产生差异。 另请参阅"安全区域：禁止用户更改策略”策略。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **默认值**：已启用  
  
- **Internet Explorer 锁定的本地计算机区域 java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **默认值**：禁用 java 
  
- **Internet Explorer 限制区域不针对 ActiveX 控件运行反恶意软件**   
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **默认值**：已禁用  
  
- **Internet Explorer 受限区域运行用验证码签名的依赖于 .NET Framework 的组件**  
  利用此策略设置，可管理用验证码签名的 .NET 框架组件是否可以从 Internet Explorer 执行。 这些组件包括从对象标记中引用的托管控件和从链接中引用的托管可执行文件。 如果启用此策略设置，则 Internet Explorer 将执行已签名的托管组件。 如果在下拉框中选择“提示”，则 Internet Explorer 将提示用户确定是否执行签名的托管组件。 如果禁用此策略设置，Internet Explorer 将不执行已签名的托管组件。 如果未配置此策略设置，Internet Explorer 将不执行已签名的托管组件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **默认值**：禁用  
  
- **Internet Explorer 受限区域访问数据源**  
  利用此策略设置，可管理 Internet Explorer 是否可以使用 Microsoft XML Parser (MSXML) 或 ActiveX 数据对象 (ADO) 访问其他安全区域的数据。 如果启用此策略设置，用户可以在区域中加载页面，该页面使用 MSXML 或 ADO 访问区域中其他站点的数据。 如果在下拉列表框中选择“提示”，将会提示用户选择是否允许在区域中加载页面，该页面使用 MSXML 或 ADO 访问区域中其他站点的数据。 如果禁用此策略设置，则用户无法在区域中加载使用 MSXML 或 ADO 访问区域中其他站点数据的页面。 如果不配置此策略设置，则用户无法在区域中加载使用 MSXML 或 ADO 访问区域中其他站点数据的页面。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **默认值**：禁用 
  
- **Internet Explorer internet 区域不针对 ActiveX 控件运行反恶意软件**  
  此策略设置用于确定 Internet Explorer 是否针对 ActiveX 控件运行反恶意软件程序，以检查是否可以在页面上安全加载这些控件。 如果启用此策略设置，则 Internet Explorer 不会为了确定是否可安全创建 ActiveX 控件实例而检查反恶意软件程序。 如果禁用此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 如果未配置此策略设置，则 Internet Explorer 始终都会检查反恶意软件程序，以确定是否可安全创建 ActiveX 控件实例。 用户可以使用“Internet Explorer 安全”设置打开或关闭此行为。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **默认值**：已禁用  
  
- **Internet Explorer internet 区域通过脚本复制和粘贴**  
  使用此策略设置，可以管理脚本是否可以在指定区域中执行剪贴板操作（例如，剪切、复制和粘贴）。 如果启用此策略设置，则脚本可以执行剪贴板操作。 如果在下拉框中选择“提示”，则会询问用户是否执行剪贴板操作。 如果禁用此策略设置，则脚本无法执行剪贴板操作。 如果未配置此策略设置，则脚本可以执行剪贴板操作。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **默认值**：禁用  
  
- **Internet Explorer 使用 ActiveX 安装程序服务**  
  使用此策略设置，可以指定如何安装 ActiveX 控件。 如果启用此策略设置，则仅在提供 ActiveX 安装程序服务且配置为允许安装 ActiveX 控件的情况下安装 ActiveX 控件。 如果禁用或未配置此策略设置，则通过标准安装过程安装 ActiveX 控件（包括每用户控件）。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **默认值**：已启用  
  
- **Internet Explorer 进程防止区域提升**  
  Internet Explorer 对它打开的每一个网页施加限制。 这些限制取决于网页的位置（Internet、Intranet、本地计算机区域等）。 例如，本地计算机上的网页具有的安全限制最少，并且这些网页位于本地计算机区域中，这使本地计算机安全区域成为恶意用户的主要攻击目标。 如果启用此策略设置，则对于所有进程，将保护任何区域不会进行区域提升。 如果禁用或未配置此策略设置，则除了 Internet Explorer 或进程列表中的进程以外，其他进程都不会受到这种保护。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **默认值**：已启用  
  
- **Internet Explorer Internet 区域下载未签名的 ActiveX 控件**   
  利用此策略设置，可管理用户是否可以从此区域中下载未签名的 ActiveX 控件。 这样的代码有潜在危险，特别是在代码来自不受信任的区域的情况下。 如果启用此策略设置，则用户无需干预即可运行未签名的控件。 如果在下拉框中选择“提示”，则会询问用户选择是否允许运行未签名的控件。 如果禁用此策略设置，则用户无法运行未签名的控件。 如果未配置此策略设置，则用户无法运行未签名的控件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **默认值**：禁用  
  
- **Internet Explorer Internet 区域跨不同域导航窗口和框架**   
  使用此策略设置，可以控制在不同域中打开窗口和框架的操作以及应用程序的访问。 如果启用此策略设置，用户可以打开其他域的窗口和框架，并访问其他域的应用程序。 如果在下拉列表框中选择“提示”，会询问用户是否允许窗口和框架访问其他域的应用程序。 如果启用此策略设置，则用户无法打开其他域的窗口和框架以访问其他域的应用程序。 如果未配置此策略设置，则用户可以打开其他域的窗口和框架，并访问其他域的应用程序。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **默认值**：禁用  
  
- **Internet ExplorerI Internet 区域通过脚本更新状态栏**  
  使用此策略设置，可以控制是否允许脚本在区域中更新状态栏。 如果启用此策略设置，则脚本可以更新状态栏。 如果禁用或未配置此策略设置，则不允许脚本更新状态栏。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 限制区域在文件上传到服务器时包含本地路径**  
  使用此策略设置，可控制用户通过 HTML 窗体上传文件时是否会发送本地路径信息。 如果发送本地路径信息，则无意中可能向服务器泄露部分信息。 例如，从用户桌面发送的文件可能包含用户名，作为路径的一部分。 如果启用此策略设置，则在用户通过 HTML 窗体上传文件时会发送路径信息。 如果禁用此策略设置，则在用户通过 HTML 窗体上传文件时删除路径信息。 如果不配置此策略设置，则用户可以在通过 HTML 窗体上传文件时选择是否发送路径信息。 默认情况下，发送路径信息。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 进程限制文件下载**   
  使用此策略设置，托管 Web 浏览器控件的应用程序能够阻止自动提示非用户发起的文件下载。 如果启用此策略设置，Web 浏览器控件将针对所有进程，阻止自动提示非用户发起的文件下载。 如果禁用此策略设置，Web 浏览器控件将针对所有进程，不会阻止自动提示非用户发起的文件下载。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **默认值**：已启用  
  
- **Internet Explorer 限制区域仅允许已批准的域使用 ActiveX 控件**   
  此策略设置控制系统是否提示用户允许 ActiveX 控件在安装 ActiveX 控件的网站以外的网站上运行。 如果启用此策略设置，系统会在 ActiveX 控件可以在此区域中的网站上运行之前提示用户。 用户可以选择允许控件在当前站点或所有站点上运行。 如果禁用此策略设置，用户不会看到每个站点上的 ActiveX 提示，并且 ActiveX 控件可以在此区域中的所有站点上运行。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **默认值**：已启用  
  
- **Internet Explorer 限制区域对非标记为安全的 Active X 控件进行初始化和编制脚本**  
  利用此策略设置，可管理未标记为安全的 ActiveX 控件。 如果启用此策略设置，则无需为不受信任的数据或脚本设置对象安全即可运行、带参数加载和脚本化 ActiveX 控件。 除安全区域和管理区域外，不建议使用此设置。 此设置忽略“脚本化标记为可安全脚本化的 ActiveX 控件”选项，导致对不安全的和安全的控件均进行初始化和脚本化。 如果启用此策略设置并在下拉框中选择“提示”，则将询问用户是否允许带参数加载或脚本化控件。 如果禁用此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。 如果未配置此策略设置，则对于无法标记为安全的 ActiveX 控件，不会带参数进行加载或对其编制脚本。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **默认值**：禁用  
  
- **Internet Explorer 用户更改策略**  
  防止用户更改安全区域设置。 安全区域是一组安全级别相同的网站。 如果启用此策略，将禁用 Internet 选项对话框中“安全”选项卡上的“自定义级别”和安全级别滑块。 如果禁用或不配置此策略，用户可以更改安全区域的设置。 此策略可防止用户更改管理员创建的安全区域设置。 注意：“禁用安全页”策略（位于\用户配置\管理模板\Windows 组件\Internet Explorer\Internet 控制面板）优先于此策略，前者从控制面板的 Internet Explorer 中删除“安全”选项卡。 如果启用该策略，则忽略此策略。 另请参阅“安全区域：仅使用计算机设置”策略。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **默认值**：已禁用  
  
- **Internet Explorer 限制区域保护模式**  
  此策略设置允许启用保护模式。 保护模式通过减少 Internet Explorer 可在注册表和文件系统中写入的位置，帮助保护 Internet Explorer 不受攻击。 如果启用此策略设置，将启用保护模式。 用户无法关闭保护模式。 如果禁用此策略设置，将关闭保护模式。 用户无法启用保护模式。 如果未配置此策略设置，则用户可以启用或关闭保护模式。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **默认值**：启用  
  
- **Internet Explorer Internet 区域用户数据暂留**  
  使用此策略设置，可以管理后列位置中的信息保存：浏览器的历史记录、收藏夹、XML 存储或保存到磁盘的网页。 如果已适当配置此策略设置，则当用户返回暂留页面时，可还原页面的状态。 如果启用此策略设置，则用户可以在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。 如果禁用此策略设置，则用户无法在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。 如果未配置此策略设置，则用户可以在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **默认值**：已禁用  
  
- **Internet Explorer Internet 区域 Web 浏览器控件脚本编写**  
 
  此策略设置决定页面是否可以通过脚本控制嵌入的 WebBrowser 控件。 如果启用此策略设置，则允许脚本访问 WebBrowser 控件。 如果禁用此策略设置，则不允许脚本访问 WebBrowser 控件。 如果不配置此策略设置，则用户可以启用或禁用对 WebBrowser 控件的脚本访问。 默认情况下，只有在本地计算机和 Intranet 区域中才允许脚本访问 WebBrowser 控件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 限制区域用户数据暂留**  
  使用此策略设置，可以管理后列位置中的信息保存：浏览器的历史记录、收藏夹、XML 存储或保存到磁盘的网页。 如果已适当配置此策略设置，则当用户返回暂留页面时，可还原页面的状态。 如果启用此策略设置，则用户可以在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。 如果禁用此策略设置，则用户无法在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。 如果未配置此策略设置，则用户无法在浏览器的历史记录、收藏夹、XML 存储中保存信息或直接在保存到磁盘的网页中保存信息。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 锁定 Intranet 区域 Java 权限**  
  利用此策略设置，可管理 Java 小程序的权限。 如果启用此策略设置，则可从下拉列表框中选择选项。 “自定义”，用于单独控制权限设置。 “低安全性”，使小程序能够执行所有操作。 “中等安全性”，使小程序能够在其沙盒（程序只能在其中进行调用的内存中的区域）中运行，以及临时空间（客户端计算机上安全可靠的存储区域）和用户控制的文件 I/O 等功能。 “高安全性”，使小程序能够在其沙盒中运行。 禁用 Java 将阻止任何小程序运行。 如果禁用此策略设置，Java 小程序将无法运行。 如果未配置此策略设置，则会禁用 Java 小程序。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **默认值**：禁用 java  
  
- **Internet Explorer 增强保护模式**  
  增强保护模式通过在 64 位版本的 Windows 上使用 64 位进程，提供更多的保护来防范恶意网站。 对于至少运行 Windows 8 的计算机，增强保护模式还限制 Internet Explorer 可从注册表和文件系统中进行读取的位置。 如果启用此策略设置，将启用增强保护模式。 已启用保护模式的任何区域都将使用增强保护模式。 用户无法禁用增强保护模式。 如果禁用此策略设置，将关闭增强保护模式。 任何已启用“保护模式”的区域都将使用 Internet Explorer 7 中为 Windows Vista 引入的保护模式版本。 如果未配置此策略，用户将能够在“Internet 选项”对话框的“高级”选项卡上启用或关闭增强保护模式。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **默认值**：已启用  
  
- **Internet Explorer 绕过 SmartScreen 警告**  
  此策略设置确定用户是否可绕过 SmartScreen 筛选器发出的警告。 有关 Internet Explorer 用户通常不从 Internet 下载的可执行文件，SmartScreen 筛选器会警告用户。 如果启用此策略设置，则 SmartScreen 筛选器警告会阻止用户。 如果禁用或未配置此策略设置，则用户可以绕过 SmartScreen 筛选器警告。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **默认值**：已禁用  
  
- **Internet Explorer 受限制区域的 meta 刷新**  
  如果网页的创建者使用 Meta 刷新设置（标记）将浏览器重定向到其他网页，则可通过此策略设置管理是否可以将用户的浏览器重定向到其他网页。 如果启用此策略设置，则可将加载包含活动 Meta 刷新设置页面的用户的浏览器重定向到其他网页。 如果禁用此策略设置，则无法将加载包含活动 Meta 刷新设置页面的用户的浏览器重定向到其他网页。 如果不配置此策略设置，则无法将加载包含活动 Meta 刷新设置页面的用户的浏览器重定向到其他网页。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **默认值**：已禁用  
  
## <a name="local-policies-security-options"></a>本地策略安全选项
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions)（策略 CSP - LocalPoliciesSecurityOptions）。 

- **限制对命名管道和共享的匿名访问**  
  启用后，此安全设置会将对共享和管道的匿名访问限制为以下设置：(1) 可以匿名访问的命名管道 (2) 可以匿名访问的共享。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **默认值**：是  
  
- **基于 NTLM SSP 的服务器的最低会话安全性**  
  此安全设置允许服务器要求对 128 位加密和/或 NTLMv2 会话安全性进行协商。 这些值取决于 LAN Manager 身份验证级别安全设置值。 选项包括：需要 NTLMv2 会话安全性：如果未协商消息完整性，则连接将失败。 需要 128 位加密。 如果未协商强加密（128 位），则连接将失败。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **默认值**：需要 NTLM V2 和 128 位加密  
  
- **激活屏幕保护程序前锁屏界面保持不活动状态的分钟数**  
  Windows 会注意登录会话的非活动；如果非活动时间量超过非活动限制，则屏幕保护程序将运行，从而锁定会话。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **默认值**：15
  
- **需要客户端始终对通信进行数字签名** 此安全设置确定是否必须对域成员发起的所有安全通道流量进行签名或加密。 当计算机加入域时，将创建计算机帐户。 稍后，当系统启动时，将使用计算机帐户密码为其域创建具有域控制器的安全通道。 此安全通道用于执行 NTLM 传递身份验证、LSA SID/名称查找等操作。 此设置确定由域成员发起的所有安全通道流量是否满足最低安全要求。 具体而言，确定是否必须对域成员启动的所有安全通道流量进行签名或加密。 如果启用此策略，除非协商对所有安全通道流量的签名或加密，否则将不会建立安全通道。 如果禁用此策略，则将与域控制器协商所有安全通道流量的加密和签名，在这种情况下，签名和加密级别取决于域控制器的版本和以下两种策略的设置：域成员：对安全通道数据进行数字加密（如果可能）域成员：对安全通道数据进行数字签名（如果可能）。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **默认值**：是
  
- **身份验证级别**  
  此安全设置确定用于网络登录的质询/响应身份验证协议。 此选择会影响客户端使用的身份验证协议级别、协商的会话安全性级别以及服务器接受的身份验证级别，如下所示：  
  - 发送 LM 和 NTLM 响应  - 客户端使用 LM 和 NTLM 身份验证，从不使用 NTLMv2 会话安全性；域控制器接受 LM、NTLM 和 NTLMv2 身份验证。 
  - 发送 LM 和 NTLM - 如果进行协商，则发送 NTLMv2  - 客户端使用 LM 和 NTLM 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器接受 LM、NTLM 和 NTLMv2 身份验证。 
  - 仅发送 NTLM 响应  - 客户端仅使用 NTLM 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器接受 LM、NTLM 和 NTLMv2 身份验证。 
  - 仅发送 NTLMv2 响应  - 客户端仅使用 NTLMv2 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器接受 LM、NTLM 和 NTLMv2 身份验证。 
  - *仅发送 NTLMv2 响应。拒绝 LM* - 客户端仅使用 NTLMv2 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器拒绝 LM（只接受 NTLM 和 NTLMv2 身份验证）。 
  - *仅发送 NTLMv2 响应。拒绝 LM 和 NTLM* - 客户端仅使用 NTLMv2 身份验证，并在服务器支持时使用 NTLMv2 会话安全性；域控制器拒绝 LM 和 NTLM（只接受 NTLMv2 身份验证）。  

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  默认值  ：仅发送 NTLMv2 响应。 拒绝 LM 和 NTLM
  
- **阻止客户端向第三方 SMB 服务器发送未加密的密码**  
  如果启用此安全设置，则服务器消息块 (SMB) 重定向程序可以将明文密码发送给在身份验证期间不支持密码加密的非 Microsoft SMB 服务器。 发送未加密的密码是一种安全风险。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **默认值**：是
  
- **要求服务器始终对通信进行数字签名**  
  此安全设置确定 SMB 客户端是否尝试协商进行 SMB 数据包签名。 服务器消息块 (SMB) 协议为 Microsoft 文件和打印共享以及许多其他网络操作（如远程 Windows 管理）提供了基础。 为了防止在传输中修改 SMB 数据包的中间人攻击，SMB 协议支持对 SMB 数据包进行数字签名。 此策略设置确定 SMB 客户端组件在连接到 SMB 服务器时是否尝试协商 SMB 数据包签名。 如果启用此设置，Microsoft 网络客户端将请求服务器在会话设置时执行 SMB 数据包签名。 如果在服务器上启用了数据包签名，则会协商数据包签名。 如果禁用此策略，则 SMB 客户端绝不会协商 SMB 数据包签名。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **默认值**：是
  
- **管理员提升权限提示行为**  
  此策略设置控制针对管理员的提升权限提示的行为。 选项包括： 
    - 不提示，直接提升  - 允许有权限的帐户执行需要提升的操作，而无需同意或凭据。 注意：此选项仅用在大多数受限制的环境中。 
    - 在安全桌面上提示提供凭据  - 当某项操作需要特权提升时，将在安全桌面上提示用户输入有权限的用户名和密码。 如果用户输入有效的凭据，则该操作将使用用户的最高可用权限继续执行。 
    - 在安全桌面上提示提供同意  - 当某项操作需要特权提升时，系统将在安全桌面上提示用户选择“允许”或“拒绝”。 如果用户选择“允许”，则该操作将使用用户的最高可用权限继续执行。 
    - 提示提供凭据  - 当某项操作需要特权提升时，系统将提示用户输入管理用户名和密码。 如果用户输入有效的凭据，则该操作将使用适用的权限继续执行。 
    - 提示提供同意  - 当某项操作需要特权提升时，系统将提示用户选择“允许”或“拒绝”。 如果用户选择“允许”，则该操作将使用用户的最高可用权限继续执行。  
    - 非 Windows 二进制文件提示提供同意  - 当非 Microsoft 应用程序的某项操作需要特权提升时，系统将在安全桌面上提示用户选择“允许”或“拒绝”。 如果用户选择“允许”，则该操作将使用用户的最高可用权限继续执行。 
  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  默认值  ：在安全桌面上提示提供同意
  
- **基于 NTLM SSP 的客户端的最低会话安全性**  
  此安全设置允许客户端要求对 128 位加密和/或 NTLMv2 会话安全性进行协商。 这些值取决于 LAN Manager 身份验证级别安全设置值。 选项包括：
  - 需要 NTLMv2 会话安全性  - 如果未协商 NTLMv 2 协议，则连接将失败。 
  - 需要 128 位加密  - 如果未协商强加密（128 位），则连接将失败。
  - 需要 NTLMv2 和 128 位加密  。  

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067324)  

  默认值  ：需要 NTLM V2 128 加密
  
- **智能卡移除行为**  
    此安全设置确定从智能卡读卡器中取下登录用户的智能卡时发生的情况。 选项包括：
     - 无操作  。 
     - *锁定工作站* - 取下智能卡时将锁定工作站，用户可离开该区域，随身携带智能卡，并仍可维护受保护的会话。
     - 强制注销  - 取下智能卡时自动注销用户。
     - 断开远程桌面会话连接  - 无需注销用户，取下智能卡即可断开会话连接。 用户可通过该选项稍后插入智能卡并恢复会话，或者在另一台配备智能卡读卡器的计算机上恢复会话，而无需再次登录。 如果是本地会话，则此策略与“锁定工作站”的功能相同。
  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **默认值**：锁定工作站
  
- **阻止匿名枚举软件资产管理帐户和共享**  
  此安全设置确定是否允许匿名枚举软件资产管理帐户和共享。 Windows 允许匿名用户执行某些操作，例如枚举域帐户和网络共享的名称。 该操作非常方便，例如，管理员想要授予对不维护相互信任的受信任域中的用户的访问权限。 如果不希望允许匿名枚举软件资产管理帐户和共享，请将此策略设置为“是”  。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **默认值**：是
  
- **用空白密码阻止远程登录**  
  此安全设置确定没有密码保护的本地帐户是否可用于从物理计算机控制台以外的位置登录。 如果启用该设置，没有密码保护的本地帐户必须使用计算机的键盘才能登录。 

  警告  ：物理上不在安全位置的计算机应始终对所有本地用户帐户强制实施强密码策略。 否则，任何对计算机具有物理访问权限的人都可以使用没有密码的用户帐户登录。 这对于便携式计算机尤其重要。 

  如果将此安全策略应用于 Everyone 组，则没有人能够通过远程桌面服务登录。 此设置不影响使用域帐户进行登录。 使用远程交互登录的应用程序可以绕过此设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **默认值**：是
  
- **标准用户提升权限提示行为**  
  此策略设置控制标准用户的提升权限提示行为。 
  - 自动拒绝提升请求  - 当某项操作需要特权提升时，将显示可配置的访问已拒绝错误消息。 以标准用户身份运行桌面的企业可以选择此设置来减少技术支持呼叫次数。 
  - 在安全桌面上提示提供凭据  - 当某项操作需要特权提升时，系统将在安全桌面上提示用户输入其他用户名和密码。 如果用户输入有效的凭据，则该操作将使用适用的权限继续执行。 
  - 提示提供凭据  - 当某项操作需要特权提升时，系统将提示用户输入管理用户名和密码。 如果用户输入有效的凭据，则该操作将使用适用的权限继续执行。  

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  默认值  ：自动拒绝提升请求
  
- **需要管理员的管理员批准模式**  
  此策略设置控制计算机的所有用户帐户控制 (UAC) 策略设置的行为。 如果您更改此策略设置，则必须重新启动计算机。 选项包括：   
  - 未配置  - 禁用管理员批准模式以及所有相关的 UAC 策略设置。 注意：如果禁用此策略设置，则安全中心将通知你操作系统的整体安全性已降低。 
  - 是  - 启用管理员批准模式。 必须启用此策略，并且必须对相关的 UAC 策略设置进行了适当设定，才能允许内置 Administrator 帐户以及所有其他属于管理员组成员的用户在管理员批准模式下运行。  

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **默认值**：是
  
- **阻止匿名枚举软件资产管理帐户**  
  此安全设置确定授予匿名连接到计算机的附加权限。 Windows 允许匿名用户执行某些操作，例如枚举域帐户和网络共享的名称。 该操作非常方便，例如，管理员想要授予对不维护相互信任的受信任域中的用户的访问权限。 此安全选项允许对匿名连接设置以下附加限制： 
  - 是  - 不允许枚举软件资产管理帐户。 此选项将资源的安全权限中的 Everyone 替换为经过身份验证的用户。
  - 未配置  - 没有其他限制。 依赖于默认权限。  
  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **默认值**：是
  
- **允许远程调用安全帐户管理器**  
  此策略设置可以将远程 rpc 连接限制为软件资产管理。 如果未选中该设置，将使用默认安全描述符。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **默认值**：O:BAG:BAD:(A;;RC;;;BA) 

- **使用管理员批准模式**  
  此策略设置控制内置 Administrator 帐户的管理员批准模式行为。 选项包括： 
  - 是  - 内置 Administrator 帐户使用管理员批准模式。 默认情况下，任何需要提升权限的操作都将提示用户批准该操作。 
  - 未配置  - 内置 Administrator 帐户使用完全管理权限运行所有应用程序。 

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **默认值**：是
  
- **允许 UI 访问安全位置的应用程序**  
  此策略控制用户界面辅助功能（UIAccess 或 UIA）程序是否可以自动禁用标准用户使用提升权限提示的安全桌面。 
  - 是  - UIA 程序（包括 Windows 远程协助）自动禁用用于提升权限提示的安全桌面。 如果不禁用“用户帐户控制：提示提升时切换到安全桌面”策略设置，则会在交互式用户桌面而不是安全桌面上出现提示。 
  - 未配置  - 安全桌面只能由交互式桌面的用户禁用，或通过禁用“用户帐户控制：提示提升时切换到安全桌面”策略设置来禁用。  

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **默认值**：是

- **检测应用程序安装和提示提升权限**  
  此策略设置控制计算机应用程序安装检测的行为。 选项包括： 
  - 启用  - 当检测到某个应用程序安装包需要特权提升时，系统将提示用户输入管理用户名和密码。 如果用户输入有效的凭据，则该操作将使用适用的权限继续执行。 
  - 禁用  - 不检测应用程序安装包和提示提升权限。 运行标准用户桌面并使用组策略软件安装或系统管理服务器 (SMS) 等委派安装技术的企业应该禁用此策略设置。 在这种情况下，安装程序检测是没有必要的。  
  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **默认值**：是
  
- **在下一次更改密码时不存储 LAN 管理器哈希值**  
  此安全设置确定在下次更改密码时是否存储新密码的 LAN Manager (LM) 哈希值。 与更强大的加密 Windows NT 哈希相比，LM 哈希相对较弱且容易受到攻击。 由于 LM 哈希存储在安全数据库中的本地计算机上，如果安全数据库受到攻击，可能会泄漏密码。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **默认值**：是

- **将文件和注册表写入错误虚拟化到每用户位置**  
  此策略设置控制应用程序写入失败是否重定向到定义的注册表和文件系统位置。 此策略设置可缓解以管理员身份运行的应用程序，并将运行时应用程序数据写入 %ProgramFiles%、%Windir%、%Windir%\system32 或 HKLM\Software     。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **默认值**：是

## <a name="ms-security-guide"></a>MS 安全指南  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide)（策略 CSP - MSSecurityGuide）。  

- **在网络登录时将 UAC 限制应用于本地帐户**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **默认值**：已启用
  
- **SMB v1 客户端驱动程序启动配置**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **默认值**：已禁用的驱动程序
  
- **SMB v1 服务器**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **默认值**：已禁用
  
- **摘要式身份验证**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **默认值**：已禁用
  
- **结构化的异常处理覆盖保护**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **默认值**：已启用
  
## <a name="mss-legacy"></a>MSS 旧版  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy)（策略 CSP - MSSLegacy）。  

- **网络 IP 源路由保护级别**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **默认值**：最高级别的保护  
  
- **网络忽略除 WINS 服务器之外的 NetBIOS 名称发布的请求**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **默认值**：已启用
  
- **网络 IPv6 源路由保护级别**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **默认值**：最高级别的保护

- **网络 ICMP 重定向替代生成的 OSPF**  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **默认值**：已禁用
  
## <a name="power"></a>电源  
有关详细信息，请参阅 Windows 文档中的 [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power)（策略 CSP - 电源）。  

- **接通电源时需要密码才能唤醒**  
  此策略设置指定在系统从睡眠状态恢复时是否提示用户输入密码。 如果启用或未配置此策略设置，系统从睡眠状态恢复时将提示用户输入密码。 如果禁用此策略设置，系统从睡眠状态恢复时不会提示用户输入密码。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **默认值**：已启用
  
- **电池处于睡眠时的待机状态**  
  此策略设置控制计算机进入睡眠状态时 Windows 是否可以使用待机状态。 如果启用或不配置此策略设置，则 Windows 使用待机状态，将计算机置于睡眠状态。 如果禁用此策略设置，则不允许使用待机状态 (S1-S3)。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **默认值**：已禁用
  
- **计算机接通电源且处于睡眠状态时的待机状态**  
  此策略设置控制计算机进入睡眠状态时 Windows 是否可以使用待机状态。 如果启用或不配置此策略设置，则 Windows 使用待机状态，将计算机置于睡眠状态。 如果禁用此策略设置，则不允许使用待机状态 (S1-S3)。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **默认值**：已禁用
  
- **使用电池时需要密码才能唤醒**  
  此策略设置指定在系统从睡眠状态恢复时是否提示用户输入密码。 如果启用或未配置此策略设置，系统从睡眠状态恢复时将提示用户输入密码。 如果禁用此策略设置，系统从睡眠状态恢复时不会提示用户输入密码。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **默认值**：已启用

## <a name="remote-assistance"></a>远程协助
- **远程协助请求**  
  此策略设置允许你打开或关闭 Solicited （询问） 在此计算机上的远程协助。 
  - *如果启用此策略设置*，在此计算机上的用户可以使用电子邮件或文件传输寻求他人的帮助。 此外，用户可以使用即时消息程序允许连接到此计算机，并可以配置其他远程协助设置。 
  - *如果禁用此策略设置*，此计算机上的用户不能使用电子邮件或文件传输寻求他人的帮助。 此外，用户不能使用即时消息程序以允许连接到此计算机。 
  - *如果不配置此策略设置*，用户可以打开或关闭远程协助 Solicited （询问） 本身在控制面板中的系统属性中。 用户还可以配置的远程协助设置。 

  如果启用此策略设置，可以通过两种方法允许帮助者提供远程协助:"允许帮助者只能查看在计算机"或"允许帮助者远程控制您的计算机"。 "最大票证时间"策略设置设置限制的时间，通过电子邮件或文件传输创建一个远程协助邀请可以保持打开状态。 "选择发送电子邮件邀请的方法"设置指定要用于发送远程协助邀请的电子邮件标准。 根据您的电子邮件程序，可以使用标准 Mailto （邀请收件人连接通过 Internet 链接） 或 SMAPI (简单 MAPI) 标准 （邀请已附加到你的电子邮件）。 此策略设置不是 Windows Vista 中提供的由于 SMAPI 是支持的唯一方法。 如果启用此策略设置还应启用适当的防火墙例外以允许远程协助通信。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067198)

  **默认**： 禁用远程协助

  如果设置为*启用远程协助*，配置以下附加设置：  
  - **远程协助请求权限**  
    **默认值**：视图  

  - **最大票证时间值**  
    **默认值**：未配置   

  - **最大票证时间段**  
    **默认**： 分钟    

  - **电子邮件邀请方法**  
    **默认**： 简单 MAPI

  
## <a name="remote-desktop-services"></a>远程桌面服务  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices)。  

- **阻止密码保存**  
  控制是否可以通过远程桌面连接在此计算机上保存密码。 如果启用此设置，将禁用远程桌面连接中的密码保存复选框，并且用户将无法保存密码。 当用户使用远程桌面连接打开 RDP 文件并保存其设置时，将删除以前存在于 RDP 文件中的所有密码。 如果禁用此设置，或不对其进行配置，则用户可以使用远程桌面连接保存密码。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **默认值**：已启用
  
- **安全 RPC 通信**  
  指定远程桌面会话主机服务器是要求与所有客户端建立安全 RPC 通信，还是允许存在不安全的通信。 可以使用此设置，通过仅允许经身份验证和加密的请求，增强与客户端 RPC 通信的安全性。 如果状态设置为“启用”，远程桌面服务会接受来自支持安全请求的 RPC 客户端的请求，且不允许与不受信任的客户端建立不安全通信。 如果状态设置为“禁用”，远程桌面服务将始终要求保障所有 RPC 通信的安全性。 但是，允许不响应请求的 RPC 客户端存在不安全的通信。 如果状态设置为“未配置”，则允许不安全的通信。 注意：RPC 接口用于管理和配置远程桌面服务。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **默认值**：已启用
  
- **阻止驱动器重定向**  
  此策略设置指定是否阻止映射远程桌面服务会话中的客户端驱动器（驱动器重定向）。 默认情况下，RD 会话主机服务器将在连接时自动映射客户端驱动器。 映射的驱动器将显示在文件资源管理器或计算机中的会话文件夹树中，并采用\<计算机名称>上的\<驱动器号>   。 此策略设置可用于重写此行为。 如果启用此策略设置，则远程桌面服务会话中不允许客户端驱动器重定向，并且运行 Windows 2003、Windows 8 和 Windows XP 的计算机上不允许剪贴板文件副本重定向。 如果禁用此策略设置，则始终允许客户端驱动器重定向。 此外，如果允许剪贴板重定向，则始终允许剪贴板文件副本重定向。 如果不配置此策略设置，则不会在组策略级别指定客户端驱动器重定向和剪贴板文件副本重定向。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **默认值**：已启用
  
- **连接时提示输入密码**  
  此策略设置指定远程桌面服务是否始终提示在连接时输入客户端密码。 可使用此设置，对登录远程桌面服务的用户强制实施密码提示，即便他们已在远程桌面连接客户端中提供密码也是如此。 默认情况下，远程桌面服务允许用户通过在远程桌面连接客户端中输入密码自动登录。 如果启用此策略设置，则用户无法通过在远程桌面连接客户端中提供其密码自动登录到远程桌面服务。 系统将提示用户输入密码进行登录。 如果禁用此策略设置，则用户始终可以通过在远程桌面连接客户端中提供其密码自动登录到远程桌面服务。 如果不配置此策略设置，则不会在组策略级别指定自动登录。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **默认值**：已启用
  
- **远程桌面服务客户端连接加密级别**  
  指定是否需要使用特定的加密级别，在远程桌面协议 (RDP) 连接期间保护客户端计算机与 RD 会话主机服务器之间的通信。 此策略仅当使用本机 RDP 加密时才适用。 但不建议使用本机 RDP 加密（相对于 SSL 加密）。 此策略不适用于 SSL 加密。 如果启用此策略设置，则远程连接期间客户端和 RD 会话主机服务器之间的所有通信都必须使用此设置中指定的加密方法。 默认情况下，加密级别设置为“高”。 可采用以下加密方法：  
  - 高  -“高”设置使用强 128 位加密对往返客户端与服务器之间的数据进行加密。 在仅包含 128 位客户端（例如，运行远程桌面连接的客户端）的环境中使用此加密级别。 不支持此加密级别的客户端无法连接到 RD 会话主机服务器。  
  - 客户端兼容  -“客户端兼容”设置采用客户端支持的最大密钥强度对客户端和服务器之间的数据进行加密。 在包含不支持 128 位加密的客户端的环境中使用此加密级别。  
  - 低  -“低”设置仅对从客户端发送到服务器的数据使用 56 位加密。  
  
  如果禁用或不配置此设置，则不会通过组策略强制执行用于远程连接到 RD 会话主机服务器的加密级别。 可以通过系统加密配置重要的 FIPS 符合性。 将 FIPS 兼容算法用于“组策略”（位于计算机配置\Windows 设置\安全设置\本地策略\安全选项）中的加密、哈希和签名设置。FIPS 兼容设置通过美国联邦信息处理标准 (FIPS) 140 加密算法，使用 Microsoft 加密模块，对往返发送于客户端与服务器之间的数据进行加密和解密。 如果客户端和 RD 会话主机服务器之间的通信需要最高级别加密，则使用此加密级别。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **默认值**：高
  
## <a name="remote-management"></a>远程管理  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement)。  

- **阻止存储运行方式凭据**  
  客户端基本身份验证。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **默认值**：已启用
  
- **基本身份验证**  
  使用此策略设置，可以控制 Windows 远程管理 (WinRM) 服务是否接受来自远程客户端的基本身份验证。 如果启用此策略设置，则 WinRM 服务将接受来自远程客户端的基本身份验证。 如果禁用或未配置此策略设置，则 WinRM 服务将不接受来自远程客户端的基本身份验证。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **默认值**：已禁用
  
- **阻止客户端摘要式身份验证**  
  使用此策略设置，可以控制 Windows 远程管理 (WinRM) 客户端是否使用摘要式身份验证。 如果启用此策略设置，则 WinRM 客户端不使用摘要式身份验证。 如果禁用或未配置此策略设置，则 WinRM 客户端将使用摘要式身份验证。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **默认值**：已启用
  
- **未加密的流量**  
  使用此策略设置，可以控制 Windows 远程管理 (WinRM) 服务是否通过网络发送和接收未经加密的消息。 如果启用此策略设置，则 WinRM 客户端将通过网络发送和接收未经加密的消息。 如果禁用或不配置此策略设置，则 WinRM 客户端将仅通过网络发送或接收经过加密的消息。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **默认值**：已禁用
  
- **客户端未加密的流量**  
  使用此策略设置，可以管理 Windows 远程管理 (WinRM) 客户端是否通过网络发送和接收未加密的消息。 如果启用此策略设置，则 WinRM 客户端将通过网络发送和接收未经加密的消息。 如果禁用或不配置此策略设置，则 WinRM 客户端将仅通过网络发送或接收经过加密的消息。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **默认值**：已禁用
  
- **客户端基本身份验证**  
  使用此策略设置，可以控制 Windows 远程管理 (WinRM) 客户端是否使用基本身份验证。 如果启用此策略设置，则 WinRM 客户端将使用基本身份验证。 如果 WinRM 配置为使用 HTTP 传输，则通过网络以明文形式发送用户名和密码。 如果禁用或未配置此策略设置，则 WinRM 客户端不使用基本身份验证。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **默认值**：已禁用
  
## <a name="remote-procedure-call"></a>远程过程调用  
有关详细信息，请参阅 Windows 文档中的[策略 CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall)。  

- **RPC 未经身份验证的客户端选项**  
  此策略设置控制 RPC 服务器运行时如何处理连接到 RPC 服务器的未经验证的 RPC 客户端。 此策略设置影响所有 RPC 应用程序。 在域环境中，请谨慎使用此策略设置，因为该策略可能会影响各种功能（包括组策略处理本身）。 恢复对此策略设置的更改可能要求手动干预每个受影响的计算机。 永远不应将此策略设置应用于域控制器。 如果禁用此策略设置，则 RPC 服务器运行时在 Windows 客户端上使用“已验证”值，而在支持此策略设置的 Windows Server 版本上使用值“无”。 如果未配置此策略设置，则会禁用该策略设置。 RPC 服务器运行时的行为就如同启用了此策略设置一样，将“已验证”值用于 Windows 客户端，而将“无”值用于支持此策略设置的服务器 SKU。 如果启用此策略设置，则它指导 RPC 服务器运行时限制未经验证的 RPC 客户端连接到计算机上运行的 RPC 服务器。 如果客户端使用命名管道或使用 RPC 安全性与服务器通信，则将该客户端视为已验证的客户端。 特别请求可以由未经验证的客户端访问的 RPC 接口可能在此限制之外，具体取决于为此策略设置选取的值。  
  - “无”  允许所有 RPC 客户端连接到应用该策略设置的计算机上运行的 RPC 服务器。 
  - “已验证”  仅允许经过验证的 RPC 客户端（依据上述定义）连接到应用该策略设置的计算机上运行的 RPC 服务器。 对请求例外的接口授予例外。 
  - “已验证并且无例外”  仅允许经过验证的 RPC 客户端（依据上述定义）连接到应用该策略的计算机上运行的 RPC 服务器。 不允许例外。 注意：只有在重启系统后才可以应用此策略设置。  

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **默认值**：已经过身份验证

## <a name="search"></a>搜索 
有关详细信息，请参阅 Windows 文档 [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search)（策略 CSP - Search）。  

- **禁用索引加密项**  
  允许或不允许项的索引。 此开关适用于 Windows Search 索引器，用于控制是否索引加密项，如受 Windows 信息保护 (WIP) 保护的文件。 启用策略后，即会索引受 WIP 保护的项，且相关元数据存储在未加密位置。 元数据包括文件路径和修改日期等。 禁用策略后，不会索引受 WIP 保护的项，也不会在 Cortana 或文件资源管理器的结果中显示这些项。 如果设备上存在许多受 WIP 保护的媒体文件，可能还会对照片和 Groove 应用产生性能影响。  
  [了解详细信息]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **默认值**：是
  
## <a name="smart-screen"></a>SmartScreen  
有关详细信息，请参阅 Windows 文档 [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen)（策略 CSP - SmartScreen）。  

- **阻止未经验证的文件**  
  阻止用户运行未经验证的文件。 
  - 未配置  - 员工可以忽略 SmartScreen 警告并运行恶意文件。 
  - 是  - 员工不可忽略 SmartScreen 警告并运行恶意文件。

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **默认值**：是

- **要求对应用和文件使用 SmartScreen**  
  允许 IT 管理员配置 Windows 适用的 SmartScreen。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **默认值**：是
  
## <a name="system"></a>System (系统)  
有关详细信息，请参阅 Windows 文档 [olicy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system)（策略 CSP - System）。  

- **系统引导启动驱动程序初始化**  
  使用此策略设置，可以根据提前启动反恶意软件引导启动驱动程序所确定的分类来指定要初始化哪些引导启动驱动程序。 提前启动反恶意软件引导启动驱动程序可为每个引导启动驱动程序返回以下分类： 
  - 好  - 驱动程序已签名且未被篡改。  
  - 差  - 驱动程序被标识为恶意软件。 建议不允许初始化已知的差驱动程序。 
  - 差，但需要启动  - 驱动程序已被标识为恶意软件，但计算机无法在不加载此驱动程序的情况下成功启动。 
  - 未知  - 驱动程序未经恶意软件检测应用程序证明，且未经提前启动反恶意软件引导启动驱动程序分类。  

  如果启用此策略设置，则可以选择下次启动计算机时要初始化的引导启动驱动程序。 如果禁用或未配置此策略设置，则初始化被确定为“好”、“未知”或“差，但启动关键”的引导启动驱动程序，而跳过初始化被确定为“差”的驱动程序。 如果恶意软件检测应用程序不包括提前启动反恶意软件引导启动驱动程序，或者提前启动反恶意软件引导启动驱动程序已禁用，则此设置无效，所有引导启动驱动程序都会被初始化。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **默认值**：“好”、“未知”和“差，但关键”


## <a name="wi-fi"></a>Wi-Fi  
有关详细信息，请参阅 Windows 文档 [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)（策略 CSP - Wifi）。  

- **阻止 Internet 共享**  
  指定可否在设备上进行 Internet 共享。   
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **默认值**：是  

- **阻止自动连接到 Wi-Fi 热点**  
  允许或不允许设备自动连接到 Wi-Fi 热点。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **默认值**：是  
  
## <a name="windows-connection-manager"></a>Windows 连接管理器  
有关详细信息，请参阅 Windows 文档 [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager)（策略 CSP - WindowsConnectionManager）。  

- **阻止连接到非域网络**  
  此策略设置阻止计算机同时连接到基于域的网络和并非基于域的网络。 如果启用此策略设置，则计算机可基于以下情况响应自动和手动网络连接尝试： 
  - 自动连接尝试：当计算机已连接到基于域的网络时，将阻止所有对非域网络的自动连接尝试。 当计算机已连接到并非基于域的网络时，将阻止所有对基于域的网络的自动连接尝试。 
  - 手动连接尝试：当计算机已通过除以太网以外的介质连接到并非基于域的网络或基于域的网络，并且用户尝试违反此策略设置，创建到其他网络的手动连接时，将断开现有网络连接将，并允许手动连接。 当计算机已通过以太网连接到并非基于域的网络或基于域的网络，并且用户尝试违反此策略设置，创建到其他网络的手动连接时，将保持现有以太网连接，并阻止手动连接尝试。  

  如果未配置或禁用此策略设置，则计算机可以同时连接到域网络和非域网络。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **默认值**：已启用
  
## <a name="windows-defender"></a>Windows Defender  
有关详细信息，请参阅 Windows 文档 [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)（策略 CSP - Defender）。  

- **扫描传入的电子邮件**  
  允许或不允许扫描电子邮件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **默认值**：是  

- **Office 应用启动子进程类型**  
  Office 应用将无法创建子进程。 包括 Word、Excel、PowerPoint、OneNote 和 Access。 这是典型的恶意软件行为，尤其是在基于宏的攻击中，该行为试图使用 Office 应用启动或下载恶意可执行文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **默认值**：阻止
  
- **Defender 示例提交同意类型**  
  检查 Windows Defender 中用户的同意级别是否可发送数据。 如果已授予所需同意，则 Windows Defender 将提交它们。 如果没有（并且用户已指定从不询问），则系统会先启动 UI 征得用户同意（允许 Defender/AllowCloudProtection 时），然后才发送数据。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **默认值**：自动发送安全示例 
  
- **签名更新间隔（小时）**  
  Defender 签名更新间隔（小时）
  
  **默认值**：4
  
- **脚本下载有效负载执行类型**  
  脚本下载有效负载执行类型
  
  **默认值**：阻止
  
- **防止凭据窃取类型**  
  Windows Defender 凭据保护使用基于虚拟化的安全性来隔离密钥，以便只有特权系统软件可以访问它们。 未经授权的访问这些密钥可能会导致凭据被盗攻击，如哈希传递或票证传递。 Windows Defender 凭据保护可通过保护 NTLM 密码哈希、Kerberos 票证授予票证和由应用程序存储为域凭据的凭据来防止这些攻击。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **默认值**：启用

- **电子邮件内容执行类型**  
  此规则可以阻止从 Microsoft Outlook 或 Webmail（如 Gmail.com 或 Outlook.com）的电子邮件中运行或启动以下文件类型：可执行文件（例如 .exe、.dll 或 .scr）、脚本文件（如 PowerShell .ps、VisualBasic .vbs 或 JavaScript .js 文件）、脚本存档文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067063)  
  
  **默认值**：阻止

- **Adobe Reader 在子进程中启动**  

  **默认值**：启用

- **网络保护类型**  
  此策略可用于在 Windows Defender 攻击防护中启用或禁用网络保护（阻止/审核）。 网络保护是 Windows Defender 攻击防护的一项功能，可阻止员工使用任何应用访问 Internet 上的钓鱼邮件、攻击宿主站点和恶意内容。 这包括阻止第三方浏览器连接到危险站点。 值类型为整数。 如果启用此设置，则会启用网络保护，且员工无法将其禁用。 可通过以下选项控制其行为：阻止和审核。 如果启用此策略并使用“阻止”选项，则会阻止用户和应用连接到危险的域。 可在 Windows Defender 安全中心看到此活动。 如果启用此策略并使用“审核”选项，则不会阻止用户/应用连接到危险的域。 但是，仍可在 Windows Defender 安全中心看到此活动。 如果禁用此策略，则不会阻止用户/应用连接到危险的域。 无法在 Windows Defender 安全中心看到任何网络活动。 如果未配置此策略，则默认禁用网络阻止。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067102)  
  
  **默认值**：启用
  
- **Defender 计划扫描日期**  
  Defender 计划扫描日期。
  
  **默认值**：每天
  
- **云提供的保护**  
  为了更好地保护你的电脑，Windows Defender 会将所发现的任何问题的相关信息发送到 Microsoft。 Microsoft 会分析该信息，详细了解影响你和其他客户的问题，并提供改进的解决方案。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **默认值**：是  

- **Defender 可能不需要的应用操作**  
  Windows Defender 防病毒中的可能不需要的应用程序 (PUA) 保护功能可以识别和阻止在网络中的终结点上下载和安装 PUA。 这些应用程序不被视为病毒、恶意软件或其他类型的威胁，但可能在终结点上执行对性能或使用产生不利影响的操作。 PUA 也指视为信誉不佳的应用程序。 典型 PUA 行为包括：各种类型的软件捆绑 广告注入到 Web 浏览器 检测问题、要求付费修复错误但始终保留在终结点上且不会进行任何更改或优化的驱动程序和注册表优化程序（也称为“流氓防病毒”程序）。 这些应用程序可能会增加网络受到恶意软件感染的风险、增加恶意软件感染的识别难度，而清理这些应用程序也会造成 IT 资源的浪费。  
  [了解详细信息](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **默认值**：阻止  

- **脚本混淆的宏代码类型**  
  恶意软件和其他威胁可能会尝试在某些脚本文件中混淆或隐藏其恶意代码。 此规则可阻止运行混淆的脚本。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **默认值**：阻止
  
- **完全扫描期间扫描可移动驱动器**  
  允许 Windows Defender 在完全扫描期间扫描可移动驱动器（例如闪存驱动器）中的恶意软件和不需要的软件。 Windows Defender 防病毒软件将在执行前扫描 USB 设备上的所有文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **默认值**：是  
  
- **扫描存档文件**  
  Defender 扫描存档文件。
  
  **默认值**：是
  
- **行为监视**  
  允许或禁止 Windows Defender 行为监视功能。 这些传感器内嵌于 Windows 10，收集并处理来自操作系统的行为信号，并将该传感器数据发送至 Microsoft Defender ATP 的专用独立云实例。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **默认值**：是

- **扫描从网络文件夹中打开的文件**  
  如果文件为只读，则用户无法删除任何检测到的恶意软件。
  
  **默认值**：是

- **不受信任的 USB 进程类型**  
  使用此规则，管理员可以防止从 USB 可移动驱动器（包括 SD 卡）运行未签名或不受信任的可执行文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **默认值**：阻止
  
- **Office 应用其他进程注入类型**  
  Office 应用（包括 Word、Excel、PowerPoint 和 OneNote）无法将代码注入其他进程。 恶意软件通常会使用此方法来运行恶意代码，试图对防病毒扫描引擎隐藏活动。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **默认值**：阻止
  
- **Office 宏代码运行 Win32 导入类型**  
  恶意软件可以在 Office 文件中使用宏代码来导入和加载 Win32 DLL，然后可以使用此 DLL 进行 API 调用，以在整个系统中实现进一步感染。 此规则会尝试阻止所含宏代码支持导入 Win32 DLL 的 Office 文件。 这包括 Word、Excel、PowerPoint 和 OneNote。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **默认值**：阻止  
  
- **Defender 云阻止级别**  
  Defender 云阻止级别。
  
  **默认值**：未配置

- **实时监视**  
  Defender 要求实时监视。
  
  **默认值**：是
 
- **Office 通信应用在子进程中启动**  

  **默认值**：启用

- **Office 应用可执行内容创建或启动类型**  
  此规则针对创建或启动可执行文件的可疑和恶意外接程序和脚本（扩展）使用的典型行为。 这是典型的恶意软件技术。 将阻止 Office 应用使用扩展。 这些扩展通常使用 Windows Scripting Host（.wsh 文件）来运行脚本，自动执行某些任务或提供用户创建的外接程序功能。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **默认值**：阻止

## <a name="windows-defender-firewall"></a>Windows Defender 防火墙  
有关详细信息，请参阅[2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) Windows 协议文档中。  

- **防火墙配置文件域**  
  指定规则所属的配置文件：域、专用、公用。 此值表示连接到域的网络的配置文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **已阻止入站连接**  
    **默认值**：是

  - **需要出站连接**  
    **默认值**：是 

  - **已阻止入站通知**  
    **默认值**：是

  - **防火墙已启用**  
    **默认值**：允许

- **公共防火墙配置文件**  
  指定规则所属的配置文件：域、专用、公用。 此值表示公用网络的配置文件。 这些网络由服务器主机中的管理员分类为公用。 主机首次连接到网络时会进行分类。 通常，这些网络位于网络中的对等方或网络管理员不被信任的机场、咖啡店和其他公共场所。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **已阻止入站连接**  
    **默认值**：是

  - **需要出站连接**  
    **默认值**：是 

  - **已阻止入站通知**  
    **默认值**：是

  - **防火墙已启用**  
    **默认值**：允许

  - **未合并来自组策略的连接安全规则**  
    **默认值**：是

  - **未合并来自组策略的策略规则**  
    **默认值**：是

- **防火墙配置文件专用**  
  指定规则所属的配置文件：域、专用、公用。 此值表示专用网络的配置文件。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067041)  

   - **已阻止入站连接**  
    **默认值**：是

  - **需要出站连接**  
    **默认值**：是 

  - **已阻止入站通知**  
    **默认值**：是

  - **防火墙已启用**  
    **默认值**：允许

## <a name="windows-hello-for-business"></a>Windows Hello 企业版  
- **需要增强型反欺骗(若有)**  
  如果是，设备将使用增强的反欺骗，可用时。 如果否，则将阻止反欺骗程序。 未配置，则将沿用在客户端上完成的配置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067192)

  **默认值**：是

- **配置 Windows Hello 企业版**   
  Windows Hello 企业版是一种取代密码、智能卡和虚拟智能卡登录 Windows 的替代方法。 如果启用或未配置此策略设置，设备将预配 Windows Hello 企业版。 如果禁用此策略设置，设备不会为任何用户预配 Windows Hello 企业版。

  **默认值**：是

- **要求 PIN 中含有小写字母**  
  如果需要，用户 PIN 必须包含至少一个小写字母。

  **默认值**：允许

- **要求 PIN 中含有特殊字符**  
  如果需要，用户 PIN 必须包含至少 1 个特殊字符。

  **默认值**：允许

- **最小 PIN 长度**  
  最小 PIN 长度必须介于 4 到 127 之间。

  **默认值**：6

- **要求 PIN 中含有大写字母**  
  如果需要，用户 PIN 必须包含至少一个大写字母。

  **默认值**：允许

## <a name="windows-ink-workspace"></a>Windows Ink 工作区  
有关详细信息，请参阅 Windows 文档 [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)（策略 CSP - WindowsInkWorkspace）。  

- **Ink 工作区**  
  指定是否允许用户访问 Ink 工作区。 
  - 已禁用  - 禁止访问 Ink 工作区。 该功能处于禁用状态。
  - 已启用  - 已启用 Ink 工作区，但用户无法在锁屏界面上访问它。
  - *未配置* - 已启用 Ink 工作区功能，并且用户可以在锁屏界面上使用它。  

  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **默认值**：已启用
 
## <a name="windows-powershell"></a>Windows PowerShell  
有关详细信息，请参阅 Windows 文档 [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell)（策略 CSP - WindowsPowerShell）。  

- **Power shell shell 脚本块日志记录**  
  使用此策略设置，可以将所有的 PowerShell 脚本输入记录到 Microsoft-Windows-PowerShell/Operational 事件日志中。 如果启用此策略设置，则 Windows PowerShell 将记录命令、脚本块、函数和脚本的处理，无论是以交互方式调用还是通过自动方式处理。 如果禁用此策略设置，则将禁止记录 PowerShell 脚本输入。 如果启用脚本块调用日志记录，则 PowerShell 在调用命令、脚本块、函数或脚本启动或停止时还会记录事件。 启用调用日志记录时会生成大量事件日志。 注意：此策略设置存在于组策略编辑器中“计算机配置”和“用户配置”的下方。 “计算机配置”策略设置优先于“用户配置”策略设置。  
  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **默认值**：已启用

## <a name="whats-changed-in-the-new-template"></a>中的新模板的更改内容
*MDM Spring 2019 更新 （19 小时 1） 的安全基准*模板具有以下更改来自*预览*模板。

### <a name="changes-to-the-baseline-settings"></a>基线设置的更改
以下设置为：
- *新*在此最新版本的基线。
- *删除*从此最新基线版本，但已存在的早期版本中。
- *修订*以某种方式从如何设置出现在以前的版本。 

*[新]* [**上面锁**](#above-lock):
- **语音激活锁定屏幕中的应用**    

*[新]* [**应用程序管理**](#application-management): 
- **阻止用户对安装进行控制**  
- **使用提升的权限的块 MSI 应用安装**  

*[已删除]* [ **Bitlocker**](#bitlocker):  
- Bit Locker 可移动驱动器策略 >**加密方法**
- **固定驱动器策略的 bit locker** *（所有设置）*
- **Bit locker 系统驱动器策略** *（所有设置）*

*[新]* [**连接**](#connectivity):
- **配置安全访问的 UNC 路径**

*[新]* [**Device Guard**](#device-guard):
- **基于虚拟化的安全性**


*[新]* [ **DMA 防护**](#dma-guard):
- **与内核 DMA 保护不兼容的外部设备的枚举**  

*[新]* [**Internet Explorer 11**](#internet-explorer):
- **Explorer Internet 区域通过脚本更新状态栏**
- **Internet Explorer Internet 区域拖放或复制和粘贴文件**  
- **Internet Explorer 限制区域 .NET Framework 相关组件**  
- **Internet Explorer 本地计算机区域不针对 ActiveX 控件运行反恶意软件**
- **Internet Explorer 加密支持**  

*[修订]* [ **Internet 资源管理器**](#internet-explorer):
- **Internet Explorer internet 区域自动提示文件下载**> 的默认值现在是**禁用**。 在预览中此已设置为已启用。

*[新]* [**远程协助**](#remote-assistance):  
- **远程协助请求** 
  - **远程协助请求权限**
  - **最大票证时间值**  
  - **最大票证时间段**  
  - **电子邮件邀请方法**


*[新]* [**WIndows Defender**](#windows-defender):
- **Adobe Reader 在子进程中启动**  
- **Office 通信应用在子进程中启动** 

*[新]* [**Windows Defender 防火墙**](#windows-defender-firewall)
- **防火墙配置文件域**  
  - **已阻止入站连接**  
  - **需要出站连接**  
  - **已阻止入站通知**  
  - **防火墙已启用**  
- **公共防火墙配置文件**  
  - **已阻止入站连接**  
  - **需要出站连接**  
  - **已阻止入站通知**  
  - **防火墙已启用** 
  - **未合并来自组策略的连接安全规则**   
  - **未合并来自组策略的策略规则**  
- **防火墙配置文件专用**  
  - **已阻止入站连接**  
  - **需要出站连接**  
  - **已阻止入站通知**  
  - **防火墙已启用**  

*[新]* [**Windows Hello 企业版**](#windows-hello-for-business):  
- **需要增强型反欺骗(若有)**  
- **配置 Windows Hello 企业版**  
- **要求 PIN 中含有小写字母** 
- **要求 PIN 中含有特殊字符** 
- **最小 PIN 长度**  
- **要求 PIN 中含有大写字母** 



<!-- The following settings were available in the Preview Baseline.   

   
## Above Lock  
For more information, see [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in the Windows documentation.  

- **Block display of toast notifications**  
  This policy setting allows you to prevent app notifications from appearing on the lock screen. If you enable this policy setting, no app notifications are displayed on the lock screen. If you disable or don't configure this policy setting, users can choose which apps display notifications on the lock screen.
  
  **Default**: Yes  

## App Runtime    
For more information, see [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in the Windows documentation.  

- **Microsoft accounts optional for Windows Store apps**  
  This policy setting lets you control whether Microsoft accounts are optional for Windows Store apps that require an account to sign in. This policy only affects Windows Store apps that support it. If you enable this policy setting, Windows Store apps that typically require a Microsoft account to sign in will allow users to sign in with an enterprise account instead. If you disable or don't configure this policy setting, users must sign in with a Microsoft account.  
  
  **Default**: Enabled  

## Application Management   
For more information, see [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in the Windows documentation.  

- **Block game DVR (desktop only)**  
  Configures whether recording and broadcasting of games is allowed.
  
  **Default**: Yes  

## Auto Play   
For more information, see [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in the Windows documentation.  

- **Auto play default auto run behavior**  
  This setting affects the default behavior for Autorun commands. Autorun commands are stored in autorun.inf files and can launch installation programs or other routines. When *Enabled*, Administrators can change the default autorun behavior on a device that runs Windows Vista or later. Behavior can be set to: a) completely disable autorun commands, or b) revert back to pre-Windows Vista behavior of automatically executing the autorun command. When set to *Disabled* or *Not Configured*, devices that run Windows Vista or later prompt the user as to whether an autorun command should run.
  
  **Default**: Do not execute  
  
- **Auto play mode**  
  This policy setting allows you to turn off the Autoplay feature. Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately. Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives. Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices. If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives. This policy setting disables Autoplay on additional types of drives. You can't use this setting to enable Autoplay on drives on which it's disabled by default. If you disable or don't configure this policy setting, AutoPlay is enabled. Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.
  
  **Default**: Disabled

- **Block auto play for non-volume devices**  
  This policy setting disallows AutoPlay for MTP devices like cameras or phones. If you enable this policy setting, AutoPlay isn't allowed for MTP devices like cameras or phones. If you disable or don't configure this policy setting, AutoPlay is enabled for non-volume devices.
  
  **Default**: Enabled  

## Bitlocker    
For more information, see [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in the Windows documentation.  

- **Bit locker removable drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you'll be able to configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.

  For Bit locker removable drive policy, configure the following settings:

    - **Require encryption for write access**  
      **Default**: Yes  
  
    - **Encryption method**  
      **Default**: AES 256bit CBC  

- **Bit locker fixed drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  
 
   For Bit locker fixed drive policy, configure the following settings: 
   - **Encryption method**
     **Default**: AES 256bit XTS  

- **Bit locker system drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  

   For Bit locker system drive policy, configure the following settings:
  - **Encryption method**  
    **Default**: AES 256bit XTS  

## Browser  
For more information, see [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in the Windows documentation.  

- **Require SmartScreen for Microsoft Edge**  
  Microsoft Edge uses Windows Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software by default. Also, by default, users can't disable (turn off) Windows Defender SmartScreen. Enabling this policy turns off Windows Defender SmartScreen and prevent users from turning it on. Don’t configure this policy to let users choose to turn Windows defender SmartScreen on or off.  
  
  **Default**: Yes  
  
- **Block malicious site access**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious sites, allowing them to continue to the site. With this policy though, you can configure Microsoft Edge to prevent users from bypassing the warnings, blocking them from continuing to the site.
  
  **Default**: Yes  
  
- **Block unverified file download**
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes  
  
- **Block Password Manager**  
  By default, Microsoft Edge uses Password Manager automatically, allowing users to manager passwords locally. Disabling this policy restricts Microsoft Edge from using Password Manager. Don’t configure this policy if you want to let users choose to save and manage passwords locally using Password Manager.
  
  **Default**: Yes  
  
- **Prevent certificate error overrides**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Yes  

## Connectivity  
For more information, see [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in the Windows documentation.  

- **Block Internet download for web publishing and online ordering wizards**  
  This policy setting specifies whether Windows should download a list of providers for the web publishing and online ordering wizards. These wizards allow users to select from a list of companies that provide services such as online storage and photographic printing. By default, Windows displays providers downloaded from a Windows website in addition to providers specified in the registry. If you enable this policy setting, Windows doesn't download providers, and only the service providers that are cached in the local registry display. If you disable or don't configure this policy setting, a list of providers downloads when the user uses the web publishing or online ordering wizards. For more information that includes details on specifying service providers in the registry, see the documentation for the web publishing and online ordering wizards.  
  
  **Default**: Enabled  

- **Block downloading of print drivers over HTTP**  
  This policy setting specifies whether to allow this client to download print driver packages over HTTP. To set up HTTP printing, non-inbox drivers need to be downloaded over HTTP. Note: This policy setting doesn't prevent the client from printing to printers on the Intranet or the Internet over HTTP. It only prohibits downloading drivers that aren't already installed locally. If you enable this policy setting, print drivers can't be downloaded over HTTP. If you disable or don't configure this policy setting, users can download print drivers over HTTP.
  
  **Default**: Enabled  

## Credentials Delegation  
For more information, see [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in the Windows documentation.  

- **Remote host delegation of non-exportable credentials**  
  Remote host allows delegation of non-exportable credentials. When using credential delegation, devices provide an exportable version of credentials to the remote host, which exposes users to the risk of credential theft from attackers on the remote host. If you enable this policy setting, the host supports Restricted Admin or Remote Credential Guard mode. If you disable or don't configure this policy setting, Restricted Administration and Remote Credential Guard mode aren't supported. User will always need to pass their credentials to the host.  

  
  **Default**: Enabled  

## Credentials UI  
For more information, see [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in the Windows documentation.  

- **Enumerate administrators** 
  This policy setting controls whether administrator accounts display when a user attempts to elevate a running application. By default, administrator accounts aren't displayed when the user attempts to elevate a running application. If you enable this policy setting, all local administrator accounts on the PC display so the user can choose one and enter the correct password. If you disable this policy setting, users will always be required to type a user name and password to elevate.  

  
  **Default**: Disabled  

## Data Protection  
For more information, see [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in the Windows documentation.  

- **Block direct memory access**  
  This policy setting allows you to block direct memory access (DMA) for all hot pluggable PCI downstream ports until a user logs into Windows. Once a user logs in, Windows will enumerate the PCI devices connected to the host plug PCI ports. Every time the user locks the machine, DMA is blocked on hot plug PCI ports with no children devices until the user logs in again. Devices that were already enumerated when the machine was unlocked will continue to function until unplugged. This policy setting is only enforced when BitLocker or device encryption is enabled.
  
  
  **Default**: Yes  

## Device Guard  
For more information, see [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in the Windows documentation.  

- **Credential Guard**  
  This setting lets users turn on Credential Guard with virtualization-based security to help protect credentials at next reboot.
   
  **Default**: Enable with UEFI lock 

- **Enable virtualization based security**   
  Turns on virtualization-based security (VBS) at the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
  
  **Default**: Yes  


- **Launch system guard**    
  **Default**: Enabled  

## Device Installation  
For more information, see [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in the Windows documentation.  

- **Hardware device installation by device identifiers**  
  This policy setting allows you to specify a list of Plug and Play hardware IDs and compatible IDs for devices that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing a device whose hardware ID or compatible ID appears in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, devices can install and update as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
  
    - **Remove matching hardware devices**   
    This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes
  
    - **Hardware device identifiers that are blocked**  
       This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes  
  
- **Hardware device installation by setup classes**  
  This policy setting allows you to specify a list of device setup class globally unique identifiers (GUIDs) for device drivers that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing or updating device drivers whose device setup class GUIDs appear in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, Windows can install and update devices as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
    - **Remove matching hardware devices**    
    This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.  

      **Default**: *No default configuration*  
  
    - **Hardware device identifiers that are blocked**  
      This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.
      
      **Default**: *No default configuration*  

## Device Lock  
For more information, see [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in the Windows documentation.  

- **Prevent use of camera**  
  Disables the lock screen camera toggle switch in PC Settings and prevents a camera from being invoked on the lock screen. By default, users can enable invocation of an available camera on the lock screen. If you enable this setting, users will no longer be able to enable or disable lock screen camera access in PC Settings, and the camera can't be invoked on the lock screen. 
  
  **Default**: Enabled  

- **Require password**  
  Specifies whether device lock is enabled.
  
  **Default**: Yes  
  
    When *Require password* is set to *Yes*, the following settings are available.

    - **Password minimum character set count**  
      The number of complex element types (uppercase and lowercase letters, numbers, and punctuation) required for a strong PIN or password. PIN enforces the following behavior for desktop and mobile devices: 1 - Digits only 2 - Digits and lowercase letters are required 3 - Digits, lowercase letters, and uppercase letters are required. Not supported in desktop Microsoft accounts and domain accounts. 4 - Digits, lowercase letters, uppercase letters, and special characters are required. Not supported in desktop. The default value is 1. 
      
      **Default**: 3  
  
    - **Number of sign-in failures before wiping device**  
      The number of authentication failures allowed before the device is wiped. A value of 0 disables device wipe functionality.
        
      **Default**: 10  
  
    - **Password expiration (days)**  
      The Maximum password age policy setting determines how long (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If Maximum password age is between 1 and 999 days, the minimum password age must be less than the maximum password age. If Maximum password age is set to 0, Minimum password age can be any value between 0 and 998 days.
      
      **Default**: 60  
  
    - **Required password type**  
      Determines the type of PIN or password required.
      
      **Default**: Alphanumeric  
  
    - **Minimum password length**  
      The Minimum password length policy setting determines the least number of characters that can make up a password for a user account. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.
      
      **Default**: 8  
  
    - **Block simple passwords**  
      Specifies whether PINs or passwords such as "1111" or "1234" are allowed. For the desktop, it also controls the use of picture passwords.
      
      **Default**: Yes  
        *A setting of Yes prevents use of simple passwords.* 

  - **Prevent reuse of previous passwords**  
    Specifies how many passwords can be stored in the history that can’t be used. The value includes the user's current password. For example, with a setting of *1* the user can't reuse their current password when choosing a new password. A setting of *5* means that a user can't set their new password to their current password or any of their previous four passwords.
    
    **Default**: 24  

- **Prevent slide show**  
  Disables the lock screen slide show settings in PC Settings and prevents a slide show from playing on the lock screen. By default, users can enable a slide show that will run after they lock the machine. If you enable this setting, users can't modify slide show settings in PC Settings, and no slide show can start.
  
    **Default**: Enabled  
    *A setting of Enabled prevents slide shows from running.* 

- **Password minimum age in days**  
  The Minimum password age policy setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow password changes immediately by setting the number of days to 0. The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.
  
    **Default**: 1  

## Event Log Service  
For more information, see [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in the Windows documentation.  

- **Security log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
   **Default**: 196608  

- **System log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

- **Application log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

## Experience  
For more information, see [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentation.  

- **Block Windows Spotlight**  
  Allows IT admins to turn off all Windows Spotlight Features - Window spotlight on lock screen, Windows Tips, Microsoft consumer features, and other related features.
  
  **Default**: Yes  

  When *Block Windows Spotlight* is set to *Yes*, the following settings are available.
  
  - **Block third-party suggestions in Windows Spotlight**  
    Specifies whether to allow app and content suggestions from third-party software publishers in Windows spotlight features like lock screen spotlight, suggested apps in the Start menu, and Windows tips. Users may still see suggestions for Microsoft features, apps, and services.
      
    **Default**: Yes  
   - **Block consumer specific features**  
      Allows IT admins to turn on experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install, and redirect tiles.
      
     **Default**: Yes  


## Exploit Guard  
For more information, see [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in the Windows documentation.  

- **Exploit protection XML**  
  Enables the IT admin to push out a configuration that represents the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. Exploit protection helps protect devices from malware that use exploits to spread and infect. You use the Windows Security app or PowerShell to create a set of mitigations (known as a configuration). You can then export this configuration as an XML file and share it with multiple machines on your network so they all have the same set of mitigation settings. You can also convert and import an existing EMET configuration XML file into an exploit protection configuration XML.
  
  **Default**: *Sample xml is provided* 
 
## File Explorer  
For more information, see [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in the Windows documentation.  

- **Block data execution prevention**  
  Disabling data execution prevention can allow certain legacy plug-in applications to function without terminating Explorer.
  
  **Default**: Disabled  
   
- **Block heap termination on corruption**  
  Disabling heap termination on corruption can allow certain legacy plug-in applications to function without terminating Explorer immediately, although Explorer may still terminate unexpectedly later.
  
  **Default**: Disabled  
    

## Internet Explorer  
For more information, see [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in the Windows documentation.  


- **Internet Explorer internet zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains within windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in the same window. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy setting or don't configure it, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog.
  
  **Default**: Disabled
  
- **Internet Explorer certificate address mismatch warning**  
  This policy setting allows you to turn on the certificate address mismatch security warning. When this policy setting is turned on, the user is warned when visiting Secure HTTP (HTTPS) websites that present certificates issued for a different website address. This warning helps prevent spoofing attacks. If you enable this policy setting, the certificate address mismatch warning always appears. If you disable or don't configure this policy setting, the user can choose whether the certificate address mismatch warning appears (by using the Advanced page in the Internet Control panel).
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Internet sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, possibly harmful navigation is prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Disabled
  
- **Internet Explorer internet zone .NET Framework reliant components**  
  This policy setting allows you to manage whether .NET Framework components that aren't signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute unsigned managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute unsigned managed components. If you disable this policy setting, Internet Explorer won't execute unsigned managed components. If you don't configure this policy setting, Internet Explorer will execute unsigned managed components.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone include local path when uploading files to server**  
  This policy setting controls if local path information gets sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information gets sent when they upload a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled 
  
- **Internet Explorer disable processes in enhanced protected mode**  
  This policy setting determines whether Internet Explorer 11 uses 64-bit processes (for greater security) or 32-bit processes (for greater compatibility) when running in Enhanced Protected Mode on 64-bit versions of Windows. Important: Some ActiveX controls and toolbars may not be available when 64-bit processes are used. If you enable this policy setting, Internet Explorer 11 will use 64-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you disable this policy setting, Internet Explorer 11 will use 32-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you don't configure this policy setting, users can turn this feature on or off using Internet Explorer settings. This feature is turned off by default.
  
  **Default**: Enabled 
  
- **Internet Explorer ignore certificate errors**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled 
  
- **Internet Explorer fallback to SSL3**  
  This policy setting allows you to block an insecure fallback to SSL 3.0. When this policy is enabled, Internet Explorer will attempt to connect to sites using SSL 3.0 or below when TLS 1.0 or greater fails. We recommend that you don't allow insecure fallback in order to prevent a man-in-the-middle attack. This policy doesn't affect which security protocols are enabled. If you disable this policy, system defaults are used.
  
  **Default**: No sites 
  
- **Internet Explorer locked down internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone.
  
  **Default**: Disable 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes consistent MIME handling**  
  Internet Explorer contains dynamic binary behaviors: components that encapsulate specific functionality for the HTML elements to which they're attached. This policy setting controls whether the Binary Behavior Security Restriction setting is prevented or allowed. If you enable this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes. If you disable this policy setting, binary behaviors are allowed for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
    
  
- **Internet Explorer Active X controls in protected mode**  
  This policy setting prevents ActiveX controls from running in Protected Mode when Enhanced Protected Mode is enabled. When a user has an ActiveX control installed that isn't compatible with Enhanced Protected Mode and a website attempts to load the control, Internet Explorer notifies the user and gives the option to run the website in regular Protected Mode. This policy setting disables this notification and forces all websites to run in Enhanced Protected Mode. Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. When Enhanced Protected Mode is enabled, and a user comes across a website that attempts to load an ActiveX control that isn't compatible with Enhanced Protected Mode, Internet Explorer notifies the user and gives the option to disable Enhanced Protected Mode for that particular website. If you enable this policy setting, Internet Explorer won't give the user the option to disable Enhanced Protected Mode. All Protected Mode websites will run in Enhanced Protected Mode. If you disable or don't configure this policy setting, Internet Explorer notifies users and provides an option to run websites with incompatible ActiveX controls in regular Protected Mode.  
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable  
  
- **Internet Explorer processes scripted window security restrictions**  
  Internet Explorer allows scripts to programmatically open, resize, and reposition windows of various types. The Window Restrictions security feature restricts popup windows and prohibits scripts from displaying windows in which the title and status bars aren't visible to the user or obfuscate other Windows' title and status bars. If you enable this policy setting, scripted windows are restricted for all processes. If you disable or don't configure this policy setting, scripted windows aren't restricted.
  
  **Default**: Enabled   
  
- **Internet Explorer restricted zone run Active X controls and plugins**  
  This policy setting allows you to manage whether ActiveX controls and plug-ins can run on pages from the specified zone. If you enable this policy setting, controls and plug-ins can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow the controls or plug-in to run. If you disable this policy setting, controls and plug-ins are prevented from running. If you don't configure this policy setting, controls and plug-ins are prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting**  
  This policy setting allows you to manage whether an ActiveX control marked safe for scripting can interact with a script. If you enable this policy setting, script interaction can occur automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow script interaction. If you disable this policy setting, script interaction is prevented from occurring. If you don't configure this policy setting, script interaction is prevented from occurring.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. 
  - *Anonymous*  - Use anonymous sign in to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. 
  - *Prompt* - Use prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in only in Intranet zone* - Use this option to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in with current user name and password*- Use this option to attempt sign in using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for sign in. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. 

  If you disable this policy setting, sign-in is set to *Automatic sign in only in Intranet zone*. If you don't configure this policy setting, sign-in is set to *Prompt* for username and password.
  
  **Default**: Anonymous  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, users are queried whether to allow the control to load with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer check server certificate revocation**  
  This policy setting allows you to manage whether Internet Explorer will check revocation status of servers' certificates. Certificates are revoked when they are compromised or no longer valid, and this option protects users from submitting confidential data to a site that may be fraudulent or not secure. If you enable this policy setting, Internet Explorer will check to see if server certificates have been revoked. If you disable this policy setting, Internet Explorer won't check server certificates to see if they have been revoked. If you don't configure this policy setting, Internet Explorer won't check server certificates to see if they have been revoked.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Restricted Sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone file downloads**  
  This policy setting allows you to manage whether file downloads are permitted from the zone. This option gets determined by the zone of the page with the link causing the download, not the zone from which the file is delivered. If you enable this policy setting, files can be downloaded from the zone. If you disable this policy setting, files are prevented from being downloaded from the zone. If you don't configure this policy setting, files are prevented from being downloaded from the zone.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer prevent per user installation of Active X controls**  
  This policy setting allows you to prevent the installation of ActiveX controls on a per-user basis. If you enable this policy setting, ActiveX controls can't be installed on a per-user basis. If you disable or don't configure this policy setting, ActiveX controls can be installed on a per-user basis.
  
  **Default**: Enabled  
  
- **Internet Explorer prevent managing smart screen filter**  
  This policy setting prevents the user from managing SmartScreen Filter, which warns the user if the website they visit is known for fraudulent attempts to gather personal information through "phishing," or is known to host malware. If you enable this policy setting, the user isn't prompted to turn on SmartScreen Filter. All website addresses that aren't on the filters allow list are sent automatically to Microsoft without prompting the user. If you disable or don't configure this policy setting, the user gets prompted to decide whether to turn on SmartScreen Filter during the first-run experience.
  
  **Default**: Enable  
  
- **Internet Explorer processes MIME sniffing safety feature**  
  This policy setting determines whether Internet Explorer MIME sniffing will prevent promotion of a file of one type to a more dangerous file type. If you enable this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type. If you disable this policy setting, Internet Explorer processes will allow a MIME sniff promoting a file of one type to a more dangerous file type. If you don't configure this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone download signed Active X controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer auto complete**  
  This Auto-Complete feature can remember and suggest User names and passwords on Forms. If you enable this setting, the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned on. You have to decide whether to select "prompt me to save passwords". If you disable this setting the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned off. The user also can't opt to be prompted to save passwords. If you don't configure this setting, the user has the freedom of turning on Auto complete for User name and passwords on forms and the option of prompting to save passwords. To display this option, the users open the Internet Options dialog box, click the Contents Tab, and click the Settings button.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone allow VBscript to run**  
  This policy setting lets you decide whether VBScript can run on pages in specific Internet Explorer zones. Options include: 
  - *Enable* - VBScript runs on pages in specific zones, without any interaction. 
  - *Prompt* - Employees are prompted whether to allow VBScript to run in the zone. 
  - *Disable* - VBScript is prevented from running in the zone. If you disable or don’t configure this policy setting, VBScript runs without any interaction in the specified zone. 
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls**  
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled 
  
- **Internet Explorer local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: Disable java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls**
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  

- **Internet Explorer restricted zone scriptlets**  
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disabled  
  
- **Internet Explorer processes notification bar**  
  This policy setting allows you to manage whether the Notification bar is displayed for Internet Explorer processes when file or code installs are restricted. By default, the Notification bar is displayed for Internet Explorer processes. If you enable this policy setting, the Notification bar displays for the Internet Explorer Processes. If you disable this policy setting, the Notification bar won't be displayed for Internet Explorer processes. If you don't configure this policy setting, the Notification bar doesn't display for Internet Explorer Processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download signed ActiveX controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer remove run this time button for outdated Active X controls**  
  This policy setting allows you to stop users from seeing the "Run this time" button and from running specific outdated ActiveX controls in Internet Explorer. If you enable this policy setting, users won't see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. If you disable or don't configure this policy setting, users will see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. Clicking this button lets the user run the outdated ActiveX control once. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone launch applications and files in an iframe**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone
  
  **Default**: Disable 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down trusted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer check signatures on downloaded programs**  
  This policy setting allows you to manage whether Internet Explorer checks for digital signatures (which identifies the publisher of signed software and verifies it hasn't been modified or tampered with) on user computers before downloading executable programs. If you enable this policy setting, Internet Explorer will check the digital signatures of executable programs and display their identities before downloading them to user computers. If you disable this policy setting, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers. If you don't configure this policy, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone scripting of web browser controls**  
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone binary and script behaviors**  
  This policy setting allows you to manage dynamic binary and script behaviors: components that encapsulate specific functionality for HTML elements to which they were attached. If you enable this policy setting, binary and script behaviors are available. If you select Administrator approved in the drop-down box, only behaviors listed in the Admin-approved Behaviors under Binary Behaviors Security Restriction policy are available. If you disable this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager. If you don't configure this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager.
  
  **Default**: Disable  
  
- **Internet Explorer security settings check**  
  This policy setting turns off the Security Settings Check feature, which checks Internet Explorer security settings to determine when the settings put Internet Explorer at risk. If you enable this policy setting, the feature is turned off. If you disable or don't configure this policy setting, the feature is turned on.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Prompt  
  
- **Internet Explorer intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: High safety 
  
- **Internet Explorer block outdated Active X controls**  
  This policy setting determines whether Internet Explorer blocks specific outdated ActiveX controls. Outdated ActiveX controls are never blocked in the Intranet Zone. If you enable this policy setting, Internet Explorer stops blocking outdated ActiveX controls. If you disable or don't configure this policy setting, Internet Explorer continues to block specific outdated ActiveX controls. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes MK protocol security restriction**  
  The MK Protocol Security Restriction policy setting reduces attack surface area by preventing the MK protocol. Resources hosted on the MK protocol will fail. If you enable this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail. If you disable this policy setting, applications can use the MK protocol API. Resources hosted on the MK protocol will work for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Low Safety.
  
  **Default**: High safety  
  
- **Internet Explorer restricted zone scripting of java applets**  
  This policy setting allows you to manage whether applets are exposed to scripts within the zone. If you enable this policy setting, scripts can access applets automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow scripts to access applets. If you disable this policy setting, scripts are prevented from accessing applets. If you don't configure this policy setting, scripts are prevented from accessing applets.
  
  **Default**: Disable  
  
- **Internet Explorer locked down restricted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer include all network paths**  
  Internet Explorer include all network paths
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer locked down restricted zone smart screen**   
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer crash detection**  
  This policy setting allows you to manage the crash detection feature of add-on Management. If you enable this policy setting, a crash in Internet Explorer will exhibit behavior found in Windows XP Professional Service Pack 1 and earlier, namely to invoke Windows Error Reporting. All policy settings for Windows Error Reporting continue to apply. If you disable or don't configure this policy setting, the crash detection feature for add-on management is functional.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to High Safety.
  
  **Default**: Disable java  
  
- **Internet Explorer restricted zone active scripting**  
  This policy setting allows you to manage whether script code on pages in the zone is run. If you enable this policy setting, script code on pages in the zone can run automatically. If you select Prompt in the drop-down box, users are queried to choose whether to allow script code on pages in the zone to run. If you disable this policy setting, script code on pages in the zone is prevented from running. If you don't configure this policy setting, script code on pages in the zone is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. Anonymous log on to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. Prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the remainder of the session. Automatic log on only in Intranet zone to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. Automatic sign in with current user name and password to attempt log on using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for log on. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. If you disable this policy setting, sign in is set to Automatic log on only in Intranet zone. If you don't configure this policy setting, sign in is set to Automatic sign in only in Intranet zone.
  
  **Default**: Prompt  
  
- **Internet Explorer restricted zone allow vbscript to run**  
  This policy setting allows you to manage whether VBScript can be run on pages from the specified zone in Internet Explorer. If you selected Enable in the drop-down box, VBScript can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow VBScript to run. If you selected Disable in the drop-down box, VBScript is prevented from running. If you don't configure or disable this policy setting, VBScript is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disabled 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer download enclosures**  
  This policy setting prevents the user from having enclosures (file attachments) downloaded from a feed to the user's computer. If you enable this policy setting, the user can't set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can't change the download setting through the Feed APIs. If you disable or don't configure this policy setting, the user can set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can change the download setting through the Feed APIs.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone download unsigned Active X controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains within windows**  
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict Active X install**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of ActiveX control installation. If you enable this policy setting, the Web Browser Control will block automatic prompting of ActiveX control installation for all processes. If you disable or don't configure this policy setting, the Web Browser Control won't block automatic prompting of ActiveX control installation for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone scriptlets**
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files**  
  This policy setting allows you to manage whether users can drag files or copy and paste files from a source within the zone. If you enable this policy setting, users can drag files or copy and paste files from this zone automatically. If you select Prompt in the drop-down box, users are queried to choose whether to drag or copy files from this zone. If you disable this policy setting, users are prevented from dragging files or copying and pasting files from this zone. If you don't configure this policy setting, users are queried to choose whether to drag or copy files from this zone.
  
  **Default**: Disable  
  
- **Internet Explorer software when signature is invalid**   
  This policy setting allows you to manage whether software, such as ActiveX controls and file downloads, can be installed or run by the user even though the signature is invalid. An invalid signature might indicate that someone has tampered with the file. If you enable this policy setting, users are prompted to install or run files with an invalid signature. If you disable this policy setting, users can't run or install files with an invalid signature. If you don't configure this policy, users can choose to run or install files with an invalid signature.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone copy and paste via script**   
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can't perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.   
  **Default**: Disabled  
  
- **Internet Explorer users adding sites**  
  Prevents users from adding or removing sites from security zones. A security zone is a group of Web sites with the same security level. If you enable this policy, the site management settings for security zones are disabled. (To see the site management settings for security zones, in the Internet Options dialog box, click the Security tab, and then click the Sites button.) If you disable this policy or don't configure it, users can add Web sites to or remove sites from the Trusted Sites and Restricted Sites zones, and alter settings for the Local Intranet zone. This policy prevents users from changing site management settings for security zones established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from the interface, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled  
  
- **Internet Explorer security zones use only machine settings**  
  Applies security zone information to all users of the same computer. A security zone is a group of Web sites with the same security level. If you enable this policy, changes that the user makes to a security zone will apply to all users of that computer. If you disable this policy or don't configure it, users of the same computer can establish their own security zone settings. Use this policy to ensure that security zone settings apply uniformly to the same computer and don't vary from user to user. Also, see the "Security zones: don't allow users to change policies" policy.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled
  
  **Default**: Disable java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone copy and paste via script**  
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer use Active X installer service**   
  This policy setting allows you to specify how ActiveX controls are installed. If you enable this policy setting, ActiveX controls are installed only if the ActiveX Installer Service is present and has been configured to allow the installation of ActiveX controls. If you disable or don't configure this policy setting, ActiveX controls, including per-user controls, are installed through the standard installation process.
  
  **Default**: Enabled  
  
- **Internet Explorer processes protection from zone elevation**  
  Internet Explorer places restrictions on each Web page it opens. The restrictions are dependent upon the location of the Web page (Internet, Intranet, Local Machine zone, and so on). For example, Web pages on the local computer have the fewest security restrictions and are in the Local Machine zone, making the Local Machine security zone a prime target for malicious users. If you enable this policy setting, any zone can be protected from zone elevation for all processes. If you disable or don't configure this policy setting, processes other than Internet Explorer or those listed in the Process List receive no such protection.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download unsigned ActiveX controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**   
  This policy setting allows you to manage the opening of windows and frames and access of applications across different domains. If you enable this policy setting, users can open windows and frames from other domains and access applications from other domains. If you select Prompt in the drop-down box, users are queried whether to allow windows and frames to access applications from other domains. If you disable this policy setting, users can't open windows and frames to access applications from different domains. If you don't configure this policy setting, users can open windows and frames from other domains and access applications from other domains.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone updates to status bar via script**  
  This policy setting allows you to manage whether a script can update the status bar within the zone. If you enable this policy setting, scripts can update the status bar. If you disable or don't configure this policy setting, script isn't allowed to update the status bar.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone include local path when uploading files to server**  
  This policy setting controls if local path information is sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information is sent when they are uploading a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict file download**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of file downloads that aren't user initiated. If you enable this policy setting, the Web Browser Control will block automatic prompting of file downloads that aren't user initiated for all processes. If you disable this policy setting, the Web Browser Control won't block automatic prompting of file downloads that aren't user initiated for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer users changing policies**  
    Prevents users from changing security zone settings. A security zone is a group of Web sites with the same security level. If you enable this policy, the Custom Level button and security-level slider on the Security tab in the Internet Options dialog box are disabled. If you disable this policy or don't configure it, users can change the settings for security zones. This policy prevents users from changing security zone settings established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from Internet Explorer in Control Panel, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
    
  **Default**: Disabled  
  
- **Internet Explorer restricted zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable  
  
- **Internet Explorer internet zone user data persistence**  
  This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone scripting of web browser controls**  
 
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone user data persistence**  
    This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.  
  
  **Default**: Disabled  
  
- **Internet Explorer locked down intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
  
- **Internet Explorer enhanced protected mode**  
  Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. If you enable this policy setting, Enhanced Protected Mode is turned on. Any zone that has Protected Mode enabled will use Enhanced Protected Mode. Users won't be able to disable Enhanced Protected Mode. If you disable this policy setting, Enhanced Protected Mode is turned off. Any zone that has Protected Mode enabled will use the version of Protected Mode introduced in Internet Explorer 7 for Windows Vista. If you don't configure this policy, users can turn on or turn off Enhanced Protected Mode on the Advanced tab of the Internet Options dialog.
  
  **Default**: Enabled  
  
- **Internet Explorer bypass smart screen warnings**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone meta refresh**  
  This policy setting allows you to manage whether a user's browser can be redirected to another Web page if the author of the Web page uses the Meta Refresh setting (tag) to redirect browsers to another Web page. If you enable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can be redirected to another Web page. If you disable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page. If you don't configure this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page.
  
  **Default**: Disabled  
  
## Local Policies Security Options
For more information, see [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in the Windows documentation. 

- **Restrict anonymous access to named pipes and shares**  
  When enabled, this security setting restricts anonymous access to shares and pipes to the settings for: (1) Named pipes that can be accessed anonymously (2) Shares that can be accessed anonymously
  
  **Default**: Yes  
  
- **Minimum session security for NTLM SSP based servers**  
  This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are: Require NTLMv2 session security: The connection will fail if message integrity isn't negotiated. Require 128-bit encryption. The connection will fail if strong encryption (128-bit) isn't negotiated.
  
  **Default**: Require NTLM V2 and 128 bit encryption  
  
- **Minutes of lock screen inactivity until screen saver activates**  
  Windows notices inactivity of a logon session, and if the amount of inactive time exceeds the inactivity limit, then the screen saver will run, locking the session.
  
  **Default**: 15
  
- **Require client to always digitally sign communications** 
  This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted. When a computer joins a domain, a computer account is created. After that, when the system starts, it uses the computer account password to create a secure channel with a domain controller for its domain. This secure channel is used to perform operations such as NTLM pass through authentication, LSA SID/name Lookup and more. This setting determines if all secure channel traffic initiated by the domain member meets minimum security requirements. Specifically it determines whether all secure channel traffic started by the domain member must be signed or encrypted. If this policy is enabled, then the secure channel won't be established unless either signing or encryption of all secure channel traffic is negotiated. If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies: Domain member: Digitally encrypt secure channel data (when possible) Domain member: Digitally sign secure channel data (when possible)
  
  **Default**: Yes
  
- **Authentication level**  
  This security setting determines which challenge/response authentication protocol is used for network logons. This choice affects the level of authentication protocol used by clients, the level of session security negotiated, and the level of authentication accepted by servers as follows:  
  - *Send LM and NTLM responses*: Clients use LM and NTLM authentication and never use NTLMv2 session security; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send LM and NTLM - NTLMv2 if negotiated*: Clients use LM and NTLM authentication and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLM response only*: Clients use NTLM authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only. Refuse LM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM (accept only NTLM and NTLMv2 authentication). 
  - *Send NTLMv2 response only. Refuse LM and NTLM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM and NTLM (accept only NTLMv2 authentication). 
    
  **Default**: Send NTLMv2 response only. Refuse LM and NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers**  
  If this security setting is enabled, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. Sending unencrypted passwords is a security risk.
  
  **Default**: Yes
  
- **Disable server digitally signing communications always**  
  This security setting determines whether the SMB client attempts to negotiate SMB packet signing. The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent man-in-the-middle attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether the SMB client component attempts to negotiate SMB packet signing when it connects to an SMB server. If this setting is enabled, the Microsoft network client will ask the server to perform SMB packet signing upon session setup. If packet signing has been enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client will never negotiate SMB packet signing.
  
  **Default**: Yes
  
- **Administrator elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for administrators. The options are: 
    - *Elevate without prompting*: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments. 
    - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege. 
    - *Prompt for consent on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege. 
    - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
    - *Prompt for consent*: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.  
    - *Prompt for consent for non-Windows binaries*: When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.   
  
  **Default**: Prompt for consent on the secure desktop
  
- **Minimum session security for NTLM SSP based clients**  
  This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are:
  - Require NTLMv2 session security: The connection will fail if NTLMv2 protocol isn't negotiated. 
  - *Require 128-bit encryption*: The connection will fail if strong encryption (128-bit) isn't negotiated.
  - *Require NTLMv2 and 128-bit encryption*. 

  **Default**: Require NTLM V2 128 encryption
  
- **Smart card removal behavior**  
    This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. The options are:
     - *No action*. 
     - *Lock Workstation* - The workstation is locked when the smart card is removed, allowing users to leave the area, take their smart card with them, and still maintain a protected session.
     - *Force Logoff* - the user is automatically logged off when the smart card is removed.
     - *Disconnect Remote Desktop session* - Removal of the smart card disconnects the session without logging the user off. This allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to log on again. If the session is local, this policy functions identically to Lock Workstation.   
    
  **Default**: Lock workstation
  
- **Block anonymous enumeration of SAM accounts and shares**  
  This security setting determines whether to allow anonymous enumeration of SAM accounts and shares. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. If you don't want to allow anonymous enumeration of SAM accounts and shares, then set this policy to *Yes*.
  
  **Default**: Yes
  
- **Block remote logon with blank password**  
  This security setting determines whether local accounts that aren't password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that aren't password protected must use the computer's keyboard to log on. 

  *Warning*: Computers that aren't in physically secure locations should always enforce strong password policies for all local user accounts. Otherwise, anyone with physical access to the computer can log on by using a user account that doesn't have a password. This is especially important for portable computers. 

  If you apply this security policy to the Everyone group, no one can log on through Remote Desktop Services. This setting doesn't affect logons that use domain accounts. It's possible for applications that use remote interactive logons to bypass this setting.
  
  **Default**: Yes
  
- **Standard user elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for standard users. 
  - *Automatically deny elevation requests*: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls. 
  - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.  
  
  **Default**: Automatically deny elevation requests
  
- **Require admin approval mode for administrators**  
  This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer. The options are:   
  - *Not configured*: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced. 
  - *Yes*: Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.  
  
  **Default**: Yes
  
- **Prevent anonymous enumeration of SAM accounts**  
  This security setting determines what additional permissions are granted for anonymous connections to the computer. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. This security option allows additional restrictions to be placed on anonymous connections as follows: 
  - *Yes*: Don't allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources.
  - *Not configured*: No additional restrictions. Rely on default permissions.  
  
  **Default**: Yes
  
- **Allow remote calls to security accounts manager**  
  This policy setting allows you to restrict remote rpc connections to SAM. If not selected, the default security descriptor is used.
  
  **Default**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode**  
  This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account. The options are: 
  - *Yes*: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation. 
  - *Not Configured*: The built-in Administrator account runs all applications with full administrative privilege.  

  **Default**: Yes
  
- **Allow UI access applications for secure locations**  
  This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user. 
  - *Yes*: UIA programs, including Windows Remote Assistance, automatically disable the secure desktop for elevation prompts. If you don't disable the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting, the prompts appear on the interactive user's desktop instead of the secure desktop. 
  - *Not Configured*: The secure desktop can be disabled only by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting.  

  **Default**: Yes

- **Detect application installations and prompt for elevation**  
  This policy setting controls the behavior of application installation detection for the computer. The options are: 
  - *Enabled*: When an application installation package is detected that requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Disabled*: Application installation packages aren't detected and prompted for elevation. Enterprises that are running standard user desktops and use delegated installation technologies such as Group Policy Software Installation or Systems Management Server (SMS) should disable this policy setting. In this case, installer detection is unnecessary.  
  
  **Default**: Yes
  
- **Prevent storing LAN manager hash value on next password change**  
  This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.
  
  **Default**: Yes

- **Virtualize file and registry write failures to per user locations**  
  This policy setting controls whether application write failures are redirected to defined registry and file system locations. This policy setting mitigates applications that run as administrator and write run-time application data to *%ProgramFiles%*, *%Windir%*, *%Windir%\system32*, or *HKLM\Software*.
  
  **Default**: Yes

## MS Security Guide  
For more information, see [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in the Windows documentation.  

- **Apply UAC restrictions to local accounts on network logon**  
  **Default**: Enabled
  
- **SMB v1 client driver start configuration**  
  **Default**: Disabled driver
  
- **SMB v1 server**  
  **Default**: Disabled
  
- **Digest authentication**  
  **Default**: Disabled
  
- **Structured exception handling overwrite protection**  
  **Default**: Enabled
  
## MSS Legacy  
For more information, see [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in the Windows documentation.  

- **Network IP source routing protection level**  
  **Default**: Highest protection  
  
- **Network ignore NetBIOS name release requests except from WINS servers**  
  **Default**: Enabled
  
- **Network IPv6 source routing protection level**  
  **Default**: Highest protection

- **Network ICMP redirects override OSPF generated**  
  **Default**: Disabled
  
## Power  
For more information, see [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentation.  

- **Require password on wake while plugged in**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
- **Standby states when sleeping while on battery**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Standby states when sleeping while plugged in**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Require password on wake while on battery**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
## Remote Desktop Services  
For more information, see [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in the Windows documentation.  

- **Block password saving**  
  Controls whether passwords can be saved on this computer from Remote Desktop Connection. If you enable this setting the password saving checkbox in Remote Desktop Connection is disabled and users won't be able to save passwords. When a user opens an RDP file using Remote Desktop Connection and saves their settings, any password that previously existed in the RDP file are deleted. If you disable this setting or leave it not configured, the user can save passwords using Remote Desktop Connection.
  
   **Default**: Enabled
  
- **Secure RPC communication**  
  Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication. You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests. If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and doesn't allow unsecured communication with untrusted clients. If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that don't respond to the request. If the status is set to Not Configured, unsecured communication is allowed. Note: The RPC interface is used for administering and configuring Remote Desktop Services.
  
  **Default**: Enabled
  
- **Block drive redirection**  
  This policy setting specifies whether to prevent the mapping of client drives in a Remote Desktop Services session (drive redirection). By default, an RD Session Host server maps client drives automatically upon connection. Mapped drives appear in the session folder tree in File Explorer or Computer in the format *\<driveletter>* on *\<computername>*. You can use this policy setting to override this behavior. If you enable this policy setting, client drive redirection isn't allowed in Remote Desktop Services sessions, and Clipboard file copy redirection isn't allowed on computers running Windows Server 2003, Windows 8, and Windows XP. If you disable this policy setting, client drive redirection is always allowed. Also, Clipboard file copy redirection is always allowed if Clipboard redirection is allowed. If you don't configure this policy setting, client drive redirection and Clipboard file copy redirection aren't specified at the Group Policy level.
  
  **Default**: Enabled
  
- **Prompt for password upon connection**  
  This policy setting specifies whether Remote Desktop Services always prompts the client for a password upon connection. You can use this setting to enforce a password prompt for users logging on to Remote Desktop Services, even if they already provided the password in the Remote Desktop Connection client. By default, Remote Desktop Services allows users to automatically log on by entering a password in the Remote Desktop Connection client. If you enable this policy setting, users can't automatically log on to Remote Desktop Services by supplying their passwords in the Remote Desktop Connection client. they're prompted for a password to log on. If you disable this policy setting, users can always log on to Remote Desktop Services automatically by supplying their passwords in the Remote Desktop Connection client. If you don't configure this policy setting, automatic logon isn't specified at the Group Policy level. 
  
  **Default**: Enabled
  
- **Remote desktop services client connection encryption level**  
  Specifies whether to require the use of a specific encryption level to secure communications between client computers and RD Session Host servers during Remote Desktop Protocol (RDP) connections. This policy only applies when you're using native RDP encryption. However, native RDP encryption (as opposed to SSL encryption) isn't recommended. This policy doesn't apply to SSL encryption. If you enable this policy setting, all communications between clients and RD Session Host servers during remote connections must use the encryption method specified in this setting. By default, the encryption level is set to High. The following encryption methods are available:  
  - *High*: The High setting encrypts data sent from the client to the server and from the server to the client by using strong 128-bit encryption. Use this encryption level in environments that contain only 128-bit clients (for example, clients that run Remote Desktop Connection). Clients that don't support this encryption level can't connect to RD Session Host servers.  
  - *Client Compatible*: The Client Compatible setting encrypts data sent between the client and the server at the maximum key strength supported by the client. Use this encryption level in environments that include clients that don't support 128-bit encryption.  
  - *Low*: The Low setting encrypts only data sent from the client to the server by using 56-bit encryption.  
  
  If you disable or don't configure this setting, the encryption level to be used for remote connections to RD Session Host servers isn't enforced through Group Policy. Important FIPS compliance can be configured through the System cryptography. Use FIPS-compliant algorithms for encryption, hashing, and signing settings in Group Policy (under Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options.) The FIPS-compliant setting encrypts and decrypts data sent from the client to the server and from the server to the client, with the Federal Information Processing Standard (FIPS) 140 encryption algorithms, by using Microsoft cryptographic modules. Use this encryption level when communications between clients and RD Session Host servers requires the highest level of encryption.
  
  **Default**: High
  
## Remote Management  
For more information, see [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in the Windows documentation.  

- **Block storing run as credentials**  
  Client basic authentication
  
  **Default**: Enabled
  
- **Basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service accepts Basic authentication from a remote client. If you enable this policy setting, the WinRM service accepts Basic authentication from a remote client. If you disable or don't configure this policy setting, the WinRM service doesn't accept Basic authentication from a remote client.
  
  **Default**: Disabled
  
- **Block client digest authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Digest authentication. If you enable this policy setting, the WinRM client doesn't use Digest authentication. If you disable or don't configure this policy setting, the WinRM client uses Digest authentication.
  
  **Default**: Enabled
  
- **Unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.  
  
  **Default**: Disabled
  
- **Client unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.
  
  **Default**: Disabled
  
- **Client basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Basic authentication. If you enable this policy setting, the WinRM client uses Basic authentication. If WinRM is configured to use HTTP transport, the user name and password are sent over the network as clear text. If you disable or don't configure this policy setting, the WinRM client doesn't use Basic authentication.
  
  **Default**: Disabled
  

## Remote Procedure Call  
For more information, see [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in the Windows documentation.  

- **RPC unauthenticated client options**  
  This policy setting controls how the RPC server runtime handles unauthenticated RPC clients connecting to RPC servers. This policy setting impacts all RPC applications. In a domain environment, use this policy setting with caution as it can impact a wide range of functionality including group policy processing itself. Reverting a change to this policy setting can require manual intervention on each affected machine. This policy setting should never be applied to a domain controller. If you disable this policy setting, the RPC server runtime uses the value of "Authenticated" on Windows Client, and the value of "None" on Windows Server versions that support this policy setting. If you don't configure this policy setting, it remains disabled. The RPC server runtime behaves as though it was enabled with the value of "Authenticated" used for Windows Client and the value of "None" used for Server SKUs that support this policy setting. If you enable this policy setting, it directs the RPC server runtime to restrict unauthenticated RPC clients connecting to RPC servers running on a machine. A client is considered an authenticated client if it uses a named pipe to communicate with the server or if it uses RPC Security. RPC Interfaces that have specifically requested to be accessible by unauthenticated clients may be exempt from this restriction, depending on the selected value for this policy setting.  
  - *None* allows all RPC clients to connect to RPC Servers running on the machine on which the policy setting is applied. 
  - *Authenticated* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. Exemptions are granted to interfaces that have requested them. 
  - *Authenticated without exceptions* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. No exceptions are allowed. Note: This policy setting won't be applied until the system is rebooted.  

  **Default**: Authenticated

## Search 
For more information, see [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in the Windows documentation.  

- **Disable indexing encrypted items**  
  Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it will index items that are encrypted, such as the Windows Information Protection (WIP) protected files. When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified. When the policy is disabled, the WIP protected items aren't indexed and don't show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.
  
**Default**: Yes
  
## Smart Screen  
For more information, see [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in the Windows documentation.  

- **Block execution of unverified files**  
  Block user from running unverified files. 
  - *Not Configured* - Employees can ignore SmartScreen warnings and run malicious files. 
  - *Yes* – Employees can't ignore SmartScreen warnings and run malicious files.

  **Default**: Yes

- **Require SmartScreen for apps and files**  
  Allows IT Admins to configure SmartScreen for Windows.

  **Default**: Yes
  
## System  
For more information, see [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in the Windows documentation.  

- **System boot start driver initialization**  
  This policy setting allows you to specify which boot-start drivers are initialized based on a classification determined by an Early Launch Antimalware boot-start driver. The Early Launch Antimalware boot-start driver can return the following classifications for each boot-start driver: 
  - *Good*: The driver has been signed and hasn't been tampered with.  
  - *Bad* - The driver has been identified as malware. We recommend that you don't allow known bad drivers to be initialized. 
  - *Bad, but required for boot*: The driver has been identified as malware, but the computer can't successfully boot without loading this driver. 
  - *Unknown* - This driver hasn't been attested to by your malware detection application and hasn't been classified by the Early Launch Antimalware boot-start driver.  

  If you enable this policy setting, you can choose which boot-start drivers to initialize the next time the computer is started. If you disable or don't configure this policy setting, the boot start drivers determined to be Good, Unknown, or Bad but Boot Critical are initialized and the initialization of drivers determined to be Bad is skipped. If your malware detection application doesn't include an Early Launch Antimalware boot-start driver or if your Early Launch Antimalware boot-start driver has been disabled, this setting has no effect and all boot-start drivers are initialized.  
  
  **Default**: Good unknown and bad critical


## Wi-Fi  
For more information, see [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in the Windows documentation.  

- **Block Internet sharing**  
  Specifies whether internet sharing is possible on the device.  

  **Default**: Yes  

- **Block Automatically connecting to Wi-Fi hotspots**  
  Allow or disallow the device to automatically connect to Wi-Fi hotspots.  

  **Default**: Yes  
  
## Windows Connection Manager  
For more information, see [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in the Windows documentation.  

- **Block connection to non-domain networks**  
  This policy setting prevents computers from connecting to both a domain-based network and a non-domain based network at the same time. If this policy setting is enabled, the computer responds to automatic and manual network connection attempts based on the following circumstances: 
  - Automatic connection attempts When the computer is already connected to a domain-based network, all automatic connection attempts to non-domain networks are blocked. When the computer is already connected to a non-domain based network, automatic connection attempts to domain-based networks are blocked. 
  - Manual connection attempts When the computer is already connected to either a non-domain based network or a domain-based network over media other than Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing network connection disconnects and the manual connection is allowed. When the computer is already connected to either a non-domain based network or a domain-based network over Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing Ethernet connection is maintained and the manual connection attempt is blocked.  

  If this policy setting isn't configured or is disabled, computers are allowed to connect simultaneously to both domain and non-domain networks.  

  **Default**: Enabled
  
## Windows Defender  
For more information, see [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in the Windows documentation.  

- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Yes  

- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Block
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not, (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Send safe samples automatically 
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: 4
  
- **Script downloaded payload execution type**  
  Defender script downloaded payload execution type
  
  **Default**: Block
  
- **Prevent credential stealing type**  
  Windows Defender Credential Guard uses virtualization-based security to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket. Windows Defender Credential Guard prevents these attacks by protecting NTLM password hashes, Kerberos Ticket Granting Tickets, and credentials stored by applications as domain credentials.
  
  **Default**: Enable

- **Email content execution type**  
  This rule blocks the following file types from being run or launched from an email seen in either Microsoft Outlook or webmail (such as Gmail.com or Outlook.com): Executable files (such as .exe, .dll, or .scr) Script files (such as a PowerShell .ps, VisualBasic .vbs, or JavaScript .js file) Script archive files.
  
  **Default**: Block
  
- **Network protection type**  
  This policy allows you to turn on network protection (block/audit) or off in Windows Defender Exploit Guard. Network protection is a feature of Windows Defender Exploit Guard that protects employees using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. This includes preventing third-party browsers from connecting to dangerous sites. Value type is integer. If you enable this setting, network protection is turned on and employees can't turn it off. Its behavior can be controlled by the following options: Block and Audit. If you enable this policy with the "Block" option, users and apps are blocked from connecting to dangerous domains. You can see this activity in Windows Defender Security Center. If you enable this policy with the "Audit" option, users/apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in Windows Defender Security Center. If you disable this policy, users/apps won't be blocked from connecting to dangerous domains. You'll not see any network activity in Windows Defender Security Center. If you don't configure this policy, network blocking is disabled by default.
  
  **Default**: Enable
  
- **Defender schedule scan day**  
  Defender schedule scan day.
  
  **Default**: Everyday
  
- **Cloud-delivered protection**  
  To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions.
  
  **Default**:  Yes  

- **Defender potentially unwanted app action**  
  The potentially unwanted application (PUA) protection feature in Windows Defender Antivirus can identify and block PUAs from downloading and installing on endpoints in your network. These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have a poor reputation. Typical PUA behavior includes: Various types of software bundling Ad injection into web browsers Driver and registry optimizers that detect issues, request payment to fix the errors, but remain on the endpoint and make no changes or optimizations (also known as "rogue antivirus" programs). These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.  
  
  **Default**: Block  

- **Script obfuscated macro code type**  
  Malware and other threats can attempt to obfuscate or hide their malicious code in some script files. This rule prevents scripts that appear to be obfuscated from running.
  
  **Default**: Block
  
- **Scan removable drives during a full scan**  
  Allows Windows Defender to scan for malicious and unwanted software in removable drives (for example, flash drives) during a full scan. Windows Defender Antivirus scans all files on USB devices before execution.
  
  **Default**: Yes  
  
- **Scan archive files**  
  Defender scan archive files.
  
  **Default**: Yes
  
- **Behavior monitoring**  
  Allows or disallows Windows Defender Behavior Monitoring functionality.Embedded in Windows 10, these sensors collect and process behavioral signals from the operating system and sends this sensor data to your private, isolated, cloud instance of Microsoft Defender ATP.
  
  **Default**: Yes

- **Scan files opened from network folders**  
  If files are read-only, user won't be able to remove any detected malware.
  
  **Default**: Yes

- **Untrusted USB process type**  
  With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards.
  
  **Default**: Block
  
- **Office apps other process injection type**  
  Office apps, including Word, Excel, PowerPoint, and OneNote, won't be able to inject code into other processes. This is typically used by malware to run malicious code in an attempt to hide the activity from antivirus scanning engines.
  
  **Default**:  Block
  
- **Office macro code allow Win32 imports type**  
  Malware can use macro code in Office files to import and load Win32 DLLs, which can then be used to make API calls to allow further infection throughout the system. This rule attempts to block Office files that contain macro code that is capable of importing Win32 DLLs. This includes Word, Excel, PowerPoint, and OneNote.
  
  **Default**: Block  
  
- **Defender cloud block level**  
  Defender cloud block level.
  
  **Default**: Not Configured

- **Real-time monitoring**  
  Defender requires real-time monitoring.
  
  **Default**: Yes
  
- **Office apps executable content creation or launch type**  
  This rule targets typical behaviors used by suspicious and malicious add-ons and scripts (extensions) that create or launch executable files. This is a typical malware technique. Extensions are blocked from being used by Office apps. Typically these extensions use the Windows Scripting Host (.wsh files) to run scripts that automate certain tasks or provide user-created add-on features
  
  **Default**: Block

## Windows Ink Workspace  
For more information, see [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in the Windows documentation.  

- **Ink Workspace**  
  Specifies whether to allow the user to access the ink workspace. 
  - *Disabled* - access to ink workspace is disabled. The feature is turned off.
  - *Enabled* - The Ink Workspace feature is turned on, but the user can't access it above the lock screen.
  - *Not Configured* - The Ink Workspace feature is turned on, and the user can use it above the lock screen.  

  **Default**: Enabled
 
## Windows PowerShell  
For more information, see [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in the Windows documentation.  

- **Power shell shell script block logging**  
  This policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log. If you enable this policy setting, Windows PowerShell will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation. If you disable this policy setting, logging of PowerShell script input is disabled. If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops. Enabling Invocation Logging generates a high volume of event logs. Note: This policy setting exists under both Computer Configuration and User Configuration in the Group Policy Editor. The Computer Configuration policy setting takes precedence over the User Configuration policy setting.
  
  **Default**: Enabled
 

End of PReview baseilne list  -->
