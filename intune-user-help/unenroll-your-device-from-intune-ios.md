---
title: 从 Intune 删除 iOS 设备 | Microsoft Docs
description: 介绍如何从 Intune 删除 iOS 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d52ef6f2cf995031c25bc9065212e39235041b2
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "55841141"
---
# <a name="remove-your-ios-device-from-intune"></a>从 Intune 删除 iOS 设备

从 Intune 删除 iOS 设备后，该设备将无法再访问公司资源并且无法再通过 Intune 进行托管。


## <a name="removing-the-device-from-my-devices"></a>从“我的设备”中删除设备

若要从 Intune 删除设备，请使用以下步骤，或观看此视频：


1.  在公司门户应用中，点击“设备”。 并选择要取消注册的设备。 如果只有一个设备，点击“设备”后将直接转到设备详细信息屏幕。

2.  点击“重命名”旁边的省略号按钮，然后点击“删除设备” > “删除”。  

    |![公司门户应用“设备”屏幕的屏幕截图，其中显示了用户单击“删除”后出现的选项。 显示了“删除设备”按钮、“出厂重置”按钮和“取消”按钮。](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![公司门户应用“设备”屏幕的屏幕截图，其中显示了用户单击“删除设备”后出现的选项。 以红色突出显示了“删除”按钮，并以蓝色突出显示了“了解详细信息”和“取消”按钮。](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


  从 Intune 取消注册设备后，将发生以下情况：

  -   设备将不再出现在公司门户中。

  -   再也不能从公司门户安装应用。

  -   将不再应用当你添加设备时在设备上更改的任何设置（例如禁用相机，或需要一定的密码长度）。

  -   你可能不再能够访问设备上的某些公司资源（例如文件共享或内部网站）。

  -   你不再能使用设备上的公司应用和公司数据。

  -   你可能不再能够使用 Wi-Fi 或虚拟专用网 (VPN) 连接到公司网络。

  -   已从设备中删除公司电子邮件配置文件。

  -   仅针对电子邮件配置的设备将不再出现在公司门户应用或网站中。
  
  -   卸载应用。 删除公司应用数据。

## <a name="removing-data-collected-by-the-company-portal-app"></a>删除由公司门户应用收集的数据

公司门户将本地数据存储在设备上的三个地方。

-   **信息日志**：Microsoft 收集的标准应用活动数据，例如应用打开时长或应用是否崩溃。从公司门户删除设备时，系统会自动清除此数据。

-   **Apple 分析**：Apple 收集的标准应用崩溃活动数据。 仅当将设备重置为出厂设置时系统才会删除此信息。 此操作会清除设备上的所有个人信息。 若要执行此操作，请打开“设置” > “常规” > “重置” > “清除所有内容和设置”。

-   **Keychain**：设备将用于登录的密码和其他信息存储在 Keychain 中。 设备上安装的任何 Microsoft 开发的应用都可以共享登录信息，包括 Microsoft Outlook 和 Microsoft Authenticator。 与 Apple 分析一样，仅当将设备重置为出厂设置时系统才会删除此信息。 此操作会清除设备上的所有个人信息。 若要执行此操作，请打开“设置” > “常规” > “重置” > “清除所有内容和设置”。


仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
