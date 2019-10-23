---
title: 在 Microsoft Intune 中启用移动威胁防御连接器
titleSuffix: Microsoft Intune
description: 在移动威胁防御 (MTD) 合作伙伴和 Microsoft Intune 之间启用连接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
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
ms.openlocfilehash: e53f50c42e768eeb652a8602bea49c04d29364c7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504423"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>在 Intune 中启用移动威胁防御连接器

> [!NOTE] 
> 本主题适用于所有移动威胁防御合作伙伴。

在移动威胁防御 (MTD) 安装过程中，已配置了用于在 MTD 合作伙伴控制台中对威胁进行分类的策略，并且已在 Intune 中创建了设备符合性策略。 如果已在 MTD 合作伙伴控制台中配置了 Intune 连接器，则现在可为 MTD 合作伙伴应用程序启用 MTD 连接。

如果你将新应用集成到 Intune Mobile Threat Defense，并启用与 Intune 的连接，Intune 会在 Azure Active Directory 中创建经典条件访问策略。 集成的每个 MTD 应用（包括 [Defender ATP](advanced-threat-protection.md) 或其他任何 [MTD 合作伙伴](mobile-threat-defense.md#mobile-threat-defense-partners)）都会新建经典条件访问策略。 可以忽略这些策略，但不能对其进行编辑、删除或禁用。

MTD 应用的经典条件访问策略： 

- 供 Intune MTD 使用，以要求在 Azure AD 中注册设备，这样它们就在与 MTD 合作伙伴通信前有设备 ID 了。 此 ID 是必需的，以便设备可以成功向 Intune 报告其状态。  
- 不会影响其他任何云应用或资源。  
- 此策略与可能创建的用于帮助管理 MTD 的条件访问策略不同。
- 默认情况下，该策略与用于评估的其他条件访问策略不交互。  

要查看经典条件访问策略，请转到 [Azure](https://portal.azure.com/#home) 中的“Azure Active Directory” > “条件访问” > “经典策略”    。


## <a name="to-enable-the-mtd-connector"></a>启用 MTD 连接器

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。

4. 在“Intune 仪表板”  中，选择“设备符合性”  ，然后选择“设置”  部分下的“移动威胁防御”  。

5. 在“移动威胁防御”窗格上，选择“添加”   。

6. 从下拉列表中选择 MTD 解决方案作为“要设置的移动威胁防御连接器”  。

    ![Intune Azure 门户中的 MTD 设置](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. 根据你组织的要求启用切换选项。 可见的切换选项因 MTD 合作伙伴而异。

## <a name="mtd-toggle-options"></a>MTD 切换选项

可以根据组织要求决定需要启用哪些 MTD 切换选项。 下面是更多详细信息：

- **将 Android 4.1+ 设备连接到 [MTD 合作伙伴名称] for Work MTD**：如果启用此选项，可以让 Android 4.1 + 设备将安全风险报回 Intune。
  - **如果未收到任何数据则标记为不符合**：如果 Intune 未从 MTD 合作伙伴收到有关此平台上的设备的数据，则将设备视为不符合。
<br></br>
- **将 iOS 8.0+ 设备连接到 [MTD 合作伙伴名称] for Work MTD**：启用此选项后，可让 iOS 8.0+ 设备向 Intune 报告安全风险。
  - **如果未收到任何数据则标记为不符合**：如果 Intune 未从 MTD 合作伙伴收到有关此平台上的设备的数据，则将设备视为不符合。
<br></br>
- **为 iOS 设备启用应用同步**：允许此 Mobile Threat Defense 合作伙伴请求 Intune 中的 iOS 应用程序的元数据，以用于威胁分析。

- **阻止不受支持的操作系统版本**：如果设备运行的操作系统版本低于支持的最低版本，则阻止该版本。

- **合作伙伴无响应之前的天数**：在 Intune 由于连接断开将合作伙伴视为无响应之前的天数。 Intune 将忽略无响应 MTD 合作伙伴的符合性状态。

> [!IMPORTANT] 
> 如有可能，我们建议在创建设备符合性和条件访问策略规则之前，先添加和分配 MTD 应用。 这样有助于确保最终用户能够安装 MTD 应用，以便访问电子邮件或其他公司资源。

> [!TIP]
> 可以从“移动威胁防御”窗格中查看 Intune 和 MTD 合作伙伴之间的“连接状态”和“上次同步”时间   。
