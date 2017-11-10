---
title: "为受管理的 Android 设备添加应用配置策略 | Microsoft Docs"
titlesuffix: Azure portal
description: "了解如何使用应用配置策略，为运行中的 Android for Work 应用提供配置数据。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e56aff30b353a2c98eb7effbec3e02bde066804f
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2017
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>为受管理的 Android 设备添加应用配置策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 中的应用配置策略可提供用户在运行 Android for Work 应用时的设置。 无需直接向用户和设备分配这些策略。 而是将策略与应用关联，然后分配应用。 只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

> [!Note]  
> 并非所有应用都支持应用配置。 请咨询应用开发人员，确定他们构建的应用是否支持应用配置策略。

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 选择“移动应用”工作负荷。
4. 在“管理”组中，单击“应用配置策略”，然后单击“添加”。
5. 设置以下详细信息：
    - **名称**  
      在 Azure 门户中显示的配置文件名称。
    - **描述**  
      在 Azure 门户中显示的配置文件说明。
    - **设备注册类型**  
      选择“受管理设备”。
6. 对“平台”选择“Android”。
7. 选择“关联应用”，以选择要为其定义应用配置策略的应用。  从你已同意并与 Intune 同步的 Android for Work 应用列表中选择。
8. 选择“配置设置”。 可使用以下方法设置配置：
    - [配置设计器](#Use-the-configuration-designer)
    - [输入 JSON 编辑器](#Use-the-JSON-editor)
9. 单击“确定”，然后单击“添加”。

## <a name="use-the-configuration-designer"></a>使用配置设计器

可对已注册或未注册 Intune 的设备上的应用使用配置设计器。 使用设计器可配置特定配置项和值。 还须指定每个值的数据类型。

对于配置中的每个项和值，请设置以下内容：

  - **配置项**  
     用于对特定设置配置进行唯一标识。
  - **值类型**  
    配置值的数据类型。 类型包括整数、实数、字符串或布尔值。
  - **配置值**  
    配置的值。 

## <a name="enter-the-json-editor"></a>输入 JSON 编辑器

无法使用配置设计器在应用上（例如捆绑型的应用）配置某些配置设置。  需要使用 JSON 编辑器配置这些值。 在安装应用时，自动向应用提供设置。

1. 对于“配置设置格式”，请选择“输入 JSON 编辑器”。
2. 在编辑器中，可定义配置设置的 JSON 值。 你可以选择“下载 JSON 模板”，下载随后可配置的示例文件。
3. 完成后，选择“确定”，然后单击“添加”。

将创建该策略并在“策略列表”边栏选项卡上显示。

当分配的应用在设备上运行时，将使用你在应用配置策略中配置的设置运行。

## <a name="preconfigure-permissions-grant-state-for-apps"></a>为应用预配置权限授予状态

你还可以为应用预配置权限以访问 Android 设备功能。 默认情况下，对于需要设备权限（如访问位置或设备相机等）的 Android 应用，系统会提示用户接受或拒绝权限。 例如，如果应用使用设备的麦克风，会提示最终用户授予应用权限以使用麦克风。

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 选择“移动应用”。 在“管理”下，选择“应用配置策略”，然后单击“添加”。
4. 设置以下详细信息：
    - **名称** - 将在 Azure 门户中显示的配置文件名称
    - **说明** - 将在 Azure 门户中显示的配置文件说明
    - **平台** - 选择 Android
    - 设备注册类型  -  已为你预先选择“受管理设备”。
5. 选择“关联应用”，以选择要定义配置策略的应用。  从你已同意并与 Intune 同步的 Android for Work 应用列表中选择。
6. 选择“权限”，然后选择“添加”。
7. 从可用应用权限列表中选择，然后选择“确定”。
8. 为各权限选择选项以授予此策略：
    - **提示** - 提示用户接受或拒绝。
    - **自动授予** - 无需通知用户即自动批准。
    - **自动拒绝** - 无需通知用户即自动拒绝。
9. 要分配应用配置策略，请依次选择“应用配置策略”、“分配”，然后选择“选择组”。
10. 选择要分配的组，然后选择“选择”。
11. 选择“保存”以分配策略。

## <a name="next-steps"></a>后续步骤

继续[分配](apps-deploy.md)和[监视](apps-monitor.md)应用。

