---
title: 使用 Intune 设置基于应用的条件性访问策略
description: 了解如何使用 Intune 创建基于应用的条件性访问策略。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b7e3654021935495189b62da5257793383586137
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>使用 Intune 设置基于应用的条件性访问策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍如何为已批准应用列表中的一部分应用设置基于应用的条件性访问策略。 已批准应用列表包含经由 Microsoft 测试过的应用。

> [!IMPORTANT]
> 本文演练使用 Exchange Online 添加基于应用的条件性访问策略的步骤，当添加已批准应用列表中的 SharePoint Online、Microsoft Teams 等其他应用时，也可使用相同的步骤。

## <a name="to-create-an-app-based-conditional-access-policy"></a>创建基于应用的条件性访问策略
1.  转到“[Azure 门户](https://portal.azure.com)”，然后使用你的凭据登录。

2.  选择“所有服务”，然后键入“Intune”。

3.  选择“Intune 应用保护”。

4.  在“条件性访问”部分下的“Intune 应用保护”上，选择“Exchange Online”。

    ![显示条件性访问部分（其中突出显示 Exchange Online 选项）的设置窗格的屏幕截图](./media/MAM-conditional-access-1.png)

6. 在“允许的应用”窗格上，选择“允许支持 Intune 应用策略的应用”选项以便仅允许 Intune 应用保护策略支持的应用能够访问 Exchange Online。 选择此选项时，会显示支持的应用的列表。

    > [!NOTE]
    > 阻止所有 Exchange Active Sync 邮件客户端（包括 iOS 和 Android 上连接到 Exchange Online 的内置邮件客户端）发送或接收电子邮件。 用户会改为收到一封电子邮件，告知他们需要使用 Outlook 邮件应用。

7. 若要将此策略应用于用户，请打开“已限制的用户组”窗格，然后选择“添加用户组”。 选择应获取此策略的一个或多个用户组。

    ![突出显示“添加用户组”选项的“已限制用户组”窗格的屏幕截图](./media/mam-ca-add-user-group.png)

8. 你可能希望在上一步中选择的用户组中的某些用户不受此策略影响。 在这种情况下，将用户组添加到被免除的用户组列表。 从“Exchange Online”窗格，选择“被免除的用户组”。 选择“添加用户组”以打开用户组的列表。 选择要从此策略中免除的组。

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>从现有的基于应用的 CA 策略中修改或删除用户组

1. 打开“已限制的用户组”窗格，然后突出显示要删除的用户组。
2. 单击椭圆查看删除选项。
3. 选择“删除”以从列表中删除用户组。

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>在 Azure AD 工作负载中创建基于应用的条件访问策略

从 Intune 1708 版本开始，IT 管理员可从 Azure AD 工作负载中创建基于应用的条件访问策略。 这样就无需在 Azure 和 Intune 工作负载之间进行切换，简化了操作。

> [!IMPORTANT]
> 需要具备 Azure AD Premium 许可证才能从 Intune Azure 门户创建 Azure AD 条件性访问策略。

### <a name="to-create-an-app-based-conditional-access-policy"></a>创建基于应用的条件性访问策略

> [!IMPORTANT]
> 使用基于应用的条件访问策略前，需要将 [Intune 应用保护策略](app-protection-policies.md)应用于应用。

1. 在“Intune 仪表板”中，选择“条件访问”。

2. 在“策略”窗格中，选择“新建策略”以创建基于应用的新条件性访问策略。

4. 输入策略名称并配置“分配”部分中可用的设置后，在“访问控制”部分下选择“授予”。

5. 选择“需要已批准的客户端应用”>“选择”>“创建”，保存新策略。

## <a name="next-steps"></a>后续步骤
[阻止不具有新式验证的应用](app-modern-authentication-block.md)

### <a name="see-also"></a>另请参阅

[使用应用保护策略保护应用数据](app-protection-policies.md)
[Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
