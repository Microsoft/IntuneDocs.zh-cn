---
title: "在 Intune 中设置注册限制"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：按平台限制注册，并在 Intune 中设置设备注册限制。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 56996592febf0be5ab74b158a70404728fe17a4d
ms.lasthandoff: 02/18/2017

---

# <a name="set-enrollment-restrictions"></a>设置注册限制 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

可对允许进行注册的设备的类型和最大数量进行设置。 在“注册限制”边栏选项卡上，可以设置：

- 允许进行注册的平台，以及是否阻止私人拥有的 Android 和 iOS 设备的注册。

- 允许用户注册的设备的最大数量。

## <a name="set-device-type-restrictions"></a>设置设备类型限制

1. 在 Azure 门户中，选择“更多服务” > “监视和管理” > “Intune”。

2. 在“Intune”边栏选项卡上，选择“注册设备”，然后选择“注册限制”。

3. 在“设备类型限制”下，选择“默认”。

4. 在“所有用户”边栏选项卡上，选择“平台”。

5. 对于允许在 Intune 中注册的平台，选择“允许”。 对于想阻止其注册的平台，选择“阻止”。 默认情况下，平台设置为“允许”。 

    >[!NOTE]
    >这些设置不适用于或会阻止使用 Intune 软件客户端进行的 Windows 注册。 这些设置仅影响使用移动设备管理进行的注册。 

6. 选择“保存”。

7. 选择“平台配置”。

8. 选择“允许”或“阻止”个人拥有的 iOS 和 Android 设备进行注册。

9. 选择“保存”。

## <a name="set-device-limit-restrictions"></a>设置设备限制

1. 在 Azure 门户中，选择“更多服务” > “监视和管理” > “Intune”。

2. 在“Intune”边栏选项卡上，选择“注册设备”，然后选择“注册限制”。

3. 在“设备限制”下，选择“默认”。

4. 在“所有用户”边栏选项卡上，选择“设备限制”。

5. 选择用户可以注册的最大设备数量，然后选择“保存”。

