---
title: 使用应用保护策略访问操作选择性地擦除数据
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中使用应用保护策略访问操作选择性地擦除数据。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2cfd426a0ae7165a7aae60a90d104852fd834db6
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909110"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>在 Intune 中使用应用保护策略访问操作选择性地擦除数据

使用 Intune 应用保护策略，可配置设置以阻止最终用户访问公司应用或帐户。 这些设置的目标是组织为越狱设备和最低 OS 版本等内容所设置的数据重定位和访问要求。
 
通过使用这些设置，可显式选择从最终用户的设备上擦除公司数据，作为对违规行为所采取的措施。 对于某些设置，可根据不同的指定值配置多项操作，例如阻止访问和擦除数据。

## <a name="create-an-app-protection-policy-using-access-actions"></a>使用访问操作创建应用保护策略

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。  
    Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“移动应用” > “应用保护策略”。
4. 单击“添加策略”（也可编辑现有策略）。 
5. 单击“配置所需设置”，查看可为策略配置的设置列表。 
6. 通过在“设置”窗格中向下滚动，将看到标题为“访问操作”的部分，其中包含可编辑的表。

    ![Intune 应用保护访问操作的屏幕截图](./media/apps-selective-wipe-access-actions01.png)

7. 选择“设置”，然后输入用户登录公司应用时必须满足的值。 
8. 如果用户不符合要求，请选择要采取的操作。 在某些情况下，可为单个设置配置多项操作。 有关详细信息，请参阅[如何创建和分配应用保护策略](app-protection-policies.md)。

>[!NOTE]
> 要使用“设备型号”设置，请输入以分号分隔的型号标识符列表。 

## <a name="policy-settings"></a>策略设置 

应用保护策略设置表包含“设置”、“值”和“操作”列。

对于 iOS，可使用“设置”下拉列表为以下设置配置操作：
-  最大 PIN 尝试次数
-  离线宽限期
-  已越狱/获得 root 权限的设备
-  最低 OS 版本
-  最低应用版本
-  最低 SDK 版本
-  设备型号

对于 Android，可使用“设置”下拉列表为以下设置配置操作：
-  最大 PIN 尝试次数
-  离线宽限期
-  已越狱/获得 root 权限的设备
-  最低 OS 版本
-  最低应用版本
-  最低修补程序版本
-  设备制造商

默认情况下，如果将“需要 PIN 才能进行访问”设置设置为“是”，则该表将填充行配置为“脱机宽限期”和“最大 PIN 尝试次数”的设置。
 
要配置设置，请从“设置”列下方的下拉列表中选择一项设置。 选择设置后，如果需要设置值，则可在同一行的“值”列下启用可编辑的文本框。 此外，将在“操作”列下启用下拉列表，其中条件启动操作适用于该设置。 

以下列表提供了常见的操作列表：
-  **阻止访问** - 阻止最终用户访问公司应用。
-  **擦除数据** - 擦除最终用户设备上的公司数据。
-  **警告** - 向最终用户提供对话框作为警告消息。

### <a name="additional-settings-and-actions"></a>其他设置和操作 

在某些情况下，例如“最低 OS 版本”设置，根据不同的版本号，可将该设置配置为执行所有适用的操作。 

![Intune 应用保护访问操作的屏幕截图 - 最低 OS 版本](./media/apps-selective-wipe-access-actions05.png)

完成设置配置后，该行将显示在只读视图中，可随时对其进行编辑。 此外，该行将显示一个可在“设置”列中选择的下拉列表。 将无法在下拉列表中选择已配置且不允许多项操作的设置。

## <a name="next-steps"></a>后续步骤

了解有关 Intune 应用保护策略的详细信息，请参阅：
- [如何创建和分配应用保护策略](app-protection-policies.md)
- [iOS 应用保护策略设置](app-protection-policy-settings-ios.md)
- [Microsoft Intune 中的 Android 应用保护策略设置](app-protection-policy-settings-android.md) 


