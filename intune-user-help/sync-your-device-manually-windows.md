---
title: 手动同步 Windows 设备 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328ec3111aae5f8363f2743d423a56eafc47d765
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546255"
---
# <a name="sync-your-windows-device-manually"></a>手动同步 Windows 设备

当应用程序安装速度不理想时，启动手动设备同步。手动同步强制你的设备与 Intune 连接，以获取最新的更新和通信。 设备同步完成后，安装速度可能会提升。

Intune 支持从公司门户应用、桌面任务栏或“开始”菜单以及从设备设置应用进行手动同步。 在运行 Creator 的 Update (1703) 或更高版本的 Windows 10 设备上支持公司门户应用功能。 

所有 Windows 设备都可以从设备设置应用中同步，其中包括：

* [Windows 10 桌面版](#windows-10-desktop)  
* [Microsoft HoloLens](#microsoft-hololens)   
* [Windows 10 移动版](#windows-10-mobile)  
* [Windows Phone 8.1](#windows-phone-81)    

## <a name="sync-directly-from-company-portal-app-for-windows"></a>直接从适用于 Windows 的公司门户应用同步
完成这些步骤，以手动同步运行 Creator 的 Update（版本 1703）或更高版本的 Windows 10 设备。

1. 在设备上打开公司门户应用。

2. 选择“设置”   > “同步”  。

    ![公司门户应用主页的屏幕截图，突出显示“设置”](./media/RS1_homePage_settings_04.png)  
    
    ![公司门户应用设置页的屏幕截图，突出显示“同步”按钮](./media/RS1_settingspage_sync05.png)  

## <a name="sync-from-device-taskbar-or-start-menu"></a>从设备任务栏或“开始”菜单进行同步   

还可从设备桌面，也即从应用外部访问同步控件。 如果已将应用直接固定到任务栏或开始菜单中，并且想要快速进行同步，可使用这种方式。  

1. 在任务栏或开始菜单中找到公司门户应用图标。  
2. 右键单击应用图标，以显示其菜单（也称为跳转列表）。  

    ![设备桌面上 Windows 任务栏的屏幕截图。 已单击公司门户应用图标，以显示带有“固定到任务栏”、“关闭窗口”和“同步此设备”操作选项的菜单。](./media/sync-device-from-start-menu-1807.png)  

3. 选择“同步此设备”  。 公司门户应用随即打开“设置”页面并启动同步  。  

## <a name="sync-from-settings-app"></a>从设置应用同步 
完成这些步骤，以手动从设置应用同步 Microsoft HoloLens、Windows 10 桌面版、Windows 10 移动版或 Windows Phone 8.1 设备。  

### <a name="windows-10-desktop"></a>Windows 10 桌面版
1. 在设备上，选择“启动”   > “设置”  。

2. 选择“帐户”  。

    ![在“设置”页上选择帐户](./media/win10pc-sync-2-settings-accounts.png)  

3. 在桌面上存在多个 Windows 10 版本。 将你的屏幕与以下屏幕截图比较，以确定执行哪组步骤。 

    * 如果你的屏幕显示的是访问工作单位或学校  ，则跳过[访问工作单位或学校](#access-work-or-school-steps)中的步骤。

    ![访问设置应用中的工作单位或学校选项](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

    * 如果你的屏幕显示的是工作单位访问  ，则跳过[工作单位访问](#work-access-steps)下的步骤。  

    ![选择工作单位访问作为帐户类型](./media/win10pc-sync-3-work-access.png)

#### <a name="access-work-or-school-steps"></a>访问工作单位或学校步骤

1. 单击“访问工作单位或学校”  。

    ![显示访问工作单位或学校选项的屏幕截图](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

2. 选择帐户旁边有公文包图标的帐户。 如果根本看不到此帐户，可能公司使用不同的方法配置了你的设置。 改为单击帐户旁边有 Microsoft 徽标的帐户。

     ![选择公文包或 Microsoft 徽标旁的帐户名](./media/win10pc-rs1-sync-info-button.png)

3. 单击“信息”  。 

4. 单击“同步”  。 

#### <a name="work-access-steps"></a>工作单位访问步骤

1. 单击“工作单位访问”  。

    ![选择工作单位访问作为帐户类型](./media/win10pc-sync-3-work-access.png)

2. 在“注册到设备管理”  下，选择你公司的名称。

    ![为设备管理选择公司名称](./media/win10pc-sync-4-tap-com-name.png)

3. 单击“同步”  。在同步完成前，该按钮是禁用的。

    ![选择“同步”按钮](./media/win10pc-sync-5-tap-sync.png)  


### <a name="windows-10-mobile"></a>Windows 10 移动版

   1. 在设备上，转到“所有应用”   > “设置”   > “帐户”  。

       ![在“设置”屏幕上选择帐户](./media/win10m-sync-1-settings-accounts.png)

   2. 选择“工作单位访问”  。

       ![选择工作单位访问作为帐户类型](./media/win10m-sync-2-work-access.png)

   3. 在“注册到设备管理”  下，选择你公司的名称。

       ![为设备管理选择公司名称](./media/win10m-sync-3-tap-comp-name.png)

   4. 选择“同步”  图标。 在同步完成前，该按钮是禁用的。

       ![选择“同步”图标](./media/win10m-sync-4-tap-sync.png)  
### <a name="microsoft-hololens"></a>Microsoft HoloLens  
这些说明适用于运行 Windows 10 Anniversary Update（也称为 RS1）的 HoloLens 设备。 
1. 在你的设备上打开设置应用。  

2. 选择“帐户”   > “工作单位访问”  。  
    ![HoloLens 设置应用截图，突出显示帐户链接](./media/RS1_holoLens_SettingsRS1_Accounts_06.png)  

3. 选择连接的帐户 >“同步”  。![HoloLens 设置应用截图，突出显示同步按钮](./media/RS1_holoLens_SyncRS1_Sync_08.png)  

### <a name="windows-phone-81"></a>Windows Phone 8.1

1. 请转到**所有应用**  >  **设置**  >  **工作区**。

    ![设置的列表](./media/wp81-1-sync-settings-workplace.png)

2. 选择你公司的名称。

    ![选择工作区帐户的公司名称](./media/wp81-2-sync-tap-compname.png)

3. 选择“同步”  图标。

    ![选择“同步”图标](./media/wp81-3-sync-tap-sync-button.png)

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
