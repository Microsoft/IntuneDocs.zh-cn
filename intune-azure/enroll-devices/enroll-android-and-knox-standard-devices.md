---
title: "在 Intune 中注册 Android 设备 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何在 Intune Azure 预览版中注册 Android 设备。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: edd6303f3bb05dfff758cbb7d4bd08e21f083998


---

# <a name="enroll-android-devices"></a>注册 Android 设备

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

作为 Intune 管理员，你可以从公司门户启用 Android 设备管理，包括 Samsung Knox 标准版设备。 然后，用户可以使用从 Google Play 提供的公司门户应用注册其设备。

## <a name="prerequisite"></a>先决条件

必须将 MDM 机构设置为“Microsoft Intune”以便为管理移动设备做好准备。 请参阅[设置 MDM 机构](set-mdm-authority.md)，了解有关说明。 只需设置一次此项目，第一次设置 Intune 以进行移动设备管理时，可能已经设置好了此项。 

## <a name="set-up-android-enrollment"></a>设置 Android 注册

默认情况下，Intune 被设置为允许注册 Android 和 Samsung Knox 标准版设备。 

若要查看允许或阻止注册 Android 设备的设置，请转到 Azure 门户中的“Intune”边栏选项卡，然后选择“注册” > “注册限制”。 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告诉用户如何注册其设备以访问公司资源

有关最终用户注册说明，请参阅[在 Intune 中注册 Android 设备](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android)。 注册过程会告知用户将出现的情况，以及 IT 管理员在其设备上可以看到和不能看到的内容。

有关其他最终用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [通过 Intune 使用 Android 设备](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)


<!--HONumber=Feb17_HO1-->


