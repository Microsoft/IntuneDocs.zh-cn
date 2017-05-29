---
title: "阻止公司数据从 Office 365 移动应用中泄露 | Microsoft Docs"
description: "可通过 Intune，使用移动应用管理 (MAM) 策略保护组织的数据，此策略可防止公司数据从 Office 365 移动应用或其他业务线 (LOB) 应用中泄露。"
keywords: 
author: jeffgilb
ms.author: jeffgilb
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 19be3de7-539c-49f5-8c46-5363b987fef9
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: db350fbefe5ed9b1aa796ee8430000d33ebd1b4e
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="quick-start-guide-prevent-company-data-leaks-from-office-365-mobile-apps"></a>快速入门指南：阻止公司数据从 Office 365 移动应用中泄露

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可以使用移动应用管理 (MAM) 策略帮助你保护组织的数据，此策略可防止从 Office 365 移动应用或其他业务线 (LOB) 应用泄露公司数据。 可以使用 Intune MAM 策略，而无需最终用户在 Intune 移动设备管理 (MDM) 中注册其设备。 因此，如果某些用户不希望将其 BYOD iOS 或 Android 移动设备注册到 Microsoft MDM 解决方案（Intune、Configuration Manager 或 EAS），你想要无需管理最终用户设备即可保护公司数据，或者你已在使用非 Microsoft MDM 解决方案，则 Intune 可以帮助你提高公司数据的安全性。   

## <a name="is-this-quick-start-guide-right-for-me"></a>此快速入门指南适合我吗？
要允许最终用户无需在移动设备管理 (MDM) 解决方案中注册设备即可访问其 iOS 和 Android 设备上的 Office 365 和 LOB 应用数据，但仍控制他们可以或不可以将数据复制和粘贴到个人应用吗？

如果是，Microsoft Intune 允许你在 iOS 和 Android 上设置 Office 365 移动应用的 MAM 策略，包括剪切/复制/粘贴限制、防止“另存为”、设置 PIN 要求以及能够以远程方式擦除 MAM 保护的数据。  这样无需用户将其设备注册到 MDM 解决方案即可保护公司数据，同时保持 Office 移动应用有很好的最终用户体验。

## <a name="how-do-i-do-it"></a>如何操作？
1.    基本了解 Intune 移动应用程序管理 (MAM) 的工作原理 /intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。
2.    了解在 Azure 门户中[创建 MAM 策略之前需要执行的操作](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。
3.    使用 Intune [创建和部署 MAM 策略](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。

### <a name="additional-information"></a>其他信息:
- 使用启用 MAM 的应用的[最终用户体验](/intune-classic/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune)。
- [使用 Intune 准备适用于 MAM 的 LOB 应用](/intune-classic/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
- <a href="https://www.microsoft.com/cloud-platform/microsoft-intune-partners" target="_blank">Microsoft Intune 应用程序合作伙伴列表 &rarr;</a> 提供启用了 MAM 的应用。

## <a name="what-should-i-do-next"></a>接下来我该怎么办？
[从非 Microsoft MDM 解决方案迁移到 Microsoft Intune](/intune-classic/deploy-use/migrate-to-intune)

[在 Intune MDM 中注册设备](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)

