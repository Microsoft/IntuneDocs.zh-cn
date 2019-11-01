---
title: 使用应用保护策略条件启动操作擦除数据
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中使用应用保护策略条件启动操作选择性地擦除数据。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 882c542d6a1d981b9924bb33eee40f03b41689f7
ms.sourcegitcommit: 4bf23327af734a9811d555fbd566c31239e2acd6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "72999479"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>在 Intune 中使用应用保护策略条件启动操作选择性地擦除数据

使用 Intune 应用保护策略，可配置设置以阻止最终用户访问公司应用或帐户。 这些设置的目标是组织为越狱设备和最低 OS 版本等内容所设置的数据重定位和访问要求。
 
通过使用这些设置，可显式选择从最终用户的设备上擦除公司数据，作为对违规行为所采取的措施。 对于某些设置，可根据不同的指定值配置多项操作，例如阻止访问和擦除数据。

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>使用条件启动操作创建应用保护策略

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格中，选择“客户端应用” > “应用保护策略”    。
4. 单击“添加策略”（也可编辑现有策略）  。 
5. 单击“配置所需设置”，查看可为策略配置的设置列表  。 
6. 在“设置”窗格中向下滚动，将会看到标题为“条件启动”  的部分，内含可编辑的表。

    ![Intune 应用保护访问操作的屏幕截图](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions01.png)

7. 选择“设置”，然后输入用户登录公司应用时必须满足的值   。 
8. 如果用户不符合要求，请选择要采取的操作  。 在某些情况下，可为单个设置配置多项操作。 有关详细信息，请参阅[如何创建和分配应用保护策略](app-protection-policies.md)。

>[!NOTE]
> 要使用“设备型号或设备制造商”设置，请输入以分号分隔的设备型号标识符列表 (iOS) 或设备制造商 (Android)  。 切勿在多值列表中使用空格。 这些值不区分大小写。 

## <a name="policy-settings"></a>策略设置 

应用保护策略设置表包含“设置”、“值”和“操作”列    。

### <a name="ios-policy-settings"></a>iOS 策略设置
对于 iOS，可使用“设置”下拉列表为以下设置配置操作  ：
- 最大 PIN 尝试次数
- 离线宽限期
- 已越狱/获得 root 权限的设备
- 最低 OS 版本
- 最低应用版本
- 最低 SDK 版本
- 设备型号
- 允许的最高设备威胁级别

若要使用“设备型号”  设置，请输入 iOS 型号标识符的分号分隔列表。 [HockeyApp 支持文档](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types)中的“设备类型”列下列出了 iOS 型号标识符。<br>
示例输入：iPhone5,2;iPhone5,3 

在最终用户设备上，Intune 客户端执行操作的依据为，Intune 中指定的设备型号字符串与应用程序保护策略的简单匹配情况。 匹配完全取决于设备报告的内容。 建议你（即 IT 管理员）务必要根据各种设备制造商和型号对小型用户组测试此设置，以确保行为按预期发生。 默认值为“未配置”  。<br>
请设置下列操作之一： 
- 允许指定项（阻止非指定项）
- 允许指定项（擦除非指定项）

**如果 IT 管理员对定目标到同一 Intune 用户的相同应用的策略输入不同的 iOS 型号标识符列表，会发生什么？**<br>
如果两个应用保护策略在已配置的值方面存在冲突，Intune 通常会采用限制性最强的方法。 因此，向下发送到目标 Intune 用户正打开的目标应用的策略是，定目标到相同应用/用户组合的“策略 A”  和“策略 B”  中列出的 iOS 型号标识符的交集。 例如，如果“策略 A”指定“iPhone5,2; iPhone5,3”，而“策略 B”指定“iPhone5,3”，则当“策略 A”和“策略 B”以 Intune 用户为目标时，组合的原则将是“iPhone5,3”     。 

### <a name="android-policy-settings"></a>Android 策略设置

对于 Android，可使用“设置”下拉列表为以下设置配置操作  ：
- 最大 PIN 尝试次数
- 离线宽限期
- 已越狱/获得 root 权限的设备
- 最低 OS 版本
- 最低应用版本
- 最低修补程序版本
- 设备制造商
- SafetyNet 设备证明
- 要求对应用进行威胁扫描
- 最小公司门户版本
- 允许的最高设备威胁级别

通过使用最小公司门户版本  ，可以指定在最终用户设备上强制执行的公司门户的特定最低定义版本。 使用此条件启动设置，可以在不满足每个值时将值设置为“阻止访问”、“擦除数据”和“警告”作为可能的操作    。 此值的可能格式遵循 [主版本].[次版本]、[主版本].[次版本].[内部版本] 或 [主版本].[次版本].[内部版本].[修订版本]    。 假设某些最终用户可能不希望立即强制更新应用，则在配置此设置时，“警告”选项可能是理想的选择。 Google Play 商店能够很好地仅为应用更新发送增量字节，但在更新数据时，仍可能有大量数据是用户不想使用的。 强制执行更新并下载更新的应用可能会导致更新时产生意外的数据费用。 如果已配置最小公司门户版本设置，则将影响获取公司门户版本 5.0.4560.0 的任何最终用户以及公司门户的任何未来版本  。 此设置对使用版本低于与此功能一起发布的公司门户版本的用户没有任何影响。 在设备上使用应用自动更新的最终用户可能看不到此功能的任何对话框，因为他们可能使用最新的公司门户版本。 此设置仅适用于已注册和未注册设备具有应用保护的 Android。

若要使用“设备制造商”  设置，请输入 Android 制造商的分号分隔列表。 可以在设备设置下找到设备的 Android 制造商。<br>
示例输入：制造商 A;制造商 B  

>[!NOTE]
> 以下是使用 Intune 报告自设备的一些常见制造商，可以用作输入：Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

在最终用户设备上，Intune 客户端执行操作的依据为，Intune 中指定的设备型号字符串与应用程序保护策略的简单匹配情况。 匹配完全取决于设备报告的内容。 建议你（即 IT 管理员）务必要根据各种设备制造商和型号对小型用户组测试此设置，以确保行为按预期发生。 默认值为“未配置”  。<br>
请设置下列操作之一： 
- 允许指定项（阻止非指定项）
- 允许指定项（擦除非指定项）

**如果 IT 管理员对定目标到同一 Intune 用户的相同应用的策略输入不同的 Android 制造商列表，会发生什么？**<br>
如果两个应用保护策略在已配置的值方面存在冲突，Intune 通常会采用限制性最强的方法。 因此，向下发送到目标 Intune 用户正打开的目标应用的策略是，定目标到相同应用/用户组合的“策略 A”  和“策略 B”  中列出的 Android 制造商的交集。 例如，如果“策略 A”指定“Google; Samsung”，而“策略 B”指定“Google”，则当“策略 A”和“策略 B”以 Intune 用户为目标时，组合的原则将是“Google”     。 

### <a name="additional-settings-and-actions"></a>其他设置和操作 

默认情况下，如果将“需要 PIN 才能进行访问”设置设置为“是”，则该表将填充行配置为“脱机宽限期”和“最大 PIN 尝试次数”的设置     。
 
要配置设置，请从“设置”列下方的下拉列表中选择一项设置  。 选择设置后，如果需要设置值，则可在同一行的“值”列下启用可编辑的文本框  。 此外，将在“操作”列下启用下拉列表，其中条件启动操作适用于该设置  。 

以下列表提供了常见的操作列表：
- **阻止访问** - 阻止最终用户访问公司应用。
- **擦除数据** - 擦除最终用户设备上的公司数据。
- **警告** - 向最终用户提供对话框作为警告消息。

在某些情况下，例如“最低 OS 版本”设置，根据不同的版本号，可将该设置配置为执行所有适用的操作  。 

![应用保护访问操作的屏幕截图 - 最低 OS 版本](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions05.png)

完成设置配置后，该行将显示在只读视图中，可随时对其进行编辑。 此外，该行将显示一个可在“设置”列中选择的下拉列表  。 将无法在下拉列表中选择已配置且不允许多项操作的设置。

## <a name="next-steps"></a>后续步骤

了解有关 Intune 应用保护策略的详细信息，请参阅：
- [如何创建和分配应用保护策略](app-protection-policies.md)
- [iOS 应用保护策略设置](app-protection-policy-settings-ios.md)
- [Microsoft Intune 中的 Android 应用保护策略设置](app-protection-policy-settings-android.md) 
