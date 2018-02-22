---
title: "准备好配置面向 Windows 10 的应用保护策略"
titlesuffix: Azure portal
description: "在 Azure AD 中设置移动应用程序管理 (MAM) 提供程序"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f4b6a442f83491160f72955d02b8023ee4d949f2
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2018
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>准备好配置面向 Windows 10 的应用保护策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

通过在 Azure AD 中设置 MAM 提供程序为 Windows 10 启用移动应用程序管理 (MAM)。 通过在 Azure AD 中设置 MAM 提供程序，可以在使用 Intune 创建新的 Windows 信息保护 (WIP) 策略时定义注册状态。 注册状态可以是 MAM 或移动设备管理 (MDM)。

> [!NOTE]
> 具有 MAM 注册状态的设备需要联接 Azure AD。

## <a name="to-configure-the-mam-provider"></a>配置 MAM 提供程序

1. 登录到 Azure 门户，然后选择“Azure Active Directory”。

2. 选择“管理”组中的“移动性(MDM 和 MAM)”。

3. 单击“Microsoft Intune”。

4. 配置“配置”边栏选项卡上的“还原默认 MAM URL”组中的设置。

    **MAM 用户范围**  
      使用 MAM 自动注册来管理员工的 Windows 设备上的企业数据。 将 MAM 自动注册配置为使用用户自己的设备方案。<ul><li>**无**<br>选择是否所有用户均可在 MAM 中注册。</li><li>**一些**<br>选择包含将要在 MAM 中进行注册的用户的 Azure AD 组。</li><li>**所有**<br>选择是否所有用户均可在 MAM 中注册。</li></ul>

    **MAM 使用条款 URL**  
     MAM 服务的使用条款终结点的 URL。 使用条款终结点用于在注册最终用户的设备用于管理之前，向用户显示服务条款。 使用条款文本通知用户有关在移动设备上强制执行的策略。

    **MAM 发现 URL**  
    MAM 服务的注册终结点的 URL。 注册终结点用于使用 MAM 服务注册设备以进行管理。

    **MAM 符合性 URL**  
      MAM 服务的符合性终结点 URL。 当系统拒绝用户访问非符合设备中的资源时，将向用户显示一个指向符合性 URL 的链接。 用户可导航至由 MAM 服务托管的此 URL，以便了解将其设备视为不符合的原因。 用户还可启动自助服务补救以使其设备变为具有符合性，从而可以继续访问资源。

5.  单击 **“保存”**。

## <a name="next-steps"></a>后续步骤

[创建 WIP 应用保护策略](windows-information-protection-policy-create.md)
