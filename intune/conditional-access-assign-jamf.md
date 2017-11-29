---
title: "将符合性策略应用到 Jamf 管理的设备。"
titlesuffix: Azure portal
description: "使用符合性帮助保护 Jamf 管理的设备。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dd84812a7e7dcf83f01c8d4d2b613706f7700775
ms.sourcegitcommit: b2a6678a0e9617f94ee8c65e7981211483b30ee7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>在使用 Jamf Pro 管理的 Mac 上强制实现符合性

|适用于：Azure 门户中的 Intune |
|--|
|正在查找有关经典门户中的 Intune 的文档？ [请转到此处](/intune/introduction-intune?toc=/intune-classic/toc.json)。|
| |

|目前处于个人预览版|
|--|
|本主题中介绍的功能仅适用于当前使用个人预览版的客户。 对所有客户发布后，此消息将会被删除。|
| |

可以使用 Azure Active Directory 和 Microsoft Intune 的条件访问策略，以确保最终用户符合组织的要求。 可以将这些策略应用到[使用 Jamf Pro 管理](conditional-access-integrate-jamf.md)的 Mac。 这需要能够同时访问 Intune 和 Jamf Pro 控制台。

## <a name="set-up-device-compliance-policies-in-intune"></a>在 Intune 中设置设备符合性策略

1. 打开 Microsoft Azure，然后导航到“Intune” > “设备符合性” > “策略”。 可以为 macOS 创建策略，其中包括对不符合要求的用户和组选择一系列的操作（例如，发送警告电子邮件）。
2. 搜索所需的组，然后向其应用策略。

## <a name="require-the-company-portal-app-for-macos"></a>需要适用于 macOS 的公司门户应用

1. 在 macOS 设备上，转到 https://aka.ms/macoscompanyportal 以下载适用于 macOS 的公司门户应用的当前版本。
2. 打开 Jamf Pro，然后导航到“计算机管理” > “程序包”。
3. 在适用于 macOS 的公司门户应用中创建新的程序包，然后单击“保存”。
4. 打开“计算机” > “策略”，然后选择“新建”。
5. 使用“常规”负载为策略配置设置，其中包括触发器和执行频率。
6. 选择“程序包”负载，然后单击“配置”。
7. 单击“添加”以选择公司门户应用中的程序包。
8. 选择“操作”弹出菜单中的“安装”。
9. 配置程序包的设置。
10. 单击“作用域”选项卡以指定应在哪些计算机上安装公司门户应用。 单击 **“保存”**。 下次，当计算机上出现所选的触发器并符合“常规”负载中的条件时，策略将运行作用域内的设备。

## <a name="direct-your-users-to-register-jamf-pro-managed-devices-with-azure-active-directory"></a>引导用户使用 Azure Active Directory 注册 Jamf Pro 管理的设备

> [!NOTE]
> 在继续下一步骤前，需要为 macOS [部署公司门户](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos)。  

最终用户需要在 Jamf 自助服务中启动公司门户应用，以使用 Azure AD 将设备注册为由 Jamf Pro 管理的设备。

1. 在 Jamf Pro 中，导航到“计算机” > “策略”，然后为设备注册创建新策略。
2. 配置“条件访问”负载，其中包括触发器和执行频率。 将优先级设置为“之后”。
3. 单击“作用域”选项卡，并将策略的作用域设置为所有目标设备。
4. 单击“自助服务”选项卡以将策略应用到 Jamf 自助服务中。 将策略添加到“设备符合性”类别中。 单击 **“保存”**。

## <a name="next-steps"></a>后续步骤

- [Azure Active Directory 中的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Azure Active Directory 中的条件访问入门](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
