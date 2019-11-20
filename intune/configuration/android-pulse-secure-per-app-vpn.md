---
title: 自定义 Android 适用的每应用 VPN 配置文件
titleSuffix: Microsoft Intune
description: 了解如何为 Microsoft Intune 托管的 Android 设备创建每应用 VPN 配置文件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3683d2aeada791c6ec827e915e02365a336e6045
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059674"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>使用 Microsoft Intune 自定义配置文件为 Android 设备创建每应用 VPN 配置文件

[!INCLUDE[azure_portal](../includes/azure_portal.md)]

可为由 Intune 管理的 Android 5.0 及更高版本设备创建每应用 VPN 配置文件。 首先，创建使用 Pulse Secure 或 Citrix 连接类型的 VPN 配置文件。 然后，创建将 VPN 配置文件与特定应用关联的自定义配置策略。

将策略分配给 Android 设备或用户组后，用户应启动 Pulse Secure 或 Citrix VPN 客户端。 然后，VPN 客户端将仅允许来自指定应用的通信使用打开的 VPN 连接。

> [!NOTE]
>
> 此配置文件仅支持 Pulse Secure 和 Citrix 连接类型。

## <a name="step-1-create-a-vpn-profile"></a>步骤 1：创建 VPN 配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入配置文件的描述性名称。 为配置文件命名，以便稍后可以轻松地识别它们。 例如，配置文件名称最好是“整个公司的 Android 每应用 VPN 配置文件”  。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Android”  。
    - **配置文件类型**：选择“VPN”  。

4. 选择“设置”   > “配置”  ，然后按照[如何配置 VPN 设置](vpn-settings-configure.md)和[适用于 Android 设备的 Intune VPN 设置](vpn-settings-android.md)中的设置配置 VPN 配置文件。

记录创建 VPN 配置文件时指定的“连接名称”  值。 在下一步中将会用到此名称。 例如**MyAppVpnProfile**。

## <a name="step-2-create-a-custom-configuration-policy"></a>步骤 2：创建自定义配置策略

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入自定义配置文件的描述性名称。 为配置文件命名，以便稍后可以轻松地识别它们。 例如，配置文件名称最好是“整个公司的自定义 OMA-URI Android VPN 配置文件”  。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Android”  。
    - **配置文件类型**：选择“自定义”  。

4. 选择“设置”   > “配置”  。
5. 在“自定义 OMA-URI 设置”  窗格上，选择“添加”  。
    - **名称**：输入设置的名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **OMA-URI**：输入 `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`，其中“Name”  是在步骤 1 中记下的连接名称。 在此示例中，字符串是 `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`。
    - **数据类型**：输入“String”  。
    - **值**：输入与配置文件相关联的包列表，其中此列表以分号进行分隔。 例如，如果你希望 Excel 和 Google Chrome 浏览器使用 VPN 连接，输入 `com.microsoft.office.excel;com.android.chrome`。

![Android per-app VPN 自定义策略示例](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>将应用列表设置为方块列表或允许列表（可选）

通过使用“BLACKLIST”  值，可输入将不能  使用 VPN 连接的应用列表。 所有其他应用将通过 VPN 连接。 或者，你可使用“WHITELIST”  值来输入可以  使用 VPN 连接的应用列表。 不在列表中的应用不会通过 VPN 连接。

1. 在“自定义 OMA-URI 设置”  窗格上，选择“添加”  。
2. 输入设置名称。
3. 在“OMA-URI”  中，输入 `./Vendor/MSFT/VPN/Profile/*Name*/Mode`，其中“Name”  是在步骤 1 中记下的 VPN 配置文件名称。 在此示例中，字符串是 `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`
4. 在“数据类型”  中，输入“String”  。
5. 在**值**中，输入**黑名单**或**白名单**。

## <a name="step-3-assign-both-policies"></a>步骤 3：分配这两个策略

向所需用户或设备[分配两个设备配置文件](device-profile-assign.md)。
