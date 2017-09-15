---
title: "在 Intune 中设置注册限制"
titlesuffix: Azure portal
description: "按平台限制注册，并在 Intune 中设置设备注册限制。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06c0c58992a2119aff7fd5be54ae90be886d2a53
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="set-enrollment-restrictions"></a>设置注册限制

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

作为 Intune 管理员，可决定哪些设备可注册 Intune 管理。 使用 Azure 门户设置以下设备注册限制：

- 最大设备注册数
- 可注册的设备平台：
  - Android
  - iOS
  - macOS
  - Windows
- 平台操作系统版本（仅 iOS 和 Android）
  - 最低版本
  - 最高版本
- 限制私人拥有的设备（仅 iOS、Android、macOS）

>[!NOTE]
>注册限制不是安全功能。 遭到入侵的设备可能会误报字符。 这些限制是针对非恶意用户的最合适的障碍。

## <a name="set-device-type-restrictions"></a>设置设备类型限制
默认注册限制适用于所有用户和无用户注册。
1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 选择“设备注册” > “注册限制”。
4. 在“注册限制” > “设备类型限制”下，选择“默认”。
5. 在“所有用户”下，选择“平台”。 为每个平台选择“允许”或“阻止”：
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  单击 **“保存”**。
6. 在“所有用户”下，选择“平台配置”，然后选择以下配置。 对于每个允许的平台，可配置以下选项：
  - “版本”- 为 Android 和 iOS 设备指定“最低”和“最高”平台操作系统版本。 操作系统版本不会应用到使用设备注册计划、Apple School Manager 或 Apple Configurator 应用注册的设备。
  - “私人拥有”- 指定是“允许”还是“阻止” Android、iOS 和 macOS 设备。
  ![设备限制工作区的屏幕截图，含默认设备平台配置，其中显示已配置私人所有的设置。](media/device-restrictions-platform-configurations.png)
  单击 **“保存”**。

>[!NOTE]
>如果阻止私人拥有的 Android 设备进行注册，私人拥有的 Android for Work 设备仍可注册。

## <a name="set-device-limit-restrictions"></a>设置设备限制
默认注册限制适用于所有用户。
1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 选择“设备注册” > “注册限制”。
4. 在 Azure 门户中，依次选择“设备注册”和“注册限制”。
5. 选择“注册限制” > “设备限制”。
6. 在“所有用户”下，选择“设备限制”。 指定每个用户的最大注册设备数。  
![含设备限制的设备限制边栏选项卡的屏幕截图。](./media/device-restrictions-limit.png)

  单击“保存” 。
