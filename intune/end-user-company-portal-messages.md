---
title: "用户可能在设备上看到的公司门户消息"
titlesuffix: Microsoft Intune
description: "了解最终用户可能在公司门户中看到的不同消息。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 03/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
ms.openlocfilehash: e78d43cf1cb96575ebc8d8143b7b4fc1103a9bd1
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2018
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>帮助最终用户理解公司门户应用消息

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> 以下信息仅适用于 Android 6.0 及更高版本设备。

了解最终用户可能在公司门户中看到的不同应用消息。 这些应用消息通常在注册过程中的不同阶段显示。 了解消息出现的位置、消息的意义以及如果用户拒绝访问将出现的情况。 此外，了解如何最好地向用户说明消息。

- __是否允许公司门户发起和管理电话呼叫?__
- __是否允许公司门户访问设备上的照片、媒体和文件?__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>是否允许公司门户发起和管理电话呼叫?

### <a name="where-it-appears"></a>显示位置
在用户注册设备时点击公司门户应用中的“注册”后，将显示“是否允许公司门户发起和管理电话呼叫?”消息。

### <a name="what-it-means"></a>其含义
若接受此提示，则表示用户允许将设备的电话号码和 IMEI 编号发送到 Intune 服务。 这些号码将在管理员控制台的“硬件”页上显示。

> [!NOTE]
> **公司门户应用绝不会发起或管理电话呼叫！** 消息文本由 Google 管控，不可更改。

若要查看“硬件”页，必须转到“组” > “所有移动设备” > “设备”。 选择用户的设备，然后转到**查看属性** > **硬件**。

### <a name="what-happens-if-users-deny-access"></a>如果用户拒绝访问将出现的情况
如果用户拒绝访问，他们可以继续使用公司门户应用和注册其设备。 但是，管理员控制台中“硬件”页上的设备电话号码和 IMEI 编号将为空白。 拒绝访问后，用户第二次登录到公司门户应用时，该消息将显示“不再询问”复选框，用户可勾选该框使提示不再出现。

如果用户先允许访问，但稍后又拒绝访问，则在注册后用户下一次登录到公司门户应用时仍将显示该消息。

如果用户稍后决定允许访问，可转到“设置” > “应用” > “公司门户” > “权限” > “电话”，然后开启权限。

### <a name="how-to-explain-this-to-your-users"></a>如何就此向用户解释
将用户转到[在 Intune 中注册 Android 设备](/intune-user-help/enroll-your-device-in-intune-android)，使其获取详细信息。

## <a name="allow-company-portal-to-access-your-contacts"></a>是否允许公司门户访问你的联系人？

### <a name="where-it-appears"></a>显示位置
在用户注册设备时点击公司门户应用中的“注册”后，将显示“是否允许公司门户访问你的联系人?”消息。

### <a name="what-it-means"></a>其含义
若接受此提示，则表示用户允许 Intune 创建工作帐户并管理在设备上为用户注册的 Azure Active Directory 标识。

> [!NOTE]
> **Microsoft 绝不会访问用户联系人！** 消息文本由 Google 管控，不可更改。

### <a name="what-happens-if-users-deny-access"></a>如果用户拒绝访问将出现的情况
若用户拒绝访问，则不在 Intune 中注册（且无法管理）其设备。 拒绝访问后，用户第二次登录到公司门户应用时，该消息将显示“不再询问”复选框，用户可勾选该框使提示不再出现。

如果用户先允许访问，但稍后又拒绝访问，则在注册后用户下一次登录到公司门户应用时仍将显示该消息。

如果用户稍后决定允许访问，可转到“设置” > “应用” > “公司门户” > “权限” > “电话”，然后开启权限。

### <a name="how-to-explain-this-to-your-users"></a>如何就此向用户解释
将用户转到[在 Intune 中注册 Android 设备](/intune-user-help/enroll-your-device-in-intune-android)，使其获取详细信息。

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>是否允许公司门户访问你设备上的照片、媒体和文件？

### <a name="where-it-appears"></a>显示位置
在用户点击“发送数据”将日志发送给其 IT 管理员后，将显示“是否允许公司门户访问设备上的照片、媒体和文件?”消息。

### <a name="what-it-means"></a>其含义
若接受此提示，则表示用户允许其设备将数据日志写入设备的 SD 卡。 这还将允许使用 USB 电缆移动这些日志。   

> [!NOTE]
> **公司门户应用绝不会访问用户的照片、媒体和文件！** 消息文本由 Google 管控，不可更改。

### <a name="what-happens-if-users-deny-access"></a>如果用户拒绝访问将出现的情况
如果用户拒绝访问，则他们仍可通过电子邮件发送数据日志，但不会向设备 SD 卡复制日志。

拒绝访问后，用户第二次登录到公司门户应用时，该消息将显示“不再询问”复选框，勾选该框将不再显示该消息。 如果用户先允许访问，但稍后又拒绝访问，则当用户下一次尝试发送日志时，仍将显示该消息。 但是，如果用户稍后决定允许访问，可转到“设置” > “应用” > “公司门户” > “权限” > “存储”，然后开启权限。


### <a name="how-to-explain-this-to-your-users"></a>如何就此向用户解释
将用户转到[通过电子邮件向 IT 管理员发送日志](/intune-user-help/send-logs-to-your-it-admin-by-email-android)。 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>公司支持人员需要授予你访问公司资源的权限

### <a name="where-it-appears"></a>显示位置
如果未将公司门户应用添加到“允许的应用”或“豁免应用”列表，用户尝试登录时，登录将失败。 此时会显示以下消息：

> 公司支持人员需要授予你访问公司资源的权限  
> 公司将使用 Windows 信息保护策略保护你的设备。 公司支持人员需要确保他们允许公司门户访问这些资源。

### <a name="what-it-means"></a>其含义

将公司门户添加到 Windows 信息保护 (WIP) 应用保护策略中的“允许的应用”或“豁免应用”列表。 有关详细信息，请参阅[通过 Intune 创建和部署 Windows 信息保护 (WIP) 应用保护策略](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune)。

### <a name="see-also"></a>另请参阅
[最终用户需了解的 Intune 使用情况](end-user-educate.md)
