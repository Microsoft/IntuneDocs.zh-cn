---
title: 在 Intune 中注册 Android Enterprise 工作配置文件设备
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中注册 Android Enterprise 工作配置文件设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c447b6b21021573d95a5ece3297e548f216b7a0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723523"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>设置 Android Enterprise 工作配置文件设备的注册

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 可帮助用户将应用和设置部署到 Android Enterprise 工作配置文件设备，确保将工作信息和个人信息分开。 有关 Android Enterprise 的特定详细信息，请参阅 [Android Enterprise 要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

若要设置 Android Enterprise 工作配置文件管理，请执行以下步骤：

1. [将 Intune 租户帐户连接到 Android Enterprise 帐户](connect-intune-android-enterprise.md)。
2. 指定 Android Enterprise 工作配置文件注册设置。 Android Enterprise 工作配置文件[仅在特定 Android 设备上受支持](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22)。 支持 Android Enterprise 工作配置文件的任何设备同时也支持 Android 设备管理员管理。 通过 Intune 可以指定应如何在[注册限制](enrollment-restrictions-set.md)范围内管理支持 Android Enterprise 工作配置文件的设备。
    - **阻止**：若未阻止 Android 设备管理员注册，则将所有 Android 设备注册为 Android 设备管理员设备，包括支持 Android Enterprise 工作配置文件的设备。 
    - **允许（默认设置）** ：支持 Android Enterprise 工作配置文件的所有设备均注册为 Android Enterprise 工作配置文件设备。 若未阻止 Android 设备管理员注册，则将不支持 Android Enterprise 工作配置文件的所有 Android 设备注册为 Android 设备管理员设备。 
> [!NOTE]
> 自 2019 年 7 月起，默认设置“允许”适用于新租户。  所有旧租户的注册限制均不会更改，将显示他们在注册限制中设置的策略。 对于未曾更改注册限制的就用户，“阻止”仍是 Android Enterprise 工作配置文件的默认设置。 

3. [告知用户如何注册其设备](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android)。  

若要使用 Android Enterprise 工作配置文件注册已通过 Android 设备管理员注册的设备，必须先取消注册这些设备，然后重新注册。
> [!NOTE]
> 管理员可以使用“停用”功能远程完成此操作。  从“全部设备”边栏选项卡选择设备后，即可从操作菜单中找到此功能。 

如果使用[设备注册管理器](device-enrollment-manager-enroll.md)帐户注册 Android Enterprise 工作配置文件设备，则每个帐户最多可注册 10 台设备。

有关详细信息，请参阅 [Intune 发送给 Google 的数据](../protect/data-intune-sends-to-google.md)。

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Android Enterprise 工作配置文件的后续步骤
- [部署 Android Enterprise 工作配置文件应用](../apps/apps-add-android-for-work.md)
- [添加 Android Enterprise 工作配置文件配置策略](../configuration/device-profiles.md)

## <a name="see-also"></a>另请参阅

[在 Microsoft Intune 中配置和排查 Android Enterprise 设备](https://support.microsoft.com/help/4476974)
