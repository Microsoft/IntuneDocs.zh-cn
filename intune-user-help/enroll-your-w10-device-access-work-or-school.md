---
title: "在 Intune 中注册 Windows 10 设备 | Microsoft Docs"
description: "将 Windows 10 1607 或更高版本设备注册到 Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope: User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: aa12a88cfd80f62e2f7b249b52333bd16cbb6533
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-your-windows-10-device-in-intune"></a>在 Intune 中注册 Windows 10 设备

> [!NOTE]
> Windows 10 适用于所有类型的设备。 无论使用台式电脑、手机还是平板电脑，所遵循的步骤都相同，但是这些步骤可能与此页面上的图像略有差异。

<iframe src="https://channel9.msdn.com/Series/IntuneEnrollment/Windows-Enrollment/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

1. 转到“开始”。

  - 如果使用 Windows 10 桌面版设备，请转到“开始”菜单。
  - 如果使用 Windows 10 移动版设备，请转到“开始”屏幕，然后轻扫至“所有应用”列表。

2.  通过在搜索栏中搜索“设置”，打开 Windows“设置”应用。

3. 选择“帐户” > “访问工作或学校” > “连接”。

    ![选择“访问工作学校帐户”](./media/w10-enroll-rs1-connect-to-work-or-school.png)

3.  输入工作或学校电子邮件地址，然后选择“下一步”。

    ![输入你的工作或学校帐户](./media/w10-enroll-rs1-set-up-work-or-school-account.png)

4. 使用你的工作或学校帐户登录 Intune。

    ![添加工作或学校帐户](./media/w10-enroll-rs1-enter-your-credentials.png)

    你将看到指示你的公司或学校正在注册你的设备的消息。

5. 当你看到**设置完成!** 屏幕，选择“关闭”。 大功告成。

  ![在“设置完成！”上选择“关闭” 屏幕](./media/w10-enroll-rs1-youre-all-set.png)

6. 如果要再次确认是否已正确连接，请返回到“**设置**”，现在应该可以看到列出的工作或学校帐户。

    ![验证已正确设置了连接](./media/w10-enroll-rs1-validate-successful-enrollment.png)

如果执行了之前的步骤，但仍无法访问你的工作或学校电子邮件帐户和文件，请按照[看到“访问工作单位或学校”时要执行的故障排除步骤](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)中的步骤操作。
