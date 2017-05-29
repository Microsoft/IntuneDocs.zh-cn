---
title: "电子邮件配置文件疑难解答 | Microsoft Docs"
description: "电子邮件配置文件问题，以及故障排除并解决这些问题的方式。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0387fa91628c5f786d9289df309b82bd17cf6447
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Microsoft Intune 中的电子邮件配置文件疑难解答

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

下面列出了一些电子邮件配置文件问题，以及排查并解决这些问题的方式。

如果此信息未解决你的问题，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)，了解更多获得帮助的方法。


## <a name="unable-to-send-images-from--email-account"></a>无法从电子邮件帐户发送图像
自动配置了电子邮件帐户的用户无法从其设备发送图片或图像。
未启用“允许从第三方应用程序发送电子邮件”时，将发生此情况。

### <a name="intune-solution"></a>Intune 解决方案

1.  打开 Microsoft Intune 管理控制台，选择**策略**工作负荷&gt;**配置策略**。

2.  选择电子邮件配置文件，然后单击**编辑**。

3.  选择“允许从第三方应用程序发送电子邮件”

### <a name="configuration-manager-integrated-with-intune-solution"></a>与 Intune 解决方案集成的 Configuration Manager

1.  打开 Configuration Manager 控制台&gt;**资产和合规性**。

2.  展开“概述” -&gt;“合规性设置” -&gt;“公司资源访问”，选择“电子邮件配置文件”。

3.  右键单击电子邮件配置文件，然后打开**属性**。

4.  在**同步设置**选项卡上，选择**允许从第三方应用程序发送电子邮件**。


## <a name="device-already-has-an-email-profile-installed"></a>设备已安装电子邮件配置文件

如果用户在通过 Intune 预配配置文件前已安装了电子邮件配置文件，则 Intune 电子邮件配置文件部署的结果将取决于设备平台：

-**iOS**：Intune 基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 用户创建的重复电子邮件配置文件将阻止由 Intune 管理员创建的配置文件的部署。 这是一个常见问题，因为 iOS 用户通常将创建电子邮件配置文件，然后注册。 公司门户将通知用户由于其手动配置的电子邮件配置文件而导致他们不符合要求，并提示用户删除该配置文件。用户应删除其电子邮件配置文件，以便可以部署 Intune 配置文件。 为防止此问题，请告知用户在安装电子邮件配置文件前进行注册，并允许 Intune 部署配置文件。

-**Windows**：Intune 基于主机名和电子邮件地址检测现有的重复电子邮件配置文件。 Intune 将覆盖由用户创建的现有电子邮件配置文件。

-**Samsung KNOX 标准版**：Intune 基于电子邮件地址识别重复的电子邮件帐户，并将使用 Intune 配置文件将其覆盖。 如果用户未配置该帐户，则 Intune 配置文件将再次覆盖该帐户。 请注意，这可能会导致帐户配置被覆盖的用户感到困惑。

由于 Samsung KNOX 不使用主机名识别配置文件，因此建议你不要创建多个电子邮件配置文件并部署到不同主机的同一邮件地址中，因为它们会相互覆盖。

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>KNOX 标准版设备的错误 0x87D1FDE8
**问题**：为各种 Android 设备创建并部署适用于 Samsung KNOX 标准版的 Exchange Active Sync 电子邮件配置文件后，将在设备的“属性”&gt;“策略”选项卡中报告错误“0x87D1FDE8” 或“修正失败”。

请查看适用于 Samsung KNOX 的 EAS 配置文件的配置以及源策略。 Samsung Notes 同步选项不再受支持，因此，不应该在配置文件中选择此选项。 确保设备有足够的时间处理策略，最多为 24 小时。

## <a name="next-steps"></a>后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。

