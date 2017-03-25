---
title: "对不符合设备的操作"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何创建针对不符合设备的操作"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 16da087e741e335144266c838c0a91050bd7d520
ms.lasthandoff: 03/15/2017


---

# <a name="create-actions-for-non-compliance"></a>创建针对不符合设备的操作

**针对不符合设备的操作**允许配置应用于不符合设备的按时间顺序排列的操作顺序。 例如，你可以通过电子邮件通知用户设备不符合，或通过条件访问阻止这些设备访问公司资源。

## <a name="use-case-scenario"></a>用例场景

默认情况下，Intune 设备符合性策略将设备报告为不符合后，条件访问将立即阻止该设备，并且用户会收到一封包含符合要求说明的电子邮件。 “**针对不符合设备的操作**”可让你更灵活地决定在设备不符合时如何执行操作。 例如，你可以决定不立即阻止设备，然后给予用户宽限期以符合要求。

有两种类型的操作：

-   通过电子邮件通知用户

-   通过条件访问阻止访问公司资源

## <a name="notify-the-user-via-email"></a>通过电子邮件通知用户

可以选择预创建的默认电子邮件模板，也可以创建完全自定义的电子邮件通知。 我们提供主题、邮件正文的定制，包括公司徽标、联系人信息和其他收件人。

## <a name="block-corporate-resource-access-through-conditional-access"></a>通过条件访问阻止访问公司资源

你可以确定应阻止设备访问公司资源的天数。 可以立即阻止设备进行访问，但也可以给予用户宽限期，使设备符合设备符合性策略。

## <a name="before-you-begin"></a>在开始之前

你需要创建至少一个设备符合性策略，以设置针对不符合设备的操作。

-   了解如何为以下系统创建设备符合性策略：

    -   [Android](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)

    -   [Android for Work](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android-for-work)

    -   [iOS](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-ios)

    -   [Windows](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-windows)

计划使用设备符合性策略阻止设备使用公司资源时，需要设置 EMS 条件访问。

- 了解[如何设置 EMS 条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)。

此外，需要创建通知消息模板。 在稍后创建针对不符合设备的操作以向用户发送电子邮件时，将使用通知消息模板。

### <a name="to-add-a-notification-message-template"></a>添加通知消息模板

在“**设备符合性策略**”边栏选项卡中：

1.  在“**管理**”下，选择“**通知**”即会打开“通知”消息模板边栏选项卡。

    ![如何添加通知模板](../media/afnc-1.png)

2.  选择“**添加**”，然后需要定义以下内容：

    a.  说明

    b。  From

    c.  使用者

    d.  Message

    e.  电子邮件标头 – 包括公司徽标

    f.  电子邮件页脚 – 包括公司名称

    g.  电子邮件页脚 - 包括联系人信息

     ![通知消息模板](../media/afnc-2.png)

添加上述信息后，单击“**创建**”。 就可以使用“通知”消息模板了。

> [!NOTE] 
> 你还可以编辑先前创建的“通知”模板。

## <a name="to-create-actions-for-non-compliance"></a>创建针对不符合设备的操作

可以在创建新的设备符合性策略或编辑现有设备符合性策略时添加操作。

1.  在“**设备符合性策略**”边栏选项卡的“**管理**”下，选择“**策略**”。

2.  单击设备符合性策略即可进行选择。

    ![相容性策略](../media/afnc-3.png)

3.  打开“**设备符合性策略属性**”边栏选项卡后，选择“**针对不符合设备的操作**”。

4.  打开“针对不符合的操作”边栏选项卡后，选择“**添加**”指定操作参数。

    ![“针对不符合设备的操作”边栏选项卡](../media/afnc-4.png)

针对不符合设备的操作包括：

-   **强制执行条件访问策略**

-   **向最终用户发送电子邮件**

### <a name="enforce-conditional-access-policy"></a>强制执行条件访问策略

要对不符合设备添加此操作，请执行以下步骤：

1.  从“**对不符合设备的操作**”边栏选项卡中选择“**添加**”。

2.  在“**操作参数**”边栏选项卡中，从“操作”下拉列表中选择“**强制执行条件访问策略**”。

3.  在“**计划**”上，你可以指定强制执行条件访问策略的天数（0 到 255）。 如果指定 **0** 天，意味着一旦设备不符合设备符合性策略，条件访问必须**立即**阻止访问企业资源。

    ![对不符合设备的操作计划](../media/afnc-5.png)

4.  选择“**添加**”，然后从“**操作**”边栏选项卡中选择“**确定**”。

5.  从“**设备符合性策略属性**”边栏选项卡中选择“**保存**”。

### <a name="send-e-mail-to-end-user"></a>向最终用户发送电子邮件

可以使用电子邮件模板向不符合用户发送邮件。 这些电子邮件有助于推动整个组织的设备符合性。

要对不符合设备添加此操作，请执行以下步骤：

1.  从“**对不符合设备的操作**”边栏选项卡中选择“**添加**”。

2.  在“**操作参数**”边栏选项卡中，从“操作”下拉列表选择“**向最终用户发送电子邮件**”。

3.  单击“**邮件模板**”选择先前创建的邮件模板。 可以查看“邮件”模板内容，然后选取“**选择**”。

    ![邮件模板](../media/afnc-6.png)

> [!NOTE] 
> 你可以查看邮件模板，但无法对其进行编辑。 如果要编辑“邮件”模板，需要返回“**通知**”边栏选项卡。

1.  在“**计划**”上，输入应在不符合多少天后向用户发送电子邮件。 如果指定 **0** 天，意味着将立即**发送**电子邮件。

2.  选择“**添加**”，然后从“**操作**”边栏选项卡中选择“**确定**”。

3.  从“**设备符合性策略属性**”边栏选项卡中选择“**保存**”。

