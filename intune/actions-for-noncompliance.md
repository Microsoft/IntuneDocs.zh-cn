---
title: "不符合要求的 Microsoft Intune 操作及相关消息 - Azure | Microsoft Docs"
description: "创建通知电子邮件，发送到不符合的设备。 在设备被标记为“不符合”后添加操作，例如添加宽限期以符合要求，或创建计划用于阻止访问在满足符合要求之前进行访问。 在 Azure 中使用 Microsoft Intune 完成此操作。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 37a8deca147bbad1e706b814f366a2c3f1247869
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2018
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>为不符合的设备自动发送电子邮件和添加操作 - Intune

“针对非符合性的操作功能”可配置一系列以时间排序的操作。 这些操作适用于不满足符合性策略的设备。 

## <a name="overview"></a>概述
默认情况下，当 Intune 检测到不符合的设备时，会立即将设备标记为不符合。 然后 Azure Active Directory (AD) [条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)阻止设备。 设备不符合时，还可使用“针对非符合性的操作”灵活决定要执行的操作。 例如，不立即阻止设备，并给予用户宽限期以符合要求。

有两种类型的操作：

- **通过电子邮件通知最终用户**：可先自定义电子邮件通知，再将其发送给最终用户。 可自定义收件人、主题和邮件正文，包括自定义公司徽标和联系人信息。

    此外，Intune 还在电子邮件通知中详细说明了不符合的设备情况。

- **将设备标记为不符合**：可在设备被标记为不符合之后创建计划（按天数计划）。 可配置立即采取的措施，也可给予用户宽限期以符合要求。

## <a name="before-you-begin"></a>在开始之前

- 至少需具备一个设备符合性策略，才能设置针对非符合性的操作。 要创建设备符合性策略，请参阅以下平台：

  - [Outlook Web Access (OWA)](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 使用设备符合性策略来阻止设备使用公司资源时，必须设置 Azure AD 条件性访问。 相关指南，请参阅 [Azure Active Directory 中的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

- 必须创建通知邮件模板。 如果要向用户发送电子邮件，可使用此模板创建针对非符合性的操作。

## <a name="create-a-notification-message-template"></a>创建通知邮件模板

1. 使用 Intune 凭据登录 [Azure 门户](https://portal.azure.com)。 
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备符合性”，然后选择“通知”。 
4. 选择“创建通知”，再输入以下信息：

  - 名称
  - 使用者
  - Message
  - 电子邮件标头 – 包括公司徽标
  - 电子邮件页脚 – 包括公司名称
  - 电子邮件页脚 – 包括联系人信息

  ![Intune 中符合性通知邮件的示例](./media/actionsfornoncompliance-1.PNG)

在完成信息添加后，选择“创建”。 通知邮件模板已就绪，可供使用。

> [!NOTE]
> 你还可以编辑先前创建的“通知”模板。

## <a name="add-actions-for-noncompliance"></a>添加针对非符合性的操作

默认情况下，Intune 自动创建针对非符合性的操作。 设备无法满足符合性策略的要求时，此操作将设备标记为不符合。 可自定义将设备标记为不符合的时长。 此操作不可撤消。

可在新建符合性策略或更新现有符合性策略时添加操作。 

1. 在 [Azure 门户](https://portal.azure.com)中，打开 Microsoft Intune，然后选择“设备符合性”。
2. 选择“策略”，选择一个策略，然后选择“属性”。 

  尚没有策略？ 创建 [Android](compliance-policy-create-android.md)、[iOS](compliance-policy-create-ios.md)、[Windows](compliance-policy-create-windows.md) 或其他平台策略。

3. 选择“针对非符合性的操作”，然后选择“添加”，输入操作参数。 可选择先前创建的消息模板，添加其他收件人，并更新宽限期计划。 可在计划中输入天数（0 到 365），然后可强制执行条件访问策略。 如果输入 0 天，则条件访问会立即阻止对公司资源的访问。

4. 完成后，选择“添加” > “确定”，保存所做更改。

## <a name="next-steps"></a>后续步骤
通过运行报表，监视设备符合性活动。 相关指南，请参见[如何使用 Intune 监视设备符合性](device-compliance-monitor.md)。
