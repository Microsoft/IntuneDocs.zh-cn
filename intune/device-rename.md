---
title: 使用 Microsoft Intune 重命名 Windows 设备 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 重命名 Windows 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567096"
---
# <a name="rename-a-windows-device-in-intune"></a>在 Intune 中重命名 Windows 设备


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

通过“重命名设备”操作可以重命名在 Intune 中注册的公司拥有的 Windows 设备。 设备的名称将在 Intune 和设备中更改。 

此功能暂不支持重命名混合 Azure AD Windows 设备。

## <a name="rename-a-device"></a>重命名设备

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备” > “所有设备”，选择 Windows 设备，然后依次单击“更多” > “重命名设备”。
4. 在“重命名设备”边栏选项卡的文本框中键入新名称。 可以使用字母、数字及连字符。 名称必须至少包含一个字母或连字符。
5. 如果要在重命名设备后重新启动该设备，请选择“重命名后重新启动”旁边的“是”。
6. 选择“重命名”。



## <a name="next-steps"></a>后续步骤

若要查看“重命名”设备操作的状态，请查看设备的“概述”页。
