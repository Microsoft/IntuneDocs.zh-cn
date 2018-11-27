---
title: Google 发送到 Intune 的数据
titleSuffix: Microsoft Intune
description: Google 向 Intune 发送的数据列表。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a0678e562ab7b63c99f10c455837cf03ee30da21
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52178773"
---
# <a name="data-google-sends-to-intune"></a>Google 发送到 Intune 的数据

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

当在设备上启用了 Android 企业设备管理时，Microsoft Intune 可与 Google 建立连接，并在 Intune 和 Google 之间共享用户和设备信息。 必须先创建一个 Google 帐户，Microsoft Intune 才可建立连接。

下表列出了在设备上启用了设备管理时 Google 向 Intune 发送的数据：


| Google 发送到 Intune 的数据 | 详细信息 | 用途 | 示例 |
|:---:|:---:|:---:|:---:|
| 企业数据 | Google 中的客户企业标识符。 | 关联 Intune 和 Google 之间的客户信息。 | enterpriseId 示例：LC04eik8a6。<br>**名称**。 配置 Android 企业版时输入的管理员名称。 示例：Joe Smith。<br>管理员电子邮件。 配置 Android 企业版时使用的 YourAdmin@gmail.com。 |
| 应用程序数据 | 托管的 Play Store 应用程序的数据。 | 为用户或设备指定可用或所需的应用程序。 | 应用程序名称示例：Contoso 仓库清单应用程序。<br>表示应用程序的唯一标识符示例：app:com.Contoso.Warehouse.InventoryTracking |
| 服务帐户 | 唯一内部 Google 服务帐户，用于特定的客户调用。 | 用于代表客户向 Google 发起调用（以查看应用、设备等） | 名称示例：InternalAccount@InternalService.com。<br>密钥示例：ServiceAccountPassword |


要停止配合使用 Android 企业设备管理与 Microsoft Intune 并删除数据，必须禁用 Microsoft Intune Android 企业设备管理并删除 Google 帐户。 请参阅 Google 帐户如何执行帐户管理。


