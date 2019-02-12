---
title: Microsoft Intune 中的设备配置文件疑难解答 - Azure | Microsoft Docs
description: 设备配置文件的常见问题包括：配置文件更改未应用到某些用户或设备、将新策略推送到设备需要多长时间、存在多个策略时会应用哪些具体设置、删除配置文件时发生的情况，以及在 Azure 门户中使用 Microsoft InTune 时遇到的更多其他问题
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 1/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 528e26ddca1b3327fb0afa2f5cff6f2dbdca1660
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846479"
---
# <a name="common-issues-and-resolutions-with-device-profiles-in-microsoft-intune"></a>Microsoft Intune 中设备配置文件的常见问题和解决方法

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用 Intune 设备配置文件解决常见问题。

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>为什么在对现有 Wi-Fi 配置文件进行密码或通行短语更改时，用户无法获取新的配置文件？ 
创建企业 Wi-Fi 配置文件、将配置文件部署到组、更改密码并保存配置文件。 配置文件发生更改时，某些用户可能无法获取新的配置文件。

若要缓解此问题，请设置来宾 Wi-Fi。 如果公司 Wi-fi 失败，用户可以连接到来宾 Wi-Fi。 请务必启用任何自动连接设置。 将来宾 Wi-Fi 配置文件部署到所有用户。

一些其他建议：  

- 由于所连接到的 Wi-Fi 网络使用密码或通行短语，因此，请确保你能直接连接到 Wi-Fi 路由器。 可使用 iOS 设备进行测试。
- 在成功连接到 Wi-Fi 终结点（Wi-Fi 路由器）后，请注意所使用的 SSID 和凭据（此值为密码或通行短语）。
- 在“预共享密钥”字段中输入 SSID 和凭据（密码或通行短语）。 
- 部署到具有有限用户数的测试组，最好仅限 IT 团队。 
- 将 iOS 设备同步到 Intune。 如果尚未注册，请先注册。 
- 再次测试连接到相同的 Wi-Fi 终结点（如先前步骤所述）。
- 推广至更大的组，并最终遍及组织中的所有预期用户。 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>策略或应用分配完成后，移动设备需要多长时间获取？
策略或应用分配完成后，Intune 会立即开始通知设备签入到 Intune 服务。 通知通常在五分钟内完成。

如果首次发出通知后设备未签入以获取策略，则 Intune 还会尝试通知 3 次。 如果设备脱机（例如设备已关机或未连接到网络），则可能无法收到通知。 在这种情况下，设备将按照以下设置在下次计划签入到 Intune 服务时获取策略：

- iOS 和 macOS：每 6 小时一次
- Android：每 8 小时一次
- Windows Phone：每 8 小时一次
- 注册为设备的 Windows 8.1 和 Windows 10 电脑：每 8 小时一次

如果设备是最近注册的，则签入会更加频繁，具体如下：

- iOS 和 macOS：6 小时内每 15 分钟一次，之后每 6 小时一次
- Android：15 分钟内每 3 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次
- Windows Phone：15 分钟内每 5 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次
- 注册为设备的 Windows 电脑：30 分钟内每 3 分钟一次，之后每 8 小时一次

若要随时立即检查策略，用户可以打开公司门户应用并同步设备。

对于没有用户关联的设备，注册后的即时同步频率不尽相同，可能为几小时到一天（或者更长）。 Intune 将以不同的时间间隔发送请求以将设备签入该服务。 但仍取决于要签入的设备。 初始注册后，设备完成签入所需的时间是无法预测的，具体要取决于设备注册的类型以及分配到设备的策略和配置文件。 但是，完成设备的注册并应用所有初始策略后，设备通常约每 6 小时检查一次新策略。

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>哪些操作会导致 Intune 立即向设备发送通知？
设备收到告知其签入的通知时或者在定期的计划签入期间，设备会签入到 Intune。 当针对某个设备或用户执行某个操作时，例如擦除、锁定、密码重置、应用分配、配置文件分配或策略分配，Intune 会立即开始通知设备签入到 Intune 服务以接收这些更新。

其他变更（如在公司门户中修订合同信息）不会导致立即向设备发送通知。

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>如果多个策略被分配到同一用户或设备，如何知道会应用哪些设置？
如果向同一用户或设备分配两个或多个策略，则会在单个设置级别上决定具体应用哪些设置：

- 合规性策略设置始终优先于配置策略设置

- 如果某个符合性策略针对不同符合性策略中的相同设置进行评估，则应用限制最严格的符合性策略设置。

- 如果配置策略设置与其他配置策略设置冲突，此冲突会显示在 Azure 门户中。 在此方案中，手动解决这些冲突。

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>应用保护策略互相冲突时会发生什么情况？ 哪一种策略将应用于应用？
除数字输入字段（如重置之前尝试 PIN）外，冲突值是应用保护策略中限制最严格的设置。 数字输入字段将设定为与你使用建议的设置选项在控制台中创建 MAM 策略时一样的值。

两个配置文件设置相同时即会发生冲突。 例如，除复制/粘贴设置外，你配置了两个完全相同的 MAM 策略。 在此方案中，复制/粘贴设置将设定为限制最严格的值，但其余设置将应用配置的值。

如果一个配置文件已分配到应用且生效，然后分配了第二个配置文件，则第一个配置文件的优先级更高并且会继续应用该配置文件，而第二个配置文件将显示冲突。 如果两个配置文件同时应用，即没有优先的配置文件，则两个都会显示冲突。 任何冲突的设置都将设定为限制最严格的值。

## <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS 自定义策略冲突时会发生什么情况？
Intune 不会评估 Apple 配置文件或自定义开放移动联盟统一资源标识符 (OMA-URI) URI 配置文件的负载。 它只作为传送机制。

分配自定义配置文件时，请确保配置的设置不会与符合性、配置或其他自定义策略冲突。 如果自定义配置文件与其设置发生冲突，则会随机应用这些设置。

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>当配置文件被删除，或不再适用时，会发生什么情况？
删除某个配置文件，或从具有配置文件的组中删除设备时，该配置文件和设置会根据下表从设备中删除：

- Wi-Fi、VPN、证书和电子邮件配置文件：这些配置文件会从所有支持的已注册设备中删除。
- 所有其他配置文件类型：  

  - **Windows 和 Android 设备**：不会从设备删除设置
  - **Windows Phone 8.1 设备**：删除了下列设置：  
  
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
    - 允许擦除
    - 允许蓝牙
    - 允许 NFC
    - 允许 Wi-Fi

  - **iOS**：删除所有设置，但不包括：
  
    - 允许语音漫游
    - 允许数据漫游
    - 允许漫游时自动同步

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>我更改了设备限制配置文件，但更改尚未生效
Windows Phone 设备不允许使用 MDM 或 EAS 设置安全策略后降低其安全性。 例如，将“最小字符密码数”设置为 8，然后尝试将其减少到 4。 已向设备应用更严格的配置文件。

如果要将配置文件更改为安全级别较低的值，则需要重置安全策略。 例如，在 Windows 8.1 桌面上，从右轻扫，然后选择“设置” > “控制面板”。 选择“用户帐户”小程序。 左侧导航菜单有一个“重置安全策略”链接（接近底部）。 选中它，然后选择“重置策略”。

对于其他 MDM 设备（例如 Android、Windows Phone 8.1 及更高版本以及 iOS 和 Windows 10），可能需要将其停用并重新注册回服务，这样才能应用限制较少的配置文件。

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Windows 10 配置文件中的某些设置返回“不适用”
Windows 10 设备上的某些设置可能显示为“不适用”。 发生这种情况时，设备上运行的 Windows 的版本或版次不支持该特定设置。 出现此消息的可能原因如下：

- 设置仅适用于较新版本的 Windows，而不适用于设备上的当前操作系统 (OS) 版本。
- 设置仅适用于特定 Windows 版本或特定 SKU，如家庭版、专业版、企业版和教育版。

若要了解不同设置的版本和 SKU 要求的详细信息，请参阅[配置服务提供程序 (CSP) 参考](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)。

## <a name="next-steps"></a>后续步骤
需要更多帮助？ 请参阅[如何获取对 Microsoft Intune 的支持](get-support.md)。
