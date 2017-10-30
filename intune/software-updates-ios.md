---
title: "配置 iOS 更新策略"
titlesuffix: Azure portal
description: "为 iOS 配置更新策略，强制受监视的 iOS 设备自动安装可用的最新软件更新。"
keywords: 
author: dougeby
manager: dougeby
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6334421-85e1-4457-9c44-e5db8d4ee00e
ms.openlocfilehash: 199760a60ee2290560ebdf933192de0eaf569e9e
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2017
---
# <a name="configure-ios-update-policies"></a>配置 iOS 更新策略
通过 iOS 的更新策略，可强制受监视的 iOS 设备自动安装可用的最新软件更新。 可选择配置不希望设备安装更新的日期和时间。

## <a name="configure-the-ios-update-policy"></a>配置 iOS 更新策略
1. 转到 Azure 门户中的“Intune”边栏选项卡。
2. 在“Intune”边栏选项卡上，选择“软件更新” > “iOS 更新策略”。
4. 在策略边栏选项卡上，选择“创建”，然后输入策略的名称和描述。
5. 选择“设置” > “配置”，然后输入 iOS 设备不强制安装最新更新时的详细信息。
6. 选择“确定”保存此配置。 现将返回“创建更新策略” 边栏选项卡。 选择“创建”以创建策略并保存设置。

系统将创建配置文件，并在“iOS 更新策略列表”边栏选项卡上显示。

## <a name="assign-an-ios-update-policy-to-users"></a>向用户分配 iOS 更新策略
若要向用户分配 iOS 更新策略，请选择已配置的策略。 可在“软件更新” > “iOS 更新策略”边栏选项卡中找到现有策略。
1. 选择要分配给用户的策略，然后选择“分配”。 将打开一个边栏选项卡，可在其中选择 Azure Active Directory 安全组并将其分配给策略。
2. 选择“选择组”以打开显示 Azure AD 安全组的边栏选项卡。 选择“选择”，将策略部署到用户。

你已将策略应用于用户。 作为策略目标的用户所使用的设备将针对更新符合性进行评估。

## <a name="change-the-restricted-days-for-the-policy"></a>更改策略的限制日期
1. 在“软件更新”边栏选项卡上，选择“iOS 更新策略”。
2. 选择想要更新的 iOS 更新策略。
3. 选择“属性”，更新限制日期信息。

## <a name="monitor-ios-devices-with-older-ios-versions"></a>监视安装了较旧 iOS 版本的 iOS 设备 
<!-- 1352223 -->
可从“软件更新” > “iOS 更新策略”边栏选项卡中获取“过期 iOS 设备”报告。 在报告中，可以查看已作为 iOS 更新策略目标但无法更新的受监督 iOS 设备的列表。 可以查看每个设备的状态，了解该设备未自动更新的原因。