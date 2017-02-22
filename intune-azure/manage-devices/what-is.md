---
title: "使用 Intune 管理设备 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何查看使用 Intune 管理的设备，并在设备上执行各种操作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 040c4e18d87110ab7380a64540d08127574a7c46
ms.openlocfilehash: 5a967cc1be387f83f95591186f786db61d3debcd


---

# <a name="what-is-device-management"></a>什么是设备管理？ 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

“设备和组”工作负荷可以让你了解所管理的设备，并能在这些设备上执行远程任务。 若要访问工作负荷，请执行以下操作：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备和组”。

    ![设备和组工作负荷](./media/devices-and-groups-workload.png)

现在，选择以下选项之一：

- **概述** 获得有关已注册设备的信息，以及每个设备运行的操作系统的相关信息。
- **管理** - 选择“所有设备”查看所管理的所有设备列表。
    选择列表中的某个设备，打开<设备名称> “概述”边栏选项卡，可在其中选择下列选项之一：
    - **概述** - 查看有关设备的常规信息，包括设备名称、所有者、是否是 BYOD 设备、上次登录时间等。 此外，还可以在设备上执行以下远程操作（并非所有设备平台都支持所有操作）：
        - **删除公司数据** - 只删除由 Intune 管理的公司数据。 不会删除设备中的个人数据。 该设备将不再由 Intune 管理，并且将不再能够访问公司资源（不受加入 Azure Active Directory 的 Windows 设备的支持）。
        - **恢复出厂设置** - 将设备恢复为其默认设置。 Intune 将不再管理该设备，并且公司和个人数据都将被删除。 不能撤消此操作。
        - **远程锁定** - 锁定该设备。 设备所有者必须使用其密码才能解锁设备。 只能远程锁定设置了 PIN 或密码的设备。
        - **重置密码** - 为设备生成一个新密码，新密码将显示在 <设备名称> “概述”边栏选项卡上。
        - **绕过激活锁** - 此功能无需用户的 Apple ID 和密码即可删除 iOS 设备中的激活锁。 绕过激活锁后，启动“查找 iPhone”应用时设备将再次打开激活锁。 请仅在拥有对设备的物理访问权限的情况下绕过激活锁。
        - **丢失模式** - 设备被盗时可以启用丢失模式。 通过该模式可以指定在设备的锁定屏幕上显示的信息和电话号码。
        - **重新启动** - 将重新启动设备。 设备所有者不会获得重新启动的自动通知，因此工作可能丢失。
        ![设备概述](http://i.imgur.com/4Rx4VXm.png)
        
    - **硬件** - 请查看有关设备的详细信息，包括其可用存储空间、型号和制造商等。
    ![托管设备硬件清单](./media/hardware-inventory.png)
    - **检测到的应用程序** - 显示 Intune 发现的安装在设备上的所有应用列表。
    ![检测到的应用程序节点](./media/detected-applications.png)
- **监视** 选择“设备操作”查看在所管理的设备上执行的设备操作列表，以及这些操作的当前状态。
![监视设备操作](./media/monitor-device-actions.png)



<!--HONumber=Feb17_HO1-->


