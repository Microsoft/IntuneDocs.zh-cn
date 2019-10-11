---
title: 为托管的 Android Enterprise 设备添加应用配置策略
titleSuffix: Microsoft Intune
description: 使用 Microsoft Intune 中的应用配置策略可提供用户在运行托管 Google Play 应用时的设置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59d93bed7bae2b757a4bd1e7b1dffc814629f6a1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725733"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>为托管的 Android Enterprise 设备添加应用配置策略

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune 中的应用配置策略向托管 Android Enterprise 设备上的托管 Google Play 应用提供设置。 应用开发人员公开 Android 托管的应用配置设置。 Intune 使用这些公开的设置来使管理员为应用配置功能。 应用配置策略已分配给用户组。 只要应用检测到策略设置（通常在应用首次运行时），即会使用它们。

> [!NOTE]  
> 并非所有应用都支持应用配置。 请咨询应用开发人员，确定他们的应用是否支持应用配置策略。

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，选择“客户端应用”   > “应用配置策略”   >  “添加”  。
2. 输入以下属性：

    - **名称**：输入策略的描述性名称。 为策略命名，以便稍后可以轻松地识别它们。 例如，策略名称最好是“适用于整个公司的 Android Enterprise Nine Work 应用策略”  。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **设备注册类型**：选择“受管理设备”  。
    - **平台**：选择“Android”  。

3. 选择“关联应用”  。 选择要定义应用配置策略的应用。 从已批准并与 Intune 同步的托管 Google Play 应用列表中选择。
4. 选择“权限”  。 可使用以下工具设置配置：

    - [配置设计器](#use-the-configuration-designer)
    - [JSON 编辑器](#enter-the-json-editor)

5. 选择“确定”   > “添加”  。

## <a name="use-the-configuration-designer"></a>使用配置设计器

当托管 Google Play 应用已设计为支持配置设置时，可以对该应用使用配置设计器。 配置适用于在 Intune 中注册的设备。 通过设计器可以为应用公开的设置配置特定的配置值。

1. 选择“添加”  。 选择想为应用输入的配置设置的列表。

    如果将 GMail 或 Nine Work 用于电子邮件应用，请参阅[用于配置电子邮件的 Android Enterprise 设备设置](../email-settings-android-enterprise.md)以了解有关这些设置的详细信息。

2. 对于配置中的每个项和值，请设置以下内容：

    - **值类型**：配置值的数据类型。 至于字符串值类型，可以根据需要选择变量或证书配置文件作为值类型。
    - **配置值**：配置的值。 如果选择变量或证书作为值类型  ，则从变量或证书配置文件的列表中进行选择。 如果选择证书，则会在运行时填充部署到设备的证书的证书别名。

### <a name="supported-variables-for-configuration-values"></a>可用作配置值的变量

如果选择变量作为值类型，有以下选项可供选择：

| 选项 | 示例 |
|----|----|
| Mail | john@contoso.com |
| 用户主体名称 | john@contoso.com |
| 部分 UPN | john |
| Domain | contoso.com |
| 用户名 | John Doe |
| 帐户 ID | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| 用户 ID | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| 设备 ID | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>仅允许在多身份应用中配置组织帐户 

对于 Android 设备，请使用以下键/值对：

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **值** | <ul><li>一个或多个 <code>;</code> 分隔的 UPN。</li><li>仅允许此键定义的托管用户帐户。</li><li> 对于已注册 Intune 的设备，<code>{{userprincipalname}}</code> 令牌可用于表示已注册的用户帐户。</li></ul> |

   > [!NOTE]
   > 当仅允许多身份配置的组织帐户时，必须使用 Outlook for Android 2.2.222 或更高版本。<p></p>
   > 作为 Microsoft Intune 管理员，可控制将哪些用户帐户添加到托管设备上的 Microsoft Office 应用程序。 可以将访问权限限制为仅允许的组织用户帐户，并阻止已注册设备上的个人帐户。 支持性应用程序将处理应用配置并删除和阻止未经批准的帐户。<p></p>
   > 对于 Microsoft Word、Microsoft Excel、Microsoft PowerPoint，必须使用应用版本 16.0.9327.1000 及更高版本。 

## <a name="enter-the-json-editor"></a>输入 JSON 编辑器

无法使用配置设计器在应用上（例如捆绑型的应用）配置某些配置设置。 使用 JSON 编辑器配置这些值。 在安装应用时，自动向应用提供设置。

1. 对于“配置设置格式”  ，请选择“输入 JSON 编辑器”  。
2. 在编辑器中，可定义配置设置的 JSON 值。 你可以选择“下载 JSON 模板”  ，下载随后可配置的示例文件。
3. 选择“确定”，然后选择“添加”   。

此时，策略创建完成，并出现在列表中。

当分配的应用在设备上运行时，将使用你在应用配置策略中配置的设置运行。

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>为应用预配置权限授予状态

你还可以预配置应用权限以访问 Android 设备功能。 默认情况下，对于需要设备权限（如访问位置或设备相机等）的 Android 应用，系统会提示用户接受或拒绝权限。

例如，应用使用设备的麦克风。 系统会提示用户授予应用权限以使用麦克风。

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，选择“客户端应用”   > “应用配置策略”   >  “添加”  。
2. 输入以下属性：

    - **名称**：输入策略的描述性名称。 为策略命名，以便稍后可以轻松地识别它们。 例如，策略名称最好是“适用于整个公司的 Android Enterprise 提示权限应用策略”  。
    - **说明**。 输入配置文件的说明。 此设置是可选的，但建议进行。
    - **设备注册类型**：选择“受管理设备”  。
    - **平台**：选择“Android”  。

3. 选择“关联应用”  。 选择要定义配置策略的应用。 从已批准并与 Intune 同步的 Android 工作配置文件应用列表中选择。
4. 选择“权限”   > “添加”  。 从列表中，选择可用的应用权限 >“确定”  。
5. 为各权限选择选项以授予此策略：
    - “提示”  。 提示用户接受或拒绝。
    - **“自动授予”** 。 无需通知用户即自动批准。
    - “自动拒绝”  。 无需通知用户即自动拒绝。
6. 要分配应用配置策略，请依次选择“应用配置策略”>“分配”   > “选择组”  。 选择要分配的用户组 >“选择”  。
7. 选择“保存”  以分配策略。

## <a name="additional-information"></a>其他信息

- [将托管 Google Play 应用分配到 Android Enterprise 设备](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [部署 Outlook for iOS 和 Outlook for Android 应用配置设置](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>后续步骤

继续[分配](apps-deploy.md)和[监视](apps-monitor.md)应用。
