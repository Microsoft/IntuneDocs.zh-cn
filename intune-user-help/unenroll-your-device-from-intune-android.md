---
title: 如何从 Intune 删除 Android 设备 | Microsoft Docs
description: 介绍如何从 Intune 取消注册 Android 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ec3c0a1c8ce4e04f4d23fb01e7c2525d8f2eed5b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-remove-your-android-device-from-intune"></a>如何从 Intune 删除 Android 设备

从 Intune 删除 Android 设备后，该设备无法再访问公司资源。  若要深入了解删除对设备的管理后会发生什么情况，请参阅[从 Intune 取消注册设备会发生什么情况？](what-happens-if-you-unenroll-your-device-from-intune-android.md)

## <a name="removing-the-device-from-the-company-portal-app"></a>从公司门户应用删除设备

若要从 Intune 和公司门户应用删除设备，请按照下列步骤操作：

1. 通过单击公司门户应用右上角的三个垂直点，打开“操作菜单”。

   ![Android 公司门户应用的图像和操作菜单将在右上角打开。 新的“删除公司门户”选项是第三个选项，位于“我的配置文件“和“设置”的下方，以及“条款和条件”、“帮助和反馈”和“关于”的上方。](./media/android_remove_cp_menu_action_after_1705.png)

2. 点击“删除公司门户”。

3. 系统将弹出一条确认消息，询问你是否确定要删除“公司门户”。 它将提供一些信息，说明取消注册设备会发生的情况。 阅读此消息后，单击“确定”删除应用。

   ![在操作菜单中选择新的“删除公司门户”选项后，将出现一个确认对话图像。 该对话将通知用户“删除公司门户，设备将不再由公司支持人员管理，并且可能删除对公司数据、公司应用和公司电子邮件的访问权限。” 然后，它会要求用户通过选择“是”确认删除“公司门户”应用。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>删除由公司门户应用收集的数据

若要删除 Android 适用的公司门户应用存储在设备上的所有数据，请执行以下操作：

-   在“应用程序”中单击该应用，然后单击“清除数据”按钮以清除应用数据
-   删除文件夹“\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal”

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
