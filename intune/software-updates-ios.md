---
title: 在 Microsoft Intune 中配置 iOS 软件更新策略
titlesuffix: ''
description: 为 iOS 配置更新策略，强制受监视的 iOS 设备自动安装可用的最新软件更新。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 1d4223ae4feb417f77909b320cd0295347b44461
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
ms.locfileid: "31836582"
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>在 Microsoft Intune 中配置 iOS 更新策略

通过软件更新策略，可强制受监视的运行 iOS 10.3 及更高版本的 iOS 设备自动安装可用的最新 OS 更新。 此功能仅适用于受监视的设备。 可选择配置不希望设备安装更新的日期和时间。 

设备签入时，大约每隔 8 小时，如果有可用更新且不在限制时间期间，设备将尝试下载并安装最新的 OS 更新。 更新设备无需用户交互。 策略不会阻止用户更新 OS。

## <a name="configure-the-ios-update-policy"></a>配置 iOS 更新策略
1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“软件更新” > “iOS 更新策略”。
4. 在“策略”窗格中，选择“创建”，然后输入策略的名称和说明。
5. 选择“设置” > “配置”，然后输入 iOS 设备不强制安装最新更新时的详细信息。 可以配置星期、时区、开始时间和结束时间。
6. 选择“确定”保存此配置。 现将返回“创建更新策略”窗格。 选择“创建”以创建策略并保存设置。

配置文件随即创建并显示在“iOS 更新策略列表”窗格中。 Apple MDM 不允许强制设备在特定时间或日期前安装更新。 

## <a name="change-the-restricted-times-for-the-policy"></a>更改策略的限制时间

1.  在“软件更新”边栏选项卡上，选择“iOS 更新策略”。
2.  选择想要更新的 iOS 更新策略。
3.  选择“属性”，更新限制时间信息。
4.  选择星期
5.  将应用此策略的时区
6.  列入方块列表小时数的开始和结束时间

## <a name="assign-an-ios-update-policy-to-users"></a>向用户分配 iOS 更新策略

若要向用户分配 iOS 更新策略，请选择已配置的策略。 可在“软件更新” > “iOS 更新策略”窗格中找到现有策略。

1. 选择要分配给用户的策略，然后选择“分配”。 将打开一个窗格，可在其中选择 Azure Active Directory 安全组并将其分配给策略。
2. 选择“所选组”以打开显示 Azure AD 安全组的窗格。 可通过分配要包括的组和要排除的组，确定哪些用户有权访问策略。
3. 选择“保存”，将策略部署到用户。

你已将策略应用于用户或设备。 作为策略目标的用户所使用的设备将针对更新符合性进行评估。 此策略还支持无用户设备。

## <a name="monitor-ios-device-installation-failures"></a>监视 iOS 设备安装失败
<!-- 1352223 -->
可在“软件更新”窗格中获取“iOS 设备安装失败”报告。 在报告中，可以查看已作为 iOS 更新策略目标、已尝试更新但无法更新的受监督 iOS 设备的列表。 可以查看每个设备的状态，了解该设备未自动更新的原因。 运行正常的最新版本设备将不会显示在列表中。 我们将“最新版本”定义为设备本身可支持的最新更新。

