---
title: "手动同步 Windows 设备 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 443c6de7-5187-4dc4-b844-6085a0c659bd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9ddbcde20fac83289c4622f69538ff00fa0cb65b
ms.openlocfilehash: 2fad0ea18485290a513d175fecf0a4947786e5eb


---


# <a name="sync-your-windows-device-manually"></a>手动同步 Windows 设备
如果你的应用安装所需时间过长，则可尝试手动同步 Windows 设备。 手动同步可能有助于加快安装速度。

仅支持以下版本。 如果未列出你的设备，则不支持同步。 请使用与你的设备类型相匹配的说明。

* [Windows 10 移动版](#windows-10-mobile)
* [Windows 10 桌面版](#windows-10-desktop)
* [Windows Phone 8.1](#windows-phone-8-1)


## <a name="windows-10-mobile"></a>Windows 10 移动版
若要手动同步你的 Windows 10 移动设备，以加快较慢的应用安装的速度：

1. 请转到**所有应用**  >  **设置**  >  **帐户**。

    ![在“设置”屏幕上选择帐户](./media/win10m-sync-1-settings-accounts.png)

2. 选择“工作单位访问”。

    ![选择工作单位访问作为帐户类型](./media/win10m-sync-2-work-access.png)

3. 在“注册到设备管理”下，选择你的公司名称。

    ![为设备管理选择公司名称](./media/win10m-sync-3-tap-comp-name.png)

4. 选择“同步”图标。

    ![选择“同步”图标](./media/win10m-sync-4-tap-sync.png)

    屏幕顶部将显示“我们正在同步你的帐户”消息。 设备完成同步前，“同步”按钮将灰显。

## <a name="windows-10-desktop"></a>Windows 10 桌面版
由于存在多个 Windows 10 版本，因此有两组步骤。 若要了解使用哪组步骤，可查看屏幕截图，然后按照设备上显示的步骤执行操作。 

1. 选择“启动”按钮，然后选择“设置”。

    ![“启动”按钮](./media/win10pc-sync-1-start-button.png)

2. 在“设置”页上，选择“帐户”。

    ![在“设置”页上选择帐户](./media/win10pc-sync-2-settings-accounts.png)

3. 查看接下来的两个屏幕，并找到与你在设备上看到的屏幕相似的屏幕。 按照与你在设备上看到的屏幕相匹配的步骤操作。

    如果看到显示有“访问工作单位或学校”的此屏幕，请按照[看到“访问工作单位或学校”时要执行的步骤](#steps-to-follow-if-you-see-access-work-or-school)中的说明操作。

    ![看到“访问工作单位或学校”时要执行的同步步骤](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    如果看到显示有“工作单位访问权限”的此屏幕，请按照[看到“工作单位访问权限”时要执行的步骤](#steps-to-follow-if-you-see-your-account)中的步骤操作。

    ![选择工作单位访问作为帐户类型](./media/win10pc-sync-3-work-access.png) 

### <a name="steps-to-follow-if-you-see-access-work-or-school"></a>看到“访问工作单位或学校”时要执行的步骤

1. 在“帐户”页上，选择“访问工作单位或学校”。

    ![选择“访问工作单位或学校”](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2. 选择工作或学校帐户。 根据 IT 管理员的设置方式，可能会看到与以下示例中类似的两个帐户。 一个帐户旁有一个公文包，另一个帐户旁有一个 Microsoft 徽标。 

    - 如果看到带有公文包的帐户，请选择它，并找到下面的“信息”按钮。 
    - 如果只看到带有 Microsoft 徽标的帐户，请选择该帐户，并找到下面的“信息”按钮。

    ![选择公文包或 Microsoft 徽标旁的帐户名](./media/win10pc-rs1-sync-info-button.png)

3. 选择“信息”按钮。 将打开一个与以下示例中类似的对话框。

    ![选择公文包或 Microsoft 徽标旁的帐户名](./media/win10pc-rs1-sync-button.png)

4. 选择“同步”按钮。 设备将与 Intune 进行同步。

### <a name="steps-to-follow-if-you-see-work-access"></a>看到“工作单位访问权限”时要执行的步骤
    
1. 在“帐户”页上，选择“工作单位访问”。

    ![选择工作单位访问作为帐户类型](./media/win10pc-sync-3-work-access.png)

2. 在“注册到设备管理”部分下，选择你的公司名称。

    ![为设备管理选择公司名称](./media/win10pc-sync-4-tap-com-name.png)

3. 选择“同步”按钮。

    ![选择“同步”按钮](./media/win10pc-sync-5-tap-sync.png)

   在同步完成之前，该按钮将变为灰显。

## <a name="windows-phone-81"></a>Windows Phone 8.1
若要手动同步你的 Windows Phone 8.1 设备，以加快较慢的应用安装的速度：

1. 请转到**所有应用**  >  **设置**  >  **工作区**。

    ![设置的列表](./media/wp81-1-sync-settings-workplace.png)

2. 选择你的公司名称。

    ![选择工作区帐户的公司名称](./media/wp81-2-sync-tap-compname.png)

3. 选择“同步”图标。

    ![选择“同步”图标](./media/wp81-3-sync-tap-sync-button.png)

   设备完成同步前，屏幕顶部将显示“我们正在同步你的帐户”消息。

仍需要帮助？ 请与 IT 管理员联系。 有关联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。



<!--HONumber=Nov16_HO1-->


