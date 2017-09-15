---
title: "如何将应用添加到 Microsoft Intune"
titlesuffix: Azure portal
description: "这些过程可助你将应用添加到 Intune，做好分配到用户和设备的准备。 \""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 108f789f16304498cf54387326d112353bf70aa2
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>如何向 Microsoft Intune 添加应用

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

必须先向 Intune 添加应用，然后才能为用户管理和分配应用。 Intune 支持各种不同的应用类型，具体选项可能因每种类型而异。

Intune 支持添加并分配以下类型的应用：

![Intune 支持的应用类型](./media/app-types.png)

支持的平台如下。

- Android 应用商店应用
- Android 业务线 (LOB) 应用
- iOS App Store 应用
- iOS 业务线 (LOB) 应用
- Web 应用
- Windows Phone 8.1 应用商店应用
- Windows Phone 业务线应用（.xap 文件）
- Windows 应用商店应用
- Windows 业务线应用（仅适用于 .msi 文件）

>[!TIP]
> 业务线 (LOB) 应用不是从应用商店安装的应用，而是通过应用安装文件安装的应用。 例如，若要安装 iOS LOB 应用，请添加应用存档文件（扩展名为 .ipa）。 这些通常是内部编写的应用。

## <a name="before-you-start"></a>开始之前

在开始添加和分配应用之前，请考虑以下几点。

- 如果要从应用商店添加和分配应用，最终用户必须具有该应用商店的帐户才能安装应用。
- 某些分配的应用或项目可能依赖于内置的 iOS 应用。 例如，如果要从 iOS 应用商店分配一本书，则 iBooks 应用必须在设备上存在。 如果已经删除了 iBooks 内置应用，则无法使用 Intune 将其恢复。

## <a name="cloud-storage-space"></a>云存储空间
使用软件安装程序安装类型（例如，业务线应用）创建的所有应用都必须打包并上载到 Intune 云存储中。 Intune 的试用订阅包括 2 GB 的云存储空间，用于存储托管应用和更新。 完整订阅包括 20 GB 的存储空间。

可以使用原始购买方式购买额外的 Intune 存储空间。  如果是通过发票或信用卡付款，请访问[订阅管理门户](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)。  否则，请联系合作伙伴或销售内勤。

云存储空间的要求如下：

-   所有应用安装文件都必须位于同一文件夹内。
-   上载的任意文件的文件大小不得超过 2 GB。

## <a name="how-to-create-and-edit-categories-for-apps"></a>如何创建和编辑应用类别

应用类别可用于对应用进行排序，让用户在公司门户中更容易查找应用。 可以向应用分配一个或多个类别（例如，“开发者应用”或“通信应用”）。
向 Intune 添加应用时，可以视需要选择所需的类别。 请参阅平台专属主题，了解如何添加应用并分配类别。 若要创建和编辑你自己的类别，请按以下过程操作：

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“移动应用”。
4. 在“移动应用”工作负荷中，选择“设置” > “应用类别”。
5. “应用类别”边栏选项卡上显示当前类别列表。 选择执行下列操作之一：
    - **创建类别** - 在“创建类别”边栏选项卡上，输入新类别的名称。 只能使用一种语言输入名称，并且 Intune 不会进行翻译。 完成后，单击“创建”。
    - **编辑类别** - 对于列表中的任意一个类别，选择“...”。 在“属性”边栏选项卡上，可以输入类别的新名称，也可以删除类别。


## <a name="apps-added-automatically-by-intune"></a>Intune 自动添加的应用

之前，Intune 包含了一些可供快速分配的内置应用。 根据你的反馈，我们已将此列表删除，你将不再看到内置应用。
但是，如果你已分配任何内置应用，则在应用列表中仍会看到这些应用。 你可以根据需要继续分配这些应用。
在后续版本中，我们计划提供一种方法，以便用户可以更轻松地在 Azure 门户中选择并分配内置应用。

## <a name="next-steps"></a>后续步骤

请参阅下列主题之一，了解如何将各平台相关应用添加到 Intune 中：

- [Android 应用商店应用](store-apps-android.md)
- [Android LOB 应用](lob-apps-android.md)
- [iOS App Store 应用](store-apps-ios.md)
- [iOS LOB 应用](lob-apps-ios.md)
- [Web 应用（适用于所有平台）](web-app.md)
- [Windows Phone 8.1 应用商店应用](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB 应用](lob-apps-windows-phone.md)
- [Windows 应用商店应用](store-apps-windows.md)
- [Windows LOB 应用](lob-apps-windows.md)
- [适用于 Windows 10 的 Office 365 应用](apps-add-office365.md)

