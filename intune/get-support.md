---
title: 如何获取对 Microsoft Intune 的支持 | Microsoft Intune
description: 获取对 Microsoft Intune 付费订阅和试用订阅的在线和电话支持。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 6a57a3a26a786e86775ce1509c5f751d2856f95b
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817290"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>如何获取对 Microsoft Intune 的支持

[!INCLUDE [azure_portal](./includes/note-for-both-portals.md)]

Microsoft 对 Microsoft Intune 提供全球技术、售前、帐单和订阅支持。 对于付费订阅和试用订阅，均通过在线和电话两种方式提供支持。 在线技术支持可通过英语和日语提供。 电话支持和联机帐单支持可使用其他语言。

>[!IMPORTANT]
> 有关可与 Intune 协作的第三方产品（例如 Saaswedo、Cisco 或 Lookout）的技术支持，请首先与该产品的供应商联系。 在对 Intune 支持发起请求之前，请确保已正确配置了其他产品。
>
> 若要详细了解如何对 Microsoft Intune 相关问题进行故障排除，请参阅 Intune 文档的[“故障排除”部分](help-desk-operators.md)。

IT 管理员可以使用“帮助 + 支持”选项，通过 Azure 门户为 Intune 提供在线支持票证。 若要创建支持票证，必须为帐户分配以下某个 [Azure Active Directory 中的管理员角色](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)：

- Intune 管理员
- 全局管理员
- 服务管理员  

## <a name="get-context-sensitive-help"></a>获取上下文相关帮助
登录到 Azure 门户并打开 Intune 后，可以从 Azure 门户中的任何 Intune 边栏选项卡选择“帮助和支持”，以查看针对该 Intune 区域的常见问题的解决方案。

如果常见的解决方案不起作用，可以选择“支持请求”来创建新的支持请求，该请求会打开 Azure“帮助 + 支持”页上的“基础知识”选项卡。 若要继续创建支持票证，请转到以下过程中的“步骤 3”：[创建在线支持票证](#create-an-online-support-ticket)。

## <a name="create-an-online-support-ticket"></a>创建在线支持票证

1. 使用 Intune 管理员凭据登录到 Azure 门户 (<https://portal.azure.com>)，选择“?” 图标，然后选择“帮助 + 支持”以转到 [Azure 帮助 + 支持](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)页。

   ![问号链接的示意图，其中突出显示了“帮助 + 支持”链接](./media/azure-get-support.png)

2. 在 Azure“帮助 + 支持”页上，选择“新建支持请求”。

   ![帮助和支持页面的示意图，其中突出显示了“新建支持请求”链接](media/azure-support-ticket-link.png)

3. 对于大多数 Intune 技术支持问题，在“基本信息”选项卡上选择以下选项：
   - **问题类型**：**技术**
   - **订阅**：<你的订阅>
   - **服务**：**Microsoft Intune**
   - **问题类型**：从下拉菜单中选择问题类型。
   - **问题子类型**：从下拉菜单中选择问题子类型。
   - **主题**：简要描述遇到的问题。

   ![“帮助 + 支持”-“新建支持请求”页上的“基本信息”选项卡的示意图](./media/get-support/help-new-support-case-basics.png)

   选择“下一步:解决方案”以继续。
4. 在“解决方案”选项卡上，查看可能有助于在不提交票证的情况下解决问题的建议步骤。 如果在查看完步骤后仍想创建支持请求，请单击“下一步:详细信息”。

   ![“帮助 + 支持”-“新建支持请求”页上的“解决方案”选项卡的示意图](./media/get-support/help-new-support-case-solutions.png)
5. 在“详细信息”选项卡上，填写问题的详细信息、支持方法、联系信息，然后单击“下一步:查看 + 创建”。

   ![“帮助 + 支持”-“新建支持请求”页上的“详细信息”选项卡的示意图](./media/get-support/help-new-support-case-details.png)
6. 查看此信息，并验证其是否正确，然后选择“创建”以提交支持请求。

   ![“新建支持请求”页上的“查看 + 创建”选项卡的示意图](./media/get-support/help-new-support-case-create.png)

<!--
  - **Support plan**: **Technical support - included** (for Intune technical issues, support is complimentary) or **Premier**
     >[!IMPORTANT]
     >- If you are a **Premier customer** and don't see **Support plan: Premier**, contact your Technical Account Manager for help linking your contract and tenant.
     >- Support for Intune, and for Intune when used with Configuration Manager, is free of charge. To review details of the Premier Support offering, see the [Description of Services](https://enterprise.microsoft.com/en-us/services/services-list/) documentation, section 5.3.3 "Advisory Services."

4. On the **Problem** blade, to make sure your request is addressed by the right subject matter expert for your problem, select the following options:

   - **Severity**
   - **Problem type**
   - **Category**

     These details also let us provide **Related help** that might solve your problem without filing a ticket.

     ![Screenshot of Azure portal help and support page with Problem items filled out and displaying solutions based on your problem](./media/support-need-solutions.png)

     To help the support team research and resolve your problem, enter the following information:
    
   - **Details**
   - **Date**
   - **Time**
   - **Supplemental data**

   Choose **Next**.

5. Provide **Contact information** for this support request. Microsoft support uses this information to contact you.
6. Choose **Create** to submit your support request.
-->
>[!IMPORTANT]
>如果有计费或订阅方面的问题，可打开一个用例，通过 [Office 管理中心](https://portal.office.com/Support/SupportEntry.aspx)获取支持。

## <a name="view-support-requests"></a>查看支持请求
可以在 Azure 门户中查看支持请求。 为此，请执行以下操作：

1. 使用 Intune 管理员凭据登录到 Azure (<https://portal.azure.com>)，选择“?” 图标，然后选择“帮助 + 支持”以转到 [Azure 帮助 + 支持](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)页。

2. 在“帮助 + 支持”页上，可以查看“最近的支持请求”列表，并选择它们以查看更多详细信息。

## <a name="new-help-and-support-experience"></a>新的“帮助和支持”体验
以下信息仅在使用“设备管理”门户时适用，并且是新的“帮助和支持”体验的一部分。本次推出的参与者是在可用的 Intune 租户中随机选择的。  

Intune 的“帮助和支持”更新是一个新体验，已在 [Microsoft 365 设备管理门户](https://devicemanagement.microsoft.com)中面向部分租户（并非所有租户）提供。 本新体验与 [Microsoft 365 管理中心](https://portal.office.com/AdminPortal/Home)中的体验类似，并且在从设备管理控制台的某些位置访问时取代了以前的“帮助和支持”体验。  

在“设备管理”门户中，从“所有服务” > “设备管理”下的任何边栏选项卡中选择“帮助和支持”时，都将获得新体验（“故障排除”边栏选项卡除外）。 从“故障排除”等其他位置访问“帮助和支持”时，请使用“?” 选择控制台横幅右上角的选项，或者从左侧窗格服务列表中选择“帮助 + 支持”时，你将获得原始体验。  

在新体验中，你可以访问“需要帮助?”视图，如下图所示：  
![“设备管理”仪表板和“需要帮助?”页](./media/get-support/help-support-dashboard.png)

在此视图中，可以执行以下操作：

1. 指定有关需要帮助的[特定问题的详细信息](#specify-details-about-an-issue)  
2. [查看上下文相关的帮助](#view-context-sensitive-help)以及基于指定的详细信息的相关解决方案  
3. 使用电子邮件或电话[获取支持](#get-support)  
4. 查看先前使用此新工作流程打开的[支持案例](#view-support-cases)  

### <a name="specify-details-about-an-issue"></a>指定有关问题的详细信息
从新体验支持的位置打开“帮助和支持”时，“需要帮助?”  页会打开。 在此页上，可以指定有关问题的详细信息。 输入详细信息时，控制台会根据使用的关键字提供常见查询。 可以选择提供的选项或完成自己的问题描述。 如果输入自己的说明，请选择“获取帮助”进行提交。 提交查询后，控制台将返回上下文相关信息，以帮助解决问题。

以下是可能提交的查询示例：
  
- 无法还原 iOS 设备  
- 无法创建条件访问策略  

![在“需要帮助”页上指定问题](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>查看上下文相关帮助
选择提供的选项或提交自己的查询后，上下文相关的结果将显示在“查看解决方案”下。 这些结果包括 Intune 特定的自助指导和基于查询条件的 Web 搜索返回的其他结果。  
![“查看结果”窗格的示意图](./media/get-support/view-results.png)

### <a name="get-support"></a>获取支持
如果自助指导或基于 Web 的指导无法帮助你解决问题，则可以使用控制台创建电子邮件或电话支持问题。  
在“需要帮助?”页上，选择要使用的选项。  

- 对于电子邮件请求，请提供电子邮件地址，也可以选择在提交中添加附件。 选择“发送”以创建请求。  

  ![“电子邮件请求”窗格的示意图](./media/get-support/email-support.png)
  
- 对于电话请求，请提供电话号码。 （可选）可以包含电子邮件地址并在提交中添加附件。 选择“给我打电话”以提交请求。  

   ![“电话请求”窗格的示意图](./media/get-support/phone-support.png)

### <a name="view-support-cases"></a>查看支持案例
选择历史记录按钮以查看已创建的支持案例。  

![“查看支持案例”窗格的示意图](./media/get-support/view-support-tickets.png)

- 在此工作流程中，只能看到使用新工作流程打开的支持案例。 要查看它们，请使用设备管理控制台中的“帮助和支持”视图，该视图是新体验的一部分。 这些案例的数字长度为八位数。 此外，还可以从 Microsoft 365 管理中心查看这些案例。  

- 在帐户添加到新的帮助和支持体验之前打开的案例不会更改。 要查看它们，必须使用不属于新体验部署的帮助和支持视图。 这些案例的数字以 117 或 118 开头，长度为 15 位。  要查看在添加到新体验之前打开的支持案例，请使用 Azure 门户。 为此，请执行以下操作：

    1. 使用 Intune 管理员凭据登录到 Azure (<https://portal.azure.com>)，选择“?” 图标，然后选择“帮助 + 支持”以转到 [Azure 帮助 + 支持](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)页。

    2. 在“帮助 + 支持”页上，可以查看“最近的支持请求”列表，并选择它们以查看更多详细信息。

## <a name="additional-resources"></a>其他资源
- [联系 Microsoft Intune 的辅助电话支持](phone-support-contact.md)
- [计费和订阅管理支持](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [批量许可](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [对 Intune 问题进行故障排除](help-desk-operators.md)