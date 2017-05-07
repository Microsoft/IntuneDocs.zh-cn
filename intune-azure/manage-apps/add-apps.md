---
title: "如何将应用添加到 Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：这些过程可助你将应用添加到 Intune，做好分配到用户和设备的准备。 "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: d85544bdfaa3a369e1d2d03e5454ff7aa2d75467
ms.lasthandoff: 04/19/2017

---

# <a name="how-to-add-an-app-to-microsoft-intune"></a>如何将应用添加到 Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

必需先将应用添加到 Intune，然后才能为用户管理和分配应用。 Intune 支持多种应用类型，每种类型的选项可能不同。

Intune 允许你添加和分配这些应用类型：

![添加 Intune 支持的类型](./media/app-types.png)

支持以下平台。 单击其中一个主题，深入了解如何添加每种应用类型。

- [Android 应用商店应用](/intune-azure/manage-apps/android-store-app)
- [Android LOB 应用](/intune-azure/manage-apps/android-lob-app)
- [iOS 应用商店应用](/intune-azure/manage-apps/ios-store-app)
- [iOS LOB 应用](/intune-azure/manage-apps/ios-lob-app)
- [Web 应用（适用于所有平台）](/intune-azure/manage-apps/web-app)
- [Windows Phone 8.1 应用商店应用](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Windows 应用商店应用](/intune-azure/manage-apps/windows-store-app)

此外，在设置租户时，Intune 会自动添加某些 Microsoft 应用。 在本主题的稍后部分可以找到这些应用的列表。

## <a name="before-you-start"></a>开始之前

在开始添加和分配应用之前，请考虑以下几点。

- 如果要从商店添加和部署应用，最终用户必须具有该商店的帐户才能安装应用。
- 某些部署的应用或项目可能依赖于内置的 iOS 应用。 例如，如果要从 iOS 应用商店部署一本书，则 iBooks 应用必须在设备上存在。 如果已经删除了 iBooks 内置应用，则无法使用 Intune 将其恢复。

## <a name="cloud-storage-space"></a>云存储空间
使用软件安装程序安装类型（例如，业务线应用）创建的所有应用都必须打包并上传到 Microsoft Intune 云存储空间。 Intune 的试用订阅包括 2 千兆字节 (GB) 基于云的存储，用于存储托管应用和更新。 完全订阅包括 20 GB 的存储空间。

可以使用原始购买方法购买额外的 Intune 存储空间。  如果通过发票或信用卡付款，请访问[订阅管理门户](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)。  否则，请联系合作伙伴或销售人员。

云存储空间的要求如下：

-   所有应用安装文件必须位于同一文件夹。
-   上传的任意文件的最大文件大小是 2 GB。

## <a name="how-to-create-and-edit-categories-for-apps"></a>如何创建和编辑应用类别

可使用应用类别帮助排列应用，让最终用户在公司门户中更易找到相关应用。 可以向应用分配一个或多个类别，例如“开发人员应用”或“通信应用”。
将应用添加到 Intune 时，可以选择所需类别。 使用特定于平台的主题来添加应用，并分配类别。 若要创建和编辑自己的类别，请使用以下过程：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
4. 在“移动应用”工作负荷中，选择“设置” > “应用类别”。
5. 在“应用类别”边栏选项卡上，将显示当前类别的列表。 选择下列其中一项操作：
    - **创建类别** - 在“创建类别”边栏选项卡上，输入新类别的名称。 只能使用一种语言输入名称，Intune 不会对其进行翻译。 完成后单击“**创建**”。
    - **编辑类别** - 对于列表中的任何类别，选择“‘...’”。 在“属性”边栏选项卡上，可以为类别输入新名称，或删除类别。


## <a name="apps-added-automatically-by-intune"></a>通过 Intune 自动添加的应用

以下由 Microsoft 发布的应用内置于 Intune，并且可供分配：

|||
|-|-|
|Name|平台|应用类型|
|Azure 信息保护|Android|托管的 Android 应用商店应用|
|适用于手机的 Dynamics CRM|Android|托管的 Android 应用商店应用|
|适用于平板电脑的 Dynamics CRM|Android|托管的 Android 应用商店应用|
|Excel|iOS|托管的 iOS 应用商店应用|
|Excel|Android|托管的 Android 应用商店应用|
|Managed Browser|Android|托管的 Android 应用商店应用|
|Managed Browser|iOS|托管的 iOS 应用商店应用|
|适用于手机的 Microsoft Dynamics CRM|iOS|托管的 iOS 应用商店应用|
|适用于平板电脑的 Microsoft Dynamics CRM|iOS|托管的 iOS 应用商店应用|
|Microsoft Power BI|iOS|托管的 iOS 应用商店应用|
|Microsoft Power BI|Android|托管的 Android 应用商店应用|
|Microsoft SharePoint|iOS|托管的 iOS 应用商店应用|
|Microsoft SharePoint|Android|托管的 Android 应用商店应用|
|Microsoft Teams|Android|托管的 Android 应用商店应用|
|Microsoft Teams|iOS|托管的 iOS 应用商店应用|
|OneDrive|iOS|托管的 iOS 应用商店应用|
|OneDrive|Android|托管的 Android 应用商店应用|
|OneNote|iOS|托管的 iOS 应用商店应用|
|Outlook|Android|托管的 Android 应用商店应用|
|Outlook|iOS|托管的 iOS 应用商店应用|
|Outlook 组|Android|托管的 Android 应用商店应用|
|Outlook 组|iOS|托管的 iOS 应用商店应用|
|PowerPoint|iOS|托管的 iOS 应用商店应用|

