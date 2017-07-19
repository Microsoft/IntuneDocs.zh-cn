---
title: "将条件访问策略从 Intune 经典门户迁移到新 Azure 门户。"
titleSuffix: Intune on Azure
description: "将条件访问策略从 Intune 经典门户迁移到新 Azure 门户。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2450a878424d8c992a43e8028ba59b7136e1d530
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2017
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-new-azure-portal"></a>将条件访问策略从 Intune 经典门户重新分配到新 Azure 门户

从新 Azure 门户开始，条件性访问按应用提供多策略支持和更高的可自定义度。

## <a name="before-you-begin"></a>在开始之前

如果准备迁移到新的 Azure 门户，则可以按照以下步骤重新分配先前在 Intune 经典门户中创建的条件性访问策略：

- 收集以前在 Intune 经典门户中创建的条件访问策略，以便了解之后需要重新分配哪些设置。

- 按照本主题中的步骤，在新 Azure 门户中重新创建这些策略。

- 当已验证新策略在新 Azure 门户中按预期工作后，请立即禁用 Intune 经典控制台中的条件策略。
<br /><br />
    - 在 Intune 典门户中“禁用”条件访问策略之前，需先规划如何将用户转移到新策略。 有两种方法：
<br /><br />
        - **使用相同的包含组来应用新 Azure 门户中创建的策略，并创建一个新免除组，以与 Intune 经典门户应用的策略配合使用**。
            - 逐渐将某些用户移动到经典门户中指定的免除组中。  这样可以阻止 Intune 经典门户所面向的且要应用的策略。 除 Intune 经典门户中应用的策略外，还会应用在新 Azure 门户中创建的、针对同一用户组的策略。 
<br /><br />
        - **在新 Azure 门户中创建一个要实施条件性访问策略的新组**。 如果选择此方法，需要执行以下操作：
            - 逐渐从 Intune 经典门户中应用条件性访问策略的安全组中删除用户。
            - 当确认新策略适用于这些用户后，可立即在 Intune 经典门户中禁用该策略。 
<br /><br />
- 如果条件性访问策略设置配置为在 Intune 经典门户中使用 Exchange Active Sync (EAS)，请参阅[本主题中的说明](#to-reassign-intune-device-based-conditional-access-policies-for-eas-clients)，了解如何**重新分配新 Azure 门户中的 EAS 条件性访问策略设置**。

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>验证 Intune 经典门户中基于设备的条件访问策略

1.  转到 [Intune 经典门户](https://manage.microsoft.com)，并用自己的凭据登录。

2.  在左侧菜单中选择“策略” 。

3.  选择“条件性访问” ，然后选择为之创建条件性访问策略的 Microsoft 云服务（Exchange Online、SharePoint Online 等）。

4.  记下条件性访问设置，并将这些记录作为参考，在新 Azure 门户中创建相同的条件性访问策略。

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>配合使用基于应用和基于设备的条件性访问策略

通过使用新 Azure 门户中的“Intune 应用保护”边栏选项卡，管理员可以设置基于应用的条件性规则，以便仅允许支持 Intune 应用保护策略的应用访问公司资源。 可使用基于设备的条件性访问策略覆盖这些基于应用的条件性访问策略。 具体取决于是要结合使用基于设备的和基于应用的条件性策略（逻辑 AND）还是提供一个选项（逻辑 OR）。 如果条件性访问策略要求是：

- 需要兼容设备和（**AND**）使用已批准的应用。
    - 应使用[“Azure AD 条件性访问”边栏选项卡](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)和 [“Intune 应用保护”边栏选项卡](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)来设置条件性访问策略。
<br /><br />
- 需要兼容设备或（**OR**）使用已批准应用。
    - 应使用 [Intune 经典门户](https://manage.microsoft.com)和[“Intune 应用保护”边栏选项卡](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)来设置条件性访问策略。

> [!TIP] 
> 本主题提供一些屏幕截图，用于比较 Intune 经典门户和新 Azure 门户的用户体验。

## <a name="to-re-assign-intune-device-based-conditional-access-policies"></a>重新分配基于设备的 Intune 条件性访问策略

1. 转到[新 Azure 门户中的条件性访问](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)并使用凭据登录。

2. 选择“新策略”。

3. 提供策略的名称。

4. 选择“分配”部分下的“用户和组”以应用新条件访问策略。
    
    ![Intune 经典门户和新 Azure 门户之间的用户组用户界面比较](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > 如果在 Intune 经典门户中选择了所有用户，则会包括所有用户。 这同样适用于组，如果选择了组，则需要选择“选择单个用户和组”以包括这些组。 此外，如果在 Intune 经典门户中，已选择“免除组”选项，则需要在新 Azure 门户中排除所选的这些组。

5. 选择了组后，单击“选择” ，然后单击“完成”。

6. 选择“分配”部分下的“云应用”。

7. 在“云应用”边栏选项卡上，选择“选择应用”。

8. 选择要应用新条件性访问策略的应用，然后单击“选择”。

9. 单击“完成”。

    ![Intune 经典门户和新 Azure 门户之间的云应用用户界面比较](./media/reassign-ca-3.png)

    > [!TIP] 
    > 如果有多个应用具有相同的策略，可考虑在新 Azure 门户中将其并入一个策略。

10. 在“分配”下选择“条件”。

11. 在“条件”边栏选项卡上，选择“设备平台”，然后选择适用的设备平台。

12. 选择完设备平台后，单击两次“完成”。

    ![Intune 经典门户和新 Azure 门户之间的设备平台用户界面比较](./media/reassign-ca-4.png)

    > [!TIP] 
    > 如果已在 Intune 经典门户中选择单个平台，请在新 Azure 门户中选择单个平台。

    > [!NOTE] 
    > 可在以后指定适用于 Windows 的域加入或兼容选项。

13. 在“分配”下选择“条件”。

14. 在“条件”边栏选项卡上，选择“客户端应用”，然后选择适用的客户端应用。

15. 选完客户端应用后，单击两次“完成”。

    ![Intune 经典门户和新 Azure 门户之间的客户端应用用户界面比较](./media/reassign-ca-6.png)

16. 如果已在 Intune 经典门户中选择了浏览器设置，请在新 Azure 门户中，同时选中“浏览器”和“移动应用和桌面客户端”。 在 Intune 经典门户中，如果未选择浏览器设置，则只选择“移动应用和桌面客户端”。 

17. 选择“访问控制”部分下的“授予”。

18. 选择“访问权限授予控制”下的“要求设备标记为兼容”，然后单击“选择”。

19. 如果有一个策略需要加入域的 Windows 设备，但同时需要允许注册了 Intune 的兼容 Windows 设备，请同时选择“需要加入域的设备”、“要求设备标记为兼容”和“需要一个所选控制”。

20. 如果不允许注册了 Intune 的兼容 Windows 设备，则免除当前策略中的 Windows 策略，然后创建一个单独的策略，其中将“设备平台”设置为“Windows”，并按上述方式设置所包含的其他条件，然后选择“访问权限授予控制”下的“需要加入域的设备”。

21. 打开“新建”条件访问策略边栏选项卡上的“启用策略”，然后单击“创建”。

    ![启用 Intune 经典门户和新 Azure 门户之间的 ca 策略用户界面比较](./media/reassign-ca-11.png)

## <a name="to-reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>重新分配用于 EAS 客户端的基于设备的 Intune 条件访问策略

如果已在 Intune 经典门户中将 Exchange Active Sync (EAS) 设置配置为 Exchange Online 策略的一部分，则需要在新 Azure 门户中创建第二个条件性访问策略。

1. 转到[新 Azure 门户中的条件性访问](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)并使用凭据登录。

2. 选择“新策略”。

3. 提供策略的名称。

4. 选择“分配”部分下的“用户和组”以应用新条件访问策略。

    ![Intune 经典门户和新 Azure 门户之间的用户组用户界面比较](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > 如果在 Intune 经典门户中选择了所有用户，则会包括所有用户。 这同样适用于组，如果选择了组，则需要选择“选择单个用户和组”以包括这些组。 此外，如果在 Intune 经典门户中，已选择“免除组”选项，则需要在新 Azure 门户中排除所选的这些组。

5. 选择了组后，单击“选择” ，然后单击“完成”。

6. 选择“分配”部分下的“云应用”。

7. 在“云应用”边栏选项卡上，单击“所选应用”，选择 Exchange Online，单击“选择”，然后单击“完成”。

    ![Intune 经典门户和新 Azure 门户之间的云应用用户界面比较](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > EAS 客户端的条件性访问策略不能包含任何其他云应用。

8. 在“条件”边栏选项卡上，选择“客户端应用”，然后选择适用的客户端应用。 如果选择阻止 Intune 不支持的客户端，请使用选项“仅将策略应用于支持的平台”。

    ![Intune 经典门户和新 Azure 门户之间的客户端应用用户界面比较](./media/reassign-ca-15.png)

9. 选完客户端应用后，单击两次“完成”。

10. 选择“访问控制”部分下的“授予”。

11. 选择“访问权限授予控制”下的“要求设备标记为兼容”，然后单击“选择”。

    ![Intune 经典门户和新 Azure 门户之间的授权访问用户界面比较](./media/reassign-ca-16.png)

12. 打开“新建”条件访问策略边栏选项卡上的“启用策略”，然后单击“创建”。

    ![启用 Intune 经典门户和新 Azure 门户之间的 ca 策略用户界面比较](./media/reassign-ca-17.png)

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>禁用 Intune 经典门户中的条件性访问策略
### <a name="before-you-start"></a>开始之前

一旦在新 Azure 门户中重新分配了条件访问策略，请务必逐渐禁用之前在 Intune 经典门户中创建的条件性访问策略。 此外，可能需要使用同一安全组来应用在新 Azure 门户中创建的条件访问策略

- 在 Intune 经典门户中禁用条件性访问策略之前，请先阅读本主题开头部分的[在开始之前](#before-you-begin)。

### <a name="to-disable-the-conditional-access-policies"></a>禁用条件性访问策略

1.  转到 [Intune 经典门户](https://manage.microsoft.com)，并用自己的凭据登录。

2.  在左侧菜单中选择“策略” 。

3.  选择“条件性访问” ，然后选择为之创建条件性访问策略的 Microsoft 云服务（Exchange Online、SharePoint Online 等）。

4.  取消选中选项“启用条件性访问策略”，然后单击“保存”。

    ![禁用条件性访问策略 Intune 经典门户](./media/reassign-ca-18.png)

## <a name="see-also"></a>另请参阅

- [通过 Intune 使用条件性访问的常见方式](conditional-access-intune-common-ways-use.md)
- [使用 Intune 且基于应用的条件性访问](app-based-conditional-access-intune.md)
- [Azure Active Directory 中的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)