---
title: "获取 Intune 的 Apple DEP 证书"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：有关配置和上传 MDM push certificate 的说明，这是在 Intune 中管理 Apple 设备的先决条件。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8edc42bb86e3856ac6568cc3c1acc5d757978e79
ms.lasthandoff: 02/18/2017

---

# <a name="get-an-apple-dep-certificate"></a>获取 Apple DEP 证书

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用 Apple 的设备注册计划 (DEP) 注册公司拥有的 iOS 设备之前，需要从 Apple 获取 DEP 令牌。 此令牌允许 Intune 同步有关公司所拥有的且加入了 DEP 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

要使用 DEP 管理公司拥有的 iOS 设备，组织必须加入 Apple DEP 并通过该计划获取设备。 该过程的详细信息，可以通过以下网站获得：https://deploy.apple.com。 该计划的优点包括免手动设置设备，无需通过 USB 电缆将每个设备连接到计算机。

> [!NOTE]
> 本说明适用于已从 Intune 管理控制台迁移到 Azure 门户的 Intune 客户。 如果在迁移期间从 Intune 管理控制台删除了 Apple DEP 令牌，则可能会发现 DEP 令牌已还原到 Intune 帐户。 如果发生这种情况，只需在 Azure 门户中删除 DEP 令牌。

## <a name="steps-to-get-the-apple-dep-certificate"></a>获取 Apple DEP 证书要执行的步骤
在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。 在“Intune”边栏选项卡上，选择“注册设备” > “Apple DEP 令牌”，然后按照 Azure 门户中的编号步骤操作，如下所示。

**步骤 1.下载创建 Apple DEP 令牌所需的 Intune 公钥证书。**<br>
选择“下载公钥”，本地下载和保存加密密钥 (.pem) 文件。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。

**步骤 2：从相应的 Apple 网站下载 Apple DEP 令牌。**<br>
选择“通过 Apple 部署计划创建 DEP 令牌”[](https://deploy.apple.com)(https://deploy.apple.com)，并使用公司的 Apple ID 登录。 必须使用此 Apple ID 才能续订 DEP 令牌。

   a.  在[设备注册计划门户](https://deploy.apple.com)中，转到“设备注册计划”&gt;“管理服务器”，然后选择“添加 MDM 服务器”。

   b。  输入“MDM 服务器名称”，然后选择“下一步”。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

   c.  此时将打开“添加 &lt;服务器名称&gt;”对话框。 选择“选择文件…” 以上传 .pem 文件，然后选择“下一步”。

   d.  “添加 &lt;ServerName&gt;”对话框显示“你的服务器令牌”链接。 将服务器令牌 (.p7m) 文件下载到计算机，然后选择“完成”。

    This certificate (.p7m) file is used to establish a trust relationship between Intune and Apple’s Device Enrollment Program servers.

**步骤 3：输入用于创建 Apple DEP 令牌的 Apple ID。此 ID 可以用于续订 Apple DEP 令牌。**

**步骤 4：浏览到要上传的 Apple DEP 令牌。Intune 会自动与 DEP 帐户同步。**<br>
转到证书 (.pem) 文件，选择“打开”，然后选择“上传”。 使用 Push Certificate，Intune 可通过将策略推送到已注册的移动设备来注册和管理 iOS 设备。

