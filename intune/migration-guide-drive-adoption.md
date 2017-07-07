---
title: "推动最终用户采用条件性访问"
description: "本文旨在提供有关如何利用条件访问推动 Intune 注册的见解。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0b2fbcc1d63f229e1b63873841bc300bdde92fa3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2017
---
# <a name="drive-end-user-adoption-with-conditional-access"></a>推动最终用户采用条件性访问

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

通过 Intune 启用条件访问功能（例如，阻止未注册设备的电子邮件）有助于推动注册和符合性，但成功迁移不需要这些功能。 迁移采用目标和安全要求应指示成功。

## <a name="migration-campaign-with-conditional-access"></a>使用条件访问的迁移活动

下面是使用条件访问促进迁移活动的典型方法：

1.  设置条件访问规则，对所有用户强制实施，但明确排除需要从旧的 MDM 提供程序迁移的用户。 可以为条件访问排除的所有用户创建 Azure AD 用户组。

2.  用户迁移时，将他们从条件访问排除组中删除。

3.  迁移完成后，将所有条件访问策略配置为默认阻止，除非 Intune 允许访问。

### <a name="advantages"></a>优点

-   为新用户帐户或不受此前解决方案管理的用户帐户提供访问控制。

-   为此前解决方案的用户提供宽限期以进行迁移。

-   尽量避免降低工作效率

### <a name="disadvantages"></a>缺点

-   在对此前解决方案的用户启用条件访问之前，他们可能无法使用非管理设备访问资源。

> [!TIP]
> 这是众多方法之一。 你可以选择一个更简单的过程来延迟所有条件访问，直到指示每个阶段进行注册，也可以选择一个更为严格的过程，从一开始就强制实施条件访问并要求所有访问完全具备符合性。

-   了解有关[条件性访问](/intune/conditional-access)的详细信息。

## <a name="task-list-for-conditional-access"></a>条件访问的任务列表

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>任务 1：决定要如何实现条件性访问

[条件性访问的常见使用方式](/intune/conditional-access-intune-common-ways-use)。

### <a name="task-2-set-up-intune-conditional-access"></a>任务 2：设置 Intune 条件访问

选择下列选项之一：

-   [在 Azure Active Directory 中配置条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

-   [使用 Intune 安装本地 Exchange 连接器](/intune/exchange-connector-install)

-   [为 Exchange Online 设置基于应用的条件性访问策略](/intune/app-based-conditional-access-intune-exchange-online-create)

-   [为 SharePoint Online 设置基于应用的条件性访问策略](/intune/app-based-conditional-access-intune-sharepoint-online-create)

-   [屏蔽不使用现代验证 (ADAL) 的应用](/intune/app-modern-authentication-block)

## <a name="next-steps"></a>后续步骤

[典型迁移周期](migration-guide-cycle.md)
