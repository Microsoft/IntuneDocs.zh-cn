---
title: Microsoft Intune App SDK for Android 测试指南
description: 用于 Android 的 Microsoft Intune App SDK 测试指南可帮助测试 Intune 托管的 Android 应用。
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9eada01f2b1e876d6d3b47140c671e3ff7eeab02
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503508"
---
# <a name="microsoft-intune-app-sdk-for-android-testing-guide"></a>Microsoft Intune App SDK for Android 测试指南

本指南可帮助开发人员测试其 Intune 托管的 Android 应用。  

## <a name="prerequisite-test-accounts"></a>必备项测试帐户
可以创建具有或不含预生成数据的新帐户。 创建新帐户：
1. 转到 [Microsoft 演示](https://demos.microsoft.com/environments/create/tenant)站点。 
2. [设置 Intune](../fundamentals/setup-steps.md) 以启用移动设备管理 (MDM)。
3. [创建用户](../fundamentals/users-add.md)。
4. [创建组](../fundamentals/groups-add.md)。
5. 根据测试[分配许可证](../fundamentals/licenses-assign.md)。


## <a name="azure-portal-policy-configuration"></a>Azure 门户策略配置
在 [Azure 门户的 Intune 边栏选项卡](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)中，[创建和分配应用保护策略](../apps/app-protection-policies.md)。 你还可以在 "Intune" 边栏选项卡中创建和分配[应用配置策略](../apps/app-configuration-policies-overview.md)。

> [!NOTE]
> 如果在 Azure 门户中未列出应用，则可以使用策略解决该问题，方法是选择“更多应用”选项并在文本框中提供包名称  。

## <a name="test-cases"></a>测试用例

以下测试用例提供了配置和确认步骤。 此指南用于帮助解决 Intune 托管的 Android 应用问题。

### <a name="required-pin-and-corporate-credentials"></a>必须使用 PIN 和公司凭据

必须使用 PIN 才能访问公司资源。 此外，在用户使用托管的应用之前，还可以强制对公司执行身份验证。 操作方法如下：

1. 请将“需要 PIN 才能进行访问”和“需要公司凭据才能进行访问”设置为“是”    。 有关详细信息，请参阅 [Microsoft Intune 中的 Android 应用保护策略设置](../apps/app-protection-policy-settings-android.md#access-requirements)。
2. 确认以下情况：
    - 应用启动时应显示提示提供 PIN 输入或在注册公司门户期间使用的生产用户。
    - 出现无效的登录提示时，可能是因为 Android 清单配置不正确，特别是 Azure Active Directory Authentication Library （ADAL）集成的值（SkipBroker、ClientID 和授权）。
    - 系统未显示任何提示可能是由于错误地集成了 `MAMActivity` 值。 有关 `MAMActivity` 的详细信息，请参阅[用于 Android 的 Microsoft Intune App SDK 开发人员指南](app-sdk-android.md)。

> [!NOTE] 
> 如果前面的测试不起作用，则以下测试可能也会失败。 请查看 [SDK](app-sdk-android.md##sdk-integration) 和 [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) 集成。

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>限制与其他应用传输和接收数据
可以控制公司托管应用程序之间的数据传输，如下所示：

1. 请将“允许应用将数据传输到其他应用”设置为“策略托管应用”   。
2. 将“允许应用从其他应用接收数据”设置为“所有应用”   。 这些策略将影响意向和内容提供商的使用。
3. 确认以下情况：
    - 从非托管应用打开应用运行正常。
    - 允许在托管应用之间共享内容。
    - 阻止从托管应用到非托管应用（如 Chrome）的共享。

### <a name="restrict-cut-copy-and-paste"></a>限制剪切、复制和粘贴
可以将系统剪贴板限制为托管应用程序，如下所示：

1. 请将“限制与其他应用进行剪切、复制和粘贴”设置为“通过粘贴托管策略”   。
2. 确认以下情况：
    - 阻止将应用中的文本复制到非托管应用（如 Message）。

### <a name="prevent-save"></a>阻止“保存”
可以控制“另存为”功能，如下所示  ：

1. 如果应用需要[集成“另存为”控件](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)，请将“阻止“另存为””设置为“是”   。
2. 确认以下情况：
    - 保存仅限于适当的托管位置。

### <a name="file-encryption"></a>文件加密
可以加密设备上的数据，如下所示：

1. 请将“加密应用数据”设置为“是”   。
2. 确认以下情况：
    - 正常应用程序行为不受影响。

### <a name="prevent-android-backups"></a>阻止 Android 备份
可以控制应用备份，如下所示：

1. 如果设置了[集成备份限制](app-sdk-android.md#protecting-backup-data)，请将“阻止 Android 备份”设置为“是”   。
2. 确认以下情况：
    - 备份会受到限制。

### <a name="unenrollment"></a>取消注册
不再对包含解密公司电子邮件和文档以及个人数据的托管应用进行管理时，可以远程将其擦除。 操作方法如下：

1. 从 Azure 门户中，[发出擦除](../apps/apps-selective-wipe.md)。
2. 如果应用未注册任何擦除处理程序，请确认以下情况：
    - 完全擦除应用。
3. 如果应用已注册 `WIPE_USER_DATA` 或 `WIPE_USER_AUXILARY_DATA`，请确认以下情况：
    - 托管的内容将从应用中删除。 有关详细信息，请参阅[用于 Android 的 Intune App SDK 开发人员指南 - 选择性擦除](app-sdk-android.md#selective-wipe)。

### <a name="multi-identity-support"></a>多身份支持
集成[多标识支持](app-sdk-android.md#multi-identity-optional)是一项高风险的更改，需要进行全面测试。 最常见的问题是由于错误地设置标识（上下文与威胁级别）和跟踪文件（`MAMFileProtectionManager`）而导致的。

至少请确认：

- **另存为**策略对托管标识运行正常。
- 从托管到个人恰当地强制执行复制粘贴限制。
- 仅加密属于托管标识的数据，并且不修改个人文件。
- 取消注册期间，选择性擦除仅删除托管标识数据。
- 从非托管帐户更改为托管帐户时，系统会提示用户进行条件性启动（仅限第一次）。

### <a name="app-configuration-optional"></a>应用配置（可选）
可以配置托管应用的行为。 如果应用使用任何应用配置设置，应测试应用是否正确处理你（如管理员）可设置的所有值。 可以在 Intune 中创建和分配[应用配置策略](../apps/app-configuration-policies-overview.md)。

## <a name="next-steps"></a>后续步骤

- [将 Android 业务线应用添加到 Microsoft Intune](../apps/lob-apps-android.md)
