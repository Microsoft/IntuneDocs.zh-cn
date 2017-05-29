---
title: "管理批量购买的 iOS 应用 | Microsoft Docs"
description: "使用 Intune 通过以下操作管理从 Apple 批量购买的应用：从应用商店导入许可证信息、跟踪已使用的许可证的数量，以及阻止安装超出你所拥有的应用的更多副本。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c05c9cb1a0de468f1a6663a7870631af159d9b04
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>使用 Microsoft Intune 管理通过批量购买计划购买的 iOS 应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

iOS 应用商店允许你为想要在公司运行的应用购买多个许可证。 这有助于降低跟踪多个已购买应用副本的管理成本。

Microsoft Intune 可帮助你通过以下操作管理通过此计划购买的应用：从应用商店中导入许可证信息、跟踪已使用的许可证的数量，以及阻止安装超出你所拥有的应用的更多副本。

> [!Important]
> 目前，Intune 将 iOS Volume Purchase Program 企业版 (VPP) 应用许可证分配给用户，而不是设备。 因此，用户必须输入其 Apple ID 密码才能安装应用。
> 此版本中不支持教育 Apple Volume Purchase Program for Education。

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>管理批量采购的适用于 iOS 设备的应用程序
通过 [Apple Volume Purchase Program 企业版](http://www.apple.com/business/vpp/)购买多个 iOS 应用许可证。 这涉及到从 Apple 网站设置一个 Apple VPP 帐户并将 Apple VPP 令牌上载到 Intune。  然后你可以将你的批量购买信息与 Intune 同步并追踪你的批量购买的应用的使用情况。

## <a name="before-you-start"></a>开始之前
在开始之前，你需要从 Apple 中获取 VPP 令牌并将其上载到 Intune 帐户。 此外，你应了解以下内容：

* Intune 支持最多添加 256 个 VPP 令牌。
* 如果你以前使用过不同产品的 VPP 令牌，必须生成一个新的令牌在 Intune 中使用。
* 每个令牌的有效期为一年。
* 默认情况下，Intune 与 Apple VPP 服务一天同步两次。 可以随时开始手动同步。
* 将 VPP 令牌导入 Intune 之后，不要将同一令牌导入任何其他设备管理解决方案。 这样做可能导致许可证分配和用户记录丢失。
* 在开始将 iOS VPP 与 Intune 配合使用之前，先删除使用其他移动设备管理 (MDM) 供应商创建的任何现有 VPP 用户帐户。 作为安全措施，Intune 不会将那些用户帐户同步到 Intune 中。 Intune 将仅同步 Apple VPP 服务中由 Intune 创建的数据。
* 如果配置了设备的用户关联，则只能将 iOS VPP 应用部署到使用设备注册协议 (DEP) 注册的用户设备。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>获取并上传 Apple VPP 令牌

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“管理”&gt;“iOS 和 Mac OS X”&gt;“批量购买计划”。

2.  选择“Apple VPP 帐户”链接。 如果你尚未拥有帐户，请注册 Volume Purchase Program 企业版。 注册后，下载你的帐户的 Apple VPP 令牌。

3.  在 Intune 控制台的“管理 Apple 批量购买计划(VPP)”页上，选择“上载 VPP 令牌”。

4.  在“上载 VPP 令牌”对话框中，输入或粘贴 VPP 令牌名称和你的 Apple ID，然后选择“上载”。

5.  在警告对话框中，选中相应复选框以指示你已了解你此后将不能更改为不同的 VPP 帐户，然后选择“是”。

在“Volume Purchase Program”页上，你现在可以查看有关 Apple VPP 令牌的信息，包括它上一次更新的时间，何时将过期，以及上一次与 Intune 同步的时间。

你可以随时通过选择“立即同步”将 Apple 保存的数据与 Intune 同步。

## <a name="to-deploy-a-volume-purchased-app"></a>部署批量购买的应用

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“应用”&gt;“应用” &gt;“批量购买应用”**V**。 此列表显示已从 Apple VPP 服务同步的所有应用。

2.  选择你想要部署的应用，选择“管理部署”，然后按照[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)主题中的说明完成应用的上载、创建和部署。

> [!TIP]
> 必须选择**必需**的部署操作。 当前不支持可用安装。 此外，只能将应用部署到用户组。

在将应用部署为**必需**安装时，安装该应用的每个用户都将使用一个许可证。

若要回收许可证，必须将部署操作更改为“卸载”。 卸载应用后，将回收许可证。

具有符合条件的设备的用户首次尝试安装 VPP 应用时，系统将要求其加入 Apple Volume Purchase Program。 继续安装应用前，他们必须执行此操作。

如果没有更多的许可证可用，则部署将失败。

## <a name="to-monitor-apple-vpp-apps"></a>监视 Apple VPP 应用
你可以从“批量购买的应用”节点中的“应用”工作区内监视已部署的 VPP 应用以及使用的许可证数。

> [!TIP]
> 你也可以使用应用“筛选器”来检查每个应用的安装状态。

### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)

