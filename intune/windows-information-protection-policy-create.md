---
title: "通过 Intune 创建和部署 Windows 信息保护 (WIP) 应用保护策略"
titlesuffix: Azure portal
description: "通过 Intune 创建和部署 WIP 应用保护策略"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab0456b58704f17d3dc5885ab5ae6b902c9ef152
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2017
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>通过 Intune 创建和部署 Windows 信息保护 (WIP) 应用保护策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

从 Intune 1704 版本开始，可将应用保护策略用于 Windows 10，在未注册设备的情况下保护应用。

## <a name="before-you-begin"></a>在开始之前

我们来讨论一些添加 WIP 策略的概念。

### <a name="list-of-allowed-and-exempt-apps"></a>允许和豁免应用列表

-   **允许的应用**：这些应用需要符合此策略。

-   **豁免应用**：这些应用从此策略中豁免，可以无限制地访问公司数据。

### <a name="types-of-apps"></a>应用类型

-   推荐的应用：一份预先填写好的应用列表（主要为 Microsoft Office 应用），便于轻松导入策略。 <!---I really don't know what you mean by "easily import into policy"--->

-   应用商店应用：可将 Windows 应用商店中的任何应用添加到策略。

-   Windows 桌面应用：可将任何传统 Windows 桌面应用添加到策略（例如，.exe、.dll）

## <a name="pre-requisites"></a>先决条件

必须先配置 MAM 提供程序，然后才可以创建 WIP 应用保护策略。 详细了解[如何通过 Intune 配置 MAM 提供程序](https://docs.microsoft.com/app-protection-policies-configure-windows-10.md)。

此外，还需要具有以下各项：

-   [Azure AD 高级版](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)许可证。
-   [Windows 创意者更新](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP 不支持多标识，一次只能存在一个托管标识。
<!---Should you be linking to a topic that explains what multi-identity is?--->

## <a name="to-add-a-wip-policy"></a>添加 WIP 策略

设置组织中的 Intune 后，可以通过 [Azure 门户](https://docs.microsoft.com/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies)创建特定于 WIP 的策略。 <!---Is there an azure topic you can use instead of a classic? if not, should this topic be moved into the azure docset?--->

1.  转到“Intune 移动应用程序管理仪表板”，选择“所有设置”>“应用策略”。

2.  在“应用策略”边栏选项卡中，选择“添加一个策略”，然后输入以下值：

    a.  **名称：**键入新策略的名称（必填）。

    b。  **说明：**键入说明（可选）。

    c.  **平台：**选择“Windows 10”作为应用保护策略的支持平台。

    d.  **注册状态：**选择“不注册”作为策略的注册状态。

3.  选择“创建”。 创建策略并在“应用策略”边栏选项卡的表中显示该策略。

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>将推荐的应用添加到允许的应用列表中

1.  在“应用策略”边栏选项卡中，选择策略的名称，然后从“添加一个策略”边栏选项卡中选择“允许的应用”。 随即打开“允许的应用”边栏选项卡，并显示此应用保护策略的列表中已包含的全部应用。

2.  在“允许的应用”边栏选项卡中，选择“添加应用”。 随即打开“添加应用”边栏选项卡，并显示属于该列表的所有应用。

3.  选择要让其访问公司数据的各个应用，然后选择“确定”。 “允许的应用”边栏选项卡会进行更新，并显示已选中的所有应用。

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>将“应用商店”应用添加到“允许的应用”列表中

**添加“应用商店”应用**

1.  在“应用策略”边栏选项卡中，选择策略的名称，然后从显示此应用保护策略列表中已包含的全部应用的菜单中选择“允许的应用”。

2.  在“允许的应用”边栏选项卡中，选择“添加应用”。

3.  在“添加应用”边栏选项卡上的下拉列表中选择“应用商店应用”。 边栏选项卡改为显示用于添加“发布程序”和应用“名称”的框。

4.  键入应用的名称及其发布程序的名称，然后选择“确定”。

    > [!TIP]
    > 以下应用示例中，“发布程序”是 *CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US*，产品“名称”是 *Microsoft.MicrosoftAppForWindows*。

5.  将这些信息输入字段后，选择“确定”将此应用添加到“允许的应用”列表中。

> [!NOTE]
> 若要同时添加多个“应用商店”应用，可以单击应用行末尾的菜单“(…)”，然后继续添加更多应用。 完成后，选择“确定”。

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>将桌面应用添加到“允许的应用”列表中

**添加桌面应用**

1.  在“应用策略”边栏选项卡中，选择策略的名称，然后选择“允许的应用”。 随即打开“允许的应用”边栏选项卡，并显示此应用保护策略列表中已包含的全部应用。

2.  在“允许的应用”边栏选项卡中，选择“添加应用”。

3.  在“添加应用”边栏选项卡上的下拉列表中选择“桌面应用程序”。

4.  将这些信息输入字段后，选择“确定”将此应用添加到“允许的应用”列表中。

> [!NOTE]
> 若要同时添加多个桌面应用，可以单击应用行末尾的菜单“(…)”，然后继续添加更多应用。 完成后，选择“确定”。

## <a name="wip-learning"></a>WIP Learning
<!---You've already defined WIP earlier in the topic. You don't need to keep doing so. --->
添加要使用 WIP 保护的应用后，必须使用“WIP Learning” 应用保护模式。

### <a name="before-you-begin"></a>在开始之前

WIP Learning 是一个报表，用于监视 WIP 未知的应用。 未知应用指不是由组织的 IT 部门部署的应用。 在“块”模式下强制执行 WIP 前，可从报告中导出这些应用并将其添加到 WIP 策略，以避免生产力中断。

对在允许的应用列表上具有相应应用的小组进行验证时，建议从“无提示”或“允许覆盖”开始。 完成后，可以更改为最终的强制策略“块”。

### <a name="what-are-the-protection-modes"></a>什么是保护模式？

#### <a name="block"></a>阻止
WIP 将查找不正确的数据共享做法并阻止用户完成操作。 这包括在不受公司保护的所有应用中共享信息，以及在组织外部的其他人员和设备之间共享公司数据。

#### <a name="allow-overrides"></a>允许覆盖
WIP 查找不正确的数据共享操作，如果用户执行的操作被认为存在潜在危险，将对用户发出警告。 但是，用户可以通过此模式覆盖该策略并共享数据，并将操作记录到审核日志中。

#### <a name="silent"></a>无提示
WIP 以无提示的方式运行，并记录不正确的数据共享操作，但不阻止在“允许覆盖”模式下收到提示进行员工互动的任何操作。 仍然阻止不允许的操作，例如应用以不正确的方式尝试访问网络资源或受 WIP 保护的数据。

#### <a name="off-not-recommended"></a>关闭(不推荐)
关闭 WIP，并且不帮助保护或审核数据。

关闭 WIP 后，将尝试在本地连接的驱动器上解密所有带有 WIP 标记的文件。 请注意，如果重新打开 WIP 保护，不会自动重新应用之前的解密和策略信息。

### <a name="add-a-protection-mode"></a>添加保护模式

1.  在“应用策略”边栏选项卡中，选择策略的名称，然后选择“所需设置”。

    ![Learning 模式屏幕截图](./media/learning-mode-sc1.png)

1.  选择“保存”。

### <a name="use-wip-learning"></a>使用 WIP Learning

1. 打开 Azure 门户。 选择“更多服务”。 在文本框筛选器中键入“Intune”。

3. 选择“Intune” > “移动应用”。

4. 选择“应用保护状态” > “报告” > “Windows 信息保护学习”。  
 
    WIP 学习日志报告中显示应用后，可以将这些应用添加到应用保护策略中。

## <a name="deploy-your-wip-app-protection-policy"></a>部署 WIP 应用保护策略

> [!IMPORTANT]
> 这适用于未注册设备的 WIP。

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

创建 WIP 应用保护策略后，必须使用 MAM 将其部署到组织。

1.  在“应用策略”边栏选项卡上，选择新创建的应用保护策略，然后选择“用户组” > “添加用户组”。

    由 Azure Active Directory 中的所有安全组组成的用户组列表在“添加用户组”边栏选项卡中打开。

1.  选择要向其应用策略的组，然后单击“选择”部署此策略。
