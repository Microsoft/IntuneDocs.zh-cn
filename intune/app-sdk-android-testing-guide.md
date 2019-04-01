---
title: Microsoft Intune App SDK for Android 开发人员测试指南
description: Microsoft Intune App SDK for Android 测试指南可帮助您测试 Intune 托管 Android 应用。
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072466"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Microsoft Intune App SDK for Android 开发人员测试指南

Microsoft Intune App SDK for Android 测试指南旨在帮助您测试 Intune 托管 Android 应用。  

## <a name="prerequisite-test-accounts"></a>必备项测试帐户
使用和不使用预生成的数据，可以创建新帐户。 创建新帐户：
1. 导航到[Microsoft 演示](https://demos.microsoft.com/environments/create/tenant)站点。 
2. [将 Intune 设置为](https://docs.microsoft.com/intune/setup-steps)若要启用移动设备管理 (MDM)。
3. [创建用户](https://docs.microsoft.com/intune/users-add)。
4. [创建组](https://docs.microsoft.com/intune/groups-add)。
5. [将许可证分配](https://docs.microsoft.com/intune/licenses-assign)以适合您的测试。


## <a name="azure-portal-policy-configuration"></a>Azure 门户策略配置
[创建和分配应用保护策略](https://docs.microsoft.com/intune/app-protection-policies)中[Azure 门户的 Intune 边栏选项卡](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)。 你[应用配置策略](https://docs.microsoft.com/intune/app-configuration-policies-overview)还可以创建并在 Intune 边栏选项卡中分配。

> [!NOTE]
> 如果在 Azure 门户中未列出您的应用程序，可以针对它的策略通过选择**更多应用**选项并提供在文本框中的包名称。

> [!IMPORTANT]
> 对于要应用的应用配置策略，注册的用户必须面向[Intune 应用保护策略](https://docs.microsoft.com/intune/app-protection-policy)。

## <a name="test-cases"></a>测试用例

以下测试用例提供配置和确认步骤。 使用此指南可帮助解决 Intune 托管 Android 应用的问题。

### <a name="required-pin-and-corporate-credentials"></a>需要的 PIN 和公司凭据

你可以要求使用 pin 才能访问公司资源。 此外，用户可以使用托管的应用可以强制执行企业身份验证。 使用以下步骤来设置这些要求：

1. 配置**需要 PIN 才能进行访问**并**访问需要公司凭据**到**是**。 有关详细信息，请参阅 [Microsoft Intune 中的 Android 应用保护策略设置](app-protection-policy-settings-android.md#access-requirements)。
2. 确认以下情况：
    - 应用程序启动应显示要求提供 PIN 输入安装程序和/或在使用公司门户注册时，使用生产用户的提示。
    - 未能提供有效的登录提示可能是由于配置不正确的 android 清单，特别是 ADAL 集成 （SkipBroker、 ClientID 和颁发机构） 的值。
    - 若要显示任何提示的失败可能是因为未正确集成`MAMActivity`值。 有关详细信息`MAMActivity`，请参阅[Microsoft Intune App SDK for Android 开发人员指南](app-sdk-android.md)。

> [!NOTE] 
> 如果不使用更高版本的测试，下面的测试可能也将失败。 审阅[SDK](app-sdk-android.md##sdk-integration)并[ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)集成。

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>限制传输和接收数据与其他应用程序
您可以控制企业的托管应用程序之间的数据传输，如下所示：

1. 设置**允许应用将数据传输到其他应用**到**策略托管应用**。
2. 将“允许应用从其他应用接收数据”设置为“所有应用”。 意向和内容提供商的使用将受这些策略。
3. 确认以下情况：
    - 从非托管应用程序到你的应用程序函数中正确打开。
    - 允许共享托管的应用之间的内容。
    - 已阻止对非托管应用 (例如，Chrome) 共享来自托管应用。

### <a name="restrict-cut-copy-and-paste"></a>限制剪切、复制和粘贴
按如下所示，可以限制对托管应用程序系统剪贴板：

1. 设置**限制剪切、 复制和与其他应用粘贴**到**带粘贴的策略托管**。
2. 确认以下情况：
    - 将文本从您的应用程序复制到托管的非托管的应用 （例如，消息） 会被阻止。

### <a name="prevent-save-as"></a>阻止“另存为”
您可以控制**另存为**功能，如下所示：

1. 如果你的应用需要[集成另存为控件](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)，请设置**另存为禁止**到**是**。
2. 确认以下情况：
    - 保存限制到仅相应的托管位置。

### <a name="file-encryption"></a>文件加密
可以按如下所示加密设备上的数据：

1. 设置**加密应用数据**到**是**。
2. 确认以下情况：
    - 正常的应用程序行为不受影响。

### <a name="prevent-android-backups"></a>阻止 Android 备份
您可以控制应用备份，请按如下所示：

1. 如果设置了[集成备份限制](app-sdk-android.md#protecting-backup-data)，配置**阻止 Android 备份**到**是**。
2. 确认以下情况：
    - 备份会受到限制。

### <a name="unenrollment"></a>取消注册
可远程擦除包含公司电子邮件和文档中的托管的应用和个人数据进行解密时不能再进行，如下所示的管理：

1. 从 Azure 门户中，[的擦除](https://docs.microsoft.com/intune/apps-selective-wipe)。
2. 如果您的应用程序不会注册为擦除的任何处理程序确认以下条件：
    - 应用程序的完全擦除会发生。
3. 如果您的应用程序已注册的`WIPE_USER_DATA`或`WIPE_USER_AUXILARY_DATA`，确认以下条件：
    - 托管的内容是从应用中删除。 有关详细信息，请参阅[Intune App SDK for Android 开发人员指南-选择性擦除](app-sdk-android.md#selective-wipe)。

### <a name="multi-identity"></a>多身份标识
将集成[多重身份验证支持](app-sdk-android.md#multi-identity-optional)需要彻底进行测试的高风险更改。 最常见的问题将是由于不正确设置的标识 （与威胁级别上下文），也在跟踪文件 (`MAMFileProtectionManager`)。

最小日志应重新验证多身份标识的以下方案：

- **另存为**策略是否正常工作的管理的标识。
- 复制并粘贴从正确地强制执行限制到个人管理。
- 只有属于托管标识的数据进行加密，不会修改个人文件。
- 在取消注册过程的选择性擦除仅删除托管的标识数据。
- 从非托管更改为托管帐户 （仅限首次） 时，将为条件启动提示最终用户。

### <a name="app-configuration-optional"></a>应用程序配置 （可选）
可以配置托管应用的行为，如下所示：

1. 如果你的应用消耗的任何应用程序配置设置，您应测试您的应用程序正确地处理 （作为管理员） 可以设置的所有值。 [应用配置策略](https://docs.microsoft.com/intune/app-configuration-policies-overview)可以创建和使用 Intune 中分配。

## <a name="next-steps"></a>后续步骤

- [将 Android 业务线应用添加到 Microsoft Intune](lob-apps-android.md)。
