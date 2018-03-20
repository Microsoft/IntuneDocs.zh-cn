---
title: "创建和部署 Windows 信息保护 (WIP) 应用保护策略"
titlesuffix: Microsoft Intune
description: "通过 Microsoft Intune 创建和部署 Windows 信息保护 (WIP) 应用保护策略"
keywords: 
author: Erikre
ms.author: erikre
manager: doubeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4325d77982bcca748a38696fbbbb413a1c304ffb
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>通过 Intune 创建和部署 Windows 信息保护 (WIP) 应用保护策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可将应用保护策略用于 Windows 10 应用，在未注册设备的情况下保护应用。

## <a name="before-you-begin"></a>在开始之前

添加 WIP 策略时，须了解一些相关概念：

### <a name="list-of-allowed-and-exempt-apps"></a>允许和豁免应用列表

-   **允许的应用**：这些应用需要符合此策略。

-   **豁免应用**：这些应用从此策略中豁免，可以无限制地访问公司数据。

### <a name="types-of-apps"></a>应用类型

-   **推荐的应用**：一份预先填写好的应用列表（主要为 Microsoft Office 应用），便于轻松导入策略。
-   应用商店应用：可将 Windows 应用商店中的任何应用添加到策略。
-   Windows 桌面应用：可将任何传统 Windows 桌面应用添加到策略（例如，.exe、.dll）

## <a name="prerequisites"></a>必备条件

必须先配置 MAM 提供程序，然后才可以创建 WIP 应用保护策略。 详细了解[如何通过 Intune 配置 MAM 提供程序](app-protection-policies-configure-windows-10.md)。

此外，还需要具有以下许可证和更新：

-   [Azure AD 高级版](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)许可证
-   [Windows 创意者更新](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP 不支持多标识，一次只能存在一个托管标识。

## <a name="to-add-a-wip-app-protection-policy"></a>添加 WIP 应用保护策略

设置组织中的 Intune 后，可以创建特定于 WIP 的策略。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。
3. 在“Microsoft Intune”边栏选项卡上，选择“移动应用”。
4. 在“移动应用”边栏选项卡上，选择“应用保护策略”。
5. 单击“添加策略”，显示“添加一个策略”边栏选项卡。
6. 添加下列值：
    - **名称：**键入新策略的名称（必填）。
    - **说明：**（可选）键入说明。
    - **平台：**选择“Windows 10”作为应用保护策略的支持平台。
    - **注册状态：**选择“不注册”作为策略的注册状态。
7.  选择“创建”。 创建策略并在“应用保护策略”边栏选项卡的表中显示该策略。

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>将推荐的应用添加到允许的应用列表中

1. 在“Microsoft Intune”边栏选项卡上，选择“移动应用”。
2. 在“移动应用”边栏选项卡上，选择“应用保护策略”。
3. 在“应用保护策略”边栏选项卡上，选择想要修改的策略。 可看到“Intune 应用保护”边栏选项卡。
4. 从“Intune 应用保护”边栏选项卡中选择“受保护的应用”。 随即打开“受保护的应用”边栏选项卡，并显示此应用保护策略列表中已包含的全部应用。
5. 选择“添加应用”。 “添加应用”信息显示筛选后的应用列表。 可使用边栏选项卡顶部的列表更改列表筛选器。
6. 选择要允许其访问公司数据的各个应用。
7. 单击" **确定**"。 “受保护的应用”边栏选项卡会进行更新，并显示已选中的所有应用。
8. 单击 **“保存”**。

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>将“应用商店”应用添加到“允许的应用”列表中

**添加“应用商店”应用**
1. 在“Microsoft Intune”边栏选项卡上，选择“移动应用”。
2. 在“移动应用”边栏选项卡上，选择“应用保护策略”。
3. 在“应用保护策略”边栏选项卡上，选择想要修改的策略。 可看到“Intune 应用保护”边栏选项卡。
4. 从“Intune 应用保护”边栏选项卡中选择“受保护的应用”。 随即打开“受保护的应用”边栏选项卡，并显示此应用保护策略列表中已包含的全部应用。
5. 选择“添加应用”。 “添加应用”信息显示筛选后的应用列表。 可使用边栏选项卡顶部的列表更改列表筛选器。
6. 从列表中，选择“应用商店应用”。
7. 输入“名称”、“发行商”、“产品名称”和“操作”的值。 请确保将“操作”值设为“允许”，使应用可访问公司数据。
9. 单击" **确定**"。 “受保护的应用”边栏选项卡会进行更新，并显示已选中的所有应用。
10. 单击 **“保存”**。

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>将桌面应用添加到“允许的应用”列表中

**添加桌面应用**
1. 在“Microsoft Intune”边栏选项卡上，选择“移动应用”。
2. 在“移动应用”边栏选项卡上，选择“应用保护策略”。
3. 在“应用保护策略”边栏选项卡上，选择想要修改的策略。 可看到“Intune 应用保护”边栏选项卡。
4. 从“Intune 应用保护”边栏选项卡中选择“受保护的应用”。 随即打开“受保护的应用”边栏选项卡，并显示此应用保护策略列表中已包含的全部应用。
5. 选择“添加应用”。 “添加应用”信息显示筛选后的应用列表。 可使用边栏选项卡顶部的列表更改列表筛选器。
6. 从列表中，选择“桌面应用”。
7. 输入“名称”、“发行商”、“产品名称”、“文件”、“最低版本”、“最高版本”和“操作”的值。 请确保将“操作”值设为“允许”，使应用可访问公司数据。
9. 单击" **确定**"。 “受保护的应用”边栏选项卡会进行更新，并显示已选中的所有应用。
10. 单击 **“保存”**。

## <a name="wip-learning"></a>WIP Learning
添加要使用 WIP 保护的应用后，必须使用“WIP Learning” 应用保护模式。

### <a name="before-you-begin"></a>在开始之前

WIP Learning 是一个报表，用于监视已启用 WIP 和 WIP 未知的应用。 未知应用指不是由组织的 IT 部门部署的应用。 在“块”模式下强制执行 WIP 前，可从报告中导出这些应用并将其添加到 WIP 策略，以避免生产力中断。

<!-- 1631908 -->
除了查看已启用 WIP 的应用的相关信息外，还可以查看与网站共享工作数据的设备的摘要。 通过此信息，可以确定应将哪些网站添加到组和用户 WIP 策略中。 摘要显示已启用 WIP 的应用访问的网站 URL。

使用已启用 WIP 和 WIP 未知的应用时，建议对在允许的应用列表上具有相应应用的小组进行验证时，从“无提示”或“允许覆盖”开始。 完成后，可以更改为最终的强制策略“块”。

### <a name="what-are-the-protection-modes"></a>什么是保护模式？

#### <a name="block"></a>阻止
WIP 将查找不正确的数据共享做法并阻止用户完成操作。 这包括在不受公司保护的所有应用中共享信息，以及在组织外部的其他人员和设备之间共享公司数据。

#### <a name="allow-overrides"></a>允许覆盖
WIP 查找不正确的数据共享操作，在用户执行的操作被认为存在潜在危险时，对用户发出警告。 但是，用户可以通过此模式覆盖该策略并共享数据，并将操作记录到审核日志中。

#### <a name="silent"></a>无提示
WIP 以无提示的方式运行，并记录不正确的数据共享操作，但不阻止在“允许覆盖”模式下收到提示进行员工互动的任何操作。 仍然阻止不允许的操作，例如应用以不正确的方式尝试访问网络资源或受 WIP 保护的数据。

#### <a name="off-not-recommended"></a>关闭(不推荐)
关闭 WIP，并且不帮助保护或审核数据。

关闭 WIP 后，将尝试在本地连接的驱动器上解密所有带有 WIP 标记的文件。 请注意，如果重新打开 WIP 保护，不会自动重新应用之前的解密和策略信息。

### <a name="add-a-protection-mode"></a>添加保护模式

1.  在“应用策略”边栏选项卡中，选择策略的名称，然后选择“所需设置”。

    ![Learning 模式屏幕截图](./media/learning-mode-sc1.png)

1.  选择一种设置，然后选择“保存”。

### <a name="use-wip-learning"></a>使用 WIP Learning

1. 打开 [Azure 门户](https://portal.azure.com)。 选择“所有服务”。 在文本框筛选器中键入“Intune”。

3. 选择“Intune” > “移动应用”。

4. 选择“应用保护状态” > “报告” > “Windows 信息保护学习”。  

    WIP 学习日志报告中显示应用后，可以将这些应用添加到应用保护策略中。

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>允许 Windows Search 索引器搜索加密项
允许或不允许项的索引。 此开关适用于 Windows Search 索引器，用于控制是否索引加密项，如受 Windows 信息保护 (WIP) 保护的文件。

此应用保护策略选项位于 Windows 信息保护策略的“高级设置”中。 应用保护策略必须设置为 Windows 10 平台，应用策略“注册状态”必须设置为“已注册”。

启用策略后，即会索引受 WIP 保护的项，且相关元数据存储在未加密位置。 元数据包括文件路径和修改日期等。

禁用策略后，不会索引受 WIP 保护的项，也不会在 Cortana 或文件资源管理器的结果中显示这些项。 如果设备上存在许多受 WIP 保护的媒体文件，可能还会对照片和 Groove 应用产生性能影响。

## <a name="add-encrypted-file-extensions"></a>添加加密文件扩展名

除了设置“允许 Windows Search 索引器搜索加密项”选项外，还可以指定文件扩展名列表。 当从网络位置列表中定义的企业边界内的服务器消息块 (SMB) 共享进行复制时，会对具有这些扩展名的文件进行加密。 如果未指定此策略，则应用现有自动加密行为。 如果已配置此策略，则仅对具有列表中的扩展名的文件进行加密。

## <a name="deploy-your-wip-app-protection-policy"></a>部署 WIP 应用保护策略

> [!IMPORTANT]
> 此信息适用于未注册设备的 WIP。

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

创建 WIP 应用保护策略后，必须使用 MAM 将其部署到组织。

1.  在“应用策略”边栏选项卡上，选择新创建的应用保护策略，然后选择“用户组” > “添加用户组”。

    由 Azure Active Directory 中的所有安全组组成的用户组列表在“添加用户组”边栏选项卡中打开。

2.  选择要向其应用策略的组，然后单击“选择”部署此策略。

## <a name="next-steps"></a>后续步骤

有关 Windows 信息保护的详细信息，请参阅 [Protect your enterprise data using Windows Information Protection (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)（使用 Windows 信息保护 (WIP) 保护企业数据）。
