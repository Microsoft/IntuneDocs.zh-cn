---
title: "使用设备组映射对设备进行分类 | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: sumitp
ms.suite: ems
ms.sourcegitcommit: bb30b8e61a768b15e2f09993f4dceae8f4e1bd8a
ms.openlocfilehash: 55f811153bf37048a4fcdfc6da301a5f181700c3


---

# 使用 Microsoft Intune 中的设备组映射对设备进行分类
使用 Microsoft Intune **设备组映射**将设备分组为你定义的类别，以便更轻松地管理这些设备。 

设备组映射使用以下工作流：
1. 为要使用的每个类别创建 Intune 设备组。
2. 配置设备组映射规则，以便将所选的类别映射到所创建的设备组。
3. 当最终用户注册其设备时，他们必须从你配置的类别中选择一个类别。 选择后，他们的设备将自动添加到你创建的相应设备组。
4. 然后，你可以在部署策略和应用时使用这些设备组。

类别示例可能为：
* 个人
* 销售点设备
* 演示设备
* 销售额
* 记帐
* Manager

但是，你可以配置所需的任何类别。

## 如何配置设备组映射
1. 针对要使用的每个设备类别，创建一个 Intune 设备组。 有关如何创建组的信息，请参阅[通过 Microsoft Intune 使用组来管理用户和设备](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)。
2. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择**管理员**。
3. 在“管理”工作区中，展开“移动设备管理”，然后选择“设备组映射”。
4. 在“设备组映射”页上，启用设备组映射。
5. 选择“添加”以创建新的映射规则。
6. 在“添加设备组映射规则”对话框中，输入你想要创建的类别的名称，然后从下拉列表中选择要将此类别映射到的设备集合。 完成后选择“添加”。
7. 完成添加类别和组后，选择“保存”。

现在，当用户注册其设备时，他们将看到你配置的类别的列表。 选择某个类别并完成注册后，他们的设备将添加到与他们选择的类别相对应的设备组。

### 另请参阅
[通过 Microsoft Intune 使用组来管理用户和设备](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=Jun16_HO3-->


