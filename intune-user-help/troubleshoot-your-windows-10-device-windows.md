---
title: "Windows 10 设备注册疑难解答 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4ab630b6-47ff-443b-a2a5-be23388bcea7
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 936a336019c37fb5ae5f7ef8f5b1201faee553fc
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="troubleshoot-your-windows-10-device-enrollment"></a>Windows 10 设备注册疑难解答
如果你按照“[在 Intune 中注册 Windows 10 移动版或 Windows 10 桌面版设备](enroll-your-w10-phone-or-w10-pc-windows.md)”中的步骤操作，但是仍无法访问工作或学校电子邮件和文件，请尝试以下故障排除步骤。

1.  查看接下来的两个屏幕，并找到与你在设备上看到的相似屏幕。 按照与你在设备上看到的屏幕相匹配的步骤操作。

    如果你看到此屏幕，请按照[看到“访问工作单位或学校”时要执行的故障排除步骤](#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)中的步骤操作。

    ![settings-accounts-access-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    如果你看到此屏幕，请按照[看到“你的帐户”时要执行的故障排除步骤](#troubleshooting-steps-to-follow-if-you-see-your-account)中的步骤操作。

    ![settings-accounts-your-account](./media/W10-enroll-2-accounts-your-account.png)

## <a name="troubleshooting-steps-to-follow-if-you-see-access-work-or-school"></a>看到“访问工作单位或学校”时执行的故障排除步骤

1.  如果执行了上述步骤，但仍无法访问你的工作或学校电子邮件和文件，请返回至“**访问工作单位或学校**”。

2. 执行以下操作之一：

    - 如果你看到类似下图的连接，点击该连接，并确认你看到“管理”、“信息”和“断开连接”选项。 如果你看到以上选项，表示你现在已注册且已连接。

    ![validate-successful-enrollment](./media/w10-enroll-rs1-validate-successful-enrollment.png)

    - 如果你没有看到以上所示的连接信息，或者你看到此类信息但是其中缺少部分选项，则点击“**连接**”，然后使用你的工作或学校凭据登录。 立即连接。

## <a name="troubleshooting-steps-to-follow-if-you-see-your-account"></a>看到“你的帐户”时执行的故障排除步骤

如果执行了上述步骤，但仍无法访问你的工作或学校电子邮件、文件和其他数据，请返回到“**帐户**”并点击“**工作访问**”。

- 如果你看到你的工作单位或学校帐户，那么恭喜你。 你已连接。

- 如果看不到工作单位或学校帐户，请点击“连接”，然后使用工作单位或学校凭据登录。

## <a name="troubleshooting-steps-to-follow-if-you-see-set-up-a-work-or-school-account"></a>看到“设置工作或学校帐户”时执行的故障排除步骤

如果看到消息“我们无法自动发现与所输入用户名匹配的管理终结点。请检查用户名并重试。如果知道管理终结点的 URL，请输入。”，则应尝试重新输入用户名和密码__。 如果仍无效，则应咨询公司支持人员，获取需在“管理终结点”文本框中提供的网站。 网站可能类似于 www.yourcompany.onmicrosoft.com。

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
