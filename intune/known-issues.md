---
title: "Microsoft Intune 预览版中的已知问题"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：阅读预览版中的已知问题"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 36b35e5311f6262c545a266003fb72b2febb277c
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Microsoft Intune 预览版中的已知问题


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


使用本主题了解 Intune 预览版中的任何已知问题。

如果要报告此处未列出的 bug，请[打开支持请求](https://docs.microsoft.com/intune-classic/troubleshoot/get-support)。

如果要请求将新功能添加到 Intune，请考虑在我们的 [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) 网站上提交报告。

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>在迁移过程中 Intune 所创建的组可能会影响其他 Microsoft 产品的功能

从经典 Intune 迁移到 Azure 门户时，可能会看到一个名为 **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** 的新组。 请注意，此组包含 Azure Active Directory 中的所有用户，而不仅仅是 Intune 许可的用户。 如果你希望某些现有用户或新用户不是任何组的成员，这可能会导致其他 Microsoft 产品出现问题。

### <a name="altering-groups-created-by-intune-during-migration-will-delay-migration"></a>在迁移期间更改 Intune 创建的组将延迟迁移

为准备迁移，将你的组从 Intune 复制到 Azure AD。 在经典 Intune 门户中进行的任何进一步更改都将在 Azure AD 组中更新。 但是，在 Azure AD 中进行的任何更改都不会同步回经典 Intune 控制台。 这可能导致到 Azure 门户的迁移失败，并导致迁移延迟。

### <a name="compliance-policies-from-intune-will-not-show-up-in-new-console"></a>Intune 的符合性策略不会在新控制台中显示

在经典 Intune 门户中创建的任何符合性策略都将被迁移，但不会显示在 Azure 门户中。 这是由 Azure 门户中的设计更改所致。 仍将强制执行在经典 Intune 门户中创建的符合性策略，但是你必须在经典门户中进行查看和编辑。
此外，在 Azure 门户中创建的新符合性策略不会在经典门户中显示。
有关详细信息，请参阅[什么是设备符合性](device-compliance.md)。




### <a name="administration-and-accounts"></a>管理和帐户

全局管理员（也被称为租户管理员）可以继续在没有单独的 Intune 或企业移动性套件 (EMS) 许可证的情况下进行日常的管理任务。 但是，如果全局管理员想要使用服务（例如注册他们自己的设备、企业设备，或使用 Intune 公司门户），与任何其他用户一样，他们需要 Intune 或 EMS 许可证。

### <a name="apple-enrollment-profile-migration"></a>Apple 注册配置文件迁移
在接下来的几个月里，Intune 将通过新的 Azure 门户实现管理你的 Apple 设备注册计划和 Apple 配置器注册。 如果你删除了 Apple 设备注册计划令牌，而且没有上载更新的令牌，将在新的 Azure 门户中作为迁移 Intune 帐户的一部分还原原始令牌。 若要删除此令牌并禁止 DEP 注册，在 Azure 门户中删除令牌即可。 

### <a name="rbac-for-apple-corporate-owned-device-enrollment"></a>Apple 公司拥有的设备注册 RBAC
尽管自定义用户角色下已列出 RBAC 权限并可在此获取此权限，但是仍需具备租户或服务管理员 Azure AD 角色才能执行 Apple DEP 和 Apple Configurator 注册任务。 将在以后公布对这些功能的 RBAC 角色支持。

