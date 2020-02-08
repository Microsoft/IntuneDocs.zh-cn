---
title: Microsoft Intune 中 BitLocker 策略的故障排除提示
titleSuffix: Microsoft Intune
description: 描述如何使用 Intune 策略在设备上启用 BitLocker 加密，以及如何验证策略是否已成功部署到设备。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61b703837598ddbe2c0c44874928b4444466c811
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886778"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Microsoft Intune 中 BitLocker 策略的故障排除

本文可帮助 Intune 管理员了解 Windows 10 设备如何根据 Intune 策略配置 BitLocker。 本文还提供有关如何使用通过 Intune 进行管理的设备上的 BitLocker 设置进行故障排除的指南。  

## <a name="understanding-bitlocker"></a>了解 BitLocker

BitLocker 驱动器加密是 Microsoft Windows 操作系统提供的一项服务，用户可通过该服务加密其硬盘驱动器上的数据。 BitLocker 支持对操作系统驱动器、可移动媒体驱动器和固定数据驱动器进行加密。 BitLocker 还支持使用 256 位加密来更好地保护敏感数据。  

借助 Microsoft Intune，你可以使用以下方法在 Windows 10 设备上管理 BitLocker：

- **设备配置策略** - 创建设备配置文件以管理终结点保护时，某些内置策略选项在 Intune 中可用。 若要查找这些选项，请[创建用于终结点保护的设备配置文件](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings)，选择“Windows 10 及更高版本”作为“平台”，然后选择“Windows 加密”类别作为“设置”     。 

   可在此处了解可用选项和功能：[Windows 加密](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)。

- **安全基线** - [安全基线](security-baselines.md)是已知的设置和默认值组，相关安全团队建议借助它们来帮助保护 Windows 设备。 不同的基线源（如“MDM 安全基线”或“Microsoft Defender ATP 基线”）可以管理相同的设置以及彼此之间不同的设置   。 它们还可以管理使用设备配置策略进行管理的相同设置。 

除 Intune 外，还可以通过其他方式（如组策略）来管理 BitLocker 设置，或由设备用户进行手动设置。

无论设置如何应用于设备，BitLocker 策略都利用 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) 在设备上配置加密。 BitLocker CSP 内置于 Windows 中，当 Intune 将 BitLocker 策略部署到分配的设备时，设备上的 BitLocker CSP 将相应的值写入 Windows 注册表，以便策略中的设置生效。

若要了解有关 BitLocker 的详细信息，请参阅以下资源：

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 概述和要求常见问题解答](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

现在，你已大致了解这些策略的作用及其工作原理，下面介绍如何验证 BitLocker 设置是否已成功应用于 Windows 客户端。

## <a name="verify-the-source-of-bitlocker-settings"></a>验证 BitLocker 设置的源

调查 Windows 10 设备上的 BitLocker 问题时，重要的是首先确定问题是与 Intune 相关还是与 Windows 相关。 在知道可能的故障来源之后，你可以将故障排除工作集中到正确的位置，并在必要时从正确的团队获得支持。  

第一步，确定 Intune 策略是否已成功部署到目标设备。 在下面的示例中，你有一个用于部署 Windows 加密 (BitLocker) 设置的设备配置策略，如下所示：

![带有设置的 Windows 加密设备配置策略](./media/troubleshooting-bitlocker-policies/settings.png)

如何确认是否已将设置应用于目标设备？ 可通过下面几种方法执行此操作。

### <a name="device-configuration-policy-device-status"></a>设备配置策略设备状态  

使用设备配置策略配置 BitLocker 时，可在 Intune 门户中检查策略的状态。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备” > “配置文件”，然后选择包含 BitLocker 设置的配置文件   。

3. 选择要查看的配置文件后，选择“设备状态”  。 列出分配给配置文件的设备，“设备状态”列指示设备是否成功部署了配置文件  。

请记住，接收 BitLocker 策略的设备与完全加密的驱动器之间可能存在延迟。  

### <a name="use-control-panel-on-the-client"></a>在客户端上使用控制面板  

在启用了 BitLocker 并对驱动器进行加密的设备上，你可以从设备的控制面板查看 BitLocker 状态。 在设备上，打开“控制面板” > “系统和安全” > “BitLocker 驱动器加密”    。 显示确认，如下图所示。  

![BitLocker 已在“控制面板”中打开](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>使用命令提示符  

在启用了 BitLocker 并对驱动器进行加密的设备上，使用管理员凭据启动命令提示符，然后运行 `manage-bde -status`。 结果应与下面的示例类似：  
![状态命令的结果](./media/troubleshooting-bitlocker-policies/command.png)

在示例中：

- “BitLocker 保护”已“开启”  
- “加密百分比”为“100%”  
- “加密方法”为“XTS-AES 256”  

还可以通过运行以下命令来检查“密钥保护程序”  ：

```cmd
Manage-bde -protectors -get c:
```

或者使用 PowerShell：

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>查看设备注册表项配置

BitLocker 策略成功部署到设备后，在设备上查看以下注册表项，可以在其中查看 BitLocker 设置的配置：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker  。 下面是一个示例：

![BitLocker 注册表项](./media/troubleshooting-bitlocker-policies/registry.png)

这些值由 BitLocker CSP 配置。 验证密钥的值是否与 Intune Windows 加密策略的源中指定的设置相匹配。 有关上述每个设置的详细信息，请参阅 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)。

> [!NOTE]
> Windows 事件查看器还将包含与 Bitlocker 相关的各种信息。 其内容过多，无法在此处列出，但搜索 **Bitlocker API** 将为你提供很多有用的信息。

### <a name="check-the-mdm-diagnostics-report"></a>检查 MDM 诊断报告

在启用了 BitLocker 的设备上，可以从目标设备生成并查看 MDM 诊断报告，以确认 BitLocker 策略是否存在。 如果在报告中可以看到策略设置，则表明策略已成功部署。 以下链接中的“Microsoft 帮助”视频介绍了如何从 Windows 设备捕获 MDM 诊断报告  。

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

分析 MDM 诊断报告时，其内容最初可能有些令人困惑。 下面的示例演示如何将报告中的内容与策略中的设置相关联：

![MDM 诊断报告示例](./media/troubleshooting-bitlocker-policies/report.png)

输出结果显示与 BitLocker 策略中的值对应的值：

![输出结果显示值 ](./media/troubleshooting-bitlocker-policies/output.png)

MDM 诊断输出结果：

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

可参考 [BitLocker CSP 文档](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)来了解每个值的含义。 对于此示例，下图中共享了一个代码片段。

![值的用途](./media/troubleshooting-bitlocker-policies/shared-example.png)

同样，你可以查看所有值并通过 BitLocker CSP 链接验证它们。

> [!TIP]
> MDM 诊断报告的主要用途是帮助 Microsoft 支持部门对问题进行故障排除。 如果你打开了 Intune 支持案例，且问题涉及 Windows 客户端，则最好收集此报告并将其包含在你的支持请求中。

## <a name="troubleshooting-bitlocker-policy"></a>BitLocker 策略疑难解答

现在，你应该已经懂得如何确认 Intune 是否已成功部署 BitLocker 策略，策略成功部署后会将 BitLocker 的配置移交给 Windows 中的 BitLocker CSP。

**策略无法访问设备** - 如果你的 Intune 策略不在任何容量中：

- **设备是否已在 Microsoft Intune 中正确注册？** 如果没有，则需要先解决该问题，然后才能对特定于策略的任何内容进行故障排除。 可在[此处](../enrollment/troubleshoot-windows-enrollment-errors.md)找到有关 Windows 注册问题的疑难解答帮助。

- **设备上是否有活动的网络连接？** 如果设备处于飞行模式、关闭状态，或位于无服务的位置，则在恢复网络连接之前，不会传递或应用此策略。

- **BitLocker 策略是否部署到正确的用户或设备组？** 检查正确的用户或设备是否是目标组的成员。

**存在策略，但未成功配置所有设置** - Intune 策略到达设备，但并非所有配置都已设置：

- **是整个策略部署失败，还是仅某些设置不适用？** 如果你发现只有某些策略设置不适用，请查看以下注意事项：

  1. **并非所有 BitLocker 设置在所有 Windows 版本上都受支持**。
     策略以单个单元的形式向下移动到设备，因此，如果某些设置适用而其他设置不适用，则你可以确信策略本身已被接收。 在这种情况下，可能设备上的 Windows 版本不支持有问题的设置。 有关每项设置的版本要求的详细信息，请参阅 Windows 文档中的 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)。

  2. **并非所有硬件都支持 BitLocker**。
     即使你使用适当版本的 Windows，基础设备硬件也有可能不符合 BitLocker 加密的要求。 可以在 Windows 文档中找到[BitLocker 的系统要求](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)，但要检查的主要问题是设备是否具有兼容的 TPM 芯片（1.2 或更高版本）和与受信任的计算组 (TCG) 兼容的 BIOS 或 UEFI 固件。

**示例调查**

- 将 BitLocker 策略部署到 Windows 10 设备，且“加密设备”设置在门户中显示“错误”状态   。

- 顾名思义，管理员可使用“BitLocker”>“设备加密”来要求开启加密  。 使用前面所述的故障排除提示，首先要检查 MDM 诊断报告。 此报告确认设备上部署了正确的策略：

  ![报告确认在设备上部署了正确的策略](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- 你还可以在注册表中验证是否成功：

  ![RequiredDeviceEncryption 注册表值显示 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- 接下来，使用 PowerShell 检查 TPM 的状态，并发现 TPM 在设备上不可用：

  ![使用 PowerShell 检查 TPM 状态](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- 由于 BitLocker 依赖于 TPM，因此你可以得出的结论是，BitLocker 出现故障并非由于 Intune 或策略问题，而是由于设备本身没有 TPM 芯片或在 BIOS 中禁用了 TPM。

  此外温馨提示，可在“应用程序和服务日志” > “Microsoft” > “Windows” > “BitLocker API”下的 Windows 事件查看器中确认相同结论     。 在“BitLocker API”事件日志中，可以找到事件 ID 853，表示 TPM 不可用  ：

  ![事件 ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > 还可以通过在设备上运行“tpm.msc”来检查 TPM 状态  。

## <a name="summary"></a>“摘要”

对 Intune 的 BitLocker 策略问题进行故障排除时，如果可确认策略已到达目标设备，则可放心推断问题与 Intune 没有直接关系。 该问题更可能是 Windows OS 或硬件问题。 在这种情况下，请开始查看其他区域（如 TPM 配置或 UEFI 以及安全启动）。

## <a name="next-steps"></a>后续步骤  

下面提供了更多资源，可帮助你使用 BitLocker：

- [BitLocker 产品文档](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 系统要求](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker 常见问题解答](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker CSP 文档](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Intune Windows 加密策略设置](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [使用 AAD/MDM 的独立于硬件的自动 BitLocker 加密](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [自动驾驶设备上 BitLocker 加密的 CSP 策略](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [演练通过 Intune 创建和部署 BitLocker 策略](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)