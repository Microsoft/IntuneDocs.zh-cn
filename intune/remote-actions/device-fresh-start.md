---
title: 使用 Microsoft Intune 重置 Windows 10 设备 - Azure | Microsoft Docs
description: 通过 Microsoft Intune 使用“全新启动”删除或卸载 Windows 10 电脑的应用。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e48b7dac5064f9daeb62e141a4c1b2a4adf11b7
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782193"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>使用“全新启动”重置使用 Intune 的 Windows 10 设备


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

“全新启动”设备操作将删除在运行 Windows 10 版本 1703 或更高版本的电脑上安装的所有应用  。 “全新启动”有助于删除新电脑通常安装的预安装 (OEM) 应用。 

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，选择“设备”   > “所有设备”  。
2. 从管理的设备列表中，选择一个 Windows 10 桌面设备。
3. 单击“全新启动”  。 
4. 选择“在此设备上保留用户数据”  以：
   * 保持设备加入 Azure AD
   * 启用 Azure Active Directory 的用户登录设备时，设备会再次注册到移动设备管理中。
   * 保留设备用户的主文件夹的内容并删除应用和设置

  > [!IMPORTANT]
 > 如果不保留用户数据，则设备将还原为默认的 OOBE（全新体验）已完成状态，并保留内置管理员帐户。
 > BYOD 设备将从 Azure AD 和移动设备管理中取消注册。
 > 启用 Azure Active Directory 的用户登录设备时，已联接 Azure AD 设备会再次注册到移动设备管理中。
 
5. 单击" **确定**"。   
6. 若要查看此操作的状态，请返回到“设备”  ，然后单击“设备操作”  。  
7. 设备将还原到初始登录屏幕。
