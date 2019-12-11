---
title: 解决 SandBlast Mobile Protect 在 Android 上发现的威胁 | Microsoft Docs
description: 了解如何解决 SandBlast Mobile Protect 在 Android 上发现的威胁。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 449c34ec-2d94-4c7f-8691-a5200efee3cb
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81248206fe406da6ad2d8a031c3f58ec170e18ef
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72507835"
---
# <a name="resolve-a-threat-found-by-sandblast-mobile-protect"></a>解决 SandBlast Mobile Protect 发现的威胁

SandBlast Mobile Protect 是一项移动威胁防御服务，可识别 Android 设备上的潜在威胁。 它将报告威胁，以便你可在公司门户应用中查看。 威胁在应用中显示为未解决的非符合性问题。 只要存在这些威胁，就可能无法：   

* 连接公司电子邮件
* 连接公司 Wi-Fi
* 连接 SharePoint Online
* 使用 OneDrive 同步公司文件
* 访问公司应用

本文介绍如何识别 Sandblast Mobile Protect 威胁警报以及如何解决这些警报。  

## <a name="troubleshoot-virus-or-security-threat"></a>排查病毒或安全威胁  
如果检测到病毒或安全威胁，SandBlast Mobile Protect 应用将根据组织的访问策略实施操作。 公司访问策略可能阻止你访问工作网络、应用和电子邮件。  

![SEP Mobile 应用警报消息的示例屏幕截图。](./media/skycure-list-of-potential-issues-android.png)  

但是，SandBlast Mobile Protect 还将提示你采取操作以重新获得失去的访问权限。 选择威胁，并按照应用中的说明解决威胁。

由于应用与公司的 MDM 提供程序集成，因此还可在公司门户应用中看到访问权限受限的相关警告。 警告将指示打开 Sandblast Mobile Protect 以解决病毒或安全威胁。

  ![公司门户设备页的示例屏幕截图，其中显示 SandBlast Mobile Protect 警告。](./media/CP-lookout-virus-banner-1808.png)  

## <a name="troubleshoot-an-app-threat"></a>排查应用威胁  

如果安装的应用对设备构成威胁，你将在 SandBlast Mobile Protect 应用内收到通知。 如果设备上仍存在此受影响的应用，将无法访问公司资源。  

要解决此问题，请从 SandBlast Mobile Protect 中的威胁列表中选择此应用。 然后按照说明删除并卸载该应用。     

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
