---
title: 配置适用于 Windows 10 的应用保护策略
titleSuffix: Microsoft Intune
description: 本主题介绍如何配置适用于 Windows 10 设备的应用保护策略 (APP)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0e1ff8fd39d301bd685e9806c319f49e9189d7f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507412"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>准备好配置面向 Windows 10 的应用保护策略 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

通过在 Azure AD 中设置 MAM 提供程序为 Windows 10 启用移动应用程序管理 (MAM)。 通过在 Azure AD 中设置 MAM 提供程序，可以在使用 Intune 创建新的 Windows 信息保护 (WIP) 策略时定义注册状态。 注册状态可以是 MAM 或移动设备管理 (MDM)。

## <a name="to-configure-the-mam-provider"></a>配置 MAM 提供程序

1. 登录到 Azure 门户，然后选择“Azure Active Directory”  。

2. 选择“管理”  组中的“移动性(MDM 和 MAM)”  。

3. 单击“Microsoft Intune”  。

4. 配置“配置”  边栏选项卡上的“还原默认 MAM URL”  组中的设置。

   **MAM 用户范围**  
   使用 MAM 自动注册来管理员工的 Windows 设备上的企业数据。 将 MAM 自动注册配置为使用用户自己的设备方案。<ul><li>**无**<br>选择是否所有用户均不可在 MAM 中注册。</li><li>**一些**<br>选择包含将要在 MAM 中进行注册的用户的 Azure AD 组。</li><li>**所有**<br>选择是否所有用户均可在 MAM 中注册。</li></ul>

   **MAM 使用条款 URL**  
   Microsoft Intune 不支持 MAM 使用条款 URL。 必须将此输入框留空，以便应用保护策略。

   **MAM 发现 URL**  
   MAM 服务的注册终结点的 URL。 注册终结点用于使用 MAM 服务注册设备以进行管理。

   **MAM 符合性 URL**  
   Microsoft Intune 不支持 MAM 符合性 URL。 必须将此输入框留空，以便应用保护策略。 

5. 单击 **“保存”** 。

## <a name="next-steps"></a>后续步骤

[创建 WIP 应用保护策略](windows-information-protection-policy-create.md)
