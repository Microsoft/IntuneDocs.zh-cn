---
title: "什么是条件性访问？"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何定义用户和设备在 Microsoft Intune Azure 预览版中访问公司资源必须满足的条件。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8ab6d782460a857a0901abd9bd567365ee2e3f70
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="what-is-conditional-access"></a>什么是条件性访问？


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


本主题将介绍条件性访问，因为它适用于企业移动性 + 安全性，然后介绍 Intune 中的条件性访问功能。

企业移动性 + 安全性 (EMS) 中的条件性访问利用 Azure Active Directory Premium 和 Microsoft Intune 的强大功能提供保护公司数据安全所需的控制，同时为用户提供可从任何设备实现最佳工作效率的体验。

通过条件性访问，可以根据位置、设备和用户状态定义限制公司数据访问权限的条件和应用程序敏感度。

从设备角度看，Intune 和 Azure Active Directory 协同工作以确保仅允许托管且合规的设备访问电子邮件和 Office 365 服务。 例如，可在 Azure Active Directory 中设置策略，仅允许加入域的计算机或在 Intune 等移动设备管理应用程序中已注册的移动设备访问 Office 365 服务。 可使用 Intune 设置评估设备合规性状态的设备合规性配置文件。 用户尝试访问公司资源时，合规性状态报告到 Azure Active Directory，用于强制执行 Azure Active Directory 中的策略。 若要了解 Intune 中设备合规性的信息，请参阅[什么是设备合规性？](device-compliance.md)。

可以通过 Azure Active Directory 配置针对云应用（如 Exchange Online）的条件性访问。 有关详细信息，请参阅此[文章](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

## <a name="on-premises-conditional-access-in-intune"></a>Intune 中的本地条件性访问

基于设备管理和注册，Intune 中的条件性访问可用于允许或阻止访问**Exchange 内部部署**。

设备合规性配置文件设置用于评估设备的合规性。 条件性访问通过评估允许或阻止访问 Exchange 内部部署。 结合使用条件性访问与设备合规性配置文件时，仅允许合规的设备访问 Exchange 内部部署。 可以在条件性访问中配置高级设置，实现更细化的控制，如：允许或阻止某些平台，或者即时阻止非 Intune 托管的设备。

设备合规性配置文件和条件性访问已分配给用户。 检查用户用于访问 Exchange 内部部署的任何设备是否合规。 请记住，使用该设备的用户必须将合规性配置文件分配到设备中，以便对其进行合规性评估。 如果未向用户部署合规性策略，该设备将被视为合规且不会对其应用任何访问限制。

当设备不满足设置的条件时，将指导最终用户完成设备注册流程并修复导致设备不兼容的问题。

## <a name="next-steps"></a>后续步骤

[如何为 Exchange 内部部署创建条件性访问策略](conditional-access-exchange-create.md)

[如何在 Azure Active Directory 中配置条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

