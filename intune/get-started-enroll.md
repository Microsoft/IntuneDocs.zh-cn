---
title: "注册设备入门"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36e658cebdfd23547e3c376124289046f81acc1f
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-enrolling-devices"></a>注册设备入门

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![iOS 设备显示公司门户应用。 显示了向用户展示注册过程的第一个屏幕。](/intune-user-help/media/ios-enroll-1a-comp-access-setup.png)

通过 Microsoft Intune，可让员工将移动设备用于工作，同时保护公司数据。 由于最终用户将在自己的设备而非管理员控制台上与 Intune 交互，因此需确保注册体验是流畅的。 这样一来，便可以将精心设计的符合性策略与你的经验相结合，亲身感受用户的使用体验。 这一点尤其重要，因为用户将可以准确地知道你作为管理员可以看见什么信息：

## <a name="what-it-cannot-see"></a>IT 管理员不能看到的内容
* 调用和 Web 浏览历史记录
* 位置
* 个人电子邮件
* 文本消息
* 联系人
* 个人帐户的密码
* 日历事件
* 图片，包括照片应用中的照片或本机照片

## <a name="what-it-can-see"></a>IT 管理员能够看到的内容
* 型号
* 序列号
* 操作系统版本
* 应用名称
* Owner
* 设备名称
* 制造商（对于非 Apple 生产的设备）
* 电话号码（对于工作设备，则为整个号码。 对于个人设备，只取后四位数字。）

## <a name="how-do-i-enroll-a-device"></a>如何注册设备？

注册设备是许多最终用户访问公司资源时面临的初步体验。 [了解该体验](end-user-educate.md)可帮助改善潜在的不悦体验。

1. 打开“App Store”并搜索“Intune 公司门户”。
2. 下载 **Microsoft Intune 公司门户**应用。
3. 打开“公司门户”应用，输入测试用户的电子邮箱地址和密码，然后点击“登录”。
4. 将临时密码更新为新密码。
5. 在“公司访问设置”页上，点击“设备注册”。
6. 在“为什么要注册设备？”页上，阅读注册设备时用户可以执行的操作，然后点击“继续”。
7. 查看用户注册时将获取的访问权限列表，然后点击“继续”。
8. 查看 IT 管理员在设备上能看见和不能看见的内容，然后点击“继续”。
9. 在“接下来会发生的情况”页上，阅读注册期间会发生的情况，然后点击“注册”。
10. 在“安装配置文件”页上，点击“安装”，然后根据系统提示输入设备密码。
11. 点击“安装”。
12. 再次点击“安装”以表示你已阅读警告。
13. 在“警告”弹出框中，点击“信任”。
14. 屏幕更改为显示配置文件已完成安装时，点击“完成”。
15. 屏幕上将显示“正在注册设备”消息，然后显示设备已成功注册。 弹出框会询问是否在公司门户打开页面。 点击“打开”。
16. 将返回到“公司访问设置”屏幕。 如果未设置测试策略，那么设备会显示符合。 如果有任何测试策略，则点击“设备符合性”将显示为确保设备安全需要执行一些操作。
