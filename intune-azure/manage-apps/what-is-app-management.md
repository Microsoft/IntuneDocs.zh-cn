---
title: "什么是应用管理 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：通过本主题了解使用 Microsoft Intune 进行应用管理的基础知识"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: d3be47257556e8bfa331cebf68baa43524690d1a
ms.lasthandoff: 02/16/2017


---

# <a name="what-is-microsoft-intune-app-management"></a>什么是 Microsoft Intune 应用管理？


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


作为 IT 管理员，很可能需要负责确保最终用户有权访问完成其工作所需的应用。 这个任务很有挑战性，因为：
- 有众多的设备平台和应用类型。
- 可能不但需要管理公司设备上的应用，还需要管理用户自有设备上的应用。
- 你需要做到所有这些事，同时还要确保你的网络和数据安全。 

此外，你可能还会想在未注册 Intune 的设备上分配和管理应用。

Intune 提供多种功能，帮助你在所需设备上获取所需应用。

## <a name="app-management-capabilities-by-platform"></a>按平台分类的应用管理功能

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|向设备和用户添加和分配应用|是|是|是|是|
|将应用分配到未注册 Intune 的设备|是|是|否|否|
|使用应用配置策略来控制应用的启动行为|否|是|否|否|
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

<sup>1</sup>请考虑使用 [Windows 信息保护](/intune-azure/configure-devices/how-to-configure-windows-information-protection)来保护运行 Windows 10 的设备上的应用。

<sup>2</sup>仅适用于由 Intune 管理的设备。


## <a name="how-to-get-started"></a>如何开始？

可在“移动应用”工作负荷中找到大部分与应用相关的内容，并可通过以下步骤进行访问：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。

    ![移动应用工作负荷](./media/apps-workload.png)

### <a name="manage"></a>管理计算机上的
- **应用** - 可在此处添加、分配和监视大多数应用。 
    - [添加应用](add-apps.md)
    - [分配应用](deploy-apps.md)
    - [监视应用](monitor-apps.md)
- **许可应用** - 查看、部署和监视从应用商店批量购买的应用。
    - [适用于企业批量采购应用的 Windows 应用商店](wsfb-apps.md)
- **应用配置策略** - 应用配置策略可提供用户在运行应用时可能需要的设置。 有关详细信息，请参阅：
    - [应用配置策略](app-configuration-policies.md)
- **应用保护策略** - 可将设置与应用关联，从而帮助保护其使用的公司数据。 例如，可以限制某应用与其他应用进行通信的功能，或要求用户输入 PIN 才能访问公司应用。
    - [应用保护策略](app-protection-policies.md)
- **应用选择性擦除** - 仅从所选用户设备中删除公司数据。
    - [应用选择性擦除](app-selective-wipe.md)

### <a name="monitor"></a>监视
- **发现的应用** - 显示由 Intune 分配，并安装在设备上的所有应用。
- **应用安装状态** - 显示你创建的应用分配的状态。
- **应用保护用户状态** - 显示所选用户的应用保护策略的状态。

有关详细信息，请参阅[监视应用](monitor-apps.md)

### <a name="setup"></a>Setup
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](ios-vpp-apps.md) --->
- **适用于企业的 Windows 应用商店** - 设置与适用于企业的 Windows 应用商店的集成。 执行此操作后，可将购买的应用程序同步到 Intune，对其进行分配，并跟踪许可证使用情况。 
    - [适用于企业批量采购应用的 Windows 应用商店](wsfb-apps.md)
- **公司门户品牌** - 自定义公司门户，向其提供公司品牌。 
    - [公司门户配置](company-portal-app.md)

