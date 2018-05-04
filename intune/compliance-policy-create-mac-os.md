---
title: 在 Microsoft Intune 中创建 macOS 设备符合性策略 - Azure | Microsoft Docs
description: 为 macOS 设备创建或配置 Microsoft Intune 设备符合性策略以使用系统完整性保护，设置最低和最高操作系统版本，选择密码要求，以及加密数据存储。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a797c68ca43a6173a4bac70e914d3f763ce5e6d0
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
---
# <a name="add-a-device-compliance-policy-for-macos-devices-with-intune"></a>使用 Intune 添加适用于 macOS 设备的设备符合性策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune macOS 设备符合性策略确定 macOS 设备为实现符合性而必须满足的规则和设置。 将设备符合性策略与条件访问一起使用时，可允许或阻止访问公司资源。 还可获取设备报表并针对非符合性采取措施。 可在 Intune Azure 门户中创建每个平台的设备符合性策略。 若要了解有关符合性策略以及所有系统必备组件的详细信息，请参阅[设备符合性入门](device-compliance-get-started.md)。

下表说明了将符合性策略与条件访问策略一起使用时如何管理非符合性设置：

---------------------------

| 策略设置 | macOS 10.11 和更高版本 |
| --- | --- |
| **PIN 或密码配置** | 已修正 |   
| **设备加密** | 已修正（通过设置 PIN） |
| **电子邮件配置文件** | 已隔离 |
|**最低操作系统版本** | 已隔离 |
| **最高操作系统版本** | 已隔离 |

---------------------------

**已修正** = 设备操作系统强制合规性。 例如，强制用户设置 PIN。

**已隔离** = 设备操作系统不会强制合规性。 （例如，Android 设备不强制用户加密设备。）设备不符合时，系统将进行以下操作：

- 如果条件访问策略应用到用户，则将阻止该设备。
- 公司门户会通知用户任何合规性问题。

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. 对于“平台”，选择“macOS”。 选择“设置配置”，然后依次输入“设备运行状况”、“设备属性”和“系统安全”设置。 完成后，请选择“确定”，然后选择“创建”。

## <a name="device-health"></a>设备运行状况

- 需要系统完整性保护：要求 macOS 设备启用[系统完整性保护](https://support.apple.com/HT204899)。

## <a name="device-properties"></a>设备属性

- 最低操作系统版本：设备不满足最低 OS 版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级其设备，然后访问公司资源。
- 最高操作系统版本：设备使用的操作系统版本高于规则中指定的版本时，会阻止访问公司资源。 会要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则设备不能访问公司资源。

## <a name="system-security-settings"></a>系统安全设置

### <a name="password"></a>密码

- 需要密码才可解锁移动设备：要求用户在访问其设备之前输入密码。
- 简单密码：设置为“阻止”后，用户无法创建简单密码，如 1234 或 1111。 设置为“未配置”以允许用户创建密码，例如 1234 或 1111。
- **最短密码长度**：输入密码必须包含的最小位数或最小字符数。
- 密码类型：选择密码是应仅包含数值字符，还是应混合使用数字和其他字符（字母数字）。
- 密码中的非字母数字字符数：输入密码中必须包含的最小特殊字符（&、#、%、! 等）数。

    设置的数字越大，要求用户创建的密码越复杂。

- **要求提供密码之前的非活动最大分钟数**：输入用户必须重新输入其密码前的空闲时间。
- 密码过期(天)：选择密码过期之前的天数，然后必须创建一个新密码。
- 要防止重用的以前的密码数：输入以前用过的不能使用的密码数。

    > [!IMPORTANT]
    > 当 macOS 设备上的密码要求发生更改时，直到用户下次更改密码时此更改才会生效。 例如，如果将密码长度限制设置为 8 位数，而 macOS 设备当前使用的是 6 位数密码，则在用户下次更新设备上的密码前，该设备将仍保持符合状态。

### <a name="encryption"></a>加密

- 设备上的数据存储加密：选择“需要”加密设备上的数据存储。

## <a name="assign-user-groups"></a>分配用户组

1. 选择已配置的策略。 现有策略位于“设备符合性” > “策略”中。
2. 选择策略，然后选择“分配”。 可以包括或排除 Azure Active Directory (AD) 安全组。
3. 选择“所选组”查看 Azure AD 安全组。 选择想要应用此策略的用户组，并选择“保存”向用户部署该策略。

> [!TIP]
> 默认情况下，设备每隔 8 小时检查一次符合性。 但是，用户可以通过 Intune 公司门户应用强制执行此过程。

你已将策略应用于用户。 将评估策略针对的用户所使用设备的符合性。

## <a name="next-steps"></a>后续步骤
[为不符合的设备自动发送电子邮件和添加操作](actions-for-noncompliance.md)  
[监视 Intune 设备符合性策略](compliance-policy-monitor.md)