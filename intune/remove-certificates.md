---
title: 在 Microsoft Intune 中删除 SCEP 或 PKCS 证书 - Azure | Microsoft Docs
titleSuffix: ''
description: 管理员可以使用擦除或停用操作，从 Microsoft Intune 中删除证书。 在某些情况下，证书将自动删除，如取消注册设备或删除符合性策略。 而在某些情况下，证书会自动保留在设备上，如丢失或删除 Intune 许可证。 请查看 Android、Android Enterprise、iOS、macOS 和 Windows 设备适用的不同方式。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: de2f201e6a7d0181847db5d212625c9eed9ea698
ms.sourcegitcommit: 9c06d8071b9affeda32e367bfe85d89bc524ed0b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413767"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>在 Microsoft Intune 中删除 SCEP 和 PKCS 证书

在 Microsoft Intune 中，可以使用简单证书注册协议 (SCEP) 和公钥加密标准 (PKCS) 证书配置文件向设备添加证书。 

这些证书也可以在[擦除](devices-wipe.md#wipe)或[停用](devices-wipe.md#retire)设备时删除。 在某些情况下，证书将自动删除，而在另外一些情况下，证书将保留在设备上。 本文列出了一些常见场景，以及它们对 PKCS 和 SCEP 证书的影响。

> [!NOTE]
> 若要为已从本地 Active Directory 或 Azure Active Directory (Azure AD) 中删除的用户删除和撤销证书，请按顺序执行以下步骤：
>
> 1. 擦除或停用用户设备。
> 2. 从本地 Active Directory 或 Azure AD 删除用户。

## <a name="manually-deleted-certificates"></a>手动删除证书  

手动删除证书是应用于所有平台的方案，它适用于通过 SCEP 或 PKCS 证书配置文件预配的所有证书。 例如，如果某一设备仍是证书策略的目标设备，用户可能从该设备中删除证书。  

在此应用场景中，删除该证书后，设备下次使用 Intune 签入时，将被识别为不符合要求，因为它缺少预期的证书。 随后 Intune 将颁发新证书，将设备还原为符合状态。 还原证书不需要执行任何其他操作。  


## <a name="windows-devices"></a>Windows 设备

#### <a name="scep-certificates"></a>SCEP 证书

出现以下情况时，将吊销并删除 SCEP 证书  ：

- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。
- 设备从 Azure AD 组中删除。
- 证书配置文件从组分配中删除。

出现以下情况时，将吊销 SCEP 证书：
- 管理员更改或更新 SCEP 配置文件。

出现以下情况时，将删除根证书：
- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，SCEP 证书将保留在设备上（证书不会被撤销，也不会被删除）： 
- 用户丢失 Intune 许可证。
- 管理员撤销 Intune 许可证。
- 管理员从 Azure AD 中删除用户或组。

#### <a name="pkcs-certificates"></a>PKCS 证书

出现以下情况时，将吊销并删除 PKCS 证书  ：

- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，将删除根证书：
- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，PKCS 证书将保留在设备上（证书不会被吊销，也不会被删除）  ：
- 用户丢失 Intune 许可证。
- 管理员撤销 Intune 许可证。
- 管理员从 Azure AD 中删除用户或组。
- 管理员更改或更新 PKCS 配置文件。
- 证书配置文件从组分配中删除。


## <a name="ios-devices"></a>iOS 设备

#### <a name="scep-certificates"></a>SCEP 证书

出现以下情况时，将吊销并删除 SCEP 证书  ：

- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。
- 设备从 Azure AD 组中删除。
- 证书配置文件从组分配中删除。

出现以下情况时，将吊销 SCEP 证书：
- 管理员更改或更新 SCEP 配置文件。

出现以下情况时，将删除根证书：
- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，SCEP 证书将保留在设备上（证书不会被撤销，也不会被删除）： 
- 用户丢失 Intune 许可证。
- 管理员撤销 Intune 许可证。
- 管理员从 Azure AD 中删除用户或组。

#### <a name="pkcs-certificates"></a>PKCS 证书

出现以下情况时，将吊销并删除 PKCS 证书  ：

- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，将删除 PKCS 证书：
- 证书配置文件从组分配中删除。
  
出现以下情况时，将删除根证书：
- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，PKCS 证书将保留在设备上（证书不会被吊销，也不会被删除）  ：
- 用户丢失 Intune 许可证。
- 管理员撤销 Intune 许可证。
- 管理员从 Azure AD 中删除用户或组。
- 管理员更改或更新 PKCS 配置文件。

## <a name="android-knox-devices"></a>Android KNOX 设备

#### <a name="scep-certificates"></a>SCEP 证书

出现以下情况时，将吊销并删除 SCEP 证书  ：
- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。

出现以下情况时，将吊销 SCEP 证书：
- 管理员运行[停用](devices-wipe.md#retire)操作。
- 设备从 Azure AD 组中删除。
- 证书配置文件从组分配中删除。
- 管理员从 Azure AD 中删除用户或组。
- 管理员更改或更新 SCEP 配置文件。

出现以下情况时，将删除根证书：
- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，SCEP 证书将保留在设备上（证书不会被撤销，也不会被删除）： 
- 用户丢失 Intune 许可证。
- 管理员撤销 Intune 许可证。
- 管理员从 Azure AD 中删除用户或组。

#### <a name="pkcs-certificates"></a>PKCS 证书

出现以下情况时，将吊销并删除 PKCS 证书  ：

- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，将删除根证书：
- 用户取消注册。
- 管理员运行[擦除](devices-wipe.md#wipe)操作。
- 管理员运行[停用](devices-wipe.md#retire)操作。

出现以下情况时，PKCS 证书将保留在设备上（证书不会被吊销，也不会被删除）  ：
- 用户丢失 Intune 许可证。
- 管理员撤销 Intune 许可证。
- 管理员从 Azure AD 中删除用户或组。
- 管理员更改或更新 PKCS 配置文件。
- 证书配置文件从组分配中删除。
  
  
> [!NOTE]
> Android for Work 设备未针对上述情形进行验证。 Android 旧设备（任何非 Samsung、非工作配置文件设备）未启用证书删除功能。 

## <a name="macos-certificates"></a>macOS 证书

#### <a name="scep-certificates"></a>SCEP 证书

出现以下情况时，将吊销并删除 SCEP 证书  ：
- 用户取消注册。
- 管理员运行[停用](devices-wipe.md#retire)操作。
- 设备从 Azure AD 组中删除。
- 证书配置文件从组分配中删除。

出现以下情况时，将吊销 SCEP 证书：
- 管理员更改或更新 SCEP 配置文件。

出现以下情况时，SCEP 证书将保留在设备上（证书不会被撤销，也不会被删除）： 
- 用户丢失 Intune 许可证。
- 管理员撤销 Intune 许可证。
- 管理员从 Azure AD 中删除用户或组。

> [!NOTE]
> 不支持使用[擦除](devices-wipe.md#wipe)操作将 macOS 设备恢复出厂设置。

#### <a name="pkcs-certificates"></a>PKCS 证书

macOS 上不支持 PKCS 证书。

