---
title: 条件访问方案
titleSuffix: Microsoft Intune
description: 了解 Intune 条件访问通常如何用于基于设备和基于应用的条件访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d30749a7eaa3d516bef2f2acff3e010d69db1c0e
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547055"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>通过 Intune 使用条件访问的常见方式有哪些？

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


使用 Intune 的条件访问有两种：基于设备的条件访问和基于应用的条件访问。 需要配置相关的符合性策略，以驱动组织中的条件访问符合性。 条件访问通常用于执行以下操作：允许或阻止对 Exchange 的访问、控制网络访问权限、与 Mobile Threat Defense 解决方案集成等。
 
本文中的信息有助于了解如何使用 Intune 移动设备符合性功能和 Intune 移动应用程序管理 (MAM) 功能   。 

> [!NOTE]
> 条件访问是 Azure Active Directory Premium 许可证附带的 Azure Active Directory 功能。 Intune 通过向解决方案添加移动设备符合性和移动应用管理来增强此功能。 从 Intune 访问的条件访问节点与从 Azure AD 访问的节点相同   。  

## <a name="device-based-conditional-access"></a>基于设备的条件访问

可以配合使用 Intune 和 Azure Active Directory，以确保仅托管且合规的设备可以访问电子邮件和 Office 365 服务、软件即服务 (SaaS) 应用和[本地应用](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)。 此外，可在 Azure Active Directory 中设置策略，以仅允许加入域的计算机或在 Intune 中已注册的移动设备访问 Office 365 服务。

Intune 提供了设备符合性策略功能，可评估设备的符合性状态。 在用户尝试访问公司资源时，符合性状态会报告给 Azure Active Directory，用于强制执行在 Azure Active Directory 中创建的条件访问策略。

通过 [Azure 门户](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)为 Exchange online 和其他 Office 365 产品配置基于设备的条件访问策略。  

- 了解有关[需要具有 Azure Active Directory 中条件访问权限的受管理设备](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)的详细信息。

- 了解有关 [Intune 设备符合性](device-compliance-get-started.md)的详细信息。

- 了解有关 [Azure Active Directory 中通过条件访问使用受支持的浏览器](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers)的详细信息。

> [!NOTE]
> 在 Android 设备上为 SharePoint Online 或对 Exchange Online 的基于浏览器的访问启用基于设备的访问时，用户必须在注册的设备上打开“启用浏览器访问”选项，如下所示： 
> 1. 启动“公司门户应用”  。
> 2. 从三个点 (…) 或硬件菜单按钮转到“设置”  页。
> 3. 按“启用浏览器访问”  按钮。 
> 4. 在 Chrome 浏览器中，从 Office 365 中注销并重启 Chrome。

### <a name="conditional-access-based-on-network-access-control"></a>基于网络访问控制的条件性访问

基于 Intune 注册和设备符合性状态，Intune 与 Cisco ISE、Aruba Clear Pass 以及 Citrix NetScaler 等合作伙伴集成，以提供访问控制。

根据用户使用的设备是否受管理以及是否符合 Intune 设备符合性策略，可以允许或拒绝他们访问企业 Wi-Fi 或 VPN 资源。

- 详细了解 [NAC 与 Intune 的集成](network-access-control-integrate.md)。

### <a name="conditional-access-based-on-device-risk"></a>基于设备风险的条件性访问

Intune 与移动威胁防护供应商合作提供安全性解决方案，以检测恶意软件、木马以及移动设备上的其他威胁。

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Intune 和移动威胁防御集成的工作方式

在移动设备安装了移动威胁防御代理后，一旦发现移动设备自身存在威胁，代理即将符合性状态消息发送回 Intune 报告。

在基于设备风险的条件访问决策中，Intune 和移动威胁防御集成发挥着重要的作用。

- 了解 [Intune 移动威胁防御](mobile-threat-defense.md)的详细信息。

### <a name="conditional-access-for-windows-pcs"></a>Windows 电脑的条件访问

适用于电脑的条件访问提供与移动设备可用的类似功能。 让我们介绍一下使用 Intune 管理电脑时，你可以使用条件性访问的方式。

#### <a name="corporate-owned"></a>公司拥有的设备

- **本地 AD 域加入：** 此选项通常适用于已经非常习惯通过 AD 组策略或 Configuration Manager 管理 PC 的组织。

- **Azure AD 域加入和 Intune 管理：** 此方案适用于希望云优先（即主要使用云服务，以减少使用本地基础结构）或仅使用云（无本地基础结构）的组织。 Azure AD 联接非常适用于混合环境，可以借助它访问云和本地应用及资源。 设备要加入 Azure AD 并在 Intune 中注册，可以将此用作访问公司资源的条件访问条件。

- **AD 域加入和 Configuration Manager：** 自当前分支起，Configuration Manager 还提供可以评估特定符合性标准的条件访问功能（作为加入域的电脑是已有功能）：

  - 电脑是否已加密？

  - 是否安装了反恶意软件？ 是否为最新版本？

  - 设备是否越狱或取得 root 权限？

#### <a name="bring-your-own-device-byod"></a>自带设备办公 (BYOD)

- **工作区加入和 Intune 管理：** 用户可以加入自己的个人设备，以访问公司资源和服务。 你可以使用工作区将设备加入并注册到 Intune MDM 以接收设备级别的策略，这是评估条件访问标准的另一个选项。

了解有关 [Azure Active Directory 中的设备管理](https://docs.microsoft.com/azure/active-directory/devices/overview)的详细信息。

## <a name="app-based-conditional-access"></a>基于应用的条件性访问

配合使用 Intune 和 Azure Active Directory，可确保仅托管的应用可访问公司电子邮件或其他 Office 365 服务。

- 了解[使用 Intune 且基于应用的条件性访问](app-based-conditional-access-intune.md)的详细信息。

### <a name="intune-conditional-access-for-exchange-on-premises"></a>本地 Exchange 的 Intune 条件访问

基于设备符合性策略和注册状态，条件性访问可用于允许或阻止访问 **Exchange 内部部署**。 结合使用条件性访问与设备符合性策略时，仅允许合规的设备访问 Exchange 内部部署。

你可以在条件性访问中配置高级设置，以进行更精细的控制，例如：

- 允许或阻止某些平台。

- 立即阻止不受 Intune 管理的设备。

应用设备符合性和条件性访问策略时，检查用于访问 Exchange 内部部署的任何设备的符合性。

设备不满足设置的条件时，指导最终用户完成设备注册流程，以修复导致设备不符合的问题。

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Exchange 内部部署工作的条件性访问方式

本地 Exchange 条件访问的工作原理不同于基于 Azure 条件访问的策略。 要安装 Intune Exchange 本地连接器，以直接与 Exchange Server 交互。 Intune Exchange 连接器将拉取存在于 Exchange 服务器上的全部 Exchange Active Sync (EAS) 记录，因此，Intune 可以使用这些 EAS 记录并将其映射到 Intune 设备记录。 这些记录都是通过 Intune 注册和识别的设备。 此过程将允许或阻止电子邮件访问。

如果 EAS 记录是新的，并且 Intune 不能识别，则 Intune 会发出一个 cmdlet 命令（发音为“command-let”），来指示 Exchange Server 阻止访问电子邮件。 下面是有关此流程工作方式的更多详细信息：

![使用 CA 流程图的 Exchange 内部部署](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. 用户尝试访问托管在 Exchange 内部部署 2010 SP1 或更高版本上的公司电子邮件。

2. 如果设备不受 Intune 管理，它将无法访问电子邮件。 Intune 会将阻止通知发送到 EAS 客户端。

3. EAS 收到阻止通知后，将设备移至隔离区域，并发送包含修正步骤（其中包含链接）的隔离电子邮件，以便用户可以注册自己的设备。

4. 发生工作区加入流程，这是 Intune 托管设备的第一步。

5. 设备已注册 Intune。

6. Intune 将 EAS 记录映射到设备记录，并保存设备符合性状态。

7. Azure AD 设备注册过程已注册 EAS 客户端 ID，此过程创建了 Intune 设备记录和 EAS 客户端 ID 之间的关系。

8. Azure AD 设备注册会保存设备状态信息。

9. 如果用户满足条件访问策略，Intune 会通过 Intune Exchange 连接器发出 cmdlet，允许邮箱进行同步。

10. Exchange Server 会将通知发送到 EAS 客户端，以便用户可以访问电子邮件。


#### <a name="whats-the-intune-role"></a>什么是 Intune 职责？

Intune 评估并管理设备状态。

#### <a name="whats-the-exchange-server-role"></a>什么是 Exchange Server 角色？

Exchange Server 提供了 API 和基础结构，可将设备移至隔离区域。

> [!IMPORTANT]
> 请注意，使用设备的用户必须将符合性配置文件和 Intune 许可证分配到该设备中，以便对其进行符合性评估。 如果未向用户部署合规性策略，该设备将被视为合规且不会对其应用任何访问限制。

## <a name="next-steps"></a>后续步骤

[如何在 Azure Active Directory 中配置条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[设置基于应用的条件访问策略](app-based-conditional-access-intune-create.md)

[如何使用 Intune 安装本地 Exchange 连接器](exchange-connector-install.md)。

[如何为本地 Exchange 创建条件访问策略](conditional-access-exchange-create.md)
