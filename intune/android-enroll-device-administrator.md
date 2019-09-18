---
title: Microsoft Intune 中的 Android 设备管理员注册
titleSuffix: ''
description: 使用设备管理员注册将 Android 设备注册到 Intune。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
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
ms.openlocfilehash: 1dc495e6356a35215943415e03a46496a72bddf1
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071047"
---
# <a name="android-device-administrator-enrollment"></a>Android 设备管理员注册

Android 设备管理员（有时称为“旧版”Android 管理，随 Android 2.2 发布）是一种管理 Android 设备的方法。 不过，[Android Enterprise](https://www.android.com/enterprise/management/)（随 Android 5.0 发布）现在提供改进的管理功能。 为了实现更现代化、更丰富、更安全的设备管理，Google 正在减少新 Android 版本中对设备管理员的支持。

因此，为了避免这种功能降低，建议不要使用下面所述的设备管理员进程来注册新设备。

出于同样的原因，如果设备要更新到 Android 10，还建议用户从设备管理员管理中迁出设备。 

有关适用于 Android 设备管理员支持的 Intune 支持的更多信息，请参阅[通知部分](whats-new.md#decreasing-support-for-android-device-administrator)。

如果仍然决定让用户使用设备管理员管理注册他们的 Android 设备，请继续阅读下一部分。  


> [!Note]  
> 混合移动设备管理（混合 MDM、使用 System Center Configuration Manager 控制台管理的 Intune）将不支持 Android 10 及更高版本，因为混合 MDM 将于 2019 年 9 月 1 日停止服务。 如果仍使用混合 MDM，则应尽快迁移到 Intune 独立版。 如果需要迁移方面的帮助，请联系支持人员。 有关详细信息，请参阅[从混合移动设备管理移动到 Azure 上的 Intune](https://aka.ms/hybrid_notification)。

有关 Google 的 Android Enterprise 功能的详细信息，请参阅以下文章：
- [从设备管理员迁移到 Android Enterprise 的 Google 指南](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [弃用设备管理员 API 计划的 Google 文档](https://developers.google.com/android/work/device-admin-deprecation)


## <a name="set-up-device-administrator-enrollment"></a>设置设备管理员注册

默认情况下，Intune 允许使用设备管理员功能注册 Android 设备。

1. 若准备管理移动设备，必须将移动设备管理 MDM 机构设置为“Microsoft Intune”  。 请参阅[设置 MDM 机构](mdm-authority-set.md)，了解有关说明。 第一次设置 Intune 以进行移动设备管理时，只需设置一次此项目
2. [告知用户如何注册其设备](/intune-user-help/enroll-your-device-in-intune-android)。  

用户注册后，可开始在 Intune 中管理其设备，包括[分配符合性策略](compliance-policy-create-android.md)、[管理应用](app-management.md)等。

有关其他用户任务的信息，请参阅以下文章：
- [有关 Microsoft Intune 最终用户体验的资源](end-user-educate.md)
- [通过 Intune 使用 Android 设备](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>阻止设备管理员注册
若要阻止 Android 设备管理员设备注册或仅阻止个人拥有的 Android 设备管理员设备注册，请参阅[设置设备类型限制](enrollment-restrictions-set.md)。



## <a name="next-steps"></a>后续步骤
- [分配合规性策略](compliance-policy-create-android.md)
- [管理应用](app-management.md)