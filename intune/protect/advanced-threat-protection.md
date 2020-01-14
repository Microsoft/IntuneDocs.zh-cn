---
title: 在 Microsoft Intune 中使用 Microsoft Defender ATP - Azure | Microsoft Docs
description: 将 Microsoft Defender 高级威胁防护 (Microsoft Defender ATP) 与 Intune 一起使用（包括设置和配置、载入带 ATP 的 Intune 设备），然后将设备 ATP 风险评估与 Intune 设备合规性和条件访问策略结合使用来保护网络资源。
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
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2fa80697f24167e2a9634bd506e9548ca654129f
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547087"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>使用 Intune 中的条件访问强制执行 Microsoft Defender ATP 的符合性

可以将 Microsoft Defender 高级威胁防护 (Microsoft Defender ATP) 和 Microsoft Intune 集成为 Mobile Threat Defense 解决方案。 集成可让你免受安全漏洞的威胁，并帮助限制组织中的漏洞影响。 Microsoft Defender ATP 适用于运行 Windows 10 或更高版本的设备。

要成功，请配合使用以下配置：

- **在 Intune 和 Microsoft Defender ATP 之间创建一个服务到服务的连接**。 通过这个连接，Microsoft Defender ATP 可以从使用 Intune 管理的 Windows 10 设备收集有关计算机风险的数据。
- **使用设备配置配置文件将设备载入 Microsoft Defender ATP**。 载入设备将其配置为与 Microsoft Defender ATP 进行通信，并提供有助于评估其风险级别的数据。
- **使用设备合规性策略设置要允许的风险级别**。 由 Microsoft Defender ATP 报告风险等级。 将超出允许风险级别的设备识别为不合规。
-  使用条件访问策略阻止用户从不合规的设备访问公司资源。

将 Intune 与 Microsoft Defender ATP 集成时，可以充分利用 ATP 威胁和漏洞管理 (TVM) 并[使用 Intune 修正由 TVM 标识的终结点漏洞](atp-manage-vulnerabilities.md)。

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>将 Microsoft Defender ATP 和 Intune 结合使用的示例

下面的示例有助于解释这些解决方案如何协同工作以帮助保组织。 在此示例中，Microsoft Defender ATP 和 Intune 已经集成在一起了。

有人向组织内的用户发送包含嵌入式恶意代码的 Word 附件。

- 在用户打开附件时，将启用内容。
- 提升的权限攻击随即启动，且来自远程计算机的攻击者对受害者的设备具有管理权限。
- 然后，攻击者会远程访问用户的其他设备。 此安全漏洞可能会影响整个组织。

Microsoft Defender ATP 可以帮助解决类似这种情况的安全事件。

- 在本例中，Microsoft Defender ATP 检测设备是否存在以下情形：执行了异常代码、遇到了进程权限提升、插入了恶意代码，以及发布了可疑的远程 Shell。
- 基于该设备的这些操作，Microsoft Defender ATP [将该设备分类为高风险](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity)，并在 Microsoft Defender 安全中心门户中包含可疑活动的详细报告。

因为你有 Intune 设备合规性策略来对具有“中等”  或“高”  风险级别的设备分类为不合规，所以受危害的设备被分类为不合规。 这种分类允许条件访问策略介入并阻止从该设备访问公司资源。

## <a name="prerequisites"></a>必备条件

若要将 Microsoft Defender ATP 与 Intune 结合使用，请确保已配置以下各项，并可供使用：

- 企业移动性 + 安全性 E3 和 Windows E5（或 Microsoft 365 企业版 E5）的许可租户
- Microsoft Intune 环境，包含同样加入了 Azure AD 的 [Intune 托管的](../enrollment/windows-enroll.md) Windows 10 设备
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) 和对 Microsoft Defender 安全中心（ATP 门户）的访问权限

> [!NOTE]
> iOS 和 Android Intune 应用保护策略不支持 Microsoft Defender ATP。

## <a name="enable-microsoft-defender-atp-in-intune"></a>在 Intune 中启用 Microsoft Defender ATP

第一步是在 Intune 和 Microsoft Defender ATP 之间设置服务到服务连接。 这需要管理访问 Microsoft Defender 安全中心和 Intune。

### <a name="to-enable-defender-atp"></a>启用 Defender ATP

只需为每个租户启用一次 Defender ATP。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“终结点安全”   > “Microsoft Defender ATP”  ，然后选择“打开 Microsoft Defender 安全中心”  。

   ![选择打开 Microsoft Defender 安全中心](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. 在“Microsoft Defender 安全中心”  中：
    1. 选择“设置”   > “高级功能”  。
    2. 对于“Microsoft Intune 连接”  ，选择“启用”  ：

        ![启用到 Intune 的连接](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. 选择“保存首选项”  。

4. 返回到 Microsoft 终结点管理器管理中心的“Microsoft Defender ATP”  。 在“MDM 符合性策略设置”  下，将“Windows 设备版本 10.0.15063 及更高版本连接到 Microsoft Defender ATP”  设置为“启用”  。

5. 选择“保存”  。

> [!TIP]
> 如果你将新应用集成到 Intune Mobile Threat Defense，并启用与 Intune 的连接，Intune 会在 Azure Active Directory 中创建经典条件访问策略。 集成的每个 MTD 应用（包括 [Defender ATP](advanced-threat-protection.md) 或其他任何 [MTD 合作伙伴](mobile-threat-defense.md#mobile-threat-defense-partners)）都会新建经典条件访问策略。 可以忽略这些策略，但不能对其进行编辑、删除或禁用。
>
> 如果删除了经典策略，你将需要删除负责创建它的 Intune 的连接，然后重新设置。 此过程将重新创建经典策略。 不支持将 MTD 应用的经典策略迁移到新的条件访问策略类型。
>
> MTD 应用的经典条件访问策略：
>
> - 供 Intune MTD 使用，以要求在 Azure AD 中注册设备，这样它们就在与 MTD 合作伙伴通信前有设备 ID 了。 此 ID 是必需的，以便设备可以成功向 Intune 报告其状态。
> - 不会影响其他任何云应用或资源。
> - 此策略与可能创建的用于帮助管理 MTD 的条件访问策略不同。
> - 默认情况下，该策略与用于评估的其他条件访问策略不交互。
>
> 要查看经典条件访问策略，请转到 [Azure](https://portal.azure.com/#home) 中的“Azure Active Directory” > “条件访问” > “经典策略”    。

## <a name="onboard-devices-by-using-a-configuration-profile"></a>使用配置文件载入设备

在 Intune 和 Microsoft Defender ATP 之间建立服务到服务连接之后，将 Intune 管理的设备载入到 ATP，以便收集和使用有关其风险级别的数据。 要载入设备，请使用适用于 Microsoft Defender ATP 的设备配置文件。

建立到 Microsoft Defender ATP 的连接后，Intune 会接收到来自 Microsoft Defender ATP 的 Microsoft Defender ATP 载入配置包。 此包部署到具有设备配置文件的设备上。 配置包配置设备，以与 [Microsoft Defender ATP 服务](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)进行通信以扫描文件、检测威胁，并向 Microsoft Defender ATP 报告风险。 使用配置包载入设备后，不需要再次执行本操作。 还可以使用[组策略或 Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) 载入设备。

### <a name="create-the-device-configuration-profile"></a>创建设备配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入“名称”  和“描述”  。
4. 在“平台”  中，选择“Windows 10 及更高版本” 
5. 对于“配置文件类型”  ，请选择“Microsoft Defender ATP (Windows 10 桌面版)”  。
6. 配置设置：

   - Microsoft Defender ATP 客户端配置包类型  ：选择“载入”  将配置包添加到配置文件。 选择“卸载”，从配置文件中删除配置包  。
  
     > [!NOTE]
     > 如果你已正确建立与 Microsoft Defender ATP 的连接，Intune 会自动为你载入  配置文件，且“Microsoft Defender ATP 客户端配置包类型”  设置将不可用。
  
   - **所有文件的示例共享**：选择“启用”  可收集示例，并与 Microsoft Defender ATP 共享示例。 例如，如果看到可疑文件，可以将其提交至 Microsoft Defender ATP 进行深入分析。 选择“未配置”  不会向 Microsoft Defender ATP 共享任何示例。
   - **加快遥测报告频率**：对于处于高风险的设备，选择“启用”  此设置，可以更频繁地向 Microsoft Defender ATP 服务报告遥测。

     有关这些 Microsoft Defender ATP 设置的详细信息，请参阅[使用 Microsoft Endpoint Configuration Manager 载入 Windows 10 计算机](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm)。

7. 选择“确定”  和“创建”  保存更改，此操作将创建配置文件。
8. [将设备配置文件分配给](../configuration/device-profile-assign.md)希望使用 Microsoft Defender ATP 进行评估的设备。

## <a name="create-and-assign-the-compliance-policy"></a>创建并分配合规性策略

合规性策略确定设备可接受的风险级别。

### <a name="create-the-compliance-policy"></a>创建符合性策略

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “符合性策略”   > “创建策略”  。
3. 输入“名称”  和“描述”  。
4. 在“平台”  中，选择“Windows 10 及更高版本”  。
5. 在“设置”下，选择“Microsoft Defender ATP”   。
6. 将“要求设备不高于计算机风险评分”设置为首选级别  。

   威胁级别分类[由 Microsoft Defender ATP 确定](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue)。

   - **清除**：此级别是最安全的。 设备不能存在任何威胁，且仍可访问公司资源。 如果发现了任何威胁，设备都会被评估为不符合。 （Microsoft Defender ATP 使用“安全”  值。）
   - **低**：如果只有低级别威胁，设备符合策略。 具有中等级别或高级别威胁的设备不符合策略。
   - **中**：如果有低级别或中等级别威胁，设备符合策略。 如果检测到高级别威胁，则设备会被确定为不合规。
   - **高**：此级别最不安全，允许所有威胁级别。 因此，存在高、中等或低级别威胁的设备被视为符合策略。

7. 选择“确定”  和“创建”  以保存更改（并创建策略）。
8. [将设备合规性策略分配](create-compliance-policy.md#assign-the-policy)给适用的组。

## <a name="create-a-conditional-access-policy"></a>创建条件访问策略

条件访问策略阻止设备访问超过合规性策略中设置的威胁级别的资源。 可以阻止设备访问公司资源，如 SharePoint 或 Exchange Online。

> [!TIP]
> 条件访问是一项 Azure Active Directory (Azure AD) 技术。 从 Microsoft 终结点管理器管理中心访问的条件访问节点与从 Azure AD  访问的节点相同。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“终结点安全”   > “条件访问”   > “新策略”  。

3. 输入策略“名称”  ，然后选择“用户和组”  。 使用“包括”或“排除”选项来添加策略的组，然后选择“完成”  。

4. 选择“云应用”  ，然后选择要保护的应用。 例如，选取“选择应用”  ，然后选择“Office 365 SharePoint Online”  和“Office 365 Exchange Online”  。

   选择“完成”  ，保存所做的更改。

5. 选择“条件”   > “客户端应用”  ，将策略应用到应用和浏览器。 例如，选择“是”  ，然后启用“浏览器”  和“移动应用和桌面客户端”  。

   选择“完成”  ，保存所做的更改。

6. 选择“授予”  ，应用基于设备符合性的条件访问。 例如，选择“授予访问权限”   > “要求设备标记为符合策略”  。

    选取“选择”  ，保存所做的更改。

7. 选择“启用策略”  ，然后选择“创建”  以保存更改。

## <a name="monitor-device-compliance"></a>监视设备符合性

接下来，监视具有 Microsoft Defender ATP 符合性策略的设备状态。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “监视器”   > “策略符合性”  。

3. 在列表中找到 Microsoft Defender ATP 策略，并查看符合策略和不符合策略的设备。

还可以对同一位置的不符合设备使用“操作”  报表：

1. 选择“设备”   > “监视”   > “不符合设备”  。

有关报表的详细信息，请参阅 [Intune 报表](../fundamentals/reports.md)。

## <a name="view-onboarding-status"></a>查看载入状态

若要查看所有 Intune 托管的 Windows 10 设备的载入状态，可以转到“设备合规性”   > “Microsoft Defender ATP”  。 在此页中，还可以启动设备配置文件的创建，以便将更多设备载入 Microsoft Defender ATP。

## <a name="next-steps"></a>后续步骤

[Microsoft Defender ATP 条件访问](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)

[Microsoft Defender ATP 风险仪表板](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)

[使用带有 ATP 漏洞管理的安全任务来修复设备上的问题](atp-manage-vulnerabilities.md)。

[设备符合性策略入门](device-compliance-get-started.md)
