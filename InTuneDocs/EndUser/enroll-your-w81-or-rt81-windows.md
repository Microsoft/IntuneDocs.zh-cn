---
# required metadata

title: 在 Intune 中注册 Windows 8.1 或 Windows RT 8.1 设备 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 28984f26-1070-4f7a-877c-669a59375c0c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: priyar
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 在 Intune 中注册 Windows 8.1 或 Windows RT 8.1 设备

如果你的公司或学校使用 Microsoft Intune，则可以注册设备以获取对公司电子邮件、文件和其他资源的访问权限。 通过注册设备可以使组织保护公司数据的安全。 若要了解有关注册的详细信息，请参阅[安装公司门户应用并在 Intune 中注册设备后会发生什么？](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)和 [IT 管理员在你的设备上可以看到和不可以看到的内容](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)。


注册 Windows 8.1 或 Windows RT 8.1 设备：

1.  在设备上，点击**设置** &gt; **电脑设置** &gt; **网络** &gt; **工作区**。

    ![nav-to-workplace](./media/W81-1-workplacejoin.png)

2.  如有必要，在“用户 ID”中输入工作单位或学校电子邮件，然后点击“加入”。

    如果不需要用户 ID，则使用登录到此设备时输入的电子邮件地址。

3.  键入你的工作或学校电子邮件的密码。

    ![type-password](./media/W81-2-workplacesettings_signin.png)

4.  在“打开设备管理”下，单击“打开”。

    ![turn-on-device-management](./media/W81-3-dev-mgt-turn-on.png)

5.  在“允许 IT 管理员提供的应用和服务”对话框中，选中“我同意”复选框，然后点击“打开”。

    ![turn-on-allow-apps-services](./media/W81-4-agree-allow-apps-services.png)

    注册成功后，你将看到下面的屏幕。

    ![enrollment-complete](./media/W81-5-enrolled-done.png)

我们还建议你安装公司门户应用，通过该应用，你可以轻松地识别和获取与你和你的角色相关的公司应用。 根据公司配置 Intune 的方式，公司门户应用可能已在注册过程中安装。 若要检查你是否具有该应用，请在应用列表中查找“公司门户”。 如果未在应用列表中看到“公司门户”，请按照这些步骤安装它。

1.  点击**开始** &gt; **应用商店**。

2.  点击“搜索”，然后输入“公司门户”。

3.  在结果列表中，点击“公司门户”。

4.  点击“安装”或“释放”。 显示的选项取决于公司配置该应用的方式。

仍需要帮助？ 请与你的 IT 管理员联系。 有关他们的联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。

### 另请参阅
[在 Intune 中注册 Windows 设备](enroll-your-device-in-intune-windows.md)</br>
[通过 Intune 使用 Windows 设备](using-your-windows-device-with-intune.md)


<!--HONumber=Jun16_HO2-->


