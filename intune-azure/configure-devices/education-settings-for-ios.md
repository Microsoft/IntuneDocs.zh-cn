---
title: "配置适用于 iOS 的 Intune 教育设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解可用于在 iOS 设备上控制教育设置的设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44c427f8-0f22-43c2-8c29-e0f9fa533b1f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8d801c0b264e95348f55b1d4046c00e43ead5d10
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-configure-intune-education-settings-for-ios-devices-in-intune-azure-preview"></a>如何在 Intune Azure 预览版中配置适用于 iOS 设备的 Intune 教育设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="create-a-device-profile-containing-ios-education-settings"></a>创建包含 iOS 教育设置的设备配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“配置设备”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入版本升级配置文件的“名称”和“说明”。
5. 在“平台”下拉列表中，选择“iOS”。
6. 在“配置文件类型”下拉列表中，选择“教育”。
7. 在“教育”边栏选项卡上，选择以下文件：
    - **教师根证书文件**
    - **教师 PKCS12 / PFX 配置文件**
    - **学生根证书文件**
    - **学生 PKCS12 / PFX 配置文件**
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。

