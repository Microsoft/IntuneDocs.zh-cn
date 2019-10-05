---
title: 防止对公司门户进行未经授权的访问
titleSuffix: Microsoft Intune
description: 在公司网络外部共享公司数据时，使用 Microsoft Intune 防止未经授权的访问。
keywords: Office 365 O365 Azure 信息保护 数据保护 外部网络 公司数据
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6a88573a-aa60-455c-858c-74562798246b
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95d6f9c06ffac2f1205186c2c0881a2953c0f447
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732810"
---
# <a name="prevent-unauthorized-access-to-company-data-using-microsoft-intune"></a>使用 Microsoft Intune 防止对公司数据进行未经授权的访问

可对 Office 365 文档和电子邮件进行分类、应用标签和保护，仅允许经授权的用户访问数据。 当IT 管理员或用户设置规则或条件后，自动管理此设置。 也可由 IT 团队提供推荐的设置，让用户遵照。 管理员和用户也可在没有其他有权限的角色协助的情况下，撤消已与他人共享的数据的访问权限。 这样做的结果是，即使数据离开公司网络，也可控制能够打开或更新受保护数据的用户。 

## <a name="before-you-begin"></a>在开始之前

满足以下要求，可使用以下操作计划：
* 你的公司已准备好安全转换到云。
* 你的公司使用 Office 365 Exchange Online、SharePoint Online、OneDrive for Business 或 Yammer。
* 你的公司拥有 Microsoft 365、企业移动性 + 安全性 (EMS) 或 Azure 信息保护的许可证。
* 你的公司使用运行 Windows 7 Service Pack 1 或更高版本的设备。
* 你的公司通过 Office 365 专业增强版订阅使用 2016 或 2013 版应用、Office 专业增强版 2016、带有 Service Pack 1 的 Office 专业增强版 2013 或 Office 专业增强版 2010。

## <a name="action-plan"></a>操作计划

完成[Azure 信息保护快速入门教程](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial)。  

## <a name="what-to-tell-employees-and-students"></a>应告知员工和学生的事项

可共享以下详细信息：[如何以及何时保护包含敏感信息的文档和电子邮件](https://docs.microsoft.com/information-protection/deploy-use/help-users)。

## <a name="next-steps"></a>后续步骤

在后续步骤中，可详细了解增强公司数据保护的其他方式，包括： 

* 了解如何使用 [iOS 和 Android 设备上的 Azure 信息保护](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq)。
* 对于 Windows Phone 和 Mac 计算机，请参阅 [Microsoft Rights Management 共享应用程序](https://technet.microsoft.com/dn451248)。
