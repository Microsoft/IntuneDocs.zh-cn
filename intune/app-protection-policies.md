---
title: "创建和部署应用保护策略"
titleSuffix: Azure portal
description: "了解 Intune 应用保护策略如何帮助保护你所管应用使用的公司数据。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4fbb9a1f6697a8339a2854e4352749ca04bb612e
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>如何创建和分配应用保护策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="before-you-begin"></a>开始之前

有关如何在 Intune 经典门户中创建策略的说明，请参阅[如何创建应用保护策略](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)。

无论设备是否由 Intune 托管，都可以将应用保护策略应用到该设备上运行的应用中。 若要详细了解应用保护策略的工作原理以及 Intune 应用保护策略支持的方案，请参阅[什么是 Microsoft Intune 应用保护策略](app-protection-policy.md)。

如果你要查找 MAM 支持应用的列表，请参阅 [MAM 应用列表](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

##  <a name="create-an-app-protection-policy"></a>创建应用保护策略
1.  在“移动应用”工作负荷中，选择“管理” > “应用保护策略”。

2.  将打开“应用保护策略”边栏选项卡，你将在此创建新策略和编辑现有策略。 选择**添加策略**。

  ![“添加策略”边栏选项卡的屏幕截图](./media/app-protection-add-policy.png)

3.  为策略键入名称、添加简要说明并选择平台类型，以便为 iOS 或 Android 创建策略。 可以为每个平台创建多个策略。

4.  选择“应用”以打开“应用”边栏选项卡，其中显示了可用应用的列表。 可从该列表中选择希望与正创建的策略关联的一个或多个应用。 选择应用后，选择“应用”边栏选项卡底部的“选择”以保存选择。

    > [!IMPORTANT]
    > 必须至少选择一个应用才能创建策略。

5.  在“添加策略”边栏选项卡上，选择“配置所需设置”以打开“策略设置”边栏选项卡。

    有两种类别的策略设置：“数据重定位”和“访问”。  数据重定位策略适用于将数据移入和移出应用，而访问策略将决定最终用户在工作环境中如何访问应用。
    为了帮助你入门，策略设置具有默认值。 如果默认值满足你的需求，则无须进行任何更改。

    > [!TIP]
    > 仅在工作环境中使用应用时，才强制执行这些策略设置。  当最终用户使用应用执行个人任务时，他们将不受这些策略影响。



6.  选择“确定”保存此配置。 现将返回“添加策略”  边栏选项卡。 选择“创建”以创建策略并保存设置。


按上述流程完成创建策略后，未将它部署到任何用户。 若要部署策略，请参阅下面的部分，即“将策略部署到用户”。

## <a name="deploy-a-policy-to-users"></a>将策略部署到用户

1.  在“策略”边栏选项卡中，选择“用户组”，随即将打开“用户组”边栏选项卡。 选择“用户组”边栏选项卡中的“添加用户组”，以打开“添加用户组”边栏选项卡。

  ![突出显示“添加用户组”菜单选项的“用户组”边栏选项卡的屏幕截图](./media/app-protection-policy-add-users.png)

2.  用户组列表将显示在“添加用户组”  边栏选项卡上。 这是你“Azure Active Directory” 中所有安全组的列表。 可选择希望将此策略应用于的用户组，然后选择“选择”。 选择“选择”会将策略部署到用户。
  ![显示 Azure Active Directory 用户列表的“添加用户组”边栏选项卡的屏幕截图](./media/azure-ad-user-group-list.png)

你现已创建策略并将其部署到用户。

该策略仅影响分配有 Microsoft Intune 许可证的用户。 所选安全组中未分配有 Microsoft Intune 许可证的用户不会受到影响。

>[!IMPORTANT]
> 如果你使用 Intune 与配置管理器来管理 iOS 和 Android 设备，则该策略将仅应用于直接位于所选组中的用户。 所选组中嵌套子组的成员不会受影响。

最终用户可以从 App Store 或 Google Play 下载应用。 有关详细信息，请参阅：
* [Android 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-android.md)
* [iOS 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>更改现有策略
你可以编辑现有策略并将其应用于目标用户。 但是，当你更改现有策略时，已登录到应用的用户在 8 小时内将看不到更改。

若要立即看到更改的效果，最终用户必须注销应用，然后重新登录。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>更改与策略关联的应用列表的步骤

1.  在“应用策略”边栏选项卡中，选择你想要更改的策略。 将打开特定于刚才所选策略的边栏选项卡。

2.  在该策略边栏选项卡中，选择“目标应用”以打开应用列表。

3.  在列表中删除或添加应用，然后选择“保存”图标以保存所做的更改。

### <a name="to-change-the-list-of-user-groups"></a>更改用户组列表的步骤

1.  在“应用策略”边栏选项卡中，选择你想要更改的策略。 将打开特定于所选策略的边栏选项卡。

2.  在该策略边栏选项卡中，选择“用户组”以打开“用户组”边栏选项卡，其中显示了具有此策略的当前用户组的列表。

3.  若要向策略添加新用户组，请选择“添加用户组”，然后选择用户组。 选择“选择”以将策略部署到所选组。

4.  若要删除用户组，请突出显示要删除的用户组。 然后选择省略号 (…)，并选择“删除”以删除该用户组。
  ![显示“删除”选项的屏幕截图](./media/app-protection-policy-delete-user.png)

### <a name="to-change-policy-settings"></a>更改策略设置的步骤

1.  在“应用策略”边栏选项卡中，选择你想要更改的策略。 将打开特定于刚才所选策略的边栏选项卡。


2.  选择“策略设置”以打开“策略设置”边栏选项卡。

3.  更改设置，然后选择“保存”图标以保存所做的更改。

## <a name="policy-settings"></a>策略设置
若要查看 iOS 和 Android 的策略设置的完整列表，请选择以下值之一：

- [iOS 策略](app-protection-policy-settings-ios.md)
- [Android 策略](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>后续步骤
[监视合规性和用户状态](app-protection-policies-monitor.md)

### <a name="see-also"></a>另请参阅
* [Android 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-android.md)
* [iOS 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-ios.md)
