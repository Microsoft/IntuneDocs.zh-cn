---
title: 如何获取对 Microsoft Intune 的支持
titleSuffix: Microsoft Intune
description: 获取对 Microsoft Intune 付费订阅和试用订阅的在线和电话支持。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91627a47f9dccfb436e64aaadeeb392648dff821
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585296"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>如何获取对 Microsoft Intune 的支持  

[!INCLUDE [azure_portal](../../intune-classic/includes/note-for-both-portals.md)]  
  
Microsoft 对 Microsoft Intune 提供全球技术、售前、帐单和订阅支持。 对于付费订阅和试用订阅，均通过在线和电话两种方式提供支持。 在线技术支持可通过英语和日语提供。 电话支持和联机帐单支持可使用其他语言。

Intune 管理员可以使用“帮助和支持”选项，通过 Azure 门户为 Intune 提交在线支持票证  。 若要创建和管理支持事件，帐户必须有 Azure Active Directory (Azure AD) 角色，其中包含操作  microsoft.office365.supportTickets/tickets/manage  。 有关创建支持票证所需的 Azure AD 角色和权限的信息，请参阅 [Azure Active Directory 中的管理员角色](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)。  

>[!IMPORTANT]  
> 有关可与 Intune 协作的第三方产品（例如 Saaswedo、Cisco 或 Lookout）的技术支持，请首先与该产品的供应商联系。 在对 Intune 支持发起请求之前，请确保已正确配置了其他产品。
>
> 若要详细了解如何对 Microsoft Intune 相关问题进行故障排除，请参阅 Intune 文档的[“故障排除”部分](help-desk-operators.md)。

## <a name="known-issues-for-creating-support-incidents"></a>创建支持事件的已知问题  

如果帐户具有所需的权限，但无法成功访问“帮助和支持”，或无法创建或管理支持事件，请查看以下已知问题和解决方法：  
- 帐户的过时用户令牌。 若要解决此问题，请注销所有活动的控制台会话，再次登录，然后尝试创建或管理支持事件。 
- 多个活动会话。 如果使用多个用户或会话登录，请保留一个控制台，注销其他所有控制台。 然后，使用单个活动会话，尝试创建或管理支持事件。

解决访问问题可能需要执行的其他操作：
- 清除活动浏览器会话的所有 cookie，然后重试创建或管理支持事件。
- 使用 InPrivate 浏览会话登录 Intune，并尝试创建或管理支持事件。  

如果上述解决方法不起作用，请转到 [Microsoft 365 管理中心](https://admin.microsoft.com)并从那里创建支持票证。 我们目前正在开发的修补程序将于夏末推出。  

## <a name="help-and-support-experience"></a>帮助和支持体验  

可从 [Microsoft 365 设备管理门户](https://devicemanagement.microsoft.com)以及 Azure 门户中 Intune 下的所有边栏选项卡（或页面）获得 Intune 的帮助和支持体验。 

![Intune 边栏选项卡](./media/get-support/intune-blades.png)


“帮助和支持”体验与 [Microsoft 365 管理中心](https://admin.microsoft.com/)中显示的体验类似，并取代了之前的“帮助 + 支持”，对于 Azure 的其他服务它保持不变。   

若要访问“帮助和支持”，请使用以下选项：  
- **设备管理仪表板：**
  - 选择 Intune 的功能区后，选择“帮助和支持”选项。 
  - 从“设备管理”门户的任意节点，选择门户右上角的“?”  图标，然后使用下拉列表选择想要获得与其相关的帮助的服务。 “设备管理”门户中的“?”  图标支持多个服务，必须选择想要获得与其相关的帮助的特定服务。  

    ![选择服务](./media/get-support/select-a-service.png)

    选择服务后，将看到该服务的“帮助和支持”页，然后可以针对想要求助的特定问题[详述详细信息](#specify-details-about-an-issue)。   

    若搜索结果看上去不符合对服务的需求，请检查并确保已选择正确的服务。 服务选择将紧随“帮助和支持”之后显示。   若选择的服务不正确，请单击“选择服务”，返回服务选择下拉列表。    

    ![确认服务](./media/get-support/confirm-your-service-selection.png) 


- **在 Azure 门户中执行以下操作：**
  - 从任何 Intune 边栏选项卡或页面选择“帮助和支持” 

  在 Azure 门户中，若从右上角选择“?”  图标，或从左侧导航窗格选择“帮助 + 支持”，将打开 Azure 的“帮助 + 支持”   。 从 Azure 的“帮助 + 支持”中，无法直接打开 Intune 支持事件，但可以执行以下操作，来转到 Intune“帮助和支持”页面：   
  1. 选择“新建支持请求”。
  2. 为“问题类型”指定“技术”。
  3. 为“服务”指定“Microsoft Intune”。
  4. 选择链接“Intune 帮助和支持”页。

> [!NOTE]  
> 若 Intune 的实例托管在政府实体的私有云（又称为主权云，如 Azure 政府）上，请参阅本文后续部分中的[政府私有云的 Intune 支持](#intune-support-for-private-cloud-for-government)。 今年晚些时候才可在政府私有云上使用 Intune 帮助和支持体验  。 


打开“帮助和支持”时，门户将显示一个视图，具体取决于是否有未解决的支持事件，若你有顶级支持，将显示一些额外的元素和选项： 
- **没有未解决的支持事件**：将显示“需要帮助?”页，如“设备管理”仪表板中的下图所示。   
- **未解决的支持事件**：将看到[支持票证](#view-support-cases)，它将显示未解决事件列表。  
- **顶级支持约定**：体验与前两个选项相同，但“需要帮助?”页上将显示以下额外的元素： 
  - 在页标题“需要帮助?”的后面，将看到“顶级支持”横幅：   
    ![顶级支持横幅](./media/get-support/premier-banner.png)
  - 在通过电话创建服务请求时，可以在页面的“获取支持”部分中设置初始严重性级别。  


![“设备管理”仪表板和“需要帮助?”页](./media/get-support/help-support-dashboard.png)

在此视图中，可以执行以下操作：

1. 指定有关需要帮助的[特定问题的详细信息](#specify-details-about-an-issue)  
2. [查看上下文相关的帮助](#view-context-sensitive-help)以及基于指定的详细信息的相关解决方案  
3. 使用电子邮件或电话[获取支持](#get-support)  
4. 查看先前使用此新工作流程打开的[支持案例](#view-support-cases)  

### <a name="specify-details-about-an-issue"></a>指定有关问题的详细信息 

从新体验支持的位置打开“帮助和支持”时，会打开“需要帮助?”页  。 在此页上，可以指定有关问题的详细信息。 输入详细信息时，控制台会根据使用的关键字提供常见查询。 选择提供的选项或完成自己的问题描述。 如果输入自己的说明，请选择“获取帮助”进行提交  。 提交查询后，控制台将返回上下文相关信息，以帮助解决问题。

以下是可能提交的查询示例：
  
- 无法还原 iOS 设备   
- *无法创建条件访问策略*  

![在“需要帮助”页上指定问题](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>查看上下文相关帮助 

选择提供的选项或提交自己的查询后，上下文相关的结果将显示在“查看解决方案”下  。 这些结果包括 Intune 特定的自助指导和基于查询条件的 Web 搜索返回的其他结果。  
![查看结果](./media/get-support/view-results.png)

### <a name="get-support"></a>获取支持 

如果自助指导或基于 Web 的指导无法帮助你解决问题，可以使用控制台打开电子邮件或电话支持问题。  
在“需要帮助?”页上，选择要使用的选项  。  

  > [!NOTE] 
  > 并非所有租户都可以使用电子邮件请求寻求支持。  

- 对于电子邮件请求，请提供电子邮件地址，也可以选择在提交中添加附件。 选择“发送”以创建请求  。 

  ![电子邮件请求](./media/get-support/email-support.png)
  
- 对于电话请求，请提供电话号码。 （可选）可以包含电子邮件地址并在提交中添加附件。 选择“给我打电话”以提交请求。  



   ![电话请求](./media/get-support/phone-support.png)

**顶级支持**：  
若你有顶级支持约定，你同样可以选择创建电话支持事件。 你还可以指定严重性以用于支持回拨，选择根据任务关键约定创建支持票证。   

![顶级支持选项](./media/get-support/premier-phone-support-options.png)


### <a name="view-support-cases"></a>查看支持案例  

选择历史记录按钮以查看已创建的支持案例。  

![查看支持案例](./media/get-support/view-support-tickets.png)

- 在此工作流程中，只能看到使用新工作流程打开的支持案例。 若要查看这些案例，请使用设备管理控制台中的“帮助和支持”视图或 Azure 门户中的 Intune 边栏选项卡。 这些案例的数字长度为八位数。 此外，还可以从 Microsoft 365 管理中心查看这些案例。  

- 在没有使用 Intune“帮助和支持”体验时打开的案例保持不变。 若要查看这些案例，必须使用不属于 Intune 体验或管理仪表板的“帮助和支持”视图。 这些案例的数字以 117 或 118 开头，长度为 15 位   。 查看管理共享：

    1. 使用 Intune 管理员凭据登录到 Azure (<https://portal.azure.com>)，选择“?”  图标，然后选择“帮助 + 支持”  以转到 [Azure 帮助 + 支持](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)页。

    2. 在“帮助 + 支持”页上，可以查看“最近的支持请求”列表，并选择它们以查看更多详细信息   。
 

## <a name="azure-help--support-experience"></a>Azure“帮助 + 支持”体验 

使用左侧导航窗格“帮助 + 支持”或使用 Azure 门户右上角的“?”   时，将打开 Azure 帮助 + 支持体验，此体验不同于 Intune 帮助和支持体验。  

自 2019 年 4 月起，只有订阅在政府实体私有云上时，才可以访问 Azure 帮助 + 支持体验，进而获取与 Intune 相关的帮助  。  

若 Intune 的实例未在政府私有云上运行，通过 Azure 帮助 + 支持导航将重定向到 Intune 帮助和支持体验，创建并管理支持事件   。  


## <a name="intune-support-for-private-cloud-for-government"></a>政府私有云的 Intune 支持  

Intune 订阅托管在政府实体私有云（又称为主权云，如 Azure 政府）上时，你尚无权访问新的 Intune 帮助和支持体验。  请改用以下信息获取 Intune 支持。 


### <a name="create-an-online-support-ticket"></a>创建在线支持票证 

>[!IMPORTANT]    
> 随着“帮助和支持”过渡到尚不适用于政府私有云的新系统，当创建支持事件时，门户将使用 15 位标识号标识支持案例  。 创建 15 位的案例后，将创建该案例的镜像，以供 Microsoft 支持部门使用。 在新支持系统中创建此镜像案例，它使用 8 位案例 ID，以便支持服务使用它跟踪所有支持事件的所有工作和通信。 创建 15 位案例后，你将很快收到电子邮件，其中将标识支持服务使用的镜像支持案例的 8 位编号。  
> 
> 支持个人工作，并从 8 位支持案例进行通信，仅使用 8 位支持案例记录通信和跟踪事件进度。 因此，你将收到来自 8 位支持案例的电子邮件更新，它们是你的案例工作跟踪记录。 15 位支持事件不记录任何详细信息。 支持结束并且 8 位支持案例关闭时，15 位支持案例（可以从 Azure 门户中查看它）将反映此状态。  15 位支持案例应没有任何其他更新或状态更改。  
> 
> 在今年稍后完成支持工具过渡后，托管在政府云上的 Intune 支持体验将与当前适用于托管在公有云上的 Intune 订阅的默认帮助和支持体验相同。   


1. 使用 Intune 管理员凭据登录到 Azure 门户 (<https://portal.azure.com>)，选择“?”  图标，然后选择“帮助 + 支持”  以转到 [Azure 帮助 + 支持](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)页。

   ![问号链接的示意图，其中突出显示了“帮助 + 支持”链接](./media/get-support/azure-get-support.png)

2. 在 Azure“帮助 + 支持”页上，选择“新建支持请求”   。

   ![帮助和支持页面的示意图，其中突出显示了“新建支持请求”链接](./media/get-support/azure-support-ticket-link.png)

3. 对于大多数 Intune 技术支持问题，在“基本信息”  选项卡上选择以下选项：
   - **问题类型**：**技术**
   - **订阅**：<你的订阅  >
   - **服务**：**Microsoft Intune**
   - **问题类型**：从下拉菜单中选择问题类型。
   - **问题子类型**：从下拉菜单中选择问题子类型。
   - **主题**：简要描述需要获得帮助的问题。

   ![“帮助 + 支持”-“新建支持请求”页上的“基本信息”选项卡的示意图](./media/get-support/help-new-support-case-basics.png)

   选择“下一步:  解决方案”以继续。
4. 在“解决方案”  选项卡上，查看可能有助于在不提交票证的情况下解决问题的建议步骤。 如果在查看完步骤后仍想创建支持请求，请单击“下一步:  详细信息”。

   ![“帮助 + 支持”-“新建支持请求”页上的“解决方案”选项卡的示意图](./media/get-support/help-new-support-case-solutions.png)
5. 在“详细信息”  选项卡上，填写问题的详细信息、支持方法、联系信息，然后单击“下一步:  查看 + 创建”。

   ![“帮助 + 支持”-“新建支持请求”页上的“详细信息”选项卡的示意图](./media/get-support/help-new-support-case-details.png)
6. 查看此信息，并验证其是否正确，然后选择“创建”  以提交支持请求。

   ![“新建支持请求”页上的“查看 + 创建”选项卡的示意图](./media/get-support/help-new-support-case-create.png)

>[!IMPORTANT]
>如果有计费或订阅相关问题，可以通过 [Microsoft 365 管理中心](https://admin.microsoft.com/Support/SupportEntry.aspx)打开一个案例以获取支持。

### <a name="view-support-requests"></a>查看支持请求  

可以在 Azure 门户中查看支持请求。 但提供的信息有限。  查看事件： 

1. 使用 Intune 管理员凭据登录到 Azure (<https://portal.azure.com>)，选择“?”  图标，然后选择“帮助 + 支持”  以转到 [Azure 帮助 + 支持](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)页。

2. 在“帮助 + 支持”页上，可以查看“最近的支持请求”列表   。

   > [!IMPORTANT]  
   > 政府私有云客户仅可以查看 15 位支持案例号以及事件状态。 所有案例通信和工作跟踪或通知均通过电子邮件发送，并引用从 Intune 控制台打开支持案例镜像时所创建的 8 位支持案例号。   

## <a name="additional-resources"></a>其他资源  

- [计费和订阅管理支持](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [批量许可](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [对 Intune 问题进行故障排除](help-desk-operators.md)
