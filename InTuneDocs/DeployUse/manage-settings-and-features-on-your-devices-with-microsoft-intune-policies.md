---
# required metadata

title: 使用策略管理设备上的设置和功能 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 06/14/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: heenamac
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 策略管理设备上的设置和功能
Microsoft Intune **策略**是控制移动设备和计算机上的功能的设置的组合。 你使用包含建议设置或自定义设置的模板创建策略，然后将策略部署到设备或用户组。

## 你可以使用哪些类型的策略？

Intune 策略划分为以下类别。 你使用的类别会影响你创建和部署策略的方式。


- **配置策略：**通常用于管理设备的安全设置和功能。 通过本主题中的信息可了解如何创建和部署这些策略，以及如何查看可用的设置。
- **设备合规性策略：**定义设备必须遵从的规则和设置，以便将设备视为符合条件性访问策略。 你也可使用合规性策略来监视和修复与条件性访问无关的设备的合规性。
有关详细信息，请参阅 [Microsoft Intune 中的设备合规性策略](introduction-to-device-compliance-policies-in-microsoft-intune.md)。
- **条件性访问策略：**这些策略可根据你指定的条件帮助确保电子邮件和其他服务的安全。
有关详细信息，请参阅[使用 Microsoft Intune 限制对电子邮件和 O365 服务的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。
- **企业设备注册策略：**有关企业设备注册策略的信息，请参阅[使用 Microsoft Intune 设置 iOS 和 Mac 管理](set-up-ios-and-mac-management-with-microsoft-intune.md)。
- **资源访问策略：**这些策略一同协作，帮助你的用户无论在何处都可以获取成功完成其工作所需的文件和资源的访问权限。
有关详细信息，请参阅[使用 Microsoft Intune 启用对公司资源的访问](enable-access-to-company-resources-with-microsoft-intune.md)。


有关 Intune 策略的完整列表，请参阅 [Microsoft Intune 策略参考](microsoft-intune-policy-reference.md)。




## 创建配置策略

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择“策略”&gt;“配置策略”&gt;“添加”。

2.  选择你想要的策略，然后选择使用策略的推荐设置（如果可用；可在稍后更改这些设置），或者使用自己的设置创建自定义策略。

    > [!TIP]要帮助选择正确的策略，请参阅 [Microsoft Intune 策略参考](microsoft-intune-policy-reference.md)。

3.  准备好后，选择“创建策略”。

4.  在“创建策略”  屏幕上，配置策略名称和可选描述。

5.  配置必要的策略设置，然后选择“保存策略”。

    如果你需要有关任何策略设置的帮助，请从以下列表中选择策略类型：

    - [适用于 iOS 设备的设置](ios-policy-settings-in-microsoft-intune.md)
    - [适用于 Android 设备的设置](android-policy-settings-in-microsoft-intune.md)
    - [适用于 Windows 8 和 Windows 8.1 设备的设置](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [适用于 Windows Phone 8.1 设备的设置](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [适用于 Windows 10 桌面和移动版设备的设置](windows-10-policy-settings-in-microsoft-intune.md)
    - [适用于 Windows Team 设备的设置](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [适用于 Windows 版本升级的设置](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Mac OS X 设备的设置](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [适用于 Exchange ActiveSync 的设置](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [适用于条款和条件策略的设置](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [适用于移动设备的常规设置（旧功能）](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  在确认对话框中，选择“是”以立即部署策略，或选择“否”以创建而不部署策略。

你可以通过浏览“策略”  工作区中的每个策略类型部分来查看和编辑新策略。

在创建使用建议设置的策略时，新策略的名称是模板名称、日期和时间的组合。 当你编辑该策略时，名称将更新为包含编辑时的时间和日期。

现在你已经创建一个策略，通常需要将其部署到一个或多个用户或者设备组。

> [!TIP]
> 你不会部署所有策略类型。 例如，不部署移动应用程序管理策略。 相反，此策略类型将与应用关联，之后你就可部署。

## 部署配置策略

1.  在“策略”工作区中，选择想要部署的策略，然后选择“管理部署”。

2.  在“管理部署”  对话框中：

    -   **部署策略** - 选择要向其部署策略的一个组或多个组，然后选择**添加**&gt;**确定**。

    -   **关闭对话框而不部署** — 选择**取消**。

如果你选择的是已部署的策略，则可以在策略列表的下半部分查看有关部署的详细信息。

## 管理策略

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择“策略”，然后浏览到并选择你想要管理的策略。

2.  选择下列其中一项操作：

- **编辑** - 打开所选策略的属性以允许你进行更改。
- **删除** - 删除所选的策略。<br>在删除策略时，会将该策略从它已部署到的所有组中删除。
- **管理部署** - 选中要对其部署策略的组并选择“添加”。


## 有关 Intune 策略的常见问题

### 策略或应用部署完成后，移动设备需要多长时间获取？
策略或应用部署完成后，Intune 会立即开始尝试通知设备其应签入到 Intune 服务。 这通常可在 5 分钟内完成。

如果首次发出通知后设备未签入以获取策略，则系统还会尝试通知 3 次。  如果设备脱机（例如已关机或未连接至网络），则可能收不到通知。

在这种情况下，设备将按照以下设置在下次计划的签入到 Intune 服务时获取策略：

- iOS - 每 6 小时
- Android - 每 8 小时
- Windows Phone - 每 8 小时
- 已注册的 Windows RT 设备 - 每 24 小时
- 注册为设备的 Windows 8.1 和 Windows 10 电脑 - 每 8 小时

如果设备刚进行注册，则签入会更频繁，具体如下：

- iOS - 6 小时内每 15 分钟一次，之后每 6 小时一次
- Android - 15 分钟内每 3 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次
- Windows Phone - 15 分钟内每 5 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次
- 注册为设备的 Windows PC - 30 分钟内每 3 分钟一次，之后每 24 小时一次

用户还可以启动公司门户应用并同步设备，立即随时检查策略。

### 哪些操作会导致 Intune 立即发送通知到设备？
当设备收到告知它们签入的通知或者在定期的计划签入期间（如上表所示），设备会签入到 Intune。  当你针对某个设备或用户执行特定操作时，例如擦除、锁定、密码重置、应用部署、配置文件部署（WiFi、VPN、电子邮件等）或策略部署，Intune 会立即开始尝试通知设备其应签入到 Intune 服务以接收这些更新。

其他变更（如在公司门户中修订合同信息）不会导致立即向设备发送通知。

> [!TIP]
> 将包含设置的策略部署到 Android 设备时，系统将提示用户他们需要采取操作以遵循策略。 在用户采取此操作或设备重启前，新的策略设置将不会生效。

### 如果多个策略部署到同一用户或设备，如何知道会应用哪些设置？
请务必知道，当两个或多个策略部署到同一用户或设备时，将在单个设置级别上评估具体应用哪个设置。

-   合规性策略设置始终优先于配置策略设置

-   如果针对不同合规性策略中的相同设置进行评估，则应用限制最严格的合规性策略设置

-   如果针对不同配置策略中的相同设置进行评估，则应用限制最严格的配置策略设置

### 移动应用程序管理 (MAM) 策略相互冲突时会发生什么情况？ 哪一种策略将应用于应用？
除数字输入字段（如重置之前尝试 PIN）外，冲突值是移动应用程序管理策略中限制最严格的设置。  数字输入字段将设定为你使用建议的设置选项在控制台中创建 MAM 策略时一样的值。

两个策略设置相同时即会发生冲突。  例如，除复制/粘贴设置外，你配置了两个完全相同的 MAM 策略。  在此方案中，复制/粘贴设置将设定为限制最严格的值，但其余设置将应用配置的值。

如果一个策略部署到应用且生效，然后部署第二个策略，则第一个策略的优先级更高并且会继续应用该策略，而第二个策略将显示冲突。 但是，如果两个策略同时应用，即它们的优先级一样，则两个都会显示冲突，任何冲突的设置都将设定为限制最严格的值。

### iOS 自定义策略冲突时会发生什么情况？
Intune 不会评估 Apple 配置文件或自定义 OMA URI 策略的负载，它只作为传送机制。

因此，在部署自定义策略时，请确保配置的设置不会与合规性、配置或其他自定义策略冲突。 如果自定义策略与设置冲突，则应用设置的顺序是随机的。

### 策略遭到删除或不再适用时，会发生什么情况？
当您删除某个策略时，或从策略部署到的组中删除设备时，策略和设置将会根据下表从设备中删除：

#### “注册的设备”

- Wi-Fi、VPN、证书和电子邮件配置文件 - 这些配置文件会从所有支持的已注册设备中删除。
- 所有其他策略类型
    - **Windows 和 Android 设备** - 设置不会从设备中删除。
    - **Windows Phone 8.1 设备** - 删除以下设置：
        - 需要密码才可解锁移动设备
        - 允许简单密码
        - 最短密码长度
        - 所需的密码类型
        - 密码过期（天数）
        - 记住密码历史记录
        - 擦除设备前允许的重复登录失败次数 - 需要提供密码之前处于非活动状态的分钟数 - 所需密码类型 - 最小字符集数 - 允许照相机 - 需要对移动设备加密 - 允许可移动存储 - 允许 Web 浏览器 - 允许应用商店 - 允许抓屏 - 允许地理位置 - 允许 Microsoft 帐户 - 允许复制和粘贴 - 允许 Wi-Fi tethering - 允许自动连接到免费 Wi-Fi 热点 - 允许 Wi-Fi 热点报告 - 允许恢复出厂设置 - 允许蓝牙 - 允许 NFC - 允许 Wi-Fi
    
    - **iOS** - 删除所有设置，但不包括：
        - 允许语音漫游
        - 允许数据漫游
        - 允许漫游时自动同步

#### 运行 Intune 客户端软件的 Windows PC

- **Endpoint Protection 设置** – 设置还原为其建议值。 唯一的例外是默认值为“否”  的“加入 Microsoft Active Protection Service” 设置。 有关详细信息，请参阅[使用 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)。
- **软件更新设置** – 设置重置为操作系统的默认状态。 有关详细信息，请参阅[在 Microsoft Intune 中利用软件更新使 Windows 电脑保持最新版本](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)。
- **Microsoft Intune 中心设置** - 从计算机中删除策略所配置的任何支持联系人信息。
- **Windows 防火墙设置** - 设置重置为计算机操作系统的默认值。 有关详细信息，请参阅[使用 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)。


### 如何刷新设备的策略以确保是最新的策略（仅适用于运行 Intune 客户端软件的 Windows PC）

1.  在任一设备组中，选择要在其上刷新策略的设备，然后选择“远程任务”&gt;“刷新策略”。
2.  选择 Intune 管理控制台右下角的“远程任务”可检查任务状态。

### 在哪里可以找到有关排查策略问题的帮助？

请参阅 [Troubleshoot policies in Microsoft Intune](../Troubleshoot/troubleshoot-policies-in-microsoft-intune)（Microsoft Intune 中的故障排除政策）。


<!--HONumber=Jun16_HO3-->


