---
title: 删除 Intune 对 Windows 设备的管理
description: 介绍如何删除 Intune 对 Windows 设备的管理
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
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
ms.openlocfilehash: 5984ac8ebe825a187b33945699a5fadc27e0c0cc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828408"
---
# <a name="remove-your-windows-device-from-management"></a>删除 Intune 对 Windows 设备的管理

当你不再希望或不再需要使用以下功能时，请删除对已注册的 Windows 设备的管理：  
* 将设备用于工作或学校。 
* 访问工作或学校电子邮件、应用或其他资源。

取消注册设备后，将失去从该设备访问学校或工作资源的权限。 可删除对以下 Windows 设备的管理。  
* Windows 10 设备 
* Windows 8.1 计算机
* Windows 8.1 手机
 
若要深入了解删除对设备的管理后会发生什么情况，请参阅[从 Intune 删除设备会发生什么情况？](what-happens-if-you-unenroll-your-device-from-intune-windows.md)。  

## <a name="remove-your-windows-10-device"></a>删除 Windows 10 设备
完成以下步骤以删除对 Windows 10 设备的管理。

### <a name="remove-in-company-portal-app-home-page"></a>通过公司门户应用“主页”删除  

1. 打开公司门户应用。
2. 在“主页”上，转到“我的设备”部分。
3. 选择要删除的设备。
3. 在顶部（应用的右上角），选择“查看更多”图标。
4. 选择“删除”。 
5. 要确认删除设备，请选择“删除”。  

### <a name="remove-in-company-portal-app-device-context-menu"></a>通过公司门户应用的设备上下文菜单删除  

1. 打开公司门户应用并转到“我的设备”。

    ![适用于 Windows 的公司门户应用的“主页”示例屏幕截图，其中突出显示了“我的设备”部分。](./media/1809_CheckAccess_Context_Select_Device.png)

2. 右键单击或按住某个设备，打开其[上下文菜单](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus)。  

3. 选择“删除”。  

    ![适用于 Windows 的公司门户应用的“主页”示例屏幕截图。 设备上下文菜单显示在该页面的“我的设备”部分，其中包括“重命名”、“删除”和“检查访问”操作。](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. 在确认过程中，单击“了解更多”，了解对工作和学校资源的访问可能会发生什么变化。 要确认删除设备，请选择“删除”。   

     ![适用于 Windows 的公司门户应用的“主页”示例屏幕截图。 “重命名”字段显示在设备上，用户可在其中键入新名称，然后单击“重命名”或“取消”。](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>通过设备设置应用删除
1. 打开设置应用。 
2. 转至“帐户” > “访问工作或学校”。
3. 选择想要删除的已连接帐户 >“断开连接”。
4. 若要确认删除设备，请选择“是”。

## <a name="remove-your-windows-81-computer"></a>删除 Windows 8.1 计算机
完成以下步骤以从 Intune 删除 Windows 8.1 计算机。

1.  依次转至“电脑设置” > “网络” > “工作区”。
2.  在“工作区加入”下，选择“退出”。
3.  在“打开设备管理”下，选择“关闭”。
4.  在打开的弹出窗口中，选择“关闭”。

## <a name="remove-your-windows-81-phone"></a>删除 Windows 8.1 手机
完成以下步骤，从 Intune 删除 Windows 8.1 手机。

1.  转到“设置” > “工作区”。
2.  点击要取消注册的工作区帐户。
3.  点击屏幕底部的“删除”。
4.  在“删除帐户”对话框中，点击“删除”。  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>删除公司门户后删除个人信息  

公司门户在 Windows 设备上存储的数据分为两种：

-   **诊断日志**：Microsoft 收集的标准应用活动数据。 卸载公司门户应用时，它会自动清除。 例如，应用活动数据是有关应用打开了多长时间或应用是否已损坏的数据。
-   应用程序缓存：应用正常工作所需的支持文件，例如图标和设置。

要删除存储的日志和缓存，请完成以下任一步骤：

* [卸载公司门户应用](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* 重置公司门户应用。 打开“设置”应用并选择 >“应用” > “公司门户” > “高级选项” > “重置”。 

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
