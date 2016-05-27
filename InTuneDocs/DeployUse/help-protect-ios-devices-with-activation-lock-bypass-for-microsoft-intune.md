---
# required metadata

title: 通过 Microsoft Intune 的绕过激活锁定帮助保护 iOS 设备 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 通过 Microsoft Intune 的绕过激活锁定帮助保护 iOS 设备
Microsoft Intune 可以帮助你管理 iOS 激活锁定，它具有 iOS 7.1 和更高版本设备上的“查找我的 iPhone”应用的功能。 当设备上使用了“查到我的 iPhone”应用时，激活锁定自动启用。 启用后，任何人都必须先输入用户的 Apple ID 和密码，然后才能执行以下操作：

-   关闭“查找我的 iPhone”

-   擦除设备

-   重新激活设备

## 激活锁定对你有何影响
尽管激活锁定可帮助保护 iOS 设备的安全，并可提高在设备丢失和被盗时的找回几率，但对于 IT 管理员来说，此功能仍然带来了许多挑战。 例如：

-   你的其中一个用户在设备上设置了激活锁定。 该用户之后离开了公司并返回使用其设备。 如果不提供用户的 Apple ID 和密码，则不能重新激活该设备。

-   你需要报告启用了激活锁定的所有设备。

-   更新你组织中的设备分配情况时，如果你希望将某些设备分配给另一个部门， 你只能重新分配未启用激活锁定的设备。

为了帮助解决这些问题，Apple 在 iOS 7.1 中引入了绕过激活锁定。 借助此功能，你无需用户的 Apple ID 和密码即可删除监管设备中的激活锁定。 监管设备可以生成设备特定的绕过激活锁定代码，该代码存储在 Apple 的激活服务器上。

> [!TIP]
> 在 iOS 设备的监管模式下，你可以使用 Apple 配置器工具来锁定设备，以将设备的功能限制为完成特定的业务目的。 监管模式通常仅适用于公司拥有的设备。

## Intune 如何帮助你管理激活锁定
Intune 可以请求运行 iOS 7.1 和更高版本的监管和非监管设备的激活锁定状态。 对于监管设备而言，Intune 可以检索绕过激活锁定代码并直接将代码发布到设备。 如果已擦除了设备，你可以直接使用该代码作为用户名并使用一个空密码来访问设备。

**此功能的业务优势有**：

-   用户能够获得 Find My iPhone 应用所具有的安全优势。

-   你可以让用户在知道如下事实的情况下进行工作：当需要重新调整设备的用途时，你可以停用或解锁设备。

## 如何从 Intune 管理员控制台使用绕过激活锁定
> [!IMPORTANT]
> 绕过设备上的激活锁定后，如果“查到我的 iPhone”应用处于打开状态，它将自动应用新的激活锁定。 因此，**你应实际拥有该设备，才能执行此过程**.

1.  在 [Microsoft Intune 管理控制平台](https://manage.microsoft.com)中，依次选择“组” &gt; “所有设备” &gt; “公司拥有的所有设备”。.

2.  选择想要绕过其“激活锁定”的设备。 选择“绕过激活锁定”.

3.  阅读警告消息。 选择“是”以继续。

你可以在设备的详细信息页上查看解锁请求的状态。

## 如何查看哪些设备正在使用激活锁定
有两种方式可以查看哪些设备正在使用激活锁定：

-   运行“移动设备清单报告” 。 此报告显示“激活锁定状态”  和“监管”  列来指示设备的状态。 “监管”  的值为“是”  或“否” ，“激活锁定状态”  的值为：

    -   已使用绕过代码启用

    -   未使用绕过代码启用(未监管设备)

    -   未使用旁路代码启用(无法到达设备)

    -   未启用

    对于不运行 iOS 7.1 或更高版本的设备而言，“激活锁定状态”  字段为空。

-   在组视图中选择一个设备，将可以在设备详细信息页中看到激活锁定状态。

    如果选择“公司拥有的所有设备”节点中的设备，并为该设备启用了激活锁定，则还可以看到绕过代码。 此代码可用于手动发布绕过激活锁定命令。

### 另请参阅
[停用设备](retire-devices-from-microsoft-intune-management.md)
[使用远程锁定和密码重置功能帮助保护设备](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


