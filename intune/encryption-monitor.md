---
title: Microsoft Intune 中的加密报表和 BitLocker 密钥
titleSuffix: Microsoft Intune
description: 查看关于设备加密状态的报表，并通过 Microsoft Intune 门户访问 BitLocker 恢复密钥。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d90bc17d01a76c9c566210edc3bdc265511fa16d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047825"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>监视 BitLocker 和设备加密  
Intune 提供一个集中位置用于识别 Windows 10 设备的加密状态，并帮助你通过设备访问 BitLocker 的重要信息，如 Azure Active Directory (Azure AD) 中所示。  

- [加密报表](#encryption-report)提供关于设备加密状态和就绪状态的详细信息。 报表的详细信息有助于找出导致无法成功加密所要保护的设备的问题。  
- 通过 Intune 门户[查看 BitLocker 的详细信息](#bitlocker-recovery-keys)，比如设备密钥 ID 和恢复密钥。  

## <a name="encryption-report"></a>加密报表
可以使用加密报表查看关于 Windows 10 设备加密状态的详细信息。  

要查找报表，请登录 [Intune](https://aka.ms/intuneportal)，前往“设备配置”，然后在“监视”下，选择“加密报表”。  

### <a name="prerequisites"></a>先决条件：
为了在加密报表中显示，设备必须运行 Windows 1607 版本或更高版本。  

### <a name="report-details"></a>报表详细信息
报表显示 Windows 10 设备的“设备名称”以及每个设备的高级详细信息，包括以下内容：  
- **OS 版本** – Windows 版本。  
- **TPM 版本** – 设备上受信任平台模块 (TPM) 芯片的版本。  
- **加密就绪状态** – 对设备支持 BitLocker 加密的就绪状态的评估。 设备可标识为：
  - **就绪**：可以使用 MDM 策略加密设备，要求是设备具有 TPM，并满足以下 Windows 10 版本和 SKU 的要求：
    - 商业版、企业版和教育版为 1703 版本或更高版本
    - 专业版为 1809 版本或更高版本  
  
    有关详细信息，请参阅 Windows 文档中的 [BitLocker 配置服务提供商 (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)。  

  - **未就绪**：设备不具完备的加密功能，但仍支持加密。 例如，用户可以手动加密设备，也可以通过可设置为无需 TMP 即可加密的组策略加密设备。
  - **不适用**：用于对此设备进行分类的信息不足。  

- **加密状态** – OS 驱动器是否加密。  


### <a name="device-encryption-status"></a>设备加密状态
选择设备时，Intune 会显示“设备加密状态”窗格。

此窗格提供以下详细信息：  
- **设备名称** – 所查看设备的名称。  
- **加密就绪状态** - 对设备支持 BitLocker 加密的就绪状态的评估。 即使设备由于缺少 TPM 而导致加密就绪状态为“未就绪”，加密状态也可能为“已加密”。 （有关详细信息，请参阅上述部分中的加密就绪状态。）
- **加密状态** - OS 驱动器是否加密。  
- **配置文件** – 适用于此设备并包括以下配置文件类型和设置的“设备配置”配置文件列表：  
  - 配置文件类型 = 终结点保护  
  - 设置 > Windows 加密 > 加密设备 = 需要  

  如果配置文件状态摘要表明存在问题，则此列表可用于查找特定策略以供查看。  

- **配置文件状态摘要** – 适用于此设备的配置文件摘要。 摘要表示所有适用配置文件中的最不利条件。 例如，如果某个配置文件导致出现错误，配置文件状态摘要将显示“错误”。  
- **状态详细信息** – 关于设备加密状态的高级详细信息。 
  > [!NOTE]  
  > Intune 仅显示运行 Windows 10 2019 年 4 月更新版或更高版本的设备的状态详细信息。
  
  此字段显示可检测到的每个适用错误的信息。 使用此信息可了解设备加密未准备就绪的原因。  

  Intune 可能报告的状态详细信息示例如下：  

   - BitLocker 策略需要用户同意启动 BitLocker 驱动器加密向导以开始加密 OS 卷，但用户未同意。  
   - OS 卷的加密方法与 BitLocker 策略不匹配。  
   - BitLocker 策略需要 TPM 保护程序保护 OS 卷，但未使用 TPM。  
   - BitLocker 策略需要只有 TPM 的保护程序保护 OS 卷，但未使用 TPM 保护。  
   - BitLocker 策略需要对 OS 卷使用 TPM+PIN 保护，但未使用 TPM+PIN 保护程序。  
   - BitLocker 策略需要对 OS 卷使用 TPM+启动密钥保护，但未使用 TPM+启动密钥保护程序。  
   - BitLocker 策略需要对 OS 卷使用 TPM+PIN+启动密钥保护，但未使用 TPM+PIN+启动密钥保护程序。  
   - OS 卷未受保护。  
   - 恢复密钥备份失败。  
   - 固定驱动器未受保护。  
   - 固定驱动器的加密方法与 BitLocker 策略不匹配。  
   - 为了加密驱动器，BitLocker 策略需要用户以管理员身份登录，或者，如果设备连接到 Azure AD，AllowStandardUserEncryption 策略必须设置为 1。  
   - Windows 恢复环境 (WinRE) 未配置。  
   - TPM 无法用于 BitLocker，原因是 TPM 不存在，导致在注册表中不可用，或者是 OS 位于可删除驱动器。  
   - TPM 未准备就绪，BitLocker 无法使用。  
   - 恢复密钥备份所需的网络不可用。  

## <a name="bitlocker-recovery-keys"></a>BitLocker 恢复密钥
Intune 允许访问 BitLocker 的 Azure AD 边栏选项卡，因此可通过 Intune 门户查看 Windows 10 设备的 BitLocker 密钥 ID 和恢复密钥。  为了能够访问，设备必须将其密钥托管到 Azure AD。 
1. 登录 [Intune](https://aka.ms/intuneportal)，前往“设备”，然后在“管理”下，选择“所有设备”。
2. 选择列表中的设备，然后在“监视”下，选择“恢复密钥”。  
  
如果 Azure AD 中有密钥，将提供以下信息：
- BitLocker 密钥 ID
- BitLocker 恢复密钥
- 驱动器类型  

如果 Azure AD 中没有密钥，Intune 将显示“未找到此设备的 BitLocker 密钥”。  

使用 [BitLocker 配置服务提供程序](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (CSP) 获取 BitLocker 的信息。 Windows 10 1703 版本和更高版本，以及 Windows 10 专业版 1809 版本和更高版本支持 BitLocker CSP。 

## <a name="next-steps"></a>后续步骤
创建适用于 Windows 10 设备的[设备合规性](compliance-policy-create-windows.md)策略来配置 BitLocker 和加密。
