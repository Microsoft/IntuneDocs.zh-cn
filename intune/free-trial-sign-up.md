---
title: 注册 Microsoft Intune 的 30 天免费试用版
titleSuffix: Microsoft Intune
description: 了解如何注册 Microsoft Intune 的 30 天免费试用版。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: get-started
ms.openlocfilehash: 6492b757376c95c366d45a63b05f2ec60bdd791b
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2018
ms.locfileid: "44254116"
---
# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>注册 Microsoft Intune 免费试用版


本文将指导你注册 Azure 门户的 Intune 独立试用版。

1. 请访问 [Intune 注册](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)页面并填写表单，注册试用订阅。
2. 如果有工作或学校帐户并希望将该帐户用于 Intune 试用版，请按照[登录说明](/intune/account-sign-up)进行操作。

* 如果大多数 IT 操作和用户都位于不同于你所在地的区域，则建议在“公司位于哪里？”下选择该区域设置。

2. 注册过程结束后，将收到一条包含新帐户信息的消息。 <br/> 

![帐户信息的图像](./media/2-end-of-sign-up-process.png) <br/>

此时如果单击“准备就绪”，则将转到 Office 365 管理中心，可以在此将用户添加到测试环境。 <br/><br/>但是，如果想直接进入 Intune Azure 门户，请打开一个新的浏览器窗口，然后在地址栏中输入 https://portal.azure.com。 将转到 Azure 登录页，可以在此使用获得的凭据进行登录。 任何时候想登录 Intune 试用版时都请使用该地址。 <br/> ![Azure 门户登录页的图像](./media/azure-portal-signin.png)

第一次登录到 Intune [Azure](https://portal.azure.com) 门户时，可能不会在 Azure 仪表板上看到 Intune。 将 Intune 服务添加到 Azure 的仪表板：
1. 在仪表板左侧的 Azure 服务列表中选择“所有服务>”，并在搜索框中输入“Intune”。
2. 从该列表中选择“Intune”，然后选择星号将服务添加到服务列表中。<br/> ![在 Azure 门户中选择 Microsoft Intune 的图像](./media/azure-add-intune1.png)
3. 然后在服务列表中选择“Intune”以打开 Intune 仪表板。

注册试用版时，在注册过程中提供的电子邮件地址还将收到一封电子邮件，该电子邮件中包含帐户信息。 该电子邮件用于确认试用版处于活动状态。

## <a name="keeping-the-admin-experiences-straight"></a>流畅高效的管理体验

可使用两个门户：
- Azure 中的 Intune 仪表板 ([portal.azure.com](https://portal.azure.com))，在此可以了解 [Intune 功能](what-is-intune.md)。 通常情况下，将在 Intune 仪表板中进行操作。
- Office 365 管理中心 ([portal.office.com](https://portal.office.com))，可以在此添加和管理用户（如果未使用 Azure Active Directory 来达到此目的）。 还可以管理帐户的帐单和支持等其他方面。

## <a name="next-steps"></a>后续步骤

### <a name="integration-with-other-products"></a>与其他产品的集成
深入了解如何在 Intune 中使用 Azure Active Directory 用户帐户：
- [身份要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [目录同步路线图](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [多重身份验证要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

深入了解如何使用 [Intune 与 System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)
