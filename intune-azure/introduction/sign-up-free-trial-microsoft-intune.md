---
title: "注册 30 天免费试用版 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：如何在 Azure 上注册 Intune。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cd98141b4b377f0013607f2a2ebb93a93cd7f0ce
ms.openlocfilehash: ce69e7efbee286839a1bf3440db692bd237b0e06


---

# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal-preview"></a>注册 Azure 门户预览的 Microsoft Intune 免费试用版

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

本文将指导你注册 Azure 门户预览的 Intune 独立试用版。 <!---and prepares your trial with some users so that you can then follow the associated evaluation guide to see how Intune manages mobile devices. ---> <!---or app data when devices are not enrolled in Intune.--->

<!--- ## Assumptions
This sign-up article and the evaluation guide assume you are using the trial for evaluation purposes only and intend to start with a clean environment when you subscribe.

To make it easy for you to get started with the trial, we are setting up a very simple environment that uses only Intune and assumes it will be your sole method of managing devices (known as the mobile device management authority). However, throughout the guide we will point you to deeper technical content if you want to explore farther.

You can do everything in the trial version that you can do in a subscription version; the only difference is you are limited to 100 user accounts in the trial.--->

<!--- ## Sign up for your trial--->
1. 请访问 [Intune 注册](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)页面并填写表单，注册试用订阅。

 <!--- If you have a work or school account and want to use that for your Intune trial, follow [these sign-in instructions](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) instead. However, this article assumes that you are not using such an account.---><br/> ![注册页的图像](./media/1-clicking-try.png)

 > [!TIP]
> 如果大多数 IT 操作和用户都位于不同于你所在地的区域，则建议在“公司位于哪里？”下选择该区域设置。

2. 注册过程结束时，将收到一条包含新帐户信息的消息。 <br/> ![帐户信息的图像](./media/2-end-of-sign-up-process.png) <br/>此时如果单击“准备就绪”，则将转到 Office 365 管理中心，可以在此将用户添加到测试环境。 <br/><br/>但是如果想直接进入 Intune Azure 门户预览版，请打开新的浏览器窗口，然后在地址栏中输入 **https://portal.azure.com**。 将转到 Azure 登录页，可以在此使用获得的凭据进行登录。 任何时候想登录 Intune 试用版时都请使用该地址。 <br/> ![Azure 门户登录页的图像](./media/azure-portal-signin.png)

第一次登录到 Intune Azure 预览版 时，可能不会在 Azure 仪表板上看到 Intune。 将 Intune 服务添加到 Azure 的仪表板：
1. 在仪表板左侧的 Azure 服务列表中选择“更多服务 >”，并在搜索框中输入“Intune”。
2. 从该列表中选择“Intune”，然后选择星号将服务添加到服务列表中。<br/> ![从服务列表中选择 Intune 这一操作的图像](./media/azure-add-intune1.png)
3. 然后在服务列表中选择“Intune”以打开 Intune 仪表板。

注册试用版时，在注册过程中提供的电子邮件地址还将收到一封电子邮件，该电子邮件中包含帐户信息。 该电子邮件用于确认试用版处于活动状态。


<!--- ## Add users
Before you leave the Office 365 Admin center for Intune, you need to add some users to your trial account.

In the Office 365 Admin center, you can add users individually or in bulk by uploading a .csv file. We will do both to set up your trial. However, in your production environment, you will probably want to take advantage of your Azure Active Directory user accounts, which you can learn more about in our [Getting Started guide](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) and in the [Next steps](#Next-steps) section of this article.

### Add an individual user
1. Choose either of the options to add a use to open a form that allows you to create a user. Only the items starred with an asterisk (\*) are required.
![Image of add user button options](./media/sign-up/add-user.png)


2.  When you add the user, the final step will be to send the user an email with their temporary Intune password. For the purposes of this evaluation, use your own work email address so you will receive the log-on information and see the email your users will get. You can then use these user identities to enroll test devices.<br/>

 ![Image of add user final step](./media/sign-up/new-user-2.png)

3. If you want to assign a user an admin role after you create it, you can edit the role in the Office 365 Admin center by selecting the user name from your list of users, and then choosing **Edit** in the Role line to see the list of user roles you can select from and assign to that user.

 ![Image of user  role options](./media/sign-up/change-user-role.png)

### Import multiple users
1. You will find the wizard for importing multiple users in the **More** list.

 ![Image of option to add multiple users](./media/sign-up/add-multiple-users.png)

2. To help you set up your .csv file correctly, you can download a template file to populate with your user data. Download the .csv file that contains headers and sample user information to see exactly the kind of data is needed for each field.

 ![Image of first step in bulk enrollment wizard](./media/sign-up/bulk-enroll-step-1.png)


3. After you’ve created and saved your .csv file, choose **Browse** to select the file. Verify, and choose **Next**. Your users will be uploaded and added to your list of active users.

> [!NOTE]
> Your users won't show up in Intune until they've enrolled a device to be managed.

Now it’s time to head over to Intune to start managing your users, their devices, and their apps.--->

## <a name="keeping-the-admin-experiences-straight"></a>流畅高效的管理体验
<!---### Classic Intune
There are two portals you will use for classic Intune:
- The Office 365 Admin center ([portal.office.com](https://portal.office.com))
- The Intune administration console ([manage.microsoft.com](https://manage.microsoft.com))

Normally, you’ll do your work in the Intune administration console, shown below. This is the site where you set up and manage your groups, policies, devices, and apps.

![Image of Intune administration console](./media/sign-up/intune-admin-console.png)

However, you will use the Office 365 Admin center, shown below, to add and manage your users and other aspects of your account, including billing and support.

![Image of Office 365 Admin center](./media/sign-up/office-admin-center.png)

You can navigate from the Office 365 Admin center to the Intune admin console. The admin centers are under the last item in the left navigation pane. Choose **Intune** to open the Intune admin console in a new tab.

![Image of link to Intune administration console](./media/sign-up/link-to-intune.png)

To get from Intune back to the Office 365 Admin center, choose the **Add Users** task on the Groups Overview page.

![Image of link back to Office 365  Admin center](./media/sign-up/task-add-users.png)--->

<!---### Intune Azure preview--->
将有三个门户用于 Intune Azure 预览：
- Azure 中的 Intune 仪表板 ([portal.azure.com](https://portal.azure.com))，在此可以了解 [Azure 门户中的 Intune 功能](what-is-microsoft-intune.md)。
- Office 365 管理中心 ([portal.office.com](https://portal.office.com))，可以在此添加和管理用户（如果未使用 Azure Active Directory 来达到此目的）。 还可以管理帐户的帐单和支持等其他方面。
- 经典 Intune 管理控制台 ([manage.microsoft.com](https://manage.microsoft.com))，可以在此了解尚未添加到 Azure 的功能。

通常情况下，将在 Intune 仪表板中进行操作，如下所示。 在 Intune 管理控制台中，可设置及管理组、策略、设备和应用。

可通过选择“打开经典 Intune 门户”磁贴，从仪表板转到经典 Intune 管理控制台。

若要返回 Intune Azure 预览版，请在浏览器地址栏中输入 https://portal.azure.com，然后再次从服务列表选择“Intune”。

 ![Intune 仪表板图像](./media/intune-azure-dashboard.png)


但是，若要添加和管理用户及帐户的其他方面（包括帐单和支持），请使用 Office 365 管理中心，如下所示。

![Office 365 管理中心图](./media/office-admin-center.png)

若要从 Office 365 管理中心转到 Intune 仪表板，请在浏览器地址栏中输入 https://portal.azure.com。 在服务列表中选择“Intune”。

若要从 Intune 返回到 Office 365 管理中心，请在浏览器地址栏中输入 https://portal.office.com。 如果已登录到 Intune，将直接转到 Office 365 管理中心。

## <a name="next-steps"></a>后续步骤

### <a name="intune-azure-preview"></a>Intune Azure 预览
了解有关 [Azure 门户预览版中的 Intune](what-is-microsoft-intune.md) 的详细信息
### <a name="classic-intune"></a>经典 Intune
评估方案：[在 Microsoft Intune 中评估移动设备管理](https://docs.microsoft.com/intune/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>与其他产品的集成
深入了解如何在 Intune 中使用 Azure Active Directory 用户帐户：
- [身份要求](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [目录同步路线图](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [多重身份验证要求](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

深入了解如何使用 [Intune 与 System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/mdm/understand/hybrid-mobile-device-management)



<!--HONumber=Feb17_HO1-->


