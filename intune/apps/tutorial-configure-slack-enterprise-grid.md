---
title: 教程 - 配置 Slack 以将 Intune 用于 EMM 和应用配置
titleSuffix: Microsoft Intune
description: 本教程将配置 Slack，以将 Intune 用于 EMM 和应用配置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dce6d71a4bc056146b581458d5c39325adad1584
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206901"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>教程：配置 Slack 以将 Intune 用于 EMM 和应用配置

Slack 是一款可与 Microsoft Intune 结合使用的协作应用。   

在本教程中，你将：
> [!div class="checklist"]
> - 在 Slack Enterprise Grid 上将 Intune 设置为企业移动性管理 (EMM) 提供程序。 你将能够将 Grid 计划的工作区的访问权限限制在 Intune 托管设备。
> - 创建应用配置策略，来管理 iOS 上用于 EMM 的 Slack 应用以及用于 Android 工作配置文件设备的 Slack 应用。
> - 创建 Intune 设备符合性策略以设置 Android 和 iOS 设备必须满足才能被视为符合的条件。

如果没有 Intune 订阅，请[注册免费试用帐户](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件
在本教程中，你将需要一个具有以下订阅的测试租户：
- Azure Active Directory Premium（[免费试用版](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)）
- Intune 订阅（[免费试用](../fundamentals/free-trial-sign-up.md)）

此外，还需要具备 [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-) 计划。

## <a name="configure-your-slack-enterprise-grid-plan"></a>配置 Slack Enterprise Grid 计划
按照 [Slack 指南](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm)为 Slack Enterprise Grid 计划启用 EMM，并[连接 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) 来作为 Grid 计划的标识提供者 (IDP)。

## <a name="sign-in-to-intune"></a>登录到 Intune
以全局管理员或 Intune 服务管理员身份登录 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="set-up-slack-for-emm-on-ios-devices"></a>在 iOS 设备上安装用于 EMM 的 Slack
将用于 EMM 的 Slack 的 iOS 应用添加到 Intune 租户，并创建应用配置策略，从而通过将 Intune 作为 EMM 提供程序来允许组织的 iOS 用户访问 Slack。

### <a name="add-slack-for-emm-to-intune"></a>将用于 EMM 的 Slack 添加到 Intune
将用于 EMM 的 Slack 添加为 Intune 中的托管 iOS 应用，并分配 Slack 用户。 由于应用都是平台特定的应用，因此需要为 Android 设备的 Slack 用户添加单独的 Intune 应用。
1. 在管理中心，选择“应用”   > “所有应用”   > “添加”  。
2. 在“应用类型”下，选择“iOS”商店应用。  
3. 选择“搜索 App Store”  。 输入搜索词“用于 EMM 的 Slack”，选择此应用。 在“搜索 App Store”窗格中单击“选择”。  
4. 选择“应用信息”，并在必要时配置任意更改。  选择“确定”以设置应用信息。 
5. 单击“添加”  。
6. 选择“分配”  。
7. 单击“添加组”  。 可能需要从“分配类型”下选择以下项，具体取决于为 Slack 启用 EMM 时所选的要影响的人员： 
    - **可用于已注册设备**：选择了“所有成员(包括来宾)”时，或
    - **不论是否注册均可使用**：选择了“所有成员(来宾除外)”或“可选”时。
8. 选择“包含的组”，并在“使此应用对所有用户可用”下选择“是”。   
9. 单击“确定”，然后再次单击“确定”以添加组。  
10. 单击 **“保存”** 。

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>为用于 EMM 的 Slack 添加应用配置策略
为 iOS 版用于 EMM 的 Slack 添加应用配置策略。 托管设备的应用配置策略都是特定于平台的，因此需要为 Android 设备的 Slack 用户添加单独的策略。
1. 在管理中心中，选择“应用” >    “应用配置策略” >   “添加” >   “托管设备”。
2. 在“名称”中输入“Slack 应用配置策略测试”。
3. 在“设备注册类型”下，确认设置了“托管设备”。 
4. 在“平台”下，选择“iOS”。 
5. 选择“关联应用”  。
6. 在搜索栏中输入“用于 EMM 的 Slack”，并选择此应用。
7. 单击“确定”，然后选择“配置设置”。   
8. 选择“确定”  ，然后选择“添加”  。
9. 在搜索栏中，输入“Slack 应用配置策略测试”，然后选择刚添加的策略。
10. 在“管理”中选择“分配”  。
11. 在“分配目标”下，选择“所有用户 + 所有设备”。 
12. 单击 **“保存”** 。

### <a name="optional-create-an-ios-device-compliance-policy"></a>（可选）创建 iOS 设备符合性策略
设置 Intune 设备符合性策略以设置设备必须满足才能被视为符合的条件。 在本教程中，我们将为 iOS 设备创建设备符合性策略。 符合性策略都是特定于平台的，因此需要为 Android 设备的 Slack 用户创建单独的策略。
1. 在管理中心中，选择“设备符合性”   > “策略”   > “创建策略”  。
2. 在“名称”中，输入“iOS 符合性策略测试”。
3. 在“描述”中，输入“iOS 符合性策略测试”。
4. 在“平台”下，选择“iOS”。 
5. 选择“设备健康状况”  。 在“已越狱的设备”旁边，选择“块”，然后选择“确定”。  
6. 选择“系统安全”并输入“密码”设置。  对于本教程，选择以下建议的设置：
    - 对于“需要密码才可解锁移动设备”，请选择“需要”。 
    - 对于“简单密码”，请选择“阻止”。 
    - 对于“最短密码长度”，请输入“4”。
    - 对于“所需的密码类型”，请选择“字母数字”。 
    - 对于“屏幕锁定后要求提供密码之前的最大分钟数”，请选择“立即”。 
    - 对于“密码过期(天数)”，请输入“41”。
    - 对于“阻止重用的曾用密码数”，请输入“5”。
7. 单击“确定”  ，然后再次选择“确定”  。
8. 单击 **“创建”** 。

## <a name="set-up-slack-on-android-work-profile-devices"></a>在 Android 工作配置文件设备上安装 Slack
将 Slack 托管的 Google Play 应用添加到 Intune 租户，并创建应用配置策略，从而通过将 Intune 作为 EMM 提供程序来允许组织的 Android 用户访问 Slack。

### <a name="add-slack-to-intune"></a>将 Slack 添加到 Intune
将 Slack 添加为 Intune 中的托管 Google Play 应用，并分配 Slack 用户。 由于应用都是平台特定的应用，因此需要为 iOS 设备的 Slack 用户添加单独的 Intune 应用。
1. 在 Intune 中，选择“应用”   > “所有应用”   > “添加”  。
2. 在“应用类型”下，选择“应用商店应用 - 托管 Google Play”。 
3. 选择“托管 Google Play - 批准”  。 输入搜索词“用于 EMM 的 Slack”，选择此应用。
4. 选择“批准”。 
5. 在搜索栏中输入“Slack”，并选择刚刚添加的应用。
6. 在“管理”中选择“分配”  。
7. 选择“添加组”  。 可能需要从“分配类型”下选择以下项，具体取决于为 Slack 启用 EMM 时所选的要影响的人员： 
    - **可用于已注册设备**：选择了“所有成员(包括来宾)”时，或
    - **不论是否注册均可使用**：选择了“所有成员(来宾除外)”或“可选”时。
8. 选择“包含的组”，并在“使此应用对所有用户可用”下选择“是”。 
9. 单击“确定”，然后再次单击“确定”。  
10. 单击 **“保存”** 。

### <a name="add-an-app-configuration-policy-for-slack"></a>为 Slack 添加应用配置策略
为 Slack 添加应用配置策略。 托管设备的应用配置策略都是特定于平台的，因此需要为 iOS 设备的 Slack 用户添加单独的策略。
1. 在 Intune 中，选择“应用”   > “应用配置策略”   > “添加”  。
2. 在“名称”中输入“Slack 应用配置策略测试”。
3. 在“设备注册类型”下，选择“托管设备”。 
4. 在“平台”下，选择“Android”。 
5. 选择“关联应用”  。
6. 在搜索栏中输入“Slack”，并选择此应用。
7. 选择“确定”，然后选择“配置设置”。  
    - 有关配置密钥及其值的信息，请参阅 [Slack AppConfig 网页](https://www.appconfig.org/company/slack/)的“技术”选项卡中的文档。
8. 单击“确定”  ，然后选择“添加”  。
9. 在搜索栏中，输入“Slack 应用配置策略测试”，然后选择刚添加的策略。
10. 在“管理”中选择“分配”  。
11. 在“分配目标”下，选择“所有用户 + 所有设备”。 
12. 单击 **“保存”** 。

### <a name="optional-create-an-android-device-compliance-policy"></a>（可选）创建 Android 设备符合性策略
设置 Intune 设备符合性策略以设置设备必须满足才能被视为符合的条件。 在本教程中，我们将为 Android 设备创建设备符合性策略。 符合性策略都是特定于平台的，因此需要为 iOS 设备的 Slack 用户创建单独的策略。
1. 在 Intune 中，选择“设备符合性”   > “策略”   > “创建策略”  。
2. 在“名称”中，输入“Android 符合性策略测试”。
3. 在“描述”中，输入“Android 符合性策略测试”。
4. 在“平台”下，选择“Android Enterprise”。 
5. 在“配置文件类型”下，选择“工作配置文件”。 
6. 选择“设备健康状况”  。 在“已取得 root 权限的设备”旁边，选择“块”，然后选择“确定”。  
7. 选择“系统安全”  并输入“密码”  设置。 对于本教程，选择以下建议的设置：
    - 对于“需要密码才可解锁移动设备”，请选择“需要”。 
    - 对于“所需的密码类型”，选择“至少为字母数字”。 
    - 对于“最短密码长度”，请输入“4”。
    - 对于“屏幕锁定后要求提供密码之前的最大分钟数”，请选择“15 分钟”。 
    - 对于“密码过期(天数)”，请输入“41”。
    - 对于“阻止重用的曾用密码数”，请输入“5”。
8. 单击“确定”，然后再次单击“确定”。  
9. 单击 **“创建”** 。

## <a name="launch-slack"></a>启动 Slack

使用你刚刚创建的策略时，尝试登录到你的任意一个工作区的任意 iOS 或 Android 工作配置文件设备都需要注册 Intune。 若要测试此应用场景，请尝试在已注册 Intune 的 iOS 设备上启动用于 EMM 的 Slack，或者在已注册 Intune 的 Android 工作配置文件设备上启动 Slack。 

## <a name="next-steps"></a>后续步骤

在本教程中：
- 在 Slack Enterprise Grid 上将 Intune 设置为企业移动性管理 (EMM) 提供程序。 
- 创建应用配置策略，来管理 iOS 上的用于 EMM 的 Slack以及用于 Android 工作配置文件设备的 Slack 应用。
- 创建 Intune 设备符合性策略以设置 Android 和 iOS 设备必须满足才能被视为符合的条件。

若要详细了解应用配置策略，请参阅 [Microsoft Intune 的应用配置策略](app-configuration-policies-overview.md)。 若要详细了解设备符合性策略，请参阅[在设备上设置规则以允许使用 Intune 访问组织中的资源](../protect/device-compliance-get-started.md)。
