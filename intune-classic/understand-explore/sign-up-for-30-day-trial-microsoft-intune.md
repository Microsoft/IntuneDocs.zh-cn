---
title: "注册 Microsoft Intune 的免费 30 天试用版 | Microsoft Docs"
description: "注册并设置 Microsoft Intune 的免费 30 天评估。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 560765fa9d9afa4a1050515e1b2304c998f8c158
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>注册 Microsoft Intune 免费试用版

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本文指导如何注册 Intune 试用版以及如何为一些用户准备试用版，然后按照相关的评估指南查看 Intune 如何管理移动设备。 <!---or app data when devices are not enrolled in Intune.--->

>[!Note]
> 从 2016 年 12 月开始，Microsoft Intune 将迁移到 Azure 门户，因此一些免费试用版注册将在 Azure 门户中完成，另外一些将在经典 Intune 中完成注册。 如果你的试用版位于 Azure 门户中，在完成本文的步骤后，你会发现 [Intune Azure 预览内容](/intune/what-is--intune)更有用。

## <a name="assumptions"></a>假设
本注册文章和评估指南假设仅将试用版用于评估目的并希望在订阅时获得一个干净的环境。

为了方便开始使用试用版，专门设置了一个非常简单的环境，该环境仅使用 Intune 并假设它是管理设备的唯一方法（称为移动设备管理机构）。 但是，在整个指南中，如果希望进一步探索，将引导进入更深层次的技术内容。

试用版的功能与订阅版相同，唯一的区别是试用版限制 100 个用户帐户。

## <a name="sign-up-for-your-trial"></a>注册试用版
请访问 [Intune 注册](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)页面并填写表单，注册试用订阅。

如果有工作或学校帐户并希望将该帐户用于 Intune 试用版，请按照[登录说明](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1)进行操作。 但是，本文及其评估指南假设不使用此类帐户。

> [!TIP]
> 如果大多数 IT 操作和用户都位于其他区域设置，则可能希望将试用版设置为该区域设置，便于进行性能测试。

### <a name="post-sign-up-considerations"></a>注册后的注意事项
注册试用版时，在注册过程中提供的电子邮件地址将收到一封电子邮件，该电子邮件中包含帐户信息。 该电子邮件用于确认试用版处于活动状态。

完成注册过程后，系统会定向到一个页面，该页面用于使用 Office 365 管理中心添加用户并为其分配许可证。 下次登录到“经典 Intune”时 (https://manage.microsoft.com) ，将自动定向到 Intune 管理控制台。

如果试用版位于“Azure 门户”中，请转到 https://portal.azure.com 并使用 Intune 试用版凭据登录。

## <a name="add-users"></a>添加用户
退出 Intune 的 Office 365 管理中心之前，需要将某些用户添加到试用帐户。

在 Office 365 管理中心内，可逐个添加用户，也可通过上传 .csv 文件批量添加。 设置试用版时将同时执行这两项操作。 但是，在生产环境中，可能希望使用 Azure Active Directory 用户帐户，可在[入门指南](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)以及本文的[后续步骤](#Next-steps)部分了解详细信息。

### <a name="add-an-individual-user"></a>添加单个用户
1. 选择任一选项添加用户，打开允许创建用户的表单。 标有星号 (\*) 的项目为必填。
![添加用户按钮选项图](./media/sign-up/add-user.png)


2.  添加用户的最后一步是向用户发送一封电子邮件，该电子邮件中提供临时 Intune 密码。 就此评估而言，请使用自己的工作电子邮件地址，接收登录信息并查看用户收到的电子邮件。 然后即可使用这些用户身份注册测试设备。<br/>

 ![添加用户的最后一步图](./media/sign-up/new-user-2.png)

3. 创建用户后，如果希望为用户分配管理员角色，可在 Office 365 管理中心内编辑角色，操作步骤是：从用户列表中选择用户名，然后在“角色”行中选择“编辑” ，查看可从中进行选择并分配给该用户的用户角色列表。

 ![用户角色选项图](./media/sign-up/change-user-role.png)

### <a name="import-multiple-users"></a>导入多个用户
1. 可在“更多”列表中找到导入多个用户的向导。

 ![添加多个用户的选项图](./media/sign-up/add-multiple-users.png)

2. 为了帮助正确设置 .csv 文件，可下载模板文件，在文件中填充自己的用户数据。 下载包含标题和示例用户信息的 .csv 文件，查看每个字段所需的确切数据类型。

 ![批量注册向导中的第一步图](./media/sign-up/bulk-enroll-step-1.png)


3. 创建并保存 .csv 文件后，选择“浏览”，选择文件。 验证，然后选择“下一步”。 用户将上传并添加活动用户列表。

> [!NOTE]
> Intune 中不会显示用户，除非注册了要管理的设备。

然后访问 Intune，开始管理用户、设备和应用。

## <a name="keeping-the-admin-experiences-straight"></a>流畅高效的管理体验
### <a name="classic-intune"></a>经典 Intune
将有两个门户用于经典 Intune：
- Office 365 管理中心 ([portal.office.com](https://portal.office.com))
- Intune 管理控制台 ([manage.microsoft.com](https://manage.microsoft.com))

通常情况下，在 Intune 管理控制台中进行操作，如下所示。 在 Intune 管理控制台中，可设置及管理组、策略、设备和应用。

![Intune 管理控制台图](./media/sign-up/intune-admin-console.png)

但是，若要添加和管理用户及帐户的其他方面（包括帐单和支持），请使用 Office 365 管理中心，如下所示。

![Office 365 管理中心图](./media/sign-up/office-admin-center.png)

可从 Office 365 管理中心导航到 Intune 管理控制台。 管理中心位于左侧导航窗格的最后一项之下。 选择 **Intune** 可在新选项卡中打开 Intune 管理控制台。

![指向 Intune 管理控制台的链接图](./media/sign-up/link-to-intune.png)

若要从 Intune 返回 Office 365 管理中心，请在“组概述”页面上选择“添加用户”任务。

![返回到 Office 365 管理中心的链接图](./media/sign-up/task-add-users.png)

### <a name="intune-azure-preview"></a>Intune Azure 预览
将有三个门户用于 Intune Azure 预览：
- Office 365 管理中心 ([portal.office.com](https://portal.office.com))
- Azure 中的 Intune 仪表板 ([portal.azure.com](https://portal.azure.com))
- 经典 Intune 管理控制台 ([manage.microsoft.com](https://manage.microsoft.com))

第一次在 Azure 中登录到 Intune 时，可能不会在 Azure 仪表板上看到它。 将 Intune 服务添加到 Azure 的仪表板：
1. 在仪表板左侧的 Azure 服务列表中选择“更多服务”>，并在搜索框中输入 Intune。
2. 从该列表中选择“Intune”，然后选择星号将服务添加到服务列表中。<br/> ![从服务列表中选择 Intune 这一操作的图像](./media/sign-up/azure-add-intune1.png)
3. 在服务列表中选择“Intune”以打开 Intune 仪表板。

通常情况下，将在 Intune 仪表板中进行操作，如下所示。 在 Intune 管理控制台中，可设置及管理组、策略、设备和应用。 可通过选择“打开经典 Intune 门户”磁贴，从仪表板转到经典 Intune 管理控制台。 若要返回 Intune Azure 预览版，请在浏览器地址栏中输入 https://portal.azure.com，然后再次从服务列表选择“Intune”。

 ![Intune 仪表板图像](./media/sign-up/intune-azure-dashboard.png)


但是，若要添加和管理用户及帐户的其他方面（包括帐单和支持），请使用 Office 365 管理中心，如下所示。

![Office 365 管理中心图](./media/sign-up/office-admin-center.png)

若要从 Office 365 管理中心转到 Intune 仪表板，请在浏览器地址栏中输入 https://portal.azure.com。 在服务列表中选择“Intune”。

若要从 Intune 返回到 Office 365 管理中心，请在浏览器地址栏中输入 https://portal.office.com。 如果已登录到 Intune，将直接转到 Office 365 管理中心。

## <a name="next-steps"></a>后续步骤
### <a name="classic-intune"></a>经典 Intune
评估方案：[在 Microsoft Intune 中评估移动设备管理](mobile-device-management-trial-guide-microsoft-intune.md)

### <a name="intune-azure-preview"></a>Intune Azure 预览
了解有关 [Azure 门户预览版中的 Intune](/intune/what-is-intune) 的详细信息

### <a name="integration-with-other-products"></a>与其他产品的集成
深入了解如何在 Intune 中使用 Azure Active Directory 用户帐户：
- [身份要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [目录同步路线图](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [多重身份验证要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

深入了解如何使用 [Intune 与 System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)

