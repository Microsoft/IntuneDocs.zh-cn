---
title: "Microsoft Intune 预览版中的已知问题"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：阅读预览版中的已知问题"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: ec3f87994b19591bda4ec201eac3c839798d634c
ms.lasthandoff: 03/15/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Microsoft Intune 预览版中的已知问题


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


使用本主题了解 Intune 预览版中的任何已知问题。

如果要报告此处未列出的 bug，请[打开支持请求](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

如果要请求将新功能添加到 Intune，请考虑在我们的 [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) 网站上提交报告。

## <a name="administration-and-accounts"></a>管理和帐户

- 全局管理员（也被称为租户管理员）可以继续在没有单独的 Intune 或企业移动性套件 (EMS) 许可证的情况下进行日常的管理任务。 但是，如果全局管理员想要使用服务（例如注册他们自己的设备、企业设备，或使用 Intune 公司门户），与任何其他用户一样，他们需要 Intune 或 EMS 许可证。

## <a name="apple-enrollment-profile-migration"></a>Apple 注册配置文件迁移
- 在接下来的几个月里，Intune 将通过新的 Azure 门户实现管理你的 Apple 设备注册计划和 Apple 配置器注册。 如果你删除了 Apple 设备注册计划令牌，而且没有上载更新的令牌，将在新的 Azure 门户中作为迁移 Intune 帐户的一部分还原原始令牌。 若要删除此令牌并禁止 DEP 注册，在 Azure 门户中删除令牌即可。 

