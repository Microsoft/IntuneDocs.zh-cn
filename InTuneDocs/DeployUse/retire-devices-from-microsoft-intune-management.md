---
title: "停用设备 | Microsoft Intune"
description: "Intune 支持选择性擦除和完全擦除，通过删除其策略和公司门户从 Intune 管理中删除该设备。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cf471320f122eea7804ff6cd6cad208f8cd5a692
ms.openlocfilehash: 29d13dcbc367c18d64f9522fa9a3b962226feebb


---

# 从 Intune 管理停用设备

无论设备是公司拥有的还是个人的，都会有需要从 Intune 管理中删除受管理设备的时候。 设备可能会出于多种原因而需要停用：

-   用户以计划方式离开公司（“托管式”离开）
-   用户突然离开（被解雇、辞职等）。
-   设备丢失
-   改变设备用途（转移给其他用户、重新用于其他目的等）

你可以对作为移动设备进行管理的设备执行选择性擦除或完全擦除，或锁定设备并重置设备密码。 擦除设备可释放用户的订阅，从而添加其他设备。 也可以停用使用 Intune 客户端软件管理的电脑。

## 从设备中擦除数据和应用
选择性擦除和完全擦除通过删除策略和公司门户从 Intune 管理中删除设备，这意味着设备不再拥有用于登录到公司资源（如 Microsoft SharePoint、电子邮件或 Office 365）所需的凭据。

对于已在 Intune 注册其自有设备的员工而言，[选择性擦除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)是首选的操作选项，因为它不会影响设备上的个人信息。 仅删除公司数据。

对于需要重新调整用途的设备，你也可以使用[完全擦除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)，这会将设备重置为出厂默认设置。

## 在 Azure Active Directory 门户中删除设备

1.  使用组织凭据登录到 [http://aka.ms/accessaad](http://aka.ms/accessaad) 或 [https://portal.office.com](https://portal.office.com)，然后选择“管理中心”&gt;“Azure AD”。

2.  创建 Azure 订阅（如果没有）。 如果有付费帐户，应该不会要求提供信用卡或付款（请选择**注册免费的 Azure Active Directory**订阅链接）。

4.  选择“Active Directory”  ，然后选择你的组织。

5.  选择“用户”  选项卡。

6.  选择要删除其设备的用户。

7.  选择**设备**。

8.  选择适当的设备并选择“删除设备”。 下一次与 Active Directory 同步时，将删除该设备。 这通常发生在 4 小时内。 同步之后，将从管理中删除该设备。 这会从该用户的设备限制中删除一台设备。

## 停用被管理的计算机
可以从 Intune 管理控制台的管理中删除使用 Intune 客户端软件管理的计算机。 删除的同时还会卸载客户端软件，并从计算机中删除 Intune 策略。 请参阅有关[停用使用 Intune 客户端软件管理的计算机](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md)的信息。

## 阻止访问设备
如果丢失了某个设备，或者因为某位员工离开公司时未归还公司拥有的硬件而必须停用某个设备，还可以[密码重置和远程锁定](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)该设备。 尽管你可能已将设备标记为丢失，但此操作可以防止公司信息被误用。

你还需要从该员工的 Intune 用户帐户吊销许可证。 这将释放许可证，然后你可以将该许可证分配给新的用户帐户。

## 停用硬件
有时，设备本身已达到了其寿命终点。 在这种情况下，使用完全擦除[重置为出厂设置](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)将删除所有的数据并从 Intune 中删除设备。 然后，你可以根据公司的策略处理掉硬件。

### 另请参阅
[使用完全擦除或选择性擦除保护数据](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Aug16_HO4-->


