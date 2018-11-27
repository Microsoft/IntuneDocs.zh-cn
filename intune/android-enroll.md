---
title: 在 Intune 中注册 Android 设备
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中注册 Android 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2b2b3ba5443cd95cd81bdca6d386ab95a2c831eb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190109"
---
# <a name="enroll-android-devices"></a>注册 Android 设备

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 管理员可管理以下 Android 设备：
- Android 设备，包括 Samsung Knox 标准设备。
- Android 企业设备，包括 [Android 工作配置文件设备](#enable-enrollment-of-android-for-work-devices)和 Android 展台设备。

运行 Samsung Knox 标准版的设备支持 Intune 进行多用户管理。 即是说，用户可以使用其 Azure AD 凭据登录和注销设备。 该设备仍然受中央管理，无论是否正在使用。 当用户登录时，他们可以访问应用，还可以获得已应用的任何策略。 用户注销时，会清除所有应用数据。

## <a name="prerequisite"></a>先决条件

若准备管理移动设备，必须将移动设备管理 MDM 机构设置为“Microsoft Intune”。 请参阅[设置 MDM 机构](mdm-authority-set.md)，了解有关说明。 第一次设置 Intune 以进行移动设备管理时，只需设置一次此项目。

## <a name="set-up-android-enrollment"></a>设置 Android 注册

默认情况下，Intune 允许注册 Android 和 Samsung Knox 标准版设备。 满足先决条件后，管理员仅需[告诉用户如何注册其设备](/intune-user-help/enroll-your-device-in-intune-android)。

用户注册后，可开始在 Intune 中管理其设备，包括[分配符合性策略](compliance-policy-create-android.md)、[管理应用](app-management.md)等。

有关其他用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](end-user-educate.md)
- [通过 Intune 使用 Android 设备](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

若要阻止 Android 设备注册或仅阻止个人拥有的 Android 设备注册，请参阅 [Set device type restrictions](enrollment-restrictions-set.md)（设置设备类型限制）。

## <a name="set-up-android-enterprise-enrollment"></a>设置 Android 企业注册

Android 企业是一组 Android 设备功能和服务，它将分隔个人应用和数据与包含工作应用和数据的工作配置文件。 Android 企业设备包括工作配置文件设备和展台设备。 

要设置 Android 企业设备的注册，必须先[将 Android 企业连接到 Intune](connect-intune-android-enterprise.md)。 完成此步骤后，可以：

[设置 Android 工作配置文件注册](android-work-profile-enroll.md)
[设置 Android 展台注册](android-kiosk-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>注册 Samsung Knox 设备时的最终用户体验
注册 Samsung Knox 设备时，应注意以下方面：
-   即使没有任何策略要求使用 PIN，设备也必须具有一个至少四位数的 PIN 才能注册。 如果设备没有 PIN，系统将提示用户创建 PIN。
-   用户无需与 Workplace Join Certificates (WPJ) 进行交互。
-   系统会提示用户有关 Service Enrollment 及其功能的信息。
-   系统会提示用户有关 Knox Enrollment 及其功能的信息。
-   如果强制执行了加密策略，则用户需要设置六个字符的复杂密码作为设备密码。
-   服务不会推送任何其他要求安装证书才能访问公司资源的用户提示。
- 某些旧版 Knox 设备会提示用户提供其他证书才能访问公司资源。
- 如果 Samsung Mini 设备未能安装 WPJ 并出现“找不到证书”或“未能注册设备”错误，请安装最新的 Samsung Firmware 更新。
