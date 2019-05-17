---
title: 在 Intune 中注册 Android Enterprise 工作配置文件设备
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中注册 Android Enterprise 工作配置文件设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66574fe66f90b73d8ebf5835c5b16e93276579e4
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568214"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>设置 Android Enterprise 工作配置文件设备的注册

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 可帮助用户将应用和设置部署到 Android Enterprise 工作配置文件设备，确保将工作信息和个人信息分开。 有关 Android Enterprise 的特定详细信息，请参阅 [Android Enterprise 要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

若要设置 Android Enterprise 工作配置文件管理，请执行以下步骤：

1. [将 Intune 租户帐户连接到 Android Enterprise 帐户](connect-intune-android-enterprise.md)。
2. 指定 Android Enterprise 工作配置文件注册设置。 Android Enterprise 工作配置文件[仅在特定 Android 设备上受支持](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22)。 支持 Android Enterprise 工作配置文件的任何设备同时也支持传统的 Android 管理。 通过 Intune 可以指定应如何在[注册限制](enrollment-restrictions-set.md)范围内管理支持 Android Enterprise 工作配置文件的设备。
    - **阻止（默认设置）**：所有 Android 设备（包括支持 Android Enterprise 工作配置文件的设备）均注册为普通 Android 设备。
    - **允许**：支持 Android Enterprise 工作配置文件的所有设备均注册为 Android Enterprise 工作配置文件设备。 不支持 Android Enterprise 工作配置文件的任何 Android 设备均注册为普通 Android 设备。
3. [告知用户如何注册其设备](/intune-user-help/enroll-your-device-in-intune-android)。


若要使用 Android Enterprise 工作配置文件注册已作为常规 Android 设备注册的设备，必须先取消注册这些设备，然后重新注册。

如果使用[设备注册管理器](device-enrollment-manager-enroll.md)帐户注册 Android Enterprise 工作配置文件设备，则每个帐户最多可注册 10 台设备。

有关详细信息，请参阅 [Intune 发送给 Google 的数据](data-intune-sends-to-google.md)。

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>在托管的 Google Play 商店中批准公司门户应用

要确保用户始终可以访问最新版本的公司门户应用，必须在托管的 Google Play 商店中批准适用于Android 的公司门户应用。 通过批准，可确保每个用户获取自动更新。 如不批准，公司门户最终会过时，并无法在 Microsoft 发布重要的 bug 修补程序或新功能时收到它们。

请按以下步骤批准 Intune 公司门户：

1.  在[托管的 Google Play 商店](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal)中浏览到公司门户应用。
2.  使用配置 Android Enterprise 绑定时所用的 Google 帐户登录托管的 Google Play 商店。
3.  单击“批准”，将打开一个新的对话框。
4.  在此对话框中查看各权限，然后单击“批准”。 需要批准这些权限，才能允许公司门户应用管理设备上的工作配置文件。
5.  选择“应用请求新的权限时始终批准”，然后单击“保存”。

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Android Enterprise 工作配置文件的后续步骤
- [部署 Android Enterprise 工作配置文件应用](apps-add-android-for-work.md)
- [添加 Android Enterprise 工作配置文件配置策略](device-profiles.md)
