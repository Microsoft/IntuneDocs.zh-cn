---
title: 通过 Microsoft Intune 中的网络位置绑定 Android 设备 - Azure | Microsoft Docs
description: 在适用于 Android 设备的 Microsoft Intune 中创建或配置网络位置。 可以根据设备的网络位置将设备标记为不符合。 如果设备超出网络位置范围，则可以阻止其访问公司资源。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da29f4fcdbd694b2817bf4eca953c37d2d3c6b0e
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848179"
---
# <a name="use-locations-network-fence-in-intune"></a>使用 Intune 中的位置（网络围墙）

如果设备离开某个位置，则你可能希望阻止其访问公司网络。 Intune 中的“位置”功能提供了此功能。 

可以创建基于位置的网络符合性策略，也称为网络隔离。 该策略确保设备必须连接到工作网络才符合要求。 该策略可以与条件性访问策略一起使用，以便设备只有在连接到工作网络时才能访问工作资源。 当设备未连接到工作网络时，该设备变得不符合要求，失去对工作资源的访问权限。

请考虑以下情形：

在制造设施中，某些员工使用 Android 设备。 员工将 Android 设备带到设施或工厂外。 为防止未经授权的访问，可以执行以下操作：

1. 创建一个具有名为“生产车间”的 IPv4 范围的位置。
2. 创建要求这些设备连接到公司网络的合符合性策略，并分配此策略。
3. 如果设备超出制造工厂的范围，则该设备被认为不符合要求，并且无法访问公司资源。

此外，还可添加[针对非符合性的操作](#configure-the-actions-for-noncompliance)。 当设备回到本地并位于网络位置中时，它将重新重新获得公司资源的访问权限。

## <a name="prerequisites"></a>必备条件

要创建基于位置的符合性策略，请执行以下步骤：

- 创建一个网络位置，作为网关服务器、DHCP 服务器和/或设备连接的 DNS 服务器的 IPV4 网络范围
- 创建使用这些位置的符合性策略，并定义在设备不再连接到该网络位置时采取的操作
- Android 设备 6.0 及更高版本，并安装了最新的公司门户应用

## <a name="create-a-location"></a>创建位置

1. 在 Intune 中，选择“设备符合性” > “位置” > “创建”。

2. 输入以下属性：  

   - 必须的。 输入该位置的“名称”，例如“生产车间”或“第 44 号安全大楼”。
   - 可选。 使用 CIDR（无类别域际路由）表示法输入“IPv4 范围”，例如 `aaa.bbb.ccc.ddd/n`。
   - 可选。 输入“IPv4 网关”地址，例如 `aaa.bbb.ccc.ddd`。
   - 可选。 输入“IPv4 DHCP 服务器”地址，例如 `aaa.bbb.ccc.ddd`。
   - 可选。 输入“IPv4 DNS 服务器”地址列表。 此设置使用子集匹配。 如果设备上的 IPv4 DNS 服务器是已定义值的子集，则该设备会被视为“进入”围墙。 请务必在每行上输入一个地址，例如：  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - 可选。 输入“DNS 后缀”列表。 此设置使用子集匹配。 如果设备上的 DNS 后缀是已定义值的子集，则该设备将被视为“进入”围墙。 请务必在每行上输入一个域名，例如：  
     `contoso.com`  
     `contoso.org`

3. 单击“保存”以保存更改。

## <a name="create-the-location-compliance-policy"></a>创建位置符合性策略

在创建符合性策略时，请对“平台”选择“Android”。 在“位置”中，可以选择一个或多个已添加的网络位置。 这些位置是你为设备创建的网络围墙的一部分。

[创建基于网络位置的符合性策略](compliance-policy-create-android.md#locations)提供了一些指导。

## <a name="configure-the-actions-for-noncompliance"></a>配置针对非符合性的操作

创建符合性策略后，会对设备应用针对非符合性的默认操作。 可以添加更多操作。 例如，添加一项操作，当设备不再符合位置时，向用户发送电子邮件。

[添加针对非符合性的操作](actions-for-noncompliance.md)一文提供了一些指导。

## <a name="company-portal-app"></a>公司门户应用

当设备连接到你的位置时，该设备会在公司门户应用中显示为符合。 当设备未连接到你的某个位置时，该设备会显示为不符合。

## <a name="next-steps"></a>后续步骤
[监视设备符合性策略](compliance-policy-monitor.md)  
[设备符合性策略入门](device-compliance-get-started.md)
