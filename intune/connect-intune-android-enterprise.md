---
title: 将 Intune 帐户连接到 Android 企业帐户
titlesuffix: Microsoft Intune
description: 了解如何将 Intune 帐户连接到 Android 企业帐户。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c32effb645b329c8095ec8757a980b1f3d80a4d7
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184280"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>将 Intune 帐户连接到 Android 企业帐户

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

要支持 Android 工作配置文件设备和 Android 展台设备，必须将 Intune 租户帐户连接到 Android 企业帐户。 

> [!NOTE]
> 因为 Google 和 Microsoft 域之间的交互，此步骤可能需要你调整浏览器设置。  请确保“portal.azure.com”和“play.google.com”在浏览器中位于同一安全区域。

1. 如果你尚未准备就绪，请将[移动设备管理机构设置](mdm-authority-set.md)为“Microsoft Intune”。
2. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)，选择“设备注册” > “Android 注册” > “托管的 Google Play”。  如果使用的是自定义 Intune 管理员角色，则访问此角色需要组织读取和更新权限。
   
   ![Android 企业注册屏幕](./media/android-work-bind.png)

3. 选择“我同意”以向 Microsoft 授予[将用户和设备信息发送给 Google](data-intune-sends-to-google.md) 的权限。 
   
4. 选择“启动 Google 立即连接”以打开托管的 Google Play 网站。 网站将在浏览器的新选项卡中打开。
  
5. 在 Google 的登录页上，输入将与此租户的所有 Android 企业管理任务相关联的 Google 帐户。 这是在公司的 IT 管理员之间共享的 Google 帐户，用于在 Google Play 控制台中管理和发布应用。 可以使用现有 Google 帐户或创建新帐户。 所选帐户不能与 G-Suite 域相关联。
    
    > [!Note]
    > 如果使用 Microsoft Edge 浏览器，单击右上角的“登录”可登录到 Google 帐户。

6. 对于“组织名称”，提供你公司的名称。 对于企业移动性管理 (EMM) 提供程序，应显示 Microsoft Intune。

7. 同意 Android 协议，然后选择“确认”。 你的请求会进行处理。

## <a name="disconnect-your-android-enterprise-administrative-account"></a>断开 Android 企业管理帐户的连接

可以关闭 Android 企业注册和管理。 若要执行此操作，必须首先停用任何已注册的 Android 工作配置文件设备。 然后，在 Intune 管理控制台中选择“断开连接”，将从注册中删除所有已注册的 Android 工作配置文件设备和展台设备。 此操作还会删除 Android 企业帐户与 Intune 之间的关系。

1. 作为 Intune 管理员，在 [Azure 门户](https://portal.azure.com)中，选择“所有服务” > “监视 + 管理” > “Intune”。
2. 选择“设备注册” > “Android 注册” > “托管的 Google Play” > “断开连接”。
3. 选择“是”可从 Intune 断开连接并取消注册所有 Android 企业设备。

## <a name="next-steps"></a>后续步骤

连接到 Android 企业帐户后，可[设置 Android 工作配置文件设备](android-work-profile-enroll.md)和[设置 Android 展台设备](android-kiosk-enroll.md)。
