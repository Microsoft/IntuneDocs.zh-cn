---
title: 在 Microsoft Intune 中创建 iOS 设备符合性策略 - Azure | Microsoft Docs
description: 创建或配置 Microsoft Intune 设备符合性策略以便 iOS 设备输入电子邮件帐户、检查已越狱设备、检查最低和最高操作系统版本及设置密码限制，包括密码长度和设备非活动状态。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1ee08c77fe085ad0f238d63481dd682ea15aa5ce
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313079"
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>在 Intune 中添加适用于 iOS 设备的设备符合性策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune iOS 设备符合性策略确定 iOS 设备为实现符合性而必须满足的规则和设置。 将设备符合性策略与条件访问一起使用时，可允许或阻止访问公司资源。 还可获取设备报表并针对非符合性采取措施。 可在 Intune Azure 门户中创建每个平台的设备符合性策略。 若要了解有关符合性策略以及所有系统必备组件的详细信息，请参阅[设备符合性入门](device-compliance-get-started.md)。

下表说明了将符合性策略与条件访问策略一起使用时如何管理非符合性设置。

---------------------------

| **策略设置** | **iOS 8.0 及更高版本** |
| --- | --- |
| **PIN 或密码配置** | 已修正 |
| **设备加密** | 已修正（通过设置 PIN） |
| **已越狱或取得 root 权限的设备** | 已隔离（非设置）
| **电子邮件配置文件** | 已隔离 |
|**最低操作系统版本** | 已隔离 |
| **最高操作系统版本** | 已隔离 |
| **Windows 运行状况证明** | “不适用” |

---------------------------

**已修正** = 设备操作系统强制合规性。 （例如，强制用户设置 PIN。）

**已隔离** = 设备操作系统不会强制合规性。 （例如，Android 设备不强制用户加密设备。）设备不符合时，系统将进行以下操作：

- 如果条件访问策略应用到用户，则将阻止该设备。
- 公司门户会通知用户任何合规性问题。

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. 对于“平台”，请选择“iOS”。 选择“设置配置”，并依次输入“电子邮件”、“设备运行状况”、“设备属性”和“系统安全”设置。 完成后，请选择“确定”，然后选择“创建”。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>Email

- 要求移动设备具有托管的电子邮件配置文件：如果将此项设置为“必需”，那些不具备由 Intune 托管的电子邮件配置文件的设备将被视为不符合要求。 如果设备未正确设定目标，或者如果用户在设备上手动设置电子邮件帐户，就可能没有托管的电子邮件配置文件。

  在以下情况中设备被视为不符合要求：
  - 电子邮件配置文件部署到合规性策略目标外的用户组。
  - 用户已在设备上设置了电子邮件帐户，且该帐户与部署到该设备的 Intune 电子邮件配置文件相匹配。 Intune 不能覆盖用户设置的配置文件，因此无法管理它。 若要确保合规性，用户必须删除现有电子邮件设置。 然后，Intune 可以安装托管的电子邮件配置文件。

- **选择必须由 Intune 管理的电子邮件配置文件**：如果选择了“必须由 Intune 管理电子邮件帐户”设置，请选择“选择”以指定 Intune 电子邮件配置文件。 电子邮件配置文件必须存在于设备上。

有关电子邮件配置文件的详细信息，请参阅[通过 Microsoft Intune 使用电子邮件配置文件配置对公司电子邮件的访问](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)。

## <a name="device-health"></a>Device health

- **已越狱设备**：如果启用此设置，已越狱设备则不符合策略。
- 要求设备不高于设备威胁级别（iOS 8.0 或更高版本）：选择将设备标记为不符合策略的最大威胁级别。 超过此威胁级别的设备将被标记为不符合策略：
  - 安全：此选项是最安全的，设备不能具有任何威胁。 如果设备被检测到具有任一等级的威胁，则会被评估为不符合要求。
  - **低**：若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
  - 中：如果设备上存在的威胁为低级或中级，设备也将被评估为符合策略。 若检测到设备存在高级威胁，则将其确定为不合规。
  - 高：此选项是最不安全的，允许所有威胁级别。 如果将此解决方案仅用作报告目的，则可能有用。

## <a name="device-properties"></a>设备属性

- **所需的最低操作系统版本**：设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 用户可以选择升级其设备。 然后可访问公司资源。
- **允许的最高操作系统版本**：设备使用的操作系统版本高于规则中指定的版本时，则会阻止访问公司资源。 然后会要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则该设备不能访问公司资源。

## <a name="system-security"></a>系统安全

### <a name="password"></a>密码

> [!NOTE]
> 符合性或配置策略应用到 iOS 设备后，系统会每 15 分钟提示用户一次，要求设置密码。 系统会持续提示用户，直到用户设置密码。

- 需要密码才可解锁移动设备：要求用户在访问其设备之前输入密码。 使用密码的 iOS 设备已加密。
- 简单密码：设置为“阻止”后，用户无法创建简单密码，如 1234 或 1111。 设置为“未配置”以允许用户创建密码，例如 1234 或 1111。
- **最短密码长度**：输入密码必须包含的最小位数或最小字符数。
- 所需的密码类型：选择密码是应仅包含数值字符，还是应混合使用数字和其他字符（字母数字）。
- **密码中的非字母数字字符数**：输入密码中必须包含的最小特殊字符（&、#、%、! 等）数。

    设置的数字越大，要求用户创建的密码越复杂。

- **要求提供密码之前的非活动最大分钟数**：输入用户必须重新输入其密码前的空闲时间。
- 密码过期(天)：选择密码过期之前的天数，然后必须创建一个新密码。
- 要防止重用的以前的密码数：输入以前用过的不能使用的密码数。

### <a name="restricted-applications"></a>受限的应用程序 
可以通过将应用的程序包 ID 添加到策略中来限制应用。 如果某一设备已安装该应用，此设备将被标记为非符合性设备。 
- **应用名称**：输入一个用户友好名称，帮助识别捆绑 ID。 
- **应用程序包 ID**：输入应用提供程序分配的唯一捆绑标识符。 若要查找捆绑 ID，请参阅 [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app)（如何查找 iOS 应用的捆绑 ID）。  

## <a name="assign-user-groups"></a>分配用户组

1. 选择已配置的策略。 现有策略位于“设备符合性” > “策略”中。
2. 选择策略，然后选择“分配”。 可以包括或排除 Azure Active Directory (AD) 安全组。
3. 选择“所选组”查看 Azure AD 安全组。 选择想要应用此策略的用户组，并选择“保存”向用户部署该策略。

你已将策略应用于用户。 将评估策略针对的用户所使用设备的符合性。

## <a name="next-steps"></a>后续步骤
[为不符合的设备自动发送电子邮件和添加操作](actions-for-noncompliance.md)  
[监视 Intune 设备符合性策略](compliance-policy-monitor.md)