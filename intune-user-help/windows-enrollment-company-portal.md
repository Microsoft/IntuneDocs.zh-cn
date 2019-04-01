---
title: Windows Intune 公司门户中的设备注册 |Microsoft Docs
description: 公司门户中的 Windows 设备注册入门
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/12/2019
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
ms.openlocfilehash: a637b6eed162243d2be81ac08fbcc055e1fd5816
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "58068908"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Windows Intune 公司门户中的设备注册  

注册 Windows 设备上的 Intune 公司门户应用以获取安全地访问工作和学校的应用、 电子邮件和文件中。 如果你的组织要求或建议特定的应用，例如 Office 或 OneDrive，你将收到其注册期间，或在注册后将是公司门户中提供。  

你可以注册 Windows 10 设备通过公司门户网站*或*应用。 如果你要注册与早期版本的 Windows 设备，必须注册设备通过公司门户网站。  

## <a name="install-company-portal-app"></a>安装公司门户应用  
你可能已在设备上安装的公司门户应用。 中的应用程序检查你__所有应用__列表。  如果未在应用列表中看到公司门户，请按照这些步骤安装它。  

1. 打开**Microsoft Store**在设备上。

2. 在中**搜索**字段中，键入**公司门户**。

3. 在结果列表中，选择“公司门户” > “安装”。

4. 选择“安装”或“释放”。 没有任何区别这两个选项;根据你的组织如何将应用设置显示单词。  

## <a name="find-windows-10-version-number"></a>找到 Windows 10 版本数  
注册步骤不同针对不同版本的 Windows 10 设备。 以下步骤介绍如何查找版本号，在 Windows 10 桌面和移动设备。 您知道您的版本后，继续执行建议的注册步骤。  

### <a name="windows-10-desktop-devices"></a>Windows 10 桌面设备  

1. 转到“开始”。

2. 在搜索栏中，键入"关于电脑。"短语 选择__关于你的电脑__从结果中。  


   ![搜索关于电脑的设置](media/searching_for_about_your_pc.png)  

3. 向下滚动到**Windows 规范**若要查找**版本**的 PC 安装的 Windows 10。  


   ![关于电脑的 Windows 10 桌面](media/settings_about_pc.png)  

4. 如果您的版本  

    *  __1607 或更高版本__： 注册通过设备[**设置** > **帐户** > **访问工作或学校**路由](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)。   
    * __1511 或更早__： 注册通过设备[**设置** > **帐户** > **帐户**路由](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)。  

### <a name="windows-10-mobile-devices"></a>Windows 10 移动设备       

1.  转到__所有应用__，然后选择__设置__应用。  
2.  选择“系统” > “关于”。      
3.  下__设备信息__，找到__版本__。  
4. 如果您的版本  

    *  __1607 或更高版本__： 你的设备使用注册[**设置** > **访问工作或学校**路由](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)。   
    * __1511 或更早__： 你的设备使用注册[**设置** > **帐户**路由](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)。  

## <a name="enroll-non-windows-10-devices"></a>注册非 Windows 10 设备  
使用以下文章来注册其他受支持的 Windows 设备通过公司门户网站：   
* [Windows 8.1 或 Windows RT 8.1 设备](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1 设备](enroll-your-wp81-windows.md)    

## <a name="next-steps"></a>后续步骤  
现在，您知道支持的设备，并且你 Windows 10 的版本号，转到建议的注册一文。  
 
有关设备管理的详细信息，公司门户中，以及如何将使用它们在学校和工作，请参阅以下文章：  
* [使用受管理设备访问工作或学校资源](use-managed-devices-to-get-work-done.md)  
* [在 Intune 中注册设备时会发生什么情况](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [在我注册自己的设备时，我的组织可以看到哪些信息？](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

需要帮助吗? 请与公司支持人员联系。 [转到公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)查找贵组织的 IT 联系信息。  
