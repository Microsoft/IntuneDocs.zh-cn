---
title: "适用于 Android - Pulse Secure 的每应用 VPN 配置文件"
titleSuffix: Intune on Azure
description: "了解如何为 Intune 托管的 Android 设备创建每应用 VPN 配置文件。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0e3a8363eb25ba3a3b2c16f15b8188acb694938
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>使用 Microsoft Intune 自定义配置文件为 Android 设备创建每应用 VPN 配置文件

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可为由 Intune 管理的 Android 5.0 及更高版本设备创建每应用 VPN 配置文件。 首先，创建使用 Pulse Secure 连接类型的 VPN 配置文件。 然后，创建将 VPN 配置文件与特定应用关联的自定义配置策略。

将策略分配到 Android 设备或用户组后，用户应启动 PulseSecure VPN。 然后，PulseSecure 将仅允许来自指定应用的通信使用打开的 VPN 连接。

> [!NOTE]
>
> 此配置文件仅支持 Pulse Secure 连接类型。


## <a name="step-1-create-a-vpn-profile"></a>步骤 1：创建 VPN 配置文件


1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
2. 在配置文件列表边栏选项卡中，选择“创建配置文件”。
3. 在“创建配置文件”边栏选项卡上，输入 VPN 配置文件的“名称”和可选“说明”。
4. 从“平台”下拉列表中，选择“Android”。
5. 在“配置文件类型”下拉列表中，选择“VPN”。
3. 选择“设置”  > “配置”，然后按照[如何配置 VPN 设置](vpn-settings-configure.md)和[适用于 Android 设备的 Intune VPN 设置](vpn-settings-android.md)中的设置配置 VPN 配置文件。

记录创建 VPN 配置文件时指定的“连接名称”值。 在下一步中将会用到此名称。 例如**MyAppVpnProfile**。

## <a name="step-2-create-a-custom-configuration-policy"></a>步骤 2：创建自定义配置策略

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在“配置文件”边栏选项卡上，单击“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入自定义配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择“Android”。
6. 从“配置文件类型”下拉列表中，选择“自定义”。
7. 选择“设置” > “配置”。
3. 在“自定义 OMA-URI 设置”边栏选项卡上，选择“添加”。
    - 输入设置名称。
    - 为“数据类型”，指定“字符串”。
    - 为 **OMA-URI** 指定以下字符串：**./Vendor/MSFT/VPN/Profile/*Name*/PackageList**，其中 *Name* 是步骤 1 中记下的 VPN 配置文件名称。 本示例中，字符串为 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**。
    - 对于**值**与配置文件相关联的包列表，其中此列表以分号进行分隔。 例如，如果你希望 Excel 和 Google Chrome 浏览器使用 VPN 连接，输入 **com.microsoft.office.excel;com.android.chrome**。

![Android per-app VPN 自定义策略示例](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>将应用列表设置为方块列表或允许列表（可选）
  通过使用**方块列表**值，可指定列表中的应用将*不能*使用 VPN 连接。 所有其他应用将通过 VPN 连接。
或者，你可使用 **WHITELIST** 值来指定*可以*使用 VPN 连接的应用列表。 不在列表中的应用不会通过 VPN 连接。
  1.    在“自定义 OMA-URI 设置”边栏选项卡上，选择“添加”。
  2.    输入设置名称。
  3.    为“数据类型”，指定“字符串”。
  4.    对于 **OMA-URI**，使用以下字符串：**./Vendor/MSFT/VPN/Profile/*Name*/Mode**，其中 *Name* 是步骤 1 中记下的 VPN 配置文件名称。 本示例中，字符串为**./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**。
  5.    对于**值**，输入 **BLACKLIST** 或 **WHITELIST**。



## <a name="step-3-assign-both-policies"></a>步骤 3：分配这两个策略

使用[如何分配设备配置文件](device-profile-assign.md)中的说明，将两个配置文件分配给所需用户或设备。
