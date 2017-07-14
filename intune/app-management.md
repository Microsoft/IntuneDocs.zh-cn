---
title: "什么是应用管理"
titleSuffix: Intune on Azure
description: "通过本主题了解使用 Microsoft Intune 进行应用管理的基础知识"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 33ddb60df7aebe36ff652e1da6da592442b96d4b
ms.sourcegitcommit: fb17b59f4aa2b994b149fcc6d32520f74b0de6a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2017
---
# 什么是 Microsoft Intune 应用管理？
<a id="what-is-microsoft-intune-app-management" class="xliff"></a>


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


作为 IT 管理员，需要负责确保最终用户有权访问完成其工作所需的应用。 这个任务很有挑战性，因为：
- 有众多的设备平台和应用类型。
- 可能需要管理公司设备和用户自有设备上的应用。
- 你必须确保网络和数据受到保护。

此外，你可能还会想在未注册 Intune 的设备上分配和管理应用。

Intune 提供多种功能，帮助你在所需设备上获取所需应用。

## 按平台分类的应用管理功能
<a id="app-management-capabilities-by-platform" class="xliff"></a>

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|向设备和用户添加和分配应用|是|是|是|是|
|将应用分配到未注册 Intune 的设备|是|是|否|否|
|使用应用配置策略来控制应用的启动行为|否|是|否|否|
|使用移动应用预配策略续订过期应用|否|是|否|否|
|使用应用保护策略来保护应用中的公司数据|是|是|否|否<sup>1</sup>|
|仅从已安装应用中删除公司数据（应用选择性擦除）|是|是|是|是|
|监视应用分配|是|是|是|是|
|分配和跟踪从应用商店批量购买的应用|否|否|否|是|
|强制在设备上安装的应用（必需）<sup>2</sup>|是|是|是|是|
|从公司门户的设备上进行可选安装（安装可用）|是|是|是|是|
|向 Web 版应用安装快捷方式（Web 剪辑）|是|是|是|是|
|内部（业务线）应用|是|是|否|否|
|来自应用商店的应用|是|是|是|是|
|更新应用|是|是|是|是|

<sup>1</sup>请考虑使用 [Windows 信息保护](windows-information-protection-configure.md)来保护运行 Windows 10 的设备上的应用。

<sup>2</sup>仅适用于由 Intune 管理的设备。

## 如何开始？
<a id="how-to-get-started" class="xliff"></a>

可在“移动应用”工作负荷中找到大部分与应用相关的内容，并可通过以下步骤进行访问：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“移动应用”。

    ![移动应用工作负荷](./media/apps-workload.png)

### 管理计算机上的
<a id="manage" class="xliff"></a>
- **应用** - 可在此节点处添加、分配和监视大多数应用。
    - [添加应用](apps-add.md)
    - [分配应用](apps-deploy.md)
    - [监视应用](apps-monitor.md)
- **应用配置策略** - 应用配置策略可提供用户在运行应用时可能需要的设置。
    - [iOS 应用配置策略](app-configuration-policies-use-ios.md)
    - [Android 应用配置策略](app-configuration-policies-use-android.md)
- **应用保护策略** - 可将设置与应用关联，从而帮助保护其使用的公司数据。 例如，可以限制某应用与其他应用进行通信的功能，或要求用户输入 PIN 才能访问公司应用。
    - [应用保护策略](app-protection-policies.md)
- **应用选择性擦除** - 仅从所选用户设备中删除公司数据。
    - [应用选择性擦除](apps-selective-wipe.md)
- **iOS 预配配置文件** - iOS 应用包含一个预配配置文件和一个证书签名的代码。 证书过期后，应用无法再运行。 Intune 提供了一些工具，用于将新的预配配置文件策略主动分配到安装了即将到期应用的设备。
    - [iOS 应用预配配置文件](app-provisioning-profile-ios.md)

### 监视
<a id="monitor" class="xliff"></a>
- **许可应用** - 查看、分配和监视从应用商店批量购买的应用。
    - [适用于企业批量采购应用的 Windows 应用商店](windows-store-for-business.md)
- **发现的应用** - 显示由 Intune 分配，并安装在设备上的所有应用。
- **应用安装状态** - 显示你创建的应用分配的状态。
- **应用保护状态** - 显示所选用户的应用保护策略的状态。

有关详细信息，请参阅[监视应用](apps-monitor.md)

### Setup
<a id="setup" class="xliff"></a>
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](vpp-apps-ios.md) --->
- **适用于企业的 Windows 应用商店** - 设置与适用于企业的 Windows 应用商店的集成。 然后，可将购买的应用程序同步到 Intune，对其进行分配，并跟踪许可证使用情况。
    - [适用于企业批量采购应用的 Windows 应用商店](windows-store-for-business.md)
- **公司门户品牌** - 自定义公司门户，向其提供公司品牌。
    - [公司门户配置](company-portal-app.md)
