---
title: "Microsoft Intune 中的已知问题"
titlesuffix: Microsoft Intune
description: "阅读 Microsoft Intune 中的已知问题。"
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02efc7e2369c590e2d21ac8c27db54ffbaae38c1
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="known-issues-in-microsoft-intune"></a>Microsoft Intune 中的已知问题


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


使用本主题了解 Microsoft Intune 中的任何已知问题。

如果要报告此处未列出的 bug，请[打开支持请求](get-support.md)。

如果要为 Intune 请求新功能，可以考虑在我们的 [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) 网站上提交报告。

## <a name="migration"></a>迁移

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Intune 旧 PC 客户端功能仅适用于 Silverlight 控制台

通过 Windows MDM 注册可在 Azure 门户上的 Intune 中管理 Windows 10。 有关详细信息，请参阅 [Azure 控制台上的 Intune 和旧 Intune PC 客户端](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure)。

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>在迁移过程中 Intune 所创建的组可能会影响其他 Microsoft 产品的功能

从 Intune 迁移到 Azure 门户时，可能会看到名为“All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421”的新组。 此组包含 Azure Active Directory 中的所有用户，而不仅仅是 Intune 许可的用户。 如果你希望某些现有用户或新用户不属于任何组的成员，此用法会导致其他 Microsoft 产品出现问题。

### <a name="status-blades-for-migrated-policies-do-not-work"></a>迁移策略的状态边栏选项卡不起作用

你无法查看从 Azure 门户中的经典门户中迁移的策略的状态信息。 但可以继续在经典门户中查看这些策略的报表。 若要查看已迁移配置策略的状态信息，请在 Azure 门户中重新创建这些策略。

## <a name="apps"></a>应用

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>仅适用于默认 Intune 租户语言的 iOS 批量采购应用
会显示 iOS 批量采购应用，且仅可为与你的 Intune 帐户相同的国家/地区代码分配这些应用。 Intune 仅同步 iTunes 区域设置与 Intune 租户账户国家/区域代码相同的的应用。 例如，如果要购买仅可通过美国商店获得的应用，但 Intune 帐户所在地区为德国，则 Intune 不会显示该应用。

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>会上传同一 iOS 批量采购计划的多个副本
不要为相同的 VPP 令牌多次单击“上传”按钮。 这将导致上传重复的 VPP 令牌，并导致应用针对同一 VPP 令牌发生多次同步。


<!-- ## Groups -->

## <a name="device-configuration"></a>设备配置

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>无法为某些设备保存 Windows 信息保护策略

对于未向 Intune 注册的设备，你只能在 Windows 信息保护策略设置中的“企业标识”字段中指定主域。
如果你添加了其他域（使用“高级设置” > “网络外围” > “添加受保护的域”），则你无法保存策略。 你看到的错误消息将会更改为更准确的消息。

### <a name="cisco-anyconnect-vpn-client-support"></a>Cisco AnyConnect VPN 客户端支持

最新版本的 Cisco AnyConnect VPN 客户端 (4.0.07072) 目前与 Intune 不兼容。
将来的 Intune 更新将提供与此 VPN 客户端版本的兼容性。 在此之前，建议不更新 Cisco AnyConnect VPN 客户端，并继续使用现有版本。

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>对 macOS Sierra 设备使用数字密码类型

目前，如果你在 macOS Sierra 设备的设备限制配置文件中选择“数值”作为“所需的密码类型”，则将强制使用“字母数字”。 如果你想对这些设备使用数字密码，则不要配置此设置。
macOS 的未来版本中可能会解决此问题。

有关这些设置的详细信息，请参阅 [Microsoft Intune 中的 macOS 设备限制设置](device-restrictions-macos.md)。

## <a name="compliance"></a>合规性

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Intune 的符合性策略不会在新控制台中显示

在经典门户中创建的任何符合性策略都将被迁移，但不会显示在 Azure 门户中，因为 Azure 门户中进行了设计更改。 在 Intune 经典门户中创建的符合性策略仍会强制执行，但必须在经典门户中才能查看和编辑这些策略。

此外，在 Azure 门户中新建的符合性策略也不会在经典门户中显示。

有关详细信息，请参阅[什么是设备符合性](device-compliance.md)。

<!-- ## Enrollment -->


## <a name="data-protection"></a>数据保护

### <a name="ios-app-protection-policies"></a>iOS 应用保护策略

可以定义 [iOS 应用保护策略](app-protection-policy-settings-ios.md)使这些策略适用于无需注册即可通过移动应用管理 (MAM) 进行管理的设备上的用户。 由于临时错误，只能为具有单个小数点版本而不是多个小数点的 iOS 版本定义这些策略。 将最低版本设置为 iOS 10.3，而不是设置为 iOS 10.3.1。 使用 iOS SDK 的即将推出的更新将解决此问题。


## <a name="administration-and-accounts"></a>管理和帐户

全局管理员（也被称为租户管理员）可以继续在没有单独的 Intune 或企业移动性套件 (EMS) 许可证的情况下进行日常的管理任务。 但是，要使用服务（例如注册他们自己的设备、企业设备，或使用 Intune 公司门户），他们需要 Intune 或 EMS 许可证。

<!-- ## Additional items -->
