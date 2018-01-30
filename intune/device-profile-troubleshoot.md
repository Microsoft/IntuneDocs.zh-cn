---
title: "Microsoft Intune 中的设备配置文件疑难解答"
titlesuffix: Azure portal
description: "如果遇到困扰，请使用此主题来帮助解决 Intune 设备配置文件相关的问题。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 1/17/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6424be562401c672966c0f7f3fbe145c19182299
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="troubleshooting-device-profiles-in-microsoft-intune"></a>Microsoft Intune 中的设备配置文件疑难解答


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题中的信息可用于帮助解决与 Intune 设备配置文件相关的常见问题。

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>为什么在对现有 Wi-Fi 配置文件进行密码或通行短语更改时，用户无法获取新的配置文件？ 
当创建企业 Wi-Fi 配置文件、将配置文件部署到组、更改密码并保存配置文件时，你会希望用户获取该新配置文件。 但有时用户可能无法获取新的配置文件。 

要缓解此问题，请确保已设置来宾 Wi-Fi，以便当企业 Wi-Fi 故障时，用户能退回来宾 Wi-Fi。 需要启用自动连接设置。 需向所有用户部署此来宾 Wi-Fi 配置文件。

还有一些其他最佳做法可供借鉴：
- 由于所连接到的 Wi-Fi 网络需要密码或通行短语，因此，请确保你能直接连接到 Wi-Fi 路由器。 可使用 iOS 设备进行测试。
- 在成功连接到 Wi-Fi 终结点（Wi-Fi 路由器）后，请注意 SSID 和所使用的凭据（它是密码或通行短语）。
- 在“预共享密钥”字段中输入 SSID 和凭据（密码或通行短语）。 
- 部署到具有有限用户数量的测试组，最好仅限 IT 团队。 
- 将 iOS 设备同步到 Intune。 如果尚未注册，请先注册。 
- 再次测试连接到相同的 Wi-Fi 终结点（如先前步骤所述）。
- 推广至更大的组，并最终遍及组织中的所有预期用户。 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>策略或应用分配完成后，移动设备需要多长时间获取？
策略或应用分配完成后，Intune 会立即开始尝试通知设备其应签入到 Intune 服务。 这通常可在五分钟内完成。

如果首次发出通知后设备未签入以获取策略，则 Intune 还会尝试通知 3 次。 如果设备脱机（例如设备已关机或未连接至网络），则可能无法收到通知。 在这种情况下，设备将按照以下设置在下次计划签入到 Intune 服务时获取策略：

- iOS 和 macOS：每 6 小时。
- Android：每 8 小时。
- Windows Phone：每 8 小时。
- 注册为设备的 Windows 8.1 和 Windows 10 电脑：每 8 小时。

如果设备刚进行注册，则签入会更频繁，具体如下：

- iOS 和 macOS：6 小时内每 15 分钟一次，之后每 6 小时一次。
- Android：15 分钟内每 3 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次。
- Windows Phone：15 分钟内每 5 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次。
- 注册为设备的 Windows 电脑：30 分钟内每 3 分钟一次，之后每 8 小时一次。

用户还可以打开公司门户应用并同步设备以立即随时检查策略。

对于没有用户关联的设备，注册后的即时同步频率不尽相同，可能为几小时到一天（或者更长）。 Intune 将以不同的时间间隔发送请求以将设备签入该服务。 但实际上仍需设备执行此操作。 初始注册后，无法预测设备完成该签入所需的时间，具体取决于设备注册的类型以及设备分配到的策略和配置文件。 但是，当已注册设备并应用所有初始策略后，设备应大约每 6 小时检查一次新策略。

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>哪些操作会导致 Intune 立即向设备发送通知？
当设备收到告知它们签入的通知时或者在定期的计划签入期间，设备会签入到 Intune。 当你针对某个设备或用户执行特定操作时，例如擦除、锁定、密码重置、应用分配、配置文件分配（Wi-Fi、VPN、电子邮件等）或策略分配，Intune 会立即开始尝试通知设备其应签入到 Intune 服务以接收这些更新。

其他变更（如在公司门户中修订合同信息）不会导致立即向设备发送通知。

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>如果多个策略被分配到同一用户或设备，如何知道会应用哪些设置？
当两个或多个策略被分配到同一用户或设备时，将在单个设置级别上评估具体应用哪个设置：

-   合规性策略设置始终优先于配置策略设置。

-   如果针对不同合规性策略中的相同设置进行评估，则应用限制最严格的合规性策略设置。

-   如果配置策略设置与其他配置策略设置冲突，此冲突会显示在 Azure 门户中。 必须手动解决此类冲突。

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>应用保护策略互相冲突时会发生什么情况？ 哪一种策略将应用于应用？
除数字输入字段（如重置之前尝试 PIN）外，冲突值是应用保护策略中限制最严格的设置。 数字输入字段将设定为与你使用建议的设置选项在控制台中创建 MAM 策略时一样的值。

两个配置文件设置相同时即会发生冲突。 例如，除复制/粘贴设置外，你配置了两个完全相同的 MAM 策略。 在此方案中，复制/粘贴设置将设定为限制最严格的值，但其余设置将应用配置的值。

如果一个配置文件已分配到应用且生效，然后分配了第二个配置文件，则第一个配置文件的优先级更高并且会继续应用该配置文件，而第二个配置文件将显示冲突。 如果两个配置文件同时应用，即没有优先的配置文件，则两个都会显示冲突。 任何冲突的设置都将设定为限制最严格的值。

## <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS 自定义策略冲突时会发生什么情况？
Intune 不会评估 Apple 配置文件或自定义开放移动联盟统一资源标识符 (OMA-URI) URI 配置文件的负载。 它只作为传送机制。

分配自定义配置文件时，请确保配置的设置不会与符合性、配置或其他自定义策略冲突。 如果自定义配置文件与设置冲突，则应用设置的顺序是随机的。

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>当配置文件被删除，或不再适用时，会发生什么情况？
当你删除某个配置文件，或从分配有配置文件的组中删除设备时，该配置文件和设置将会根据下表从设备中删除。

### <a name="enrolled-devices"></a>注册的设备

- Wi-Fi、VPN、证书和电子邮件配置文件：这些配置文件会从所有支持的已注册设备中删除。
- 所有其他配置文件类型：
    - **Windows 和 Android 设备**：设置不会从设备中删除。
    - **Windows Phone 8.1 设备**：会删除以下设置：
        - 需要密码才可解锁移动设备
        - 允许简单密码
        - 最短密码长度
        - 所需的密码类型
        - 密码过期（天数）
        - 记住密码历史记录
        - 擦除设备前允许的重复登录失败次数
        - 需要提供密码之前处于非活动状态的分钟数
        - 所需密码类型 - 最小字符集数
        - 允许相机
        - 需要对移动设备加密
        - 允许可移动存储
        - 允许 Web 浏览器
        - 允许应用程序商店
        - 允许屏幕捕获
        - 允许地理位置
        - 支持 Microsoft 帐户
        - 允许复制和粘贴
        - 允许 Wi-Fi tethering
        - 允许自动连接到免费 Wi-Fi 热点
        - 允许 Wi-Fi 热点报告
        - 允许恢复出厂设置
        - 允许蓝牙
        - 允许 NFC
        - 允许 Wi-Fi

    - **iOS**：删除所有设置，但不包括：
        - 允许语音漫游
        - 允许数据漫游
        - 允许漫游时自动同步

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>我更改了设备限制配置文件，但更改尚未生效
Windows Phone 设备不允许通过 MDM 或 EAS 设置安全策略后降低其安全性。 例如，将“最小字符密码数”设置为 8，然后尝试将其减少到 4。 已向设备应用更严格的配置文件。

如果要将配置文件更改为安全级别较低的值，可能需要重置安全策略，具体视设备平台而定。
例如，在 Windows 中，在桌面上从右轻扫打开“超级按钮”栏并选择“设置”&gt;“控制面板”。 选择“用户帐户”小程序。
左侧导航菜单底部有一个“重置安全策略”链接。 选中它，然后选择“重置策略”按钮。
对于其他 MDM 设备（例如 Android、Windows Phone 8.1 及更高版本以及 iOS），可能需要将其停用并重新注册回服务，这样才能应用限制较少的配置文件。


### <a name="next-steps"></a>后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](get-support.md)中所述。