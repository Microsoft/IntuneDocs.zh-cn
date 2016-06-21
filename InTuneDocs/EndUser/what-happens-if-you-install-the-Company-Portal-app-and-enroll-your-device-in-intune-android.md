---
# required metadata

title: 安装公司门户应用并在 Intune 中注册设备后会发生什么？ | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 安装公司门户应用并在 Intune 中注册设备后会发生什么？

当安装公司门户应用并在 Intune 中注册 Android 设备时，可以使用公司门户应用：

-   访问公司网络、你的电子邮件和工作文件

-   从公司门户获取应用

-   自动配置公司电子邮件帐户

-   在手机丢失或被盗时将它重置为出厂设置

在添加 Android 设备时，将向 IT 管理员授予访问设备的权限。 他们可执行诸如以下操作：

-   将你的设备重置回制造商的默认设置。 如果设备丢失或被盗，这非常有用。

-   删除公司相关的所有数据。 不会删除你的个人数据和设置。

-   强制你在设备上设置密码或 PIN，如果尝试输入太多次不正确的密码，你可能会被锁定，无法访问设备，或者将你的设备重置回制造商的默认设置（可能包括删除数据）。

-   要求你接受条款和条件。

-   在设备上启用或禁用相机。

-   强制对设备上的所有数据（包括公司和个人数据）进行加密。 如果设备丢失或被盗，这可帮助保护数据。

-   将你的设备添加到公司门户后，该设备将每隔大约 8 小时执行下列操作：

    -   下载 IT 管理员已提供的任何策略或应用更新。

    -   发送任何硬件清单更新（这些更新不包含个人信息）。

    -   发送任何公司应用清单更新（这些更新不包含个人信息）。

如有疑问，并且找不到 IT 管理员的联系信息，请查看在[公司门户网站](http://portal.manage.microsoft.com)中是否已经列出。

### 另请参阅
[通过 Intune 使用 Android 设备](using-your-android-device-with-intune.md)

<!--HONumber=Jun16_HO1-->


