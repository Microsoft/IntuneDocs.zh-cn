---
title: 使用 Intune 创建移动威胁防御 (MTD) 应用保护策略
titleSuffix: Microsoft Intune
description: 使用 Microsoft Intune 创建移动威胁防御 (MTD) 应用保护策略。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
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
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794415"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>使用 Intune 创建移动威胁防御应用保护策略

> [!NOTE] 
> 本文适用于支持应用保护策略的所有移动威胁防御 (MTD) 合作伙伴：Better Mobile (Android)、Zimperium (iOS)、Lookout for Work (Android/iOS)。

搭载 MTD 的 Intune 可帮助检测移动设备上存在的威胁和评估相关风险。 可以创建 Intune 应用保护策略，用于评估风险以确定是否允许设备访问公司数据。 

## <a name="before-you-begin"></a>在开始之前

在 MTD 设置过程中，需在 MTD 合作伙伴控制台中创建一个将各种威胁分类为高、中和低的策略。 现在需要在 Intune 应用保护策略中设置移动威胁防御级别。

具有 MTD 应用保护策略的先决条件：

- 使用 Intune 设置 MTD 集成。 如果没有此集成，MTD 应用保护策略将无效。

## <a name="to-create-an-mtd-app-protection-policy"></a>创建 MTD 应用保护策略

1. 转到 [Azure 门户](https://portal.azure.com/)，然后使用 Intune 凭据登录。

2. 在“Azure 仪表板”中，从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune    。

3. 选择“Intune”  ，随即显示“Intune 仪表板”  。

4. 在“Intune 仪表板”中，选择“客户端应用”，然后选择“管理”部分下的“应用保护策略”     。

5. 选择“创建策略”，输入“名称”、“描述”，然后选择“平台”     。 

6. 在“条件启动”窗格中的“设备条件”表下，从“允许的最高设备威胁级别”下的下拉列表中选择移动威胁级别    。

    a.  **安全**：此级别是最安全的。 设备不能存在任何威胁，且仍可访问公司资源。 如果发现了任何威胁，设备都会被评估为不符合。

    b.  **低**：如果设备上仅存在低级威胁，则该设备符合要求。 低级以上的任意威胁都将使设备不合规。

    c.  **中**：如果有低级别或中等级别威胁，则设备符合要求。 如果检测到高级别威胁，则设备会被确定为不合规。

    d.  **高**：此级别是最不安全的威胁级别。 此选项将许可所有威胁级别，且仅将移动威胁防御用作报告目的。 设备必须使用此设置激活 MTD 应用。

7. 单击“保存”两次，然后选择“创建”   。

## <a name="to-assign-an-mtd-app-protection-policy"></a>分配 MTD 应用保护策略

若要为用户分配设备合规性策略，请选择之前已配置的策略。 可在“设备符合性 - 策略”窗格中找到现有策略  。

1. 选择要分配给用户的策略，然后选择“分配”  。 此操作将打开窗格，可在其中选择“Azure Active Directory 安全组”并将其分配到策略  。

2. 选择“选择要添加的组”以打开显示 Azure AD 安全组的窗格  。 选择“选择”会将策略部署到用户  。

> [!NOTE] 
> 你已将策略应用于用户。 将通过 Intune 应用保护评估策略目标用户所使用的设备，以确定是否允许其访问目标应用上的公司数据。

## <a name="next-steps"></a>后续步骤  

- 详细了解 Microsoft Intune 中的[移动威胁防御](~/protect/mobile-threat-defense.md)。
