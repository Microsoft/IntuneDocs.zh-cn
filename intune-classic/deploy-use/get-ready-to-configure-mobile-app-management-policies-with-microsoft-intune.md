---
title: "MAM 策略的先决条件 | Microsoft Docs"
description: "本主题介绍创建移动应用管理策略之前设置用户的先决条件。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3c209a350a7de7ba7ddb71468c5cd4230dcf5423
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="get-ready-to-configure-app-protection-policies-in-the-azure-portal"></a>准备好在 Azure 门户中配置应用保护策略

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题介绍可以在 Azure 门户中创建应用保护策略**之前**必须完成的先决条件和步骤。

若要了解 Intune 应用保护策略可以如何保护公司数据，请参阅[使用应用保护策略保护应用和数据](protect-apps-and-data-with-microsoft-intune.md)。

## <a name="what-is-the-azure-portal"></a>什么是 Azure 门户？

Azure 门户是用于创建应用保护策略的新管理控制台。 它支持以下 MAM 方案：
- 在 Intune 中注册的设备
- 由其他移动设备管理 (MDM) 解决方案管理的设备
- 不受任何 MDM 解决方案管理的设备 (BYOD)

目前，通过 **Intune 管理员控制台**和 **Azure 门户**，均可配置应用保护策略。  请考虑下列各项：

* 之前列出的**所有 MAM 方案**均支持在 **Azure 门户**中创建的策略。 **Intune 管理员控制台** 仅支持为**由 Intune 注册和管理的设备**创建策略。

* 可能无法在 Intune 管理员控制台中看到所有应用策略设置，因为“新建设置”只能添加到 **Azure 门户**。

* 如果**同时**在 Intune 管理控制台和 Azure 门户中创建了应用保护策略，则 **Azure 门户中的策略将应用到应用并部署到用户**。
    * 在 Intune 管理控制台中创建的应用保护策略不能导入到 Azure 门户中。  在 Azure 门户中，必须重新创建应用保护策略。


* 其他**应用管理功能**（如部署应用和应用配置策略）目前仅在 **Intune 管理员控制台**中可用。


如果不熟悉 Azure 门户，请参阅 [Microsoft Intune 应用保护策略的 Azure 门户](azure-portal-for-microsoft-intune-mam-policies.md)，了解使用 Azure 门户的基础知识。

有关如何在 Intune 管理控制台创建应用策略的说明，请参阅[配置和部署 Microsoft Intune 控制台中的应用保护策略](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)。


##  <a name="supported-platforms"></a>受支持的平台
- iOS 8.1 或更高版本
- Android 4 或更高版本
- Windows 10

>[!NOTE]
>从版本 1703 开始，无需注册方案便可在 MAM 中为 Windows 10 设备定义应用保护策略。 有关详细信息，请参阅[使用 Windows 信息保护 (WIP) 保护企业数据](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。

##  <a name="supported-apps"></a>受支持的应用
* **Microsoft 应用：**这些应用内置有 Intune 应用 SDK，且无需进一步处理就可应用应用保护策略。
若要查看受支持的 Microsoft 应用的完整列表，请转到 Microsoft Intune 应用程序合作伙伴页上的 [Microsoft Intune 移动应用程序库](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。 单击应用可查看支持的方案和平台以及查看应用是否支持多个标识。

* **组织的业务线应用：**必须准备这些应用以包含 Intune App SDK，才可应用应用保护策略。

  * 有关 Intune 管理的设备，请参阅[决定如何为 MAM 准备应用](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)。

  * 对于非托管的设备（如员工自有设备），或者由其他移动设备管理解决方案托管的设备，请参阅[保护未在 Intune 中注册的设备上的业务线应用和数据](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)。

## <a name="prerequisites"></a>先决条件

-   **Microsoft Intune 订阅**。 用户需要 Intune 许可证才能获取具有应用保护策略的应用。
如果当前使用 Intune 来管理设备，那么你已经具有 Intune 订阅。 如果你已购买企业移动性套件 (EMS) 许可证，那么你还具有 Intune 订阅。 如果要试用 Intune 来检查 MAM 功能，可在 [Microsoft Intune 页面](https://www.microsoft.com/server-cloud/products/microsoft-intune/)上获取试用帐户。

    若要验证是否具有 Intune 订阅，请在 Office 门户中转到“帐单”页面。  如果拥有订阅，应可以看到在订阅中 Intune 显示为“活动”状态。

-   以下事项需要 **Office 365 订阅**：

  - 将应用保护策略应用于具有多个标识支持的应用。

  - 创建 SharePoint Online 和 Exchange Online 工作帐户。 不支持 Exchange 内部部署和 SharePoint 内部部署。

-   **用于新式验证的 Skype for Business Online 设置**。 有关详细信息，请参阅[启用新式验证](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。


- Azure Active Directory (Azure AD) 用于创建用户。 当用户打开应用并输入其凭据时，Azure AD 对用户进行身份验证。

    > [!NOTE]
    > 必须在 Azure AD 中设置用户组。 不能使用 Intune 用户组在 Azure 门户中部署应用保护策略。

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>创建用户并分配 Microsoft Intune 许可证

1.  使用管理员凭据登录到 [Office 门户](https://portal.office.com)。

2.  按照 [Intune 评估指南](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)的**完成 30 天 Intune 评估的步骤**部分所述，添加用户，然后分配 Intune 许可证。 若要赋予用户访问 Office 门户、Azure AD 门户和 Azure 门户的权限，请将“**全局管理员**”角色分配给此用户。

5.  应用保护策略已部署到 Azure Active Directory 中的用户组。 若要创建应用保护策略的用户组，请按照[创建用于组织评估订阅用户和设备的组](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3)的**创建用户组**部分所述，创建用户组。

### <a name="assign-roles-to-non-global-admin-users"></a>向非全局管理员用户分配角色

全局管理员具有访问 [Azure 门户](https://portal.azure.com)的权限。  如果希望非全局管理员用户能够配置策略和执行其他移动应用管理任务，请参阅[使用角色分配管理 Azure 订阅资源的访问](https://azure.microsoft.com/documentation/articles/role-based-access-control-configure/)文章。

## <a name="next-steps"></a>后续步骤
[使用 Microsoft Intune 创建和部署应用保护策略](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

