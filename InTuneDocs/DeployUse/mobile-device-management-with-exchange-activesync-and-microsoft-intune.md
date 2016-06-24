---
# required metadata

title: 使用 Exchange ActiveSync 和 Microsoft Intune 管理移动设备 | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Exchange ActiveSync 和 Microsoft Intune 管理移动设备
要使用 Microsoft Intune 直接管理移动设备，用户必须在 Intune 中注册设备。 对于用户未注册的移动设备，你可以使用 Exchange Connector 启用 Exchange ActiveSync (EAS) 管理。 可以使用本地 Exchange 服务器和 Microsoft Office 365 上的云托管 Exchange 管理设备。

## 移动设备的 Exchange 访问规则 ##

Exchange 需要一组规则，这些规则用于定义当移动设备尝试连接到 EAS 时会发生什么情况。 这些规则在 Intune 管理控制台中管理。

[移动设备的 Exchange 访问规则](exchange-access-rules-for-mobile-devices.md)

## 安装 Exchange Connector
通过 Exchange Connector 你可以在 Intune 控制台中管理 Exchange 部署。 你必须首先安装并配置合适的 Intune 到 Exchange 连接器。 根据你的 Exchange 服务器是在本地还是作为服务在云中托管来选择合适的选项：

-   [为本地 Exchange 安装 Intune 连接器](intune-on-premises-exchange-connector.md)
-   [将 Intune 服务配置为托管 Exchange 的服务连接器](intune-service-to-service-exchange-connector.md)

## 将策略应用于 Exchange 管理的移动设备
可以通过 Intune 控制台应用策略设置，请参阅 [Manage settings and features on your devices with Microsoft Intune policies（使用 Microsoft Intune 策略管理设备上的设置和功能）](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。 有关特定移动设备所支持的 Exchange ActiveSync 策略设置和功能的详细列表，请参阅 [Exchange ActiveSync Client Comparison Table（Exchange ActiveSync 客户端对照表）](http://go.microsoft.com/fwlink/?LinkId=247270)。

> 将 Intune 连接到 Microsoft Exchange 环境后，针对通过 Intune 管理的所有用户的 EAS 策略将重置为 Microsoft Exchange 服务器上的当前的默认策略，除非在 Intune 中定义了更加具体的策略。

## 从移动设备中擦除公司数据
最后，如果公司数据不再使用，或者如果设备丢失或被盗，则可以[从 EAS 管理的移动设备中擦除公司数据](wipe-for-exchange-managed-mobile-devices.md)。


<!--HONumber=May16_HO2-->


