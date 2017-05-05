---
title: "准备好配置面向 Windows 10 的应用保护策略 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "在 Azure AD 中设置移动应用程序管理 (MAM) 提供程序"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: 7cd202384eeb17f5ff5a2812fe87a2fffabe6eb0
ms.lasthandoff: 04/27/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>准备好配置面向 Windows 10 的应用保护策略

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

创建并使用 Windows 10 应用保护策略前，必须在 Azure AD 中设置 MAM 提供程序，以启用面向 Windows 10 的移动应用程序管理 (MAM)。 通过 Intune 新建 Windows 信息保护 (WIP) 策略时可以通过此配置定义注册状态。

> [!NOTE]
> 注册状态可以是 MAM 或移动设备管理 (MDM)。

## <a name="to-configure-the-mam-provider"></a>配置 MAM 提供程序

1.  转到 [Azure 门户](https://portal.azure.com/)，然后使用 Intune 凭据登录。

2.  从左侧菜单中，选择“Azure Active Directory”。

    ![MAM 提供程序配置](../media/AppManagement/mam-provider-sc-1.png)

3.  “Azure AD”边栏选项卡打开后，选择“移动性(MDM 和 MAM)”，然后单击“Microsoft Intune”。

    ![移动性 MDM 和 MAM](../media/AppManagement/mam-provider-sc-1.png)

4.  配置边栏选项卡打开后，首先选择“还原默认 MAM URL”，然后配置以下内容：

    a.  MAM 用户作用域：可以使用 MAM 保护使用 Windows 10 设备的特定用户组或所有用户的公司数据。

    b。  MAM 使用条款 URL：MAM 服务的使用条款终结点的 URL。 它用于向最终用户显示 MAM 服务条款。

    c.  MAM 发现 URL：这是设备在需要应用应用保护策略时查找的 URL。

    d.  MAM 符合性 URL：

5.  配置这些设置后，选择“保存”。

## <a name="next-steps"></a>后续步骤

[创建 WIP 应用保护策略](https://docs.microsoft.com/intune-azure/manage-apps/create-windows-information-protection-policy-with-intune)

