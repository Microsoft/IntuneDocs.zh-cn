---
title: Microsoft Intune 的应用生命周期概述
description: 了解 Microsoft Intune 中托管的应用生命周期。 应用生命周期涉及到添加、部署、配置、保护和停用应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.openlocfilehash: 048b8472be00c544611fe2ea8763b16019cebc0b
ms.sourcegitcommit: 580eb4920d18ce09c9431d9d0dfee9d195459c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2018
ms.locfileid: "52887043"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Microsoft Intune 中的应用生命周期概述

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

当添加 Microsoft Intune 应用并进一步完成其他阶段时，该应用的生命周期便已开始，直到删除它。 通过了解这些阶段，可掌握在 Intune 中开始进行应用管理所需的详细信息。

![应用生命周期](./media/app-lifecycle.png "Intune 应用生命周期")

## <a name="add"></a>添加

应用部署的第一步是添加你要管理的应用并将其分配到 Intune 中。 尽管你可以使用许多不同的应用类型，但基本的过程都是相同的。 使用 Intune，可添加不同的应用类型，包括内部编写的应用（业务线）、应用商店中的应用、内置应用以及 Web 应用。 有关应用类型的详细信息，请参阅[如何将应用添加到 Microsoft Intune](apps-add.md)。 

## <a name="deploy"></a>在来宾群集上部署

在将应用添加到 Intune 后，就可以[将其分配到你管理的用户和设备](apps-deploy.md)。 Intune 让这一过程变得简单，部署应用后，可以在 Azure 门户中[监视 Intune 中的部署是否成功](apps-monitor.md)。 此外，在一些应用商店中，如 [Apple](vpp-apps-ios.md) 和 [Windows](windows-store-for-business.md) 应用商店，可以为公司批量购买应用许可证。 Intune 可以同步这些商店的数据，从而让你直接从 Intune 管理控制台为这些类型的应用部署和跟踪许可证使用情况。

## <a name="configure"></a>配置

作为应用生命周期的一部分，将定期发布新版本的应用。 Intune 提供一些工具，可轻松地[将你部署的应用更新](apps-add.md)到较新版本。 此外，你还可以为一些应用配置额外的功能，例如：
- [iOS 应用配置策略](app-configuration-policies-use-ios.md)为应用运行时所使用的兼容 iOS 应用提供设置。 例如，某个应用可能需要特定的品牌设置或必须连接的服务器的名称。
- [Managed Browser 策略](app-configuration-managed-browser.md)帮助你为 Intune Managed Browser 配置设置，该浏览器将取代默认设备浏览器并让你能够限制用户可以访问的网站。

## <a name="protect"></a>保护

Intune 为你提供了许多方法来帮助保护你的应用中的数据。 主要方法是：
- [条件访问](conditional-access.md)，根据指定的条件控制对电子邮件和其他服务的访问。 条件包括设备类型或者是否符合已部署的[设备合规性策略](device-compliance.md)。
- [应用保护策略](app-protection-policy.md)作用于各个应用，以帮助保护它们使用的公司数据。 例如，你可以限制在非托管应用和你管理的应用之间复制数据，或者可以阻止应用在已越狱或取得 root 权限的设备上运行。

## <a name="retire"></a>停用

最后，有可能你部署的应用会过期，并且需要将其删除。 Intune 使得[从服务停用应用](device-management.md)变得简单。

## <a name="next-steps"></a>后续步骤

- 了解 [Microsoft Intune 中的应用管理](app-management.md)