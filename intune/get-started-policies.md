---
title: Microsoft Intune 中的策略入门
titlesuffix: ''
description: 创建策略来帮助保护公司数据并管理最终用户用于访问公司资源的设备。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b8bffd0435988cc59c5c0e4d754b861729d466ae
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-with-creating-policies"></a>创建策略入门

Intune 入门的主要目标之一是注册设备，以确保其符合公司策略。 符合性策略不仅有助于管理专用的设备类型，如公司拥有的网亭，还可帮助管理个人（自带）设备、平板电脑和无用户设备。

![几乎没有数据的符合性仪表板](/intune/media/generic-compliance-dashboard.png)

使用符合性策略管理以下区域中的移动设备：

* 控制每个用户注册的设备数
* 管理设备设置（如设备级别的加密、密码长度、照相机使用情况）
* 提供应用、电子邮件配置文件、VPN 配置文件等等。
* 评估安全符合性策略的设备级条件

可以为每个平台单独创建符合性策略。 在此练习中，我们只讨论 iOS。 iOS 设备可使用以下策略：

* PIN 或密码配置
* 设备加密
* 已越狱设备
* 电子邮件配置文件
* 最低操作系统版本
* 最高操作系统版本

__如何创建策略？__

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 选择“设备符合性”。
4. 在“设备符合性”窗格上，选择“策略”。
5. 选择“创建策略”，然后填写“名称”和“说明”等详细信息。 
6. 选择“iOS”作为“平台”。
6. 在“设置”中，选择“系统安全”，然后将“需要密码来解锁移动设备”切换为“需要”。 还可以设置其他规则，例如“最短密码长度”、“所需的密码类型”和“密码中的非字母数字字符数”。 完成策略设置后，选择“确定”。
7. 返回到“创建策略”窗格卡，然后选择“创建”。
8. 策略创建后，选择“分配”将策略分配到测试组。 选择测试组 – 其中应包含测试用户 – 然后通过单击“保存”将策略分配到该组。
9. 等待几分钟，然后注册的设备会提示它需要更新密码以便与公司策略保持一致。 还可以通过依次点击设备名称和“同步”按钮，在“适用于 iOS 的公司门户应用”中对此进行手动检查。

## <a name="next-steps"></a>后续步骤

[设备注册入门](get-started-enroll.md) - 通过完整体验 iOS 设备的注册过程了解整个注册过程。

## <a name="learn-more"></a>了解详细信息

* [监视 Intune 设备符合性策略](compliance-policy-monitor.md)
* [通过 Intune 使用条件性访问策略的常见方式](conditional-access-intune-common-ways-use.md)
