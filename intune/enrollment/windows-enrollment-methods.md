---
title: 适用于 Windows 设备的 Intune 注册方法
titleSuffix: Microsoft Intune
description: 了解在 Intune 中注册 Windows 设备的不同方法
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: 060c3c00a228794d3f237a6362b048bf23e1a933
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547722"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>适用于 Windows 设备的 Intune 注册方法

要管理 Intune 中的设备，必须先在 Intune 服务中注册设备。 个人拥有和公司拥有的设备都可以注册，以进行 Intune 管理。 

有两种方法可以在 Intune 中注册设备：
- 用户可自助注册其 Windows 电脑 
- 管理员可以配置策略以强制实施自动注册，而无需任何用户参与

## <a name="user-self-enrollment-in-intune"></a>Intune 中的用户自助注册

用户可以使用以下任何方法自助注册其 Windows 设备：

- [自带设备办公 (BYOD)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device)：用户通过选择从设备的“设置”连接“工作和学校”帐户来注册其个人拥有的设备   。 过程如下：
  - 使用 Azure Active Directory 注册设备以访问企业资源（如电子邮件）。
  - 将设备作为个人拥有的设备 (BYOD) 注册到 Intune 中。
如果管理员已配置自动注册（Azure AD 高级订阅可用），则用户只需输入一次凭据。 否则，他们必须通过仅限 MDM 注册单独注册并重新输入其凭据。  
- “仅限 MDM 注册”允许用户将加入电脑的现有工作组、Active Directory 或 Azure Active 目录注册到 Intune  。 用户从现有 Windows 电脑上的“设置”中注册。 不建议使用此方法，因为它不会将设备注册到 Azure Active Directory 中。 它还会禁止使用条件访问等功能。
- [Azure Active Directory (Azure AD) 联接](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) - 使用 Azure Active Directory 加入设备，并允许用户使用其 Azure AD 凭据登录 Windows。 如果启用了自动注册，则设备将自动注册到 Intune 中。 自动注册的好处在于，用户可以单步执行过程。 否则，他们必须通过仅限 MDM 注册单独注册并重新输入其凭据。 用户在初始 Windows OOBE 或“设置”期间以这种方式注册。 该设备在 Intune 中标记为公司拥有的设备。
- [Autopilot](enrollment-autopilot.md) -自动执行 Azure AD 联接，并将新公司拥有的设备注册到 Intune。 此方法简化了开箱即用体验，无需将自定义操作系统映像应用到设备上。 管理员使用 Intune 管理 Autopilot 设备时，他们可以在注册设备后管理策略、配置文件和应用等。  有四种类型的 Autopilot 部署：[自部署模式](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying)（适用于网亭、数字签名或共享设备）、[用户驱动模式](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)（适用于传统用户）、[白手套](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove)（使合作伙伴和 IT 人员可以预配 Windows 10 电脑，使其配置完善且可用于业务）和[适用于现有设备的 Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices)（使用户可将最新版本的 Windows 10 轻松部署到现有设备）。

## <a name="administrator-based-enrollment-in-intune"></a>Intune 中基于管理员的注册

管理员可以设置以下不需要用户交互的注册方法：

- [混合 Azure AD 联接](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)允许管理员配置 Active Directory 组策略，以自动注册已联接混合 Azure AD 的设备。 
- [Configuration Manager 共同管理](https://docs.microsoft.com/configmgr/comanage/overview)允许管理员将其现有的 Configuration Manager 受管理设备注册到 Intune 中，以获得 Intune 和 Configuration Manager 的双重优势。 
- [设备注册管理员](device-enrollment-manager-enroll.md) (DEM) 是一个特殊的服务帐户。 DEM 帐户具有以下权限，即允许授权用户注册和管理多个公司拥有的设备。 这些类型的设备非常适用于销售点或实用工具应用，但是不适用于需要访问电子邮件或公司资源的用户。 这种方法还禁止使用条件访问等功能。 
- [批量注册](../windows-bulk-enroll.md)允许授权用户将大量新的公司拥有的设备加入 Azure Active Directory 和 Intune。 可以使用 Windows 配置设计器 (WCD) 应用来创建预配包。 然后，在初始 Windows OOBE 体验期间或从现有 Windows 电脑使用 USB 介质时，可以安装预配包以自动将设备注册到 Intune 中。 这种方法还禁止使用条件访问。 
- [注册 Windows IoT Core 设备](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment)通过使用 Windows IoT Core 仪表板准备设备，然后使用 Windows 配置设计器来创建预配包完成。 然后，在初始启动过程中使用 SD 卡媒体，将会安装预配包以将设备自动注册到 Intune。

## <a name="next-steps"></a>后续步骤

[了解 Windows 注册方法的功能](enrollment-method-capab.md)
