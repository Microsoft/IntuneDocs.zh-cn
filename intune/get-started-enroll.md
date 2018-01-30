---
title: "注册设备入门"
titlesuffix: Azure portal
description: "通过完整体验 iOS 设备的注册过程了解整个注册过程。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3818556f300821fb9acaa260300ae683f43b13e3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="get-started-enrolling-devices"></a>设备注册入门

通过 Microsoft Intune，可让员工将移动设备用于工作，同时保护公司数据。 由于最终用户将在自己的设备而非管理员控制台上与 Intune 交互，因此需确保注册体验是流畅的。 这样一来，便可以将精心设计的符合性策略与你的经验相结合，亲身感受用户的使用体验。 这一点尤其重要，因为用户将可以准确地知道你作为管理员可以看见什么信息：

| IT 管理员不能看到的内容 | IT 管理员能够看到的内容 |
|---|---|
| 调用和 Web 浏览历史记录 | 型号 |
| 位置 | 序列号 |
| 个人电子邮件 | 操作系统版本 |
| 文本消息 | 应用名称 |
| 联系人 | Owner |
| 个人帐户的密码 | 设备名称 |
| 日历事件 | 制造商（对于非 Apple 生产的设备） |
| 图片，包括照片应用中的照片或本机照片 | 电话号码（对于工作设备，则为整个号码。 对于个人设备，只取后四位数字。） |

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

## <a name="next-steps"></a>后续步骤

[应用添加入门](get-started-apps.md) - 查找应用并将应用添加到设备，以便员工完成工作。

## <a name="learn-more"></a>了解详细信息

* [Intune 注册选项](enrollment-options.md)
* [通过 Intune 启用“自带设备办公”](byod-enable.md)
* [让最终用户了解注册和设备管理](end-user-educate.md)
