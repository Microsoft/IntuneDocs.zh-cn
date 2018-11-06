---
title: 如何从 Intune 删除 Android 设备 | Microsoft Docs
description: 介绍如何从 Intune 取消注册 Android 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
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
ms.openlocfilehash: d932005c955afed7f16e9766b559b77b2cd43182
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959479"
---
# <a name="unenroll-your-android-device-from-management"></a>取消注册 Android 设备管理  

删除已注册的 Android 设备，使其不再由组织管理。 本文介绍如何从公司门户应用中删除设备。 删除设备后：  

* 设备将无法访问组织受保护的数据和资源。
* 设备不再显示在公司门户中。
* 不能通过“公司门户”安装应用。
* 将不再应用当添加设备时在设备上更改的任何设置（例如禁用相机，或需要一定的密码长度）。  

1. 在公司门户中，转到右上角并点击三个垂直点。 “操作”菜单随即打开。

   ![Android 公司门户应用的图像和操作菜单将在右上角打开。 新的“删除公司门户”选项是第三个选项，位于“我的配置文件“和“设置”的下方，以及“条款和条件”、“帮助和反馈”和“关于”的上方。](./media/android_remove_cp_menu_action_after_1705.png)

2. 点击“删除公司门户”。  

3. 将显示一条消息，说明取消注册设备后会发生的情况。 点击“确定”，确认要从公司门户中删除设备。

   ![在操作菜单中选择新的“删除公司门户”选项后，将出现一个确认对话图像。 该对话将通知用户“删除公司门户，设备将不再由公司支持人员管理，并且可能删除对公司数据、公司应用和公司电子邮件的访问权限。” 然后，它会要求用户通过选择“是”确认删除“公司门户”应用。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>删除由公司门户应用收集的数据  

若要删除 Android 适用的公司门户应用存储在设备上的所有数据，请执行以下操作：

-   在“应用程序”中单击该应用，然后单击“清除数据”按钮以清除应用数据
-   删除文件夹“\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal”

## <a name="uninstall-the-company-portal-app"></a>卸载公司门户应用  
公司门户是一个设备管理应用，因此在[取消注册设备管理](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management)之前，都无法将其卸载。 该操作完成后，请点击并按住公司门户应用图标，直到看到“卸载”。 点击“卸载”，从设备中删除应用。  

或者，点击“设置” > “应用” > “公司门户” > “卸载”。  

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)
