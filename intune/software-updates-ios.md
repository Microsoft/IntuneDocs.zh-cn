---
title: "配置 iOS 更新策略"
titleSuffix: Intune on Azure
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
ms.openlocfilehash: d4af2d58ec21c54362cf451eac1a33b2088885d5
ms.sourcegitcommit: 7674efb7de5ad54390801165364f5d9c58ccaf84
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2017
---
# <a name="configure-ios-update-policies"></a>配置 iOS 更新策略
通过 iOS 的更新策略，可强制受监视的 iOS 设备自动安装可用的最新软件更新。 可选择配置不希望设备安装更新的日期和时间。

## <a name="configure-the-ios-update-policy"></a>配置 iOS 更新策略
1. 转到 Azure 门户中的“Intune”边栏选项卡。
2. 在“Intune”边栏选项卡上，选择“软件更新” > “iOS 更新策略”。
4. 在策略边栏选项卡上，选择“创建”，然后输入策略的名称和描述。
5. 选择“设置” > “配置”，然后输入不会强制 iOS 设备安装最新更新的时间的详细信息。
6. 选择“确定”保存此配置。 现将返回“创建更新策略” 边栏选项卡。 选择“创建”以创建策略并保存设置。

系统将创建配置文件，并在“iOS 更新策略列表”边栏选项卡上显示。

## <a name="assign-an-ios-update-policy-to-users"></a>向用户分配 iOS 更新策略
若要向用户分配 iOS 更新策略，请选择已配置的策略。 可在“软件更新” > “iOS 更新策略”边栏选项卡中找到现有策略。
1. 选择要分配给用户的策略，然后选择“分配”。 此操作将打开边栏选项卡，可在其中选择 Azure Active Directory 安全组并将其分配给策略。
2. 选择“选择组”以打开显示 Azure AD 安全组的边栏选项卡。 选择“选择”，将策略部署到用户。

你已将策略应用于用户。 将评估策略针对的用户所使用设备的更新符合性。

## <a name="change-the-restricted-days-for-the-policy"></a>更改策略的限制日期
1. 在“软件更新”边栏选项卡上，选择“iOS 更新策略”。
2. 选择想要更新的 iOS 更新策略。
3. 选择“属性”，更新限制日期信息。
