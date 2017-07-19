---
title: "注册 30 天免费试用版"
titleSuffix: Intune on Azure
description: "如何在 Azure 上注册 Intune。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 06/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7dafdb974dd975eaa7f3268119de6c047c50f858
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal"></a>注册 Azure 门户的 Microsoft Intune 免费试用版


本文将指导你注册 Azure 门户的 Intune 独立试用版。

1. 请访问 [Intune 注册](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)页面并填写表单，注册试用订阅。
account-sign-up.md

  如果大多数 IT 操作和用户都位于不同于你所在地的区域，则建议在“公司位于哪里？”下选择该区域设置。

2. 注册过程结束后，将收到一条包含新帐户信息的消息。 <br/> ![帐户信息的图像](./media/2-end-of-sign-up-process.png) <br/>此时如果单击“准备就绪”，则将转到 Office 365 管理中心，可以在此将用户添加到测试环境。 <br/><br/>但是，如果想直接进入 Intune Azure 门户，请打开一个新的浏览器窗口，然后在地址栏中输入 **https://portal.azure.com**。 将转到 Azure 登录页，可以在此使用获得的凭据进行登录。 任何时候想登录 Intune 试用版时都请使用该地址。 <br/> ![Azure 门户登录页的图像](./media/azure-portal-signin.png)

第一次登录到 Intune Azure 门户时，可能不会在 Azure 仪表板上看到 Intune。 将 Intune 服务添加到 Azure 的仪表板：
1. 在仪表板左侧的 Azure 服务列表中选择“更多服务 >”，并在搜索框中输入“Intune”。
2. 从该列表中选择“Intune”，然后选择星号将服务添加到服务列表中。<br/> ![从服务列表中选择 Intune 这一操作的图像](./media/azure-add-intune1.png)
3. 然后在服务列表中选择“Intune”以打开 Intune 仪表板。

注册试用版时，在注册过程中提供的电子邮件地址还将收到一封电子邮件，该电子邮件中包含帐户信息。 该电子邮件用于确认试用版处于活动状态。



## <a name="keeping-the-admin-experiences-straight"></a>流畅高效的管理体验


有三个门户用于 Intune Azure 门户：
- Azure 中的 Intune 仪表板 ([portal.azure.com](https://portal.azure.com))，在此可以了解 [Azure 门户中的 Intune 功能](what-is-intune.md)。
- Office 365 管理中心 ([portal.office.com](https://portal.office.com))，可以在此添加和管理用户（如果未使用 Azure Active Directory 来达到此目的）。 还可以管理帐户的帐单和支持等其他方面。
- 经典 Intune 管理控制台 ([manage.microsoft.com](https://manage.microsoft.com))，可以在此了解尚未添加到 Azure 的功能。

通常情况下，将在 Intune 仪表板中进行操作，如下所示。 在 Intune 管理控制台中，可设置及管理组、策略、设备和应用。

可通过选择仪表板顶部的“经典门户”，从仪表板转到经典 Intune 管理控制台。

若要返回 Intune Azure 门户，请在浏览器地址栏中输入 https://portal.azure.com，然后再次从服务列表选择 Intune。

 ![Intune 仪表板图像](./media/intune-azure-dashboard.png)


若要添加和管理用户及帐户的其他方面（包括帐单和支持），需要使用 Office 365 管理中心，如下所示。

![Office 365 管理中心图](./media/office-admin-center.png)

若要从 Office 365 管理中心转到 Intune 仪表板，请在浏览器地址栏中输入 https://portal.azure.com。 在服务列表中选择“Intune”。

若要从 Intune 返回到 Office 365 管理中心，请在浏览器地址栏中输入 https://portal.office.com。 如果已登录到 Intune，将直接转到 Office 365 管理中心。

## <a name="next-steps"></a>后续步骤

### <a name="intune-on-azure"></a>Azure 上的 Intune
了解有关 [Azure 门户中的 Intune](what-is-intune.md) 的详细信息
### <a name="classic-intune"></a>经典 Intune
评估方案：[在 Microsoft Intune 中评估移动设备管理](https://docs.microsoft.com/intune-classic/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>与其他产品的集成
深入了解如何在 Intune 中使用 Azure Active Directory 用户帐户：
- [身份要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [目录同步路线图](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [多重身份验证要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

深入了解如何使用 [Intune 与 System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)
