---
title: 在 Microsoft Intune 中使用 Windows Defender ATP - Azure | Microsoft Docs
description: 了解如何在端到端应用场景中启用 Windows Defender 高级威胁防护 (ATP)，包括在 Intune 和 Windows Defender 安全中心（ATP 门户）中启用 ATP，使用 ATP 配置文件载入设备，创建 Intune 设备符合性策略，创建 Azure AD 条件访问策略，以及监视设备符合性。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 036f2ca8302f9b3c2d700a04918c4c49a4c6211a
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61490532"
---
# <a name="enforce-compliance-for-windows-defender-atp-with-conditional-access-in-intune"></a>使用 Intune 中的条件访问强制执行 Windows Defender ATP的符合性

Windows Defender 高级威胁防护 (ATP) 和 Microsoft Intune 一起协作来帮助免受安全漏洞的威胁，并帮助限制组织中的漏洞影响。

此功能适用于：Windows 10 设备

例如，有人向组织内的用户发送包含嵌入式恶意代码的 Word 附件。 在用户打开附件时，将启用内容。 提升的权限攻击随即启动，且来自远程计算机的攻击者对受害者的设备具有管理权限。 然后，攻击者会远程访问用户的其他设备。

此安全漏洞可能会影响整个组织。

Windows Defender ATP 可以解决类似这种情况的安全事件。 Windows Defender 安全中心（ATP 控制台）将设备报告为“高风险”，并包括可疑活动的详细报告。 在本例中，Windows Defender ATP 检测设备是否存在以下情形：执行了异常代码、遇到了进程权限提升、插入了恶意代码，以及发布了可疑的远程 Shell。 然后，Windows Defender ATP 会为你提供选项来缓解威胁。

使用 Intune 可创建符合性策略，用于确定可接受的风险级别。 如果设备超过这一级别的风险，则设备不符合策略。 与 Azure Active Directory (AD) 条件访问结合使用时，将阻止用户访问公司资源。

本文介绍如何：

- 在 ATP 中启用 Intune，然后在 Intune 中启用 ATP。 这些任务在 Intune 和 Windows Defender ATP 之间创建一个服务到服务的连接。 此连接允许 Windows Defender ATP 写入 Intune 设备的计算机风险。
- 在 Intune 中创建符合性策略。
- 根据威胁级别在设备上启用 Azure Active Directory (AD) 中的条件访问。

## <a name="prerequisites"></a>必备条件

若要将 ATP 与 Intune 结合使用，请确保已配置以下各项，并可供使用：

- 企业移动性 + 安全性 E3 和 Windows E5（或 Microsoft 365 企业版 E5）的许可租户
- Microsoft Intune 环境，包含同样加入了 Azure AD 的 [Intune 托管的](windows-enroll.md) Windows 10 设备
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) 和对 Windows Defender 安全中心（ATP 门户）的访问权限

## <a name="enable-windows-defender-atp-in-intune"></a>在 Intune 中启用 Windows Defender ATP

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备符合性” > “Windows Defender ATP” > “打开 Windows Defender 安全中心”。

    ![选择打开 Windows Defender 安全中心](./media/atp-device-compliance-open-windows-defender.png)

4. 在“Windows Defender 安全中心”中：
    1. 选择“设置” > “高级功能”。
    2. 对于“Microsoft Intune 连接”，选择“启用”：

        ![启用到 Intune 的连接](./media/atp-security-center-intune-toggle.png)

    3. 选择“保存首选项”。

5. 返回到 Intune，“设备符合性” > “Windows Defender ATP”。 将“将 Windows 设备版本 10.0.15063 及更高版本连接到 Windows Defender ATP”设置为“启用”。
6. 选择“保存”。

通常执行此任务一次。 因此，如果已在 Intune 资源中启用 ATP，则不需要再次执行本操作。

## <a name="onboard-devices-using-a-configuration-profile"></a>使用配置文件载入设备

当最终用户在 Intune 中注册时，可以使用配置文件向设备推送不同的设置。 这同样适用于 Windows Defender ATP。

Windows Defender 包括载入配置包，该包可与 [Windows Defender ATP 服务](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)进行通信以扫描文件、检测威胁，并向 Windows Defender ATP 报告风险。

载入时，Intune 将从 Windows Defender ATP 收到自动生成的配置包。 配置文件被推送或部署到设备后，此配置包也会被推送到该设备。 这使 Windows Defender ATP 能够监视设备中的威胁。

使用配置包载入设备后，不需要再次执行本操作。 还可以使用[组策略或 System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection) 载入设备。

### <a name="create-the-configuration-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入“名称”和“描述”。
4. 在“平台”中，选择“Windows 10 及更高版本”
5. 对于“配置文件类型”，请选择“Windows Defender ATP (Windows 10 桌面版)”。
6. 配置设置：

  - **Windows Defender ATP 客户端配置包类型**：选择“载入”将配置包添加到配置文件。 选择“卸载”，从配置文件中删除配置包。
  
    > [!NOTE] 
    > 如果你已正确建立与 Windows Defender ATP 的连接，Intune 会自动为你载入配置配置文件，且“Windows Defender ATP 客户端配置包类型”设置将不可用。
  
  - **所有文件的示例共享**：选择“启用”可收集示例，并与 Windows Defender ATP 共享示例。 例如，如果看到可疑文件，可以将其提交至 Windows Defender ATP 进行深入分析。 选择“未配置”不会向 Windows Defender ATP 共享任何事例。
  - **加快遥测报告频率**：对于处于高风险的设备，选择“启用”此设置，可以更频繁地向 Windows Defender ATP 服务报告遥测。

    有关这些 Windows Defender ATP 设置的详细信息，请参阅[使用 System Center Configuration Manager 载入 Windows 10 计算机](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection)。

7. 选择“确定”和“创建”保存更改，此操作将创建配置文件。

## <a name="create-the-compliance-policy"></a>创建符合性策略
符合性策略确定设备上可接受的风险级别。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备符合性” > “策略” > “创建策略”。
3. 输入“名称”和“描述”。
4. 在“平台”中，选择“Windows 10 及更高版本”。
5. 在“Windows Defender ATP”设置中，将“要求设备不高于计算机风险评分”设置为首选级别。 威胁级别分类[由 Windows Defender ATP 确定](https://review.docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/alerts-queue-windows-defender-advanced-threat-protection?branch=atp-server2008#sort-filter-and-group-the-alerts-queue)。

   - **清除**：此级别是最安全的。 设备不能存在任何威胁，且仍可访问公司资源。 如果发现了任何威胁，设备都会被评估为不符合。 （Windows Defender ATP 使用“安全”值。）
   - **低**：如果只有低级别威胁，设备符合策略。 具有中等级别或高级别威胁的设备不符合策略。
   - **中**：如果有低级别或中等级别威胁，设备符合策略。 如果检测到高级别威胁，则设备会被确定为不合规。
   - **高**：此级别最不安全，允许所有威胁级别。 因此，存在高、中等、低级别威胁的设备被视为符合策略。

6. 选择“确定”和“创建”以保存更改（并创建策略）。

## <a name="assign-the-policy"></a>分配策略

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备符合性” > “策略”>选择你的 Windows Defender ATP 符合性策略。
3. 选择“分配”。
4. 包含或排除你的 Azure AD 组以向它们分配策略。
5. 若要将策略部署到组，请选择“保存”。 将评估策略针对的用户设备的符合性。

## <a name="create-a-conditional-access-policy"></a>创建条件访问策略
如果设备不符合策略，条件访问策略将阻止访问资源。 因此，如果设备超出威胁级别，可以阻止对公司资源（如 SharePoint 或 Exchange Online）的访问。  

> [!TIP]  
> 条件访问是一项 Azure Active Directory (Azure AD) 技术。 从 Intune 访问的条件访问节点与从 Azure AD 访问的节点相同。  

1. 在 [Azure 门户](https://portal.azure.com)中，打开“Intune” > “条件访问” > “新建策略”。
2. 输入策略“名称”，然后选择“用户和组”。 使用“包括”或“排除”选项来添加策略的组，然后选择“完成”。
3. 选择“云应用”，然后选择要保护的应用。 例如，选取“选择应用”，然后选择“Office 365 SharePoint Online”和“Office 365 Exchange Online”。

    选择“完成”，保存所做的更改。

4. 选择“条件” > “客户端应用”，将策略应用到应用和浏览器。 例如，选择“是”，然后启用“浏览器”和“移动应用和桌面客户端”。

    选择“完成”，保存所做的更改。

5. 选择“授予”，应用基于设备符合性的条件访问。 例如，选择“授予访问权限” > “要求设备标记为符合策略”。

    选取“选择”，保存所做的更改。

6. 选择“启用策略”，然后选择“创建”以保存更改。

[什么是条件访问？](conditional-access.md)是很棒的资源。

## <a name="monitor-device-compliance"></a>监视设备符合性
接下来，监视具有 Windows Defender ATP 符合性策略的设备状态。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备符合性” > “策略符合性”。
3. 在列表中找到 Windows Defender ATP 策略，并查看符合策略和不符合策略的设备。

## <a name="more-good-stuff"></a>更多出色内容
[Windows Defender ATP 条件访问](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Windows Defender ATP 风险仪表板](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[设备符合性策略入门](device-compliance-get-started.md)  
[Azure AD 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
