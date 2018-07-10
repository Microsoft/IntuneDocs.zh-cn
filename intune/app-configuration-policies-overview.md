---
title: Microsoft Intune 的应用配置策略
titlesuffix: ''
description: 了解如何在 Microsoft Intune 中的 iOS 或 Android 设备上使用应用配置策略。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6c04d2d8fa2e302c4d11760d3660a0a67e8b3695
ms.sourcegitcommit: b47fad133ef8ef1eb65484463431c6c53f6a638a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35291540"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Microsoft Intune 的应用配置策略

使用 Microsoft Intune 中的应用配置策略提供适用于 iOS 或 Android 应用的配置设置。 可利用这些配置设置自定义应用。 无需直接向用户和设备分配这些配置策略。 而是应将配置策略与一个应用相互关联，然后分配该应用。 只要应用检测到配置策略设置（通常在其首次运行时），即会使用它们。

可通过将包括和排除分配相结合来向一组用户和设备分配应用配置策略。 添加应用配置策略后，即可设置应用分配策略的配置。 设置策略分配时，可选择包括和排除应用该策略的用户组。 选择包括一个或多个组时，可以选择要包括的特定组或选择内置组。 内置组包括“所有用户”、“所有设备”和“所有用户 + 所有设备”。

例如，应用可能要求指定以下任意详细信息：

- 自定义端口号
- 语言设置
- 安全设置
- 公司徽标之类的品牌设置

如果用户输入的这些设置不正确，可能会加重支持人员的负担并降低新应用的采用率。

通过让你在运行应用之前将策略中的这些设置分配给用户，应用配置策略可消除此类问题。 随后这些设置会自动提供，用户无需执行任何操作。

只要应用检测到配置设置，即会使用它们。 通常情况下，应用在用户首次运行该应用时检测配置设置。

对于如何使用 Intune 的应用配置，你有两个选择：
 - **受管理设备** - 设备由 Intune 作为移动设备管理 (MDM) 提供程序进行管理。
 - **托管应用** - 在未进行设备注册的情况下受到管理的应用。

## <a name="apps-that-support-app-configuration"></a>支持应用配置的应用

可对支持应用配置策略的应用使用该策略。 要在 Intune 中提供应用配置，应用必须编写为支持使用应用配置。 有关详细信息，请咨询应用供应商。

可通过如下方式准备业务线应用：将 Intune App SDK 合并到应用，或在开发应用后对其进行包装。 Intune App SDK 可用于 iOS 和 Android，可对应用启用 Intune 应用配置策略。 其将努力使应用开发人员所需的代码更改数量降到最低。 有关详细信息，请参阅 [Intune App SDK 概述](app-sdk.md)。

## <a name="graph-api-support-for-app-configuration"></a>应用配置的图形 API 支持

此外，可使用图形 API 完成应用配置任务。 有关详细信息，请参阅[针对 Graph API 参考 MAM 的配置](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)。

## <a name="next-steps"></a>后续步骤

### <a name="managed-devices"></a>托管设备

 - 了解如何将应用配置用于 iOS 设备。  请参阅[为受管理的 iOS 设备添加应用配置策略](app-configuration-policies-use-ios.md)。
 - 了解如何将应用配置用于 Android 设备。  请参阅[为受管理的 Android 设备添加应用配置策略](app-configuration-policies-use-android.md)。

### <a name="managed-apps"></a>托管应用

 - 了解如何将应用配置用于受管理的应用。 请参阅[为受管理应用添加应用配置策略（无需设备注册）](app-configuration-policies-managed-app.md)。
