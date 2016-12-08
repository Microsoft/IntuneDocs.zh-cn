---
title: "Exchange ActiveSync 设备管理 | Microsoft Intune"
description: "通过 Exchange Connector 使用 Exchange ActiveSync (EAS) 管理来管理移动设备"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 1b26e1298cf0b65f99219338b7ba59987e70c3ab


---

# <a name="exchange-activesync-mobile-device-management-with-microsoft-intune"></a>使用 Microsoft Intune 管理 Exchange ActiveSync 移动设备
若要使用 Microsoft Intune 直接管理移动设备，则必须[在 Intune 中注册](prerequisites-for-enrollment.md)设备。 或者，管理员可以启用限制更多的管理解决方案，该解决方案通过 Exchange 连接器使用 Exchange ActiveSync (EAS) 管理。 使用 Office 365，可以通过本地 Exchange 服务器或 Exchange Online 管理设备。 Intune 仅支持每个订阅中存在一个任意类型的 Exchange 连接器连接。

## <a name="exchange-access-rules-for-mobile-devices"></a>移动设备的 Exchange 访问规则 ##

Exchange 需要一组规则，这些规则用于定义当移动设备尝试连接到 EAS 时会发生什么情况。 这些规则在 Intune 管理控制台中管理。

[移动设备的 Exchange 访问规则](exchange-access-rules-for-mobile-devices.md)

## <a name="install-the-exchange-connector"></a>安装 Exchange Connector
通过 Exchange Connector 你可以在 Intune 控制台中管理 Exchange 部署。 必须先安装并设置合适的 Intune 到 Exchange 连接器。 根据 Exchange 服务器是在本地还是作为服务托管在云中来选择合适的选项：

-   [为 Exchange Online 或新 Exchange Online Dedicated 环境配置 Intune](intune-service-to-service-exchange-connector.md)
-   [安装适用于本地 Exchange 服务器和旧版 Exchange Online Dedicated 环境的 Intune 连接器](intune-on-premises-exchange-connector.md)


## <a name="apply-policy-for-exchange-managed-mobile-devices"></a>将策略应用于 Exchange 管理的移动设备
Intune 控制台可用于管理 [EAS 策略设置](exchange-activesync-policy-settings-in-microsoft-intune.md)和[限制对公司资源的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。 有关特定移动设备所支持的 Exchange ActiveSync 策略设置和功能的列表，请参阅 [Exchange ActiveSync Client Comparison Table](http://go.microsoft.com/fwlink/?LinkId=247270)（Exchange ActiveSync 客户端对照表）。

> [!NOTE]
> 将 Intune 连接到 Microsoft Exchange 环境后，针对通过 Intune 管理的所有用户的 EAS 策略将重置为 Microsoft Exchange 服务器上的当前的默认策略，除非在 Intune 中定义了更加具体的策略。

## <a name="wipe-company-data-from-mobile-devices"></a>从移动设备中擦除公司数据
最后，如果公司数据不再使用，或者如果设备丢失或被盗，则可以[从 EAS 管理的移动设备中擦除公司数据](wipe-for-exchange-managed-mobile-devices.md)。



<!--HONumber=Nov16_HO1-->


