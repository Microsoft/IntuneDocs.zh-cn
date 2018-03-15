---
title: "在 Microsoft Intune 中配置 iOS 更新策略"
titlesuffix: 
description: "为 iOS 配置更新策略，强制受监视的 iOS 设备自动安装可用的最新软件更新。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.openlocfilehash: 2062f9cd551ec6d7f42449041e6c8de837221631
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>在 Microsoft Intune 中配置 iOS 更新策略
通过 iOS 的更新策略，可强制受监视的 iOS 设备自动安装可用的最新软件更新。 可选择配置不希望设备安装更新的日期和时间。

## <a name="configure-the-ios-update-policy"></a>配置 iOS 更新策略
1. 转到 Azure 门户中的“Intune”页。
2. 在“Intune”页，选择“软件更新” > “iOS 更新策略”。
4. 在“策略”页，选择“创建”，然后输入策略的名称和说明。
5. 选择“设置” > “配置”，然后输入 iOS 设备不强制安装最新更新时的详细信息。
6. 选择“确定”保存此配置。 现将返回“创建更新策略”页。 选择“创建”以创建策略并保存设置。

配置文件随即创建并显示在“iOS 更新策略列表”页中。

## <a name="assign-an-ios-update-policy-to-users"></a>向用户分配 iOS 更新策略
若要向用户分配 iOS 更新策略，请选择已配置的策略。 可在“软件更新” > “iOS 更新策略”页找到现有策略。
1. 选择要分配给用户的策略，然后选择“分配”。 将打开一个页面，可在其中选择 Azure Active Directory 安全组并将其分配给策略。
2. 选择“选择组”以打开显示 Azure AD 安全组的页。 选择“选择”，将策略部署到用户。

你已将策略应用于用户。 作为策略目标的用户所使用的设备将针对更新符合性进行评估。

## <a name="change-the-restricted-days-for-the-policy"></a>更改策略的限制日期
1. 在“软件更新”页，选择“iOS 更新策略”。
2. 选择想要更新的 iOS 更新策略。
3. 选择“属性”，更新限制日期信息。

## <a name="monitor-ios-devices-with-older-ios-versions"></a>监视安装了较旧 iOS 版本的 iOS 设备 
<!-- 1352223 -->
可从“软件更新” > “iOS 更新策略”页获取“过期 iOS 设备”报告。 在报告中，可以查看已作为 iOS 更新策略目标但无法更新的受监督 iOS 设备的列表。 可以查看每个设备的状态，了解该设备未自动更新的原因。