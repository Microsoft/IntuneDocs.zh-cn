---
title: "应用预配配置文件 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：Intune 提供了一些工具，用于将新的预配配置文件主动分配到安装了即将到期应用的设备。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: fa3e0b481c31779261d5f6b23b729ca55331266b
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="use-ios-mobile-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>使用 iOS 移动预配配置文件防止应用过期

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="introduction"></a>简介

分配到 iPhone 和 iPad 的 Apple iOS 业务线应用附带已包含的预配配置文件和证书签名的代码。 应用运行时，iOS 将确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。 发生以下验证：

- **安装文件完整性** - iOS 将应用详细信息与企业签名证书的公钥进行比较。 如果它们不同，则应用内容可能已经更改，该应用不允许运行。
- **功能强制实施** - iOS 尝试从应用安装 (.ipa) 文件中的企业预配配置文件（而非各开发人员预配配置文件）强制实施应用功能。


用于签署应用的企业签名证书通常持续三年。 但是，预配配置文件在 1 年后过期。 使用 Intune 对拥有即将过期（但证书仍然有效）应用的设备主动分配新的预配配置文件。
证书过期后，必须使用新证书再次对应用进行签名，并使用新证书的密钥嵌入新的预配配置。


## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>如何创建 iOS 移动应用预配配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“移动应用”。
1.  在“移动应用”工作负荷中，选择“管理” > “iOS 预配配置文件”。
2.  在配置文件边栏选项卡列表中，选择“创建配置文件”。
3. 在“创建配置文件”边栏选项卡中，配置下列值：
    - **命名** - 为此移动预配配置文件提供一个名称。
    - **说明** -（可选）提供策略的说明。
    - **上载配置文件文件** - 选择“导入”，然后选择从 Apple 开发人员网站下载的 Apple 移动配置文件（扩展名为 **.mobileprovision**）。
4. 完成后，选择“创建”。

## <a name="next-steps"></a>后续步骤

将该配置文件分配给所需的 iOS 设备。 有关详细信息，请使用[如何分配设备配置文件](../configure-devices/how-to-assign-device-profiles.md)中的步骤。

