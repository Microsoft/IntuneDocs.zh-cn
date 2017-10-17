---
title: "使用设备组映射对设备进行分类"
description: "使用 Microsoft Intune 设备组映射将设备分组为你定义的类别，以便更轻松地管理这些设备。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d6783f0dbf21d8bb1e652522df7ae1f37cbf4ffd
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="categorize-devices-with-device-group-mapping-in-microsoft-intune"></a>使用 Microsoft Intune 中的设备组映射对设备进行分类

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune 设备组映射可基于你定义的类别自动将设备添加到组，以便更轻松地管理这些设备。 

设备组映射使用以下工作流：
1. 创建用户在注册其设备时将进行选择的类别
2. 可为要使用的每个类别创建组或使用现有组。 根据所使用的 Intune 版本，这些组是 Intune 组或 Azure Active Directory 安全组。
2. 配置将所选类别映射到所创建的设备组的规则。
3. 当 iOS 和 Android 设备的最终用户注册其设备时，他们必须从你配置的类别列表中选择一个类别。 若要向 Windows 设备分配一个类别，最终用户必须使用“公司门户”网站（请参阅本主题中的“配置设备组之后”了解详细信息）。
4. 你随后可以将策略和应用部署到这些组。

可以创建任何所需的设备类别，例如：
* 销售点设备
* 演示设备
* 销售额
* 记帐
* Manager

## <a name="important-information-about-a-change-in-group-management-for-intune"></a>有关 Intune 组管理中的更改的重要信息

基于反馈，我们正在跨企业移动性 + 安全性统一分组和目标体验。 因此，我们很快会将 Intune 组转换为基于 Azure Active Directory 的安全组。 进行此更改之后，你将不会再使用 Intune 创建组。 而是会在 Azure 门户中创建它们。 此更改会逐步进行，你可以在[本主题](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)中阅读有关此更改及其时间线的完整详细信息。

### <a name="which-procedure-in-this-topic-should-you-use-to-configure-device-group-mapping"></a>应使用本主题中的哪个过程来配置设备组映射？

由于基于 Azure Active Directory 的安全组的分阶段实现，因此必须在 [Intune 管理控制台](https://manage.microsoft.com)中打开“组”工作区来确定要使用的过程：

-  如果看到指向 Azure 门户的链接，则不会再使用 Intune 组。 遵循[如何为 Azure Active Directory 组配置设备组映射](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-azure-active-directory-groups)中的以下步骤。
-  如果未看到指向 Azure 门户的链接，则仍在使用 Intune 组。 遵循[如何为 Intune 组配置设备组映射](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-intune-groups)中的以下步骤。

## <a name="how-to-configure-device-group-mapping-for-intune-groups"></a>如何为 Intune 组配置设备组映射
1. 针对要使用的每个设备类别，创建一个 Intune 设备组，或标识一个现有组。 有关如何创建组的信息，请参阅[通过 Microsoft Intune 使用组来管理用户和设备](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)。
2. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择**管理员**。
3. 在“管理”工作区中，展开“移动设备管理”，然后选择“设备组映射”。
4. 在“设备组映射”页上，启用设备组映射。
5. 选择“添加”以创建新的映射规则。
6. 在“添加设备组映射规则”对话框中，输入你想要创建的类别的名称，然后从下拉列表中选择要将此类别映射到的设备集合。 完成后选择“添加”。
7. 完成添加类别和组后，选择“保存”。



## <a name="how-to-configure-device-group-mapping-for-azure-active-directory-groups"></a>如何为 Azure Active Directory 组配置设备组映射

### <a name="step-1---create-device-categories-in-the-intune-administration-console"></a>步骤 1 - 在 Intune 管理控制台中创建设备类别
1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“管理员”。
3. 在“管理”工作区中，展开“移动设备管理”，然后选择“设备类别”。
4. 在“设备类别”页上，你会看到一个列表，可以在其中配置设备类别： 
- 可以输入名称，然后单击“添加”以将它添加为新的设备类别。
- 此外，可以选择类别，然后“删除”它。

在步骤 2 中创建 Azure Active Directory 安全组时将使用设备类别名称。

### <a name="step-2---create-azure-active-directory-security-groups"></a>步骤 2 - 创建 Active Directory 安全组

在此步骤中，你将在 Azure 门户中基于设备类别和设备类别名称创建动态组。

若要继续，请参阅 Azure Active Directory 文档中的主题[使用属性创建高级规则](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)。
按照本主题中的信息可使用“deviceCategory”属性创建具有高级规则的设备组。
例如 (**device.deviceCategory -eq** "<*从 Intune 管理控制台获取的设备类别名称*>")


## <a name="after-you-configure-device-groups"></a>配置设备组之后

当 iOS 和 Android 设备的最终用户注册其设备时，他们必须从你配置的类别列表中选择一个类别。 选择某个类别并完成注册后，他们的设备将添加到与他们选择的类别相对应的 Intune 设备组或 Active Directory 安全组。

若要向 Windows 设备分配一个类别，注册设备后最终用户必须使用“公司门户”网站 (portal.manage.microsoft.com)。 在 Windows 设备上，访问此网站并转到“菜单” > “我的设备”。 选择页面上列出的一个已注册设备，然后选择一个类别。 

选择类别后，该设备将自动添加到你创建的对应组。 在配置类别前，如果设备已经注册，则最终用户将会在“公司门户”网站上看到一个关于此设备的通知，并在下次从 iOS 或 Android 访问“公司门户”应用时被要求选择一个类别。



### <a name="see-also"></a>另请参阅
[通过 Microsoft Intune 使用组来管理用户和设备](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
