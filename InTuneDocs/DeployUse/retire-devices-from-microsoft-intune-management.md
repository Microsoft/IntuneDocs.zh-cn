---
title: "停用设备 | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: c06f1fc1168b0dde515eaa82d15095ec4d73d1cf


---

# 从 Intune 管理停用设备

无论设备是公司拥有的还是个人的，都会有需要在 Intune 中从管理停用托管设备的时候。 设备停用是比较简单直接的；你可以执行选择性擦除或完全擦除。
## 从设备中擦除数据和应用
选择性擦除和完全擦除通过删除策略和公司门户从 Intune 管理中删除设备，这意味着设备不再拥有用于登录到公司资源（如 Microsoft SharePoint、电子邮件或 Office 365）所需的凭据。

对于已在 Intune 注册其自有设备的员工而言，[选择性擦除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)是首选的操作选项，因为它不会影响设备上的个人信息。 仅删除公司数据。

对于公司拥有的设备而言，你也可以使用[完全擦除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)，这会将设备重置为出厂设置。

## 撤销对公司网络的访问权限
如果因为员工离开公司且忘了交还公司拥有的硬件而需要你停用设备时，你也可以[远程锁定](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)设备。 尽管你可能已将设备标记为丢失，但此操作也可以防止公司信息和公司硬件被误用。

你还需要从该员工的 Intune 用户帐户吊销许可证。 这将释放许可证，然后你可以将该许可证分配给新的用户帐户。

## 停用硬件
有时，设备本身已达到了其寿命终点。 在这种情况下，使用完全擦除[重置为出厂设置](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)将删除所有的数据并从 Intune 中删除设备。 然后，你可以根据公司的策略处理掉硬件。

### 另请参阅
[使用完全擦除或选择性擦除保护数据](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


