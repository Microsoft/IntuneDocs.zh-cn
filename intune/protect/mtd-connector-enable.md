---
title: 在 Microsoft Intune 中启用移动威胁防御连接器
titleSuffix: Microsoft Intune
description: 在移动威胁防御 (MTD) 合作伙伴和 Microsoft Intune 之间启用连接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8243ae4014660a76c6327afd9c970ce8a9eae58
ms.sourcegitcommit: 960ffb2214c35d75ad219fa2571a999529a0abd4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/25/2019
ms.locfileid: "74478840"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>在 Intune 中启用移动威胁防御连接器

在移动威胁防御 (MTD) 安装过程中，已配置了用于在移动威胁防御合作伙伴控制台中对威胁进行分类的策略，并且已在 Intune 中创建了设备合规性策略。 如果已在 MTD 合作伙伴控制台中配置了 Intune 连接器，则现在可为 MTD 合作伙伴应用程序启用 MTD 连接。

> [!NOTE]
> 本主题适用于所有移动威胁防御合作伙伴。

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>MTD 应用的经典条件访问策略

如果你将新应用集成到 Intune Mobile Threat Defense，并启用与 Intune 的连接，Intune 会在 Azure Active Directory 中创建经典条件访问策略。 集成的每个 MTD 应用（包括 [Defender ATP](advanced-threat-protection.md) 或其他任何 [MTD 合作伙伴](mobile-threat-defense.md#mobile-threat-defense-partners)）都会新建经典条件访问策略。 可以忽略这些策略，但不能对其进行编辑、删除或禁用。

如果删除了经典策略，你将需要删除负责创建它的 Intune 的连接，然后重新设置。 此过程将重新创建经典策略。 不支持将 MTD 应用的经典策略迁移到新的条件访问策略类型。

MTD 应用的经典条件访问策略：

- 供 Intune MTD 使用，以要求在 Azure AD 中注册设备，这样它们就在与 MTD 合作伙伴通信前有设备 ID 了。 此 ID 是必需的，以便设备可以成功向 Intune 报告其状态。

- 不会影响其他任何云应用或资源。

- 此策略与可能创建的用于帮助管理 MTD 的条件访问策略不同。

- 默认情况下，该策略与用于评估的其他条件访问策略不交互。

要查看经典条件访问策略，请转到 [Azure](https://portal.azure.com/#home) 中的“Azure Active Directory” > “条件访问” > “经典策略”    。

## <a name="to-enable-the-mobile-threat-defense-connector"></a>启用移动威胁防御连接器

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“租户管理”   > “连接器和令牌”   > “移动威胁防御”  。

3. 在“移动威胁防御”  窗格上，选择“添加”  。

4. 对于“要设置的移动威胁防御连接器”  从下拉列表中选择 MTD 解决方案。

5. 根据你组织的要求启用切换选项。 可见的切换选项因 MTD 合作伙伴而异。  例如，下图显示了适用于 Symantec Endpoint Protection 的选项：

   ![Intune Azure 门户中的 MTD 设置](./media/mtd-connector-enable/enable-mtd-connector-1.png)

## <a name="mobile-threat-defense-toggle-options"></a>移动威胁防御切换选项

根据组织要求，可以决定需要启用哪些 MTD 切换选项。 移动威胁防御合作伙伴并非支持以下所有选项：

**MDM 符合性策略设置**

- **将 Android 设备版本 _\<支持的版本>_ 连接到 _\<MTD 合作伙伴名称>_** ：如果启用此选项，可以让 Android 4.1 + 设备将安全风险报回 Intune。

- **将 iOS 设备版本 _\<支持的版本>_ 连接到 _\<MTD 合伙伙伴名称>_** ：启用此选项后，可让 iOS 8.0+ 设备向 Intune 报告安全风险。

- **为 iOS 设备启用应用同步**：允许此 Mobile Threat Defense 合作伙伴请求 Intune 中的 iOS 应用程序的元数据，以用于威胁分析。

- **阻止不受支持的操作系统版本**：如果设备运行的操作系统版本低于支持的最低版本，则阻止该版本。

**应用保护策略设置**

- **将 Android 设备版本 \<支持的版本>  连接到 \<MTD 合作伙伴名称>  以进行应用保护策略评估**：启用此选项时，使用设备威胁级别规则的应用保护策略将评估包括来自此连接器的数据的设备。

- **将 iOS 设备版本 \<支持的版本>  连接到 \<MTD 合作伙伴名称>  以进行应用保护策略评估**：启用此选项时，使用设备威胁级别规则的应用保护策略将评估包括来自此连接器的数据的设备。

若要了解有关使用移动威胁防御连接器进行 Intune 应用保护策略评估的详细信息，请参阅[为未注册的设备设置移动威胁防御](~/protect/mtd-enable-unenrolled-devices.md)。

**常见的共享设置**

- **合作伙伴无响应之前的天数**：在 Intune 由于连接断开将合作伙伴视为无响应之前的天数。 Intune 将忽略无响应 MTD 合作伙伴的符合性状态。

> [!IMPORTANT]
> 如有可能，我们建议在创建设备符合性和条件访问策略规则之前，先添加和分配 MTD 应用。 这样有助于确保最终用户能够安装 MTD 应用，以便访问电子邮件或其他公司资源。

> [!TIP]
> 可以从“移动威胁防御”窗格中查看 Intune 和 MTD 合作伙伴之间的“连接状态”和“上次同步”时间   。

## <a name="next-steps"></a>后续步骤

- [使用 Intune 创建移动威胁防御 (MTD) 应用保护策略](~/protect/mtd-app-protection-policy.md)。
