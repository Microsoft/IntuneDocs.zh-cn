---
title: Intune 中的数据收集
titleSuffix: Microsoft Intune
description: 了解 Intune 中收集个人数据的方式。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd204271b9ae3e57e15a101647444913749f4109
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514228"
---
# <a name="data-collection-in-intune"></a>Intune 中的数据收集

用户使用 Intune 注册公司设备或个人设备时，Intune 会收集并共享一些个人数据。 Intune 从以下来源收集个人数据：

- 管理员在 Azure 门户中使用 Intune。
- 最终用户设备（他们注册 Intune 管理服务时以及使用过程中）。
- 第三方服务处的客户帐户（按每个管理员的说明）。
- 诊断、性能和使用情况信息。

Intune 从这些来源中收集到的信息可以分为以下三类：[标识数据](#identified-data)、[使用假名的数据](#pseudonymized-data)以及[聚合数据](#aggregated-data)。

> [!NOTE]
> 我们不会出于任何原因向任何第三方出售我们服务收集的任何数据。

## <a name="identified-data"></a>标识数据

Intune 收集的大部分个人数据都是标识数据。 此数据绑定至某个用户、设备或应用程序，对管理的性质来说至关重要。 标识数据用于管理用户的设备和应用程序，以及预配 Intune 服务。

Intune 收集的标识数据可能包括但不限于以下内容： 

- 用户信息
  - 显示的所有者名称/用户（由 Azure 用户 ID 标识的注册了 Azure 的用户名）
  - 用户主体名称或电子邮件地址
  - 第三方用户标识（例如 AppleID）
- 硬件清单信息
  - 设备名称
  - 制造商
  - 操作系统
  - 序列号
  - IMEI 编号
  - IP 地址
  - Wi-Fi MacAddress
  - ICCID
  - 电话号码
- 审核日志信息，包括以下活动的相关数据
  - 管理
  - 创建
  - 更新（编辑）
  - 删除
  - 分配
  - 远程任务
- 支持信息
  - 联系信息（姓名、电话号码和电子邮件地址）
  - 与 Microsoft 支持部门、产品和/或客户体验团队成员之间的电子邮件讨论
- 访问控制信息（Intune 使用此数据通过类似于[基于角色的访问控制](../fundamentals/role-based-access-control.md)的功能对管理角色和职能的访问权限进行管理）。
  - 静态验证器（客户密码）
  - 证书的隐私密钥 
- 管理员和帐户信息
  - 管理员用户的名字和姓氏
  - 管理员用户名
  - UPN（电子邮件）
  - 电话号码
  - 帐户所有者的电子邮件地址
  - 每个客户的 IT 管理员的 Active Directory ID
  - 客户帐单的付款数据
  - 订阅密钥
- 应用程序清单，例如
  - 应用名称
  - 版本
  - 应用 ID
  - 大小
  - 安装位置
  - 只有在由管理员标记为公司所有的设备或者开启了符合的应用功能时，才会收集应用程序清单数据。  
- 客户第三方租户 ID，例如 Apple ID。 

## <a name="pseudonymized-data"></a>使用假名的数据

使用假名的数据与唯一标识符相关联，通常是由系统生成的数字，只靠它无法识别个人，但是可用于向用户传递企业服务。 

Intune 收集的使用假名的数据可能包括但不限于以下内容： 

- 与用户和/或设备绑定的诊断、性能和使用情况数据
  - 某项功能的使用次数
  - 提供给该功能的命令
  - 服务的响应时间
  - 安装和其他进程的成功率
  - Intune 公司门户应用程序错误
  - 用户和设备标识符
  - 用于引用、关联和管理的标识符 
- 没有与设备或用户绑定的设备数据（如果此数据与某个设备或用户绑定，Intune 会将其视为标识数据）
  - Intune 设备 ID
  - Azure Active Directory 设备 ID
  - Intune 设备管理 ID
  - 租户 ID
  - 帐户 ID
  - EAS 设备 ID
  - 特定于平台的 ID
  - iOS/iPadOS 设备的 AppleID
  - Mac 设备的 Mac 地址
  - Windows 设备的 Windows ID
- 托管应用程序信息
  - 托管应用程序 ID
  - 托管应用程序设备标记
  - Intune 设备管理 ID
  - Azure Active Directory 设备 ID
  - 加密密钥

## <a name="aggregated-data"></a>聚合数据

聚合数据用于预配和改进 Intune 服务。 

Intune 收集的聚合数据可能包括但不限于以下内容： 

- 所有 Intune 租户中的管理员使用情况数据（例如，在与管理控制台进行交互时所选择的管理控件）
- 租户帐户信息（可从 Intune 边栏选项卡获得此数据）
  - 已注册的设备数或用户数
  - 已标识的设备平台数  
  - 已安装的设备数
  - installedDeviceCount：已安装该应用程序的设备数。
  - notApplicableDeviceCount：无法使用该应用程序的设备数。
  - notInstalledDeviceCount：可使用该应用程序但是尚未安装的设备数。
  - pendingInstallDeviceCount：可使用该应用程序但还在等待安装的设备数。

## <a name="next-steps"></a>后续步骤

详细了解 Intune [存储和处理](privacy-data-store-process.md)以及[共享](privacy-data-secure-share.md)个人数据的方式。 
