---
title: "管理批量购买的 iOS 应用"
titlesuffix: Azure portal
description: "了解如何可以将从 iOS 应用商店批量购买的应用同步到 Intune 中，然后管理并跟踪其使用情况。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 08/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8be922d6cc839708ff26de2ebe792241b9bf357a
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理通过批量购买计划购买的 iOS 应用


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

iOS 应用商店允许你为想要在公司运行的应用购买多个许可证。 购买应用的多个副本，有助于降低跟踪多个已购买应用副本的管理开销。

Microsoft Intune 可帮助管理通过此类计划购买的应用，方法为：

- 报告应用商店中的许可证信息
- 跟踪已使用的许可证数量
- 帮助防止安装的应用副本数超过所拥有的数目

可通过两种方法分配批量采购的应用：

### <a name="device-licensing"></a>设备许可

将应用分配到设备时，需使用一个应用证书，此证书将与其分配到的设备保持关联。
将批量采购的应用分配到设备时，设备的最终用户不必提供 Apple ID 即可访问应用商店。 



### <a name="user-licensing"></a>用户许可

将应用分配给用户时，需使用一个应用证书，此证书将与用户关联。 可以在用户拥有的多个（数量限制由 Apple 控制）设备上运行该应用。
将批量采购的应用分配给用户时，每个最终用户必须具有有效且唯一的 Apple ID 才能访问应用商店。


此外，还可以使用 Intune 同步和管理从 Apple Volume Purchase Program 商店购买的电子图书。 有关详细信息，请参阅[如何管理通过批量购买计划购买的 iOS 电子书](vpp-ebooks-ios.md)。


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>管理批量采购的适用于 iOS 设备的应用程序
通过 [Apple Volume Purchase Program 企业版](http://www.apple.com/business/vpp/)或 [Apple Volume Purchase Program 教育版](http://volume.itunes.apple.com/us/store)购买多个 iOS 应用许可证。 这一过程将需要从 Apple 网站设置一个 Apple VPP 帐户并将 Apple VPP 令牌上传到 Intune。  然后你可以将你的批量购买信息与 Intune 同步并追踪你的批量购买的应用的使用情况。

## <a name="before-you-start"></a>开始之前
开始前，需要先从 Apple 获取 VPP 标记，并将其上传到 Intune 帐户。 此外，还应了解以下注意事项：

* 可以将多个批量购买计划令牌与你的 Intune 帐户关联。
* 如果你以前使用过不同产品的 VPP 令牌，必须生成一个新的令牌在 Intune 中使用。
* 每个令牌的有效期为一年。
* 默认情况下，Intune 与 Apple VPP 服务一天同步两次。 可以随时开始手动同步。
* 在开始将 iOS VPP 与 Intune 配合使用之前，先删除使用其他移动设备管理 (MDM) 供应商创建的任何现有 VPP 用户帐户。 作为安全措施，Intune 不会将那些用户帐户同步到 Intune 中。 Intune 将仅同步 Apple VPP 服务中由 Intune 创建的数据。
* Intune 支持最多添加 256 个 VPP 令牌。
* 如果要为通过设备注册配置文件或 Apple Configurator 注册的设备分配批量购买的应用，则此操作只适用于面向设备的应用。 不能让批量采购的应用面向 DEP 设备的用户，这不存在任何用户关联。
因为 iOS VPP 用户许可机制能让数千台设备使用同一用户帐户进行注册。 iOS VPP 用户许可允许最终用户在 5-10 台设备上安装同一应用。
这意味着前几台 DEM 注册设备可使用用户许可安装 VPP 应用，后续其他设备则无法再安装该应用。
* 仅支持一次在一个 Intune 帐户上使用一个 VPP 令牌。 不要将同一个 VPP 令牌重复用于多个 Intune 账户。
* 使用用户授权模型向用户或设备（具有用户关联）分配 VPP 应用时，每个 Intune 用户在其设备上接受 Apple 条款与条件时都需与一个唯一的 Apple ID 或电子邮件地址相关联。
确保为新的 Intune 用户设置设备时，使用该用户的唯一 Apple ID 或电子邮件地址来配置设备。 Apple ID 或电子邮件地址与 Intune 用户配成唯一对，并可最多用于 5 台设备。

>[!IMPORTANT]
>将 VPP 令牌导入 Intune 之后，不要将同一令牌导入任何其他设备管理解决方案。 这样做可能导致许可证分配和用户记录丢失。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>获取并上传 Apple VPP 令牌

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“移动应用”。
1.  在“移动应用”工作负载中，依次选择“设置” > “iOS VPP 标记”。
2.  在 VPP 标记列表边栏选项卡上，单击“添加”。
3.  在“新 VPP 令牌”边栏选项卡中，指定下列信息：
    - **VPP 令牌文件** - 如果尚未注册，则请注册 Volume Purchase Program 企业版或 Volume Purchase Program 教育版。 注册后，为你的帐户下载 Apple VPP 令牌，并在此处选择它。
    - **Apple ID** - 输入与批量购买计划关联的帐户的 Apple ID。
    - **VPP 帐户类型** - 从“企业版”或“教育版”中进行选择。
4. 完成后，请单击“上传”。

该令牌将显示在令牌列表边栏选项卡中。


你可以随时通过选择“立即同步”将 Apple 保存的数据与 Intune 同步。

> [!NOTE]
> Microsoft Intune 将仅同步可通过 iTunes 应用商店公开获得的应用信息。 尚不支持“针对 iOS 的自定义 B2B 应用”。 如果方案针对此类应用，将不同步该应用信息。

## <a name="to-assign-a-volume-purchased-app"></a>如何分配批量购买应用

1.  在“移动应用”工作负荷中，选择“管理” > “应用许可证”。
2.  在应用列表边栏选项卡上，选择要分配的应用，然后依次选择“...”>“分配组”。
3.  在“<app name> -  分配”边栏选项卡上，选择“管理” > “分配”。
4.  选择“选择组”，然后在“选择组”边栏选项卡上，选择要将应用分配到的 Azure AD 用户或设备组。
5.  请为选择的每个组选择以下设置：
    - 类型 - 选择应用将为“可用”（最终用户可以从公司门户安装应用）还是“必需”（最终用户设备将自动安装应用）。
    - 许可证类型 - 选择“用户许可”或“设备许可”。
6.  完成后，选择“保存”。


>[!NOTE]
>所显示的应用列表中的每个应用与一个令牌相关联。 如果具有一个与多个 VPP 令牌相关联的应用，会看到同一应用显示多次，一次对应一个令牌。

## <a name="further-information"></a>更多信息

若要回收许可证，必须将分配操作更改为“卸载”。 卸载应用后，将回收许可证。 如果删除了分配给用户的应用，Intune 会尝试回收与该用户关联的所有应用许可证。

符合条件设备的用户首次尝试在设备上安装 VPP 应用时，系统将要求其加入 Apple Volume Purchase Program。 开始安装应用前，他们必须加入该计划。 加入 Apple Volume Purchase 计划的邀请需要用户可以使用 iOS 设备上的 iTunes 应用。 如果已设置禁用 iTunes 应用商店应用的策略，基于用户许可的 VPP 应用将无法工作。 解决方案是删除策略，或使用基于设备的许可来允许 iTunes 应用。



## <a name="next-steps"></a>后续步骤

有关帮助监视应用分配的信息，请参阅[如何监视应用](apps-monitor.md)。