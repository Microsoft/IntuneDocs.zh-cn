---
title: 审核、导出或删除个人数据
description: 了解如何审核、导出或删除个人数据。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fb30e8e07d71b72e337a8c2b27b3ed751c9d03e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722002"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>在 Intune 中审核、导出或删除个人数据

Intune 管理员可使用审核日志跟踪与个人数据有关的活动。 管理员还可以导出和删除个人数据。

[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>审核个人数据

审核日志为租户管理员提供导致 Microsoft Intune 有所变化的活动记录。 审核日志可用于许多管理活动，通常包括创建、更新（编辑）、删除和分配操作。 还可查看生成审核事件的远程任务。 这些审核日志可能包含已在 Intune 中注册其设备的用户的个人数据。  

出于安全目的，Intune 可能会将用户的审核日志和设备操作保留一年时间。 一年保留期后将自动删除这些日志。

若要查看审核日志，请参阅 [Intune 活动的审核日志](../fundamentals/monitor-audit-logs.md)。 

管理员不能删除审核日志。

这些审核事件会保留一年。 租户管理员可以使用[此支持请求表单](https://privacy.microsoft.com/en-US/privacy-questions?)请求审核日志。

## <a name="export-personal-data"></a>导出个人数据

管理员可以导出最终用户个人数据，包括帐户、服务数据和关联日志，以遵从“数据主体权限”请求。 是否向数据主体提供个人数据副本取决于你和你的组织，或者取决于你是否有不提供该副本的正当业务理由。 如果决定提供，可以提供实际文档的副本、经过适当修订的版本或你认为适合共享的部分的屏幕截图。

要导出用户的个人数据，可使用： 
- “Intune MDM 设备”边栏选项卡导出设备列表。 还可以直接复制设备数据。
- [Export-IntuneData.ps1 脚本](https://aka.ms/intunedataexport)。

## <a name="delete-end-user-personal-data"></a>删除最终用户的个人数据

可通过三种方法从 Intune 管理中删除个人数据：
- 从 Azure Active Directory 中删除用户
- 将设备重置为出厂设置
- 用户自行删除

### <a name="delete-a-user-from-intune"></a>从 Intune 中删除用户

要从 Intune 中删除最终用户的个人数据，管理员必须[从 Azure Active Directory (AAD) 中删除该用户](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user)。 从 AAD 中删除（硬删除）用户时，Intune 将收到 AAD 的删除信号，然后自动开始从 Intune 服务中清除该用户的所有个人数据。 Intune 服务中的用户信息将在删除操作后的 30 天内删除。

### <a name="reset-device-to-factory-settings"></a>将设备重置为出厂设置
重置为出厂设置会将所有公司和个人数据及设置还原到原始出厂设置。 这样即可将设备提供给下一位员工。 用户文件、用户安装的应用程序和非默认设置都将删除，并且此数据将在删除操作后的 30 天内从 Intune 服务中删除。

### <a name="user-self-removal-from-intune-management"></a>用户从 Intune 管理中自行删除
用户可从 Intune 管理中删除其 [Android、Apple 或 Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android) 个人设备，无需管理员的协助。   

### <a name="retire"></a>停用
“停用”操作将删除 Intune 预配的数据，例如公司应用程序、Intune 当前管理的应用的相关数据、策略设置和通过 Intune 预配的电子邮件配置文件  。 此操作会将用户个人数据保留在设备上。

### <a name="delete-a-tenant-from-microsoft-intune"></a>从 Microsoft Intune 中删除租户

如果 Intune 租户客户取消其 Intune 帐户，所有租户数据都将在客户关闭 Intune 帐户后 180 天内删除。 如果 AAD 租户与其他 Microsoft 企业订阅（Azure、Office 365）关联，则仅删除 Intune 客户数据。 将保留 AAD 租户资源，供其他订阅使用。 如果 Intune 帐户是与 AAD 租户关联的唯一订阅，则将删除该租户及所有资源和客户数据。

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>删除混合移动设备管理 (MDM) 环境中的用户
如果具有混合 MDM 环境（与 Configuration Manager 集成的 Intune），则必须完成以下操作才能完全删除用户并将其从本地 Active Directory、Configuration Manager 和 Intune 中完全移除。

1. 从本地 Active Directory (AD) 中删除用户。 这将阻止用户同步到 Azure AD，还可避免用户被 Configuration Manager 发现所发现。 
2. 从 Configuration Manager 控制台中删除用户，以从 Configuration Manager 中删除用户和关联数据。 在控制台中，转到“资产和符合性” > “用户”，右键单击要删除的用户，然后单击“删除”    。
3. [从 AAD 中删除用户](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user)，这可同时从 Azure Active Directory 和 Intune 中删除用户和关联数据。 从 AAD 中删除（硬删除）用户时，Intune 将收到 AAD 的删除信号，然后自动开始从 Intune 服务中清除该用户的所有个人数据。 Intune 服务中的用户信息将在删除操作后的 30 天内删除。

> [!Important]
>已弃用载入新的混合 MDM 客户这一功能。 有关详细信息，请参阅博客文章[从混合移动设备管理移动到 Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)。

## <a name="next-steps"></a>后续步骤

了解如何在 Intune 中[审核、导出或删除](privacy-data-audit-export-delete.md)个人数据。
