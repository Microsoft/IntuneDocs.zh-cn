---
title: 快速入门 - 免费试用 Microsoft Intune
titlesuffix: ''
description: 在本快速入门中，将创建免费试用版订阅、了解支持的配置和网络要求，并能根据需要配置自己的域名。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2257253d023c97d14418b3566c0c493a3cd8f615
ms.sourcegitcommit: 279f923b1802445e501324a262d14e8bfdddabde
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2018
ms.locfileid: "53737910"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>快速入门：免费试用 Microsoft Intune 

Microsoft Intune 可帮助你通过管理设备和应用保护员工的企业数据。 在本快速入门中，将创建免费版订阅以在测试环境中试用 Intune。

Intune 通过 Microsoft Azure 门户管理的基于云的安全服务提供移动设备管理 (MDM) 和移动应用管理 (MAM)。 使用 Intune，可以确保正确配置、访问和更新员工的企业资源（数据、设备和应用），从而满足公司的符合性策略和要求。 

## <a name="prerequisites"></a>必备条件
在设置 Microsoft Intune 之前，请查看以下要求：

   - [支持的操作系统和浏览器](supported-devices-browsers.md) 
   - [网络配置要求和带宽](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>注册 Microsoft Intune 免费试用版

可以免费试用 Intune 30 天。 如果已有工作或学校帐户，请使用该帐户进行“登录”，并将 Intune 添加到订阅中。 否则，也可通过“注册”创建新帐户，以便为组织使用 Intune。

> [!IMPORTANT]
> 注册新帐户后，不能合并现有的工作或学校帐户。

1. 转到 [Microsoft Intune 试用版](https://go.microsoft.com/fwlink/?linkid=2019088)页面并填写表格。

    ![Microsoft Intune 试用版帐户注册网页的屏幕截图](./media/account-sign-up-site-full-browser.png)

    如果大多数 IT 操作和用户都不位于你所在的区域，则可能需要在“国家或地区”下选择该区域设置。 Azure 使用你的区域信息来提供正确的服务。 此设置以后无法更改。

2. 用公司名称加上“.onmicrosoft.com”来创建自己的帐户。 

    ![Microsoft Intune 试用版帐户新凭据进程的屏幕截图](./media/account-sign-up-site-user-id.png)

    如果组织使用自己的自定义域而不采用“.onmicrosoft.com”，可以在本文后面介绍的 Office 365 管理门户中进行更改。

3. 在注册过程结束时查看新帐户信息。

    ![帐户信息的图像](./media/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>登录到 Azure 门户

1. 打开新的浏览器窗口，在地址栏中输入 https://portal.azure.com 。 
2. 使用在上述步骤中获得的凭据。

    ![Azure 门户登录页的图像](./media/azure-portal-signin.png)

3. 要在 Azure 端口中查看 Microsoft Intune ，从页面左侧的边栏中选择“所有服务”。
4. 在筛选器框中搜索 Microsoft Intune 并选择它。
5. 选择星形图标，将 Intune 添加到收藏的服务列表底部，并打开 Intune 仪表板。

注册试用版时，还将收到一份电子邮件消息，其中包含你在注册过程中提供的帐户信息和电子邮件地址。 该电子邮件用于确认试用版处于活动状态。

> [!TIP]
> 使用 Azure 门户时，在常规模式而不是专用模式下使用浏览器，可能会获得更好的效果。

## <a name="set-the-mdm-authority-to-intune"></a>将 MDM 机构设置为 Intune

在登录 Azure 门户并选择 Intune 后，可能会看到一条橙色横幅，表示尚未设置 MDM 机构。 移动设备管理 (MDM) 机构设置决定了管理设备的方式。 必须先设置 MDM 机构，然后用户才能注册设备来进行管理。

要将 MDM 机构设置为 Intune，请执行以下步骤。

1. 打开新的浏览器窗口，在地址栏中输入 https://portal.azure.com 。 
2. 选择“所有服务” > “Microsoft Intune”。
3. 选择表示尚未启用设备管理的横幅，或者如果没有立即看到横幅，请选择“设备注册”。 如果尚未启用设备管理，将显示“选择 MDM 机构”边栏选项卡。

    > [!NOTE]
    > 如果尚未设置 MDM 机构，则仅显示橙色横幅。

    ![“选择 MDM 机构”边栏选项卡的图像](./media/choose-mdm-authority.png) 

4. 在“选择 MDM 机构”下，将 MDM 机构设置为“Intune MDM 机构”。

有关 MDM 机构的更多信息，请参阅[设置移动设备管理机构](mdm-authority-set.md)。

## <a name="configure-your-custom-domain-name-optional"></a>配置自定义域名（可选）

如上所述，若想组织使用自己的自定义域而不采用“.onmicrosoft.com”，可以在 Office 365 管理门户中进行更改。 将添加、验证并配置自己的自定义域名。  

> [!IMPORTANT]
> 无法重命名或删除初始“onmicrosoft.com”域名。 可以添加、验证或删除用于 Intune 的自定义域名，以保证业务标识清晰。

1. 转到 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)并使用管理员帐户登录。

2. 在导航窗格中，选择“设置” > “域” > “添加域”。

3. 输入自定义域名。 然后选择“下一步”。

   ![Office 365 管理中心的屏幕截图 - 添加域](./media/domain-custom-add.png)

4. 验证你是否是前面输入的域的所有者。 
    
    若选择“通过电子邮件发送代码”，会将向域中已注册的联系人发送电子邮件。 收到电子邮件后，请复制该代码，并将其输入标为“在此键入验证码”的字段。 如果验证码匹配，该域将添加至你的租户。 显示的电子邮件可能看起来不太熟悉。 一些注册机构会隐藏真实的电子邮件地址，然后隐藏注册域时提供的内容。

   ![Office 365 管理中心的屏幕截图 - 验证域](./media/domain-custom-verify.png)

   > [!NOTE]
   > 有关 TXT 记录验证的详细信息，请参阅[在 Office 365 的任何 DNS 托管提供商处创建 DNS 记录](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166)。

## <a name="admin-experiences"></a>管理员体验

可使用两个门户：
- Azure 中的 Intune 仪表板 ([portal.azure.com](https://portal.azure.com))，在此可以了解 [Intune 功能](what-is-intune.md)。 通常情况下，将在 Intune 仪表板中进行操作。
- 如果没有使用 Azure Active Directory 来添加和管理用户，可以在 Office 365 管理中心 ([portal.office.com](https://portal.office.com)) 进行此类操作。 还可以管理帐户的帐单和支持等其他方面。

## <a name="next-steps"></a>后续步骤

在本快速入门中，已创建免费版订阅以在测试环境中试用 Intune。 有关设置 Intune 的详细信息，请参阅[设置 Intune](setup-steps.md)。

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：创建用户并向用户分配许可证](quickstart-create-user.md)
