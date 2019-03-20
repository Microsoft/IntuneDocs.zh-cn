---
title: 设备缺少必需的证书 | Microsoft Docs
titlesuffix: Microsoft Intune
description: 设备缺少公司支持人员所需的证书。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc86a53dd790059297430fd6b08f1a699aafbc84
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "55850652"
---
# <a name="your-device-is-missing-a-required-certificate"></a>你的设备缺少必需的证书

## <a name="whats-a-certificate"></a>什么是证书？

[加密](https://technet.microsoft.com/library/cc962030.aspx)是为信息提供安全性的技术。 传统上来说，加密一直被用于传递编码消息，以[确保通信处于保密状态](https://technet.microsoft.com/library/cc962019.aspx)。 加密的最简单形式是替代或转置字母，以在不可读取、杂乱或隐藏的消息中创建已编码消息。 只有具有解码密钥或证书的人才能将编码消息转换回其原始的可读取形式。 Android 设备结合使用证书和 Intune，确保设备与组织资源（如电子邮件和文档）之间的通信，通过无线电从一端传递到另一端的过程中始终保持安全。

## <a name="fixing-certificate-issues"></a>修复证书问题

如果 Android 设备未在 Intune 中注册，并且缺少公司支持人员所需的特定证书，则无法登录到公司门户应用。 在尝试登录时，你将看到以下消息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

首先应尝试确认设备是否[缺少通常随附预安装在其上的证书](your-device-is-missing-a-preinstalled-certificate-android.md)。

如果你在解决证书问题后仍看到错误，公司支持人员会[要求你再安装一个证书以获取额外安全防护](your-device-is-missing-an-IT-required-certificate-android.md)。

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
