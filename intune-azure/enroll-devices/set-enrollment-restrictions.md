---
title: "在 Intune 中设置注册限制 | Intune Azure 预览版 | Microsoft 文档"
description: "Intune Azure 预览版：按平台限制注册，并在 Intune 中设置设备注册限制。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 1bdefce35c20ce24b94ee701a2d13b5408f435ce

---

# <a name="set-enrollment-restrictions"></a>设置注册限制 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

可通过指定允许的平台，在 Intune 中限制可以注册的设备类型。 还可以设置用户允许注册的最大设备数量。

## <a name="set-device-type-restrictions"></a>设置设备类型限制

1. 在 Azure 门户中，选择“更多服务”，在文本框中输入“Intune”，然后选择“其他” > “Intune”

2. 在“Intune”边栏选项卡上，选择“注册设备”，然后选择“注册限制”。

3. 在“设备类型限制”下，选择“默认”。

4. 在“所有用户”边栏选项卡上，选择“平台”。

5. 对于允许在 Intune 中注册的平台，选择“允许”。 对于想阻止其注册的平台，选择“阻止”。

6. 选择“保存”。

7. 选择“平台配置”。

8. 选择“允许”还是“阻止”个人拥有的 iOS 设备进行注册。

9. 选择“保存”。

## <a name="set-device-limit-restrictions"></a>设置设备限制

1. 在 Azure 门户的“Intune”边栏选项卡上，选择“注册设备”，然后选择“注册限制”。

2. 在“设备限制”下，选择“默认”。

3. 在“所有用户”边栏选项卡上，选择“设备限制”。

4. 选择用户可以注册的最大设备数量，然后选择“保存”。



<!--HONumber=Feb17_HO1-->


