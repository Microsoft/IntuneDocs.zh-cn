---
title: Microsoft Intune 中的电子邮件配置文件疑难解答 - Azure | Microsoft Docs
description: 请参阅 Microsoft Intune 中电子邮件配置文件的常见问题和解决方案，包括重复的电子邮件配置文件和 Samsung KNOX 标准版 Android 设备上的错误。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/17/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2246e3f6faa853f620327558a7faf4dc9d6a6e85
ms.sourcegitcommit: 43ba5a05b2e1dc1997126d3574884f65cde449c7
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67197511"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Microsoft Intune 中电子邮件配置文件的常见问题和解决方法

回顾一些常见电子邮件配置文件问题，并了解如何排查并解决这些问题。

## <a name="what-you-need-to-know"></a>须知内容

- 已为注册设备的用户部署了电子邮件配置文件。 若要配置电子邮件配置文件，Intune 使用 Azure Active Directory (AD) 属性中的用户的电子邮件配置文件在注册过程。 [将电子邮件设置添加到设备](email-settings-configure.md)可能是很好的资源。
- 从 Configuration Manager 混合迁移至 Intune 独立版后, 从 Configuration Manager 混合环境的电子邮件配置文件将保持在设备上 7 天。 这是预期行为。 如果需要更快地删除电子邮件配置文件，请联系[Intune 支持](get-support.md)。
- Android 企业版 Gmail 或部署使用托管的 Google Play 商店工作的 9 个。 [添加托管 Google Play 应用](apps-add-android-for-work.md)列出的步骤。
- Microsoft Outlook for iOS 和 Android 不支持电子邮件配置文件。 相反，将部署应用配置策略。 有关详细信息，请参阅[Outlook 配置设置](app-configuration-policies-outlook.md)。
- 针对设备组 （而不是用户组） 的电子邮件配置文件可能无法传递到设备。 如果设备具有主要用户，则设备目标设定应起作用。 如果电子邮件配置文件包含用户证书，请确保为目标用户组。
- 可能会反复提示用户输入其密码的电子邮件配置文件。 在此方案中，选中在电子邮件配置文件中引用的所有证书。 如果其中一个证书不针对的是用户，Intune 会尝试将电子邮件配置文件部署。

## <a name="device-already-has-an-email-profile-installed"></a>设备已安装电子邮件配置文件

如果用户在 Intune 或 Office 365 MDM 中注册前创建的电子邮件配置文件，由 Intune 部署的电子邮件配置文件可能无法按预期工作：

- **iOS**：Intune 基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 用户创建电子邮件配置文件会阻止部署 Intune 创建的配置文件。 这是一个常见问题，因为 iOS 用户通常会创建电子邮件配置文件，然后注册。 公司门户应用指明用户不符合策略，并可能会提示用户删除电子邮件配置文件。

  用户应删除其电子邮件配置文件，以便可部署 Intune 配置文件。 若要避免此问题，请通知用户注册 Intune，并允许 Intune 部署电子邮件配置文件。 然后，用户可以创建其电子邮件配置文件。

- **Windows**：Intune 基于主机名和电子邮件地址检测现有的重复电子邮件配置文件。 Intune 会覆盖由用户创建的现有电子邮件配置文件。

- **Samsung KNOX 标准**：Intune 基于电子邮件地址识别重复的电子邮件帐户，并使用 Intune 配置文件将其覆盖。 如果用户配置该帐户，则 Intune 配置文件将再次覆盖该帐户。 这可能会让帐户配置被覆盖的用户感到困惑。

Samsung KNOX 不使用主机名识别配置文件。 不建议创建多个电子邮件配置文件以部署到不同主机上的同一电子邮件地址，因为这样会导致它们相互覆盖。

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>KNOX 标准版设备的错误 0x87D1FDE8

**问题**：为不同的 Android 设备创建并部署适用于 Samsung KNOX 标准的 Exchange Active Sync 电子邮件配置文件后，设备的“属性”>“策略”选项卡中会显示错误“0x87D1FDE8”  或“修正失败”  。

请查看适用于 Samsung KNOX 的 EAS 配置文件的配置以及源策略。 Samsung Notes 同步选项不再受支持，因此，不应在配置文件中选择此选项。 确保设备有足够的时间处理策略，最多为 24 小时。

## <a name="unable-to-send-images-from--email-account"></a>无法从电子邮件帐户发送图像

自动配置了电子邮件帐户的用户无法从其设备发送图片或图像。 未启用“允许从第三方应用程序发送电子邮件”时，可能会发生此情况  。

### <a name="intune-solution"></a>Intune 解决方案

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 依次选择“设备配置”   > “配置文件”  。
3. 选择电子邮件配置文件 >**属性** > **设置**。
4. 设置**允许从第三方应用程序发送电子邮件**将设置为**启用**。

### <a name="configuration-manager-hybrid"></a>Configuration Manager 混合

1. 打开 Configuration Manager 控制台 >“资产和符合性”  。

2. 展开“概述” > “符合性设置” > “公司资源访问”，然后选择“电子邮件配置文件”     。

3. 右键单击电子邮件配置文件，然后打开**属性**。

4. 在**同步设置**选项卡上，选择**允许从第三方应用程序发送电子邮件**。

## <a name="next-steps"></a>后续步骤

[从 Microsoft 获取支持帮助](get-support.md)，或使用[社区论坛](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。
