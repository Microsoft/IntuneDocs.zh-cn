---
title: 创建 Exchange 条件访问策略
titleSuffix: Microsoft Intune
description: 在 Intune 中配置本地 Exchange 和旧版 Exchange Online Dedicated 的条件访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4962b4c75460b129f9df7729b5a34485d8ee0760
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576074"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>创建本地 Exchange 和旧版 Exchange Online Dedicated 的条件访问策略

本文介绍如何基于设备符合性配置本地 Exchange 的条件访问。

如果你具有 Exchange Online Dedicated 环境并需要确定其采用的是新配置还是旧配置，请与帐户管理员联系。 若要控制对本地 Exchange 或旧版 Exchange Online Dedicated 环境的电子邮件访问，请在 Intune 中配置本地 Exchange 的条件访问。

## <a name="before-you-begin"></a>在开始之前

在可配置条件访问之前，请先验证以下配置是否存在：

- Exchange 版本为 Exchange 2010 SP1 或更高版本  。 支持 Exchange Server 客户端访问服务器 (CAS) 阵列。

- 已安装并使用 [Exchange ActiveSync 本地 Exchange 连接器](exchange-connector-install.md)（用于将 Intune 连接到 Exchange）。

    >[!IMPORTANT]  
    >Intune 支持每个订阅有多个本地 Exchange 连接器。  但是，每个本地 Exchange 连接器特定于单一 Intune 租户，且不能用于其他任何租户。  如果你拥有多个本地Exchange组织，则可以为每个 Exchange 组织设置一个单独的连接器。

- 本地 Exchange 组织的连接器可以安装在任何能够与 Exchange 服务器通信的计算机上。

- 此连接器支持 **Exchange CAS 环境**。 Intune 支持直接在 Exchange CAS 服务器上安装连接器。 建议将其安装在单独的计算机上，因为连接器会对服务器造成额外负载。 在配置连接器时，必须对其进行设置，以便与其中一个 Exchange CAS 服务器通信。

- 必须使用基于证书的身份验证或用户凭据条目来配置 Exchange ActiveSync  。

- 当配置条件访问策略并将其面向用户时，在用户可以连接到其电子邮件前，他们使用的设备  必须：
  - **已注册**到 Intune 或是已加入域的 PC。
  - **已在 Azure Active Directory 中注册**。 此外，还必须向 Azure Active Directory 注册客户端 Exchange ActiveSync ID。

- Azure AD 设备注册服务 (DRS) 会对 Intune 和 Office 365 客户自动激活。 已经部署了 ADFS 设备注册服务的用户不会在他们本地的 Active Directory 上看到已注册的设备。 **这不适用于 Windows 电脑和 Windows Phone 设备**。

- **符合**部署到该设备的设备符合性策略。

- 如果设备不满足条件访问设置，则用户会在登录时会看到以下消息的其中一条：
  - 如果设备未向 Intune 注册，或未在 Azure Active Directory 中注册，则会显示一条消息，其中包含有关如何安装公司门户应用、注册设备和激活电子邮件的说明。 此过程也将设备的 Exchange ActiveSync ID 和 Azure Active Directory 中的设备记录相关联。
  - 如果设备不合规，则会显示一条消息，引导用户转到 Intune 公司门户网站或公司门户应用。 在公司门户中，可以找到问题的详细信息和纠正方法。

### <a name="support-for-mobile-devices"></a>对移动设备的支持

- Windows Phone 8.1 及更高版本
- iOS/iPadOS 上的本机电子邮件应用。
- EAS 邮件客户端（如 Android 4 或更高版本上的 Gmail）。
- EAS 邮件客户端 Android 工作配置文件设备  ：Android 工作配置文件设备上仅支持工作配置文件中的 Gmail 和 Nine Work for Android Enterprise    。 为了使条件访问适用于 Android 工作配置文件，必须为 Gmail 或 Nine Work for Android Enterprise 应用部署电子邮件配置文件，还要将这些应用部署为必需的安装。

> [!NOTE]
> Microsoft Outlook for Android 和 Microsoft Outlook for iOS/iPadOS 不通过 Exchange 本地连接器支持。 如果想要将 Azure Active Directory 条件访问策略和 Intune 应用保护策略与本地邮箱的 Outlook for iOS/iPadOS 和 Outlook for Android 配合使用，请参阅[将混合新式身份验证与 Outlook for iOS/iPadOS 和 Outlook for Android 配合使用](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)。

### <a name="support-for-pcs"></a>对 PC 的支持

Windows 8.1 和更高版本上的本机邮件  应用程序（使用 Intune 向 MDM 注册时）

## <a name="configure-exchange-on-premises-access"></a>配置 Exchange 内部部署访问权限

在你可以使用以下过程来设置 Exchange 本地访问控制之前，必须为本地 Exchange 至少配置一个 [Intune 本地 Exchange 连接器](exchange-connector-install.md)。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 转到“租户管理” > “Exchange 访问”，然后选择“Exchange 本地访问”    。

3. 在“Exchange 本地访问”  窗格上，选择“是”  以“启用 Exchange 本地访问控制”  。

   > [!div class="mx-imgBorder"]
   > ![Exchange 本地访问屏幕的示例屏幕截图](./media/conditional-access-exchange-create/exchange-on-premises-access.png)

4. 在“分配”  下，选择“选择要包含的组”  ，然后选择一个或多个要配置访问权限的组。

   所选组的成员具有适用于本地 Exchange 访问的条件访问策略。 接收此策略的用户必须在 Intune 中注册其设备，并符合合规性配置文件，然后才能访问本地 Exchange。

   > [!div class="mx-imgBorder"]
   > ![选择要包含的组](./media/conditional-access-exchange-create/select-groups.png)

5. 若要排除组，请选择“选择要排除的组”  ，然后选择一个或多个不满足在访问本地 Exchange 之前注册设备并符合合规性配置文件的要求的组。

   选择“保存”  以保存配置，并返回到“Exchange 访问”  窗格。

6. 接下来，配置 Intune 本地 Exchange 连接器的设置。 在控制台中，选择“租户管理” > “Exchange 访问”> “Exchange ActiveSync 本地连接器”，然后选择要配置的 Exchange 组织的连接器    。

7. 对于“用户通知”  ，选择“编辑”  以打开“编辑组织”  工作流，可以在其中修改“用户通知”  消息。

   > [!div class="mx-imgBorder"]
   > ![“编辑组织”工作流的“通知”示例屏幕截图](./media/conditional-access-exchange-create/edit-organization-user-notification.png)

   如果用户的设备不符合要求并且他们希望访问本地 Exchange，则修改发送给用户的默认电子邮件。 消息模板使用的是标记语言。 键入时还可看到消息的预览显示情况

   选择“查看并保存”，然后选择“保存”   ，保存编辑内容以完成 Exchange 本地访问的配置。

   > [!TIP]
   > 若要了解有关标记语言的详细信息，请参阅这篇维基百科[文章](https://en.wikipedia.org/wiki/Markup_language)。

8. 接下来，选择“高级 Exchange ActiveSync 访问设置”   以打开“高级 Exchange ActiveSync 访问设置”工作流，可以在其中配置设备访问规则。

   > [!div class="mx-imgBorder"]
   > ![“编辑组织”工作流的“高级设置”示例屏幕截图](./media/conditional-access-exchange-create/edit-organization-advanced-settings.png)

   - 对于“非托管设备访问”，请设置不受条件访问或其他规则影响的设备访问的全局默认规则  ：

     - **允许访问** - 所有设备均可立即访问本地 Exchange。 如果属于前面过程中配置为包含的组中用户的设备，后来被评估为不符合合规性策略或未在 Intune 中注册，将阻止此设备。

     - **阻止访问**和**隔离** – 一开始会立即阻止所有设备访问本地 Exchange。 属于前面过程中配置为包含的组中的用户的设备在 Intune 中注册后获取访问权限，并被评估为符合策略。

       未运行 Samsung Knox Standard 的 Android 设备不支持此设置，始终会被阻止  。

   - 对于“设备平台例外”  ，选择“添加”  ，然后根据环境需要指定详细信息。

      如果将“非托管设备访问”  设置为“已阻止”  ，则即使平台专门阻止，已注册且符合要求的设备仍可访问。  

9. 选择“确定”，保存你的编辑内容  。

10. 选择“查看并保存”，然后选择“保存”   以保存 Exchange 条件访问策略。

## <a name="next-steps"></a>后续步骤

接下来，创建合规性策略并将其分配给 Intune 的用户以评估其移动设备，请参阅[设备合规性入门](device-compliance-get-started.md)。

[Microsoft Intune 中 Intune 本地 Exchange 连接器疑难解答](https://support.microsoft.com/help/4471887)
