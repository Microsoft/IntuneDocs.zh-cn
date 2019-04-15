---
title: 使用 Microsoft Intune 激活 iOS 丢失模式 - Azure | Microsoft Docs
description: 使用 Microsoft Intune，启用或启动“丢失模式”，以自定义丢失或被盗 iOS 设备的锁屏界面上显示的消息。 并获取有关使用丢失模式时的安全与隐私信息。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66a3ba7d57d71aeb446bf86449f39c4a557eed62
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57392288"
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>使用 Intune 启用 iOS 设备上的丢失模式

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

“丢失模式”设备操作可帮助你在丢失或被盗的 iOS 设备上启用丢失模式。 通过此模式，可输入在设备锁屏界面上显示的消息和电话号码。 若要使用丢失模式，设备必须是处于监督模式下的公司拥有的 iOS 设备。

## <a name="supported-platforms"></a>受支持的平台

- iOS 9.3 及更高版本

以下系统不支持此功能： 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>启用丢失模式

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 依次选择“设备”和“所有设备”。
4. 从所管理设备的列表中，选择一个 iOS 设备，然后选择“...更多”。 然后选择“丢失模式”远程操作。
5. 在“丢失模式”下，启用此功能。 然后，输入要显示的消息和联系人电话号码。
6. 选择“确定”，保存所做更改。

启用丢失模式后，将阻止对该设备的所有使用。 最终用户无法访问设备，直到你禁用丢失模式。 尽管丢失模式已启用，但仍可使用[定位设备](device-locate.md)操作找到设备。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>丢失模式的安全与隐私信息和查找设备操作
- 启用此操作之前，不会向 Intune 发送任何设备的位置信息。
- 使用“定位设备”操作时，设备的纬度和经度坐标会发送到 Intune，并在 Azure 门户中显示。
- 该数据存储 24 小时，然后删除。 不能手动删除位置数据。
- 位置数据在存储和传输时均进行加密处理。
- 在输入的要在锁屏界面上显示的消息中，请务必添加特定的详细信息，以返回丢失的设备。

## <a name="next-steps"></a>后续步骤

若要查看“丢失模式”的启用状态，请打开“设备”，然后选择“设备操作”。
