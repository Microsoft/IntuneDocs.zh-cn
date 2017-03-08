---
title: "设置 Microsoft Intune 中的条款和条件"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：设置用户将在公司门户中看到的 Intune 条款和条件。 "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 07a42cf8fa10d3223129fbb2932217ff90ac365b
ms.lasthandoff: 02/18/2017

---

# <a name="set-terms-and-conditions"></a>设置条款和条件 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

可以将 Intune 条款和条件部署到用户组，以解释注册、访问工作资源和使用公司门户对设备和用户有何影响。 用户必须接受这些条款和条件，然后才能使用公司门户进行注册或访问工作。

你可以创建和部署包含不同条款和条件的多个策略。 也可以用不同的语言生成相同条款和条件的不同版本，然后将它们部署到相应的组。

**创建条款和条件**：

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在 Intune 边栏选项卡上，选择“注册设备”，然后选择“条款和条件”。

3. 选择“创建”。

4. 在“创建条款和条件”边栏选项卡上，指定以下信息：

   - **显示名称**：要用于条款的名称。 用户将在公司门户中看到此名称。

   - **描述**：帮助在 Azure 门户中标识策略的可选详细信息。

5. 选择“定义使用条款”旁边的箭头打开“条款和条件”边栏选项卡，然后输入以下信息：

   - **标题**：用户在公司门户中看到的标题。

   - **条款摘要**：阐释用户接受条款的含义的文字。

   - **条款和条件**：用户可查看且必须接受或拒绝的法律标签，例如：“我同意条款和条件”。

6. 选择“确定”。

