---
title: 使用 Microsoft Intune 创建 MTD 设备符合性策略
titlesuffix: ''
description: 创建使用 MTD 合作伙伴威胁级别的 Intune 设备符合性策略，以确定移动应用是否可以访问公司资源。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1152473206826aa2e3f63c7196a3d0538101a948
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>使用 Intune 创建移动威胁防御 (MTD) 设备符合性策略

> [!NOTE] 
> 此信息适用于所有移动威胁防御合作伙伴。

搭载 MTD 的 Intune 可帮助检测移动设备上存在的威胁和评估相关风险。 可创建评估风险的 Intune 设备符合性策略规则，确定设备是否合规。 然后可使用条件性访问策略，根据设备合规性阻止对服务的访问。

## <a name="before-you-begin"></a>在开始之前

在 MTD 设置过程中，需在 MTD 合作伙伴控制台中创建一个将各种威胁分类为高、中和低的策略。 现在需要在 Intune 设备符合性策略中设置移动威胁防御级别。

MTD 设备符合性策略先决条件：

-   使用 Intune 设置 MTD 集成

## <a name="to-create-an-mtd-device-compliance-policy"></a>创建 MTD 设备符合性策略

1.  转到 [Azure 门户](https://portal.azure.com/)，然后使用 Intune 凭据登录。

2.  在“Azure 仪表板”中，从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune。

3.  选择“Intune”，随即显示“Intune 仪表板”。

4. 在“Intune 仪表板”中，选择“设备符合性”，然后选择“管理”部分下的“策略”。

5.  选择“创建策略”，输入设备符合性“名称”、“说明”，选择“平台”，然后选择“设置”部分下的“配置”。

6.  在“符合性策略”窗格中，选择“设备运行状况”。

7.  在“设备运行状况”窗格中，从“要求设备不高于设备威胁级别”下的下拉列表中选择移动威胁级别。

    a.  **安全**：此级别是最安全的威胁级别。 设备不能存在任何威胁，且仍可访问公司资源。 如果发现了任何威胁，设备都会被评估为不符合。

    b.  **低**：如果设备上仅存在低级威胁，则该设备合规。 低级以上的任意威胁都将使设备不合规。

    c.  **中**：如果设备上发现的威胁为低级别或中等级别，设备为合规。 如果检测到高级别威胁，则设备会被确定为不合规。

    d.  **高**：此级别是最不安全的威胁级别。 此选项将许可所有威胁级别，且仅将移动威胁防御用作报告目的。 设备必须使用此设置激活 MTD 应用。

8.  单击“确定”两次，然后选择“创建”。

> [!IMPORTANT]
> 如果为 Office 365 或其他服务创建条件性访问策略，将评估设备的符合性并阻止不符合设备访问公司资源，直到解决威胁。

## <a name="to-assign-an-mtd-device-compliance-policy"></a>分配 MTD 设备符合性策略

若要为用户分配设备合规性策略，请选择之前已配置的策略。 可在“设备符合性 - 策略”窗格中找到现有策略。

1. 选择要分配给用户的策略，然后选择“分配”。 此操作将打开窗格，可在其中选择“Azure Active Directory 安全组”并将其分配给策略。

2. 选择“选择要添加的组”以打开显示 Azure AD 安全组的窗格。  选择“选择”会将策略部署到用户。

    > [!NOTE] 
    > 你已将策略应用于用户。 将评估策略针对的用户所使用设备的符合性。

## <a name="next-steps"></a>后续步骤

- [通过 Intune 启用 MTD](mtd-connector-enable.md)