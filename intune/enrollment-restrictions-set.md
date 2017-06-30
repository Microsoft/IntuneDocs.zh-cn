---
title: "在 Intune 中设置注册限制"
titleSuffix: Intune on Azure
description: "按平台限制注册，并在 Intune 中设置设备注册限制。 &quot;"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: b13ec0113096e4efc83463ed09e4c0db7fd7d6e1
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017

---

# <a name="set-enrollment-restrictions"></a>设置注册限制

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可对允许进行注册的设备的类型和最大数量进行设置。 在“注册限制”边栏选项卡上，可以设置：

- 允许进行注册的平台，以及是否阻止私人拥有的 Android 和 iOS 设备的注册。

- 允许用户注册的设备的最大数量。

## <a name="set-device-type-restrictions"></a>设置设备类型限制

1. 在 Intune 门户中，选择“注册设备”，然后选择“注册限制”。

2. 在“设备类型限制”下，选择“默认”。

3. 在“所有用户”边栏选项卡上，选择“平台”。

4. 对于允许在 Intune 中注册的平台，选择“允许”。 对于想阻止其注册的平台，选择“阻止”。 默认情况下，平台设置为“允许”。

    >[!NOTE]
    >这些设置不适用于或会阻止使用 Intune 软件客户端进行的 Windows 注册。 这些设置仅影响使用移动设备管理进行的注册。

6. 选择“保存”。

7. 选择“平台配置”。

8. 选择“允许”或“阻止”个人拥有的 iOS 和 Android 设备进行注册。

9. 选择“保存”。

## <a name="set-device-limit-restrictions"></a>设置设备限制

1. 在 Intune 门户中，选择“设备注册”，然后选择“注册限制”。

3. 在“设备限制”下，选择“默认”。

4. 在“所有用户”边栏选项卡上，选择“设备限制”。

5. 选择用户可以注册的最大设备数量，然后选择“保存”。

