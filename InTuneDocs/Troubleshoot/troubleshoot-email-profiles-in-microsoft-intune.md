---
# required metadata

title: 电子邮件配置文件疑难解答 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的电子邮件配置文件疑难解答
下面列出了一些电子邮件配置文件问题，以及排查并解决这些问题的方式。

如果此信息未解决你的问题，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)，了解更多获得帮助的方法。


## 无法从电子邮件帐户发送图像
自动配置了电子邮件帐户的用户无法从其设备发送图片或图像。
未启用“允许从第三方应用程序发送电子邮件”时，将发生此情况。

### Intune 解决方案

1.  打开 Microsoft Intune 管理控制台，选择**策略**工作负荷&gt;**配置策略**。

2.  选择电子邮件配置文件，然后单击**编辑**。

3.  选择“允许从第三方应用程序发送电子邮件”

### 与 Intune 解决方案集成的 Configuration Manager

1.  打开 Configuration Manager 控制台&gt;**资产和合规性**。

2.  展开**概述** -&gt;**合规性设置** -&gt;**公司资源访问**，然后选择**电子邮件配置文件**。

3.  右键单击电子邮件配置文件，然后打开**属性**。

4.  在**同步设置**选项卡上，选择**允许从第三方应用程序发送电子邮件**。

## 后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。


<!--HONumber=Jun16_HO1-->


