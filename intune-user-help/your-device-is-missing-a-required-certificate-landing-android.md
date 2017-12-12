---
title: "设备缺少必需的证书 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 256f643eedcf833ce77c29b389d5e500322802e8
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2017
---
# <a name="your-device-is-missing-a-required-certificate"></a>你的设备缺少必需的证书

## <a name="whats-a-certificate"></a>什么是证书？

[加密](https://technet.microsoft.com/library/cc962030.aspx)是为信息提供安全性的技术。 传统上来说，加密一直被用于传递编码消息，以[确保通信处于保密状态](https://technet.microsoft.com/library/cc962019.aspx)。 加密最简单的形式便是替代或转置字母，以将编码消息创建到不可读取、杂乱或隐藏的消息中。 只有具有解码密钥或证书的人才能将编码消息转换回其原始的可读取形式。 Android 设备结合使用证书和 Intune，确保设备与组织资源（如电子邮件和文档）之间的通信，通过无线电从一端传递到另一端的过程中始终保持安全。

## <a name="fixing-certificate-issues"></a>修复证书问题

如果 Android 设备未在 Intune 中注册，并且缺少公司支持人员所需的特定证书，则无法登录到公司门户应用。 在尝试登录时，你将看到以下消息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

首先应尝试确认设备是否[缺少通常随附预安装在其上的证书](your-device-is-missing-a-preinstalled-certificate-android.md)。

如果无法确认，则公司支持人员会[要求再安装一个证书以获取额外的安全性](your-device-is-missing-an-IT-required-certificate-android.md)。

仍需要帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
