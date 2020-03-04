---
title: 创建和部署应用保护策略
titleSuffix: Microsoft Intune
description: 本主题介绍如何创建并分配 Microsoft Intune 应用保护策略 (APP)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 662c60b8eb5295997f3c37a02ea23771cf1abaa9
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781285"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>如何创建和分配应用保护策略

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

了解如何为组织中的用户创建和分配 Microsoft Intune 应用保护策略 (APP)。 本主题还介绍如何对现有策略进行更改。

## <a name="before-you-begin"></a>在开始之前

无论设备是否由 Intune 托管，都可以将应用保护策略应用到该设备上运行的应用中。 若要详细了解应用保护策略的工作原理以及 Intune 应用保护策略支持的方案，请参阅[什么是 Microsoft Intune 应用保护策略？](app-protection-policy.md)

如果你要查找 MAM 支持应用的列表，请参阅 [MAM 应用列表](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

有关将组织的业务线 (LOB) 应用添加到 Microsoft Intune 以准备应用保护策略的信息，请参阅[将应用添加到 Microsoft Intune](apps-add.md)。

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>面向 iOS/iPadOS 和 Android 应用的应用保护策略

为 iOS/iPadOS 和 Android 应用创建应用保护策略时，需遵循新式 Intune 流程，生成新的应用保护策略。

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>创建 iOS/iPadOS 或 Android 应用保护策略
1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 在 Intune 门户中，选择“应用” > “应用保护策略”   。 此选项会打开“应用保护策略”  详细信息，可在此创建新策略和编辑现有策略。
3. 选择“创建策略”，然后选择“iOS/iPadOS”或“Android”    。 将显示“创建策略”窗格  。
4. 在“基本信息”页上，添加以下值  ：

    | 值 | 说明 |
    |--------------|------------------------------------------------|
    | 名称 | 此应用保护策略的名称。 |
    | 说明 | [可选]此应用保护策略的说明。 |


    根据前置选择设置“平台”值  。

    ![“创建策略”窗格“基本信息”页的屏幕截图](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. 单击“下一步”以显示“应用”页面   。<br>
    通过“应用”页面，可以选择如何将此策略应用于不同设备上的应用  。 必须添加至少一个应用。<p>
    
    | 值/选项 | 说明 |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 面向所有类型的设备上的应用 | 使用此选项使策略面向处于任何管理状态的设备上的应用。 选择“否”以面向特定类型的设备上的应用  。 有关信息，请参阅[根据设备管理状态设置应用保护策略的适用对象](#target-app-protection-policies-based-on-device-management-state) |
    |     设备类型 | 使用此选项指定此策略适用于 MDM 受管理设备还是非托管的设备。 对于 iOS/iPadOS 应用策略，请从“非管理”  和“受管理”  设备中选择。 对于 Android 应用策略，请从“非托管”、“Android 设备管理员”和“Android Enterprise”中选择    。  |
    | 公共应用 | 单击“选择公共应用”以选择要面向的应用  。 |
    | 自定义应用 | 单击“选择自定义应用”，根据捆绑包 ID 选择要面向的自定义应用  。 |
    
    你选择的应用将显示在“公共和自定义应用”列表中。 
6. 单击“下一步”以显示“数据保护”页面   。<br>
    此页提供数据丢失预防 (DLP) 控件的设置，包括剪切、复制、粘贴和另存为限制。 这些设置决定了用户如何与应用此保护策略的应用中的数据进行交互。

    **数据保护设置**：<br>
    - **iOS/iPadOS 数据保护** - 有关信息，请参阅 [iOS/iPadOS 应用保护策略设置 - 数据保护](~/apps/app-protection-policy-settings-ios.md#data-protection)。
    - **Android 数据保护** - 有关信息，请参阅 [Android 应用保护策略设置 - 数据保护](~/apps/app-protection-policy-settings-android.md#data-protection)。

7. 单击“下一步”以显示“访问要求”页面   。<br>
    此页提供设置，允许你配置用户在工作上下文中访问应用程序所必须满足的 PIN 和凭据要求。 
 
    **访问要求设置** ：<br>
    - **iOS/iPadOS 访问要求** - 有关信息，请参阅 [iOS/iPadOS 应用保护策略设置 - 访问要求](~/apps/app-protection-policy-settings-ios.md#access-requirements)。
    - **Android 访问要求** - 有关信息，请参阅 [Android 应用保护策略设置 - 访问要求](~/apps/app-protection-policy-settings-android.md#access-requirements)。

8. 单击“下一步”以显示“条件启动”页面   。<br>
    此页提供设置以设置应用保护策略的登录安全要求。 选择“设置”，然后输入用户登录公司应用时必须满足的值   。 请选择用户不符合要求时要采取的操作  。 在某些情况下，可为单个设置配置多项操作。

    **条件启动设置** ：<br>
    - **iOS/iPadOS 条件启动** - 有关信息，请参阅 [iOS/iPadOS 应用保护策略设置 - 条件启动 ](~/apps/app-protection-policy-settings-ios.md#conditional-launch)。
    - **Android 条件启动** - 有关信息，请参阅 [Android 应用保护策略设置 - 条件启动 ](~/apps/app-protection-policy-settings-android.md#conditional-launch)。

9. 单击“下一步”以显示“分配”页面   。<br>
   通过“分配”页面，可以将应用保护策略分配到用户组  。

10. 单击“**下一步:** 查看 + 创建”，查看为此应用保护策略输入的值和设置。

11. 完成后，单击“创建”以在 Intune 中创建应用保护策略  。 

    > [!TIP]
    > 仅在工作环境中使用应用时，才强制执行这些策略设置。 最终用户使用应用执行个人任务时，不受这些策略的影响。 请注意，创建新文件时，会将该文件视为个人文件。 

最终用户可以从 App Store 或 Google Play 下载应用。 有关详情，请参阅：
* [Android 应用由应用保护策略托管时会出现的情况](../fundamentals/end-user-mam-apps-android.md)
* [iOS/iPadOS 应用由应用保护策略托管时会出现的情况](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>更改现有策略
你可以编辑现有策略并将其应用于目标用户。 但是，更改现有策略时，已登录到应用的用户在 8 小时内将看不到更改。

若要立即看到更改的效果，最终用户必须注销应用，然后重新登录。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>更改与策略关联的应用列表的步骤

1. 在“应用保护策略”窗格中，选择要修改的策略  。

2. 在“Intune 应用保护”  窗格中，选择“属性”  。

3. 在标题为“应用”  的部分旁边，选择“编辑”  。

4. 通过“应用”页面，可以选择如何将此策略应用于不同设备上的应用  。 必须添加至少一个应用。<p>
    
    | 值/选项 | 说明 |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 面向所有类型的设备上的应用 | 使用此选项使策略面向处于任何管理状态的设备上的应用。 选择“否”以面向特定类型的设备上的应用  。 有关信息，请参阅[根据设备管理状态设置应用保护策略的适用对象](#target-app-protection-policies-based-on-device-management-state) |
    |     设备类型 | 使用此选项指定此策略适用于 MDM 受管理设备还是非托管的设备。 对于 iOS/iPadOS 应用策略，请从“非管理”  和“受管理”  设备中选择。 对于 Android 应用策略，请从“非托管”、“Android 设备管理员”和“Android Enterprise”中选择    。  |
    | 公共应用 | 单击“选择公共应用”以选择要面向的应用  。 |
    | 自定义应用 | 单击“选择自定义应用”，根据捆绑包 ID 选择要面向的自定义应用  。 |

    你选择的应用将显示在“公共和自定义应用”列表中。 

5. 单击“查看 + 创建”  以查看为此策略选择的应用。

6. 完成后，单击“保存”以更新应用保护策略  。
 
#### <a name="to-change-the-list-of-user-groups"></a>更改用户组列表的步骤

1. 在“应用保护策略”窗格中，选择要修改的策略  。

2. 在“Intune 应用保护”  窗格中，选择“属性”  。

3. 在标题为“分配”  的部分旁边，选择“编辑”  。

4. 若要向策略添加新用户组，请在“包括”选项卡中选择“选择要包括的组”，然后选择用户组   。 选择“选择”  以添加组。 

5. 若要排除用户组，在“排除”  选项卡中，选择“选择要排除的组”  ，然后选择用户组。 选择“选择”  以删除用户组。  

6. 若要删除之前已添加的组，在  “包括”或“排除”  选项卡上，选择省略号 (...)，然后选择“删除”  。

7. 单击“查看 + 创建”  以查看为此策略选择的用户组。

8. 对分配所做的更改准备就绪后，选择“保存”  以保存配置并将策略部署到一组新用户。 如果在保存配置之前选择“取消”  ，则将放弃对  “包括”和“排除”  选项卡所做的所有更改。

### <a name="to-change-policy-settings"></a>更改策略设置的步骤

1. 在“应用保护策略”窗格中，选择要修改的策略  。

2. 在“Intune 应用保护”  窗格中，选择“属性”  。

3. 在对应于要更改的设置的部分旁边，选择“编辑”  。 然后将设置更改为新值。

7. 单击“查看 + 创建”  以查看此策略的更新设置。

4. 选择“保存”以保存所做的更改  。 重复此过程以选择设置区域并进行修改，然后保存所做的更改，直到所有更改已完成。 然后，可以关闭“Intune 应用保护 - 属性”窗格  。 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>根据设备管理状态设置应用保护策略的适用对象
在许多组织中，允许最终用户使用 Intune 移动设备管理 (MDM) 托管的设备（如公司拥有的设备）和使用仅由 Intune 应用保护策略提供保护的非托管设备的情况都很常见。 非托管设备通常称为“自带设备”(BYOD)。

Intune 应用保护策略是一种针对用户身份的策略，因此用户的保护设置可应用于已注册（MDM 托管）和未注册（非 MDM）设备。 因此，可以将 Intune 应用保护策略应用于已注册或未注册 Intune 的 iOS/iPadOS 和 Android 设备。 你可以对非托管设备应用具备严格数据丢失防护 (DLP) 措施的保护策略，并对 MDM 托管设备应用 DLP 措施较为宽松的单独保护策略。 有关详细信息，请参阅[应用保护策略和工作配置文件](android-deployment-scenarios-app-protection-work-profiles.md)。

若要创建这些策略，请在 Intune 控制台中浏览找到“应用” > “应用保护策略”，然后选择“创建策略”    。 还可以编辑现有的应用保护策略。 要将应用保护策略同时应用到受管理和不受管理的设备，请导航至“应用”页面并确保将“面向所有类型的设备上的应用”设置为“是”（这是默认值）    。 如果希望根据管理状态逐渐分配，请将“面向所有类型的设备上的应用”设置为“否”   。 

### <a name="device-types"></a>设备类型

- **非托管**：非托管设备是未检测到 Intune MDM 管理的设备。 这包括由第三方 MDM 供应商托管的设备。
- **Intune 托管设备**：托管设备由 Intune MDM 管理。
- **Android 设备管理员**：使用 Android 设备管理 API 的 Intune 托管设备。
- **Android Enterprise**：使用 Android Enterprise 工作配置文件或 Android Enterprise 完全设备管理的 Intune 托管设备。

> [!NOTE]
> 无论选择哪种设备类型，Android 设备都将提示安装 Intune 公司门户应用。 例如，如果选择“Android Enterprise”，则仍会提示使用非托管 Android 设备的用户。

对于 iOS/iPadOS，需要额外的应用配置设置才能将应用保护策略 (APP) 设置定位到 Intune 注册设备上的应用：

- 必须为所有 MDM 托管应用程序配置“IntuneMAMUPN”  。 有关详细信息，请参阅[如何在 Microsoft Intune 中管理 iOS/iPadOS 应用之间的数据传输](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)。
- 必须为所有第三方和业务线 MDM 托管应用程序配置“IntuneMAMDeviceID”  。 应将“IntuneMAMDeviceID”配置为设备 ID 令牌  。 例如，`key=IntuneMAMDeviceID, value={{deviceID}}`。 有关详细信息，请参阅[为受管理 iOS/iPadOS 设备添加应用配置策略](app-configuration-policies-use-ios.md)。
- 若仅配置了“IntuneMAMDeviceID”，则 Intune 应用会将设备视为非托管设备  。

> [!NOTE]
> 有关根据设备管理状态分配应用保护策略的 iOS/iPadOS 具体支持信息，请参阅[根据管理状态应用 MAM 保护策略](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state)。

## <a name="policy-settings"></a>策略设置
若要查看 iOS/iPadOS 和 Android 的策略设置的完整列表，请选择以下链接之一：

- [iOS/iPadOS 策略](app-protection-policy-settings-ios.md)
- [Android 策略](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>后续步骤
[监视合规性和用户状态](app-protection-policies-monitor.md)

## <a name="see-also"></a>另请参阅
* [Android 应用由应用保护策略托管时会出现的情况](../fundamentals/end-user-mam-apps-android.md)
* [iOS/iPadOS 应用由应用保护策略托管时会出现的情况](../fundamentals/end-user-mam-apps-ios.md)
