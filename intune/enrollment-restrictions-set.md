---
title: "在 Intune 中设置注册限制"
titleSuffix: Intune on Azure
description: "按平台限制注册，并在 Intune 中设置设备注册限制。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2dfcba8c788f262ce816dcd23dc2921fd57f331b
ms.sourcegitcommit: d1ad84edf4f03cb4c11fe55131556b43fc3a4500
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2017
---
# <a name="set-enrollment-restrictions"></a>设置注册限制

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

作为 Intune 管理员，可决定哪些设备可注册 Intune 管理。 使用 Intune 门户设置以下设备注册限制：

- 最大设备注册数
- 可注册的设备平台：
  - Android
  - iOS
  - macOS
  - Windows
- 限制私人拥有的设备（仅 iOS 和 Android）

>[!NOTE]
>注册限制不是一项安全功能。 遭到入侵的设备可能会误报字符。 这些限制是针对非恶意用户的最合适的障碍。

## <a name="set-device-type-restrictions"></a>设置设备类型限制
默认注册限制适用于未分配有更高优先级注册限制的所有用户。  
1. 在 Intune 门户中，选择“设备注册”，然后选择“注册限制”。
![设备限制工作区的屏幕截图，其中含有默认设备类型限制和与设备限制相关的限制。](media/device-restrictions-set-default.png)
2. 在“注册限制” > “设备类型限制”下，选择“默认”。
3. 在“所有用户”下，选择“平台”。 为每个平台选择“允许”或“阻止”：
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  单击“保存” 。
4. 在“所有用户” 中，选择“平台配置”，然后选择以下配置：
  - “私人拥有”**-** 对于 Android 和 iOS 设备，指定是“允许”还是“阻止”。
  ![设备限制工作区的屏幕截图，含默认设备平台配置，其中显示已配置私人所有的设置。](media/device-restrictions-platform-configurations.png)
  单击“保存” 。

>[!NOTE]
>如果阻止私人拥有的 Android 设备进行注册，Android for Work 设备仍可进行注册。

## <a name="set-device-limit-restrictions"></a>设置设备限制
默认注册限制适用于未分配有更高优先级注册限制的所有用户。  
1. 在 Intune 门户中，选择“设备注册”，然后选择“注册限制”。
2. 选择“注册限制” > “设备限制”。
3. 在“所有用户”下，选择“设备限制”。 指定每个用户的最大注册设备数。  
![含设备限制的设备限制边栏选项卡的屏幕截图。](./media/device-restrictions-limit.png)

  单击“保存” 。
