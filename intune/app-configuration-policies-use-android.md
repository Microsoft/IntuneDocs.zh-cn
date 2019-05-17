---
title: 为受管理的 Android 设备添加应用配置策略
titleSuffix: Microsoft Intune
description: 使用 Microsoft Intune 中的应用配置策略，可提供用户在运行 Android 工作配置文件应用时的设置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dccbfe597fa4bd461bb71cb86d38ffdfd52d719a
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567421"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>为受管理的 Android 设备添加应用配置策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 中的应用配置策略，可为 Android 工作配置文件应用提供设置。 应用开发人员必须公开 Android 托管应用配置设置，以便指定该应用的配置设置。 将应用配置策略分配给想要应用设置的用户组。  只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

> [!Note]  
> 并非所有应用都支持应用配置。 请咨询应用开发人员，确定他们构建的应用是否支持应用配置策略。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 选择“客户端应用”工作负载。
4. 在“管理”组中，选择“应用配置策略”，然后选择“添加”。
5. 设置以下详细信息：
    - **名称** - 将在 Azure 门户中显示的配置文件名称。
    - **说明** - 将在 Azure 门户中显示的配置文件说明。
    - **设备注册类型** - 选择“托管应用”。
6. 对“平台”选择“Android”。
7. 选择“关联应用”，可选择要为其定义应用配置策略的应用。 从已批准并与 Intune 同步的 Android 工作配置文件应用列表中选择。
8. 选择“权限”。 可使用以下工具设置配置：
    - [配置设计器](#use-the-configuration-designer)
    - [JSON 编辑器](#enter-the-json-editor)
9. 选择“确定”，然后选择“添加”。

## <a name="use-the-configuration-designer"></a>使用配置设计器

当 Android 应用已设计为支持配置设置时，可以对该应用使用配置设计器。 配置将应用于已在 Intune 中注册的设备。 相较于应用公开，通过设计器可以为设置配置特定的配置值。

选择“添加”，以选择想为应用指定的配置设置的列表。  
对于配置中的每个项和值，请设置以下内容：

  - **值类型**  
    配置值的数据类型。 至于字符串值类型，可以根据需要选择变量或证书配置文件作为值类型。
  - **配置值**  
    配置的值。 如果选择变量或证书作为值类型，则可以从配置值下拉列表中的一系列变量或证书配置文件中进行选择。  如果选择证书，则运行时将填充部署到设备的证书的证书别名。
    
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
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **值** | <ul><li>一个或多个 <code>;</code> 分隔的 UPN。</li><li>仅允许此键定义的托管用户帐户。</li><li> 对于已注册 Intune 的设备，<code>{{userprincipalname}}</code> 令牌可用于表示已注册的用户帐户。</li></ul> |

   > [!NOTE]
   > 当仅允许多身份配置的组织帐户时，必须使用 Outlook for Android 2.2.222 或更高版本。<p></p>
   > 作为 Microsoft Intune 管理员，可控制将哪些用户帐户添加到托管设备上的 Microsoft Office 应用程序。 可以将访问权限限制为仅允许的组织用户帐户，并阻止已注册设备上的个人帐户。 支持性应用程序将处理应用配置并删除和阻止未经批准的帐户。<p></p>
   > 对于 Microsoft Word、Microsoft Excel、Microsoft PowerPoint，必须使用应用版本 16.0.9327.1000 及更高版本。 

## <a name="enter-the-json-editor"></a>输入 JSON 编辑器

无法使用配置设计器在应用上（例如捆绑型的应用）配置某些配置设置。 需要使用 JSON 编辑器配置这些值。 在安装应用时，自动向应用提供设置。

1. 对于“配置设置格式”，请选择“输入 JSON 编辑器”。
2. 在编辑器中，可定义配置设置的 JSON 值。 你可以选择“下载 JSON 模板”，下载随后可配置的示例文件。
3. 选择“确定”，然后选择“添加”。

将创建该策略并在“策略列表”边栏选项卡上显示。

当分配的应用在设备上运行时，将使用你在应用配置策略中配置的设置运行。

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>为应用预配置权限授予状态

你还可以为应用预配置权限以访问 Android 设备功能。 默认情况下，对于需要设备权限（如访问位置或设备相机等）的 Android 应用，系统会提示用户接受或拒绝权限。 例如，如果应用使用设备的麦克风，会提示用户授予应用权限以使用麦克风。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 选择“客户端应用”。
3. 在“管理”下，选择“应用配置策略”，然后选择“添加”。
4. 设置以下详细信息：
    - **名称**。 在 Azure 门户中显示的配置文件名称。
    - **说明**。 在 Azure 门户中显示的配置文件说明。
    - “设备注册类型”。 选择“受管理设备”。
    - “平台”。 选择“Android”。
5. 选择“关联应用”，以选择要定义配置策略的应用。 从已批准并与 Intune 同步的 Android 工作配置文件应用列表中选择。
6. 选择“权限”，然后选择“添加”。
7. 从可用应用权限列表中选择，然后选择“确定”。
8. 为各权限选择选项以授予此策略：
    - “提示”。 提示用户接受或拒绝。
    - **“自动授予”**。 无需通知用户即自动批准。
    - “自动拒绝”。 无需通知用户即自动拒绝。
9. 要分配应用配置策略，请依次选择“应用配置策略”、“分配”，然后选择“选择组”。
10. 选择要分配的组，然后选择“选择”。
11. 选择“保存”以分配策略。

## <a name="next-steps"></a>后续步骤

继续[分配](apps-deploy.md)和[监视](apps-monitor.md)应用。

