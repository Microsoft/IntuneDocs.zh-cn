---
title: 使用 Microsoft Intune 同步设备 - Azure | Microsoft Docs
description: 同步使用 Microsoft Intune 注册或管理的设备，以获取最新的策略和操作。 包括使用 Azure 门户进行同步的步骤，并且列出了可以重试的错误代码。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 30b4cf585edd7153ee01710ce8c572593056454f
ms.sourcegitcommit: f5998019bbb4769fb50a7ea9bf424199516eb9ee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2018
ms.locfileid: "39117865"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>将设备与 Intune 同步以获取最新的策略和操作


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

“同步”设备操作会强制所选设备立即通过 Intune 签入。 当设备签入时，该设备会立即收到已分配给自己的任何挂起的操作或策略。 此功能可帮助立即验证和对已分配的策略进行故障排除，而无需等待下一个安排的签入。

## <a name="supported-platforms"></a>受支持的平台

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>同步设备

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。 
3. 在 Intune 中，选择“设备” > “所有设备”。
4. 在所管理的设备列表中，选择一个设备，选择“更多”，然后选择“同步”。
5. 选择“是”以确认。

选择“设备” > “设备操作”，查看同步操作的状态。

## <a name="retryable-error-codes"></a>可重试错误代码

当管理员运行“同步”设备操作时，已失败但引发了可重试错误代码的 iOS 和 Android 应用仍对设备可用。 但是，引发不可重试错误代码的应用必须等待七日，才可用于设备。


| 错误代码  | 建议的说明 | 可重试 |
|---|---|---|
| 2016330898 | 出现未知错误。 | 否 |
| 2016330897 | 对 Intune 的连接已超时。重置连接。 | 是 |
| 2016330896 | 对 Internet 的连接已断开。 重置连接。 | 是 |
| 2016330895 | 对 Internet 的连接已断开。 重置连接。 | 是 |
| 2016330894 | 对 Internet 的连接已断开。 重置连接。 | 是 |
| 2016330893 | 对 Internet 的连接已断开。 重置连接。 | 是|
| 2016330892 | 国际漫游已禁用。 | 否|
| 2016330891 | 进行电话呼叫时无法访问此设备的手机网络数据连接。 等待电话呼叫完成。 | 是|
| 2016330890 | 此设备的手机网络。 当前无法使用这些设备。 | 否|
| 2016330889 | 安全连接失败。 重置连接。 | 是|
| 2016330888 | 服务器信任评估失败。 | 否|

## <a name="next-steps"></a>后续步骤

可[查看设备的详细信息](device-inventory.md)。
 
