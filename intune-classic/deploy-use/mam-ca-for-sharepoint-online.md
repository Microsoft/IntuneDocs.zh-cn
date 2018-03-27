---
title: 为 SharePoint Online 创建基于应用的条件性访问策略
description: ''
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 05/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 5848fc18e0c288f8806f1fc93427d96c48317d64
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="set-up-app-based-conditional-access-ca-policies-for-sharepoint-online"></a>为 SharePoint Online 设置基于应用的条件性访问 (CA) 策略

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

本主题将提供关于如何为 SharePoint Online 设置基于应用的条件性访问策略的指导。 基于应用的 CA 将帮助管理员仅允许已应用 Intune 应用保护策略的移动应用。

## <a name="to-create-the-app-based-ca-policy-for-sharepoint-online"></a>为 SharePoint Online 创建基于应用的 CA 策略

1. 转到“[Azure 门户](https://portal.azure.com)”，然后使用你的凭据登录。

    > [!NOTE]
    > 如果是刚接触 Azure 门户体验，请阅读[应用保护策略的 Azure 门户](azure-portal-for-microsoft-intune-mam-policies.md)主题。

2. 从左侧菜单中选择“**更多服务**”，然后在文本框筛选器中键入 **Intune**。

3. 选择“Intune 应用保护” > “Intune 移动应用程序管理” > “所有设置”。

4. 在“Intune 移动应用程序管理”边栏选项卡中，选择“SharePoint Online”磁贴。

5. 在“允许的应用”边栏选项卡上，选择“允许支持 Intune 应用策略的应用”选项以便仅允许 Intune 应用保护策略支持的应用。

    > [!NOTE] 
    > 当选中仅允许 Intune 应用保护策略支持的应用的选项时，将显示仅包含支持的应用列表。

    ![显示应用列表的允许应用边栏选项卡的屏幕快照](../media/mam-ca-spo-allowed-apps.png)

## <a name="to-assign-app-based-ca-policies-to-your-users"></a>将基于应用的 CA 策略分配给用户

1. 打开“已限制的用户组”边栏选项卡，然后选择“添加用户组”。

2. 选择应获取此策略的一个或多个用户组。

    ![突出显示添加用户组选项的已限制用户组边栏选项卡的屏幕截图](../media/mam-ca-spo-restricted-groups.png)

    > [!IMPORTANT] 
    > 你可能希望在上一步中选择的用户组中的某些用户不受此策略影响。 在这种情况下，将用户组添加到被免除的用户组列表。 

3. 在“SharePoint Online”边栏选项卡上，选择“被免除的用户组”，然后选择“添加用户组”以打开用户组列表。

4. 选择要从此策略中免除的组。  

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>从现有的基于应用的 CA 策略中修改或删除用户组

1. 打开“已限制的用户组”边栏选项卡，然后突出显示要删除的用户组。
2. 单击椭圆查看删除选项。
3. 选择“删除”以从列表中删除用户组。

> [!NOTE] 
> 可以按照步骤过程从“被免除的用户组”列表中删除用户组。

## <a name="next-steps"></a>后续步骤

[阻止不使用现代身份验证的应用](block-apps-with-no-modern-authentication.md)

## <a name="see-also"></a>另请参阅

[使用应用保护策略保护应用数据](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[为 Exchange Online 配置基于应用的 CA](mam-ca-for-exchange-online.md)
