---
title: "在 Intune 中注册 Android 设备"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何在 Intune Azure 预览版中注册 Android 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: b2cbabea781840df0a2a283f803dc76520590aba
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017


---

# <a name="enroll-android-devices"></a>注册 Android 设备

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

可借助 Intune 管理 Android 设备，包括 Samsung Knox 标准版设备。 若要启用设备管理，用户必须下载 Intune 公司门户应用（Google Play 中提供），然后打开该应用并按照注册提示来注册其设备。 Android 设备处于托管状态后，可[创建符合性策略](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)、[管理应用](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management)等。

现在，运行 Samsung KNOX 标准版的设备支持 Intune 进行多用户管理。 这意味着最终用户可以使用其 Azure AD 凭据登录和注销设备，并且无论是否正在使用，都会集中管理设备。 当最终用户登录时，他们可以访问应用，还可以获得已应用的任何策略。 用户注销时，会清除所有应用数据。

## <a name="prerequisite"></a>先决条件

必须将 MDM 机构设置为“Microsoft Intune”以便为管理移动设备做好准备。 请参阅[设置 MDM 机构](set-mdm-authority.md)，了解有关说明。 只需设置一次此项目，第一次设置 Intune 以进行移动设备管理时，可能已经设置好了此项。

## <a name="set-up-android-enrollment"></a>设置 Android 注册

默认情况下，Intune 允许注册 Android 和 Samsung Knox 标准版设备。

若要阻止 Android 设备注册或仅阻止个人拥有的 Android 设备注册，请参阅 [Set device type restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions)（设置设备类型限制）。

若要设置用户可注册的最多设备数，请参阅 [Set device limit restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions)（设置设备限制约束）。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告诉用户如何注册其设备以访问公司资源

需告知最终用户转到 Google Play 下载 Intune 公司门户应用，然后打开该应用并按照提示注册其设备。 该应用会引导用户完成注册过程，说明用户将遇到的情况，以及 IT 管理员在其设备上可以看到和不能看到的内容。

还可以向他们发送有关在线注册步骤的链接：[在 Intune 中注册 Android 设备](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android)。

有关其他最终用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [通过 Intune 使用 Android 设备](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)

