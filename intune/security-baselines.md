---
title: 在 Microsoft Intune 中使用安全基线 - Azure | Microsoft Docs
description: 添加或配置建议的组安全设置，以保护使用 Microsoft Intune 进行移动设备管理的设备上的用户和数据。 启用 bitlocker、配置 Windows Defender 高级威胁防护、控制 Internet Explorer、使用智能屏幕、设置本地安全策略、要求输入密码、阻止 Internet 下载等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b2a5e2bbd6d06cc4ec0cf71ee815229b01040a8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61490638"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>在 Intune 中创建 Windows 10 安全基线

安全基线是一项预览版功能，适用于运行 Windows 10 或更高版本的设备。 此功能包括 Intune 支持的多个设置，你可以使用这些设置来保护用户和设备。 它还将这些设置自动设置为安全团队建议的值。 例如，基线自动启用 BitLocker、自动要求必须输入密码才能解锁设备、自动禁用基本身份验证等。

此功能适用于：

- Windows 10 版本 1809 及更高版本

> [!NOTE]
> 虽然安全基线处于预览阶段，但 Microsoft 并不建议在生产环境中使用配置文件，因为基线可能会在预览过程中发生变化。 正式发布安全基线时，现有的配置文件将不会转换为最新的受支持的配置文件。

使用安全基线的目标是，在用户使用 Microsoft 365 时，提供端到端安全工作流。 一些优势包括：

- 安全基线包括关于影响安全性的设置的最佳做法和建议。 Intune 与创建组策略安全基线的相同 Windows 安全团队合作。 这些建议是根据指导和广泛经验提出的。
- 如果是第一次使用 Intune，不确定从何处入手，那么使用安全基线会为自己带来优势。 可以快速创建和部署安全配置文件，同时确信自己这样做是在保护组织的资源和数据。
- 如果当前使用的是组策略，使用这些基线可以更轻松地迁移到 Intune 进行管理。 这些基线内置于 Intune 本机，提供新式管理体验。

安全基线在 Intune 中创建“配置文件”。 此配置文件包括基线中的所有设置。 然后，可以将此配置文件应用或分配到用户、组和设备。

分配此配置文件后，可以监视配置文件和基线。 例如，可以查看哪些设备与基线匹配或不匹配。

本文展示了如何使用安全基线来创建、分配和监视配置文件。

若要详细了解此功能，最好参考 [Windows 安全基线](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)资源。 若要详细了解 MDM 以及可以在 Windows 设备上执行哪些操作，最好参考[移动设备管理](https://docs.microsoft.com/windows/client-management/mdm/) (MDM) 资源。

## <a name="prerequisites"></a>必备条件
要在 Intune 中管理基线，帐户必须具有内置的[策略和配置文件管理员](role-based-access-control.md#built-in-roles)角色。


## <a name="co-managed-devices"></a>共同管理的设备

Intune 托管设备上的安全基线类似于使用 Configuration Manager 的共同管理设备。 共同管理设备同时使用 System Center Configuration Manager 和 Microsoft Intune 来管理 Windows 10 设备。 这样一来，可以通过云附加现有 Configuration Manager 投资，以充分发挥 Intune 的优势。 如果使用的是 Configuration Manager，且希望获取云优势，最好参考[共同管理概述](https://docs.microsoft.com/sccm/comanage/overview)资源。

使用共同管理设备时，必须将“设备配置”工作负载（其设置）切换为“Intune”。 有关详细信息，请参阅[设备配置工作负载](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration)。

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com/)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“安全基线(预览版)”。 此时，系统列出了可用基线。 添加更多基线后，如下图所示：

    ![查看 Intune 中当前可用的安全基线列表](./media/security-baselines/available-baselines.png)

3. 依次选择要使用的基线和“创建配置文件”。
4. 在“基本信息”中，输入以下属性：

    - **名称**：输入安全基线配置文件的名称。 例如，输入 `pilot Windows 10 MDM baseline - Oct 2018`。
    - **说明**：输入一些文本来描述此基线的用途。 可以在“说明”中视需要输入任意文本。 虽是可选属性，但强烈建议输入说明。

5. 展开“设置”。 在列表中，可以看到此安全基线中的所有设置，以及这些设置的自动设置值。 这些设置及其值都是建议的，可自行更改。

    ![展开“设置”查看此安全基线在 Intune 中的所有设置](./media/security-baselines/sample-list-of-settings.png)

    展开一些设置可以查看它们的值。 例如，展开“Windows Defender”。 请注意一些设置及其设置值：

    ![查看部分“Windows Defender”设置在 Intune 中的自动设置值](./media/security-baselines/expand-windows-defender.png)

6. 创建配置文件。 
7. 选择“配置文件”。 此时，配置文件创建完成，并出现在列表中。 不过，它尚未执行任何操作。 下一步是分配配置文件。

## <a name="assign-the-profile"></a>分配配置文件

创建完成的配置文件可供分配到用户、设备和组。 分配完成后，配置文件及其设置便会应用于选定用户、设备和组。

1. 在 Intune 中，依次选择“安全基线”、基线和“配置文件”。
2. 依次选择配置文件和“分配”。

    ![选择 Intune 中的安全基线配置文件，并单击“分配”来部署配置文件](./media/security-baselines/assignments.png)

3. 在“包括”选项卡中，添加要将此策略应用到的组、用户或设备。

    > [!TIP]
    > 请注意，还可以排除组。 如果向“所有用户”应用策略，建议排除管理员组。 万一发生什么事情，你和你的管理员不希望无计可施。

4. 单击“保存”以保存更改。

只要保存，配置文件就会推送到通过 Intune 签入的设备。 所以这可能会立即发生。

## <a name="available-security-baselines"></a>可用的安全基线  

以下安全基线可与 Intune 一起使用。
- **预览版：MDM 安全基线**
  - 版本：[2018 年 10 月](security-baseline-settings-windows.md)

## <a name="q--a"></a>问与答

#### <a name="why-these-settings"></a>为什么要使用这些设置？

Microsoft 安全团队多年来一直与 Windows 开发人员以及安全社区直接合作，共同创建这些建议，经验丰富。 此基线中的设置被视为最相关的安全相关配置选项。 在 Windows 的每个新内部版本中，团队都会根据新发布的功能调整自己的建议。

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>面向组策略和 Intune 的 Windows 安全基线建议是否有区别Intune？

为每个基线选择并整理设置的 Microsoft 安全团队不变。 Intune 包含 Intune 安全基线中的所有相关设置。 组策略基线中有一些本地域控制器专用设置。 这些设置被排除在 Intune 建议范围之外。 其他所有设置都是相同的。

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Intune 安全基线是否符合 CIS 或 NSIT？

严格来讲不符合。 Microsoft 安全团队咨询 CIS 等组织来汇编建议。 不过，“符合 CIS”和 Microsoft 基线不存在一对一映射关系。

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Microsoft 安全基线有哪些认证？ 

- Microsoft 多年来一直在发布面向组策略 (GPO) 和[安全性符合性工具包](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10)的安全基线。 许多组织都使用这些基线。 这些基线中的建议是 Microsoft 安全团队与企业客户及外部机构交流得出，包括美国国防部 (DoD)、美国国家标准技术研究所 (NIST) 等。 我们与这些组织共享建议和基线。 这些组织也有他们自己的建议，这些建议与 Microsoft 的建议非常相似。 随着移动设备管理 (MDM) 继续向云发展，Microsoft 为这些组策略基线创建了等效的 MDM 建议。 这些附加基线内置于 Microsoft Intune，其中包括关于遵循（或不遵循）基线的用户、组和设备的符合性报告。

- 许多客户使用 Intune 基线建议作为起点，再进行自定义，从而满足自己的 IT 和安全需求。 Microsoft 发布的第一个基线是 Windows 10 RS5 MDM 安全基线。 此基线是作为通用基础结构构建，可便于客户最终导入基于 CIS、NIST 和其他标准的其他安全基线。 目前，它适用于 Windows，最终将适用于 iOS 和 Android。

- 使用 Azure Active Directory (AD) 和 Microsoft Intune 从本地 Active Directory 组策略迁移到纯云解决方案是一个过程。 为了提供帮助，我们还针对混合 AD 和 Azure AD 加入设备发布了配套 GPO。 这些设备可以从云 (Intune) 中获取 MDM 设置，并根据需要从本地域控制器获取组策略设置。

## <a name="next-steps"></a>后续步骤
- 请查看 Intune 支持的 [Windows 安全基线设置](security-baseline-settings-windows.md)。  
- 检查状态并监视[基线和配置文件](security-baselines-monitor.md)。
