---
# required metadata

title: 向 Microsoft Intune 的 30 天评估添加用户 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9e40999b-46f7-447b-8974-72af82bec7ef

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 向 Microsoft Intune 的 30 天评估添加用户
完成帐户注册后，使用“新用户”向导将单个用户帐户添加到 Intune，或使用“批量添加用户”向导来批量添加用户（请参阅本部分中的说明）。  开始使用之前，了解 Intune 对管理员帐户的处理方式非常重要。

租户管理员使用 Office 365 管理中心来将用户添加到 Microsoft Intune“用户组”。 添加用户到“用户组”   会将 Intune 订阅许可证分配给用户，这也正是让这些用户能够显示在 Microsoft Intune 管理控制台中的方式。

与普通用户帐户不同，Intune 的管理员帐户不是在 Office 365 管理中心中创建的。 而是通过使用“管理权管理”下“管理”工作区中的管理控制台，将只读访问或完全访问管理权限分配给用户。 分配到只读访问权限的服务管理员无法更改 Intune 设置，但可以查看数据和运行报表。 具有完全访问权限的服务管理员具有所有可用的管理权限。

通过使用 Intune 管理控制台，你可以查看租户管理员信息，但不能创建租户管理员。 默认情况下，订阅所有者将成为你的 Microsoft Intune 服务的租户管理员并具有对 Office 365 管理中心和 Intune 管理控制台的完全访问权限。 我们建议使用 Office 365 管理中心创建至少一个额外的租户管理员帐户，以帮助委派任务和确保不会由于你忘记密码而无法使用 Intune 服务管理员帐户。

## 添加单独的用户帐户
使用以下步骤在评估租户中创建其他的用户帐户。 请记住，你添加的每个用户帐户都会计入作为 Intune 免费评估的一部分得到的 100 个许可证之一。

1.  在 [Office 365 管理中心](http://go.microsoft.com/fwlink/p/?LinkId=698854)中，选择“添加用户” &gt; “新建”&gt; “用户”以启动“新建用户”向导。

2.  在 **“详细信息”** 页上，填写必填字段。

3.  在“设置”  页上，为用户设置“位置”  。

4.  在“组”页上，单击“下一步”以接受默认值并将 Intune 的许可证分配给用户的帐户。

5.  在 **“电子邮件”** 页上指定最多五个电子邮件地址，这些电子邮件地址将接收包含帐户的用户名和临时密码的通知。 用分号 (;) 分隔多个电子邮件地址。 完成后，选择“创建”将用户添加到订阅。

6.  在 **“结果”** 页上，可以查看新帐户名称及其临时密码。 Intune 会自动创建临时密码。

7.  当新的用户出现在 Office 365 管理中心中时，验证已成功创建新用户：

    1.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，单击“管理” &gt; “公司门户”，然后滚动到屏幕底部。 复制“Intune 公司门户”下方显示的 URL

    2.  以“隐私模式”打开新浏览器窗口（在 Internet Explorer 中，选择“工具” &gt; “InPrivate 浏览”），或在其他设备上打开新浏览器窗口，然后导航到你在上一步中复制的 URL。 用户第一次登录时，必须为帐户提供新密码。

## 批量添加用户
要批量添加用户到 Intune，请使用“批量添加用户”向导上载包含用户数据的逗号分隔值 (CSV) 文件。 可通过向导中的链接下载空白模板和示例 CSV 文件。 CSV 文件的第一行必须以正确的顺序包含每个用户数据列标签。 然后，你必须为 CSV 文件中的每个用户包括“用户名”（如 **bob@contoso.com**）和“显示名称”（如 **Bob Kelly**）

1.  在 [Office 365 管理中心](http://go.microsoft.com/fwlink/p/?LinkId=698854)中，选择“用户” &gt; “新建”

2.  选择“批量添加”以启动“批量添加用户”向导。

3.  在“选择文件”页上，选择“浏览”以指定并加载计算机中的现有 CSV 文件。 你也可以通过使用向导中的链接来下载示例 CSV 文件或空白模板文件。

4.  在“验证”页上查看结果，然后选择“查看”以了解更多详细信息。

5.  在“设置”页上，确认登录状态为“已允许”，并设置“位置”。 这些设置将应用于通过 CSV 文件添加的所有用户帐户。

6.  在“组”页上，选择“下一步”以接受默认值并将 Intune 的许可证分配给通过 CSV 文件添加的所有用户帐户。 默认情况下，复选框处于选定状态，会为每个帐户分配 Intune 的许可证。

7.  在“电子邮件”页上指定最多五个电子邮件地址，用于接收 Intune 为每个帐户创建的包含用户名和临时密码的通知。 用分号 (;) 分隔多个电子邮件地址。 选择“创建”将用户添加到订阅。

8.  在“结果”  页上，你可以查看每个用户帐户的帐户名称和临时密码。

通过导入添加的每个用户帐户现在将出现在 Office 365 管理中心的“用户”节点中。 新用户第一次登录时，必须为自己的用户帐户指定新密码。

### 后续步骤
祝贺你！ 你刚完成了“Microsoft Intune 评估”演练的步骤 2。

>[!div class="step-by-step"]

>[&larr; **注册评估**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)     [**创建组** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)  


<!--HONumber=May16_HO2-->


