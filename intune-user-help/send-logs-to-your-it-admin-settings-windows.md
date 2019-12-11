---
title: 将 Windows 10 设备的日志发送给公司支持人员 | Microsoft Docs
description: 将 Windows 10 1511 设备注册到 Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e88fa55391ace4f8a86416412489ca055083503
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502046"
---
# <a name="send-logs-to-your-company-support-from-the-settings-app-for-windows-10"></a>通过 Windows 10 的“设置”应用将日志发送给公司支持人员

使用“设置”应用对适用于 Windows 10 的公司门户进行故障排除。 如果在 Windows 10 设备上使用应用时遇到问题，可以向支持团队发送电子邮件寻求帮助。 公司门户应用中发生的事件和错误将保存在设备上一个名为“诊断日志”  的特殊文档中。 它们可以包含关于错误的额外见解，并且在导出时对支持团队非常有用。

1. 若要打开“设置”应用，请转到“启动”菜单 >“设置”    。 还可以在搜索栏中搜索“设置”  。
2. 转至“帐户”   > “访问工作或学校”  。
3. 选择“导出管理日志文件”  。

   ![“访问工作或学校屏幕”显示了“相关设置”标题下的“导出”选项。](./media/w10-export-logs.png)

4. 日志将保存在 **C:\Users\Public\Public Documents\MDMDiagnostics** 中。 将创建两个文件：一个是日志本身；另一个是一个特殊文档，允许管理员使用其他程序（如 Microsoft Excel）查看日志。 将这两个文件附加到电子邮件中发送给管理员。如果多次执行此操作，请仅从创建日志的那天选择文件。 

另外，可能还需要[通过公司门户应用发送日志](send-logs-to-your-it-admin-cp-windows.md)，以便为公司支持人员提供更多帮助，协助他们尽力对所发现的问题进行故障排除。 

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
