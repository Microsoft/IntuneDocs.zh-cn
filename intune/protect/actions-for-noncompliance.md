---
title: 不符合要求的 Microsoft Intune 操作及相关消息 - Azure | Microsoft Docs
description: 创建通知电子邮件，发送到不符合的设备。 在设备被标记为“不符合”后添加操作，例如添加宽限期以符合要求，或创建计划用于阻止访问在满足符合要求之前进行访问。 在 Azure 中使用 Microsoft Intune 完成此操作。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e3867bfc2de29c059766e134bd0d2c8801e1c70
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712910"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>为 Intune 中不符合要求的设备自动发送电子邮件和添加操作

对于不满足符合性策略或规则的设备，可添加针对非符合性的操作  。 此功能会配置一系列按时间顺序排列的操作，例如向最终用户发送电子邮件等。

## <a name="overview"></a>概述

默认情况下，当 Intune 检测到不符合的设备时，会立即将设备标记为不符合。 然后 Azure Active Directory (AD) [条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)阻止设备。 当设备不符合要求时，还可通过“针对非符合性的操作”灵活决定要执行的操作  。 例如，不立即阻止设备，并给予用户宽限期以符合要求。

有多种类型的操作：

- **向最终用户发送电子邮件**：先自定义电子邮件通知，再将其发送给最终用户。 可自定义收件人、主题和邮件正文，包括自定义公司徽标和联系人信息。

    此外，Intune 还在电子邮件通知中详细说明了不符合的设备情况。

- **远程锁定不符合要求的设备**：对于不符合要求的设备，可发出远程锁定操作。 然后提示用户输入 PIN 或密码以解锁设备。 [远程锁定](../remote-actions/device-remote-lock.md)功能的详细信息。

- **将设备标记为不符合**：创建在设备被标记为不符合之后要执行的计划时间（天数）。 可配置立即采取的措施，也可给予用户宽限期以符合要求。

本文介绍如何：

- 创建消息通知模板
- 针对非符合性创建操作（例如发送电子邮件或远程锁定设备）


## <a name="before-you-begin"></a>在开始之前

- 至少需具备一个设备符合性策略，才能设置针对非符合性的操作。 要创建设备符合性策略，请参阅以下平台：

  - [Android
](compliance-policy-create-android.md)
  - [Android 工作配置文件](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 使用设备符合性策略来阻止设备使用公司资源时，必须设置 Azure AD 条件访问。 请参阅 [Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)或[使用 Intune 条件访问的常见方式](conditional-access-intune-common-ways-use.md)以获取指南。

## <a name="create-a-notification-message-template"></a>创建通知邮件模板

要向用户发送电子邮件，请创建通知消息模板。 设备不符合要求时，在模板中输入的详细信息将显示在发送给用户的电子邮件中。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “符合性策略”   > “通知”   > “创建通知”  。
3. 在“基本”  下，指定以下信息：

   - **名称**
   - **主题**
   - **Message**

4. 此外，在“基本”  下，配置以下通知选项，这些选项都默认为“启用”  ：

   - **电子邮件标头 – 包括公司徽标**
   - **电子邮件页脚 – 包括公司名称**
   - **电子邮件页脚 – 包括联系人信息**

   作为公司门户品牌的一部分上传的徽标可用于电子邮件模板。 有关公司门户品牌的详细信息，请参阅[公司标识品牌自定义](../apps/company-portal-app.md#company-identity-branding-customization)。

   ![Intune 中符合性通知邮件的示例](./media/actions-for-noncompliance/actionsfornoncompliance-1.PNG)

   选择“下一步”继续操作  。

5. 在“查看 + 创建”  下，查看你的配置以确保通知消息模板已准备就绪可供使用。 选择“创建”  以成功创建通知。

> [!NOTE]
> 你还可以选择之前创建的现有通知模板，并选择“编辑”  来编辑其信息以更新模板。

## <a name="add-actions-for-noncompliance"></a>添加针对非符合性的操作

创建设备符合性策略时，Intune 会自动为非符合性创建操作。 如果设备不满足符合性策略的要求，此操作会将设备标记为不符合。 可自定义将设备标记为不符合的时长。 此操作不可撤消。

还可以在创建符合性策略或更新现有策略时添加其他操作。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “符合性策略”   > “策略”  ，选择其中一个策略，然后选择“属性”  。

   尚没有策略？ 创建 [Android](compliance-policy-create-android.md)、[iOS](compliance-policy-create-ios.md)、[Windows](compliance-policy-create-windows.md) 或其他平台策略。

   > [!NOTE]
   > 此时，JAMF 设备和面向设备组的设备无法接收符合性操作。

3. 选择“针对非符合性的操作” > “添加”   。

4. 选择“操作”： 

   - **向最终用户发送电子邮件**：当设备不符合要求时，选择给用户发送电子邮件。 此外：
     - 选择此前创建的“消息模板” 
     - 通过选择组输入任何“其他收件人” 

   - **远程锁定不符合要求的设备**：当设备不符合要求时，锁定设备。 该操作会强制用户输入 PIN 或密码来解锁设备。

5. 配置计划  :输入非符合性状态触发用户设备操作之后的宽限天数（0 到 365 天）。 在此宽限期后，可以强制执行[条件访问](conditional-access-intune-common-ways-use.md)策略。 如果输入“0”（零）天，则条件访问将立即生效   。 例如，如果设备不合规，请使用条件访问来立即阻止对电子邮件、SharePoint 和其他组织资源的访问。

   在你创建合规性策略时，“标记不合规设备”  操作会自动创建，并自动设置为“0”  天（即立即执行）。 通过此操作，当设备签入时，系统会立即将设备评估为不合规。 如果还使用条件访问，条件访问会立即生效。 若要给予宽限期，请更改“标记不合规设备”  操作中的“计划”  。

   在合规性策略中，假设还想要通知用户。 可以添加“向最终用户发送电子邮件”  操作。 在此“发送电子邮件”  操作中，将“计划”  设置为“2”天。 如果设备或最终用户在第 2 天仍被评估为不合规，系统就会在第 2 天发送电子邮件。 若要在被评估为不合规的第 5 天再次向用户发送电子邮件，请添加另一个操作，并将“计划”  设置为“5”天。

   若要详细了解合规性和内置操作，请参阅[合规性概述](device-compliance-get-started.md)。

6. 完成后，选择“添加” > “确定”，保存所做更改   。

## <a name="next-steps"></a>后续步骤

[监视策略](compliance-policy-monitor.md)。
