---
title: "设置移动设备管理机构 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何在 Intune 中设置移动设备管理机构。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 3c0de501c172484f036aa2d812f0c40fcfa1d93f

---

# <a name="set-the-mobile-device-management-authority"></a>设置移动设备管理机构 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

移动设备管理机构设置决定了管理设备的方式。 可能的设置包括：

- **Intune 独立版** - 仅限云的管理，可使用 Azure 门户进行配置。 包括 Intune 提供的所有功能。

- **Intune 混合版** - 集成了 Intune 云解决方案和 System Center Configuration Manager。 可使用 Configuration Manager 控制台配置 Intune。

- **Office 365 的移动设备管理** - 集成了 Office 365 和 Intune 云解决方案。 可在 Office 365 管理中心中配置 Intune。 包括 Intune 独立版中提供的部分功能。

>[!IMPORTANT]
>移动设备管理机构一旦设定，若要进行更改，必须联系 [Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)，所以请谨慎选择。

**若要设置移动设备管理机构，请执行以下操作：**

1. 在 Azure 门户中，选择“更多服务”，在文本框中输入“Intune”，然后选择“其他” > “Intune”。

2. 在“Intune”边栏选项卡上，选择“注册设备”，然后选择“概述”。

3. 在“开始管理设备”边栏选项卡上，选择“将 MDM 机构设置为 Intune”。 将出现一条消息，表明已成功将 MDM 机构设置为 Intune。



<!--HONumber=Feb17_HO1-->


