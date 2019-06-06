---
title: Microsoft Intune 中的电子邮件配置文件疑难解答 - Azure | Microsoft Docs
description: 请参阅 Microsoft Intune 中电子邮件配置文件的常见问题和解决方案，包括重复的电子邮件配置文件和 Samsung KNOX 标准版 Android 设备上的错误。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
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
ms.openlocfilehash: e0fe37deb63457fef869df0f7263970a4e53cb29
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402710"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Microsoft Intune 中电子邮件配置文件的常见问题和解决方法

回顾一些常见电子邮件配置文件问题，并了解如何排查并解决这些问题。

## <a name="device-already-has-an-email-profile-installed"></a>设备已安装电子邮件配置文件

如果用户在 Intune 中注册之前创建电子邮件配置文件，则 Intune 电子邮件配置文件可能无法按预期工作：

- **iOS**：Intune 基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 用户创建电子邮件配置文件会阻止部署 Intune 创建的配置文件。 这是一个常见问题，因为 iOS 用户通常会创建电子邮件配置文件，然后注册。 公司门户应用指明用户不符合策略，并可能会提示用户删除电子邮件配置文件。

  用户应删除其电子邮件配置文件，以便可部署 Intune 配置文件。 若要避免此问题，请通知用户注册 Intune，并允许 Intune 部署电子邮件配置文件。 然后，用户可以创建其电子邮件配置文件。

- **Windows**：Intune 基于主机名和电子邮件地址检测现有的重复电子邮件配置文件。 Intune 会覆盖由用户创建的现有电子邮件配置文件。

- **Samsung KNOX 标准**：Intune 基于电子邮件地址识别重复的电子邮件帐户，并使用 Intune 配置文件将其覆盖。 如果用户配置该帐户，则 Intune 配置文件将再次覆盖该帐户。 这可能会让帐户配置被覆盖的用户感到困惑。

Samsung KNOX 不使用主机名识别配置文件。 不建议创建多个电子邮件配置文件以部署到不同主机上的同一电子邮件地址，因为这样会导致它们相互覆盖。

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>KNOX 标准版设备的错误 0x87D1FDE8

**问题**：为不同的 Android 设备创建并部署适用于 Samsung KNOX 标准的 Exchange Active Sync 电子邮件配置文件后，设备的“属性”>“策略”选项卡中会显示错误“0x87D1FDE8”  或“修正失败”  。

请查看适用于 Samsung KNOX 的 EAS 配置文件的配置以及源策略。 Samsung Notes 同步选项不再受支持，因此，不应在配置文件中选择此选项。 确保设备有足够的时间处理策略，最多为 24 小时。

## <a name="unable-to-send-images-from--email-account"></a>无法从电子邮件帐户发送图像

适用于 Azure 经典门户中的 Intune。

自动配置了电子邮件帐户的用户无法从其设备发送图片或图像。 未启用“允许从第三方应用程序发送电子邮件”时，可能会发生此情况  。

### <a name="intune-solution"></a>Intune 解决方案

1. 打开 Microsoft Intune 管理控制台，选择“策略”工作负荷 >“配置策略”   。

2. 选择电子邮件配置文件，然后单击**编辑**。

3. 选择“允许从第三方应用程序发送电子邮件” 

### <a name="configuration-manager-integrated-with-intune-solution"></a>与 Intune 解决方案集成的 Configuration Manager

1. 打开 Configuration Manager 控制台 >“资产和符合性”  。

2. 展开“概述” > “符合性设置” > “公司资源访问”，然后选择“电子邮件配置文件”     。

3. 右键单击电子邮件配置文件，然后打开**属性**。

4. 在**同步设置**选项卡上，选择**允许从第三方应用程序发送电子邮件**。

## <a name="next-steps"></a>后续步骤

[从 Microsoft 获取支持帮助](get-support.md)，或使用[社区论坛](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。