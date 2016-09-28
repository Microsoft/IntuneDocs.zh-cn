---
title:
- "移动应用程序管理故障排除 | Microsoft Intune"
description: 
keywords: 
author: karaman
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: 9cfb3694b2fae919fd0554a6e21b497cdcf19c72
ms.openlocfilehash: f33e8de82ee07bb4571a5bfaff63af72f9086376


---

# 移动应用程序管理故障排除

若有关于移动应用程序管理的问题，请从此处开始阅读。 本主题包含你可能会遇到的一些常见问题以及解决方案。


**问题：**Azure 控制台中无注册策略的 MAM 不应用到 iOS 和 Android 设备上的 Skype for Business 应用。

解决方案：必须将 Skype for Business 设置为新式验证。  请按照[为租户启用新式验证](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)中的指示为 Skype 设置新式验证。

**问题：**不具有注册策略的 MAM 不应用到任何用户(受支持的 Office 应用)[https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners]。
 
解决方案：请确认用户已获得 Intune 授权。  

**问题：**IT 管理员用户无法在 Azure 门户配置 MAM 策略

解决方案：下列角色可访问 Azure 门户：

- 全局管理员，可在 [Office 门户](http://portal.office.com/)中设置
- 所有者，可在 [Azure 门户](https://portal.azure.com/)设置中。
- 参与者，可在 [Azure 门户](https://portal.azure.com/)设置中。

请参阅[准备好使用 Microsoft Intune 配置移动应用管理策略](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)，获取设置这些角色的帮助。 

**问题：**应用报表不显示近期应用 MAM 策略的用户。

解决方案：若用户最近才成为 MAM 策略的目标，则可能要 24 小时后，该用户才在报表中显示为目标用户。 

**问题：**应用策略更改/更新需 8 小时。  

解决方案：最终用户可注销该应用，然后重新登录，强行与服务同步。  

**问题：**MAM 策略不应用到 Apple DEP 的设备

解决方案：请确保通过 Apple 设备注册程序 (DEP) 使用用户关联。 对需要在 DEP 下进行用户身份验证的应用而言，用户关联是必须的。
请参阅 [Enroll corporate-owned Device Enrollment Program iOS devices（将通过“设备注册计划”购买的 iOS 设备注册为企业所有）](https://docs.microsoft.com/en-us/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)，了解有关 iOS DEP 注册的详细信息。


### 另请参阅
- [验证移动应用管理设置](https://docs.microsoft.com/en-us/intune/deploy-use/validate-mobile-application-management)
- [准备好使用 Microsoft Intune 配置移动应用管理策略](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 





<!--HONumber=Sep16_HO2-->


