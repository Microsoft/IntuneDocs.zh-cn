---
title: Microsoft Intune 中的 iOS 应用预配配置文件
titlesuffix: ''
description: Intune 提供了一些工具，用于将新的预配配置文件主动分配到安装了即将到期应用的设备。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8fdfa89654df1f62979240f364c2e28b5a15e78f
ms.sourcegitcommit: d047a692c798e1fb61ee43a487d6332bce344610
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44058908"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>使用 iOS 应用预配配置文件防止应用过期

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>简介

分配到 iPhone 和 iPad 的 Apple iOS 业务线应用使用附带的预配配置文件和证书签名的代码构建。 应用运行时，iOS 将确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。 发生以下验证：

- **安装文件完整性** - iOS 将应用详细信息与企业签名证书的公钥进行比较。 如果它们不同，则应用内容可能已发生更改，并且不允许运行该应用。
- **功能强制实施** - iOS 尝试从应用安装 (.ipa) 文件中的企业预配配置文件（而非各开发人员预配配置文件）强制实施应用功能。


用于签署应用的企业签名证书通常持续三年。 但是，预配配置文件在 1 年后过期。 使用 Intune 对拥有即将过期（但证书仍然有效）应用的设备主动分配新的预配配置文件。
证书过期后，必须使用新证书再次对应用进行签名，并使用新证书的密钥嵌入新的预配配置。

管理员可以将某些安全组包含在分配 iOS 应用预配配置的范围内，或将其排除在外。 例如，可以将 iOS 应用预配配置分配给“所有用户”，但将高级管理人员组排除在外。

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>如何创建 iOS 移动应用预配配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“客户端应用”。
1.  在“客户端应用”工作负载中，选择“管理” > “iOS 应用预配配置文件”。
2.  在配置文件窗格列表中，选择“创建配置文件”。
3. 在“创建配置文件”窗格中，配置下列值：
    - **命名** - 为此移动预配配置文件提供一个名称。
    - **说明** -（可选）提供策略的说明。
    - **上载配置文件文件** - 选择“导入”，然后选择从 Apple 开发人员网站下载的 Apple 移动配置文件（扩展名为 **.mobileprovision**）。
4. 完成后，选择“创建”。

## <a name="next-steps"></a>后续步骤

将该配置文件分配给所需的 iOS 设备。 有关详细信息，请使用[如何分配设备配置文件](device-profile-assign.md)中的步骤。
