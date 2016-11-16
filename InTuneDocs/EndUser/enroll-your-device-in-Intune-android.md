---
title: "在 Intune 中注册 Android 设备 | Microsoft Intune"
description: "介绍如何在 Intune 中注册 Android 设备"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6dc3173207d1e99e1bd0207f8ea5a5b137b36be1
ms.openlocfilehash: b87799b0ee8dcf98b82bd8353ca7684ede0d8bc2


---


# <a name="enroll-your-android-device-in-intune"></a>在 Intune 中注册 Android 设备

如果你的公司或学校使用 Microsoft Intune，则可以注册 Android 设备以获取对公司电子邮件、文件和其他资源的访问权限。 注册设备时，IT 部门可以管理这些工作或学校资源，使其保持安全，并使你可以自由地使用首选设备来完成工作。 若要了解有关注册的详细信息，请参阅[安装公司门户应用并注册设备后会发生什么情况？](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md)。

这些注册说明适用于 Samsung KNOX Android 设备和“本机”（非 Samsung Knox）Android 设备。 若要检查你是否拥有 Samsung KNOX 设备，请转到“设置”&gt;“关于设备”。 如果未在此处看到列出了“KNOX 版本”，则你具有本机 Android 设备。

注册前/后，系统可能会要求你选择最恰当地描述了你使用设备的方式的类别。 IT 管理员使用此类别来帮助检查你有权访问的应用。

如果尝试在 Intune 中注册设备时遇到错误，则可以[将注册错误消息发送给 IT 管理员](send-enrollment-errors-to-your-it-administrator-android.md)。

**注册 Android 设备：**

1.  从 [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) 安装免费的 Intune 公司门户应用。

2.  打开 Microsoft Intune 公司门户应用。

3.  在公司门户的“欢迎”屏幕上，点击“登录”，然后使用你的工作或学校帐户登录。

    ![android-company-portal-sign-in](./media/and-enroll-0-welcome-screen.png)   

4.  如果 IT 管理员设置了公司条款和条件，请点击“接受”以接受这些条款。

    ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5.  使用你的工作或学校帐户和密码登录公司门户应用，然后点击“登录”。

    ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6.  在“公司访问设置”屏幕上，点击“开始”。

    ![“公司访问设置”屏幕](./media/and-enroll-4a-comp-access-setup.png)

7.  在**为什么要注册设备？**屏幕上，阅读注册设备时你可以执行的操作，然后点击**继续**。

    ![“为什么要注册设备？”屏幕](./media/and-enroll-4b-why-enroll.png)

8.  查看 IT 管理员在你的设备上可以看到和不可以看到的内容的列表，然后点击“继续”。

    ![隐私设置](./media/and-enroll-4c-we-care-privacy.png)

9.  在“接下来会发生的情况”屏幕上，阅读注册期间会发生的情况，然后点击“注册”。

    ![“接下来会发生的情况”屏幕](./media/and-enroll-4d-what-comes-next.png)

10.  如果在使用 Android 6.0 或更高版本，则执行此步骤。 否则，请转到下一步。

    如果 IT 管理员设置了特定策略，则你可能会看到以下消息：
    -   **是否允许公司门户发起和管理电话呼叫？**

        ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

    如果看到此消息，请点击“允许”。 点击“允许”是安全的，因为 **Microsoft 绝不会发起或管理电话呼叫**！ 消息文本由 Google 管控，Microsoft 无法更改。 允许访问时，只需让设备将设备的国际移动台设备标识 (IMEI) 编号发送给 Intune。 IMEI 编号类似于序列号，可唯一地标识移动设备。

    如果拒绝访问，下次登录到公司门户时将再次出现此消息，但是你可以点击“不再询问”框关闭以后接收此消息。 如果你稍后决定允许访问，请转到**设置** &gt; **应用** &gt; **公司门户** &gt; **权限** &gt; **手机**，然后开启权限。

    -   **是否允许公司门户访问你的联系人？**

        ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

    如果看到此消息，请点击“允许”。 点击“允许”是安全的，因为 **Microsoft 绝不会访问你的联系人！** 消息文本由 Google 管控，Microsoft 无法更改。 当你允许访问时，它只允许公司门户应用创建、使用和管理你的工作账户。

    如果拒绝访问，下次登录到公司门户时将再次出现此消息，但是你可以点击“不再询问”框关闭以后接收此消息。 如果你稍后决定允许访问，请转到**设置** &gt; **应用** &gt; **公司门户** &gt; **权限** &gt; **手机**，然后开启权限。

11.  在“激活设备管理员”屏幕上，点击“激活”。

    ![“激活设备管理员”屏幕](./media/and-enroll-5-activate.png)

12.  按照提示输入 PIN 或密码。 如果已经在此设备上设置 PIN 或密码，将不会显示此屏幕或要求你输入新的 PIN 或密码。

    ![输入 PIN 或密码](./media/and-enroll-6-PIN-native.png)

13.  如果你使用的是 Samsung Knox 设备，请点击“确认”，你将看到一条指示正在注册设备的消息。 如果你使用的是本机 Android 设备，则只需注意下面的屏幕，其中显示正在注册设备。

    ![Samsung KNOX 隐私策略](./media/and-enroll-7-knox-privacy-policy.png)

    此屏幕显示正在注册设备。

    ![注册设备屏幕](./media/and-enroll-8-device-enrolling.png)

14. “公司访问设置”屏幕出现时，点击“继续”。 如果消息指示你的设备不兼容，请按照说明修复该问题，然后点击“继续”。

    ![“公司访问设置”屏幕](./media/and-enroll-9-comp-access-setup.png)  

11. 在“公司访问设置完成”屏幕上，点击“完成”。 你的设备现已注册。

    ![“公司访问设置完成”屏幕](./media/and-enroll-10-comp-access-setup-complete.png)

你需转到“设置”&gt;“安全性”，然后打开“未知源”才能尝试安装公司应用。 如果你在尝试安装应用前未打开此选项，则会看到以下消息：“已阻止安装”。 出于安全性考虑，你的设置已被设置为阻止安装未知来源的应用。” 你可点击错误对话框上的“设置”以转到“未知来源”选项。

仍需要帮助？ 请联系 IT 管理员（访问[公司门户网站](http://portal.manage.microsoft.com)获取联系信息），或写邮件给 Microsoft Android 团队（地址为 wintunedroidfbk@microsoft.com.）



<!--HONumber=Nov16_HO1-->


