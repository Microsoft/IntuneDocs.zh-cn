---
title: JAMF Pro 向 Intune 发送的数据
titleSuffix: Microsoft Intune
description: 集成 Jamf Pro 使用 Intune 管理 Mac 后，请查看 Jamf Pro 发送到 Microsoft Intune 的数据列表。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86f2f47322e668815d1ff37ce6c2de1e4d6cdc16
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670900"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Jamf Pro 向 Intune 发送的数据

使用 [Jamf Pro](https://www.jamf.com) 管理使用 Intune 的最终用户 Mac 时，Jamf Pro 会捕获有关托管的 macOS 设备的清单信息。 Jamf Pro 向 Intune 报告以下信息：

* 设备 Azure AD ID
* JAMF 清单状态（Jamf Pro 在过去 24 小时内签入的计算机的清单状态）
* 操作系统版本
* 用户 Azure AD ID
* 已加密（FileVault 2）
* 网关守卫状态
* 密码：最小字符集数
* 密码过期(天)
* 密码类型 - 简单、字母数字字符或未知
* 防止自动登录
* 所需的密码长度
* 密码：阻止重用的曾用密码数
* 系统完整性保护
* 上次签入时间
* 体系结构类型
* 可用的 RAM 槽
* 电池容量
* 启动 ROM
* 总线速度
* 缓存大小
* 设备名称
* 域加入
* Jamf ID
* MAC 地址
* 品牌
* 型号
* 模型标识符
* NIC 速度
* 内核数量
* 处理器数目
* 操作系统
* 平台
* 处理器速度
* 处理器类型
* 辅助 MAC 地址
* 序列号
* SMC 版本
* 总 RAM
* UDID
* 用户电子邮件


通过在“所有设备”视图中选择“删除”，可从 Intune 控制台中删除 Jamf 托管设备   。 通过选择多个设备并单击“删除”，可启用批量设备删除  。

获取有关如何[在 Jamf Pro 文档中删除 Jamf 托管设备](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)的信息。还可通过 [Jamf 支持](https://www.jamf.com/support/)提交支持票证，获取更多帮助。 

