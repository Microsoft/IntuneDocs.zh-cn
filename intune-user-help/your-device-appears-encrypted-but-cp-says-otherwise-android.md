---
title: "你的 Android 设备似乎已加密"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
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
ms.sourcegitcommit: 5ed0e84c16ea540c08e97cb55ef8a09cbc7339f6
ms.openlocfilehash: 269ad7968242f8f5ce7095c9c73347987675e846
ms.contentlocale: zh-cn
ms.lasthandoff: 05/26/2017


---


# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>你的 Android 设备似乎已加密，但公司门户将该设备识别为未加密

加密设备是指在设备上使用只有你自己知道的密钥编码信息，用以防止未经授权的人员访问设备。 为确保信息安全，组织会要求加密 Android 设备才能访问公司文件、电子邮件或数据。

## <a name="common-issues"></a>常见问题

较新版本的 Android（尤其是以 v7.0 开头的），需要启动密码以确保你的设备已完全加密。 不同设备制造商的启动密码说明和位置会有所不同。 大多数情况下，这称为“安全启动”。 

## <a name="solutions"></a>解决方案

### <a name="add-a-startup-pin"></a>添加启动 PIN

某些 Android 设备将要求你创建启动 PIN，以确保设备的安全。 有多个来自不同制造商版本的 Android。 你可以尝试通过在设置应用中查找位置启用此选项来解决此问题。 例如，在 Samsung Galaxy S7 上，通过转到“设置” > “锁定屏幕和安全性” > “安全启动”启用“安全启动”。  

### <a name="downgrade-your-version-of-android"></a>降级 Android 版本
如果设备提供降级到 Android 6.0+ 的选项，请进行降级。 如果尝试进行设备降级，将存在数据丢失的风险。 若要避免此风险，建议联系 IT 管理员解决此问题。 可在[公司门户网站](http://portal.manage.microsoft.com)获取 IT 管理员的联系信息。

## <a name="specific-manufacturer-issues"></a>特定制造商问题

一些 Android 设备（版本 7.0+）会以与某些 Android 平台标准不同的方式加密数据。 这些设备可能看起来已加密，但 Intune 认为所使用的这些方法会让设备信息受到具有对设备的物理访问权限的恶意用户的威胁。

> [!Note]
> Microsoft 将与制造商协作以解决我们在测试中发现的，或用户上报的任何问题。 每当有可用的新信息时，我们将更新本文。 

## <a name="known-devices"></a>已知设备

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>可更新来解决此问题的已知设备

如果你拥有以下设备之一，如果你未将设备更新到最新的 Android 版本，则可能会遇到此问题。 你可以通过转到“设置” > “更新”为此类设备安装更新。 

- [华为荣耀 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [华为 P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>目前无法更新来解决此问题的已知设备

- [华为 Mate 8](http://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [小米 Mi 智能手机](https://xiaomi-mi.com/mi-smartphones/)

