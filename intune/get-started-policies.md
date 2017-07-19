---
title: "策略入门"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 232ec25c34df5e71f70737ca5f0f8a2ef12a05f0
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-with-policies"></a>策略入门

Intune 入门的主要目标之一是注册设备，以确保其符合公司策略。 符合性策略不仅有助于管理专用的设备类型，如公司拥有的网亭，还可帮助管理个人（自带）设备、平板电脑和无用户设备。

![具有很少数据的符合性仪表板](/intune/media/generic-compliance-dashboard.png)

符合性策略为移动设备提供以下管理功能：

* 控制每个用户注册的设备数
* 管理设备设置（如设备级别的加密、密码长度、相机使用情况）
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
2. 使用“搜索资源”搜索“Intune”。
3. 选择“设备符合性”。
4. 在“设备符合性”边栏选项卡上，选择“策略”。
5. 选择“创建策略”，然后填写“名称”和“说明”等详细信息。 选择“iOS”作为“平台”。
6. 在“设置”中，选择“系统安全”，然后将“需要密码来解锁移动设备”切换为“需要”。 还可以设置其他规则，例如“最短密码长度”、“所需的密码类型”和“密码中的非字母数字字符数”。 完成策略设置后，选择“确定”。
7. 返回到“创建策略”边栏选项卡，然后选择“创建”。
8. 策略创建后，选择“分配”将策略分配到测试组。 选择测试组 – 其中应包含测试用户 – 然后通过单击“保存”将策略分配到该组。
9. 等待几分钟，然后注册的设备会提示它需要更新密码以便与公司策略保持一致。 还可以通过依次点击设备名称和“同步”按钮，在“适用于 iOS 的公司门户应用”中对此进行手动检查。
