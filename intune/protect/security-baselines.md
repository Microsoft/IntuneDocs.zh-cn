---
title: 在 Microsoft Intune 中使用安全基线 - Azure | Microsoft Docs
description: 使用建议的 Windows 安全设置，以保护使用 Microsoft Intune 进行移动设备管理的设备上的用户和数据。 启用加密、配置 Microsoft Defender 高级威胁防护、控制 Internet Explorer、设置本地安全策略、要求输入密码、阻止 Internet 下载等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d447f2bf45d1bf3e6355a9d5dcc42b4bc2f3a9f3
ms.sourcegitcommit: 4bf23327af734a9811d555fbd566c31239e2acd6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "72999762"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>使用安全基线在 Intune 中配置 Windows 10 设备

使用 Intune 的安全基线来帮助保护用户和设备的安全。 安全基线是预配置的 Windows 设置组，可帮助应用已知设置组以及相关安全团队建议的默认值。 在 Intune 中创建安全基线配置文件时，将创建包含多个“设备配置”配置文件的模板  。

此功能适用于：

- Windows 10 版本 1809 及更高版本

在 Intune 中将安全基线部署到用户或设备组，并将设置应用于运行 Windows 10 或更高版本的设备。 例如，  MDM 安全基线自动为可移动驱动器启用 BitLocker、自动要求输入密码才能解锁设备、自动禁用基本身份验证等。 如果默认值不适用于你的环境，请自定义基线以应用所需的设置。

不同基线类型可能包含相同的设置，但对这些设置使用不同的默认值。 请务必了解你选择使用的基线默认值，然后修改每个基线以满足你的组织需求。

> [!NOTE]
> Microsoft 不建议在生产环境中使用安全基线的预览版本。 预览版基线中的设置可能会在预览过程中逐渐发生更改。

安全基线可以帮助你在使用 Microsoft 365 时拥有端到端安全工作流。 一些优势包括：

- 安全基线包括关于影响安全性的设置的最佳做法和建议。 Intune 与创建组策略安全基线的相同 Windows 安全团队合作。 这些建议是根据指导和广泛经验提出的。
- 如果是第一次使用 Intune，不确定从何处入手，那么使用安全基线会为自己带来优势。 可以快速创建和部署安全配置文件，同时确信自己这样做是在保护组织的资源和数据。
- 如果当前使用的是组策略，使用这些基线可以更轻松地迁移到 Intune 进行管理。 这些基线内置于 Intune 本机，提供新式管理体验。

若要详细了解此功能，最好参考 [Windows 安全基线](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)资源。 若要详细了解 MDM 以及可以在 Windows 设备上执行哪些操作，最好参考[移动设备管理](https://docs.microsoft.com/windows/client-management/mdm/) (MDM) 资源。

## <a name="about-baseline-versions-and-instances"></a>关于基线版本和实例

基线的每个新版本实例可以添加或删除设置或引入其他更改。 例如，当新版本的 Windows 10 中提供新 Windows 10 设置时，MDM 安全基线可能会收到包含最新设置的新版本实例。

在 Intune 控制台中，每个基线的磁贴显示基线模板名称，以及相应基线的基本信息。 此类信息包括，你有多少配置文件使用相应基线类型、有多少基线类型的单独实例（版本）可用，以及标识相应基线模板添加到租户的时间的“上次发布日期”  。 以下示例展示了频繁使用的 MDM 安全基线的磁贴：

![基线磁贴](./media/security-baselines/baseline-tile.png)

若要查看所使用的基线版本的详细信息，请选择基线磁贴以打开它的“概览”  窗格，再选择“版本”  。 此时，Intune 显示配置文件使用的基线版本的详细信息。 在“版本”窗格中，可以选择单个版本以进一步详细了解使用该版本的配置文件。 还可以选择两个不同的版本，然后选择“比较基线”  ，下载详细介绍其差异的 CSV 文件。

![比较基线](./media/security-baselines/compare-baselines.png)

创建安全基线配置文件  时，该配置文件将自动使用最新发布的安全基线实例。  可以继续使用和编辑之前创建的使用较低基线版本实例（包括使用预览版本创建的基线）的配置文件。

可以选择[更改给定配置文件使用的基线版本](#change-the-baseline-version-for-a-profile)。 这意味着当新版本推出时，无需创建新的基线配置文件即可充分利用它。 相反，当一切就绪后，可以选择基线配置文件，然后使用内置选项将相应配置文件的实例版本更改为新实例版本。

## <a name="available-security-baselines"></a>可用的安全基线

 可以同时在 Intune 环境中使用一个或多个可用基线。 还可以使用包含不同自定义项的相同安全基线的多个实例。

使用多个安全基线时，请审阅每个安全基线的设置，以确定不同的基线何时引入相同设置的冲突值。 由于可以部署用于不同意图的安全基线，并部署包含自定义设置的相同基线的多个实例，因此可能会为设备创建[必须调查并解决的配置冲突](security-baselines-monitor.md#troubleshoot-using-per-setting-status)。  另请注意[设备配置文件](../configuration/device-profiles.md)，这些配置文件可以配置多个与安全基线相同的设置。

以下安全基线实例可与 Intune 一起使用。 使用链接可以查看每个基线的最新实例的设置。

- **MDM 安全基线**
  - [2019 年 5 月 MDM 安全基线](security-baseline-settings-mdm-all.md?pivots=mdm-may-2019)
  - [预览版：2018 年 10 月的 MDM 安全基线](security-baseline-settings-mdm-all.md?pivots=mdm-preview)

- **Microsoft Defender ATP 基线**
   *（若要使用此基线，环境必须满足使用 [Microsoft Defender 高级威胁防护](advanced-threat-protection.md#prerequisites)的先决条件）* 。
  - [Microsoft Defender ATP 基线](security-baseline-settings-defender-atp.md)

  > [!NOTE]
  > Microsoft Defender ATP 安全基线已针对物理设备进行了优化，目前不建议在虚拟机 (VM) 或 VDI 终结点上使用。 某些基线设置可能会影响虚拟化环境中的远程交互式会话。  有关详细信息，请参阅 Windows 文档中的 [Increase compliance to the Microsoft Defender ATP security baseline](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline)（提高 Microsoft Defender ATP 安全基线的符合性）。

可以继续使用和编辑之前基于预览版模板创建的配置文件，无需考虑该预览模板是否可用于创建新配置文件。

## <a name="manage-baselines"></a>管理基线

使用安全基线时的常见任务包括：

- [创建配置文件](#create-the-profile) - 配置要使用的设置，然后将基线分配给组。
- [更改版本](#change-the-baseline-version-for-a-profile) - 更改配置文件使用的基线版本。
- [删除基线分配](#remove-a-security-baseline-assignment) - 了解停止使用安全基线来管理设置时会发生什么。


### <a name="prerequisites"></a>必备条件

- 要在 Intune 中管理基线，帐户必须具有内置的[策略和配置文件管理员](../fundamentals/role-based-access-control.md#built-in-roles)角色。

- 使用某些基线时，可能需要拥有对额外服务（如 Microsoft Defender ATP）的有效订阅。

### <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后选择“设备安全性”   >   “安全基线”以查看可用基线列表。

   ![选择要配置的安全基线](./media/security-baselines/available-baselines.png)

2. 依次选择要使用的基线和“创建配置文件”  。

3. 在“基本信息”  选项卡上，指定以下属性：

   - **名称**：输入安全基线配置文件的名称。 例如，输入“Defender ATP 的标准配置文件”  。

   - **说明**：输入一些文本来描述此基线的用途。 可以在“说明”中视需要输入任意文本。 此属性不是必填项，但建议填写。

   选择“下一步”  转到下一个选项卡。转到新选项卡后，选择选项卡名称可以返回到以前查看过的选项卡。

4. 在“配置”设置选项卡上，查看所选基线中可用的“设置”  组。 可以展开组以查看该组的设置，以及这些设置在基线中的默认值。 若要查找特定设置：
   - 选择一个组以展开并查看可用的设置。
   - 使用“搜索”  栏并指定用于筛选视图以仅显示包含搜索条件的组的关键字。

   基线中的每个设置都具有该基线版本的默认配置。 重新配置默认设置以满足你的业务需求。 不同的基线可能包含相同的设置，并对这些设置使用不同的默认值，具体取决于基线的目的。

   ![展开某个组以查看该组的设置](./media/security-baselines/sample-list-of-settings.png)

5. 在“作用域标记”  选项卡上，选择“选择作用域标记”  以打开“选择标记”  窗格，将作用域标记分配给配置文件。

6. 在“分配”  选项卡上，选择“选择要包括的组”  ，然后将基线分配给一个或多个组。 使用“选择要排除的组”  对分配进行相应调整。

   ![分配配置文件](./media/security-baselines/assignments.png)

7. 准备好部署基线后，请转到“查看 + 创建”  选项卡以查看基线的详细信息。 选择“创建”  以保存并部署配置文件。

   配置文件一经创建，便会推送到已分配的组，并可能会立即得以应用。

   > [!TIP]
   > 如果在保存配置文件之前，未先将配置文件分配给组，可以稍后编辑配置文件以执行此操作。

   ![查看基线](./media/security-baselines/review.png)

8. 创建配置文件后，通过转到“设备安全性”   >   “安全基线”对其进行编辑，选择已配置的基线类型，然后选择“配置文件”  。 从可用的配置文件列表中选择配置文件，然后选择“属性”  。 可以编辑所有可用的配置选项卡中的设置，并选择“查看 + 保存”  以提交所做的更改。

### <a name="change-the-baseline-version-for-a-profile"></a>更改配置文件的基线版本

可以更改配置文件使用的基线实例版本。  更改版本时，选择相同基线的可用实例。 无法在两种不同的基线类型之间进行更改，如将配置文件从使用 Defender ATP 基线更改为使用 MDM 安全基线。

配置基线版本更改时，可以下载 CSV 文件，其中列出了所涉及的两个基线版本之间的更改。 还可以选择保留原始基线版本的所有自定义项，或使用所有默认值来实现新版本。 更改配置文件的基线版本时，无法选择对各个设置进行更改。

经过保存并且在转换完成后，基线将立即重新部署到已分配的组。

**转换期间**：

- 添加你使用的原始版本中未包含的新设置，并将其设置为使用默认值。

- 你选择的新基线版本中未包含的设置将被删除，并且此安全基线配置文件不再强制执行该设置。

  如果某个设置不再由基线配置文件管理，那么该设置不会在设备上重置。 相反，设备上的设置仍设置为其最近一次的配置，直到某个其他进程管理这些设置并对其进行更改。 在停止管理某个设置后可以更改该设置的进程示例包括不同的基线配置文件、组策略设置或在设备上进行的手动配置。

#### <a name="to-change-the-baseline-version-for-a-profile"></a>更改配置文件的基线版本的具体步骤

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，选择“设备安全性”   >   “安全基线”，然后选择具有要更改的配置文件的基线类型的磁贴。

2. 接下来，选择“配置文件”  ，然后选中要编辑的配置文件对应的复选框，选择“更改版本”  。

   ![选择基线](./media/security-baselines/select-baseline.png)

3. 在“更改版本”  窗格中，使用“选择要更新到的安全基线”  下拉列表，然后选择要使用的版本实例。

   ![选择版本](./media/security-baselines/select-instance.png)

4. 选择“查看更新”  ，下载显示配置文件当前实例版本与所选新版本之间的差异的 CSV 文件。 审阅此文件，以了解哪些设置是新的或已删除的，以及这些设置在更新后的配置文件中的默认值是什么。

   准备就绪后，继续执行下一步骤。

5. 为“选择更新配置文件的方法”  选择两个选项之一：
   - **接受基线更改但保留我现有的设置自定义项** - 此选项保留对基线配置文件所设置的自定义项，并将其应用于你选择使用的新版本。
   - **接受基线更改并放弃现有设置自定义项** - 此选项将完全覆盖原始配置文件。 更新的配置文件将对所有设置使用默认值。

6. 选择“提交”  。 配置文件更新到所选的基线版本，转换完成后，基线将立即重新部署到已分配的组。

### <a name="remove-a-security-baseline-assignment"></a>删除安全基线分配

当安全基线设置不再适用于设备，或基线中的设置设为“未配置”  时，设备上的这些设置不会恢复为管理前的配置。 相反，设备上之前管理的设置仍保留其从基线收到的最近一次配置，直到某个其他进程更新设备上的这些设置。

可在稍后更改设备设置的其他进程包括其他或新的安全基线、设备配置文件、组策略配置或设备设置的手动编辑。

## <a name="co-managed-devices"></a>共同管理的设备

Intune 托管设备上的安全基线类似于使用 Configuration Manager 的共同管理设备。 共同管理设备同时使用 System Center Configuration Manager 和 Microsoft Intune 来管理 Windows 10 设备。 这样一来，可以通过云附加现有 Configuration Manager 投资，以充分发挥 Intune 的优势。 如果使用的是 Configuration Manager，且希望获取云优势，最好参考[共同管理概述](https://docs.microsoft.com/sccm/comanage/overview)资源。

使用共同管理设备时，必须将“设备配置”  工作负载（其设置）切换为“Intune”。 有关详细信息，请参阅[设备配置工作负载](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration)。

## <a name="q--a"></a>问与答

### <a name="why-these-settings"></a>为什么要使用这些设置？

Microsoft 安全团队多年来一直与 Windows 开发人员以及安全社区直接合作，共同创建这些建议，经验丰富。 此基线中的设置被视为最相关的安全相关配置选项。 在 Windows 的每个新内部版本中，团队都会根据新发布的功能调整自己的建议。

### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>面向组策略和 Intune 的 Windows 安全基线建议是否有区别Intune？

为每个基线选择并整理设置的 Microsoft 安全团队不变。 Intune 包含 Intune 安全基线中的所有相关设置。 组策略基线中有一些本地域控制器专用设置。 这些设置被排除在 Intune 建议范围之外。 其他所有设置都是相同的。

### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Intune 安全基线是否符合 CIS 或 NSIT？

严格来讲不符合。 Microsoft 安全团队咨询 CIS 等组织来汇编建议。 不过，“符合 CIS”和 Microsoft 基线不存在一对一映射关系。

### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Microsoft 安全基线有哪些认证？ 

- Microsoft 多年来一直在发布面向组策略 (GPO) 和[安全性符合性工具包](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10)的安全基线。 许多组织都使用这些基线。 这些基线中的建议是 Microsoft 安全团队与企业客户及外部机构交流得出，包括美国国防部 (DoD)、美国国家标准技术研究所 (NIST) 等。 我们与这些组织共享建议和基线。 这些组织也有他们自己的建议，这些建议与 Microsoft 的建议非常相似。 随着移动设备管理 (MDM) 继续向云发展，Microsoft 为这些组策略基线创建了等效的 MDM 建议。 这些附加基线内置于 Microsoft Intune，其中包括关于遵循（或不遵循）基线的用户、组和设备的符合性报告。

- 许多客户使用 Intune 基线建议作为起点，再进行自定义，从而满足自己的 IT 和安全需求。 Microsoft 发布的第一个基线是 Windows 10 RS5 MDM 安全基线  。 此基线是作为通用基础结构构建，可便于客户最终导入基于 CIS、NIST 和其他标准的其他安全基线。 目前，它适用于 Windows，最终将适用于 iOS 和 Android。

- 使用 Azure Active Directory (AD) 和 Microsoft Intune 从本地 Active Directory 组策略迁移到纯云解决方案是一个过程。 若要获取帮助，可以使用[安全性和符合性工具包](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10)中包含的组策略模板，帮助管理加入了混合 AD 和 Azure AD 的设备。 这些设备可以从云 (Intune) 中获取 MDM 设置，并根据需要从本地域控制器获取组策略设置。

## <a name="next-steps"></a>后续步骤

- 查看可用基线的最新版本中的设置：
  - [MDM 安全基线](security-baseline-settings-mdm-all.md)
  - [Microsoft Defender ATP 基线](security-baseline-settings-defender-atp.md)

- 检查状态并监视[基线和配置文件](security-baselines-monitor.md)
