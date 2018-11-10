---
title: Intune 中的公司门户注册放弃
titlesuffix: Microsoft Intune
description: 了解公司门户放弃报表。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: ba1ee5a6811457b8c6e7343de7355261a2fcecdb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236742"
---
# <a name="company-portal-abandonment-report"></a>公司门户放弃报表

此报表会显示公司门户注册用户放弃注册过程的位置。

要查看报表，请依次选择“Intune” > “设备注册” > “公司门户放弃”。

使用此放弃信息，可以更新加入文档，以帮助用户完成注册。 例如，如果许多用户在“使用条款”区域退出，则可以调查该区域并使其更直观地为用户呈现。

## <a name="what-is-abandonment"></a>什么是放弃？

放弃是指用户执行以下任何操作的情况：

-   明确选择停止注册的操作
-   在注册过程中关闭公司门户
-   注册部分之间花费的时间超过 30 分钟

如果用户选择停止注册并多次重启，则会显示多次尝试和多次放弃。 如果用户在不同的注册屏幕之间等待 30 分钟，则会被视为多次放弃。

## <a name="what-does-the-report-show"></a>报表显示什么？

注册报表包括 iOS 和 Android 设备的数据。

报表显示过去两周的数据，但可以筛选报表以显示过去 30 天内的任何时段。

可以通过选择“筛选器”来筛选日期范围、操作系统和注册部分。

### <a name="number-and-percentage-tiles"></a>数量和百分比磁贴

在报表的顶部，可以查看与所有注册相关的已放弃报表的数量和百分比。

-   启动的注册：尝试的注册数。
-   放弃的注册：未完全注册和不符合设备的尝试的注册数。
-   放弃率：放弃的注册尝试的百分比（放弃的注册/启动的注册）。

### <a name="line-graph"></a>折线图

折线图显示了以下四个核心注册部分中每个部分的每日放弃数：

-   安装程序清单
-   平台屏幕
-   使用条款
-   符合性/激活

### <a name="user-abandonment-actions"></a>用户的放弃操作

下表显示了有资格作为放弃的用户操作列表。 要查看注册屏幕的示例，可以观看 [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) 和 [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment) 的注册视频。 


#### <a name="setup-checklist-section"></a>安装程序清单部分

| 放弃名称 | 屏幕或流 | 平台 | 操作 |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | 提示在公司门户中打开页面 | iOS/Android | 取消 |
| EnrollmentWrapUp | 注册设备屏幕直到完成“加载公司资源” | iOS/Android | 用时超过 30 分钟 |
| DeviceCategory | 选择“设备类别”（如果管理员已配置），然后单击“完成” | iOS/Android | 用时超过 30 分钟 |
| PreEnrollmentWizard | 在已开始注册但返回到“设置访问权限”时设置访问屏幕 | iOS/Android| **推迟** |
| PreEnrollmentWizard | 设置访问屏幕，直到单击“下一步是什么”屏幕上的“下一步” | iOS/Android | 用时超过 30 分钟 |

#### <a name="platform-screens-section"></a>平台屏幕部分

| 放弃名称 | 屏幕或流 | 平台 | 操作 |
| ---- |---- |---- |---- |
| iOSProfileLaunch | 提示显示配置文件 | iOS | **忽略** |
| iOSProfileLaunch | 安装配置文件屏幕 | iOS | **取消** |
| iOSProfileLaunch | 提示信任配置文件的来源以注册设备 | iOS | **取消** |
| iOSProfileLaunch | 安装配置文件屏幕，直到安装配置文件完成 | iOS | 用时超过 30 分钟 |
| AndroidPermissions | 设备管理员激活屏幕 | Android | **取消** |
| AndroidPermissions | 从提示批准打电话和管理电话到设备管理员“激活” | Android | 用时超过 30 分钟 |
| KnoxActivation | KLMS 代理激活（仅限 Samsung） | Android| **取消** |
| KnoxActivation | “确认”前的 KLMS 代理激活 | Android | 用时超过 30 分钟|

#### <a name="terms-of-use-section"></a>使用条款部分

| 放弃名称 | 屏幕或流 | 平台 | 操作 |
| ---- |---- |---- |---- |
| TermsofUse | 使用条款（如果管理员已配置） | iOS/Android | **全部拒绝** |
| TermsofUse | “全部接受”之前的使用条款 | iOS/Android | 用时超过 30 分钟 |

#### <a name="complianceactivation-section"></a>“符合性/激活”部分

| 放弃名称 | 屏幕或流 | 平台 | 操作 |
| ---- |---- |---- |---- |
| 合规性 | 设备符合性（如果管理员已配置）在注册后的访问设置中显示为非绿色| iOS/Android | **推迟** |
| 合规性 | 设备符合性显示为非绿色，更新后会显示为绿色 | iOS/Android | 用时超过 30 分钟 |
| 激活 | 注册激活（如果管理员已配置）在访问设置中显示为非绿色 | iOS/Android | **推迟** |
| 合规性 | 设备激活显示为非绿色，更新后会显示为绿色 | iOS/Android | 用时超过 30 分钟 |

## <a name="next-steps"></a>后续步骤

在检查放弃率后，可以查看[注册选项](enrollment-options.md)，了解是否可以进行任何更改以改善注册。