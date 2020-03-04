---
title: 管理批量购买的 iOS/iPadOS 电子书
titleSuffix: Microsoft Intune
description: 了解如何才能将从 iOS 应用商店批量购买的书籍同步到 Intune 中，然后管理并跟踪其使用情况。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff2ed62695bad781b7b55ac590e9b97490ba2416
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216081"
---
# <a name="how-to-manage-iosipados-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理通过批量购买计划购买的 iOS/iPadOS 电子书


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

通过 Apple Volume Purchase Program (VPP)，可让你为想要分发给公司中多个用户的书籍购买多个许可证。 你可以从企业版应用商店或教育版应用商店中分发书籍。

Microsoft Intune 可帮助你同步、管理和分配通过此计划购买的书籍。 你可以从应用商店中导入许可证信息，然后跟踪用户使用的许可证数量。

管理书籍的过程与[管理 VPP 应用](../vpp-apps-ios.md)类似。

## <a name="manage-volume-purchased-books-for-ios-devices"></a>管理批量采购的适用于 iOS 设备的书籍
通过 [Apple Volume Purchase Program 企业版](https://www.apple.com/business/vpp/)或 [Apple Volume Purchase Program 教育版](https://volume.itunes.apple.com/us/store)购买多个 iOS/iPadOS 书籍许可证。 这一过程将需要从 Apple 网站设置一个 Apple VPP 帐户并将 Apple VPP 令牌上传到 Intune。  然后，你可以将批量购买信息与 Intune 同步并跟踪你批量购买书籍的使用情况。

## <a name="before-you-start"></a>开始之前
在开始之前，从 Apple 中获取 VPP 令牌并将其上传到 Intune 帐户。 此外：

* 如果你以前使用过不同产品的 VPP 令牌，必须生成一个新的令牌在 Intune 中使用。
* 每个令牌的有效期为一年。
* 默认情况下，Intune 与 Apple VPP 服务一天同步两次。 可以随时开始手动同步。
* 将 VPP 令牌导入 Intune 之后，不要将同一令牌导入任何其他设备管理解决方案。 这样做可能导致许可证分配和用户记录丢失。
* 在开始使用 Intune 管理 iOS/iPadOS 书籍之前，请先删除使用其他移动设备管理 (MDM) 供应商创建的任何现有 VPP 用户帐户。 作为安全措施，Intune 不会将那些用户帐户同步到 Intune 中。 Intune 将仅同步 Apple VPP 服务中由 Intune 创建的数据。
* 在向设备分配一本书时，该设备必须安装内置的 iBooks 应用， 否则，最终用户必须重新安装该应用才能阅读书籍。 当前不能使用 Intune 来还原已删除的内置应用。
* 你只能从 Apple Volume Purchase Program 站点分配书籍。 你无法上传，然后分配在内部创建的书籍。
* 你当前无法使用与应用相同的操作方式将书籍分配到最终用户类别。
* 分配书籍后不能回收许可证。
* 具有符合条件的设备的用户首次尝试安装 VPP 书籍时，必须加入 Apple Volume Purchase Program 才能安装书籍。 你还可以向具有托管 Apple ID 的安全组分配许可证。 如果这样，安装书籍时，系统将不会向用户提示其 Apple ID。
* 设备必须通过用户关联进行注册，因为电子书只能分配给用户组。   


## <a name="to-get-and-upload-an-apple-vpp-token"></a>获取并上传 Apple VPP 令牌

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“租户管理”   > “连接器和令牌”   > “Apple VPP 令牌”  。
3. 在 VPP 令牌列表窗格上单击“创建”  。
5. 在“新 VPP 令牌”窗格中，指定下列信息  ：
    - **VPP 令牌文件** - 确保你已注册 Volume Purchase Program 企业版或 Volume Purchase Program 教育版。 然后，为你的帐户下载 Apple VPP 令牌，并在此处选择它。
    - **Apple ID** - 输入与批量购买计划关联的帐户的 Apple ID。
    - **VPP 帐户类型** - 从“企业版”  或“教育版”  中进行选择。
5. 完成后，单击“创建”  。

该令牌显示在“令牌列表”窗格中。


你可以随时通过选择“立即同步”将 Apple 保存的数据与 Intune 同步。 

## <a name="to-assign-a-volume-purchased-app"></a>如何分配批量购买应用

1. 选择“应用”   > “电子书”   > “所有电子书”  。
2. 在书籍列表窗格中，选择要分配的书籍，然后依次选择“...”和“分配组”   。
3. 在“<书籍名称> - 已分配的组”窗格中，选择“管理” > “已分配的组”     。
4. 选择“分配组”，然后在“选择组”窗格中，选择要将书籍分配到的 Azure AD 用户组   。 目前不支持设备组。
选择一个“可用”或“必需”的分配操作   。 
5. 完成后，选择“保存”  。

## <a name="next-steps"></a>后续步骤

有关帮助监视书籍分配的信息，请参阅[如何监视应用](apps-monitor.md)。






