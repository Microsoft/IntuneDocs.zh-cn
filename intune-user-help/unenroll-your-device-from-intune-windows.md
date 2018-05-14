---
title: 从 Intune 删除 Windows 设备 | Microsoft Docs
description: 介绍如何从 Intune 删除 Windows 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 89a69f7d5cda31658cc9faf068a2a37698fdd93c
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="remove-your-windows-device-from-intune"></a>从 Intune 删除 Windows 设备

如果在 Intune 中注册了设备，但不想再通过该 Windows 设备来使用工作或学校电子邮件、应用或其他资源，则需要删除对该设备的管理。 从 Intune 删除设备后，就无法再访问这些资源。 若要深入了解删除对设备的管理后会发生什么情况，请参阅[从 Intune 取消注册设备会发生什么情况？](what-happens-if-you-unenroll-your-device-from-intune-windows.md)。

## <a name="remove-your-windows-10-device"></a>删除 Windows 10 设备

1.  从应用列表，请点击“公司门户”  应用。

2.  使用工作单位或学校凭据登录。

3.  在“我的设备” 中，选择要取消注册的设备。

4.  点击**删除** &gt; **删除**。

## <a name="remove-your-windows-81-computer"></a>删除 Windows 8.1 计算机

1.  转至**电脑设置** &gt; **网络** &gt; **工作区**。

2.  在“工作区加入”下，选择“退出”。

3.  在“打开设备管理”下，选择“关闭”。

4.  在打开的弹出窗口中，选择“关闭”。

## <a name="remove-your-windows-phone-81-mobile-device"></a>删除 Windows Phone 8.1 移动设备

1.  转到**设置** &gt; **工作区**。

2.  点击要取消注册的工作区帐户。

3.  点击屏幕底部的“删除”。

4.  在“删除帐户”对话框中，点击“删除”。

## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>删除公司门户后删除个人信息

公司门户在 Windows 设备上存储的数据分为两种：

-   **诊断日志**：Microsoft 收集的标准应用活动数据，例如应用开启时长或应用是否崩溃。卸载公司门户应用时，系统会自动清除此数据。
-   **应用程序缓存**：存储应用正常工作所需的某些支持文件，例如图标和设置。

完全删除此信息需执行以下步骤：

### <a name="uninstall-the-company-portal"></a>卸载公司门户  

[卸载公司门户应用](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs)将删除存储在设备上的部分应用数据。  

### <a name="reset-the-company-portal"></a>重置公司门户

在“设置”中重置公司门户应用可以重置该应用剩下的应用数据。 依次打开“设置” > “应用和功能” > “公司门户” > “高级选项” > “重置”。

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
