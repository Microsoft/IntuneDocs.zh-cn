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
ms.openlocfilehash: ffabcace189efd60e9d532172ecd1f2a048eec2c
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2019
ms.locfileid: "74562410"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Apple 用户注册支持的 Intune 操作和选项

用户注册支持部分设备管理选项。 如果将预先存在的配置文件应用于用户注册设备，则只会将用户注册支持的设置应用于该设备。

> [!NOTE]
> Intune 中对 Apple 用户注册的支持目前处于预览状态。

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

## <a name="app-deployment-options"></a>添加部署选项
可在用户注册设备上部署以下应用类型：
- 用户许可的批量采购计划 (VPP) 应用，包括自定义应用
- 业务线 (LOB) 应用
- Web 应用

## <a name="other-supported-options"></a>其他支持的选项

对于使用 Apple 用户注册注册的设备，Intune 支持以下选项：
- 每个应用 VPN。 此支持不包括 Safari 域，因为用户注册不支持配置 Safari 设置。
- WiFi 
- 取消注册后删除企业应用
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
- 将 App Store 应用作为托管应用安装。
- 托管 APFS 卷之外的应用程序的 MDM 控制。
- 应用程序保护策略仍将应用于这些应用。 但是，除非用户从其设备中删除这些应用，否则你无法接管管理或部署这些应用的托管版本。
- 需要监督的操作、配置、设置和命令。 

## <a name="options-not-supported-in-preview"></a>预览版不支持的选项
- 允许/阻止个人拥有的设备的注册设备类型限制 

## <a name="known-issues-in-preview"></a>预览版中的已知问题
- VPP 许可证吊销：未显示已吊销许可证的通知。 当前行为是吊销成功，但不通知最终用户。 
- VPP 应用程序报告：在位于“客户端应用”>“应用”>“[应用名称]”>“设备安装状态”的报表中，部署到用户注册设备的 VPP 应用程序将报告为“失败”，即使应用程序成功部署到设备也是如此。 
- 应用程序报告：对于用户注册不支持的应用类型，报表可能会提供无关的错误消息。 
- 公司门户应用体验：无论用户注册的设备是否支持这些应用程序类型，用户都会看到所有相关应用程序。 
- 公司门户应用体验：用户会看到相同的文本，指出组织可以看到和不可以看到的用户和设备注册的内容。
- 如果用户在注册过程中选择“我的组织拥有此设备”，则在 Intune 内仍会将设备标识为“个人”，除非在管理控制台中或通过关系图进行修改。 
- 注册目标：iPadOS 未在平台选择器中列出。 iPadOS 在预览版中受支持，但在管理控制台中未显式声明。 


## <a name="next-steps"></a>后续步骤

[设置 iOS 和 iPadOS 用户注册](ios-user-enrollment.md)
