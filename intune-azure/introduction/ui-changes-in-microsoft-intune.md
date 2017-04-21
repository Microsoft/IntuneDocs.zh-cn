---
title: "在 Azure 中我的 Intune 功能处于哪个位置？"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：帮助你在 Azure 控制台中找到 Intune 功能。"
keywords: 
author: dagerrit
ms.author: dagerrit
manager: angrobe
ms.date: 03/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 6a6b64465c95a3edd6fc2e2d4ae3da80ba3367ee
ms.openlocfilehash: 92bd41aa4acc02e67e983c68f818bd656b0b9608
ms.lasthandoff: 04/12/2017


---
# <a name="where-did-my-intune-feature-go-in-azure"></a>在 Azure 中我的 Intune 功能处于哪个位置？
我们已将 Intune 移动到 Azure 门户，借此机会我们以更有逻辑的方式整理了某些任务。 但每一次改进都需要熟悉新的布局整理。 因此，我们创作了此参考指南，以满足那些非常熟悉经典控制台中的 Intune 并且想知道如何在 Azure 上的 Intune 中完成工作的用户。 如果本文未涵盖你正在查找的功能，请在文章末尾处留下评论，以便我们更新。
## <a name="quick-reference-guide"></a>快速参考指南
| 功能 | 经典控制台中的路径 | Azure 上的 Intune 中的路径 ||------------||---------------|---------------|
| 设备注册计划 (DEP) | 管理员 > 移动设备管理 > iOS 和 Mac OS X > 设备注册计划|[设备注册 > Apple 注册 > 注册计划令牌](#where-did-apple-dep-go) |
| 设备注册计划 (DEP) | 管理员 > 移动设备管理 > iOS 和 Mac OS X > 设备注册计划 |[设备注册 > Apple 注册 > 注册计划序列号](#where-did-apple-dep-go) |
| 注册规则 |管理员 > 移动设备管理 > 注册规则|[设备注册 > 注册限制](#where-did-enrollment-rules-go) |
| 按 iOS 序列号排列的组 | 组 > 所有设备 > 企业预注册的设备 > 按 iOS 系列号排列 |[设备注册 > Apple 注册 > 注册计划序列号](#where-did-corporate-pre-enrolled-devices-go) |
| 按 iOS 序列号排列的组 | 组 > 所有设备 > 企业预注册设备 > 按 iOS 序列号排列| [设备注册 > Apple 注册 > AC 序列号](#where-did-corporate-pre-enrolled-devices-go)|
| 按 IMEI 排列的组（所有平台）| 组 > 所有设备 > 企业预注册设备 > 按 IMEI 排列（所有平台）| [设备注册 > 企业设备标识符](#by-imei-all-platforms)|
企业设备注册配置文件 | 策略 > 企业设备注册 | [设备注册 > Apple 注册 > 注册计划配置文件](#where-did-corporate-pre-enrolled-devices-go) |
| 企业设备注册配置文件 | 策略 > 企业设备注册 | [设备注册 > Apple注册 > AC 配置文件](#where-did-corporate-pre-enrolled-devices-go) |


## <a name="where-do-i-manage-groups"></a>在哪个位置管理组？
Azure 上的 Intune 使用[Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) 管理组。

## <a name="where-did-enrollment-rules-go"></a>注册规则在处于哪个位置？
在经典控制台中，你可以设置规则以管理移动和现代 Windows 和 macOS 设备的 MDM 注册：

![经典移动设备注册规则的图像](./media/ui-changes/01-classic-rules.png)

这些规则适用于你的 Intune 帐户中没有异常的所有用户。 在 Azure 门户中，这些规则现在表现为两种不同的策略类型：设备类型限制和设备限制：

![Azure 移动设备注册限制的图像](./media/ui-changes/02-azure-enroll-restrictions.png)

默认设备限制对应于经典控制台中的设备注册限制：

![Azure 设备限制的图像](./media/ui-changes/03-azure-device-limit.png)

默认设备类型限制对应于经典控制台中的平台限制：

![Azure 设备类型限制的图像](./media/ui-changes/04-azure-platform-restrictions.png)

现在在设备类型限制的平台配置下管理允许或阻止个人拥有的设备的功能：

![Azure 个人设备阻止块设置的图像](./media/ui-changes/05-azure-personal-block.png)

新的限制功能将仅添加到 Azure 门户。

## <a name="where-did-apple-dep-go"></a>Apple DEP 处于哪个位置？
在经典控制台中，你可以将 Intune 设置为与 Apple 设备注册计划进行集成，并手动请求与 Apple 的服务同步：

![经典 DEP 令牌的图像](./media/ui-changes/06-classic-dep-token.png)

在 Azure 门户中，你将使用 Intune 经典控制台中所用的相同步骤设置 Apple 设备注册计划：

![Azure DEP 令牌的图像](./media/ui-changes/07-azure-dep-token.png)

但是，经典控制台中的“同步”选项已移至序列号管理工作流，因为手动同步的结果将显示于此处：

![Azure DEP 同步的图像](./media/ui-changes/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>企业预注册设备处于哪个位置？
### <a name="by-ios-serial-number"></a>按 iOS 序列号排列
在经典控制台中，你可以通过 Apple 设备注册计划 (DEP) 和 Apple 配置器工具注册 iOS 设备。 这两种方法都按序列号提供设备预注册，并且设计分配特殊企业设备注册的配置文件。 注册之前，可以通过“按 iOS 序列号排列的企业预注册设备”设备组管理注册配置文件的分配：

![经典 Apple 序列号的图像](./media/ui-changes/09-classic-apple-serials.png)

这将列出单个列表中 Apple DEP 和 Configurator 注册的序列号。 为了减少配置文件的不匹配分配（将 DEP 配置文件分配到 AC 序列号，反之亦然），我们在 Azure 门户上将序列号分成两个列表：

**DEP 序列号**
![Azure DEP 序列号的图像](./media/ui-changes/10-azure-dep-serials.png)

**Apple Configurator 序列号**
![Azure Apple Configurator 序列号的图像](./media/ui-changes/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>按 IMEI 排列（所有平台）

在经典控制台中，可以预先列出设备的 IMEI 号码，以便在注册到 Intune 时将其标记为企业：

![IMEI 号码经典列表的图像](./media/ui-changes/12-classic-corp-imei.png)

在 Azure 控制台中，必须使用逗号分隔值 (csv) 文件将相同的 IMEI 上传到公司设备标识符列表。 新门户不支持手动输入 IMEI 号码：

![IMEI 号码 Azure 列表的图像](./media/ui-changes/13-azure-corp-imei.png)

除了 IMEI，Azure 门户中的 Intune 还会适应未来，支持其他类型的标识符，但目前只允许预先列出 IMEI号码。

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>公司设备注册配置文件处于哪个位置？
若要通过 Apple 设备注册计划或 Apple 配置器工具注册 iOS 设备，则必须提供要分配给设备的公司设备注册配置文件。 在经典控制台中，这些配置文件的创建和管理位于单个列表中：

![经典设备注册配置文件的图像](./media/ui-changes/14-classic-corp-profiles.png)

此列表显示可用于 Apple 设备注册计划的配置文件（**DEP 开启**）和仅可用于 Apple 配置器工具的配置文件（**DEP 关闭**）。

为了减少两种配置文件类型之间的混淆以及潜在的不匹配分配（将 DEP 配置文件分配到配置器设备，反之亦然），我们将注册计划配置文件（支持 Apple 设备注册计划和 Apple 校园教务管理）与 Apple 配置器配置文件的创建和管理进行了分离：

**DEP 配置文件**
![Azure DEP 配置文件的图像](./media/ui-changes/15-azure-dep-profiles.png)

**Apple 配置器配置文件**
![Azure Apple 配置器配置文件的图像](./media/ui-changes/16-azure-ac-profiles.png)

