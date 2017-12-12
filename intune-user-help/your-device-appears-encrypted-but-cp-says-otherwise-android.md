---
title: "你的 Android 设备似乎已加密 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: f9c91c85b4a93fb211b5cd278dd82277a58cb08e
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>你的 Android 设备似乎已加密，但公司门户将该设备识别为未加密

加密设备是指在设备上使用只有你自己知道的密钥编码信息。 这可防止未经授权的人员访问设备。 许多组织要求用户先加密 Android 设备，才能访问公司文件、电子邮件或数据。

## <a name="common-issues"></a>常见问题

较新版本的 Android（尤其是以 v7.0 开头的），需要启动密码以确保你的设备已完全加密。 不同设备制造商的启动密码说明和位置会有所不同。 大多数情况下，此设置称为“安全启动”。 

## <a name="solutions"></a>解决方案

### <a name="add-a-startup-pin"></a>添加启动 PIN

某些 Android 设备需要创建启动 PIN，确保设备安全。 有多个来自不同制造商版本的 Android。 你可以尝试通过在设置应用中查找位置启用此选项来解决此问题。 例如，在 Samsung Galaxy S7 上，通过转到“设置” > “锁定屏幕和安全性” > “安全启动”启用“安全启动”。  

### <a name="downgrade-your-version-of-android"></a>降级 Android 版本

如果设备提供降级到 Android 6.0+ 的选项，请进行降级。 如果尝试进行设备降级，将存在数据丢失的风险。 若要避免此风险，建议联系公司支持人员解决此问题。 可在[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)获取公司支持人员的联系信息。

### <a name="encrypt-the-entire-device"></a>加密整个设备

某些设备支持选择加密整个设备或仅加密已用空间。 请选择“加密整个设备”选项而非“仅加密已用空间”。 如果已选择仅加密已用空间，则需：

1. [从公司门户中删除此设备](unenroll-your-device-from-intune-android.md)
2. 解密已用空间
3. 加密整个设备
4. 重新注册设备

## <a name="specific-manufacturer-issues"></a>特定制造商问题

一些 Android 设备（版本 7.0+）会以与某些 Android 平台标准不同的方式加密数据。 即使这些设备是全新的，也有可能显示已加密。 Intune 认识到，这些设备的加密方法会对设备信息构成风险。 这种风险主要源自对设备拥有物理访问权限的恶意用户。

> [!Note]
> Microsoft 将与制造商协作以解决我们在测试中发现的，或用户上报的任何问题。 每当有新的信息可用时，我们会更新本文。 

## <a name="known-devices"></a>已知设备

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>可更新来解决此问题的已知设备

如果你拥有以下设备之一，如果你未将设备更新到最新的 Android 版本，则可能会遇到此问题。 你可以通过转到“设置” > “更新”为此类设备安装更新。 

- [华为荣耀 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [华为 P9](http://consumer.huawei.com/en/phones/p9/)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>目前无法更新来解决此问题的已知设备

无法在下列设备上解决此问题。 可能需要使用其他设备来访问公司资源。 

- [华为 Mate 8](https://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [OPPO 设备](http://www.oppo.com/en/smartphones)
- [Vivo 设备](https://www.vivo.co.in)
- [小米 Mi 智能手机](https://xiaomi-mi.com/mi-smartphones/)
