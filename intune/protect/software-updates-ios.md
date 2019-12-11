---
title: 在 Microsoft Intune 中配置 iOS 软件更新策略 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建或添加配置策略，以限制软件更新在 iOS 设备上自动安装的时间。 可以选择不安装更新的日期和时间。 还可以将此策略分配给组、用户或设备，并检查是否存在任何安装故障。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f9750603d19d9b19697c7d2660351c4586432f6
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73984194"
---
# <a name="add-ios-software-update-policies-in-intune"></a>在 Intune 中添加 iOS 软件更新策略

软件更新策略可强制受监督的 iOS 设备自动安装可用的最新 OS 更新。 配置策略时，可以添加不希望设备安装更新的日期和时间。

此功能适用于：

- iOS 10.3 及更高版本（受监督）

设备大约每 8 小时查看一次 Intune。 如果有可用更新，则设备会下载并安装该更新，但在受限制的情况下除外。 尽管更新过程通常不涉及到任何用户交互，但如果设备有密码，则用户需要输入密码才能启动软件更新。 这适用于 iOS 10.3 及更高版本。 策略不会阻止用户手动更新 OS。

## <a name="configure-the-policy"></a>配置策略

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“软件更新”   > “适用于 iOS 的更新策略”   > “创建”  。
3. 在“基本信息”选项卡上，为该策略指定名称并指定描述（可选），然后选择“下一步”   。

   ![“基本信息”选项卡](./media/software-updates-ios/basics-tab.png) 

4. 在“更新策略设置”选项卡上，指定不强制安装更新时的限制期限  。  
   - 不支持夜间时段，如果选择，可能无法正常使用。 例如，请勿在“开始时间”为晚上 8 点和“结束时间”为早上 6 点的时间段期间配置策略   。
   - 凌晨 12 点开始到凌晨 12 点结束的策略会计算为 0 小时而不是 24 小时。 此配置结果没有限制。

   设置限制期限时，请输入以下详细信息：

   - **天**：可以选择星期几不安装更新。 例如，可以选中星期一、星期三和星期五，避免在这几天安装更新。
   - **时区**：选择时区。
   - **开始时间**：选择限期的开始时间。 例如，输入凌晨 5 点，避免从凌晨 5 开始安装更新。
   - **结束时间**：选择限制期限的结束时间。 例如，输入凌晨 1 点，避免从凌晨 1 开始安装更新。
  
   > [!IMPORTANT]  
   > 将开始时间和结束时间设为凌晨 12 点的策略计算为 0 小时，而不是 24 小时   。 其效果是不实施限制。  
    
   若要在受监管的 iOS 设备上延迟软件更新在特定时间内的可见性，请在[设备限制](../configuration/device-restrictions-ios.md#general)中配置这些设置。 软件更新策略会替代任何设备限制。 同时设置软件更新策略和延迟软件更新可见性限制时，设备将按策略强制执行软件更新。 应用此限制适后，用户不会看到自行更新设备的选项，将在 iOS 更新策略定义的第一个时间窗口推送更新。

   配置“更新策略设置”之后，选择“下一步”   。 

5. 若要将标记应用于更新策略，请在“作用域标记”选项卡上，选择“+ 选择作用域标记”以打开“选择标记”窗格    。
   
   - 在 **“选择标记”** 窗格中，选择一个或多个标记，然后单击 **“选择”** 以将其添加到策略，然后返回 *“作用域标记”* 窗格。  

   准备就绪后，选择“下一步”，转到“分配”   。

6. 在“分配”选项卡上，选择“+ 选择要包括的组”，然后将更新策略分配到一个或多个组   。 使用“+ 选择要排除的组”对分配进行相应调整  。 准备就绪后，选择“下一步”继续操作  。 

   需对策略目标用户所用的设备进行更新符合性评估。 此策略还支持无用户设备。

7. 在“查看 + 创建”选项卡中，查看设置，然后在已准备好保存 iOS 更新策略时选择“创建”   。 新策略显示在 iOS 更新策略列表中。


如需 Intune 支持团队的指导，请参阅[在 Intune 中为受监督的设备延迟软件更新可见性](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753)。

> [!NOTE]
> Apple MDM 不允许强制设备在特定时间或日期前安装更新。

## <a name="edit-a-policy"></a>编辑策略
可以编辑现有策略，包括更改限制时间：

1. 在“软件更新”中，选择“适用于 iOS 的更新策略”，然后选择要编辑的策略   。

2. 在查看策略“属性”时，为要修改的策略页面选择“编辑”   。  
   ![编辑策略](./media/software-updates-ios/edit-policy.png)   

3. 进行更改后，选择“查看 + 保存” > “保存”，保存所做的修改，然后返回策略“属性”    。  
 
> [!NOTE]
> 如果“开始时间”和“结束时间”都设为凌晨 12 点，则 Intune 不会检查有关更新安装时间的限制   。 这意味着将忽略已有的任何“选择阻止安装更新的时间”配置，结果是可以随时安装更新  。  


## <a name="monitor-device-installation-failures"></a>监视设备安装故障
<!-- 1352223 -->
“软件更新” > “iOS 设备安装故障”列出了虽是策略更新目标，但尝试更新后却未能成功更新的受监督 iOS 设备   。 可以查看每个设备的状态，了解该设备未自动更新的原因。 运行正常的最新版本设备不会显示在该列表中。 “最新版本”设备包括设备本身支持的最新更新。

## <a name="next-steps"></a>后续步骤

[监视其状态](../configuration/device-profile-monitor.md)。
