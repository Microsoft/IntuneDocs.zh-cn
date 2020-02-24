---
title: 使用 Microsoft Intune 查看设备详细信息 - Azure | Microsoft Docs
description: 查看设备的详细信息，包括操作系统、存储空间、制造商和型号。 在 Azure 的 Microsoft Intune 中获取已安装应用的列表、检查符合性策略和设置 TeamViewer。 类似于查看管理设备的清单。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af4270587ab5894d52a7d12b1c2082b7b3298e51
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413749"
---
# <a name="see-device-details-in-intune"></a>在 Intune 中查看设备详细信息

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

“设备”功能可提供管理设备的其他详细信息，包括其硬件和已安装的应用  。

本文介绍如何在 Azure 门户中查看所有设备及其属性。

## <a name="view-the-device-details"></a>查看设备详细信息

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 选择“设备” > “所有设备”，然后选择某个列出的设备以打开其详细信息   ：

   - “概述”显示设备名称，并列出设备的某些关键属性，例如该设备是否是自带设备办公 (BYOD) 设备和设备的签入时间等  。 可以在设备上执行以下操作：
      - [停用](devices-wipe.md#retire)
      - [擦除](devices-wipe.md#wipe)
      - [远程锁定](device-remote-lock.md)
      - [同步设备](device-sync.md)
      - [重置密码](device-passcode-reset.md)
      - [重启](device-restart.md)（仅限 Windows）
      - [重新开始](device-fresh-start.md)（仅限 Windows）
      - 开始远程协助会话
   - 使用“属性”可以将设备分配到[你创建的设备类别](../enrollment/device-group-mapping.md)，并将设备的所有权更改为个人设备或公司设备  。
   - “硬件”包括有关设备的详细信息，例如设备 ID、操作系统和版本、存储空间等详细信息  。
   - “发现的应用”列出 Intune 发现的安装在设备上的所有应用以及应用版本  。 有关详细信息，请参阅 [Intune 发现的应用](../apps/app-discovered-apps.md)。
   - “设备符合性”列出分配到的所有符合性策略，以及设备是否符合要求  。
   - “设备配置”显示分配给该设备的所有设备配置策略，以及该策略成功还是失败  。

## <a name="hardware-device-details"></a>硬件设备详细信息
根据设备使用的运营商，可能并不会收集所有详细信息

> [!Note]  
> 硬件和软件清单每 7 天在 Intune 服务中刷新一次。

|详情|说明|平台| 
|--------------|----------------------|----|  
|名称|设备的名称。|Windows、iOS|
|管理名称|仅在控制台中使用的设备名。 更改此名称不会更改设备上的名称。|Windows、iOS|
|UDID|设备的唯一设备标识符。|Windows、iOS|
|Intune 设备 ID|用于唯一标识设备的 GUID。|Windows、iOS|
|序列号|制造商提供的设备序列号。|Windows、iOS|
|共享设备|如果为“是”  ，设备将被多个用户共享。|Windows、iOS|
|用户已批准注册|如果为“是”  ，则设备具有用户已批准注册，可让管理员管理设备上的某些安全设置。|Windows、iOS|
|操作系统|设备上使用的操作系统。|Windows、iOS|
|操作系统版本|设备上的操作系统版本。|Windows、iOS|
|操作系统语言|设备上为操作系统设置的语言。|Windows、iOS|
|内部版本号|操作系统的内部版本号。|Android|
|安全修补程序级别|设备的安全修补程序级别。|Android|
|总存储空间|设备上的总存储空间（以千兆字节为单位）。|Windows、iOS|
|可用存储空间|设备上未使用的存储空间（以千兆字节为单位）。|Windows、iOS|
|IMEI|设备的国际移动设备识别。|Windows、iOS/iPadOS、Android|
|MEID|设备的移动设备标识符。|Windows、iOS/iPadOS、Android|
|制造商|设备制造商。|Windows、iOS/iPadOS、Android|
|型号|设备型号。|Windows、iOS/iPadOS、Android|
|电话号码|分配给设备的电话号码。|Windows、iOS/iPadOS、Android*|
|订阅运营商|设备的无线运营商。|Windows、iOS/iPadOS、Android|
|蜂窝技术|设备使用的无线系统。|Windows、iOS/iPadOS、Android|
|Wi-Fi MAC|设备的媒体访问控制地址。|Windows、iOS/iPadOS、Android|
|ICCID|集成电路卡标识符，即 SIM 卡的唯一标识号。|Windows、iOS/iPadOS、Android|
|注册日期|设备在 Intune 中注册的日期和时间。|Windows、iOS/iPadOS、Android|
|上次联系|设备上次连接到 Intune 的日期和时间。|Windows、iOS/iPadOS、Android|
|激活锁旁路代码|可用于禁用激活锁的代码。|iOS|
|已注册 Azure AD|如果为“是”  ，则设备已向 Azure Directory 注册。|Windows、iOS/iPadOS、Android|
|已注册 Intune|如果为“是”  ，则设备已向 Intune 注册。|Windows、iOS/iPadOS、Android|
|合规性|设备的符合性状态。|Windows、iOS/iPadOS、Android|
|已激活 EAS|如果为“是”  ，则设备已于 Exchange 邮箱同步。|Windows、iOS/iPadOS、Android|
|EAS 激活 ID|设备的 Exchange ActiveSync 标识符。|Windows、iOS/iPadOS、Android|
|受到监督|如果为“是”  ，管理员对设备的控制增强。|Windows、iOS/iPadOS、Android|
|已加密|如果为“是”  ，则设备上存储的数据已加密。|Windows、iOS/iPadOS、Android|

> [!Note]  
> Android Enterprise 专用设备或完全托管设备上未列出电话号码清单。

## <a name="next-steps"></a>后续步骤
了解使用 Intune [管理设备](device-management.md)还可以执行哪些操作。
