---
title: "如何在 Intune 中使用设备类别 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何使用用户在 Intune 中注册其设备时可以选择的设备类别。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1609ed2f127fe9d7d1f1c3b3e923bd12f1088200
ms.openlocfilehash: 41b3cfb8006a7390094d01b4f0fdc38417e858be


---

# <a name="map-device-groups"></a>映射设备组


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用 Microsoft Intune 设备类别可基于你定义的类别自动将设备添加到组，以便更轻松地管理这些设备。

设备类别使用以下工作流：
1.    创建用户在注册其设备时将进行选择的类别
4.    当最终用户注册其设备时，他们必须从你配置的类别列表中选择一个类别。 如果已注册了设备，则最终用户将需要在下次访问公司门户应用时选择类别。


可以创建任何所需的设备类别，例如：
- 销售点设备
- 演示设备
- 销售额
- 记帐
- Manager

## <a name="how-to-configure-device-categories"></a>如何配置设备类别

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>步骤 1 - 在 Azure 门户的“Intune”边栏选项卡中创建设备类别
1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“注册设备”。
3. 在“注册”边栏选项卡中，选择“设备类别”。
4. 在“设备类别”页上，选择“创建”以添加新类别。
5. 在下一个边栏选项卡中，输入新类别的“名称”和可选“说明”。
6. 完成后单击“**创建**”。 将在类别列表中看到刚才创建的类别。

在步骤 2 中创建 Azure Active Directory 安全组时将使用设备类别名称。

### <a name="step-2---create-azure-active-directory-security-groups"></a>步骤 2 - 创建 Active Directory 安全组
在此步骤中，你将在 Azure 门户中基于设备类别和设备类别名称创建动态组。

若要继续，请参阅 Azure Active Directory 文档中的主题[使用属性创建高级规则](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)。 

按照本部分中的信息可使用 **deviceCategory** 属性创建具有高级规则的设备组。 例如 (**device.deviceCategory -eq** "*<the device category name you got from the Intune portal>*")

在你配置设备组且用户注册其设备后，他们将看到你配置的类别的列表。 用户选择某个类别并完成注册后，其设备将添加到与其选择的类别相对应的 Active Directory 安全组。

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>如何查看所管理设备的类别
1.    在 Azure 门户的“Intune”边栏选项卡中，选择“设备和组”。

2.    在“管理”下，单击“所有设备”。

3.    在设备列表中，查看“类别”列。

如果未显示“类别”列，则单击“列”，从列表中选择“类别”，然后单击“应用”。

### <a name="to-change-the-category-of-a-device"></a>更改设备的类别

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备和组”。
4. 在“设备和组”边栏选项卡上，选择“管理” > “所有设备”。
5. 在设备列表中，选择所需设备，然后在“设备属性”边栏选项卡上选择“管理” > “属性”。
6. 在下一个边栏选项卡上，可以将所选设备的“设备类别”更改为之前配置的任一类别名称。



## <a name="further-information"></a>更多信息
- 可以在 Azure 门户中编辑设备类别，但如果这样做，则必须手动更新引用此类别的所有 Azure Active Directory 安全组。

- 删除某个类别后，分配到该类别的所有设备的类别名称随后都将显示“未分配”。





<!--HONumber=Feb17_HO2-->


