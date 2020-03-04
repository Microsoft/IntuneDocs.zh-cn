---
title: 使用 Intune 绕过 iOS/iPadOS 激活锁
titleSuffix: Microsoft Intune
description: 了解如何使用 Intune 绕过 iOS/iPadOS 激活锁以访问锁定的设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af5bb1c95a15a5c52585278605e2f7a86307cb76
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782234"
---
# <a name="disable-activation-lock-on-supervised-iosipados-devices-with-intune"></a>使用 Intune 在受监管的 iOS/iPadOS 设备上禁用激活锁


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune 可以帮助管理 iOS/iPadOS 激活锁，这是适用于 iOS/iPadOS 8.0 及更高版本设备的“查找我的 iPhone”应用的功能。 当用户在设备上打开了“查找我的 iPhone”应用时，激活锁定将自动启用。 启用后，任何人都必须先输入用户的 Apple ID 和密码，然后才能执行以下操作：

- 关闭“查找我的 iPhone”
- 擦除设备
- 重新激活设备

## <a name="how-activation-lock-affects-you"></a>激活锁定对你有何影响

尽管激活锁可帮助保护 iOS/iPadOS 设备的安全，并可提高找回丢失和被盗设备的几率，但对于 IT 管理员来说，此功能仍然带来了许多挑战。 例如：

- 某个用户在设备上设置了激活锁定。 该用户之后离开了公司并返回使用其设备。 如果不提供用户的 Apple ID 和密码，则不能重新激活该设备。
- 你需要报告启用了激活锁定的所有设备。
- 更新你组织中的设备分配情况时，你希望将某些设备分配重新给另一个部门。 你只能重新分配未启用激活锁定的设备。

为了帮助解决这些问题，Apple 在 iOS/iPadOS 7.1 中引入了激活锁禁用。 通过“禁用激活锁”，无需用户的 Apple ID 和密码即可删除受监管的设备中的激活锁。 监管设备可以生成设备特定的绕过激活锁定代码，该代码存储在 Apple 的激活服务器上。

>[!TIP]
>在 iOS/iPadOS 设备的监管模式下，你可以使用 Apple Configurator 来锁定设备，以将设备的功能限制为完成特定的业务目的。 监督模式仅适用于公司拥有的设备。

可以在 [Apple 的网站](https://support.apple.com/HT201365)上阅读有关激活锁定的详细信息。

## <a name="how-intune-helps-you-manage-activation-lock"></a>Intune 如何帮助你管理激活锁定
Intune 可以请求运行 iOS/iPadOS 8.0 和更高版本的监管设备的激活锁状态。 仅就监管设备而言，Intune 可以检索“禁用激活锁”代码并直接将代码发布到设备。 如果已擦除设备，可通过使用空的用户名和代码作为密码来直接访问设备。

使用 Intune 来管理激活锁的业务优点包括： 

- 用户能够获得 Find My iPhone 应用所具有的安全优势。
- 你可以让用户在知道如下事实的情况下进行工作：当需要重新调整设备的用途时，你可以停用或解锁设备。

## <a name="before-you-start"></a>开始之前
必须先按照以下说明在设备上启用“激活锁”，然后才能禁用它：

1. 使用[如何配置设备限制设置](/intune-azure/configure-devices/how-to-configure-device-restrictions)中的信息为 iOS/iPadOS 配置 Intune 设备限制配置文件。
2. 在 [iOS/iPadOS 的设备限制设置](../configuration/device-restrictions-ios.md)中，在“常规”设置下启用“激活锁”选项   。
3. 保存配置文件，然后将其[分配](../configuration/device-profile-assign.md)到要管理“禁用激活锁”的设备。


## <a name="how-to-use-disable-activation-lock"></a>如何使用“禁用激活锁”

>[!IMPORTANT]
>禁用设备上的激活锁后，如果“查找我的 iPhone”应用处于启动状态，将自动应用新的激活锁。 因此，**你应实际拥有该设备，才能执行此过程**。

Intune“禁用激活锁”  远程设备操作无需用户的 Apple ID 和密码即可去除 iOS/iPadOS 设备中的激活锁。 禁用激活锁后，启动“查找 iPhone”应用时设备将再次打开激活锁。 请仅在拥有对设备的物理访问权限的情况下禁用激活锁。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 在“Intune”边栏选项卡上，选择“设备”   。
4. 在“设备”边栏选项卡上，选择“所有设备”   。
5. 在管理的设备列表中，选择“禁用激活锁”  设备远程操作。
6. 转到设备的“硬件”部分，然后复制“条件访问”下的“激活锁旁路代码”值   。

    >[!NOTE]
    >擦除设备前，请复制旁路代码。 如果在复制该代码之前重置设备设置，则会从 Azure 中删除该代码。

7. 转到设备的“概述”边栏选项卡，然后选择“擦除”   。
8. 重置设备后，系统会提示输入 Apple ID 和密码   。 将“ID”字段留空，然后输入密码的“旁路代码”    。 这会从设备中删除该帐户。 


## <a name="next-steps"></a>后续步骤

你可以在“管理设备”  工作负荷中的设备的详细信息页上查看解锁请求的状态。
