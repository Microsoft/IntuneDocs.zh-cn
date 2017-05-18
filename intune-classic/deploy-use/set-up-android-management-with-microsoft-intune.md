---
title: "设置 Android 管理 | Microsoft Docs"
description: "使用 Microsoft Intune 为 Android 和 KNOX 标准版设备启用移动设备管理 (MDM)。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 4042a22ecfbab7970ea4b3dab8ee6a82b0da5f78
ms.lasthandoff: 04/24/2017


---

# <a name="set-up-android-device-management"></a>设置 Android 设备管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

作为 Intune 管理员，你可以从公司门户启用 Android 设备管理，包括 Samsung Knox 标准版设备。 然后，用户可以使用从 Google Play 提供的公司门户应用注册其设备。

默认情况下，Android 设备可在 Intune 中进行注册。 若要阻止 Android 设备注册，请使用管理员凭据登录 [Microsoft Intune 管理门户](https://manage.microsoft.com)。 选择“管理员” > “移动设备管理” > “注册规则”，然后清除“允许 Android 设备”复选框。

1.  **设置 Intune**<br>
    如果你尚未设置，请通过[将移动设备管理机构设置](prerequisites-for-enrollment.md#step-2-set-mdm-authority)为“Microsoft Intune”并设置 MDM，为管理移动设备做好准备。

2.  **已启用 Android 注册**<br>
    在 Intune 控制台中，启用 Android 移动设备注册无需其他配置。

3.  **告诉用户如何注册其设备以获取对公司资源的访问权限。**

    有关最终用户注册说明，请参阅[在 Intune 中注册 Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)。 注册过程会告知用户将出现的情况，以及 IT 管理员在其设备上可以看到和不能看到的内容。

    有关其他最终用户任务的信息，请参阅以下文章：
  - [有关 Microsoft Intune 最终用户体验的资源](how-to-educate-your-end-users-about-microsoft-intune.md)
  - [适用于 Android 设备的最终用户指南](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

由于中国地区没有 Google Play 商店，Android 设备必须从中国的应用市场获取公司门户。 可在以下应用商店下载用于 Android 的公司门户应用：
* [百度](https://go.microsoft.com/fwlink/?linkid=836946)
* [华为](https://go.microsoft.com/fwlink/?linkid=836948)
* [腾讯](https://go.microsoft.com/fwlink/?linkid=836949)
* [豌豆荚](https://go.microsoft.com/fwlink/?linkid=836950)
* [小米](https://go.microsoft.com/fwlink/?linkid=836947)

Android 版公司门户应用使用 Google Play Services 与 Microsoft Intune 服务进行通信。 由于 Google Play Services 尚未在中国推出，因此执行以下任何任务最高可能需要 8 个小时才能完成。 

|Intune 管理控制台| Android 适用的 Intune 公司门户应用 |Intune 公司门户网站|   
|---|---|---|
|完全擦除| 移除远程设备| 移除设备（本地和远程）|
|“选择性擦除”| 重置设备| 重置设备|
|新的或更新的应用部署| 安装可用的业务线应用| 设备密码重置|
|远程锁定|||
|密码重置|||

### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中注册设备的先决条件](prerequisites-for-enrollment.md)

