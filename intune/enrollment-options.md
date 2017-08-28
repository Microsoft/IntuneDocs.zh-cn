---
title: "Intune 的注册选项"
description: 
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
ms.openlocfilehash: 3514b580a4e35cc9e0813d6dd7fd0e1eee550d7c
ms.sourcegitcommit: af013af8d9a63c9aa16e5e9eddf38ad9c5a77898
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2017
---
# <a name="enrollment-options-for-intune"></a>Intune 的注册选项

作为 Intune 管理员，可以配置设备注册来帮助用户并启用 Intune 功能。  Intune 包括以下注册选项：

## <a name="terms-and-conditions"></a>条款和条件

可以要求用户先接受公司的条款和条件，然后他们才可以使用公司门户注册其设备并访问公司应用和电子邮件等资源。 条款和条件配置是可选的。 详细了解[条款和条件](terms-and-conditions-create.md)。

## <a name="enrollment-restrictions"></a>注册限制

可选择通过下列方式限制设备注册：
- 设备平台
- 每个用户的设备数
- 阻止个人设备

详细了解[注册限制](enrollment-restrictions-set.md)。

## <a name="enable-apple-device-enrollment"></a>启用 Apple 设备注册

必须拥有 MDM Push Certificate 才能注册 iOS 和 macOS 设备。 详细了解 [MDM Push Certificate](apple-mdm-push-certificate-get.md)。

## <a name="corporate-identifiers"></a>企业标识符

可列出国际移动设备标识符 (IMEI) 号码和序列号，以标识公司拥有的设备。 详细了解[企业标识符](corporate-identifiers-add.md)。
## <a name="multi-factor-authentication"></a>多重身份验证

可要求用户在注册设备时使用其他验证方法，例如电话、PIN 或生物特征数据。 了解[多重身份验证](multi-factor-authentication.md)的详细信息。

## <a name="device-enrollment-manager"></a>设备注册管理器
可让用户成为设备注册管理员。  DEM 用户可使用单个用户帐户注册大量移动设备。 设备注册管理员 (DEM) 帐户最多可注册 1,000 台设备。 详细了解[设备注册管理员](device-enrollment-manager-enroll.md)。

## <a name="device-categories"></a>设备类别

可基于定义的类别，使用设备类别自动向组添加设备。 将设备整理成组可更轻松地管理这些设备。 详细了解[设备类别](device-group-mapping.md)。
