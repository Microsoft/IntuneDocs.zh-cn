---
title: 使用 Microsoft Intune 重置 Windows 10 设备 - Azure | Microsoft Docs
description: 通过 Microsoft Intune 使用“全新启动”删除或卸载 Windows 10 电脑的应用。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1eb1e671cc16196974cb15cdc785ba7d99fa8f46
ms.sourcegitcommit: 4bd992da609b8bcc85edc2d64fe8128546aa4617
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55303406"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>使用“全新启动”重置使用 Intune 的 Windows 10 设备


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

“全新启动”设备操作将删除在运行 Windows 10 版本 1703 或更高版本的电脑上安装的所有应用。 “全新启动”有助于删除新电脑通常安装的预安装 (OEM) 应用。  

1. 登录到 [Azure 门户](https://portal.azure.com)，然后转到 >“Microsoft Intune” > “设备” > “所有设备”。
2. 从管理的设备列表中，选择一个 Windows 10 桌面设备。
3. 单击“全新启动”。 
4. 选择“在此设备上保留用户数据”以：
   * 保持设备加入 Azure AD
    * 启用 Azure Active Directory 的用户登录设备时，设备会再次注册到移动设备管理中。
    * 保留设备用户的主文件夹的内容并删除应用和设置  
  > [!IMPORTANT]
 > 如果不保留用户数据，设备将还原到其全新状态。 BYOD 设备将从 Azure AD 和移动设备管理中取消注册。
 > 启用 Azure Active Directory 的用户登录设备时，已联接 Azure AD 设备会再次注册到移动设备管理中。
 
5. 单击" **确定**"。   
6. 若要查看此操作的状态，请返回到“设备”，然后单击“设备操作”。  
