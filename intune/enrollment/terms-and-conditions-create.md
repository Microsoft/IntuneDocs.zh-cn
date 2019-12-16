---
title: 设置 Microsoft Intune 中的条款和条件
titleSuffix: ''
description: 设置用户将在公司门户中看到的 Intune 条款和条件。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fb5818609763753878fec7a84fd8c19eb154f88
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955433"
---
# <a name="terms-and-conditions-for-user-access"></a>用户访问条款和条件

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 管理员可以要求用户在使用公司门户之前接受公司的条款和条件，以便：
- 注册设备
- 访问公司应用和电子邮件等资源。

条款和条件配置是可选的。

可以创建多个条款集并将其分配给不同的组，以便支持不同的语言。

创建公司的条款和条件有两种方法：
- 通过使用本文中所述的 Intune。
- 通过使用 [Azure Active Directory 使用条款功能](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)

要了解哪种方法最适合你，请参阅博客文章[为组织选择合适的条款解决方案](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409)。 

## <a name="create-terms-and-conditions"></a>创建条款和条件
完成这些步骤来创建条款和条件。 显示名称和描述供管理使用，条款属性将向“公司门户”中的用户显示。

1. 登录 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，选择“租户管理” > “条款和条件”   。
2. 选择“创建”  。
3. 在“基本信息”  页上，指定下列信息：

   - **名称**：条款在 Azure 门户中的显示名称。 用户看不到此名称。
   - **说明**：有助于在 Azure 门户中标识这组条款的可选详细信息。

    ![显示条款和条件的“基本信息”页的 Azure 门户的屏幕截图](./media/terms-and-conditions-create/terms-basics-page.png)

4. 选择“下一步”，转到“条款”页，并提供以下信息：  

   - **标题**：用户在公司门户中“摘要”  上方看到的条款名称。
   - **条款和条件**：用户看到且必须接受或拒绝的条款和条件。
   - **条款摘要**：解释用户接受条款意味着什么的文本。 例如，“注册设备即表示你同意 Contoso 制定的使用条款。 继续操作前，请仔细阅读条款。”

5. 选择“下一步”，转到“作用域标记”页。  

6. 选择“作用域标记”，选择要向这些条款和条件分配的作用域标记，然后选择“选择”。   

7. 选择“下一步”，转到“分配”页，并为“分配目标”选择以下选项之一：   
    - **所有用户**：选择此选项，将这些条款和条件分配给所有用户。
    - **选择组**：选择此选项，以将这些条款和条件分配给通过选择“选择要包含的组”所标识的组中的所有人。 

8. 选择“下一步”   > “创建”  。

## <a name="see-how-terms-are-displayed-to-your-users"></a>请参阅如何向用户显示条款
下面的示例在管理员控制台和公司门户中显示了“标题”  和“条款摘要”  。

![管理员控制台和公司门户中标题和条款摘要的屏幕截图。](./media/terms-and-conditions-create/terms-summary-terms.png)

下面的示例在管理员控制台和公司门户中显示了标题和条款摘要。

![管理员控制台和公司门户中条款和条件的屏幕截图。](./media/terms-and-conditions-create/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>监视条款和条件

1. 登录 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，选择“租户管理” > “条款和条件”   。
2. 在条款和条件列表中，选择想要查看其接受状态的条款，然后选择“接受报告”  。

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>使用多个版本的条款和条件
可以编辑条款和条件并管理其版本。 每次对条款和条件进行重大更改时，都应执行以下操作：
- 增加版本号
- 要求用户接受新的条款和条件

如果修改错别字或更改格式设置，则维持当前版本号。

1. 登录 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，选择“租户管理” > “条款和条件” > 选择要修改的条款和条件 >“属性”    。

2. 在“属性”窗格中，选择“条款和条件”，然后根据需要修改“标题”、“条款摘要”和“条款和条件”      。 如果作出的更改需要用户重新接受新的条款，请选择“要求用户重新接受并增加版本号” 

3. 选择“确定” > “保存”   。

用户仅需接受一次更新的条款和条件。 有多台设备的用户无需在每台设备上都接受条款和条件。
