---
title: "如何在 Intune 中将设备分类为组"
titleSuffix: Microsoft Intune
description: "了解如何将设备分类为组以便更轻松地管理。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 416ce4fb671494efabf805595426f25d027d256e
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2018
---
# <a name="categorize-devices-into-groups-for-easier-management"></a>将设备分类为组以便更轻松地管理

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 设备类别可基于你定义的类别自动将设备添加到组，以便更轻松地管理这些设备。

设备类别使用以下工作流：
1. 创建可供用户在注册设备时选择的类别
2. 当 iOS 和 Android 设备的最终用户注册其设备时，他们必须从你配置的类别列表中选择一个类别。 若要向 Windows 设备分配类别，最终用户必须使用“公司门户”网站（有关详细信息，请参阅本文中的“配置设备组后”）。
3. 你随后可以将策略和应用部署到这些组。

可以创建任何所需的设备类别，例如：
- 销售点设备
- 演示设备
- 销售额
- 记帐
- Manager

## <a name="how-to-configure-device-categories"></a>如何配置设备类别

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>步骤 1 - 在 Azure 门户的“Intune”边栏选项卡中创建设备类别
1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在“Intune”边栏选项卡上，选择“设备注册”。
3. 在“设备注册”边栏选项卡中，选择“设备类别”。
4. 在“设备类别”页上，选择“创建”以添加新类别。
5. 在“创建设备类别”边栏选项卡中，输入新类别的“名称”和可选“说明”。
6. 完成后，单击“创建”。 可以在类别列表中看到新类别。

在步骤 2 中创建 Azure Active Directory 安全组时将使用设备类别名称。

### <a name="step-2---create-azure-active-directory-security-groups"></a>步骤 2 - 创建 Active Directory 安全组
在此步骤中，你将在 Azure 门户中基于设备类别和设备类别名称创建动态组。

若要继续操作，请参阅 Azure Active Directory 文档中的[使用属性创建高级规则](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)一文。

按照本部分中的信息可使用 **deviceCategory** 属性创建具有高级规则的设备组。 例如，(device.deviceCategory -eq "<the device category name you got from the Azure portal>")

在你配置设备组且用户注册其设备后，他们将看到你配置的类别的列表。 用户选择某个类别并完成注册后，其设备将添加到与其选择的类别相对应的 Active Directory 安全组。

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>如何查看所管理设备的类别

1.  在 [Azure 门户](https://portal.azure.com)中，选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。

2. 在 Azure 门户的“Intune”边栏选项卡中，选择“设备”。

3.  在“管理”下，单击“所有设备”。

4.  在设备列表中，查看“设备类别”列。

如果未显示“设备类别”列，则单击“列”，从列表中选择“设备类别”，然后单击“应用”。

### <a name="to-change-the-category-of-a-device"></a>更改设备的类别

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“管理”部分下的“设备”边栏选项卡上，选择“所有设备”。
5. 在设备列表中，选择所需设备，然后在“管理”部分下的“设备属性”边栏选项卡上，选择“属性”。
6. 在下一个边栏选项卡上，可以将所选设备的“设备类别”更改为之前配置的任一类别名称。

## <a name="after-you-configure-device-groups"></a>配置设备组之后

当 iOS 和 Android 设备的最终用户注册其设备时，他们必须从你配置的类别列表中选择一个类别。 选择某个类别并完成注册后，他们的设备将添加到与他们选择的类别相对应的 Intune 设备组或 Active Directory 安全组。

Windows 上的最终用户应使用公司门户网站选择类别。

无论采用何种平台，最终用户在注册设备后始终可以转到 portal.manage.microsoft.com。 让用户访问公司门户网站，并转到“我的设备”。 他们可以选择页面上列出的一个已注册设备，然后选择一个类别。

选择类别后，该设备将自动添加到你创建的对应组。 在配置类别前，如果设备已经注册，则最终用户将会在“公司门户”网站上看到一个关于此设备的通知，并在下次从 iOS 或 Android 访问“公司门户”应用时被要求选择一个类别。

## <a name="further-information"></a>更多信息
- 虽然可以在 Azure 门户中编辑设备类别，但必须手动更新引用此类别的任何 Azure Active Directory 安全组。

- 如果删除设备分配到的类别，设备显示“未分配”类别名称。
