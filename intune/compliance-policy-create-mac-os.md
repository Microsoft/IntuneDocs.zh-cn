---
title: "在 Microsoft Intune 中创建 macOS 设备符合性策略"
titleSuffix: 
description: "为 macOS 设备创建 Microsoft Intune 设备符合性策略，以便可指定设备必须满足的符合性要求。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e7703b8ea26d6ce53b82e806a78c788d14ae05b4
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="create-a-device-compliance-policy-for-macos-devices-with-intune"></a>使用 Intune 创建适用于 macOS 设备的设备符合性策略


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

适用于 macOS 的 Intune 设备符合性策略指定 macOS 设备为实现符合性而必须满足的规则和设置。 可将这些策略与条件访问相结合，进而允许/阻止访问公司资源，还可获取设备报告并采取措施应对不符合的情形。 可在 Intune Azure 门户中创建每个平台的设备符合性策略。

## <a name="before-you-begin"></a>在开始之前

在创建和分配设备符合性策略之前，请查看 Intune 设备符合性策略概念。

- 若要了解有关设备符合性策略的详细信息，请参阅[设备符合性策略入门](device-compliance.md)。

> [!IMPORTANT]
> 需要为每个平台创建设备符合性策略。 Intune 设备符合性策略设置取决于平台功能，这些功能是通过 MDM 协议公开的设置。

下表说明了将符合性策略与条件访问策略一起使用时如何管理非符合性设置：


| 策略设置 | macOS 10.11 和更高版本 |
| --- | --- |
| **PIN 或密码配置** | 已修正 |   
| **设备加密** | 已修正（通过设置 PIN） |
| **电子邮件配置文件** | 已隔离 |
|**最低操作系统版本** | 已隔离 |
| **最高操作系统版本** | 已隔离 |  


**已修正** = 设备操作系统强制合规性。 （例如，强制用户设置 PIN。）

**已隔离** = 设备操作系统不会强制合规性。 （例如，Android 设备不强制用户加密设备。）设备不符合时，系统将进行以下操作：

- 如果条件访问策略应用到用户，则将阻止该设备。
- 公司门户会通知用户任何合规性问题。

## <a name="macos-compliance-policy-settings"></a>MacOS 符合性策略设置

创建新的 Intune 设备符合性时，可以选择具有不同设置的类别：

- 设备运行状况

- 设备属性

- 系统安全

### <a name="device-health"></a>设备运行状况

- **需要系统完整性保护**：设置为“必需”，以检查 macOS 设备是否启用了系统完整性保护。

### <a name="device-properties"></a>设备属性

- **最低操作系统版本**：设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 用户可以选择升级其设备。 然后可访问公司资源。

- **最高操作系统版本**：设备使用的操作系统版本高于规则中指定的版本时，将阻止访问公司资源，并要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则该设备将不能用于访问公司资源。

### <a name="system-security-settings"></a>系统安全设置

#### <a name="password"></a>密码

- **需要密码才可解锁移动设备**：设置为“必需”，因此用户需要在访问其设备之前输入密码。

- **简单密码**：设置为“阻止”，因此用户无法创建简单密码，如 1234 或 1111。

- **最短密码长度**：指定密码必须包含的最小位数或最小字符数。

- **密码类型**：指定用户必须创建字母数字密码还是数字密码。

- **密码中非字母数字字符数**：如果将“所需的密码类型”设置为“字母数字”，请使用此设置指定密码必须具有的最小字符集数。 

    > [!NOTE]
    > 设置的数字越大，要求用户创建的密码越复杂。

    > [!IMPORTANT]
    > 对于 macOS 设备，此设置是指必须包括在密码中的特殊字符数（例如 ! 、**#**、**&amp;**）。

- **要求提供密码之前的非活动最大分钟数**：指定用户必须重新输入其密码前的空闲时间。

- **密码过期(天)**：选择密码过期之前的天数（介于 1 至 250 之间），然后必须创建一个新密码。

- **要防止重用的以前的密码数**：指定以前用过的不能重复使用的密码数。

    > [!IMPORTANT]
    > 当 macOS 设备上的密码要求发生更改时，直到用户下次更改密码时此更改才会生效。 例如，如果将密码长度限制设置为 8 位数，而 macOS 设备当前使用的是 6 位数密码，则在用户下次更新设备上的密码前，该设备将仍保持符合状态。

## <a name="to-create-a-device-compliance-policy"></a>创建设备符合性策略

1. 转到 [Azure 门户](https://portal.azure.com)，然后使用 Intune 凭据登录。

2. 成功登录后，可以看到“Azure 仪表板”。

3. 从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune。

4. 选择“Intune”，可以看到“Intune 仪表板”。

5. 选择“设备符合性”，然后在“管理”下选择“策略”。

6. 选择“创建策略”。

7. 键入名称、说明，并选择要应用此策略的平台。

8. “macOS 符合性策略”窗格将打开，选择设备符合性设置类别“系统安全性”、“设备运行状况”和“设备属性”以指定设置。

10. 选择设置后，在每个设备符合性设置类别下选择“确定”。

11. 选择“确定”，然后选择“创建”。

## <a name="assign-user-groups"></a>分配用户组

若要为用户分配合规性策略，请选择已配置的策略。 可在“设备符合性 – 策略”窗格中找到现有策略。

1. 选择要分配给用户的设备符合性策略，然后选择“分配”。 随即打开一个窗格，可在此处选择“Azure Active Directory 安全组”并对其分配策略。

2. 选择“所选组”以打开显示 Azure AD 安全组的窗格。

3. 选择“保存”，以将设备符合性策略分配给 Azure AD 安全组。

4. 将设备符合性策略分配给组后，可以关闭“分配”窗格。

    > [!TIP]
    > 默认情况下，设备每 8 小时检查一次符合性，但用户可以通过 Intune 公司门户应用强制执行此过程。

## <a name="next-steps"></a>后续步骤

[如何监视设备符合性策略](compliance-policy-monitor.md)
