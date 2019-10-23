---
title: Apple 用户注册支持的 Intune 操作和选项
titleSuffix: Microsoft Intune
description: 了解 Apple 用户注册支持哪些 Intune 操作和选项
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96c802e76aab673aa6a9108dc0a14f553c26b96b
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505416"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Apple 用户注册支持的 Intune 操作和选项

用户注册支持部分设备管理选项。 如果将预先存在的配置文件应用于用户注册设备，则只会将用户注册支持的设置应用于该设备。

## <a name="password-settings"></a>密码设置

在用户注册设备上，如果配置任何密码设置，则“简单密码”  设置将自动设置为“阻止”  ，并强制使用 6 位 PIN。

例如，配置“密码过期”  设置，并将此策略推送到用户注册的设备。 在设备上，会出现以下情况：
- 将忽略“密码过期”  设置。
- 不允许使用简单密码，如 `1111` 或 `1234`。
- 强制使用 6 位 pin。

## <a name="administrator-remote-device-actions-and-options"></a>管理员远程设备操作和选项
管理员可以在用户注册设备上执行以下操作和选项：
- 停用
- 删除
- 远程锁定
- 同步

不支持所有其他操作。

## <a name="end-user-actions"></a>最终用户操作
在用户注册设备上，最终用户可以从公司门户应用程序和网站对他们的设备执行以下操作：
- 重命名。 此操作仅适用于公司门户中面向用户的名称。 它不会在该上下文之外完全重命名设备。
- 删除
- 远程锁定
- 检查状态

## <a name="other-supported-options"></a>其他支持的选项

对于使用 Apple 用户注册注册的设备，Intune 支持以下选项：
- 每个应用 VPN。 此支持不包括 Safari 域，因为用户注册不支持配置 Safari 设置。
- WiFi 
- 取消注册后删除企业应用
- 通过用户许可的批量采购计划 (VPP) 进行应用部署
- 越狱检测

支持以下限制：
- 在非托管应用中查看公司文档
- 在公司应用中查看非公司文档
- 允许非托管应用从托管联系人帐户读取
- 将 AirDrop 视为非托管目标
- 需要加密的备份
- 通过托管的应用同步到云
- 在设备锁定时访问控制中心
- 在设备锁定时访问通知中心
- 在设备锁定时显示“今日”视图
- 阻止屏幕截图
- 阻止企业簿备份
- 阻止企业簿元数据同步
- 需要加密的备份
- 需要检测戴表手腕
- 阻止 Siri
- 在设备锁定时阻止 Siri
- 需要 Safari 欺诈警告
- 阻止向 Apple 提交诊断


## <a name="options-not-supported"></a>不支持的选项
通过用户注册进行注册的设备不支持以下选项。 如果需要这些选项，请查看适用于个人拥有的设备的设备注册或适用于公司设备的自动设备注册。
- 收集托管 APFS 卷之外的应用的应用清单。
- 收集托管 APFS 卷之外的证书和预配配置文件的清单。
- 收集 UDID 和其他永久设备标识符。
- 用户注册支持每个注册设备的唯一注册 ID，但在取消注册后不会保留此 ID。
- 由于此限制，不支持以下 Intune 功能：
- 使用序列号的使用者名称格式的 SCEP 用户配置文件。
- 设备级别的 VPN。
- 设备许可的 VPP 应用部署。
- 托管 APFS 卷之外的应用程序的 MDM 控制。
- 应用程序保护策略仍将应用于这些应用。 但是，除非用户从其设备中删除这些应用，否则你无法接管管理或部署这些应用的托管版本。
- 需要监督的操作、配置、设置和命令。 

## <a name="next-steps"></a>后续步骤

[设置 iOS 和 iPadOS 用户注册](ios-user-enrollment.md)