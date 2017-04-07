---
title: "利用 Intune 来管理设备"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何查看使用 Intune 管理的设备，并在设备上执行各种操作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 671d862c8d9a98e02f33d96cf6ceba712e740dec
ms.openlocfilehash: 8a43e1646476696b978a7f8a3e92f920606a698b
ms.lasthandoff: 03/17/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>什么是 Microsoft Intune 设备管理？ 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

**设备**工作负荷可以让你了解所管理的设备，并能在这些设备上执行远程任务。 若要访问工作负荷，请执行以下操作：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。

现在，选择以下选项之一：

- **概述** 获得有关已注册设备的信息，以及每个设备运行的操作系统的相关信息。
- **管理** - 选择“所有设备”查看所管理的所有设备列表。
    选择列表中的某个设备，打开<设备名称> “概述”边栏选项卡，可在其中选择下列选项之一：
    - **概述** - 查看有关设备的常规信息，包括设备名称、所有者、是否是 BYOD 设备、上次登录时间等。 
                
    - **硬件** - 请查看有关设备的详细信息，包括其可用存储空间、型号和制造商等。
    ![托管设备硬件清单](./media/hardware-inventory.png)
    - **检测到的应用程序** - 显示 Intune 发现的安装在设备上的所有应用列表。
    ![检测到的应用程序节点](./media/detected-applications.png)
- **监视** 选择“设备操作”查看在所管理的设备上执行的设备操作列表，以及这些操作的当前状态。
![监视设备操作](./media/monitor-device-actions.png)
- **帮助和支持** - 显示故障排除和支持文档的链接。

## <a name="available-device-actions"></a>可用的设备操作

此外，还可以在设备上执行以下远程操作（并非所有设备平台都支持所有操作）：

### <a name="remove-company-data"></a>**删除公司数据**
只删除由 Intune 管理的公司数据。 不会删除设备中的个人数据。 该设备将不再由 Intune 管理，并且将不再能够访问公司资源（不受加入 Azure Active Directory 的 Windows 设备的支持）。

### <a name="factory-reset"></a>**恢复出厂设置**
将设备恢复为其默认设置。 Intune 将不再管理该设备，并且公司和个人数据都将被删除。 不能撤消此操作。

### <a name="remote-lock"></a>**远程锁定**
锁定设备。 设备所有者必须使用其密码才能解锁设备。 只能远程锁定设置了 PIN 或密码的设备。

### <a name="reset-passcode"></a>**重置密码**
为设备生成一个新密码，新密码将显示在<“*设备名称*”> “**概述**”边栏选项卡上。

### <a name="bypass-activation-lock"></a>**绕过激活锁**
此功能无需用户的 Apple ID 和密码即可删除 iOS 设备中的激活锁。 绕过激活锁后，启动“查找 iPhone”应用时设备将再次打开激活锁。 请仅在拥有对设备的物理访问权限的情况下绕过激活锁。

### <a name="lost-mode"></a>**丢失模式**
iOS 设备丢失或被盗时，可以启用丢失模式。 通过该模式可以指定在设备的锁定屏幕上显示的信息和电话号码。 为此，请执行以下操作：
1.    在 iOS 设备的属性边栏选项卡上，选择“**更多**” > “**丢失模式**”。
2.    在“**丢失模式**”边栏选项卡上，启用丢失模式，输入将要显示的消息，以及联系电话号码（可选）。
3.    单击" **确定**"。
启用丢失模式时，将阻止对该设备的所有使用。 最终用户无法访问设备，直到你禁用丢失模式。 虽然丢失模式已启用，但可以使用**查找设备**操作找到设备所在的位置。
要使用丢失模式，此设备必须是处于监督模式下通过 EDP 注册的公司所有的 iOS 设备。

### <a name="locate-device"></a>**查找设备**
使用此远程操作在地图上显示丢失或被盗 iOS 设备的位置。 此设备必须是处于监督模式下通过 EDP 注册的公司所有的 iOS 设备。 使用此操作之前，必须将此设备置于丢失模式。
1.    在 iOS 设备的属性边栏选项卡上，选择“**更多**” > “**查找设备**”。
2.    找到设备后，**查找设备**边栏选项卡上会显示其位置。 
    ![查找设备边栏选项卡](./media/locate-device.png)

### <a name="restart"></a>**重新启动**
将重新启动设备。 设备所有者不会获得重新启动的自动通知，因此工作可能丢失。


## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>丢失模式的安全与隐私信息和查找设备操作
- 在开启此操作之前，任何设备的位置信息都不会发送到 Intune。
- 使用查找设备操作时，设备的纬度和经度坐标会发送到 Intune，并在 Azure 门户中显示。
- 该数据存储 24 小时，然后删除。 不能手动删除位置数据。
- 位置数据在存储和传输时均进行加密处理。
- 在配置丢失模式时，我们建议在锁定屏幕上显示的输入消息中加入可确定设备位置的信息。

