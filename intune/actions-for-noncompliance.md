---
title: 不符合要求的 Microsoft Intune 操作及相关消息 - Azure | Microsoft Docs
description: 创建通知电子邮件，发送到不符合的设备。 在设备被标记为“不符合”后添加操作，例如添加宽限期以符合要求，或创建计划用于阻止访问在满足符合要求之前进行访问。 在 Azure 中使用 Microsoft Intune 完成此操作。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b799fd65a08646b46bf7fcce67bf4a09dc0413a6
ms.sourcegitcommit: cc5d757018d05fc03ac9ea3d30f563df9bfd61ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66819909"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>为 Intune 中不符合要求的设备自动发送电子邮件和添加操作

对于不满足符合性策略或规则的设备，可添加针对非符合性的操作。 此功能会配置一系列按时间顺序排列的操作，例如向最终用户发送电子邮件等。

## <a name="overview"></a>概述

默认情况下，当 Intune 检测到不符合的设备时，会立即将设备标记为不符合。 然后 Azure Active Directory (AD) [条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)阻止设备。 当设备不符合要求时，还可通过“针对非符合性的操作”灵活决定要执行的操作。 例如，不立即阻止设备，并给予用户宽限期以符合要求。

有多种类型的操作：

- **向最终用户发送电子邮件**：先自定义电子邮件通知，再将其发送给最终用户。 可自定义收件人、主题和邮件正文，包括自定义公司徽标和联系人信息。

    此外，Intune 还在电子邮件通知中详细说明了不符合的设备情况。

- **远程锁定不符合要求的设备**：对于不符合要求的设备，可发出远程锁定操作。 然后提示用户输入 PIN 或密码以解锁设备。 [远程锁定](device-remote-lock.md)功能的详细信息。 

- **将设备标记为不符合**：创建在设备被标记为不符合之后要执行的计划时间（天数）。 可配置立即采取的措施，也可给予用户宽限期以符合要求。

本文介绍如何：

- 创建消息通知模板
- 针对非符合性创建操作（例如发送电子邮件或远程锁定设备）


## <a name="before-you-begin"></a>在开始之前

- 至少需具备一个设备符合性策略，才能设置针对非符合性的操作。 要创建设备符合性策略，请参阅以下平台：

  - [Outlook Web Access (OWA)](compliance-policy-create-android.md)
  - [Android 工作配置文件](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 使用设备符合性策略来阻止设备使用公司资源时，必须设置 Azure AD 条件性访问。 请参阅 [Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)或[通过 Intune 使用条件性访问的常见方式](conditional-access-intune-common-ways-use.md)以获取指南。

## <a name="create-a-notification-message-template"></a>创建通知邮件模板

要向用户发送电子邮件，请创建通知消息模板。 设备不符合要求时，在模板中输入的详细信息将显示在发送给用户的电子邮件中。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备符合性” > “通知”。
3. 选择“创建通知”。 输入以下信息：

   - **名称**
   - **主题**
   - **Message**
   - **电子邮件标头 – 包括公司徽标**
   - **电子邮件页脚 – 包括公司名称**
   - **电子邮件页脚 – 包括联系人信息**

   ![Intune 中符合性通知邮件的示例](./media/actionsfornoncompliance-1.PNG)

4. 在完成信息添加后，选择“创建”。 通知邮件模板已就绪，可供使用。 作为公司门户品牌的一部分上传的徽标可用于电子邮件模板。 有关公司门户品牌的详细信息，请参阅[公司标识品牌自定义](company-portal-app.md#company-identity-branding-customization)。

> [!NOTE]
> 还可更改或更新先前创建的现有通知模板。

## <a name="add-actions-for-noncompliance"></a>添加针对非符合性的操作

创建设备符合性策略时，Intune 会自动为非符合性创建操作。 如果设备不满足符合性策略的要求，此操作会将设备标记为不符合。 可自定义将设备标记为不符合的时长。 此操作不可撤消。

还可以在创建符合性策略或更新现有策略时添加其他操作。 

1. 登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后选择“设备符合性”。
2. 选择“策略”，选择一个策略，然后选择“属性”。 

    尚没有策略？ 创建 [Android](compliance-policy-create-android.md)、[iOS](compliance-policy-create-ios.md)、[Windows](compliance-policy-create-windows.md) 或其他平台策略。
  
    > [!NOTE]
    > 此时，JAMF 设备和面向设备组的设备无法接收符合性操作。

3. 选择“针对非符合性的操作” > “添加”。
4. 选择“操作”： 

    - **向最终用户发送电子邮件**：当设备不符合要求时，选择给用户发送电子邮件。 此外： 
    
         - 选择此前创建的“消息模板”
         - 通过选择组输入任何“其他收件人”
    
    - **远程锁定不符合要求的设备**：当设备不符合要求时，锁定设备。 该操作会强制用户输入 PIN 或密码来解锁设备。 
    
5. 配置计划:输入非符合性状态触发用户设备操作之后的宽限天数（0 到 365 天）。 在此宽限期之后，可以强制执行条件访问策略。 如果输入“0”（零）天，则条件访问将立即生效。 例如，如果设备不符合要求，可以立即阻止其对公司资源的访问。

6. 完成后，选择“添加” > “确定”，保存所做更改。

## <a name="next-steps"></a>后续步骤

[监视策略](compliance-policy-monitor.md)。
