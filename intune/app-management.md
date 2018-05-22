---
title: 什么是 Microsoft Intune 中的应用管理？
titlesuffix: ''
description: 了解使用 Microsoft Intune 进行应用管理的基础知识。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6d11de1e20f46fb6e13d6d3ef5c9f4a9ee0f98c1
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="what-is-microsoft-intune-app-management"></a>什么是 Microsoft Intune 应用管理？


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

作为 IT 管理员，可以使用 Microsoft Intune 来管理公司员工使用的移动应用。 除了此功能外，还可管理设备和保护数据。 管理员的首要任务之一是，确保最终用户能够访问他们在执行工作时所需的应用。 这个目标很有挑战性，因为：
- 有众多的设备平台和应用类型。
- 可能需要管理公司设备和用户个人设备上的应用。
- 必须确保网络和数据的安全性。

此外，还建议分配和管理未向 Intune 注册的设备上的应用。

Intune 提供各种功能，用于在设备上获取所需的应用，以便在其中运行。 下表提供了有关应用管理功能的摘要： 

## <a name="app-management-capabilities-by-platform"></a>按平台分类的应用管理功能

||||||
|-|-|-|-|-|
| |Android|iOS|Windows Phone 8.1|Windows 10|
|向设备和用户添加和分配应用|是|是|是|是|
|将应用分配到未注册 Intune 的设备|是|是|否|否|
|使用应用配置策略来控制应用的启动行为|否|是|否|否|
|使用移动应用预配策略续订过期应用|否|是|否|否|
|使用应用保护策略来保护应用中的公司数据|是|是|否|否<sup>1</sup>|
|仅从已安装应用中删除公司数据（应用选择性擦除）|是|是|是|是|
|监视应用分配|是|是|是|是|
|分配和跟踪从应用商店批量购买的应用|否|否|否|是|
|强制在设备上安装的应用（必需）<sup>2</sup>|是|是|是|是|
|从公司门户的设备上进行可选安装（可用安装）|是|是|是|是|
|安装 Web 版应用快捷方式（Web 链接）|是|是|是|是|
|内部（业务线）应用|是|是|否|是|
|来自应用商店的应用|是|是|是|是|
|更新应用|是|是|是|是|

<sup>1</sup>请考虑使用 [Windows 信息保护](windows-information-protection-configure.md)来保护运行 Windows 10 的设备上的应用。

<sup>2</sup> 仅适用于由 Intune 管理的设备。

## <a name="get-started"></a>入门

可以在“移动应用”工作负载中找到大多数应用的相关信息，可通过执行以下操作进行访问：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。  
    Intune 位于“监视 + 管理”部分中。
3. 在“Microsoft Intune”窗格中，选择“移动应用”。

    ![“移动应用”工作负载窗格](./media/apps-workload.png)

接下来的四节描述了“移动应用”窗格中的可用选项。

### <a name="manage"></a>管理计算机上的
- 应用：选择此选项可添加、查看、分配和监视员工使用的应用。 有关详情，请参阅：
    - [添加应用](apps-add.md)。
    - [分配应用](apps-deploy.md)。
    - [监视应用](apps-monitor.md)。
- 应用配置策略：选择此选项可提供用户在运行应用时可能需要的设置。 有关详情，请参阅：
    - [Intune 的应用配置策略](app-configuration-policies-overview.md)。
        - [iOS 应用配置策略](app-configuration-policies-use-ios.md)。
        - [Android 应用配置策略](app-configuration-policies-use-android.md)。
- 应用保护策略：选择此选项可将设置与应用关联，并帮助保护其使用的公司数据。 例如，可以限制某应用与其他应用进行通信的功能，或者可能要求用户输入 PIN 才能访问公司应用。 有关详情，请参阅：
    - [应用保护策略](app-protection-policies.md)。
- 应用选择性擦除：选择此选项将从选定用户的设备中仅删除公司数据。 有关详情，请参阅：
    - [应用选择性擦除](apps-selective-wipe.md)。
- iOS 应用预配配置文件：iOS 应用包含一个预配配置文件和一个证书签名的代码。 证书过期后，应用无法再运行。 Intune 提供了一些工具，用于将新的预配配置文件策略主动分配到安装了即将到期应用的设备。 有关详情，请参阅：
    - [iOS 应用预配配置文件](app-provisioning-profile-ios.md)。

有关本部分的详细信息，请参阅[管理应用](app-management.md)。

### <a name="monitor"></a>监视
- 应用许可证：查看、分配和监视从应用商店批量购买的应用。 有关详情，请参阅：
    - [iOS 批量采购计划 (VPP) 应用](vpp-apps-ios.md)。
    - [适用于企业的 Microsoft Store 批量采购的应用](windows-store-for-business.md)。
- 发现的应用：查看由 Intune 分配，并安装在设备上的所有应用。
- 应用安装状态：查看你创建的应用分配的状态。
- 应用保护状态：查看所选用户的应用保护策略的状态。
- 审核日志：查看所有 IT 管理员的 Intune 应用相关活动。

有关本部分的详细信息，请参阅[监视应用](apps-monitor.md)。

### <a name="set-up"></a>设置
- iOS VPP 令牌：应用并查看 iOS 批量采购计划 (VPP) 许可证。 有关详情，请参阅：
    - [iOS 批量采购的应用](vpp-apps-ios.md)
- Windows 企业证书：应用或查看用于将业务线应用分发到托管 Windows 设备的代码签名证书的状态。
- Windows Symantec 证书：应用或查看将 XAP 和 WP8.x appx 文件分配到 Windows 10 移动设备所需的 Symantec 代码签名证书的状态。
- 适用于企业的 Microsoft Store：设置与适用于企业的 Microsoft Store 的集成。 然后，可将购买的应用程序同步到 Intune，对其进行分配，并跟踪许可证使用情况。 有关详情，请参阅：
    - [适用于企业的 Microsoft Store 批量采购的应用](windows-store-for-business.md)。
- Windows 旁加载密钥：添加 Windows 旁加载密钥，可用于将应用直接安装到设备，而无需从 Windows 应用商店发布和下载应用。 有关详情，请参阅：
    - [旁加载 Windows 应用](app-sideload-windows.md)。
- 公司门户品牌：自定义公司门户，向其提供公司品牌。 有关详情，请参阅：
    - [公司门户配置](company-portal-app.md)。
- 应用类别：添加、固定和删除应用类别名称。
- Android for Work：审核并同步已为企业批准的应用。 有关详情，请参阅：
    - [Android for Work 应用](apps-add-android-for-work.md)。

### <a name="help-and-support"></a>帮助和支持
- 帮助和支持：排查问题、请求获取支持或查看 Intune 状态。 有关详情，请参阅：
    - [排查问题](help-desk-operators.md)。

## <a name="next-steps"></a>后续步骤

- [向 Microsoft Intune 添加应用](apps-add.md)
