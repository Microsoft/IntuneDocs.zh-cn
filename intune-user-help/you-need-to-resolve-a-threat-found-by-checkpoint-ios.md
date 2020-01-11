---
title: 解决 SandBlast Mobile Protect 在 iOS 上发现的威胁 | Microsoft Docs
description: 了解如何解决 SandBlast Mobile Protect 在 iOS 上发现的威胁。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 5b2a69e7-cc86-4f1b-81d9-35b8b23b937b
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 386afdf91995f3e38eced269375e5e49ef6044d0
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858558"
---
# <a name="resolve-a-threat-found-by-sandblast-mobile-protect"></a>解决 SandBlast Mobile Protect 发现的威胁

SandBlast Mobile Protect 是一项移动威胁防御服务，可识别和评估 iOS 设备上的潜在威胁。 然后，它将报告威胁，以便你可在公司门户应用中查看。 威胁在应用中显示为未解决的非符合性问题。 只要存在这些威胁，就可能无法：   

* 连接公司电子邮件
* 连接公司 Wi-Fi
* 连接 SharePoint Online
* 使用 OneDrive 同步公司文件
* 访问公司应用

本文介绍如何识别 Sandblast Mobile Protect 威胁警报以及如何解决这些警报。  

## <a name="troubleshoot-virus-or-security-threat"></a>排查病毒或安全威胁  
如果检测到病毒或安全威胁，SandBlast Mobile Protect 应用将根据组织的访问策略实施操作。 访问策略可能阻止你访问工作网络、应用和电子邮件。  

![SEP Mobile 应用警报消息的示例屏幕截图。](./media/skycure-list-of-potential-issues-android.png)  
SandBlast Mobile Protect 将提示你采取操作以重新获得失去的访问权限。 选择威胁，并按照应用中的说明解决威胁。

由于应用与公司的 MDM 提供程序集成，因此还可在公司门户应用中看到访问权限受限的相关警告。 警告将指示打开 Sandblast Mobile Protect 以解决病毒或安全威胁。  

  ![公司门户设备页的示例屏幕截图，其中显示 Sandblast Mobile Protect 警告。](./media/CP-lookout-virus-banner-1808.png)  

## <a name="troubleshoot-an-app-threat"></a>排查应用威胁  

如果安装的应用对设备构成威胁，你将在 SandBlast Mobile Protect 应用内收到通知。 如果设备上仍存在此受影响的应用，将无法访问公司资源。  

要解决此问题，请从 SandBlast Mobile Protect 中的威胁列表中选择此应用。 然后按照说明删除并卸载该应用。  

仍需帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)中查找他们的联系信息。  
