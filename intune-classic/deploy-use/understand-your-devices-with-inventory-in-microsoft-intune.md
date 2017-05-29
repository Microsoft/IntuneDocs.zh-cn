---
title: "通过清单了解设备 | Microsoft Docs"
description: "使用 Intune 查看你管理的设备的硬件的相关信息。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 59b6a72a17490d7c4aada6bee5caaaac2ba0979c
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="understand-your-devices-with-inventory-in-microsoft-intune"></a>在 Microsoft Intune 中了解你的设备清单

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

通过 Microsoft Intune，你可查看运行 Intune 客户端软件的已注册设备和 Windows 电脑的清单。
Intune 通常每隔 7 天从受管理设备收集一次清单。 因此，在报表显示最近对设备进行的任何更改（例如，对设备名称的更改，或对免费存储空间的更改）的结果前可能会有一定的延迟。

## <a name="whats-collected-from-enrolled-devices"></a>从已注册的设备中收集了哪些信息？
若要查看移动设备收集的清单，请运行[移动设备清单报表](understand-microsoft-intune-operations-by-using-reports.md)。 Intune 将从已注册设备收集以下清单：

|属性|收集方|
|------------|-----------------------|
|**Name**|“所有设备”|
|**操作系统**|“所有设备”|
|**制造商**|“所有设备”|
|**型号**|“所有设备”|
|**管理通道**|“所有设备”|
|**已注册 AAD**|Mac OS X 以外的所有设备|
|**符合**|“所有设备”|
|**已激活 EAS**|Mac OS X 以外的所有设备|
|**EAS 激活 ID**|Mac OS X 以外的所有设备|
|**EAS 激活时间**|Mac OS X 以外的所有设备|
|**管理状态**|“所有设备”|
|**电子邮件地址**|“所有设备”|
|**Exchange ActiveSync ID**|“所有设备”|
|**已越狱或取得 root 权限**|仅限 iOS 和 Android 设备|
|**唯一设备 ID**|Exchange ActiveSync 以外的所有设备|
|**序列号**|iOS、Mac OS X、Android、Windows 8.1 和 Windows 10 桌面版设备|
|**总存储空间**|iOS、Mac OS X、Windows 8.1 和 Windows 10 桌面版和移动版设备|
|**可用存储空间**|iOS、Mac OS X、Windows 8.1 和 Windows 10 桌面版设备|
|**电话号码**<br>归类为企业的电话将以其完整的电话号码进行标识（例如在运行移动设备清单报表时）。 将使用 &#42 屏蔽 BYOD 电话号码；仅显示最后 4 位数字。|iOS、Android 和 Windows Phone 设备|
|**IMEI**|Exchange ActiveSync、iOS、Android 和 Windows Phone 设备|
|**MEID**<br>移动设备标识符|仅限 iOS 设备|
|**Wi-Fi MAC**|Exchange ActiveSync 以外的所有设备|
|**订阅者运营商**|仅限 iOS 和 Android 设备|
|**手机网络技术**|仅限 iOS 和 Android 设备|
|**受监督**|仅限 iOS 设备|
|**激活锁状态**|仅限 iOS 设备|
|**注册日期**|“所有设备”|
|**上次更新时间**|“所有设备”|
|**以太网 MAC**|仅限 Mac OS X 设备|
|**已启用激活锁**|仅限 iOS 设备|
|**已启用加密**|“所有设备”|

## <a name="whats-collected-from-windows-pcs"></a>从 Windows 电脑收集了哪些信息？
> [!IMPORTANT]
> 本部分仅适用于运行 Intune Windows 电脑客户端软件的 Windows 电脑。

若要查看 Windows 电脑收集的清单，请运行[计算机清单报表](understand-microsoft-intune-operations-by-using-reports.md)。 Intune 将从 Windows 电脑收集以下清单：

-   **Name**

-   **底盘类型**

-   **制造商**

-   **型号**

-   **操作系统**

-   **TPM 版本**

-   **总磁盘空间**

-   **已用的磁盘空间**

-   **可用磁盘空间**

-   **OS 磁盘名称**

-   **OS 磁盘空间**

-   **OS 磁盘可用空间**

-   **物理内存**

-   **处理器名称**

-   **处理器体系结构**

-   **CPU 速度**

-   **IP 地址**

-   **序列号**

-   **上一个登录的用户**

-   **分配的用户**

-   **上次更新时间**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->

