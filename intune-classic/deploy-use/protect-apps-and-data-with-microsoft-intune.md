---
title: "保护应用和数据"
description: "本主题介绍供你使用的各种 Intune 特性和功能，以帮助保护你的公司应用和数据。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 59168615548d3c7da8dc284476227ed0f01ceffe
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="protect-apps-and-data-with-microsoft-intune"></a>使用 Microsoft Intune 保护应用和数据

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 通过多个技术层保护公司数据。 在标识层上，条件性访问通过仅允许从托管及合规设备进行访问来保护对服务的访问。 在客户端应用程序层上，移动应用管理 (MAM) 通过防止将数据移动到不受保护的应用或存储位置以及在设备丢失或被盗时擦除数据来防止数据丢失。 应结合使用这两个保护层，在保持移动办公人员高效工作的同时保护数据。

保护公司数据的第一步是实施条件性访问，这一步非常重要。 这可通过确保用于访问数据的设备使用强密码和加密等安全保护且未越狱来实现。 使用 Intune，可设置设备必须遵守才能访问公司电子邮件和数据的条件。

[条件性访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)由可在 Intune 中设置的两种策略类型决定：
- [合规性策略](introduction-to-device-compliance-policies-in-microsoft-intune.md)用于确定设备的合规性。 它们评估以下设置和条件：
  - PIN 和密码：可创建以下规则：必须提供密码才可解锁设备、设定密码的复杂性要求和其他密码设置。
  - 加密：你可以限制对加密设备的访问。
  - 设备未越狱或取得 root 权限：Intune 可检测注册的设备是否已越狱。 可以设置策略来阻止此类设备的访问。
- [条件性访问策略](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)专为 Exchange Online 或 SharePoint Online 等特定服务配置。 对于每个服务，你可以定义这些策略应该应用到哪些用户组。 例如，你可以确保财务部门的每个人只能从注册的合规设备访问公司电子邮件。

保护对公司资源的访问只是保护公司数据的第一步。 在设备上访问数据后，仍需要保护数据的能力。 现在可以将数据复制、移动、保存到其他位置，或进行共享。 Intune 通过创建以下规则组来向你提供限制数据移动的能力，从而解决此问题：
- 阻止复制和粘贴，或防止将数据传输到工作环境之外。
- 防止备份到个人云存储位置，防止“另存为”等功能。
- 要求 PIN/密码或企业凭据，保障应用访问安全。
- 在 Intune 管理的浏览器中打开所有 Web 链接。

这些规则组被称为[移动应用管理 (MAM) 策略](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。 可将 MAM 策略应用于设备上运行的应用，无论该设备是否受管理均是如此。  

可对**已在 Intune 中注册的设备**、**由其他第三方移动设备管理 (MDM) 解决方案注册或管理的设备**，或者**未在任何 MDM 解决方案中注册的设备**（例如员工自有设备）应用 MAM 策略来保护公司数据。

若要将应用与 MAM 策略相关联，该应用必须包含 Microsoft Intune 应用软件开发工具包 (SDK)，或者能够使用应用包装工具。

与 Microsoft Office 应用类似的应用内置了 Intune 应用 SDK。 若要查看所支持应用的完整列表，请转到 Microsoft Intune 应用程序合作伙伴页面上的 [Microsoft Intune 移动应用程序库](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。 选择应用可查看支持的方案、平台以及应用是否支持多身份。

还可[启用自定义构建的业务线应用](/intune/apps-prepare-mobile-application-management)，与 MAM 策略配合使用。

如果设备丢失或被盗，或者用户不再与公司合作，除了限制数据移动之外，还可[选择性擦除公司数据](wipe-managed-company-app-data-with-microsoft-intune.md)，仅保留个人数据。
