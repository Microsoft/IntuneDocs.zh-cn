---
title: 如何获取对 Microsoft Intune 的支持
titleSuffix: Microsoft Intune
description: 获取对 Microsoft Intune 付费订阅和试用订阅的在线和电话支持。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: srik
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5aca7dbae7a74af399bcbf21aec1dd9dd2d1e851
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390746"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>如何获取对 Microsoft Intune 的支持

Microsoft 对 Microsoft Intune 提供全球技术、售前、帐单和订阅支持。 对于付费订阅和试用订阅，均通过在线和电话两种方式提供支持。 在线技术支持可通过英语和日语提供。 电话支持和联机帐单支持可使用其他语言。

Intune 管理员可以使用“帮助和支持”选项，通过 Azure 门户为 Intune 提交在线支持票证  。 若要创建和管理支持事件，帐户必须有 Azure Active Directory (Azure AD) 角色，其中包含操作  microsoft.office365.supportTickets  。 有关创建支持票证所需的 Azure AD 角色和权限的信息，请参阅 [Azure Active Directory 中的管理员角色](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)。

>[!IMPORTANT]
> 有关可与 Intune 协作的第三方产品（例如 Saaswedo、Cisco 或 Lookout）的技术支持，请首先与该产品的供应商联系。 在对 Intune 支持发起请求之前，请确保已正确配置了其他产品。
>
> 若要详细了解如何对 Microsoft Intune 相关问题进行故障排除，请参阅 Intune 文档的[“故障排除”部分](help-desk-operators.md)。


## <a name="help-and-support-experience"></a>帮助和支持体验

可从 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)以及 Azure 门户中 Intune 下的所有边栏选项卡（或页面）获得 Intune 的帮助和支持体验。

“帮助和支持”体验与 [Microsoft 365 管理中心](https://admin.microsoft.com/)中显示的体验类似，并取代了之前的“帮助 + 支持”，对于 Azure 的其他服务它保持不变。  

> [!TIP]
> 从 2019 年 11 月 18 日开始，向租户推出已更新并简化的控制台内体验，以便用户获得帮助和支持。 如果你尚未能感受此新体验，敬请期待，很快就会推出。

### <a name="options-to-access-help-and-support"></a>用于访问帮助和支持的选项

将新创建的租户用于 Intune 时，“帮助和支持”  可能无法打开并返回以下消息：

- 遇到未知问题。  请刷新页面，但如果问题仍然存在，请通过 [M365 管理中心](https://admin.microsoft.com)创建案例并引用提供的会话 ID。

错误详细信息包括“会话 ID”  、“扩展”  详细信息等。 
 
如果尚未通过 M365 管理中心  (https://admin.microsoft.com ) 或 Office 365 门户  (https://portal.office.com ) 对新租户帐户进行身份验证，则会出现此问题。 若要解决此问题，请在消息中选择 M365 管理中心  对应的链接，或访问 https://portal.office.com 并登录。 在任一站点上进行身份验证后，将可以访问 Intune 的”帮助和支持“  。


**访问帮助和支持**：

- **在 Azure 门户中**

  - 从任何 Intune 边栏选项卡或页面选择“帮助和支持”  。

  > [!NOTE]  
  > 若 Intune 的实例托管在政府的私有云（又称为主权云，如 Azure 政府）上，请参阅本文后续部分中的[政府私有云的 Intune 支持](#intune-support-for-private-cloud-for-government)。 直至明年才可在政府私有云上使用 Intune 帮助和支持体验  。

- **从 Microsoft 终结点管理器管理中心**
  - 选择 Intune 的功能区后，选择“帮助和支持”选项。 
  - 从“Microsoft 终结点管理器管理中心”的任何节点，选择“?”  图标，然后使用下拉列表选择想要获得与其相关的帮助的服务。 “设备管理”门户中的“?”  “Microsoft 终结点管理器管理中心”中的图标支持多个服务，必须选择想要获得与其相关的帮助的特定服务。  

    ![选择服务](./media/get-support/select-a-service.png)

    选择服务后，将看到该服务的“帮助和支持”页，你可以在此页针对特定问题指定详细信息来[查找解决方案](#find-solutions)。 

    若搜索结果看上去不符合对服务的需求，请检查并确保已选择正确的服务。 服务选择将紧随“帮助和支持”之后显示。   若选择的服务不正确，请单击“选择服务”，返回服务选择下拉列表。 

    ![确认服务](./media/get-support/confirm-your-service-selection.png)

###  <a name="the-support-experience"></a>支持体验

  打开“帮助和支持”时，门户会显示“需要帮助?”窗口  ：

  ![查看“需要帮助”窗口](./media/get-support/need-help.png)

  在左上角，可以选择三个图标来打开“需要帮助?”窗口的不同窗格  。 正在查看的窗格由下划线标识。

  具有“顶级”或“统一”支持合同的客户具有支持的[其他选项](#premier-and-unified-support-customers)，并且在“需要帮助?”中看到的横幅如下图所示    ：![顶级横幅](./media/get-support/premier-banner.png)

  “需要帮助?”将打开“查找解决方案”窗格   。 但是，如果具有活动支持案例，则该窗口将打开“服务请求”窗格，你可以在其中查看有关活动和已关闭支持案例的详细信息  。

#### <a name="find-solutions"></a>查找解决方案

![选择“查找解决方案”窗格](./media/get-support/find-solutions.png)

在“查找解决方案”窗格上，在提供的文本框中指定有关问题的一些详细信息  。 根据你提供的有关问题的文本，将使用可能匹配的见解填充该窗格。 你还将获得指向可帮助你解决问题的推荐文章的链接。

如果找到了所描述的详细信息的高度匹配项，则“需要帮助?”窗口中就会显示故障排除提示  。

例如，你可能会输入“密码同步错误”  。 结果包括直接在窗格中的故障排除指南，以及指向文档库中的推荐文章的链接。

![查看故障排除见解](./media/get-support/troubleshooting-insights.png)

#### <a name="contact-support"></a>联系支持

![选择“联系支持人员”窗格](./media/get-support/contact-support.png)

从“联系支持人员”  窗格中，可以提交请求以获得帮助。 在“查找解决方案”窗格中提供一些基本关键字后，可以使用此窗格  。

请求帮助时，请根据需要尽可能多地提供该问题的说明。  确认你的电话和电子邮件联系人信息后，选择所需的联系方式。 此窗口将显示每个联系方式的响应时间，为你提供预期的联系时间。 在提交请求之前，附加有助于填写问题详细信息的文件（如日志或屏幕截图）。

![“联系支持人员”窗体](./media/get-support/contact-support-form.png)

填写所需信息后，选择“联系我”以提交请求  。

#### <a name="service-requests"></a>服务请求

![选择“服务请求”窗格](./media/get-support/service-requests.png)

“服务请求”窗格将显示你的案例历史记录  。 活动案例位于列表的顶部，已关闭的问题也可供查看。

![查看服务请求列表](./media/get-support/service-requests-pane.png)

如果具有活动支持案例编号，则可以在此处输入该编号以跳转到该问题，也可以从活动和已关闭事件的列表中选择任何事件以查看相关详细信息。

查看事件的详细信息后，选择“服务请求”窗口顶部显示的向左箭头（就在三个“需要帮助?”窗格图标的正上方）  。 向后箭头将返回到已打开的支持事件的列表。

#### <a name="premier-and-unified-support-customers"></a>“顶级”和“统一”支持客户

具有“顶级”或“统一”支持合同的客户可以指定问题的严重性，并计划特定时间和日期的支持回调   。 当你打开或提交新问题以及编辑活动支持案例时，可以使用这些选项。

**严重性** - 用于指定问题严重性的选项取决于支持合同：

- *顶级*：A、B 或 C 的严重性
- *统一*：关键或非关键

选择严重性 A 或关键问题限制为电话支持案例，该案例提供获取支持的最快选项   。

**回调计划** - 可以在特定日期和时间请求回调。

## <a name="azure-help--support-experience"></a>Azure“帮助 + 支持”体验

无法再使用 Azure“帮助 + 支持”体验获取与 Intune 相关的帮助，除非订阅在政府私有云上  。
若 Intune 的实例未在政府私有云上运行，通过 Azure 帮助 + 支持导航将重定向到 Intune 帮助和支持体验，创建并管理支持事件   ：

使用左侧导航窗格“帮助 + 支持”或使用 Azure 门户右上角的“?”   选项打开“帮助”  窗格，然后选择“帮助 + 支持”  时，将打开 Azure“帮助 + 支持”  页。 


从此页中选择“+ 新建支持请求”  以打开“帮助 + 支持 + 新建支持请求”  页的“基本信息”  选项卡。

![帮助 + 支持](./media/get-support/help-plus-support.png)

本页内容：

- 对于“问题类型”，选择“技术”   。
- 对于“服务”，选择“Microsoft Intune”   。

  随后会显示一个链接，该链接会将你重定向到 [Intune 帮助和支持页面](https://aka.ms/intunehelpsupport)。
  
  ![新建支持请求](./media/get-support/new-request.png)


## <a name="intune-support-for-private-cloud-for-government"></a>政府私有云的 Intune 支持

Intune 订阅托管在政府私有云（又称为主权云，如 Azure 政府）上时，你尚无权访问新的 Intune“帮助和支持”体验。  请改用以下信息获取 Intune 支持。

### <a name="create-an-online-support-ticket"></a>创建在线支持票证

>[!IMPORTANT]
> 随着“帮助和支持”过渡到尚不适用于政府私有云的新系统，当创建支持事件时，门户将使用 15 位标识号标识支持案例  。 创建 15 位的案例后，将创建该案例的镜像，以供 Microsoft 支持部门使用。 在新支持系统中创建此镜像案例，它使用 8 位案例 ID，以便支持服务使用它跟踪所有支持事件的所有工作和通信。 创建 15 位案例后，你将很快收到电子邮件，其中将标识支持服务使用的镜像支持案例的 8 位编号。
>
> 支持个人工作，并从 8 位支持案例进行通信，仅使用 8 位支持案例记录通信和跟踪事件进度。 因此，你将收到来自 8 位支持案例的电子邮件更新，它们是你的案例工作跟踪记录。 15 位支持事件不记录任何详细信息。 支持结束并且 8 位支持案例关闭时，15 位支持案例（可以从 Azure 门户中查看它）将反映此状态。  15 位支持案例应没有任何其他更新或状态更改。
>
> 在今年稍后完成支持工具过渡后，托管在政府云上的 Intune 支持体验将与当前适用于托管在公有云上的 Intune 订阅的默认帮助和支持体验相同。 

1. 使用 Intune 管理员凭据登录到 Azure 门户 (<https://portal.azure.us>)，选择“?”  图标，然后选择“帮助 + 支持”  以转到 [Azure 帮助 + 支持](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)页。

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
