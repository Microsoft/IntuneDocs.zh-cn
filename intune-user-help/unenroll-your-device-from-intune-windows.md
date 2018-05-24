---
title: 从 Intune 删除 Windows 设备
description: 介绍如何从 Intune 删除 Windows 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/08/2018
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
ms.openlocfilehash: a3cad6a73b3455790441c594933d599b2c6e89f9
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="remove-your-windows-device-from-intune-management"></a>删除 Intune 对 Windows 设备的管理

当你不再希望或不再需要使用以下功能时，请从 Intune 删除已注册的 Windows 设备：  
* 将设备用于工作或学校。 
* 访问工作或学校电子邮件、应用或其他资源。

设备被删除后，你将无法通过该设备访问学校或工作资源。 可从 Intune 删除的 Windows 设备包括：  
* Windows 10 设备 
* Windows 8.1 计算机
* WIndows 8.1 移动设备
 
若要深入了解删除 Intune 对设备的管理后会发生什么情况，请参阅[从 Intune 删除设备会发生什么情况？](what-happens-if-you-unenroll-your-device-from-intune-windows.md)。

## <a name="remove-your-windows-10-device"></a>删除 Windows 10 设备
完成以下步骤以从 Intune 删除 Windows 10 设备。

### <a name="via-the-company-portal-app"></a>通过公司门户应用

1. 打开公司门户应用。
2. 使用工作单位或学校凭据登录。
3. 在“我的设备”中，选择要删除的设备。
4. 在顶部（应用的右上角），选择“查看更多”图标。
5. 选择“删除”。 
6. 若要确认删除设备，请选择“删除设备”。

### <a name="via-device-settings-app"></a>通过设备设置应用
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

## <a name="remove-your-windows-81-mobile-device"></a>删除 Windows 8.1 移动设备
完成以下步骤以从 Intune 删除 Windows 8.1 移动设备。

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

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
