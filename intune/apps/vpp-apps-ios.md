---
title: 管理 Apple 批量采购的应用
titleSuffix: Microsoft Intune
description: 了解如何才能将从 iOS/iPadOS 和 macOS App Store 批量购买的应用同步到 Microsoft Intune 中，然后管理并跟踪其使用情况。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9127ee06bc2125f476c18e9b8e46a127e48d0245
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513395"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理通过 Apple Volume Purchase Program 购买的 iOS 和 macOS 应用


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple 允许使用 [Apple Business Manager](https://business.apple.com/) 或 [Apple School Manager](https://school.apple.com/) 为你要在组织的 iOS/iPadOS 和 macOS 设备上使用的应用购买多个许可证。 然后你可以将你的批量购买信息与 Intune 同步并追踪你的批量购买的应用的使用情况。 购买应用许可证可帮助你有效管理公司内的应用，并保持对所购买的应用程序的所有权和控制权。 

Microsoft Intune 可帮助管理通过此类计划购买的应用，方法为：

- 同步从 Apple Business Manager 下载的位置令牌。
- 跟踪可用的许可证数量，以及已用于购买应用的许可证数量。
- 帮助安装应用程序，具体取决于你所拥有的许可证数量。

此外，还可以使用 Intune 同步和管理从 Apple Business Manager 购买的书籍，并将它们分配到 iOS/iPadOS 设备。 有关详细信息，请参阅[如何管理通过批量购买计划购买的 iOS/iPadOS 电子书](vpp-ebooks-ios.md)。

## <a name="what-are-location-tokens"></a>什么是位置令牌？
位置令牌也称为“Volume Purchase Program (VPP) 令牌”。 这些令牌用于分配和管理使用 Apple Business Manager 购买的许可证。 内容管理员可以购买许可证，并将其与在 Apple Business Manager 中拥有权限的位置令牌相关联。 然后，这些位置令牌从 Apple Business Manager 下载并在 Microsoft Intune 上传。 Microsoft Intune 支持每个租户上传多个位置令牌。 每个令牌的有效期为一年。

## <a name="how-are-purchased-apps-licensed"></a>如何授权购买的应用？
购买的应用可以使用 Apple 提供的用于 iOS/iPadOS 和 macOS 设备的两种类型的许可证分配给组。

|   | 设备许可 | 用户许可 |
|-----|------------------|----------------|
| **App Store 登录** | 不需要。 | 系统提示登录到 App Store 时，每个最终用户都必须使用唯一的 Apple ID。 |
| **阻止访问 App Store 的设备配置** | 可以使用公司门户安装和更新应用。 | 加入 Apple VPP 的邀请需要访问 App Store。 如果已设置禁用 App Store 的策略，用户许可的 VPP 应用将无法工作。 |
| **自动进行应用更新** | 在 Apple VPP 令牌设置中由 Intune 管理员配置，其中应用的“分配类型”  为“必需”  。 <br> <br> 如果“分配类型”  为“可用于已注册的设备”  ，则可以从公司门户安装可用的应用更新。 | 在个人 App Store 设置中由最终用户配置。 这不能由 Intune 管理员管理。 |
| **用户注册** | 不支持。 | 支持使用托管的 Apple ID。 |
| **书籍** | 不支持。 | 支持。 |
| **已使用的许可证** | 每台设备 1 个许可证。 许可证与设备关联。 | 1 个许可证，最多 5 台设备使用同一个人 Apple ID。 许可证与用户关联。 <br> <br> 与 Intune 中的个人 Apple ID 和托管 Apple ID 关联的最终用户会使用 2 个应用许可证。|
| **许可证迁移** | 应用可以无提示地从用户迁移到设备许可证。 | 应用无法从设备迁移到用户许可证。 |

> [!NOTE]  
> 公司门户不会在用户注册设备上显示设备许可应用，因为用户注册设备上只能安装用户许可的应用。

## <a name="what-app-types-are-supported"></a>支持哪些应用类型？
你可以使用 Apple Business Manager 购买和分发公共应用及专用应用。
- **应用商店应用：** 使用 Apple Business Manager，内容管理员可以购买 App Store 中提供的免费和付费应用。
- **自定义应用：** 使用 Apple Business Manager，内容管理员还可以购买专用于组织的自定义应用。 这些应用是由与你直接合作的开发人员根据组织的特定需求定制的。 了解有关[如何分发自定义应用](https://developer.apple.com/business/custom-apps/)的详细信息。

## <a name="prerequisites"></a>必备条件
- 组织的 [Apple Business Manager](https://business.apple.com/) 或 [Apple School Manager](https://school.apple.com/) 帐户。 
- 分配给一个或多个位置令牌的已购买应用许可证。 
- 下载的位置令牌。 

> [!IMPORTANT]
> - 位置令牌一次只能与一个设备管理解决方案一起使用。 在开始在 Intune 中使用购买的应用之前，请先撤销和删除其他移动设备管理 (MDM) 供应商使用的任何现有位置令牌。 
> - 仅支持一次在一个 Intune 租户上使用一个位置令牌。 不要将同一个令牌重复用于多个 Intune 账户。
> - 默认情况下，Intune 会每天将位置令牌与 Apple 同步两次。 你可以在任何时候从 Intune 启动手动同步。
> - 将位置令牌导入 Intune 之后，不要将同一令牌导入任何其他设备管理解决方案。 这样做可能导致许可证分配和用户记录丢失。

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>从 Volume Purchase Program (VPP) 迁移到应用和书籍
如果组织尚未迁移到 Apple Business Manager 或 Apple School Manager，请参阅[有关迁移到应用和书籍的 Apple 指南](https://support.apple.com/HT208257)，然后再继续管理 Intune 中已购买的应用。

> [!IMPORTANT]
> - 为了获得最佳迁移体验，每个位置只迁移一个 VPP 购买者。 如果每个购买者都迁移到唯一位置，则所有许可证（已分配和未分配）都将迁移到应用和书籍。
> - 请勿删除 Intune 中的现有旧 VPP 令牌，或在 Intune 中删除与现有旧版 VPP 令牌关联的应用和分配。 这些操作将要求在 Intune 中重新创建所有应用分配。

按照以下步骤将现有已购买的 VPP 内容和令牌迁移到 Apple Business Manager 或 Apple School Manager 中的应用和书籍：

1. 邀请 VPP 购买者加入你的组织，并指导每个用户选择一个唯一位置。 
2. 在继续前，请确保组织内的所有 VPP 购买者都已完成步骤 1。
3. 验证所有购买的应用和许可证是否均已迁移到 Apple Business Manager 或 Apple School Manager 中的应用和书籍。
4. 转到“Apple Business（或 School）Manager”   > “设置”   > “应用和书籍”   > “我的服务器令牌”  下载新位置令牌。
5. 若要在 Microsoft 终结点管理器管理中心更新位置令牌，请转到“租户管理”   > “连接器和令牌”   > “Apple VPP 令牌”  并同步令牌。

## <a name="upload-an-apple-vpp-or-location-token"></a>上传 Apple VPP 或位置令牌

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 选择“租户管理”   > “连接器和令牌”   > “Apple VPP 令牌”  。
4. 在 VPP 令牌列表窗格中，选择“创建”  。
5. 在“创建 VPP 令牌”窗格中，指定下列信息  ：
    - **VPP 令牌文件** - 如果尚未注册，请注册 Apple Business Manager 或 Apple School Manager。 注册后，为你的帐户下载 Apple VPP 令牌，并在此处选择它。
    - **Apple ID** - 输入与上传的令牌关联的帐户的托管 Apple ID。
    - **控制另一个 MDM 的令牌** - 将此选项设置为“是”  以允许将令牌从另一个 MDM 解决方案重新分配给 Intune。
    - **令牌名称** - 用于设置令牌名称的管理字段。    
    - **国家/地区** - 选择 VPP 国家/地区应用商店。  Intune 将同步指定 VPP 国家/地区应用商店中所有区域设置对应的 VPP 应用。
        > [!WARNING]  
        > 对于使用此令牌创建的应用，更改国家/地区将更新应用元数据，并在下次与 Apple 服务同步时存储 App Store URL。 如果应用未在新的国家/地区应用商店中提供，则不会更新该应用。

    - **VPP 帐户类型** - 从“企业版”  或“教育版”  中进行选择。
    - **自动应用更新** - 从“关”切换为“开”以启用或停用自动更新   。 启用后，Intune 将在应用商店内检测 VPP 应用更新，并在设备进行签入时自动将这些更新推送到设备中。 
        
        > [!NOTE] 
        > Apple VPP 应用的自动应用更新将仅自动更新通过“必需”的安装意向所部署的应用  。 对于通过“可用”安装意向部署的应用，自动更新会为 IT 管理员生成状态信息，提示该应用有可用的新版本  。 选择应用，选择“设备安装状态”，然后选中“状态详细信息”，即可查看此状态消息。  

    - **我授权 Microsoft 向 Apple 发送用户和设备信息。** - 必须选择“我同意”  才能继续。 若要查看 Microsoft 向 Apple 发送的数据，请参阅 [Intune 向 Apple 发送的数据](~/protect/data-intune-sends-to-apple.md)。

6. 完成后，选择“创建”  。 该令牌显示在“令牌列表”窗格中。

## <a name="synchronize-a-vpp-token"></a>同步 VPP 令牌
可以通过为所选令牌选择“同步”  ，在 Intune 中为已购买的应用同步应用名称、元数据和许可证信息。

## <a name="assign-a-volume-purchased-app"></a>分配批量购买的应用

1. 选择“应用”   > “所有应用”  。
2. 在应用列表窗格中，选择要分配的应用，然后选择“分配”  。
3. 在“应用名称 - 分配”窗格中，选择“添加组”，然后在“添加组”窗格中，选择“分配类型”以及要将应用分配到的 Azure AD 用户或设备组      。
5. 请为选择的每个组选择以下设置：
    - **类型** - 选择应用将为“可用”（最终用户可以从公司门户安装应用）还是“必需”（最终用户设备将自动安装应用）   。
    - 许可证类型 - 选择“用户许可”或“设备许可”    。
6. 完成后，选择“保存”  。


>[!NOTE]
>设备组不支持可用部署意图，仅用户组支持。 所显示的应用列表中的每个应用与一个令牌相关联。 如果具有一个与多个 VPP 令牌相关联的应用，会看到同一应用显示多次，一次对应一个令牌。

> [!NOTE]  
> Intune（或其他任何相关 MDM）不会安装 VPP 应用。 Intune 会连接到 VPP 帐户，并告诉 Apple 将哪些应用许可证分配到哪些设备。 从这里开始，所有实际安装都由 Apple 和设备进行协调。
> 
> [Apple MDM 协议参考，第 135 页](https://developer.apple.com/business/documentation/MDM-Protocol-Reference.pdf)

## <a name="end-user-prompts-for-vpp"></a>VPP 的最终用户提示

在许多场景下，最终用户都将收到 VPP 应用安装的提示。 下表分别介绍了每种情况：

| # | 方案                                | 邀请到 Apple VPP 计划                              | 应用安装提示 | Apple ID 提示 |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD - 用户已获许可（非用户注册设备）                             | 是                                                                                               | 是                                           | 是                                 |
| 2 | Corp - 用户已获许可（不受监督的设备）     | 是                                                                                               | 是                                           | 是                                 |
| 3 | Corp - 用户已获许可（受监督的设备）         | 是                                                                                               | N                                           | 是                                 |
| 4 | BYOD - 设备已获许可                           | N                                                                                               | 是                                           | N                                 |
| 5 | CORP - 设备已获许可（不受监督的设备）                           | N                                                                                               | 是                                           | N                                 |
| 6 | CORP - 设备已获许可（受监督的设备）                           | N                                                                                               | N                                           | N                                 |
| 7 | 展台模式（受监督的设备）- 设备已获许可 | N                                                                                               | N                                           | N                                 |
| 8 | 展台模式（受监督的设备）- 用户已获许可   | --- | ---                                          | ---                                |

> [!Note]  
> 不建议使用用户许可将 VPP 应用分配给展台模式设备。

## <a name="revoking-app-licenses"></a>撤销应用许可证

可根据给定的设备、用户或应用，撤销所有关联的 iOS/iPadOS 或 macOS 批量采购计划 (VPP) 应用许可证。  但 iOS/iPadOS 与 macOS 平台之间有一些差异。 

|   | iOS/iPadOS | macOS |
|-----|------------------|----------------|
| **删除应用分配** | 删除已分配给用户的应用时，Intune 将回收用户或设备许可证，并从设备中卸载该应用。 | 删除已分配给用户的应用时，Intune 将回收用户或设备许可证。 应用不会从设备上卸载。 |
| **吊销应用许可证** | 吊销应用许可证将从用户或设备中回收应用许可证。 必须将分配更改为“卸载”  才能从设备中删除应用。 | 吊销应用许可证将从用户或设备中回收应用许可证。 设备上使用已撤销的许可证的 macOS 应用仍然可用，但只有向用户或设备重新分配许可证后它才可以更新。 根据 Apple 的规定，超过 30 天的宽限期后，将删除此类应用。 但 Apple 未向 Intune 提供使用“卸载”分配操作删除应用的方式。

>[!NOTE]
> - 当员工离开公司，并且不再属于 AAD 组时，Intune 将回收应用许可证。
> - 当使用“卸载”  意向分配购买的应用时，Intune 将回收许可证并卸载应用。
> - 从 Intune 管理中删除设备时，不会回收应用许可证。 

## <a name="deleting-vpp-tokens"></a>删除 VPP 令牌
<!-- 820879 -->  
可以使用控制台删除 Apple Volume Purchase Program (VPP) 令牌。 当你有重复的 VPP 令牌实例时，可能需要执行此操作。 删除令牌也将删除任何关联的应用和分配。 但是，删除令牌不会撤销应用许可证或卸载应用。 

>[!NOTE]
>删除令牌后，Intune 不能撤销应用许可证。 

<!-- 820870 -->  
若要撤销适用于给定 VPP 令牌的所有 VPP 应用的许可证，必须首先撤销所有与令牌相关联的应用许可证，然后删除令牌。

## <a name="renewing-app-licenses"></a>续订应用许可证

可以通过从 Apple Business Manager 或 Apple School Manager 下载新的令牌并更新 Intune 中的现有令牌来续订 Apple VPP 令牌。

## <a name="deleting-a-vpp-app"></a>删除 VPP 应用

目前，无法从 Microsoft Intune 中删除 iOS/iPadOS VPP 应用。

## <a name="assigning-custom-role-permissions-for-vpp"></a>分配 VPP 自定义角色权限

可以利用分配给 Intune 自定义管理员角色的权限独立控制 Apple VPP 令牌和 VPP 应用访问。

* 若要允许 Intune 自定义角色管理 Apple VPP 令牌，请在“应用” > “Apple VPP 令牌”中分配对“托管应用”的权限。   
* 若要允许 Intune 自定义角色管理使用 iOS/iPadOS VPP 令牌购买的应用，请在“应用” > “所有应用”中分配对“移动应用”的权限    。 

## <a name="additional-information"></a>其他信息

Apple 提供针对创建和续订 VPP 令牌的直接协助。 有关详细信息，请参阅 Apple 文档一部分的[使用批量采购计划 (VPP) 将内容分发给用户](https://go.microsoft.com/fwlink/?linkid=2014661)。 

如果在 Intune 门户中指示了“分配给外部 MDM”，你（管理员）必须从第三方 MDM 中删除 VPP 令牌，然后才能使用 Intune 中的 VPP 令牌  。

## <a name="frequently-asked-questions"></a>常见问题解答

### <a name="how-many-tokens-can-i-upload"></a>可以上传多少个令牌？
最多可在 Intune 中上传 3000 个令牌。

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>从设备中安装和删除应用后，门户需要多长时间来更新许可证计数？
安装或卸载应用后，许可证会在几小时内更新。 请注意，如果最终用户从设备中删除应用，许可证仍将继续分配给该用户或设备。

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>是否可以超额订阅应用，如可以，请指明情况。
是。 Intune 管理员可以超额订阅应用。 例如，如果管理员针对应用 XYZ 购买 100 个许可证，然后将应用分配给包含 500 个成员的组。 则前 100 个成员（用户或设备）将分配到许可证，而其余成员不会获得许可证分配。


## <a name="next-steps"></a>后续步骤

有关帮助监视应用分配的信息，请参阅[如何监视应用](apps-monitor.md)。

有关解决应用相关问题的信息，请参阅[如何排查应用问题](~/apps/troubleshoot-app-install.md)。
