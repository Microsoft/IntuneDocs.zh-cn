---
title: Intune 的设备策略、配置文件和问答 - Azure | Microsoft Docs
description: 阅读可在 Microsoft Intune 中使用的不同策略和配置文件，包括用于配置设备、获取对公司资源的访问权限、启用条件访问和注册公司设备的策略。 并查看常见问题的答案。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8a7a7405fe40d3568e736c244d9fcb308350709
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317973"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>使用 Intune 策略管理设备上的设置和功能

Microsoft Intune *策略*是控制移动设备和计算机上的功能的设置的组合。 使用包含建议或自定义设置的模板来创建策略。 然后，将这些策略部署到设备或用户组。

## <a name="types-of-policies"></a>策略类型

Intune 策略划分为以下类别。 使用的类别会影响创建和部署策略的方式。

- **配置策略**：通常用于管理设备上的安全设置和功能，包括对公司资源的访问权限。 从 [Intune 设备配置文件](device-profiles.md)开始操作。
- **设备符合性策略**：定义设备必须遵从的规则和设置，以便将设备视为符合条件访问策略。 你也可使用合规性策略来监视和修复与条件性访问无关的设备的合规性。 [设备符合性策略](device-compliance-get-started.md)入门。
- **条件访问策略**：根据你输入的条件帮助确保电子邮件和其他服务的安全。 [什么是条件访问](conditional-access.md)和[使用条件访问的常见方式](conditional-access-intune-common-ways-use.md)都是不错的入门资源。
- **企业设备注册策略**：有关企业设备注册策略的信息，请参阅[注册 iOS 设备](ios-enroll.md)。

## <a name="frequently-asked-questions-about-intune-policies"></a>有关 Intune 策略的常见问题

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>策略或应用部署完成后，移动设备需要多长时间获取？
策略或应用部署完成后，Intune 会立即开始通知设备签入到 Intune 服务。 此步骤通常可在五分钟内完成。

如果首次发出通知后设备未签入以获取策略，则 Intune 还会尝试通知 3 次。  如果设备脱机（例如已关机或未连接至网络），则可能无法收到通知。 在这种情况下，设备将按照以下设置在下次计划签入到 Intune 服务时获取策略：

| 平台 | 签入频率 |
| --- | --- |
| iOS | 每 6 小时一次 | 
| Mac OS X | 每 6 小时一次 |
| Android | 每 8 小时一次 | 
| Windows Phone | 每 8 小时一次 | 
| Windows 8.1  | 每 8 小时一次 |  
| 注册为设备的 Windows 10 PC | 每 8 小时一次 | 

如果设备是最近注册的，则签入会更加频繁，具体如下：

| 平台 | 频率 |
| --- | --- |
| iOS | 6 小时内每 15 分钟一次，之后每 6 小时一次 |  
| Mac OS X | 6 小时内每 15 分钟一次，之后每 6 小时一次 | 
| Android | 15 分钟内每 3 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次 | 
| Windows Phone | 15 分钟内每 5 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次 | 
| 注册为设备的 Windows PC | 30 分钟内每 3 分钟一次，之后每 8 小时一次 | 

用户还可以打开公司门户应用并同步设备以立即随时检查策略。

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>哪些操作会导致 Intune 立即向设备发送通知？
当设备收到告知它们签入的通知时或者在定期的计划签入期间，设备会签入到 Intune。  当你针对某个设备或用户执行操作时，例如擦除、锁定、密码重置、应用部署、配置文件部署（Wi-Fi、VPN、电子邮件）或策略部署，Intune 会立即尝试通知设备签入到 Intune 服务。

其他变更（如在公司门户中修订合同信息）不会导致立即向设备发送通知。

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>如果多个策略被部署到同一用户或设备，如何知道会应用哪些设置？
当两个或多个策略被部署到同一用户或设备时，将在单个设置级别上评估应用的设置：

- 合规性策略设置始终优先于配置策略设置。

- 如果针对不同符合性策略中的相同设置进行评估，则应用限制最严格的符合性策略设置。

- 如果配置策略设置与其他配置策略设置冲突，此冲突会显示在 Intune 中。 手动解决这些冲突。

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>移动应用管理策略相互冲突时会发生什么情况？ 哪种适用于应用？
除数字输入字段（如重置之前尝试 PIN）外，冲突值是 MAM 策略中限制最严格的设置。  数字输入字段将设定为与你使用建议的设置选项在控制台中创建 MAM 策略时一样的值。

两个策略设置相同时即会发生冲突。  例如，除复制/粘贴设置外，你配置了两个完全相同的 MAM 策略。  在此方案中，复制/粘贴设置将设定为限制最严格的值，但其余设置将应用配置的值。

如果一个策略部署到应用且生效，然后部署第二个策略，则第一个策略的优先级更高并且会继续应用该策略。 而第二个策略将显示冲突。 如果两个策略同时应用，即它们的优先级一样，则两个都会显示冲突。 任何冲突的设置都将设定为限制最严格的值。

### <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS 自定义策略冲突时会发生什么情况？
Intune 不会评估 Apple 配置文件或自定义开放移动联盟统一资源标识符 (OMA-URI) 策略的负载。 它只作为传送机制。

部署自定义策略时，请确认配置的设置不会与符合性、配置或其他自定义策略冲突。 如果自定义策略与设置冲突，则应用设置的顺序是随机的。

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>当策略被删除，或不再适用时，会发生什么情况？
如果删除某个策略，或从包含已部署策略的组中删除设备，则将根据下表从设备中删除策略和设置。

#### <a name="enrolled-devices"></a>注册的设备

- Wi-Fi、VPN、证书和电子邮件配置文件：这些配置文件会从所有支持的已注册设备中删除。
- 所有其他策略类型：
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
    - 允许擦除
    - 允许蓝牙
    - 允许 NFC
    - 允许 Wi-Fi

  - **iOS**：删除所有设置，但不包括：
    - 允许语音漫游
    - 允许数据漫游
    - 允许漫游时自动同步

### <a name="where-can-i-find-help-troubleshooting-policies"></a>在哪里可以找到有关排查策略问题的帮助？

请参阅[策略疑难解答](troubleshoot-policies-in-microsoft-intune.md)。
