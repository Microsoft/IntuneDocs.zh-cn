---
title: "选择如何管理设备 | Microsoft Intune"
description: "了解让你可以注册和管理设备的各种方法。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c329bd08aaf72ae2acaa03dcb12c911d84b46b4e
ms.openlocfilehash: cfd9df3814d0d306a254a5566155a91ce5d0ca16


---

# 选择如何管理设备
Intune 允许你通过将一系列设备*注册*到服务来管理这些设备。 然后，用户可以使用*公司门户*来执行一系列操作，例如注册其设备，浏览和安装应用，确保其设备符合公司策略，以及联系其 IT 支持。

## 如何管理移动设备
Intune 可以管理以下设备平台：

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

> [!NOTE]
> 如果以前注册的设备运行的 iOS 版本早于受支持的版本，将保留这些设备的已注册状态。 请查看文档以确认此功能支持此版本的 iOS。

Intune 可以管理用户的设备，一般称为“自带设备办公”(BYOD)。 它还可以管理公司拥有的设备，包括公司提供用户可以从中进行选择的设备列表（称为“选择自己的设备”(CYOD)）的方案。

### 向管理系统注册设备
对于包括 iOS、Android 和 Windows Phone 在内的移动设备操作系统，你始终必须注册设备。 如何注册设备取决于你组织的需求：

|注册类型|BYOD|CYOD|带管理人员帐户的共享设备|无用户帐户的共享设备|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**说明**|使用 Microsoft Intune 注册的个人设备|适用于单个用户的公司拥有的设备|使用多个用户共享的管理人员帐户的公司拥有的设备|由多个用户使用的公司拥有的无用户设备。|
|**设备的用户**|Owner|分配的用户|没有特定于用户的帐户|未特定的用户|
|**谁注册？**|Owner|管理员|设备管理器|任何人|
|**谁注销？**|所有者或管理员|平台 |管理员或用户|管理员或用户|
|**谁可以重置？**|所有者或管理员|管理员|管理员|管理员|

有关其他指南，请参阅[选择如何注册移动设备](/intune/get-started/choose-how-to-enroll-devices1)。

> [!NOTE]
> 有关通过注册设备获得的功能的完整列表，请参阅[移动设备管理功能](mobile-device-management-capabilities-in-microsoft-intune.md)。

## 如何管理 Windows 电脑
Intune 可以使用 Intune 计算机客户端管理 Windows Vista 及更高版本的 Windows 电脑。 但是，对于 Windows 电脑，你可以选择注册它们，或者安装 Intune 电脑客户端软件（可提供注册设备时不可用的一些功能）。 在大多数情况下，你将向 Intune 注册 Windows 设备，这样可提供比计算机客户端更多的功能。

请考虑在以下情况下使用 Intune 计算机客户端：

- 使用任何 Microsoft Intune 计算机客户端启用的功能来管理 Windows 电脑
- 管理运行不支持注册的操作系统的 Windows 电脑

> [!NOTE]
> 有关通过在受支持的 Windows 电脑上安装 Intune 计算机客户端获得的功能的完整列表，请参阅 [Windows 电脑管理功能](windows-pc-management-capabilities-in-microsoft-intune.md)。

## Exchange ActiveSync 管理
你还可以使用 Exchange ActiveSync 来管理设备。 若要使用 Exchange ActiveSync 管理设备，你需要安装本地连接器或使用内置服务间连接器来连接到 Exchange Server。

若要了解有关安装本地连接器的硬件和软件要求的信息，请参阅[本地连接器的要求](/intune/deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connector)。

若要了解有关将本地连接器或服务间连接器与 Exchange 配合使用的信息，请参阅[使用 Exchange ActiveSync 和 Microsoft Intune 管理移动设备](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)。



## 后续步骤
你已经了解向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 注册设备后可使用的一些功能。 接下来，你需要[注册设备](/intune/deploy-use/enroll-devices-in-microsoft-intune)。 注册设备后，你就可以利用你在本主题中了解到的所有功能。 <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->



<!--HONumber=Aug16_HO3-->


