---
title: 设置 Microsoft Intune 中的条款和条件
titlesuffix: ''
description: 设置用户将在公司门户中看到的 Intune 条款和条件。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b0571ad6196277ee2bc257d72cc4db24fcc3424
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237939"
---
# <a name="terms-and-conditions-for-user-access"></a>用户访问条款和条件

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 管理员可以要求用户在使用公司门户之前接受公司的条款和条件，以便：
- 注册设备
- 访问公司应用和电子邮件等资源。    
条款和条件配置是可选的。

可以创建多个条款集并将其分配给不同的组，以便支持不同的语言。

创建公司的条款和条件有两种方法：
- 通过使用本文中所述的 Intune。
- 通过使用[Azure Active Directory 使用条款功能](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou) 要了解哪种方法最适合你，请参阅博客文章 [Choosing the right Terms solution for your organization blog post](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409)（为组织选择合适的条款解决方案）。 

## <a name="create-terms-and-conditions"></a>创建条款和条件
完成这些步骤来创建条款和条件。 显示名称和描述供管理使用，条款属性将向“公司门户”中的用户显示。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“设备注册” > “条款和条件”。
2. 选择“创建”。
![显示条款和条件的“创建”按钮的 Azure 门户的屏幕截图](media/terms-create-terms.png)
3. 在展开的窗格中，指定下列信息：

   - **显示名称**：条款在 Azure 门户中的显示名称。 用户看不到此名称。

   - **说明**：有助于在 Azure 门户中标识这组条款的可选详细信息。

4. 选择“定义使用条款”旁边的箭头以打开“条款和条件”窗格，然后输入以下信息：

   ![最终用户条款和条件接受屏幕的屏幕截图，其中包含条款摘要](./media/terms-summary-create.png)

   - **标题**：用户在公司门户中“摘要”上方看到的条款名称。
   - **条款摘要**：解释用户接受条款意味着什么的文本。 例如，“注册设备即表示你同意 Contoso 制定的使用条款。 继续操作前，请仔细阅读条款。”
   - **条款和条件**：用户看到且必须接受或拒绝的条款和条件。

5. 选择“确定” > “创建”。

## <a name="see-how-terms-are-displayed-to-your-users"></a>请参阅如何向用户显示条款
下面的示例在管理员控制台和公司门户中显示了“标题”和“条款摘要”。

![管理员控制台和公司门户中标题和条款摘要的屏幕截图。](./media/terms-summary-terms.png)

下面的示例在管理员控制台和公司门户中显示了标题和条款摘要。

![管理员控制台和公司门户中条款和条件的屏幕截图。](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>分配条款和条件

可以将条款和条件分配给用户组，这些用户必须先接受它们，然后才能使用“公司门户”。

1. 在 Azure 门户中，依次选择“设备注册”和“条款和条件”。
2. 在条款和条件列表中，选择想要分配的条款，然后选择“管理” > “分配”。
![Azure 门户的“分配组”窗格的屏幕快照，其中显示了用于分配条款和条件的“选择组”按钮和“选择”按钮](media/terms-assign-groups.png)
3. 选择“选择要包含的组”并选择要分配条款的组，然后单击“选择”。 无法为动态组分配条款和条件。
4. 在“已分配组”窗格中，单击“保存”。  现已将条款和条件分配给所选组中的用户。 在用户下一次访问公司门户时将提示他们接受条款。 仅需接受一次条款和条件。 有多台设备的用户无需在每台设备上都接受。


## <a name="monitor-terms-and-conditions"></a>监视条款和条件

1. 在 Azure 门户中，选择“所有服务” > “监视 + 管理” > “Intune”。 
1. 在“Intune”窗格中，选择“设备注册” > “条款和条件”。
2. 在条款和条件列表中，选择想要查看其接受状态的条款，然后选择“接受报告”。

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>使用多个版本的条款和条件
可以编辑条款和条件并管理其版本。 每次对条款和条件进行重大更改时，都应执行以下操作：
- 增加版本号
- 要求用户接受新的条款和条件，如果要修改拼写错误或更改格式等，请维持当前版本号。

1. 在 Azure 门户中，选择“所有服务” > “监视 + 管理” > “Intune”。

2. 在“Intune”窗格中，选择“设备注册” > “条款和条件”> 选择要修改的条款和条件 >“属性”。

4. 在“属性”窗格中，选择“条款和条件”，然后根据需要修改“标题”、“条款摘要”和“条款和条件”。 如果作出的更改需要用户重新接受新的条款，请选择“要求用户重新接受并增加版本号”

4.  选择“确定” > “保存”。

用户仅需接受一次更新的条款和条件。 有多台设备的用户无需在每台设备上都接受条款和条件。
