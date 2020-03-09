---
title: 演练 - 在 Microsoft Intune 中创建管理模板 - Azure | Microsoft Docs
description: 本教程或演练使用 Microsoft Intune 在 Windows 10 及更高版本的相关设备上配置 Office、Windows 和 Microsoft Edge ADMX 模板。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a96f291203e1513ab89196b26a7802856f90e048
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77688085"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>教程：通过云使用 ADMX 模板和 Microsoft Intune 为 Windows 10 相关设备配置组策略

> [!NOTE]
> 本教程是作为 Microsoft Ignite 的技术研讨会而创建的。 它比典型教程具有更多的先决条件，因为它比较了在 Intune 和本地中使用和配置 ADMX 策略。

组策略管理模板（也称为 ADMX 模板）包含可以在 Windows 10 相关设备（包括电脑）上配置的设置。 其他服务提供了 ADMX 模板设置。 这些设置由包括 Microsoft Intune 在内的移动设备管理 (MDM) 提供程序使用。 例如，可以在 PowerPoint 中打开设计创意，在 Microsoft Edge 中设置主页，在 Internet Explorer 中阻止 ActiveX 控件等。

ADMX 模板可用于以下服务：

- **Microsoft Edge**：通过 [Microsoft Edge 策略文件](https://www.microsoftedgeinsider.com/en-us/enterprise)下载。
- **Office**：通过 [Office 365 ProPlus：Office 2019 和 Office 2016](https://www.microsoft.com/download/details.aspx?id=49030) 下载。
- **Windows**：内置于 Windows 10 OS 中。

有关 ADMX 策略的详细信息，请参阅[了解支持 ADMX 的策略](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)。

在 Microsoft Intune 中，这些模板内置于 Intune 服务中，可用作管理模板配置文件  。 在此配置文件中，你可以配置要包含的设置，然后将此配置文件“分配”给相关设备。

在本教程中，你将：

> [!div class="checklist"]
> * 了解 [Microsoft终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
> * 创建用户组并创建设备组。
> * 将 Intune 中的设置与本地 ADMX 设置进行比较。
> * 创建不同的管理模板，并配置面向不同组的设置。

本实验室结束后，你将具备开始使用 Intune 和 Microsoft 365 管理用户以及部署管理模板的技能。

此功能适用于：

- Windows 10 1703 版及更高版本

## <a name="prerequisites"></a>必备条件

- Microsoft 365 E3 或 E5 订阅，其中包括 Intune 和 Azure Active Directory (AD) Premium。 如果没有 E3 或 E5 订阅，请[免费试用](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide)。

  有关使用不同的 Microsoft 365 许可证可获得的好处的详细信息，请参阅[利用 Microsoft 365 实现企业转型](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)。

- Microsoft Intune 配置为 **Intune MDM 机构**。 有关详细信息，请参阅[设置移动设备管理机构](../fundamentals/mdm-authority-set.md)。

  > [!div class="mx-imgBorder"]
  > ![在租户状态下将 MDM 机构设置为 Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- 在本地 Active Directory 域控制器 (DC) 上：

  1. 将以下 Office 和 Microsoft Edge 模板复制到[中央存储（SYSVOL 文件夹）](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra)：

      - [Office 管理模板](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Microsoft Edge 管理模板 > 策略文件](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. 创建一个组策略，将这些模板推送到与 DC 位于同一域中的 Windows 10 Enterprise 管理员计算机。 在本教程中：

      - 使用这些模板创建的组策略称为 **OfficeandEdge**。 你将在映像中看到此名称。
      - 我们使用的 Windows 10 Enterprise 管理员计算机称为**管理员计算机**。

      在某些组织中，域管理员有两个帐户：一个典型的域工作帐户和一个仅用于域管理员任务（例如组策略）的其他域管理员帐户。

      此管理员计算机用于让管理员使用其域管理员帐户登录，并使用专为管理组策略而设计的工具  。

- 在此**管理员计算机上**：

  - 使用域管理员帐户登录。

  - 安装“RSAT:  组策略管理工具”：

    1. 打开“设置”应用 >“应用” > “可选功能” > “添加功能”     。
    2. 选择“RSAT:  组策略管理工具” > “安装”  。

        等待 Windows 安装该功能。 完成后，它最终会显示在 Windows 管理工具应用中  。

        > [!div class="mx-imgBorder"]
        > ![Windows 管理工具应用，包括组策略管理应用](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - 确认你是否拥有 Internet 访问权限和 Microsoft 365 订阅的管理员权限，其中包括终结点管理器管理中心。

## <a name="open-the-endpoint-manager-admin-center"></a>打开终结点管理器管理中心

1. 打开 chromium web 浏览器，例如 Microsoft Edge 77 版及更高版本。
2. 转到 [Microsoft终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431) (https://devicemanagement.microsoft.com) 。 使用以下帐户登录：

    **用户**：输入 Microsoft 365 租户订阅的管理员帐户。  
    **密码**：输入其密码。

此管理中心侧重于设备管理，包括 Azure AD 和 Intune 等 Azure 服务。 你可能看不到 Azure Active Directory 和 Intune 商标，但你正在使用它们   。

你也可以通过 [Microsoft 365 管理中心](https://admin.microsoft.com)打开终结点管理器管理中心：

1. 转到 [https://admin.microsoft.com](https://admin.microsoft.com)。
2. 使用 Microsoft 365 租户订阅的管理员帐户登录。
3. 在“管理中心”下，选择“所有管理中心” > “终结点管理”    。 随即打开终结点管理器管理中心。

    > [!div class="mx-imgBorder"]
    > ![查看 Microsoft 365 管理中心的所有管理中心](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>创建组并添加用户

本地策略按 LSDOU 顺序（本地、站点、域和组织单位 (OU)）应用。 在此层次结构中，OU 策略覆盖本地策略，域策略覆盖站点策略，依此类推。

在 Intune 中，策略将应用于你创建的用户和组。 不存在层次结构。 如果两个策略更新相同的设置，则该设置将显示为冲突。 如果两个合规性策略发生冲突，则应用其中较严格的策略。 如果两个配置文件发生冲突，则不会应用此设置。 有关详细信息，请参阅[设备策略和配置文件的常见疑问、问题和解决方案](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied)。

在接下来的这些步骤中，你将创建安全组，并将用户添加到该组。 可以将一名用户添加到多个组。 例如，一名用户拥有多台设备（例如用于工作的 Surface Pro 和用于个人的 Android 移动设备）是正常的。 而且，通常人们可以从这些多台设备访问组织资源。

1. 在终结点管理器管理中心，选择“组” > “新建组”   。

2. 输入以下设置：

    - **组类型**：选择“安全性”  。
    - **组名称**：输入“所有 Windows 10 学生设备”  。
    - **成员身份类型**：选择“已分配”  。

3. 选择“成员”并添加一些设备  。

    添加设备是可选的。 目的是练习创建组，并了解如何添加设备。 如果你在生产环境中使用本教程，请注意你正在执行的操作。

4. 选择“选择” > “创建”以保存所做的更改   。

    看不到你的组？ 选择“刷新”  。

5. 选择“新组”并输入以下设置  ：

    - **组类型**：选择“安全性”  。
    - **组名称**：输入“所有 Windows 设备”  。
    - **成员身份类型**：选择“动态设备”  。
    - **动态设备成员**：配置查询：

        - **属性**：选择“deviceOSType”  。
        - **运算符**：选择“等于”  。
        - **值**：输入“Windows”  。

        1. 选择“添加表达式”  。 表达式显示在规则语法中  ：

            > [!div class="mx-imgBorder"]
            > ![创建动态查询，并在 Microsoft Intune 管理模板中添加表达式](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            用户或设备满足输入的条件时，会自动将其添加到动态组。 在此示例中，当操作系统为 Windows 时，设备自动添加到此组。 如果你在生产环境中使用本教程，请务必小心。 目的是练习创建动态组。

        2. 选择“保存” > “创建”以保存更改   。

6. 使用以下设置创建“所有教师”组  ：

    - **组类型**：选择“安全性”  。
    - **组名称**：输入“所有教师”  。
    - **成员身份类型**：选择“动态用户”  。
    - **动态用户成员**：配置查询：

      - **属性**：选择“部门”  。
      - **运算符**：选择“等于”  。
      - **值**：输入“教师”  。

        1. 选择“添加表达式”  。 表达式显示在“规则语法”中  。

            用户或设备满足输入的条件时，会自动将其添加到动态组。 在此示例中，当用户的部门为教师时，用户自动添加到此组。 将用户添加到组织中后，可以输入部门和其他属性。 如果你在生产环境中使用本教程，请务必小心。 目的是练习创建动态组。

        2. 选择“保存” > “创建”以保存更改   。

### <a name="talking-points"></a>论据

- 动态组是 Azure AD Premium 中的一项功能。 如果没有安装 Azure AD Premium，则只可以创建已分配的组。 有关动态组的详细信息，请参阅：

  - [Azure Active Directory 中的动态组成员资格（第 1 部分）](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/)
  - [Azure Active Directory 中的动态组成员资格（第 2 部分）](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/)

- Azure AD Premium 包括管理应用和设备时常用的其他服务，包括[多重身份验证 (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) 和[条件访问](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)。

- 许多管理员询问何时使用用户组以及何时使用设备组。 若要获取相关指南，请参阅[用户组与设备组](device-profile-assign.md#user-groups-vs-device-groups)。

- 请记住，一个用户可以属于多个组。 请考虑你可以创建的一些其他动态用户和设备组，例如：

  - 所有学生
  - 所有 Android 设备
  - 所有 iOS/iPadOS 设备
  - “营销”
  - 人力资源
  - 所有 Charlotte 员工
  - 所有位于 Redmond 的员工
  - 西海岸 IT 管理员
  - 东海岸 IT 管理员

在 [Microsoft 365 管理中心](https://admin.microsoft.com)、Azure 门户中的 Azure AD 和 [Azure 门户中的 Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中也可以查看创建的用户和组。 可以在所有这些区域中为租户订阅创建和管理组。 如果你的目标是设备管理，请使用 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)  。

### <a name="review-group-membership"></a>查看组成员身份

1. 在终结点管理器管理中心，选择“用户”，再选择任何现有用户的名称  。

    > [!div class="mx-imgBorder"]
    > ![在终结点管理器管理中心，选择“用户”](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. 查看可以添加或更改的某些信息。 例如，查看可配置的属性，例如职务、部门、城市、办公室位置等。 创建动态组时，可以在动态查询中使用这些属性。
3. 选择“组”以查看此用户的成员身份  。 还可以从组中删除用户。
4. 选择一些其他选项，以查看详细信息以及可执行的操作。 例如，查看分配的许可证、用户的设备等。

### <a name="what-did-i-just-do"></a>内容回顾

在终结点管理器管理中心，你创建了新的安全组，并将现有用户和设备添加到了这些组中。 在本教程的后续步骤中，我们将使用这些组。

## <a name="create-a-template-in-intune"></a>在 Intune 中创建模板

在本部分中，我们将在 Intune 中创建一个管理模板，查看“组策略管理”中的某些设置，并比较 Intune 中的相同设置  。 目的是在组策略中显示设置，并在 Intune 中显示相同的设置。

1. 在终结点管理器管理中心，选择“设备” > “配置文件” > “创建配置文件”    。
2. 输入以下属性：

    - **名称**：输入配置文件的描述性名称。 为配置文件命名，以便稍后可以轻松地识别它们。 例如，输入 **“管理模板 - Windows 10 学生设备”** 。
    - **描述**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Windows 10 及更高版本”  。
    - **配置文件类型**：选择“管理模板”  。

3. 选择“创建”。  在“选择类别”下拉列表中，选择“所有产品”   。 会显示所有设置。 在这些设置中，请注意以下属性：

    - 策略路径  与组策略管理或 GPEdit 相同。
    - 设置适用于用户或设备。

### <a name="open-group-policy-management"></a>打开组策略管理

在本部分中，我们将在 Intune 中显示策略，并在组策略管理编辑器中显示其匹配策略。

#### <a name="compare-a-device-policy"></a>比较设备策略

1. 在“管理员计算机”上，打开“组策略管理”应用   。

    此应用将与“RSAT:  组策略管理工具”一起安装，你可以选择在 Windows 上安装该工具。 （本文中的）[先决条件](#prerequisites)列出了安装此功能的步骤。

2. 展开“域”> 选择你的域  。 例如，选择“contoso.net”  。
3. 右键单击“OfficeandEdge”策略 >“编辑”   。 这将打开组策略管理编辑器应用。

    > [!div class="mx-imgBorder"]
    > ![右键单击 Office 和 Edge ADMX 组策略，然后选择“编辑”](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    OfficeandEdge 是包含 Office 和 Microsoft Edge ADMX 模板的组策略  。 （本文中的）[先决条件](#prerequisites)介绍了此策略。

4. 展开“计算机配置” > “策略” > “管理模板” > “控制面板” > “个性化”      。 请注意可用的设置。

    > [!div class="mx-imgBorder"]
    > ![在组策略管理编辑器中展开“计算机配置”，然后转到“个性化”](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    双击“阻止启用锁屏界面相机”，并查看可用选项  ：

    > [!div class="mx-imgBorder"]
    > ![请参阅组策略中的“计算机配置设置”选项](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png)

5. 在设备管理管理中心，转到“管理模板 - Windows 10 学生设备”模板  。
6. 从下拉列表中选择“所有产品”，然后搜索“个性化”   ：

    > [!div class="mx-imgBorder"]
    > ![在 Microsoft Intune 的管理模板中搜索个性化](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    请注意可用的设置。

    设置类型为“设备”，路径为 \Control Panel\Personalization   。 此路径与你在组策略管理编辑器中看到的路径类似。 如果打开设置，则会在组策略管理编辑器中看到相同的“未配置”、“已启用”和“已禁用”选项    。

#### <a name="compare-a-user-policy"></a>比较用户策略

1. 在管理模板中，搜索“Inprivate 浏览”  。 请注意路径，并且此设置适用于所有用户和设备。

2. 在“组策略管理编辑器”中，查找匹配的用户和设备设置  ：

    - 设备：展开“计算机配置”   > “策略”   > “管理模板”   > “Windows 组件”   > “Internet Explorer”   > “隐私”   >   “关闭 InPrivate 浏览”。
    - 用户：展开“用户配置”   > “策略”   > “管理模板”   > “Windows 组件”   > “Internet Explorer”   > “隐私”   >   “关闭 InPrivate 浏览”。

    > [!div class="mx-imgBorder"]
    > ![使用 ADMX 模板关闭 Internet Explorer 中的 InPrivate 浏览](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> 若要查看内置的 Windows 策略，还可以使用 GPEdit（编辑组策略应用  ）。

#### <a name="compare-an-edge-policy"></a>比较 Edge 策略

1. 在设备管理管理中心，转到“管理模板 - Windows 10 学生设备”模板  。
2. 从下拉列表中选择 Edge 77 版及更高版本  。
3. 搜索“启动”  。 请注意可用的设置。
4. 在“组策略管理编辑器”中，查找以下设置：

    - 设备：展开“计算机配置”   > “策略”   > “管理模板”   > “Microsoft Edge”   >   “启动”、“主页”和“新建”选项卡页。
    - 用户：展开“用户配置”   > “策略”   > “管理模板”   > “Microsoft Edge”   >   “启动”、“主页”和“新建”选项卡页

### <a name="what-did-i-just-do"></a>内容回顾

你在 Intune 中创建了管理模板。 在此模板中，我们查看了一些 ADMX 设置，并在组策略管理中查看了相同的 ADMX 设置。

## <a name="add-settings-to-the-students-admin-template"></a>向学生管理模板添加设置

在此模板中，我们将配置一些 Internet Explorer 设置，以锁定由多名学生共享的设备。

1. 在“管理模板 - Windows 10 学生设备”中，搜索“关闭 InPrivate 浏览”，并选择设备策略   ：

    > [!div class="mx-imgBorder"]
    > ![在 Microsoft Intune 的管理模板中关闭 InPrivate 浏览设备策略](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. 在此窗口中，请注意可以设置的描述和值。 这些选项与你在组策略中看到的选项类似。
3. 选择“已启用” > “确定”，保存所做更改   。
4. 同时配置以下 Internet Explorer 设置。 确保选择“确定”，以保存所做更改  。

    - **允许拖放文件或复制并粘贴文件**
      - **类型**：设备
      - **路径**：\Windows Components\Internet Explorer\Internet Control Panel\Security Page\Internet Zone
      - **值**：已禁用

    - **防止忽略证书错误**
      - **类型**：设备
      - **路径**：\Windows Components\Internet Explorer\Internet Control Panel
      - **值**：Enabled

    - **禁用更改主页设置**
      - **类型**：用户
      - **路径**：\Windows Components\Internet Explorer
      - **值**：Enabled
      - **主页**：输入 URL，如 `contoso.com`。

5. 清除搜索筛选器。 请注意，配置的设置在顶部列出：

    > [!div class="mx-imgBorder"]
    > ![配置的设置在 Microsoft Intune 的顶部列出](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>分配模板

1. 在模板中，选择“分配”  。 可能需要关闭模板，然后从“设备 - 配置文件”列表中选择模板  ：

    > [!div class="mx-imgBorder"]
    > ![从 Microsoft Intune 中的设备配置文件列表中选择管理模板配置文件](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. 选择“选择要包含的组”  。 随即显示现有用户和组的列表。
3. 选择之前创建的“所有 Windows 10 学生设备”组，然后选择“选择”   。

    如果你在生产环境中使用本教程，请考虑添加空的组。 目的是练习分配模板。

4. 单击“保存”以保存更改  。

保存配置文件后，配置文件将在设备通过 Intune 签入时立即应用到设备。 如果设备已连接到 Internet，则可能会立即发生。 有关策略刷新时间的详细信息，请参阅[分配设备后多长时间才能获得策略、配置文件或应用](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)。

分配严格或限制性策略和配置文件时，请勿自行锁定。请考虑创建从策略和配置文件中排除的组。 这样做是为了可以进行故障排除。 监视此组以确认正在按预期方式使用它。

### <a name="what-did-i-just-do"></a>内容回顾

在终结点管理器管理中心，你已创建了管理模板设备配置文件，并将此配置文件分配了给创建的组。

## <a name="create-a-onedrive-template"></a>创建 OneDrive 模板

在本部分中，你将在 Intune 中创建 OneDrive 管理模板来控制某些设置。 选择这些特定设置是因为它们是组织常用的设置。

1. 创建其他配置文件（“设备” > “配置文件” > “创建配置文件”    ）。

2. 输入以下属性：

    - **名称**：输入“管理模板 - 适用于所有 Windows 10 用户的 OneDrive 策略”  。
    - **描述**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Windows 10 及更高版本”  。
    - **配置文件类型**：选择“管理模板”  。

3. 选择“创建”。 
4. 从下拉列表中选择“Office”  。
5. 启用以下设置  。 确保选择“确定”，以保存所做更改  。

    - **用户使用其 Windows 凭据以无提示的方式登录到 OneDrive 同步客户端**
    - **按需使用 OneDrive 文件**
    - **阻止用户同步个人 OneDrive 帐户**

设置如下所示：

> [!div class="mx-imgBorder"]
> ![在 Microsoft Intune 中创建 OneDrive 管理模板](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

有关 OneDrive 客户端设置的详细信息，请参阅[使用组策略控制 OneDrive 同步客户端设置](https://docs.microsoft.com/onedrive/use-group-policy)。

### <a name="assign-your-template"></a>分配模板

1. 在模板中，选择“分配”  。
2. 选择“选择要包含的组”  。 随即显示现有用户和组的列表。
3. 选择之前创建的“所有 Windows 设备”组，然后选择“选择”   。

    如果你在生产环境中使用本教程，请考虑添加空的组。 目的是练习分配模板。

4. 单击“保存”以保存更改  。

此时，你创建了一些管理模板，并将其分配给了创建的组。 下一步是使用 Windows PowerShell 和适用于 Intune 的 Microsoft Graph API 创建管理模板。

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>可选：使用 PowerShell 和图形 API 创建策略

本部分使用以下资源。 我们将在本部分中将安装这些资源。

- [Intune PowerShell SDK](https://github.com/microsoft/Intune-PowerShell-SDK)
- [适用于 Intune的 Microsoft Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. 在“管理员计算机”上，以管理员身份打开 Windows PowerShell   ：

    1. 在搜索栏中，输入“powershell”  。
    2. 右键单击“Windows PowerShell” > “以管理员身份运行”   。

    > [!div class="mx-imgBorder"]
    > ![以管理员身份运行 Windows PowerShell](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. 获取并设置执行策略。

    1. 输入：`get-ExecutionPolicy`

        记下设置的内容，这可能受到限制  。 完成本教程后，请将其设置回其原始值。

    2. 输入：`Set-ExecutionPolicy -ExecutionPolicy Unrestricted`

    3. 输入 `Y` 以更改它。

    PowerShell 的执行策略有助于防止执行恶意脚本。 有关详细信息，请参阅[关于执行策略](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)。

3. 输入：`Install-Module -Name Microsoft.Graph.Intune`

    输入 `Y`，适用于以下情况：

    - 要求安装 NuGet 提供程序
    - 要求从不受信任的存储库安装模块

    这可能需要几分钟时间才能完成。 完成后，系统将显示类似于以下提示的提示：

    > [!div class="mx-imgBorder"]
    > ![安装模块后出现 Windows PowerShell 提示](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. 在 Web 浏览器中，转到 [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases)，并选择“Intune-PowerShell-SDK_v6.1907.00921.0001.zip”文件  。

    1. 选择“另存为”，然后选择要记住的文件夹  。 `c:\psscripts` 是一个不错的选择。
    2. 打开文件夹，右键单击 .zip 文件 >“提取所有” > “提取”   。 文件夹结构与以下文件夹的结构类似：

        > [!div class="mx-imgBorder"]
        > ![解压缩后的 Intune PowerShell SDK 文件夹结构](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. 在“查看”选项卡上，选中“文件扩展名”   ：

    > [!div class="mx-imgBorder"]
    > ![在资源管理器中的“视图”选项卡上选择文件扩展名](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. 在文件夹中，然后转到 `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`。 右键单击每个 .dll >“属性” > “取消阻止”   。

    > [!div class="mx-imgBorder"]
    > ![取消阻止 Dll](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. 在 Windows PowerShell 应用中，输入  ：

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    如果系统提示从不受信任的发行商运行，请输入 `R`。

8. Intune 管理模板使用 Graph 的 beta 版本：

    1. 输入：`Update-MSGraphEnvironment -SchemaVersion 'beta'`

    2. 输入：`Connect-MSGraph -AdminConsent`

    3. 系统出现提示时，请使用相同的 Microsoft 365 管理员帐户登录。 这些 cmdlet 在租户组织中创建策略。

        **用户**：输入 Microsoft 365 租户订阅的管理员帐户。  
        **密码**：输入其密码。

    4. 选择“接受”  。

9. “测试配置文件”配置文件  。 输入：

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    如果这些 cmdlet 成功，则会创建配置文件。 若要确认，请转到 Endpoint Manager管理中心 >“配置文件”  。 应列出“测试配置”配置文件  。

10. 获取所有 SettingDefinitions。 输入：

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. 使用设置显示名称查找定义 ID。 输入：

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. 配置设置。 输入：

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>查看策略

1. 在终结点管理器管理中心，转到“配置文件” > “刷新”   。
2. 选择“测试配置”配置文件 >“设置”   。
3. 在下拉列表中，选择“所有产品”  。

你将看到配置了“用户使用其 Windows 凭据以无提示的方式登录到 OneDrive 同步客户端”设置  。

## <a name="policy-best-practices"></a>策略最佳做法

在 Intune 中创建策略和配置文件时，需要考虑一些建议和最佳做法。 有关详细信息，请参阅[策略和配置文件最佳做法](device-profile-create.md#recommendations)。

## <a name="clean-up-resources"></a>清理资源

不再需要这些资源时，可以执行以下操作：

- 删除创建的组：

  - **所有 Windows 10 学生设备**
  - **所有 Windows 设备**
  - **所有教师**

- 删除创建的管理模板：

  - **管理模板 - Windows 10 学生设备**
  - **管理模板 - 适用于所有 Windows 10 用户的 OneDrive 策略**
  - **测试配置**

- 将 Windows PowerShell 执行策略设置回其原始值。 下面的示例将执行策略设置为受限：

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>后续步骤

在本教程中，你更加熟悉了 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，使用查询生成器创建了动态组，并在 Intune 中创建了管理模板来配置 [ADMX 设置](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)。 你还通过 Intune 比较了在本地和在云中使用 ADMX 模板的情况。 意外收获是，你使用 PowerShell cmdlet 创建了管理模板。

有关 Intune 中的管理模板的详细信息，请参阅：

> [!div class="nextstepaction"]
> [使用 Windows 10 模板在 Intune 中配置组策略设置](administrative-templates-windows.md)
