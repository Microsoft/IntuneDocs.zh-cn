---
title: 在 Microsoft Intune 中配置 iOS 软件更新策略 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建或添加配置策略，以限制在由 Intune 管理或监督的 iOS 设备上自动安装软件更新的时间。 可以选择不安装更新的日期和时间。 还可以将此策略分配给组、用户或设备，并检查是否存在任何安装故障。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a5c9dea847ace51c7d6f06cfa43c44beead18f8
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373418"
---
# <a name="add-ios-software-update-policies-in-intune"></a>在 Intune 中添加 iOS 软件更新策略

软件更新策略可强制受监督的 iOS 设备自动安装可用的最新 OS 更新。 配置策略时，可以添加不希望设备安装更新的日期和时间。 

此功能适用于：

- iOS 10.3 及更高版本（受监督）

设备大约每 8 小时查看一次 Intune。 若有可用更新，并且不在限制时间内，则设备会下载并安装最新的 OS 更新。 更新设备无需任何用户交互。 策略不会阻止用户手动更新 OS。

## <a name="configure-the-policy"></a>配置策略

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“软件更新”   > “适用于 iOS 的更新策略”   > “创建”  。
3. 输入以下设置：

    - **名称**：输入软件更新策略的名称。 例如，输入 `iOS restricted update times`。
    - **说明**：输入策略的说明。 此设置是可选的，但建议进行。

4. 选择“设置”>“配置”  。 输入以下设置：

    - **选择阻止安装更新的时间**：指定期间不强制安装更新的限制期限。 
      - 不支持夜间时段，如果选择，可能无法正常使用。 例如，请勿在“开始时间”为晚上 8 点和“结束时间”为早上 6 点的时间段期间配置策略   。
      - 凌晨 12 点开始和凌晨 12 点结束的策略会计算为 0 小时而不是 24 小时，结果是没有限制。

      设置限制期限时，请输入以下详细信息：

      - **天**：可以选择星期几不安装更新。 例如，可以选中星期一、星期三和星期五，避免在这几天安装更新。
      - **时区**：选择时区。
      - **开始时间**：选择限期的开始时间。 例如，输入凌晨 5 点，避免从凌晨 5 开始安装更新。
      - **结束时间**：选择限制期限的结束时间。 例如，输入凌晨 1 点，避免从凌晨 1 开始安装更新。

    - **在不更改计划更新的情况下延迟最终用户看到软件更新的时间（天数）** ： 

      **此设置已移动至[设备限制](device-restrictions-ios.md#general)。它将从门户中的此位置中删除**。 在短时间内，可在此处更改现有策略。 大约一个月之后，将从现有策略中删除此设置。

      若要限制设置的影响程度，建议：
        - 从门户中的此位置中删除现有策略。
        - 创建新的[设备限制策略](device-restrictions-ios.md#general)。
        - 目标用户与原始策略的目标用户相同。

      如果存在冲突，此设置不产生效果，除非两个值相同  。 若要防止冲突，请确保从门户中的此位置中更改或删除现有策略。
      > [! 重要事项]  
      > 将开始时间和结束时间设为凌晨 12 点的策略计算为 0 小时，而不是 24 小时   。 其效果是不实施限制。  

5. 选择“确定” > “创建”以保存更改并创建策略   。

配置文件随即创建并显示在策略列表中。

如需 Intune 支持团队的指导，请参阅[在 Intune 中为受监督的设备延迟软件更新可见性](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753)。

> [!NOTE]
> Apple MDM 不允许强制设备在特定时间或日期前安装更新。

## <a name="change-the-restricted-times-for-the-policy"></a>更改策略的限制时间

1. 在“软件更新”中，选择“适用于 iOS 的更新策略”   。
2. 选择一个现有策略，然后选择“属性”  。
3. 更新限制时间：

    1. 选择星期
    2. 选择应用此策略的时区
    3. 输入列入阻止列表小时的开始和结束时间

    > [!NOTE]
    > 如果开始时间和结束时间都设为凌晨 12 点，则 Intune 不会检查有关更新安装时间的限制   。 这意味着将忽略已有的任何“选择阻止安装更新的时间”配置，结果是可以随时安装更新  。  

## <a name="assign-the-policy-to-users"></a>将策略分配给用户

可将现有策略分配给组、用户或设备。 分配后，将应用该策略。

1. 在“软件更新”中，选择“适用于 iOS 的更新策略”   。
2. 选择一个现有策略，然后选择“分配”  。 
3. 选择要包含在此策略中或要从中排除的 Azure Active Directory 组、用户或设备。
4. 选择“保存”，将策略部署到组  。

需对策略目标用户所用的设备进行更新符合性评估。 此策略还支持无用户设备。

## <a name="monitor-device-installation-failures"></a>监视设备安装故障
<!-- 1352223 -->
“软件更新” > “iOS 设备安装故障”列出了虽是策略更新目标，但尝试更新后却未能成功更新的受监督 iOS 设备   。 可以查看每个设备的状态，了解该设备未自动更新的原因。 运行正常的最新版本设备不会显示在该列表中。 “最新版本”设备包括设备本身支持的最新更新。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
