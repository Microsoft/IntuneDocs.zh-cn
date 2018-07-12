---
title: 为受管理的 Android 设备添加应用配置策略
titlesuffix: Microsoft Intune
description: 使用 Microsoft Intune 中的应用配置策略，可提供用户在运行 Android 工作配置文件应用时的设置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c837f9a5a2cb1a6f267f85f888453725da6acb66
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905744"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>为受管理的 Android 设备添加应用配置策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 中的应用配置策略，可为 Android 工作配置文件应用提供设置。 应用开发人员必须公开 Android 托管应用配置设置，以便指定该应用的配置设置。 将应用配置策略分配给想要应用设置的用户组。  只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

> [!Note]  
> 并非所有应用都支持应用配置。 请咨询应用开发人员，确定他们构建的应用是否支持应用配置策略。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 选择“移动应用”工作负荷。
4. 在“管理”组中，选择“应用配置策略”，然后选择“添加”。
5. 设置以下详细信息：
    - **名称** - 将在 Azure 门户中显示的配置文件名称。
    - **说明** - 将在 Azure 门户中显示的配置文件说明。
    - **设备注册类型** - 选择“托管应用”。
6. 对“平台”选择“Android”。
7. 选择“关联应用”，可选择要为其定义应用配置策略的应用。 从已批准并与 Intune 同步的 Android 工作配置文件应用列表中选择。
8. 选择“权限”。 可使用以下工具设置配置：
    - [配置设计器](#Use-the-configuration-designer)
    - [JSON 编辑器](#Enter-the-JSON-editor)
9. 选择“确定”，然后选择“添加”。

## <a name="use-the-configuration-designer"></a>使用配置设计器

可以对支持配置的 Android 应用使用配置设计器。 配置将应用于已在 Intune 中注册的设备。 相较于应用公开，通过设计器可以为设置配置特定的配置值。

选择“添加”，以选择想为应用指定的配置设置的列表。  
对于配置中的每个项和值，请设置以下内容：

  - **值类型**  
    配置值的数据类型。 至于字符串值类型，可以根据需要选择变量或证书配置文件作为值类型。
  - **配置值**  
    配置的值。 如果选择变量或证书作为值类型，则可以从配置值下拉列表中的一系列变量或证书配置文件中进行选择。  如果选择证书，则运行时将填充部署到设备的证书的证书别名。
    
### <a name="supported-variables-for-configuration-values"></a>可用作配置值的变量

如果选择变量作为值类型，有以下选项可供选择：
- 用户主体名称 - 例如 John@contoso.com
- 邮件 - 例如 John@contoso.com
- &IAM;Partian UPN - 例如 John
- 帐户 ID - 例如 fc0dc142-71d8-4b12-bbea-bae2a8514c81
- 设备 ID - 例如 b9841cd9-9843-405f-be28-b2265c59ef97
- 用户 ID -例如 3ec2c00f-b125-4519-acf0-302ac3761822
- 用户名称 - 例如 John Doe


## <a name="enter-the-json-editor"></a>输入 JSON 编辑器

无法使用配置设计器在应用上（例如捆绑型的应用）配置某些配置设置。 需要使用 JSON 编辑器配置这些值。 在安装应用时，自动向应用提供设置。

1. 对于“配置设置格式”，请选择“输入 JSON 编辑器”。
2. 在编辑器中，可定义配置设置的 JSON 值。 你可以选择“下载 JSON 模板”，下载随后可配置的示例文件。
3. 选择“确定”，然后选择“添加”。

将创建该策略并在“策略列表”边栏选项卡上显示。

当分配的应用在设备上运行时，将使用你在应用配置策略中配置的设置运行。

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>为应用预配置权限授予状态

你还可以为应用预配置权限以访问 Android 设备功能。 默认情况下，对于需要设备权限（如访问位置或设备相机等）的 Android 应用，系统会提示用户接受或拒绝权限。 例如，如果应用使用设备的麦克风，会提示用户授予应用权限以使用麦克风。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 选择“移动应用”。
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

