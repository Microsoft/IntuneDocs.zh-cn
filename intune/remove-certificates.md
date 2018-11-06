---
title: 在 Microsoft Intune 中删除 SCEP 或 PKCS 证书 - Azure | Microsoft Docs
titleSuffix: ''
description: 管理员可以使用擦除或停用操作，从 Microsoft Intune 中删除证书。 在某些情况下，证书将自动删除，如取消注册设备或删除符合性策略。 而在某些情况下，证书会自动保留在设备上，如丢失或删除 Intune 许可证。 请查看 Android、Android Enterprise、iOS、macOS 和 Windows 设备适用的不同方式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d4287322fd494c97cf24feb8cc16435a4405f2af
ms.sourcegitcommit: 7a649a5995600fb91817643e20a5565caedbb8f2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/26/2018
ms.locfileid: "50150095"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>在 Microsoft Intune 中删除 SCEP 和 PKCS 证书

在 Microsoft Intune 中，可以向设备添加 SCEP 和 PKCS 证书。 这些证书也可以在[擦除](devices-wipe.md#wipe)或[停用](devices-wipe.md#retire)设备时删除。 在某些其他情况下，证书将自动删除，而在某些情况下，证书将保留在设备上。

本文列出了一些常见场景，以及它们对 PKCS 和 SCEP 证书的影响。

> [!NOTE]
> 若要为已从 Active Directory (AD) 或 Azure AD 中删除的用户删除和吊销证书，请务必按顺序执行以下步骤：
>
>    1. 擦除或停用用户设备
>    2. 从 AD 或 Azure AD 中删除用户

## <a name="windows-devices"></a>Windows 设备

#### <a name="scep-certificates"></a>SCEP 证书

- 出现以下情况时，将吊销并删除 SCEP 证书：

  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作
  - 从 Azure Active Directory (AD) 组中删除设备
  - 从组分配中删除符合性策略
  - 从组分配中删除配置文件

- 出现以下情况时，将吊销 SCEP 证书：
  - 管理员更改或更新 SCEP 配置文件

- 出现以下情况时，将删除根证书：
  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作
  - 从组分配中删除符合性策略

- 出现以下情况时，SCEP 证书将保留在设备上（证书不会被吊销，也不会被删除）：
  - 最终用户丢失 Intune 许可证
  - 管理员撤销 Intune 许可证
  - 管理员从 Azure AD 中删除用户或组

#### <a name="pkcs-certificates"></a>PKCS 证书

- 出现以下情况时，将吊销并删除 PKCS 证书：

  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作

- 出现以下情况时，将删除根证书：
  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作

- 出现以下情况时，PKCS 证书将保留在设备上（证书不会被吊销，也不会被删除）：
  - 最终用户丢失 Intune 许可证
  - 管理员撤销 Intune 许可证
  - 管理员从 Azure AD 中删除用户或组
  - 管理员更改或更新 PKCS 配置文件
  - 从组分配中删除配置文件
  - 从组分配中删除符合性策略 


## <a name="ios-devices"></a>iOS 设备

#### <a name="scep-certificates"></a>SCEP 证书

- 出现以下情况时，将吊销并删除 SCEP 证书：

  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作
  - 从 Azure Active Directory (AD) 组中删除设备
  - 从组分配中删除符合性策略
  - 从组分配中删除配置文件

- 出现以下情况时，将吊销 SCEP 证书：
  - 管理员更改或更新 SCEP 配置文件

- 出现以下情况时，将删除根证书：
  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作
  - 从组分配中删除符合性策略

- 出现以下情况时，SCEP 证书将保留在设备上（证书不会被吊销，也不会被删除）：
  - 最终用户丢失 Intune 许可证
  - 管理员撤销 Intune 许可证
  - 管理员从 Azure AD 中删除用户或组

#### <a name="pkcs-certificates"></a>PKCS 证书

- 出现以下情况时，将吊销并删除 PKCS 证书：

  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作

- 出现以下情况时，将删除 PKCS 证书：
  - 从组分配中删除符合性策略
  - 从组分配中删除配置文件
  
- 出现以下情况时，将删除根证书：
  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作

- 出现以下情况时，PKCS 证书将保留在设备上（证书不会被吊销，也不会被删除）：
  - 最终用户丢失 Intune 许可证
  - 管理员撤销 Intune 许可证
  - 管理员从 Azure AD 中删除用户或组
  - 管理员更改或更新 PKCS 配置文件

## <a name="android--android-enterprise-devices"></a>Android 和 Android Enterprise 设备

#### <a name="scep-certificates"></a>SCEP 证书

- 出现以下情况时，将吊销并删除 SCEP 证书：
  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作

- 出现以下情况时，将吊销 SCEP 证书：
  - 管理员运行[停用](devices-wipe.md#retire)操作
  - 从 Azure Active Directory (AD) 组中删除设备
  - 从组分配中删除符合性策略
  - 从组分配中删除配置文件
  - 管理员从 Azure Active Directory (AD) 中删除用户或组
  - 管理员更改或更新 SCEP 配置文件

- 出现以下情况时，将删除根证书：
  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作

- 出现以下情况时，SCEP 证书将保留在设备上（证书不会被吊销，也不会被删除）：
  - 最终用户丢失 Intune 许可证
  - 管理员撤销 Intune 许可证
  - 管理员从 Azure AD 中删除用户或组

#### <a name="pkcs-certificates"></a>PKCS 证书

- 出现以下情况时，将吊销并删除 PKCS 证书：

  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作

- 出现以下情况时，将删除根证书：
  - 最终用户取消注册
  - 管理员运行[擦除](devices-wipe.md#wipe)操作
  - 管理员运行[停用](devices-wipe.md#retire)操作

- 出现以下情况时，PKCS 证书将保留在设备上（证书不会被吊销，也不会被删除）：
  - 最终用户丢失 Intune 许可证
  - 管理员撤销 Intune 许可证
  - 管理员从 Azure AD 中删除用户或组
  - 管理员更改或更新 PKCS 配置文件
  - 从组分配中删除配置文件
  - 从组分配中删除符合性策略 

## <a name="macos-certificates"></a>macOS 证书

#### <a name="scep-certificates"></a>SCEP 证书

- 出现以下情况时，将吊销并删除 SCEP 证书：
  - 最终用户取消注册
  - 管理员运行[停用](devices-wipe.md#retire)操作
  - 从 Azure Active Directory (AD) 组中删除设备
  - 从组分配中删除符合性策略
  - 从组分配中删除配置文件

- 出现以下情况时，将吊销 SCEP 证书：
  - 管理员更改或更新 SCEP 配置文件

- 出现以下情况时，SCEP 证书将保留在设备上（证书不会被吊销，也不会被删除）：
  - 最终用户丢失 Intune 许可证
  - 管理员撤销 Intune 许可证
  - 管理员从 Azure AD 中删除用户或组

> [!NOTE]
> 不支持使用[擦除](devices-wipe.md#wipe)操作将 macOS 设备恢复出厂设置。

#### <a name="pkcs-certificates"></a>PKCS 证书

macOS 上不支持 PKCS 证书。

