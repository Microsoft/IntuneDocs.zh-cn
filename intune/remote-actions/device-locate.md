---
title: 使用 Microsoft Intune 查找丢失的 iOS 设备 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 中的定位设备功能查找丢失或被盗的 iOS 设备。 获取使用“定位设备”操作时的安全与隐私相关详细信息。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c438ebeaae8a7259efb74089f51a6ca92003cfea
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509475"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>使用 Intune 定位丢失或被盗的 iOS 设备

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

若要在地图上获取丢失或被盗 iOS 设备的位置，请使用“定位设备”操作  。 设备必须处于监管模式。 使用此操作之前，请确保设备处于[丢失模式](device-lost-mode.md)。

## <a name="supported-platforms"></a>受支持的平台

- iOS 9.3 及更高版本

以下系统不支持此功能： 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>定位丢失或被盗的设备

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 依次选择“设备”和“所有设备”   。
4. 从所管理设备的列表中，选择一个 iOS 设备，然后选择“...更多”  。 然后选择“定位设备”远程操作  。
5. 定位设备后，其位置会在“定位设备”中显示  。
    ![在 Azure 中使用 Intune 定位设备的屏幕截图](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>在 iOS 设备上激活丢失模式声音警报

如果有人丢失了 iOS 9.3 或更高版本的设备，则可以远程触发设备发出警报声，以便用户找到它。 该设备必须处于[丢失模式](device-lost-mode.md)。

在 [Azure 门户的 Intune](https://aka.ms/intuneportal) 中，选择“设备”   >   “所有设备”>“选择 iOS 设备”>“概述”   >   “更多” >   “播放丢失模式声音(仅监督)”。

声音将继续播放，直到用户禁用设备上的声音或将设备从丢失模式中移除。


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>丢失模式和定位设备操作的安全与隐私信息
- 启用此操作之前，不会向 Intune 发送任何设备的位置信息。
- 使用“定位设备”操作时，可使用图形 API 检索设备的纬度和经度坐标。
- 该数据存储 24 小时，然后删除。 不能手动删除位置数据。
- 位置数据在存储和传输时均进行加密处理。
- 配置丢失模式时，可以自定义锁屏界面上显示的消息。 在此消息中，为帮助查找该设备的用户，请务必添加特定的详细信息，以返回丢失的设备。

## <a name="next-steps"></a>后续步骤

若要查看“查找设备”的启用状态，请打开“设备”，然后选择“设备操作”   。
