---
title: Microsoft Intune 中的策略入门 - Azure | Microsoft Docs
description: 创建策略来帮助保护公司数据并管理最终用户用于访问公司资源的设备。 然后，向组分配策略。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7fa1b596a1800971919cfc0ab3e94d2d16ec328
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271518"
---
# <a name="get-started-with-creating-policies"></a>创建策略入门

Intune 策略非常适合用于注册设备以确保其符合公司策略。 符合性策略有助于管理专用的设备类型，如公司拥有的网亭、个人（自带）设备、平板电脑和无用户设备。

![几乎没有数据的符合性仪表板](/intune/media/generic-compliance-dashboard.png)

可使用符合性策略管理移动设备，包括：

* 控制用户在 Intune 中注册的设备数量
* 管理设备设置，如设备级加密、密码长度和照相机使用情况
* 交付应用、电子邮件配置文件、VPN 配置文件等
* 评估安全符合性策略的设备级条件

可面向所有平台创建符合性策略，如 iOS、Android、Windows 等。 对于本练习，请使用 iOS。 iOS 设备可使用以下策略：

* PIN 或密码配置
* 设备加密
* 已越狱设备
* 电子邮件配置文件
* 最低操作系统版本
* 最高操作系统版本

## <a name="create-a-policy"></a>创建策略

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备符合性” > “策略” > “创建策略”。
4. 输入策略“名称”和“说明”。 
5. 对于“平台”，选择“iOS”。
6. 在“设置”中，选择“系统安全”，然后将“需要密码才可解锁移动设备”设置为“需要”。 

    还可设置其他规则，例如： 
    - **最短密码长度**
    - **所需的密码类型**
    - **密码中非字母数字字符的数量**
    
    策略设置完成后，选择“确定”。
  
7. 返回“创建策略”，选择“创建”。 此步骤可创建策略并在“设备符合性” > “策略”下列出该策略。
8. 选择新策略，然后选择“分配”。 可以包括或排除 Azure Active Directory (AD) 安全组。
选择“所选组”可查看现有 Azure AD 安全组。 选择想要应用此策略的用户组，并选择“保存”向用户部署该策略。

为了符合新公司策略，几分钟后，注册的设备将提示输入更新后的密码。 可在“iOS 版公司门户应用”中手动检查更新。 打开公司门户应用，选择设备名称，然后选择“同步”。

> [!NOTE]
> 应用到动态设备组的新策略可能需要 8 小时才可应用到组中的所有设备。

## <a name="next-steps"></a>后续步骤

[设备注册入门](get-started-enroll.md) - 通过完整体验 iOS 设备的注册过程了解整个注册过程。

## <a name="learn-more"></a>了解详细信息

* [监视 Intune 设备符合性策略](compliance-policy-monitor.md)
* [通过 Intune 使用条件性访问策略的常见方式](conditional-access-intune-common-ways-use.md)
