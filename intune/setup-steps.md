---
title: 设置 Microsoft Intune
description: 开始使用 Intune 订阅的要求和先决条件
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 89a03bde6ecdfb031f7beaad407cd713ebc6f03e
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848885"
---
# <a name="set-up-intune"></a>设置 Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

以下设置步骤有助于使用 Intune 实现移动设备管理 (MDM)。 必须先执行设备管理，然后才能授予用户对公司资源的访问权限或管理设备上的设置。

某些步骤（例如设置 Intune 订阅和设置 MDM 机构）是在多数情况下都需要执行的。 其他步骤（例如配置自定义域或添加应用）是可选步骤，具体取决于公司需要。

如果当前正在使用 Microsoft System Center Configuration Manager 管理计算机和服务器，则可以[使用共同管理云连接 Configuration Manager](https://docs.microsoft.com/sccm/comanage/overview)。

>[!TIP]
>在符合条件的计划中，如果购买的 Intune 许可证达到 150 个，就可以使用 *FastTrack 中心权益*。 通过此服务，Microsoft 专家将协助用户针对 Intune 做好环境准备。 请参阅 [FastTrack 企业移动性 + 安全性 (EMS) 中心权益](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program)。



| 步骤 |                                                                                                                       状态                                                                                                                       |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   1   |                                        [支持的配置](supported-devices-browsers.md) - 在准备阶段需要了解的信息。 包括支持的配置和网络要求。                                         |
|   2   |                                                                 [登录 Intune](account-sign-up.md) - 登录试用订阅或创建新的 Intune 订阅。                                                                  |
|   3   |                [配置域名](custom-domain-name-configure.md) - 设置 DNS 注册，以将公司域名与 Intune 连接。 此操作可在连接 Intune 和使用资源时为用户提供熟悉的域。                |
|   4   |                                   [添加用户](users-add.md) - 手动添加用户或连接 Active Directory 以将用户与 Intune 同步。 除非设备是“无用户”网亭设备，否则必须执行此操作。                                    |
|   5   |                                            [分配许可证](licenses-assign.md) - 向用户授予使用 Intune 的权限。 所有用户设备和无用户设备都需要 Intune 许可证才能访问服务。                                             |
|   6   |                                               [添加组](groups-add.md) - 使用用户和设备组以简化管理任务。 使用组来分配应用、设置和其他资源。                                                |
|   7   |                                                                        [添加应用](apps-add.md) - 可以将应用分配给组，并可自动或选择性地安装应用。                                                                         |
|   8   | [配置设备](device-profiles.md) - 设置用于管理设备设置的配置文件。 设备配置文件可预配置电子邮件、VPN、Wi-Fi 和设备功能的设置。 它们还可对设备进行限制，以帮助同时保护设备和数据。 |
|   9   |       [自定义公司门户](company-portal-app.md) - 自定义用户在注册设备和安装应用时使用的 Intune 公司门户。 公司门户应用中和 Intune 公司门户网站上均显示这些设置。       |
|  10   |                                [启用设备注册](mdm-authority-set.md) - 通过设置 MDM 机构并启用特定平台实现对 iOS、Windows、Android 和 Mac 设备的 Intune 管理。                                 |
|  11   |                                                        [配置应用策略](app-protection-policy.md) - 基于 Microsoft Intune 中的应用保护策略提供特定设置。                                                         |

