---
title: 解决 Zimperium zIPS 在 Android 上发现的威胁
description: 了解如何解决在 Android 设备上发现的安全和应用威胁。
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
ms.assetid: 9ffbb656-93cd-4e0b-96c0-c5038cd2cf31
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 204ee3d70e2ae65eb495eb30fbf4d5064ccc3050
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857297"
---
# <a name="resolve-a-threat-found-by-zimperium-zips"></a>解决 Zimperium zIPS 发现的威胁

Zimperium zIPS 是一项移动威胁防御服务，可识别 Android 设备上的潜在威胁。 这些威胁将被报告到公司门户应用，并显示为未解决的非符合性问题。 如果设备被识别为非符合性设备，则可能无法：

* 连接公司电子邮件
* 连接公司 Wi-Fi
* 连接 SharePoint Online
* 使用 OneDrive 同步公司文件
* 访问公司应用

本文介绍如何识别 Zimperium zIPS 威胁警报以及如何解决这些问题。 

## <a name="troubleshoot-virus-or-security-threat"></a>排查病毒或安全威胁  
如果检测到病毒或安全威胁，Zimperium zIPS 将根据组织的访问策略强制实施限制。 公司访问策略可能阻止你的设备访问工作网络、应用和电子邮件。  

Zimperium zIPS 将提示你采取操作以重新获得失去的访问权限。 选择威胁，并按照应用中的说明解决威胁。

由于应用与公司的 MDM 提供程序集成，因此也可在公司门户应用中看到访问权限受限的相关警告。 警告将指示打开 Zimperium zIPS 以解决病毒或安全威胁。  

  ![公司门户设备页的示例屏幕截图，其中显示 Zimperium zIPS 警告。](./media/CP-lookout-virus-banner-1808.png)  

选中受影响设备下方显示的警告横幅。 Zimperium zIPS 将打开并指示如何消除该威胁。  

## <a name="resolve-an-app-threat"></a>解决应用威胁

如果安装的应用对设备构成威胁，你将在 Zimperium zIPS 应用内收到通知。 如果设备上仍存在此受影响的应用，将无法访问公司资源。  

要解决此问题，请从 Zimperium zIPS 中的威胁列表中选择此应用。 然后按照屏幕上的指示删除并卸载该应用。    

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。 
