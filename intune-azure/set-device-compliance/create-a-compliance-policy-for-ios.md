---
title: "如何创建 iOS 符合性策略"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何创建适用于 iOS 设备的合规性策略。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: c2ace3061e175a6eefd864bdda176651cc09a5b1
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune-azure-preview"></a>如何在 Intune Azure 预览版中创建适用于 iOS 设备的设备合规性策略


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

为每个平台创建合规性策略。  可以在 Azure 门户中创建合规性策略。 若要详细了解什么是合规性策略，请参阅[什么是设备合规性](what-is-device-compliance.md)主题。 若要了解创建合规性策略之前需要解决的先决条件，请参阅[设备合规性入门](get-started-with-device-compliance.md)主题。

下表说明了将合规性策略与条件访问策略一起使用时如何管理非合规性设置。

-------------------------------


| **策略设置** | **iOS 8.0 及更高版本** |
| --- | --- |
| **PIN 或密码配置** | 已修正 |   
| **设备加密** | 已修正（通过设置 PIN） |
| **已越狱或取得 root 权限的设备** | 已隔离（非设置）
| **电子邮件配置文件** | 已隔离 |
|**最低操作系统版本** | 已隔离 |
| **最高操作系统版本** | 已隔离 |  
| **Windows 运行状况证明** | 不适用 |  
----------------------------


**已修正** = 设备操作系统强制合规性。 （例如，强制用户设置 PIN。）

**已隔离** = 设备操作系统不会强制合规性。 （例如，Android 设备不强制用户加密设备。）当设备不合规时，进行以下操作：

- 如果条件访问策略应用到用户，则将阻止该设备。
- 公司门户会通知用户任何合规性问题。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>在 Azure 门户中创建合规性策略

1. 在“Intune”边栏选项卡中，选择“设置设备合规性”。 在“管理”下，选择“所有设备合规性策略”，然后选择“创建”。
2. 键入名称、说明，并选择要应用此策略的平台。
3. 选择“合规性要求”以在该处指定“安全性”、“设备运行状况”和“设备属性”设置，完成后，选择“确定”。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>分配用户组

若要为用户分配合规性策略，请选择已配置的策略。 可在“合规性 - 策略”边栏选项卡中找到现有策略。

1. 选择要分配给用户的策略，然后选择“分配”。 此操作将打开边栏选项卡，可以在其中选择“Azure Active Directory 安全组”并将其分配给策略。
2. 选择“选择组”以打开显示 Azure AD 安全组的边栏选项卡。  选择“选择”会将策略部署到用户。

你已将策略应用于用户。  将评估策略针对的用户所使用设备的合规性。

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>系统安全设置

### <a name="password"></a>Password

- **需要密码才可解锁移动设备**：将此选项设置为“是”，要求用户在访问其设备之前输入密码。 使用密码的 iOS 设备已加密。
- **允许简单密码**：将此选项设置为“是”，允许用户创建简单密码，如 **1234** 或 **1111**。
- **最短密码长度**：指定密码必须包含的最小位数或最小字符数。
- **所需的密码类型**：指定用户必须创建**字母数字**密码还是**数字**密码。
- **最小字符集数**：如果将“所需的密码类型”设置为“字母数字”，请使用此设置指定密码必须具有的最小字符集数。 四个字符集为：
  - 小写字母
  - 大写字母
  - 符号
  - 数字

设置的数字越大，要求用户创建的密码越复杂。

对于 iOS 设备，此设置是指必须包括在密码中的特殊字符数（例如 **!** 、**#**、**&amp;**）。

- **要求提供密码之前的非活动分钟数**：指定用户必须重新输入其密码前的空闲时间。
- **密码过期(天)**：选择密码过期之前的天数，然后必须创建一个新密码。
- **记住密码历史记录**：将此设置与“防止重用旧密码”结合使用，以限制用户使用以前创建的密码。
- **防止重用以前的密码**：如果选择了“记住密码历史记录”，请指定不能重用的以前用过的密码数。
- **设备从空闲状态返回时需要密码**：将此设置与“要求提供密码之前的非活动分钟数”设置一起使用。 设备在“要求提供密码之前的非活动分钟数”设置指定的时间内处于非活动状态时，将提示用户输入密码才能访问设备。

### <a name="email-profile"></a>电子邮件配置文件

- **必须由 Intune 管理电子邮件帐户**：如果该选项设置为“是”，则设备必须使用部署到设备的电子邮件配置文件。 在以下情况中设备被视为不符合要求：
  - 电子邮件配置文件部署到合规性策略目标外的用户组。
  - 用户已在设备上设置了电子邮件帐户，且该帐户与部署到该设备的 Intune 电子邮件配置文件相匹配。 Intune 不能覆盖用户设置的配置文件，因此无法管理它。 若要确保合规性，用户必须删除现有电子邮件设置。 然后，Intune 可以安装托管的电子邮件配置文件。
- **选择必须由 Intune 管理的电子邮件配置文件**：如果选择了“必须由 Intune 管理电子邮件帐户”设置，请选择“选择”以指定 Intune 电子邮件配置文件。 电子邮件配置文件必须存在于设备上。

有关电子邮件配置文件的详细信息，请参阅[通过 Microsoft Intune 使用电子邮件配置文件配置对公司电子邮件的访问](https://docs.microsoft.com/en-us/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)。

## <a name="device-health-settings"></a>设备运行状况设置

- **设备不得越狱或取得 root 权限**：如果启用此设置，已越狱的设备将不符合要求。

## <a name="device-properties"></a>设备属性

- **所需的最低操作系统版本**：设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 用户可以选择升级其设备。 然后可访问公司资源。
- **允许的最高操作系统版本**：设备使用的操作系统版本高于规则中指定的版本时，将阻止访问公司资源，并要求用户联系其 IT 管理员。 除非变更规则以允许该操作系统版本，否则该设备将不能用于访问公司资源。

<!--- ## Next steps

[How to monitor device compliance](monitor-device-compliance.md)--->

