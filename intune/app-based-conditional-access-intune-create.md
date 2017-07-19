---
title: "使用 Intune 且基于应用的条件性访问策略"
description: "本主题介绍如何使用 Intune 配置基于应用的条件性访问策略。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a7f054868d0bae061f348239614f3a40b96a15b1
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2017
---
# <a name="set-up-app-based-conditional-access-policies"></a>设置基于应用的条件性访问策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题就如何为已批准应用列表中的一部分应用设置基于应用的条件性访问策略提供指导。 已批准应用列表包含经由 Microsoft 测试过的应用。

> [!IMPORTANT]
> 本主题演练使用 Exchange Online 添加基于应用的条件性访问策略的步骤，当添加已批准应用列表中的 SharePoint Online、Microsoft Teams 等其他应用时，也可使用相同的步骤。

## <a name="to-create-an-app-based-conditional-access-policy"></a>创建基于应用的条件性访问策略
1.  转到“Azure 门户[](https://portal.azure.com)”，然后使用你的凭据登录。

2.  选择“更多服务”，然后键入 Intune。

3.  选择“Intune 应用保护”。

4.  在“Intune 移动应用程序管理”边栏选项卡中，选择“全部设置”。

5.  在“条件性访问”部分中，选择“Exchange Online”。

    ![显示条件访问部分（其中突出显示 Exchange Online 选项）的设置边栏选项卡的屏幕截图](./media/MAM-conditional-access-1.png)

6. 在“允许的应用”边栏选项卡上，选择“允许支持 Intune 应用策略的应用”选项以便仅允许 Intune 应用保护策略支持的应用能够访问 Exchange Online。 选择此选项时，会显示支持的应用的列表。

    > [!NOTE]
    > 会阻止所有 Exchange Active Sync 邮件客户端（包括 iOS 和 Android 上连接到 Exchange Online 的内置邮件客户端）发送或接收电子邮件。 用户会改为收到一封电子邮件，告知他们需要使用 Outlook 邮件应用。

7. 若要将此策略应用于用户，请打开“已限制的用户组”边栏选项卡，然后选择“添加用户组”。 选择应获取此策略的一个或多个用户组。

    ![突出显示添加用户组选项的已限制用户组边栏选项卡的屏幕截图](./media/mam-ca-add-user-group.png)

8. 你可能希望在上一步中选择的用户组中的某些用户不受此策略影响。 在这种情况下，将用户组添加到被免除的用户组列表。 从“Exchange Online”边栏选项卡，选择“被免除的用户组”。 选择“添加用户组”以打开用户组的列表。 选择要从此策略中免除的组。

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>从现有的基于应用的 CA 策略中修改或删除用户组

1. 打开“已限制的用户组”边栏选项卡，然后突出显示要删除的用户组。
2. 单击椭圆查看删除选项。
3. 选择“删除”以从列表中删除用户组。

## <a name="next-steps"></a>后续步骤
[阻止不具有新式验证的应用](app-modern-authentication-block.md)

### <a name="see-also"></a>另请参阅

[使用应用保护策略保护应用数据](app-protection-policies.md)
