---
title: 快速入门 - 向不符合要求的设备发送通知
titleSuffix: Microsoft Intune
description: 本快速入门将使用 Microsoft Intune 将电子邮件通知发送到不符合的设备。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 148320dc55ee044c057222a2316077396040882d
ms.sourcegitcommit: d2ac912b834c4840de9cc92ba1815b6ecfbfb52b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483034"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>快速入门：将通知发送到不符合的设备

本快速入门将使用 Microsoft Intune 向具有不符合要求的设备的员工发送电子邮件通知。

默认情况下，当 Intune 检测到不符合的设备时，会立即将设备标记为不符合。 然后 Azure Active Directory (AAD) [条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)会阻止设备。 设备不符合要求时，Intune 允许向不符合的设备添加操作，这样可以灵活地决定要执行的操作。 例如，可以在阻止不符合的设备之前为用户提供符合条件的宽限期。

设备不满足符合性时，你可以执行的操作之一是向这些最终用户发送电子邮件。 此外，还可先自定义电子邮件通知，再将其发送给最终用户。 具体来说，可自定义收件人、主题和邮件正文，包括自定义公司徽标和联系人信息。 Intune 还在电子邮件通知中说明了关于不符合设备的详细信息。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件
- 使用设备符合性策略阻止设备使用公司资源时，必须设置 AAD 条件访问。 如果已完成[创建设备符合性策略](quickstart-set-password-length-android.md)快速入门，则可使用 Azure Active Directory。 有关 AAD 的详细信息，请参阅 [Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)和[使用 Intune 条件访问的常见方式](conditional-access-intune-common-ways-use.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以[全局管理员](users-add.md#types-of-administrators)或 Intune [服务管理员身份](users-add.md#types-of-administrators)登录 [Intune](https://aka.ms/intuneportal) 门户。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="create-a-notification-message-template"></a>创建通知邮件模板

要向用户发送电子邮件，请创建通知消息模板。 设备不符合要求时，在模板中输入的详细信息将显示在发送给用户的电子邮件中。

1. 在 Intune 中，选择“设备符合性” > “通知” > “创建通知”    。 
2. 输入以下信息：

   - **名称**：Contoso 管理员 
   - **主题**：*设备符合性*
   - **消息**：当前设备不满足组织符合性要求。 
   - **电子邮件标头 – 包括公司徽标**：设置为“已启用”以显示组织的徽标  。
   - **电子邮件页脚 – 包括公司名称**：设置为“已启用”以显示组织的名称  。
   - **电子邮件页脚 – 包括联系人信息**：设置为“已启用”以显示组织的联系人信息  。

   ![Intune 中符合性通知邮件的示例](./media/quickstart-send-notification-01.png)

3. 在完成信息添加后，选择“创建”  。 通知邮件模板已就绪，可供使用。

    > [!NOTE]
    > 此外，还可以编辑先前创建的“通知”模板。

有关设置公司名称、公司联系人信息和公司徽标的详细信息，请参阅[公司信息和隐私声明](company-portal-app.md#company-information-and-privacy-statement)、[支持部门信息](company-portal-app.md#support-information)以及[公司标识品牌自定义](company-portal-app.md#company-identity-branding-customization)。 

## <a name="add-a-noncompliance-policy"></a>添加不符合性策略

创建设备符合性策略时，Intune 会自动为非符合性创建操作。 设备不满足符合性策略时，Intune 会自动将设备标记为不符合。 可自定义将设备标记为不符合的时长。 此外，还可以在创建符合性策略或更新现有符合性策略时添加其他操作。 

以下步骤将为 Windows 10 设备创建符合性策略。

1. 在 Intune 中，选择“设备符合性”  。
2. 选择“策略” > “创建策略”   。
3. 输入以下信息：

   - **名称**：Windows 10 符合性 
   - **说明**：Windows 10 符合性策略 
   - **平台**：Windows 10 及更高版本

4. 选择“设置” > “系统安全”，显示与设备安全相关的设置   。
5. 将“需要密码才可解锁移动设备”设置为“需要”   。 此设置指定在允许访问用户移动设备上的信息之前是否要求用户输入密码。 
6. 将“最短密码长度”设置为“6”   。 此设置指定密码的最小位数或最小字符数。

    <img alt="System Security settings for a new compliance policy" src="./media/quickstart-send-notification-02.png" width="600">

7. 依次选择“确定”   > “确定”   > “创建”  即可创建合规性策略。
8. 选择“属性” > “针对非符合性的操作” > “添加”    。
9. 在“操作”下拉框中，确认选中“向最终用户发送电子邮件”   。
10. 选择“消息模板” > “Contoso 管理员” > “选择”以选择先前在本主题中创建的消息模板    。
11. 选择“ADD”   > “确定”   > “保存”  以保存所做的更改。

## <a name="assign-the-policy"></a>分配策略

可以将符合性策略分配给特定用户组或所有用户。 当 Intune 识别出设备不符合时，将通知用户他们必须更新其设备以满足符合性策略。 可使用以下步骤分配策略。

1. 选择前面创建的“Windows 10 符合性”策略  。
2. 选择“分配”  。
3. 在“分配给”下拉框中，选择“所有用户”   。 此操作将选择所有用户。 任何具有“Windows 10 及更高版本”设备且不符合此符合性策略的用户都将收到通知  。

    > [!NOTE]
    > 可以在分配符合性策略时包含和排除组。

4. 单击 **“保存”** 。

如果已成功创建并保存该策略，则它将显示在“设备符合性”-“策略”列表中  。 请注意将列表中的“已分配”设置为“是”   。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你使用了 Intune 来为员工的 Windows 10 设备创建和分配符合性策略，以要求提供长度为至少六个字符的密码。 有关为 Windows 设备创建符合性策略的详细信息，请参阅[在 Intune 中为 Windows 设备添加设备符合性策略](compliance-policy-create-windows.md)。

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：添加并分配客户端应用](quickstart-add-assign-app.md)
