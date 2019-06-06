---
title: Microsoft Intune 中的疑难解答策略 - Azure | Microsoft Docs
description: 了解如何使用内置的故障排除功能，并了解在 Microsoft Intune 中使用符合性策略和配置文件时的常见疑难或问题及其解决方案
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1bed0fda1c19df181dacb36c832a2a4c94e61aff
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402662"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>在 Intune 中对策略和配置文件进行故障排除

Microsoft Intune 包含一些内置的故障排除功能。 使用这些功能可帮助解决环境中的符合性策略和配置配置文件问题。

本文列出了一些常见的故障排除技术，并介绍可能会遇到的一些问题。

## <a name="use-built-in-troubleshooting"></a>使用内置的故障排除功能

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，选择“故障排除”  ：

    ![在 Intune 中，转到帮助和支持，并选择“故障排除”](./media/help-and-support-troubleshoot.png)

2. 选择“选择用户”> 选择有问题的用户 >“选择”   。
3. 确认“Intune 许可证”和“帐户状态”都显示绿色对勾   ：

    ![在 Intune 中，选择用户，并确认“帐户状态”和“Intune 许可证”都显示绿色复选标记状态](./media/account-status-intune-license-show-green.png)

    **有用的链接**：

    - [分配许可证，以便用户可以注册设备](licenses-assign.md)
    - [将用户添加到 Intune](users-add.md)

4. 在“设备”下，找到有问题的设备  。 查看不同的列：

    - **托管**：要使设备接收符合性或配置策略，此属性必须显示“MDM”或“EAS/MDM”   。

      - 如果“托管”未设置为“MDM”或“EAS/MDM”，则设备未注册    。 除非注册设备，否则设备收不到符合性或配置策略。

      - 应用保护策略（移动应用管理）不要求注册设备。 有关详细信息，请参阅[创建和分配应用保护策略](app-protection-policies.md)。

    - **Azure AD 加入类型**：应设置为“工作区”或“AzureAD”   。
 
      - 如果此列为“未注册”，则可能存在注册问题  。 通常情况下，取消注册并重新注册设备可消除此状态。

    - **Intune 符合性**：应为“是”  。 如果显示“否”，则符合性策略存在问题，或设备未连接到 Intune 服务  。 例如，设备可能已关闭，或者可能未连接到网络。 最终，该设备可能在 30 天后变得不符合。

      有关详细信息，请参阅[设备符合性策略入门](device-compliance-get-started.md)。

    - **Azure AD 符合性**：应为“是”  。 如果显示“否”，则符合性策略存在问题，或设备未连接到 Intune 服务  。 例如，设备可能已关闭，或者可能未连接到网络。 最终，该设备可能在 30 天后变得不符合。

      有关详细信息，请参阅[设备符合性策略入门](device-compliance-get-started.md)。

    - **上次迁入时间**：应为最近的时间和日期。 默认情况下，Intune 设备每隔 8 小时签入一次。

      - 如果“上次签入时间”超过 24 小时，则设备可能存在问题  。 未签入的设备无法从 Intune 接收策略。

      - 强制签入：
        - 在 Android 设备上，打开公司门户应用 >“设备”> 从列表中选择设备 >“检查设备设置”   。
        - 在 iOS 设备上，打开公司门户应用 >“设备”> 从列表中选择设备 >“检查设置”   。 
        - 在 Windows 设备上，打开“设置” > “帐户” > “访问工作或学校”> 选择帐户或 MDM 注册>“信息” > “同步”      。

    - 选择设备以查看特定于策略的信息。

      “设备符合性”显示分配给设备的符合性策略的状态  。

      “设备配置”显示分配给设备的配置策略的状态  。

      如果“设备符合性”或“设备配置”下未显示所需策略，则说明未正确定位策略   。 打开策略，并将策略分配给此用户或设备。

      **策略状态**：

      - **不适用**：此策略在该平台上不受支持。 例如，iOS 策略不适用于 Android。 Samsung KNOX 策略不适用于 Windows 设备。
      - **冲突**：设备上有现有设置，Intune 无法覆盖该设置。 或者，使用不同的值部署了两个具有相同设置的策略。
      - **挂起**：设备未签入到 Intune，无法获得策略。 或者，设备接收到该策略，但尚未将状态报告给 Intune。
      - **错误**：在[公司资源访问权限问题疑难解答](troubleshoot-company-resource-access-problems.md)处查看错误和可能的解决方案。

      **有用的链接**： 

      - [部署设备符合性策略的方法](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
      - [监视设备符合性策略](compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>不确定是否正确应用了配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备” > “所有设备”> 选择设备 >“设备配置”    。 

    每台设备均列出了其配置文件。 每个配置文件都具有“状态”  。 综合考虑所有分配的配置文件（包括硬件以及 OS 限制和要求）时，状态适用。 可能的状态包括：

    - **符合**：设备收到配置文件并向 Intune 报告其符合设置。

    - **不适用**：配置文件设置不适用。 例如，iOS 设备的电子邮件设置不适用于 Android 设备。

    - **挂起**：配置文件已发送到设备，但尚未向 Intune 报告状态。 例如，Android 上的加密需要用户启用加密，可能显示为挂起状态。

**有用链接**：[监视配置设备配置文件](device-profile-monitor.md)

> [!NOTE]
> 当具有不同限制级别的两个策略应用于同一个设备或用户时，会使用限制更严格的策略。

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>警报：将访问规则保存到 Exchange 中的操作失败

**问题**：你在管理控制台中收到警报“将访问规则保存到 Exchange 中的操作失败”   。

如果在 Exchange 内部部署策略工作区（管理控制台）中创建了策略，但使用的是 Office 365，则 Intune 不会强制执行所配置的策略设置。 在警报中，请注意策略来源。 在 Exchange 内部部署工作区下删除旧规则。 旧规则是 Intune 内本地 Exchange 的全局 Exchange 规则，与 Office 365 不相关。 然后，为 Office 365 创建新策略。

[Intune 本地 Exchange 连接器疑难解答](troubleshoot-exchange-connector.md)可能是很好的资源。

## <a name="cant-change-security-policies-for-enrolled-devices"></a>无法更改已注册设备的安全策略

Windows Phone 设备不允许使用 MDM 或 EAS 设置安全策略后降低其安全性。 例如，将“最小字符密码数”设置为 8，然后尝试将其减少到 4  。 对设备应用更严格的策略。

如果要将策略更改为安全级别较低的值，可能需要重置安全策略，具体视设备平台而定。

例如，在 Windows 中，在桌面上从右轻扫打开“超级按钮”  栏。 选择“设置” > “控制面板” > “用户帐户”    。 在左侧，选择“重置安全策略”  链接，然后选择“重置策略”  。

对于其他 MDM 设备（例如 Android、iOS 以及 Windows Phone 8.1），可能需要将其停用并重新注册，这样才能应用限制较少的策略。

[设备注册疑难解答](troubleshoot-device-enrollment-in-intune.md)可能是很好的资源。

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>使用 Intune 软件客户端的电脑 - 经典门户

> [!NOTE]
> 本部分适用于经典门户。 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>policyplatform.log 中与 Microsoft Intune 策略相关的错误

对于使用 Intune 软件客户端进行管理的 Windows 电脑，`policyplatform.log` 文件中的策略错误可能来自设备上 Windows 用户帐户控制 (UAC) 中的非默认设置。 某些非默认 UAC 设置会影响 Microsoft Intune 客户端安装和策略执行。

#### <a name="resolve-uac-issues"></a>解决 UAC 问题

1. 停用计算机。 请参阅[删除设备](devices-wipe.md)。

2. 等待 20 分钟，以便删除客户端软件。

    > [!NOTE]
    > 请勿尝试从“程序和功能”中删除客户端。

3. 在开始菜单上，键入“UAC”，打开“用户帐户控制”设置  。

4. 将通知滑块移动到默认设置。

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>错误：无法从计算机中获取值，0x80041013

如果本地系统上的时间不同步达到或超过五分钟或更长时间，则会出现此问题。 如果本地计算机上的时间不同步，安全事务将因时间戳无效而失败。

要解决此问题，请将本地系统时间设置为尽可能接近 Internet 时间。 或者，将其设置为网络上的域控制器的时间。

## <a name="next-steps"></a>后续步骤

[电子邮件配置文件的常见问题和解决方法](troubleshoot-email-profiles-in-microsoft-intune.md)

[从 Microsoft 获取支持帮助](get-support.md)，或使用[社区论坛](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。