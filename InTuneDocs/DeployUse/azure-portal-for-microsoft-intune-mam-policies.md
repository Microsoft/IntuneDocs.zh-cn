---
title: "用于 MAM 策略的 Azure 门户 | Microsoft Intune"
description: "使用 Azure 门户创建移动应用管理策略。 此处创建的策略可以应用于在 Intune 中注册或未注册的设备。"
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 359f76daa35a14e4107a9e03c6a1b1f4d1215777
ms.openlocfilehash: c466a854474c1c5ba3270f848caa51edcd5b6856


---

# 用于 Microsoft Intune MAM 策略的 Azure 门户
## 访问 Azure 门户
**Azure 门户**允许你创建和管理移动应用管理策略。

Azure 门户支持为以下应用创建 MAM 策略：
- **由 Intune 注册和管理**的设备上运行的应用。
- 未在任何 MDM 解决方案中**注册**的设备上运行的应用
- **已在第三方 MDM 解决方案中注册**的设备上运行的应用。

>[!IMPORTANT]

> 如果你当前使用 Intune 管理控制台管理设备，则可以创建一个 MAM 策略，来支持在 Intune 中使用 [Intune 管理控制台](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)注册的设备的应用。

> 你可能无法在 Intune 管理控制台中看到全部 MAM 策略设置。 Azure 门户是创建 MAM 策略的新管理控制台。如果你同时在 Intune 管理控制台和 Azure 门户创建了 MAM 策略，则将 Azure 门户中的策略应用到应用程序，并部署到用户。

## 登录到 Azure 门户并自定义起始页

1.  转到 [Azure 门户](https://portal.azure.com)，然后使用你的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 凭据登录。

    ![Azure 门户登录页的屏幕截图](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  成功登录后，你将看到“仪表板”。 “仪表板”页附带一组默认磁贴，你可以删除磁贴和添加新的磁贴，以自定义该页面。

    ![Azure 门户仪表板的屏幕截图](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  从**浏览**菜单中查找 **Intune**。![突出显示 Intune 的浏览菜单的屏幕截图](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  单击**Intune>Intune 移动应用管理>设置**。

    ![“Intune 移动应用程序管理”边栏选项卡的屏幕截图](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > 要将边栏选项卡固定到“开始”  页上，可以使用边栏选项卡上的“固定”  选项。  单击 **Intune 移动应用管理边栏选项卡**上的图钉图标 ，将其固定到“开始”  页。

    ![突出显示图钉图标的“Intune 移动应用程序管理”边栏选项卡的屏幕截图](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![具有固定 Intune 磁贴的仪表板的屏幕截图](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## 后续步骤
[准备好配置移动应用管理策略](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


