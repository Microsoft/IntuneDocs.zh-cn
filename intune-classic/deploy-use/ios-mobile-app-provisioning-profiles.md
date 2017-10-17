---
title: "应用预配配置文件"
description: "Intune 提供了一些工具，用于将新的预配配置文件策略主动部署到安装了即将到期应用的设备。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d39d4deb00c7a79b856b82d57b042b0fdc585507
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="use-ios-mobile-provisioning-profile-policies-to-prevent-your-apps-from-expiring"></a>使用 iOS 移动预配配置文件策略防止你的应用过期

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

部署到 iPhone 和 iPad 的 Apple iOS 业务线应用附带已包含的预配配置文件和证书签名的代码。 应用运行时，iOS 将确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。 发生以下验证：

- **安装文件完整性** - iOS 将应用详细信息与企业签名证书的公钥进行比较。 如果它们不同，则应用内容可能已经更改，该应用不允许运行。
- **功能强制实施** - iOS 尝试从应用安装 (.ipa) 文件中的企业预配配置文件（而非各开发人员预配配置文件）强制实施应用功能。


用于签署应用的企业签名证书通常持续三年。 但是，预配配置文件在 1 年后过期。 使用 Intune 对拥有即将过期（但证书仍然有效）应用的设备主动部署新的预配配文件策略。
证书过期后，必须使用新证书再次对应用进行签名，并使用新证书的密钥嵌入新的预配配置。



## <a name="how-to-find-out-when-a-line-of-business-app-will-expire"></a>如何知道业务线应用何时过期

1. 在“[Microsoft Intune 管理控制台](https://manage.microsoft.com)”中，选择“**应用**” > “**应用**”。
2. 在应用列表中，查看“**到期日期**”列以查看应用的到期日期。 你还可以将“**筛选器**”下拉列表设置为“**过期/即将到期**”以仅查看你必须采取操作的应用。

## <a name="how-to-create-an-ios-mobile-provisioning-profile-policy"></a>如何创建 iOS 移动预配配置文件策略


1. 在“[Microsoft Intune 管理控制台](https://manage.microsoft.com)”中，选择“**策略**” > “**概述**” > “**添加策略**”。
2. 在“新建策略”对话框中，选择“iOS” > “移动预配配置文件策略”，然后选择“创建策略”。
3. 在“**常规**”页，配置下列值：
    - **命名** - 为该预配配置文件策略提供一个名称。
    - **说明** -（可选）提供策略的说明。
    - **配置文件** - 单击“导入”，然后选择从 Apple 开发人员网站下载的 Apple 移动配置文件（扩展名为 **.mobileprovision**）。
4. 完成后，选择“**保存策略**”。
5. 现在，将策略部署到所需的 iOS 设备。 有关详细信息，请参阅[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。
