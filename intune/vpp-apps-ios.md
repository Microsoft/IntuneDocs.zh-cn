---
title: 在 Microsoft Intune 中管理 iOS 批量购买的应用
titlesuffix: ''
description: 了解如何才能将从 iOS 应用商店批量购买的应用同步到 Microsoft Intune 中，然后管理并跟踪其使用情况。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 574880ae1ff7f734edcb02ebc89d7a0270064d4e
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905965"
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

iOS 应用商店允许你为想要在公司运行的应用购买多个许可证。 购买多个副本可帮助你有效地管理公司的应用。

Microsoft Intune 可帮助你管理通过此计划购买的多个应用副本，方法为：

- 从应用商店中报告许可证信息。
- 跟踪已使用的许可证数量。
- 帮助防止安装的应用副本数超过所拥有的数目。

可通过两种方法分配批量采购的应用：

### <a name="device-licensing"></a>设备许可

将应用分配到设备时，需使用一个应用证书，此证书将与其分配到的设备保持关联。

将批量采购的应用分配到设备时，设备的最终用户不必提供 Apple ID 即可访问应用商店。

### <a name="user-licensing"></a>用户许可

将应用分配给用户时，需使用一个应用证书，此证书将与用户关联。 可以在用户拥有的多个（数量限制由 Apple 控制）设备上运行该应用。

将批量采购的应用分配给用户时，每个最终用户必须具有有效且唯一的 Apple ID 才能访问应用商店。

此外，还可以使用 Intune 同步和管理从 Apple Volume Purchase Program (VPP) 商店购买的电子图书。 有关详细信息，请参阅[如何管理通过批量购买计划购买的 iOS 电子书](vpp-ebooks-ios.md)。

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>管理批量采购的适用于 iOS 设备的应用程序

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>支持适用于 iOS 设备的 Apple Volume Purchase Program 批量采购应用

通过 [Apple Volume Purchase Program 企业版](http://www.apple.com/business/vpp/)或 [Apple Volume Purchase Program 教育版](http://volume.itunes.apple.com/us/store)购买多个 iOS 应用许可证。 这一过程将需要从 Apple 网站设置一个 Apple VPP 帐户并将 Apple VPP 令牌上传到 Intune。  然后你可以将你的批量购买信息与 Intune 同步并追踪你的批量购买的应用的使用情况。

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>支持适用于 iOS 设备的企业到企业批量采购应用

此外，第三方开发人员还可以私下将应用分发给适用于 iTunes Connect 中指定的业务成员的经授权 Volume Purchase Program。 这些面向业务成员的 VPP 可以登录 Volume Purchase Program App Store 并购买应用。 最终用户购买的适用于业务应用的 VPP 将同步到其 Intune 租户中。

## <a name="before-you-start"></a>开始之前
开始前，需要先从 Apple 获取 VPP 标记，并将其上传到 Intune 帐户。 此外，还应了解以下注意事项：

* 可将多个 VPP 令牌与你的 Intune 帐户关联。
* 如果你以前使用过不同产品的 VPP 令牌，必须生成一个新的令牌在 Intune 中使用。
* 每个令牌的有效期为一年。
* 默认情况下，Intune 与 Apple VPP 服务一天同步两次。 可以随时开始手动同步。
* 在开始配合使用 Apple VPP 和 Intune 之前，先删除使用其他移动设备管理 (MDM) 供应商创建的任何现有 VPP 用户帐户。 作为安全措施，Intune 不会将那些用户帐户同步到 Intune 中。 Intune 将仅同步 Apple VPP 服务中由 Intune 创建的数据。
* Intune 支持最多添加 256 个 VPP 令牌。
* Apple 的设备注册配置文件 (DEP) 计划可将移动设备管理 (MDM) 注册自动化。 利用 DEP，可以在不触及企业设备的情况下对其进行配置。 可以使用用于 Apple VPP 的相同计划代理帐户在 DEP 计划中进行注册。 [Apple 部署计划](https://deploy.apple.com)网站下列出的计划具有唯一的 Apple 部署计划 ID，并且此 ID 可用于登录 Apple 服务，如 iTunes 商店。
* 使用用户授权模型向用户或设备（具有用户关联）分配 VPP 应用时，每个 Intune 用户在其设备上接受 Apple 条款与条件时都需与一个唯一的 Apple ID 或电子邮件地址相关联。 确保为新的 Intune 用户设置设备时，使用该用户的唯一 Apple ID 或电子邮件地址来配置设备。 Apple ID 或电子邮件地址与 Intune 用户配成唯一对，并且最多可用于 5 台设备。
* 仅支持一次在一个 Intune 帐户上使用一个 VPP 令牌。 不要将同一个 VPP 令牌重复用于多个 Intune 账户。
* 使用用户授权模型向用户或设备（具有用户关联）分配 VPP 应用时，每个 Intune 用户在其设备上接受 Apple 条款与条件时都需与一个唯一的 Apple ID 或电子邮件地址相关联。
确保为新的 Intune 用户设置设备时，使用该用户的唯一 Apple ID 或电子邮件地址来配置设备。 Apple ID 或电子邮件地址与 Intune 用户配成唯一对，并且最多可用于 5 台设备。

>[!IMPORTANT]
>将 VPP 令牌导入 Intune 之后，不要将同一令牌导入任何其他设备管理解决方案。 这样做可能导致许可证分配和用户记录丢失。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>获取并上传 Apple VPP 令牌

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
1.  在“Intune”窗格中，选择“设置”下的“移动应用” > “iOS VPP 令牌”。
2.  在 VPP 令牌列表窗格中，选择“创建”。
4. 在“创建 VPP 令牌”窗格中，指定下列信息：
    - **VPP 令牌文件** - 如果尚未注册，则请注册 Volume Purchase Program 企业版或 Volume Purchase Program 教育版。 注册后，为你的帐户下载 Apple VPP 令牌，并在此处选择它。
    - **Apple ID** - 输入与批量购买计划关联的帐户的 Apple ID。
    - **国家/地区** - 选择 VPP 国家/地区应用商店。  Intune 将同步指定 VPP 国家/地区应用商店中所有区域设置对应的 VPP 应用。
        > [!WARNING]  
        > 对于使用此标记创建的应用，更改国家/地区将更新应用元数据，并在下次与 Apple 服务同步时存储 URL。 如果应用未在新的国家/地区应用商店中提供，则不会更新该应用。

    - **VPP 帐户类型** - 从“企业版”或“教育版”中进行选择。
    - **自动应用更新** - 从“关”切换为“开”以启用自动更新。 启用后，当设备签入时，Intune 将更新通过 Intune 服务针对指定令牌购买的所有应用。
Intune 将在应用商店内检测 VPP 应用更新，并在设备签入时自动将这些更新推送到设备中。
4. 完成后，选择“创建”。

该令牌显示在“令牌列表”窗格中。

你可以随时通过选择“立即同步”将 Apple 保存的数据与 Intune 同步。

## <a name="to-assign-a-volume-purchased-app"></a>如何分配批量购买应用

1.  在“Intune”窗格中，选择“管理”下的“移动应用” > “应用”。
2.  在应用列表窗格中，选择要分配的应用，然后选择“分配”。
3.  在“应用名称 - 分配”窗格中，选择“添加组”，然后在“添加组”窗格中，选择“分配类型”以及要将应用分配到的 Azure AD 用户或设备组。
5.  请为选择的每个组选择以下设置：
    - **类型** - 选择应用将为“可用”（最终用户可以从公司门户安装应用）还是“必需”（最终用户设备将自动安装应用）。
    - 许可证类型 - 选择“用户许可”或“设备许可”。
6.  完成后，选择“保存”。


>[!NOTE]
>所显示的应用列表中的每个应用与一个令牌相关联。 如果具有一个与多个 VPP 令牌相关联的应用，会看到同一应用显示多次，一次对应一个令牌。

## <a name="end-user-prompts-for-vpp"></a>VPP 的最终用户提示

在许多场景下，最终用户都将收到 VPP 应用安装的提示。 下表分别介绍了每种情况：

| # | 方案                                | 邀请到 Apple VPP 计划                              | 应用安装提示 | Apple ID 提示 |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD - 用户已获许可                             | Y                                                                                               | Y                                           | Y                                 |
| 2 | Corp - 用户已获许可（不受监督的设备）     | Y                                                                                               | Y                                           | Y                                 |
| 3 | Corp - 用户已获许可（受监督的设备）         | Y                                                                                               | N                                           | Y                                 |
| 4 | BYOD - 设备已获许可                           | N                                                                                               | Y                                           | N                                 |
| 5 | CORP - 设备已获许可（不受监督的设备）                           | N                                                                                               | Y                                           | N                                 |
| 6 | CORP - 设备已获许可（受监督的设备）                           | N                                                                                               | N                                           | N                                 |
| 7 | 展台模式（受监督的设备）- 设备已获许可 | N                                                                                               | N                                           | N                                 |
| 8 | 展台模式（受监督的设备）- 用户已获许可   | --- | ---                                          | ---                                |

> [!Note]  
> 不建议使用 VPP 用户许可将 VPP 应用分配给展台模式设备。

## <a name="revoking-app-licenses-and-deleting-tokens"></a>撤消应用许可证和删除令牌 

可根据给定的设备、用户或应用，撤销所有关联的 iOS 批量采购计划 (VPP) 应用许可证。 可在取消向用户分配应用时向其发出通知。 撤销应用许可证将不会从设备中卸载相关的 VPP 应用。 若要卸载 VPP 应用并回收分配给用户或设备的应用许可证，必须将分配操作更改为“卸载”。 删除已分配给用户的应用时，Intune 将回收用户或设备许可证，并从设备中卸载该应用。 回收的许可证计数将反映在 Intune“应用”工作负荷的“许可应用”节点中。 卸载 VPP 应用并回收应用许可证后，可选择将应用许可证分配给其他用户或设备。 

>[!NOTE]
>当员工离开公司，并且不再属于 AAD 组时，Intune 将检索用户已获许可的所有 iOS VPP 应用许可证。

<!-- 820879 -->  
可以使用控制台删除 iOS 批量采购计划 (VPP) 令牌。 当你有重复的 VPP 令牌实例时，可能需要执行此操作。 删除令牌也将删除任何关联的应用和分配。 但是，删除令牌不会撤销应用许可证或卸载应用。 

>[!NOTE]
>删除令牌后，Intune 不能撤销应用许可证。 

<!-- 820870 -->  
若要撤销适用于给定 VPP 令牌的所有 VPP 应用的许可证，必须首先撤销所有与令牌相关联的应用许可证，然后删除令牌。

## <a name="further-information"></a>更多信息

符合条件设备的用户首次尝试在设备上安装 VPP 应用时，系统将要求其加入 Apple Volume Purchase Program。 开始安装应用前，他们必须加入该计划。 加入 Apple Volume Purchase 计划的邀请需要用户可以使用 iOS 设备上的 iTunes 应用。 如果已设置禁用 iTunes 应用商店应用的策略，基于用户许可的 VPP 应用将无法工作。 解决方案是删除策略，或使用基于设备的许可来允许 iTunes 应用。

## <a name="frequently-asked-questions"></a>常见问题

#### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>从设备中安装和删除应用后，门户需要多长时间来更新许可证计数？
安装或卸载应用后，许可证会在几小时内更新。 请注意，如果最终用户从设备中删除应用，许可证仍将继续分配给该用户或设备。

#### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>是否可以超额订阅应用，如可以，请指明情况。
是。 Intune 管理员可以超额订阅应用。 例如，如果管理员针对应用 XYZ 购买 100 个许可证，然后将应用分配给包含 500 个成员的组。 则前 100 个成员（用户或设备）将分配到许可证，而其余成员不会获得许可证分配。

#### <a name="i-understand-intune-automatically-syncs-app-licenses-each-day-with-apple-is-that-correct"></a>据我了解，Intune 每天与 Apple 自动同步应用许可证，是这样吗？
Intune 每天与 Apple 同步 2 次应用许可证。

## <a name="next-steps"></a>后续步骤

有关帮助监视应用分配的信息，请参阅[如何监视应用](apps-monitor.md)。
