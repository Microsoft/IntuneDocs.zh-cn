---
title: "了解你的设备清单 | Microsoft Intune"
description: "使用 Intune 查看你管理的设备的硬件的相关信息。"
keywords: 
author: robstackmsft
manager: arob98
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a409d36c1c5fcfd3d81ce0cbdf1f69af4747157a
ms.openlocfilehash: 669e096735ae7123123873dad8982abf2c4c38d6


---

# 在 Microsoft Intune 中了解你的设备清单
通过 Microsoft Intune，你可查看运行 Intune 客户端软件的已注册设备和 Windows 电脑的清单。

## 从已注册的设备中收集了哪些信息？
若要查看移动设备收集的清单，请运行[移动设备清单报表](understand-microsoft-intune-operations-by-using-reports.md)。 Intune 将从已注册设备收集以下清单：

|属性|收集方|
|------------|-----------------------|
|**Name**|“所有设备”|
|**操作系统**|“所有设备”|
|**制造商**|“所有设备”|
|**型号**|“所有设备”|
|**管理通道**|“所有设备”|
|**已向 ADD 注册**|Mac OS X 以外的所有设备|
|**是否满足条件**|“所有设备”|
|**已激活 EAS**|Mac OS X 以外的所有设备|
|**EAS 激活 ID**|Mac OS X 以外的所有设备|
|**EAS 激活时间**|Mac OS X 以外的所有设备|
|**管理状态**|“所有设备”|
|**电子邮件地址**|“所有设备”|
|**Exchange ActiveSync ID**|“所有设备”|
|**已越狱或取得 root 权限**|仅限 iOS 和 Android 设备|
|**唯一的设备 ID**|Exchange ActiveSync 以外的所有设备|
|**序列号**|iOS、Mac OS X、Android、Windows 8.1、Windows 10 设备|
|**总存储空间**|iOS、Mac OS X、Windows 8.1、Windows 10 设备|
|**可用存储空间**|iOS、Mac OS X、Windows 8.1、Windows 10 设备|
|**电话号码**<br>例如在运行移动设备清单报表时，归类为企业的手机将以其完整电话号码进行标识。 BYOD 电话号码将使用 &#42屏蔽；仅显示最后 4 位数字。|iOS、Android 和 Windows Phone 设备|
|**IMEI**|Exchange ActiveSync、iOS、Android 和 Windows Phone 设备|
|**MEID**<br>移动设备标识符|仅限 iOS 设备|
|**Wi-Fi MAC**|Exchange ActiveSync 以外的所有设备|
|**用户载波**|仅限 iOS 和 Android 设备|
|**移动电话技术**|仅限 iOS 和 Android 设备|
|**受到监督**|仅限 iOS 设备|
|**激活锁定状态**|仅限 iOS 设备|
|**注册日期**|“所有设备”|
|**上次更新时间**|“所有设备”|
|**以太网 MAC**|仅限 Mac OS X 设备|
|**已启用激活锁定**|仅限 iOS 设备|
|**已启用加密**|“所有设备”|

## 从 Windows 电脑收集的信息
> [!IMPORTANT]
> 本部分仅适用于运行 Intune Windows 电脑客户端软件的 Windows 电脑。

若要查看 Windows 电脑收集的清单，请运行[计算机清单报表](understand-microsoft-intune-operations-by-using-reports.md)。 Intune 将从 Windows 电脑收集以下清单：

-   **Name**

-   **底盘类型**

-   **制造商**

-   **型号**

-   **操作系统**

-   **TPM 版本**

-   **磁盘空间总计**

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



<!--HONumber=Jul16_HO3-->


