---
title: "如何将应用添加到Microsoft Intune | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：这些过程可助你将应用添加到 Intune，做好分配到用户和设备的准备。 "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 969ce8deae9142944f3481172277dc252baa5779
ms.openlocfilehash: a7838f57b2eb8bd36a875f7b5b001b12eafcbf8d

---

# <a name="how-to-add-an-app"></a>如何添加应用 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

必需先将应用添加到 Intune，然后才能为用户管理和分配应用。 Intune 支持多种应用类型，每种类型的选项可能不同。

Intune 支持添加和分配以下应用类型：

![添加 Intune 支持的类型](./media/app-types.png)

支持以下平台。 单击其中一个主题，深入了解如何添加每种应用类型。

- [Android 业务线应用](/intune-azure/manage-apps/android-lob-app)
- [Android 应用商店应用](/intune-azure/manage-apps/android-store-app)
- [iOS 业务线应用](/intune-azure/manage-apps/ios-lob-app)
- [iOS 应用商店应用](/intune-azure/manage-apps/ios-store-app)
- [Web 应用（适用于所有平台）](/intune-azure/manage-apps/web-app)
- [Windows Phone 8.1 应用商店应用](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Windows 应用商店应用](/intune-azure/manage-apps/windows-store-app)

> [!NOTE]
> 如果要从商店添加和部署应用，最终用户必须具有该商店的帐户才能安装应用。

## <a name="how-to-create-and-edit-categories-for-apps"></a>如何创建和编辑应用类别 

可使用应用类别帮助排列应用，让最终用户在公司门户中更易找到相关应用。 可以向应用分配一个或多个类别，例如“开发人员应用”或“通信应用”。 将应用添加到 Intune 时，可以选择所需类别。 使用特定于平台的主题来添加应用，并分配类别。 若要创建和编辑自己的类别，请使用以下过程： 

1. 登录到 Azure 门户中。 
2. 选择“更多服务” > “监视 + 管理” > “Intune”。 
3. 在“Intune”边栏选项卡上，选择“管理应用”。 
4. 在“移动应用”工作负荷中，选择“设置” > “应用类别”。 
5. 在“应用类别”边栏选项卡上，将显示当前类别的列表。 选择下列其中一项操作： 
    - **创建类别** - 在“创建类别”边栏选项卡上，输入新类别的名称。 只能使用一种语言输入名称，Intune 不会对其进行翻译。 完成后单击“**创建**”。
    - **编辑类别** - 对于列表中的任何类别，选择“‘...’”。 在“属性”边栏选项卡上，可以为类别输入新名称，或删除类别。 --->






<!--HONumber=Feb17_HO1-->


