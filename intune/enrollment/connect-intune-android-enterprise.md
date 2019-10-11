---
title: 将 Intune 帐户连接到托管的 Google Play 帐户。
titleSuffix: Microsoft Intune
description: 了解如何将 Intune 帐户连接到托管的 Google Play 帐户。
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
ms.openlocfilehash: 5ad9c098c0c9575f511c14c7b2b8120815abe3cb
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723380"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>将 Intune 帐户连接到托管的 Google Play 帐户

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

要支持 [Android Enterprise 工作配置文件](android-work-profile-enroll.md)、[Android Enterprise 完全托管](android-fully-managed-enroll.md)和 [Android Enterprise 专用设备](android-kiosk-enroll.md)，必须将 Intune 租户帐户连接到托管的 Google Play 帐户。  

Intune 将自动向 Intune 管理控制台添加四个常见的与 Android Enterprise 相关的应用，以便在连接到 Google Play 后可以轻松配置和使用 Android Enterprise 管理。 这四个 Android Enterprise 应用如下所示：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用于 Android Enterprise 完全托管方案。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 帮助你使用双因素身份验证登录帐户。
- **[Intune 公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用于应用保护策略 (APP) 和 Android Enterprise 工作配置文件方案。
- [托管的主屏幕](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用于 Android Enterprise 专用/展台方案。

> [!NOTE]
> 因为 Google 和 Microsoft 域之间的交互，此步骤可能需要你调整浏览器设置。  请确保“portal.azure.com”和“play.google.com”在浏览器中位于同一安全区域。

1. 如果你尚未准备就绪，请将[移动设备管理机构设置](../fundamentals/mdm-authority-set.md)为“Microsoft Intune”  。
2. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)，选择“设备注册” > “Android 注册” > “托管的 Google Play”    。  如果使用的是自定义 Intune 管理员角色，则访问此角色需要组织读取和更新权限。
   
   ![Android 企业注册屏幕](./media/connect-intune-android-enterprise/android-work-bind.png)

3. 选择“我同意”以向 Microsoft 授予[将用户和设备信息发送给 Google](../protect/data-intune-sends-to-google.md) 的权限  。 
   
4. 选择“启动 Google 立即连接”以打开托管的 Google Play 网站  。 网站将在浏览器的新选项卡中打开。
  
5. 在 Google 的登录页上，输入将与此租户的所有 Android Enterprise 管理任务相关联的 Google 帐户。 这是在公司的 IT 管理员之间共享的 Google 帐户，用于在 Google Play 控制台中管理和发布应用。 可以使用现有 Google 帐户或创建新帐户。 所选帐户不能与 G-Suite 域相关联。
    
    > [!Note]
    > 如果使用 Microsoft Edge 浏览器，单击右上角的“登录”可登录到 Google 帐户  。

6. 对于“组织名称”，提供你公司的名称  。 对于企业移动性管理 (EMM) 提供程序  ，应显示 Microsoft Intune  。

7. 同意 Android 协议，然后选择“确认”  。 你的请求会进行处理。

## <a name="disconnect-your-android-enterprise-administrative-account"></a>断开 Android Enterprise 管理帐户的连接

可以关闭 Android Enterprise 注册和管理。 为此，必须先停用所有已注册的 Android Enterprise 设备，包括工作配置文件设备、专用设备和完全托管的设备。 然后，在 Intune 管理控制台中选择“断开连接”，从注册中删除所有已注册的 Android Enterprise 工作配置文件设备、专用设备和完全托管的设备  。 此操作还会删除托管的 Google Play 帐户与 Intune 之间的关系。

1. 以 Intune 管理员身份登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备注册” > “Android 注册” > “托管的 Google Play” > “断开连接”     。
3. 选择“是”可从 Intune 断开连接并取消注册所有 Android 企业设备  。

## <a name="next-steps"></a>后续步骤

连接到托管的 Google Play 帐户后，可[设置 Android Enterprise 工作配置文件设备](android-work-profile-enroll.md)，[设置 Android Enterprise 专用设备](android-kiosk-enroll.md)以及[设置 Android Enterprise 完全托管设备](android-kiosk-enroll.md)
