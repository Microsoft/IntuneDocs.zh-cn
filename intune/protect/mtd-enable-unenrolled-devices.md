---
title: 为未注册的设备启用移动威胁防御连接器
titleSuffix: Microsoft Intune
description: 在 Microsoft Intune 中未注册的设备启用移动威胁防御连接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25d7c357c0ea313891f80433f33cd4ac57cfad2c
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782091"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>在 Intune 中为未注册的设备启用移动威胁防御连接器

在移动威胁防御 (MTD) 安装过程中，已配置了用于在移动威胁防御合作伙伴控制台中对威胁进行分类的策略，并且已在 Intune 中创建了应用保护策略。 如果已在 MTD 合作伙伴控制台中配置了 Intune 连接器，则现在可为 MTD 合作伙伴应用程序启用 MTD 连接。

> [!NOTE]
> 本文适用于支持应用保护策略的所有移动威胁防御合作伙伴：
>
> - Better Mobile（Android、iOS/iPadOS）
> - Zimperium（Android、iOS/iPadOS）
> - Lookout for Work（Android、iOS/iPadOS）

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>MTD 应用的经典条件访问策略

如果你将新应用集成到 Intune Mobile Threat Defense，并启用与 Intune 的连接，Intune 会在 Azure Active Directory 中创建经典条件访问策略。 集成的每个 MTD 应用（包括 [Defender ATP](advanced-threat-protection.md) 或其他任何 [MTD 合作伙伴](mobile-threat-defense.md#mobile-threat-defense-partners)）都会新建经典条件访问策略。 可以忽略这些策略，但不能对其进行编辑、删除或禁用。

如果删除了经典策略，你将需要删除负责创建它的 Intune 的连接，然后重新设置。 此过程将重新创建经典策略。 不支持将 MTD 应用的经典策略迁移到新的条件访问策略类型。

MTD 应用的经典条件访问策略：

- 供 Intune MTD 使用，以要求在 Azure AD 中注册设备，这样它们就在与 MTD 合作伙伴通信前有设备 ID 了。 此 ID 是必需的，以便设备可以成功向 Intune 报告其状态。

- 不会影响其他任何云应用或资源。

- 此策略与可能创建的用于帮助管理 MTD 的条件访问策略不同。

- 默认情况下，该策略与用于评估的其他条件访问策略不交互。

要查看经典条件访问策略，请转到 [Azure](https://portal.azure.com/#home) 中的“Azure Active Directory” > “条件访问” > “经典策略”    。

## <a name="to-enable-the-mtd-connector"></a>启用 MTD 连接器

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“租户管理”   > “连接器和令牌”   > “移动威胁防御”  。

3. 在“移动威胁防御”窗格上选择“添加”   。

4. 从下拉列表中选择 MTD 解决方案作为“要设置的移动威胁防御连接器”  。

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. 根据你组织的要求启用切换选项。 可见的切换选项因 MTD 合作伙伴而异。

## <a name="mobile-threat-defense-toggle-options"></a>移动威胁防御切换选项

可以根据组织要求决定需要启用哪些 MTD 切换选项。 下面是更多详细信息：

**应用保护策略设置**

- **将版本 4.4 及更高版本的 Android 设备连接到 *\<MTD 合作伙伴名称>* 以进行应用保护策略评估**：启用此选项时，使用设备威胁级别规则的应用保护策略将评估包括来自此连接器的数据的设备。

- **将 iOS 11 及更高版本设备连接到 *\<MTD 合作伙伴名称>* 以进行应用保护策略评估**：启用此选项时，使用设备威胁级别规则的应用保护策略将评估包括来自此连接器的数据的设备。

**常见的共享设置**

- **合作伙伴无响应之前的天数**：在 Intune 由于连接断开将合作伙伴视为无响应之前的天数。 Intune 将忽略无响应 MTD 合作伙伴的符合性状态。

> [!TIP]
> 可以从“移动威胁防御”窗格中查看 Intune 和 MTD 合作伙伴之间的“连接状态”和“上次同步”时间   。

## <a name="next-steps"></a>后续步骤

- [使用 Intune 创建移动威胁防御 (MTD) 应用保护策略](~/protect/mtd-app-protection-policy.md)。
