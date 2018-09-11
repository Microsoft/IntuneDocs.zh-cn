---
title: 在 Microsoft Intune 中配置 iOS 软件更新策略 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建或添加配置策略，以限制在由 Intune 管理或监督的 iOS 设备上自动安装软件更新的时间。 可以选择不安装更新的日期和时间。 还可以将此策略分配给组、用户或设备，并检查是否存在任何安装故障。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 1fe0258d3b6d9092c032184fca5fc0f8dc3f12df
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313490"
---
# <a name="configure-ios-update-policies-in-intune"></a>在 Intune 中配置 iOS 更新策略

软件更新策略可强制受监督的 iOS 设备自动安装可用的最新 OS 更新。 此功能仅适用于受监视的设备。 配置策略时，可以添加不希望设备安装更新的日期和时间。 

设备大约每 8 小时查看一次 Intune。 若有可用更新，并且不在限制时间内，则设备会下载并安装最新的 OS 更新。 更新设备无需任何用户交互。 策略不会阻止用户手动更新 OS。

此功能支持运行 iOS 10.3 及更高版本的设备。

## <a name="configure-the-policy"></a>配置策略
1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“软件更新” > “适用于 iOS 的更新策略” > “创建”。
4. 输入策略的名称和描述。
5. 选择“设置”。 

    输入 iOS 设备不强制安装最新更新时的详细信息。 这些设置会创建受限制的时间范围。 可以配置一周里的一天、时区、开始时间、结束时间，以及是否延迟软件更新的可见性(天)，以便输入用户。 可以选择软件更新的延迟范围（1 到 90 天）。 若要选择退出设置软件更新延迟，请输入 0。 这些更新设置将仅应用于受监管的 iOS 设备。

6. 选择“确定”，保存所做更改。 选择“创建”以创建策略。

配置文件随即创建并显示在策略列表中。 Apple MDM 不允许强制设备在特定时间或日期前安装更新。 

## <a name="change-the-restricted-times-for-the-policy"></a>更改策略的限制时间

1. 在“软件更新”中，选择“适用于 iOS 的更新策略”。
2. 选择一个现有策略，然后选择“属性”。
3. 更新限制时间：

    1. 选择星期
    2. 选择应用此策略的时区
    3. 输入列入黑名单小时的开始和结束时间

    > [!NOTE]
    > 如果“开始时间”和“结束时间”都设置为中午 12 点，则会关闭维护时间检查。

## <a name="assign-the-policy-to-users"></a>将策略分配给用户

可将现有策略分配给组、用户或设备。 分配后，将应用该策略。

1. 在“软件更新”中，选择“适用于 iOS 的更新策略”。
2. 选择一个现有策略，然后选择“分配”。 
3. 选择要包含在此策略中或要从中排除的 Azure Active Directory 组、用户或设备。
4. 选择“保存”，将策略部署到组。

需对策略目标用户所用的设备进行更新符合性评估。 此策略还支持无用户设备。

## <a name="monitor-device-installation-failures"></a>监视设备安装故障
<!-- 1352223 -->
“软件更新” > “iOS 设备安装故障”列出了虽是策略更新目标，但尝试更新后却未能成功更新的受监督 iOS 设备。 可以查看每个设备的状态，了解该设备未自动更新的原因。 运行正常的最新版本设备不会显示在该列表中。 “最新版本”设备包括设备本身支持的最新更新。

