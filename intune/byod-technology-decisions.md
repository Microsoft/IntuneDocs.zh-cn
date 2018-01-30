---
title: "通过 EMS 启用 BYOD 的技术决策"
description: "用于通过 Microsoft 企业移动性 + 安全性启用 BYOD 和保护公司数据的关键技术决策。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/8/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.openlocfilehash: 85fa202c3e80cdc830155299c16f121f96cc5742
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>用于通过 Microsoft 企业移动性 + 安全性 (EMS) 启用 BYOD 的技术决策

为使员工能够在自己的设备上远程办公 (BYOD) 而制定策略时，需要针对以下方案做出关键决策：启用 BYOD 以及如何保护公司数据。 幸运的是，EMS 提供了一套全面解决方案所需的全部功能。  

在本主题中，我们会查看启用 BYOD 使员工有权访问企业电子邮件的简单用例。 我们会重点关注需要管理整个设备还是只需要管理应用程序，这两者都是完全有效的选择。

## <a name="assumptions"></a>假设
* 具备 Azure Active Directory 和 Microsoft Intune 的基础知识
* 电子邮件帐户托管在 Exchange Online 中

## <a name="common-reasons-to-manage-the-device-mdm"></a>管理设备 (MDM) 的常见原因
通过在 Exchange Online 上部署[条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)策略，可轻松地让用户在设备管理中注册其设备。 下面是可能需要管理个人设备的原因：

**WiFi/VPN** - 如果用户需要企业连接配置文件高效工作，可无缝配置此配置文件。

**应用程序** - 如果用户需要将一组应用推送到设备中，可无缝地传递这些应用。 这包括出于安全目的考虑而需要的应用程序，例如移动威胁防御应用。

**符合性** - 某些组织需要符合法规或调用特定 MDM 控制的其他策略的要求。 例如，需要 MDM 加密整个设备，或者生成设备上所有应用的报告。

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>只管理应用 (MAM) 的常见原因
对支持 BYOD 的组织而言，不进行 MDM 而进行 MAM 是非常普遍的。 通过在 Exchange Online 上部署条件访问策略，可让用户从支持 MAM 保护的 Outlook Mobile 中访问电子邮件。 下面是可能只需要管理个人设备上的应用的原因：

**用户体验** - MDM 注册包括许多由平台强制执行的警告提示，这些提示通常会导致用户最终决定不在其个人设备上访问电子邮件。 MAM 大大减少了用户的担忧，因为他们一次只会收到一个弹出窗口，以知晓 MAM 保护已到位。

**符合性** - 某些组织需要符合一些策略的要求，这些策略对个人设备需要较少的管理功能。 例如，MAM 只能删除应用中的公司数据，与此相反，MDM 能够删除设备中的所有数据。

![对移动设备上的设备和应用管理的比较图](./media/byod-app-device-mgmt.png)

详细了解[设备管理和应用管理的生命周期](introduction-device-app-lifecycles.md)。

## <a name="mdm-vs-mam-capability-comparison"></a>MDM 与 MAM 的功能比较
如前所述，条件访问可让用户注册其设备或使用 Outlook Mobile 等托管应用。 在任一情况下都可应用许多其他条件，包括：

* 尝试访问的用户
* 位置是否可信任
*   登录风险级别
* 设备平台

尽管如此，许多组织通常有自身关注的特定风险。  下表列出了常见风险，以及 MDM 与 MAM 应对该风险的方法。

| 风险   |   MDM  |   MAM  |
|------------|--------|--------|
|数据访问未经授权 | 需要组成员身份 | 需要组成员身份 |
|数据访问未经授权 | 需要注册设备 | 需要受保护的应用 |
|数据访问未经授权 | 需要采用特定位置 | 需要采用特定位置 |
| | | |
|用户帐户遭到泄露| 需要进行 MFA | 需要进行 MFA|
|用户帐户遭到泄露 | 阻止高风险用户 | 阻止高风险用户 |
|用户帐户遭到泄露 | 设备 PIN | 应用 PIN |
| | | |
| 设备或应用遭到泄露 | 需要兼容设备 | 在应用启动时进行越狱检查 |
| 设备或应用遭到泄露 | 加密设备数据 | 加密应用数据 |
| | | |
|设备丢失或被盗 | 删除所有设备数据 | 删除所有应用数据|
| | | |
| 意外共享数据，或将数据保存到不安全的位置 | 限制设备数据备份 | 限制剪切/复制/粘贴|
| 意外共享数据，或将数据保存到不安全的位置 | 限制另存为 | 限制另存为 |
|意外共享数据，或将数据保存到不安全的位置 | 禁用打印 | N/A|

## <a name="next-steps"></a>后续步骤
现在是时候决定是否要在组织中启用 BYOD 了，可以选择是重点关注设备管理、应用管理还是上述两者的组合。 实现选择由你掌控，可以确信的是 Azure AD 提供的标识和安全功能在任何时候都可用。

使用 Intune [规划指南](planning-guide.md)来制定下一级别的规划。
