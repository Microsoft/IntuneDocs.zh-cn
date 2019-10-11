---
title: 在 Microsoft Intune 中设置电信费用管理服务 - Azure | Microsoft Docs
titleSuffix: ''
description: 将 Microsoft Intune 与 Saaswedo 电信费用管理服务集成，以在 Android 和 iOS 设备上监视数据使用情况，并设置阈值或限制。
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3e459e4e22c7985e2e68e624c413ce967e1a8ba
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723848"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>设置 Intune 中的电信支出管理服务

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

借助 Intune，可以在组织拥有的移动设备上管理数据使用情况产生的电信费用。 Intune 与 Saaswedo 的 [Datalert 电信费用管理](http://datalert.biz/get-started)集成。 Datalert 是管理电信数据使用情况的实时电信费用管理解决方案。 它可帮助避免 Intune 托管设备产生成本高昂的意外数据和漫游费。

与 Datalert 集成后，可以设置、监视和强制实施漫游和国内数据流量限制。 当限制超出定义的阈值时，会自动触发警报。 还可以将服务配置为针对个人或组应用不同的操作，例如禁用漫游或超出阈值。 Datalert 管理控制台包含显示数据使用情况和监视信息的报告。

下图显示 Intune 如何与 Datalert 集成：

  ![Intune 和 Datalert 集成的图示](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

若要将 Datalert 服务与 Intune 配合使用，需要在 Datalert 和 Intune 中完成一些配置设置。 本文介绍如何：

- 在 Datalert 控制台中配置设置，以将 Datalert 服务连接到 Intune。
- 在 Intune 中确认此连接可用并且已启用它。
- 使用 Intune 将 Datalert 应用添加到设备。
- 关闭 Intune 的 Datalert 服务（可选）。

## <a name="supported-platforms"></a>受支持的平台

- 支持 Knox (Samsung) 的 Android 4.4 及更高版本的设备

  [支持 Knox 的 Android 版本](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0)（打开 Samsung 网站）列出了 Knox 支持的版本。

- iOS 8.0 及更高版本

## <a name="prerequisites"></a>必备条件

- 订阅 Microsoft Intune 和拥有 [Azure 门户](https://portal.azure.com)的访问权限
- [Datalert](http://www.datalert.biz/) 订阅（打开 Datalert 网站）

## <a name="telecom-expense-management-providers"></a>电信费用管理提供商

Intune 与下列电信费用管理提供商集成：

- [Saaswedo Datalert 电信费用管理服务](http://www.datalert.biz/)（打开 Datalert 网站）

## <a name="deploy-the-intune-and-datalert-solution"></a>部署 Intune 和 Datalert 解决方案

### <a name="step-1-connect-the-datalert-service-to-intune"></a>步骤 1：将 Datalert 服务连接到 Intune

1. 使用管理员凭据登录 Datalert 管理控制台。

2. 在控制台中，转到“设置”选项卡 >“MDM 配置”。  

3. 选择“取消阻止”。  “取消阻止”允许你更改或更新页面上的设置。 

4. 在“Intune/Datalert 连接” > “Server MDM”中，选择“Microsoft Intune”。   

5. 对于“Azure AD 域”，请输入 Azure 租户 ID  。 选择“连接”。 

    选择“连接”时，Datalert 服务将与 Intune 连接。  它将确认不存在任何已有的 Datalert 连接。 片刻之后将出现 Microsoft 登录页，随后是 Datalert Azure 身份验证。

6. 在 Microsoft 身份验证页上，选择“接受”  。

    将重定向到 Datalert“谢谢”页，该页会在片刻后关闭  。 Datalert 会验证连接，并在其验证的项旁显示绿色复选标记。 如果验证失败，将看到一条红色消息。 请联系 Datalert 支持以获取帮助。

    下图显示连接成功时出现的绿色复选标记：

      ![显示连接成功的 Datalert 页面](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. 在“Datalert 应用/ADAL 许可”中，将开关设置为“打开”   。 在 Microsoft 身份验证页上，选择“接受”  。

    将重定向到 Datalert“谢谢”页，该页会在片刻后关闭  。 Datalert 会验证连接，并在其验证的项旁显示绿色复选标记。 如果验证失败，将看到一条红色消息。 请联系 Datalert 支持以获取帮助。

    下图显示连接成功时出现的绿色复选标记：

      ![显示连接成功的 Datalert 页面](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. 在“MDM 配置文件管理(可选)”中，将开关设置为“打开”。   此设置允许 Datalert 读取 Intune 中可用的配置文件，以便帮助设置策略。 

    在 Microsoft 身份验证页上，选择“接受”  。

    将重定向到 Datalert“谢谢”页，该页会在片刻后关闭  。 Datalert 会验证连接，并在其验证的项旁显示绿色复选标记。 如果验证失败，将看到一条红色消息。 请联系 Datalert 支持以获取帮助。

    下图显示连接成功时出现的绿色复选标记：

   ![显示连接成功的 Datalert 页面](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>步骤 2：在 Intune 中确认电信费用管理可用

完成步骤 1 后，会自动启用连接。 在 Intune 中，连接状态显示“可用”。  请使用以下步骤确认状态为可用：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。

2. 选择“设备配置” > “电信费用管理”。   查找“可用”  连接状态：

   ![显示 Datalert 连接状态为“活动”的 Intune 页面](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>步骤 3：将 Datalert 应用部署到设备

若要确保仅从组织拥有的线路收集数据使用情况，请务必执行以下操作：

- 在 Intune 中创建设备类别。
- 使 Datalert 应用仅面向组织手机。

此部分说明了这些步骤。

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>创建设备类别和映射到各类别的设备组

根据组织的需求，至少创建两个设备类别，例如，“公司”和“个人”。 然后为每个类别创建动态设备组。 可以根据需要为组织创建更多类别。

若要在 Intune 中创建设备类别，请参阅[将设备映射到组](../enrollment/device-group-mapping.md)。

注册过程中，将向用户显示这些类别（[注册 Android 设备](../enrollment/android-enroll.md)）。 根据用户选择的类别，会将已注册的设备移至相应的设备组。

  ![“添加策略”窗格的屏幕截图](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>将 Datalert 应用添加到 Intune

以下步骤将添加 Datalert 应用。 将以 iOS 为例。 有关这些步骤的详细信息，请参阅[添加应用](../apps/apps-add.md)和[使用作用域标记](../fundamentals/scope-tags.md)。

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，选择“客户端应用” > “应用” > “添加”。    

2. 选择“应用类型”。  例如，对于 iOS，则选择“Store 应用 - iOS”。 

3. 在“搜索 App Store”中，键入“Datalert”，以查找 Datalert 应用。  

4. 选择“Datalert”应用 >“选择”：  

   ![从 App Store 中将 Datalert 应用添加到 Intune 客户端应用](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. 输入任意其他属性，例如应用信息和作用域标记：

   ![输入应用属性，包括名称、描述，在 Intune 中选择操作系统以及对此应用的其他设置](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. 选择“确定” > “添加”，保存所做更改   。 列表将显示 Datalert 应用。

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>将 Datalert 应用分配给公司设备组

1. 在“客户端应用 - 应用”中，选择在上一步中添加的 Datalert 应用。 

2. 选择“分配” > “添加组”   。 选择如何分配此应用。 有关这些设置的详细信息，请参阅[在 Intune 中将应用分配给组](../apps/apps-deploy.md)。

    在这些步骤中，将选择对于该组要将应用安装设置为必需还是可选。 下面的示例显示此安装为必需。 设置为必需时，用户注册设备后则必须安装 Datalert 应用。

   ![“添加策略”窗格的屏幕截图](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>步骤 4：将组织电话线路添加到 Datalert 控制台

现已将 Intune 和 Datalert 服务配置为相互通信。 接下来，将组织付费电话线路添加到 Datalert 控制台。 然后输入阈值和对手机网络或漫游使用情况违规的操作。 可以将公司付费的电话线路手动添加到 Datalert 控制台，或者在 Intune 中注册设备后可以自动添加这些线路。

若要设置这些项目，请转到[为 Microsoft Intune 设置 Datalert](http://www.datalert.fr/microsoft-intune/intune-setup)（打开 Datalert 网站）。 在“设置”  选项卡中，按照设置向导中的步骤操作。

  ![“添加策略”窗格的屏幕截图](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

Datalert 服务现已可用。 它开始监视数据流量，并在超过所配置流量限制的设备上禁用手机网络和漫游数据。

## <a name="end-user-enrollment"></a>最终用户注册

下面的文章可帮助实现最终用户体验：

- [在电信费用管理中注册 iOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [在电信费用管理中注册 Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>关闭 Datalert 服务

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，选择“设备配置” > “电信费用管理”。   
2. 将“启用电信费用管理，并阻止设备上已超出配置的使用率配额的手机网络数据或漫游数据”设置为“禁用”。  
3. 单击“保存”以保存更改  。

> [!IMPORTANT]
> 如果在 Intune 中禁用 Datalert 服务：
>
> - 因为之前违反流量限制而应用到设备的所有操作都将撤消。
> - 将不再阻止用户进行数据访问和漫游。
> - Intune 仍然会接收来自服务的信号，但 Intune 将忽略这些信号。

## <a name="next-steps"></a>后续步骤

可从 Saaswedo 的 Datalert 管理控制台获取数据流量报告。
