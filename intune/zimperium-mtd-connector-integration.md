---
title: 将 Zimperium MTD 与 Microsoft Intune 集成
titleSuffix: Microsoft Intune
description: 如何设置 Zimperium Mobile Threat Defense (MTD) 解决方案与 Microsoft Intune 的集成，以控制移动设备对公司资源的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3eb18c45f81e427f1d14ce77086e0d7684994e82
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884165"
---
# <a name="integrate-zimperium-with-intune"></a>将 Zimperium 与 Intune 集成

若要将 Zimperium 移动威胁防御解决方案与 Intune 集成，请完成以下步骤。

## <a name="before-you-begin"></a>在开始之前

> [!NOTE]
> 以下步骤是在 [Zimperium MTD 控制台](https://www.zimperium.com/platform)中完成。

开始将 Zimperium 与 Intune 集成之前，请确保具有以下订阅和凭据：

- Microsoft Intune 订阅

- 授予下列权限的 Azure Active Directory 全局管理员管理凭据：

  - 登录和读取用户配置文件

  - 使用已登录用户的身份访问目录

  - 读取目录数据

  - 向 Intune 发送设备信息

- 用于访问 Zimperium MTD 控制台的管理员凭据。

### <a name="zimperium-app-authorization"></a>Zimperium 应用授权

Zimperium 应用授权流程如下：

- 授权 Zimperium 服务将与设备运行状况状态相关的信息传输回 Intune。 必须使用全局管理员凭据，才能授予这些权限。 权限授予是一次性操作。 在权限被授予后，无需使用全局管理员凭据，即可执行日常操作。

- 同步 Zimperium 与 Azure Active Directory (AD) 注册组成员身份，以填充其设备的数据库。

- 允许 Zimperium 管理控制台使用 Azure AD 单一登录 (SSO)。

- 允许 Zimperium 应用使用 Azure AD SSO 登录。

若要详细了解许可和 Azure Active Directory 申请，请参阅 Azure Active Directory 文章 *Azure Active Directory v2.0 终结点中的权限和许可*中的[向目录管理员请求权限](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin)。


## <a name="to-set-up-zimperium-integration"></a>设置 Zimperium 集成

1. 转到 [Zimperium MTD 控制台](https://www.zimperium.com/platform)使用你的凭据登录。 必须以具有全局管理员角色的 Azure Active Directory 用户身份登录，才能执行 Zimperium 集成设置过程。 此一次性设置操作使用全局管理员权限，在组织中授权 Zimperium 应用与 Intune 进行通信。 

2. 从左侧菜单中选择“管理”  。

3. 选择“MDM 设置”  选项卡。

4. 选择“添加 MDM”，然后从“MDM 提供商”列表中选择“Microsoft Intune”    。

5. 将 Microsoft Intune 设置为 MDM 服务后，将弹出“Microsoft Intune 配置”窗口，在其中为以下每个选项选择“添加 Azure Active Directory”   ： **“Zimperium zConsole”** 、 **“zIPS iOS 和 Android 应用”** ，以授权 Zimperium 通过 Azure AD 单一登录与 Intune 和 Azure AD 进行通信。

    > [!IMPORTANT]  
    > 必须添加 Zimperium zConsole、zIPS iOS 和 Android 应用，才能完成与 Intune 集成的过程。

6. 选择“接受”，授权 Zimperium 应用与 Intune 和 Azure Active Directory 通信  。

7. 将 Zimperium zConsole  以及 zIPS iOS 和 Android  应用添加到 Azure AD 后，添加 Azure AD 安全组。 此添加允许 Zimperium 将 Azure AD 安全组与其服务同步。

8. 选择“完成”  ，保存配置并启动首次 Azure AD 安全组同步。

9. 注销 Zimperium MTD 控制台。

## <a name="next-steps"></a>后续步骤

- [设置 Zimperium 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
