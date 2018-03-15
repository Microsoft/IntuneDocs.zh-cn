---
title: "Intune 向 Apple 发送的数据"
titlesuffix: Azure portal
description: "Intune 向 Apple 发送的数据列表。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d23fdce58b9ef35fe292ca6570904320e0922f16
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/27/2018
---
# <a name="data-intune-sends-to-apple"></a>Intune 向 Apple 发送的数据

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

当在设备上启用了任何以下 Apple 服务时，Microsoft Intune 将与 Apple 建立连接并与 Apple 共享用户和设备信息： 

- [Apple 设备注册计划 (DEP)](device-enrollment-program-enroll-ios.md)
- [Apple MDM Push Certificate (APNS)](apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/en-us/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync.md)
- [Apple Volume Purchase Program (VPP)](vpp-apps-ios.md)

在 Microsoft Intune 可以建立连接之前，必须为每个 Apple 服务创建一个 Apple 帐户。

下表列出了 Microsoft Intune 从设备发送到已启用的 Apple 服务的数据。 

| 服务 | 发送到 Apple 的数据 | 用途 |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 令牌、PushMagic | 如果服务器接受设备，则该设备向服务器提供其推送通知设备令牌。 服务器应使用此令牌将推送消息发送到设备。 此签入消息还包含 PushMagic 字符串。 服务器必须记住此字符串，并将其包含在任何发送到设备的推送消息中。 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 服务器令牌 | 用于向 Apple 服务进行身份验证的推送通知设备令牌。 |
| ASM/DEP | server_name | MDM 服务器的可识别名称。 |
| ASM/DEP | server_uuid | 系统生成的服务器标识符。 |
| ASM/DEP | admin_id | 生成当前正在使用的令牌的用户的 Apple ID。 |
| ASM/DEP | org_name | 组织的名称。 |
| ASM/DEP | org_email | 组织的电子邮件地址。 |
| ASM/DEP | org_phone | 组织的电话。 |
| ASM/DEP | org_address | 组织的地址。 |
| ASM/DEP | org_id | DEP 客户 ID。 此密钥仅在协议版本 3 及更高版本中可用。 |
| ASM/DEP | serial_number | 设备的序列号（字符串）。 |
| ASM/DEP | model | 型号名称（字符串）。 |
| ASM/DEP | description | 设备的说明（字符串）。 |
| ASM/DEP | asset_tag | 设备的资产标记（字符串）。 |
| ASM/DEP | profile_status | 配置文件安装状态。 可能的值为：“空”、“已分配”、“已推送”或“已删除”。 |
| ASM/DEP | profile_uuid | 分配的配置文件的唯一 ID。 |
| ASM/DEP | device_assigned_by | 分配设备的用户的电子邮件。 |
| ASM/DEP | os | 设备的操作系统：iOS、OSX 或 tvOS。 此密钥在 X-Server-Protocol-Version 2 及更高版本中有效。 |
| ASM/DEP | device_family | 设备的 Apple 产品系列：iPad、iPhone、iPod、Mac 或 AppleTV。 此密钥在 X-Server-Protocol-Version 2 及更高版本中有效。 |
| ASM/DEP | profile_name | 字符串。 人工可读的配置文件名称。 |
| ASM/DEP | support_phone_number | 可选。 字符串。 组织的支持电话号码。 |
| ASM/DEP | support_email_address | 可选。 字符串。 组织的支持电子邮件地址。 此密钥在 X-Server-Protocol-Version 2 及更高版本中有效。 |
| ASM/DEP | department | 可选。 字符串。 用户定义的部门或位置名称。 |
| ASM/DEP | 设备 | 包含设备序列号的字符串数组。 （可能为空。） |
| VPP | Intune UserId guid | 由 Intune 生成的 GUID。 |
| VPP | 托管 AppleId UPN | 配置 VPP 令牌与 Apple 的连接时由管理员指定的 AppleID。 |
| VPP | 序列号 | 托管设备的序列号。 |

若要停止通过 Microsoft Intune 使用 Apple 服务并删除数据，必须同时禁用 Microsoft Intune Apple 令牌并删除 Apple 帐户。 请参阅 Apple 帐户如何执行帐户管理。


