---
title: 检查设备访问 | Microsoft Docs
description: 检查设备访问，确定设备是否符合要求，能否访问工作或学校资源。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49075fd750ade6aaa412d551f4177822b52ce7f2
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490102"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>通过适用于 Windows 的公司门户应用检查访问

验证设备是否具有工作或学校资源的访问权限。 

组织强制实施某些要求（&ndash;如加密和密码限制&ndash;），确保仅受信任的安全设备能访问其数据。 托管设备必须满足并维护这些要求才能访问组织资源。

“检查访问”操作将评估设备的设置及其访问状态  。 “设备详细信息”页列出了需要调整才能重获访问权限的设置。  

完成本文中的步骤，通过适用于 Windows 的公司门户应用检查访问。  

## <a name="check-access-from-device-details-page"></a>通过“设备详细信息”页检查访问  
1. 打开适用于 Windows 的公司门户应用并转到“我的设备”  。  

    ![适用于 Windows 的公司门户应用的“主页”示例屏幕截图，其中突出显示了“我的设备”部分。](./media/1809_CheckAccess_Context_Select_Device.png)  
2. 选择设备。  
3. 在“设备详细信息”页上，选择“检查访问”   。 应用会将设备与组织的当前要求进行同步并检查，确保设备符合这些要求。 此检查可能需要几分钟时间才能完成。  

    ![适用于 Windows 的公司门户应用的“设备详细信息”页示例屏幕截图，其中突出显示了“检查访问”按钮。](./media/1809_CheckAccess_Checking_Status.png) 

4. 查看状态更新。 它将显示设备“可以访问组织的资源”或“无法访问组织的资源”   。  

   ![适用于 Windows 的公司门户应用的“设备详细信息”页示例屏幕截图，其中突出显示了“状态”部分。](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. 如果设备无法访问资源，请转到页面顶部的警报。 单击“更多”可展开其详细信息  。 单击“更少”可将其折叠  。  

    ![适用于 Windows 的公司门户应用的“设备详细信息”页示例屏幕截图，其中突出显示了页面顶部的警报。](./media/1809_CheckAccess_Device_details_alert1.png)  

6. 如果适用，该消息将显示更多帮助链接和修正措施。 选择其中一个或多个选项立即开始进行故障排除。 只有在受影响的设备上使用公司门户时，才会显示&ndash;下面介绍的&ndash;解决、同步和联系操作。  

     * “如何解决此问题”可打开相关的帮助文章（如果可用）  。  
     * “解决”将重定向到设备上的设置  。  
     * “同步”将对设备进行评估以确保其符合组织要求  。  
     * “联系 IT 部门”将重定向到 IT 团队的联系信息  。   
 
6. 更新设置后，单击“检查访问”，确认设备状态  。  

    ![适用于 Windows 的公司门户应用的“设备详细信息”页示例屏幕截图，其中突出显示了“状态”部分。](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>通过设备上下文菜单检查访问  
1. 打开适用于 Windows 的公司门户应用并转到“我的设备”  。  

    ![适用于 Windows 的公司门户应用的“主页”示例屏幕截图，其中突出显示了“我的设备”部分。](./media/1809_CheckAccess_Context_Select_Device.png)  

2. 右键单击或按住某个设备，打开其[上下文菜单](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus)。  

    ![适用于 Windows 的公司门户应用的“主页”示例屏幕截图。 设备上下文菜单显示在该页面的“我的设备”部分，其中包括“重命名”、“删除”和“检查访问”操作。](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. 选择“检查访问”  。 应用会将设备与组织的当前要求进行同步并检查，确保设备符合这些要求。 此检查可能需要几分钟时间才能完成。  
 
4. 设备下方会显示一条消息，告知你设备“可以访问公司资源”或“无法访问公司资源”   。 

    ![适用于 Windows 的公司门户应用的“设备详细信息”页示例屏幕截图，其中突出显示了“状态”部分。](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. 如果设备无法访问资源，请选择该设备。  
6. 在“设备详细信息”页上，转到页面顶部的警报  。 单击“更多”可展开其详细信息  。 单击“更少”可将其折叠  。  

    ![适用于 Windows 的公司门户应用的“设备详细信息”页示例屏幕截图，其中突出显示了页面顶部的警报。](./media/1809_CheckAccess_Device_details_alert1.png)  

6. 如果适用，该消息将显示更多帮助链接和修正措施。 选择其中一个或多个选项立即开始进行故障排除。 只有在受影响的设备上使用公司门户时，才会显示&ndash;下面介绍的&ndash;解决、同步和联系操作。  

     * “如何解决此问题”可打开相关的帮助文章（如果可用）  。  
     * “解决”将重定向到设备上的设置  。  
     * “同步”将对设备进行评估以确保其符合组织要求  。  
     * “联系 IT 部门”将重定向到 IT 团队的联系信息  。    

7. 更新设置后，单击页面底部的“检查访问”  。  

    ![适用于 Windows 的公司门户应用的“设备详细信息”页示例屏幕截图，其中突出显示了“检查访问”操作。](./media/1809_CheckAccess_Device_details_button.png) 


需要更多帮助？ 在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)上查找公司支持人员的联系信息。
