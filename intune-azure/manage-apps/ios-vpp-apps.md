---
title: "管理 iOS 批量购买的应用"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何将从 iOS App Store 批量购买的应用同步到 Intune，并管理和跟踪这些应用的使用情况。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: ff43a0be6ebc124bb7e52e5be31e89985ce32166
ms.contentlocale: zh-cn
ms.lasthandoff: 04/24/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理通过 Volume Purchase Program 购买的 iOS 应用


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

在 iOS App Store 中，可以购买要在公司中运行的应用的多个许可证。 这有助于降低跟踪多个已购买应用副本的管理成本。

使用 Microsoft Intune，可以从 App Store 导入许可证信息、跟踪已使用的许可证数量，并能阻止安装不拥有的应用副本，从而有助于你管理通过此计划购买的应用。

此外，还可以使用 Intune 同步和管理从 Apple Volume Purchase Program 商店购买的电子图书，然后将其分配给用户。 使用 Intune 门户中的“图书”工作负载可以管理图书。 图书管理过程与应用管理过程相同。
为此，必须上载 Apple Volume Purchase Program 标记。 目前，只能将图书分配为“必需”安装项。
向设备分配图书时，设备上必须已安装内置的 iBooks 应用。 如果未安装，最终用户必须重新安装此应用，才能阅读图书。 暂无法使用 Intune 还原已删除的内置应用。


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>管理批量采购的适用于 iOS 设备的应用程序
可以通过 [Apple Volume Purchase Program 企业版](http://www.apple.com/business/vpp/)或 [Apple Volume Purchase Program 教育版](http://volume.itunes.apple.com/us/store)购买多个 iOS 应用许可证。 为此，需要在 Apple 网站中创建 Apple VPP 帐户，然后将 Apple VPP 标记上载到 Intune 中。  然后，可以将批量购买信息与 Intune 同步，并跟踪批量购买应用的使用情况。

## <a name="before-you-start"></a>开始之前
开始前，需要先从 Apple 获取 VPP 标记，并将其上载到 Intune 帐户中。 此外，还应了解以下注意事项：

* 可以将多个 Volume Purchase Program 标记与 Intune 帐户相关联。
* 如果以前对其他产品使用过 VPP 标记，必须生成用于 Intune 的新标记。
* 每个令牌的有效期为一年。
* 默认情况下，Intune 每天与 Apple VPP 服务同步两次。 可以随时启动手动同步。
* 将 VPP 标记导入 Intune 后，请勿将同一标记导入其他任何设备管理解决方案中。 这样做可能会丢失许可证分配和用户记录。
* 开始将 iOS VPP 用于 Intune 前，请删除与其他移动设备管理 (MDM) 供应商一起创建的任何现有 VPP 用户帐户。 为保障安全，Intune 不会将这些用户帐户同步到 Intune。 Intune 只会同步 Intune 创建的 Apple VPP 服务数据。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>如何获取并上载 Apple VPP 标记

1. 登录 Azure 门户。
2. 依次选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“移动应用”。
1.  在“移动应用”工作负载中，依次选择“设置” > “iOS VPP 标记”。
2.  在 VPP 标记列表边栏选项卡上，单击“添加”。
3.  在“新建 VPP 标记”边栏选项卡上，指定下列信息：
    - VPP 标记文件 - 如果尚未注册，请注册 Volume Purchase Program 企业版或 Volume Purchase Program 教育版。 注册后，下载适用于帐户的 Apple VPP 标记，并在此处选择它。
    - Apple ID - 输入与 Volume Purchase Program 关联的帐户的 Apple ID。
    - VPP 帐户类型 - 从“企业版”或“教育版”中进行选择。
4. 完成后，请单击“上载”。

此时，标记会显示在标记列表边栏选项卡中。


可以随时选择“立即同步”，将 Apple 保存的数据与 Intune 同步。

## <a name="to-assign-a-volume-purchased-app"></a>如何分配批量购买应用

1. 在“移动应用”工作负载中，依次选择“管理” > “获得许可的应用”。
2. 在应用列表边栏选项卡上，选择要分配的应用，然后依次选择“...” >“分配组”。
3. 在“<*应用名称*> - 已分配的组”边栏选项卡上，依次选择“管理” > “已分配的组”。
4. 选择“分配组”，然后在“选择组”边栏选项卡上，选择要向其分配应用的 Azure AD 用户或设备组。
必须选择“必需”分配操作。 此外，2017 年 1 月之后创建的新租户还可以将应用分配给设备组。 如果租户是在此日期之前创建，且无法视需要将 VPP 应用分配给设备组，请联系 Intune 支持人员。
5. 完成后，选择“保存”。

请参阅[如何监视应用](monitor-apps.md)，了解如何监视应用分配。

## <a name="further-information"></a>更多信息

将应用分配为“必需”安装项后，安装应用的所有用户便都使用许可证。

若要回收许可证，必须将分配操作更改为“卸载”。 卸载应用后，将回收许可证。

当具有符合条件的设备的用户首次安装 VPP 应用时，系统会要求其加入 Apple Volume Purchase Program。 用户必须先执行此操作，然后才能继续安装应用。

如果将 VPP 应用部署为“可用”，应用内容和许可证会直接从 App Store 进行部署。

