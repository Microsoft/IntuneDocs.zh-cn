---
title: "使用适用于 Android for Work 的 Intune 应用配置策略"
titlesuffix: Azure portal
description: "了解如何使用应用配置策略，为运行中的 Android for Work 应用提供配置数据。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4b73202a1a68bd2dd3dcbfa86c21cb09ae00056c
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-android-for-work"></a>如何使用适用于 Android for Work 的 Microsoft Intune 应用配置策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 中的应用配置策略可提供用户在运行 Android for Work 应用时可用的设置。 并非所有应用都支持应用配置。 请咨询应用的开发人员，确定他们是否生成了应用来支持应用配置策略。

应用配置策略可在用户运行应用之前，帮助你为用户预配置可用的应用设置。 一些 Android 应用支持受管理配置选项，可以使用[配置设计器](#use-configuration-designer)在 Azure 门户中配置这些选项。 无法使用配置设计器在应用上（例如捆绑型的应用）配置某些配置设置。  你将需要为这些值使用 [JSON 编辑器](#use-json-editor)。   在安装应用时，自动向应用提供设置。

无需直接向用户和设备分配这些策略。 而是将策略与应用关联，然后分配应用。 只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

## <a name="use-configuration-designer"></a>使用配置设计器

1. 在 Azure 门户中，选择“移动应用”。 在“管理”下方，选择“应用配置策略”并单击“添加”。
2. 设置以下详细信息：
    - **名称** - 将在 Azure 门户中显示的配置文件名称
    - **说明** - 将在 Azure 门户中显示的配置文件说明
    - **平台** - 选择 Android
    - 为你预先选择**设备注册类型** - **已注册 Intune**。
3. 选择“关联应用”，以选择要定义配置策略的应用。  从你已同意并与 Intune 同步的 Android for Work 应用列表中选择
4. 选择“配置设置”。
5. 对于**配置设置格式**，选择**使用配置设计器**。
6. 选择“添加”。 显示可用配置设置的列表。 该列表包括：
    - **配置密钥** - 设置的名称。
    - **值类型** - 可配置的设置，例如**布尔值**或**字符串**。
    - **描述** - 配置设置的描述。
7. 选择你想要使用此配置文件配置的设置的复选框，然后单击“确定”。
8. 系统将显示所选设置的列表，连同其可用的“配置值”。 指定每个设置的值，然后单击“确定”。

## <a name="use-json-editor"></a>使用 JSON 编辑器

1. 在 Azure 门户中，选择“移动应用”。 在“管理”下方，选择“应用配置策略”并单击“添加”。
2. 设置以下详细信息：
    - **名称** - 将在 Azure 门户中显示的配置文件名称
    - **说明** - 将在 Azure 门户中显示的配置文件说明
    - **平台** - 选择 Android
    - 为你预先选择**设备注册类型** - **已注册 Intune**。
3. 选择“关联应用”，以选择要定义配置策略的应用。  从你已同意并与 Intune 同步的 Android for Work 应用列表中选择。
5. 选择“配置设置”。
6. 对于“配置设置格式”，请选择“输入 JSON 编辑器”。
7. 在编辑器中可以定义配置设置的 JSON 值。 你可以选择“下载 JSON 模板”，下载随后可配置的示例文件。
8. 完成后，选择“确定”，然后单击“添加”。

将创建该策略并在“策略列表”边栏选项卡上显示。



当分配的应用在设备上运行时，将使用你在应用配置策略中配置的设置运行。

## <a name="preconfigure-permissions-grant-state-for-apps"></a>为应用预配置权限授予状态

你还可以为应用预配置权限以访问 Android 设备功能。 默认情况下，对于需要设备权限（如访问位置或设备相机等）的 Android 应用，系统会提示用户接受或拒绝权限。 例如，如果应用使用设备的麦克风，会提示最终用户授予应用权限以使用麦克风。

1. 在 Azure 门户中，选择“移动应用”。 在“管理”下方，选择“应用配置策略”并单击“添加”。
2. 设置以下详细信息：
    - **名称** - 将在 Azure 门户中显示的配置文件名称
    - **说明** - 将在 Azure 门户中显示的配置文件说明
    - **平台** - 选择 Android
    - 为你预先选择**设备注册类型** - **已注册 Intune**。
3. 选择“关联应用”，以选择要定义配置策略的应用。  从你已同意并与 Intune 同步的 Android for Work 应用列表中选择。
5. 选择“权限”，然后选择“添加”。
6. 从可用应用权限列表中选择，然后选择“确定”。
7. 为各权限选择选项以授予此策略：
    - **提示** - 提示用户接受或拒绝。
    - **自动授予** - 无需通知用户即自动批准。
    - **自动拒绝** - 无需通知用户即自动拒绝。
8. 要分配应用配置策略，请依次选择“应用配置策略”、“分配”，然后选择“选择组”。
9. 选择要分配的组，然后选择“选择”。
10. 选择“保存”以分配策略。

## <a name="next-steps"></a>后续步骤

照常继续[分配](apps-deploy.md)和[监视](apps-monitor.md)应用。

