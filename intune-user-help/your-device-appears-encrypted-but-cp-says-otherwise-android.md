---
title: "你的 Android 设备似乎已加密，但公司门户将该设备识别为未加密"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6da1d00ce654add003a2f8e39b1a1c987d96e5a4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---


# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>你的 Android 设备似乎已加密，但公司门户将该设备识别为未加密

加密设备即是在设备上使用只有自己知道的密钥编码信息，以防止未经授权的人员访问设备。 为确保信息安全，组织会要求加密 Android 设备才能访问公司文件、电子邮件或数据。

一些 Android 设备（版本 7.0+）会以与某些 Android 平台标准不同的方式加密数据。 这些设备可能看起来已加密，但 Intune 认为所使用的这些方法会让设备信息受到具有对设备的物理访问权限的恶意用户的威胁。

> [!Note]
> Microsoft 与所有列出的制造商合作来解决此问题，并在任意修补程序完成后，相应地更新此列表。

## <a name="an-incomplete-list-of-devices"></a>不完整的设备列表

如果具有以下设备之一，将遇到此问题。

- [华为荣耀 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [华为 P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

## <a name="solutions"></a>解决方案

如果设备提供降级到 Android 6.0+ 的选项，请进行降级。 如果尝试进行设备降级，将存在数据丢失的风险。 若要避免此风险，建议联系 IT 管理员解决此问题。 可在[公司门户网站](http://portal.manage.microsoft.com)获取 IT 管理员的联系信息。

