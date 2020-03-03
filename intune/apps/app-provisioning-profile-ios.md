---
title: Microsoft Intune 中的 iOS/iPadOS 应用预置描述文件
titleSuffix: ''
description: Intune 提供了一些工具，用于将新的预配配置文件主动分配到安装了即将到期应用的设备。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f40b6f458a95a466874a2d1ce44fcafa37249d46
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513616"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>使用 iOS 应用预配配置文件防止应用过期

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>简介

分配到 iPhone 和 iPad 的 Apple iOS/iPadOS 业务线应用使用附带的预置描述文件和证书签名的代码进行构建。 应用运行时，iOS/iPadOS 将确认 iOS/iPadOS 应用的完整性，并强制实施由预置描述文件定义的策略。 发生以下验证：

- **安装文件完整性** - iOS/iPadOS 将应用详细信息与企业签名证书的公钥进行比较。 如果它们不同，则应用内容可能已发生更改，并且不允许运行该应用。
- **功能强制实施** - iOS/iPadOS 尝试从应用安装 (.ipa) 文件中的企业预置描述文件（而非各开发人员预置描述文件）强制实施应用功能。


用于签署应用的企业签名证书通常持续三年。 但是，预配配置文件在 1 年后过期。 使用 Intune 对拥有即将过期（但证书仍然有效）应用的设备主动分配新的预配配置文件。
证书过期后，必须使用新证书再次对应用进行签名，并使用新证书的密钥嵌入新的预配配置。

管理员可以将某些安全组包含在分配 iOS/iPadOS 应用预配配置的范围内，或将其排除在外。 例如，可以将 iOS/iPadOS 应用预配配置分配给“所有用户”，但将高级管理人员组排除在外。

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>如何创建 iOS 移动应用预配配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用” > “iOS 应用预配配置文件” > “创建配置文件”    。
3. 在“基本信息”页上，添加以下值  ：
    - **命名** - 为此移动预配配置文件提供一个名称。
    - **说明** -（可选）提供策略的说明。
    - **上传配置文件的文件** - 选择“打开”  图标，然后选择从 [Apple 开发者网站](https://developer.apple.com/)下载的 Apple 移动配置文件（扩展名为 `.mobileprovision`）。

   将用你在上面添加的 Apple 移动配置文件中的值填充“过期日期”  。<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. 单击“**下一步:** 作用域标记”。<br>
   在“作用域标记”页上，你可以选择配置作用域标记，以确定谁可以在 Intune 中查看 iOS/iPadOS 应用预置描述文件  。 若要详细了解作用域标记，请参阅[将基于角色的访问控制和作用域标记用于分布式 IT](../fundamentals/scope-tags.md)。
5. 单击“**下一步:** 分配”。<br>
   通过“分配”页面，可以将配置文件分配到用户和设备  。 值得注意的是，无论设备是否由 Intune 管理，都可以将配置文件分配到设备。
6. 单击“**下一步:查看 + 创建**”以查看你为配置文件输入的值。
7. 完成后，单击“创建”以在 Intune 中创建 iOS/iPadOS 应用预置描述文件  。 

## <a name="next-steps"></a>后续步骤

将该配置文件分配给所需的 iOS/iPadOS 设备。 有关详细信息，请使用[如何分配设备配置文件](../device-profile-assign.md)中的步骤。
