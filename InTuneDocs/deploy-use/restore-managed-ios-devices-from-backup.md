---
title: "从备份还原 Intune 托管 iOS 设备 | Microsoft Docs"
description: "向最终用户提供有关如何在从备份还原之后重新注册其设备的指南。"
keywords: "还原，托管，iOS"
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 2dd3844e83818f760df22fb748e74c8013ddd9cd


---

# <a name="restore-intune-managed-ios-devices-from-backup"></a>从备份还原 Intune 托管 iOS 设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

在某些情况下你或你的用户需要从备份还原 iOS 设备（例如当用户获取新设备时）。 本主题说明在还原设备之后为设置 Intune 管理而必须执行的其他步骤。

## <a name="restoring-backups-onto-the-same-device"></a>将备份还原到相同设备

如果要将备份还原到相同设备，则也会还原该设备上的注册状态。 无需执行其他操作。

## <a name="restoring-backups-onto-different-devices"></a>将备份还原到不同设备

如果将备份还原到不同设备，则不会在新设备上自动还原注册状态。 用户需要在应用版本为 2.1.22 或更高版本的公司门户应用中执行标准注册步骤，以便[在 Intune 中注册其 iOS 设备](/Intune/EndUser/enroll-your-device-in-intune-ios)。

> [!NOTE]
> 如果是以使用条件访问策略的最终用户为目标，则他们在重新注册之前，将无法访问公司电子邮件。

> [!TIP]
> 针对用户的示例通信可能如下所示：若要在新设备上注册，请确保公司门户应用是版本 2.1.22 或更高版本。 若要检查版本，请打开公司门户应用，点击右上角的“菜单”按钮，然后点击“关于”。 如果使用的是早期版本，则退出公司门户应用并打开应用商店。 点击右下角的“更新”按钮，然后点击列表中公司门户项旁边的“更新”按钮。 更新完成之后，启动公司门户应用并[在 Intune 中注册 iOS 设备](/Intune/EndUser/enroll-your-device-in-intune-ios)。

## <a name="resolving-known-issues-with-restores"></a>解决还原的已知问题

如果用户的公司门户版本为 2.1.21 或更早版本，则在还原设备和启动公司门户应用时可能会遇到一些困难。 可以根据用户的实际情况采用相应的步骤来解决这些问题。

### <a name="for-users-who-will-only-use-their-new-device"></a>对于仅使用新设备的用户
启动公司门户应用，然后选择当前的设备磁贴并点击“删除”按钮来取消注册。 在删除后，按照标准注册步骤[将 iOS 设备注册到 Intune](/Intune/EndUser/enroll-your-device-in-intune-ios)。

### <a name="for-users-who-will-use-both-their-old-and-new-devices"></a>对于同时使用新旧设备的用户
通过点击“设置” > “Safari” > “清除历史记录和网站数据”从 Safari 中清除 cookie。 在清除后，卸载并重新安装公司门户应用，然后按照标准注册步骤[将 iOS 设备注册到 Intune](/Intune/EndUser/enroll-your-device-in-intune-ios)。



<!--HONumber=Dec16_HO2-->


