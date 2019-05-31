---
title: Intune 公司门户中的 Windows 设备注册 | Microsoft Docs
description: 开始在公司门户中注册 Windows 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9f29e2d737dfd7bef709f239d6c8506c3bb746c
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196886"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Intune 公司门户中的 Windows 设备注册  

在 Intune 公司门户应用中注册 Windows 设备，以安全访问工作和学校应用、电子邮件和文件。 如果组织需要或推荐某些应用（如 Office 或 OneDrive），你将在注册期间收到这些应用，或者注册后公司门户中会提供这些应用。  

可以通过公司门户网站或应用注册 Windows 10 设备  。 如果要使用早期版本的 Windows 注册设备，则必须通过公司门户网站注册该设备。  

## <a name="install-company-portal-app"></a>安装公司门户应用  
你可能已在设备上安装了公司门户应用。 请在“所有应用”列表中检查应用  。  如果未在应用列表中看到公司门户，请按照这些步骤安装它。  

1. 在设备上打开“Microsoft Store”  。

2. 在“搜索”字段中，键入“公司门户”   。

3. 在结果列表中，选择“公司门户”   > “安装”  。

4. 选择“安装”  或“释放”  。 这两个选项没有区别；根据组织设置应用的方式显示字词。  

## <a name="find-windows-10-version-number"></a>查找 Windows 10 版本号  
不同版本的 Windows 10 设备注册步骤会有所不同。 以下步骤介绍如何在 Windows 10 桌面和移动设备上查找版本号。 了解你的版本后，请继续执行推荐的注册步骤。  

### <a name="windows-10-desktop-devices"></a>Windows 10 桌面设备  

1. 转到“开始”  。

2. 在搜索栏中，键入短语“关于电脑”。 从结果中，选择“关于电脑”  。  


   ![搜索关于电脑的设置](media/searching_for_about_your_pc.png)  

3. 向下滚动到“Windows 规格”，找到电脑上安装的 Windows 10 版本   。  


   ![关于电脑的 Windows 10 桌面](media/settings_about_pc.png)  

4. 如果版本为  

    *  __1607 或更高版本__：通过[“设置” > “帐户” > “使用工作或学校帐户”路由](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)注册设备    。   
    * __1511 或更早版本__：通过[“设置” > “帐户” > “你的帐户”路由](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)注册设备    。  

### <a name="windows-10-mobile-devices"></a>Windows 10 移动设备       

1.  转到“所有应用”，然后选择“设置”应用   。  
2.  选择“系统” > “关于”   。      
3.  在“设备信息”下，找到“版本”   。  
4. 如果版本为  

    *  __1607 或更高版本__：使用[“设置” > “使用工作或学校帐户”路由](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)注册设备   。   
    * __1511 或更早版本__：使用[“设置” > “帐户路由”](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)注册设备   。  

## <a name="enroll-non-windows-10-devices"></a>注册非 Windows 10 设备  
可参阅以下文章，通过公司门户网站注册其他受支持的 Windows 设备：   
* [Windows 8.1 或 Windows RT 8.1 设备](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1 设备](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>IT 管理员支持  
如果你是 IT 管理员且在注册设备时遇到问题，请参阅 [Microsoft Intune 中的 Windows 设备注册问题疑难解答](https://support.microsoft.com/help/4469913)。 本文列出了常见错误、错误原因及其解决方法步骤。  

## <a name="next-steps"></a>后续步骤  
现在你了解了受支持的设备和你的 Windows 10 版本号，请继续阅读推荐的注册文章。  
 
有关设备管理、公司门户以及如何在学校和工作中使用这两者的详细信息，请参阅以下文章：  
* [使用受管理设备访问工作或学校资源](use-managed-devices-to-get-work-done.md)  
* [在 Intune 中注册设备时会发生什么情况](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [在我注册自己的设备时，我的组织可以看到哪些信息？](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

需要帮助吗? 请与公司支持人员联系。 请[转到公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)，查找组织的 IT 人员联系信息。  
