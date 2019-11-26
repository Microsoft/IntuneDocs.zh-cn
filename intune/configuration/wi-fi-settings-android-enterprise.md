---
title: 适用于 Android Enterprise 和展台设备的 Wi-Fi 设置 - Microsoft Intune | Microsoft Docs
description: 为 Android Enterprise 和 Android 展台创建或添加 WiFi 设备配置文件。 请参阅不同的设置，包括添加证书、选择 EAP 类型以及在 Microsoft Intune 中选择身份验证方法。 对于展台设备，还要输入网络的预共享密码。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04d35f49f9e07cb72a1fea92210b05e0a95ec256
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390813"
---
# <a name="add-wi-fi-settings-for-android-enterprise-dedicated-and-fully-managed-devices-in-microsoft-intune"></a>在 Microsoft Intune 中为 Android Enterprise 专用和完全托管设备添加 Wi-fi 设置

可以使用特定的 Wi-Fi 设置创建配置文件，然后将此配置文件部署到 Android Enterprise 完全托管和专用的设备。 Microsoft Intune 提供多种功能，包括对网络进行身份验证，使用预共享密钥等。

本文将说明这些设置。 [在设备上使用 Wi-Fi](wi-fi-settings-configure.md) 详细介绍了 Microsoft Intune 中的 Wi-Fi 功能。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](wi-fi-settings-configure.md#create-a-device-profile)。

## <a name="device-owner-only"></a>仅设备所有者

如果要部署到 Android 企业专用或完全托管设备，请选择此选项。  Android 企业专用和完全托管设备目前支持 SCEP 证书部署，但不支持 PKCS。

### <a name="basic"></a>基本

- Wi-Fi 类型  ：选择“基本”  。
- 网络名称  ：输入此 Wi-Fi 连接的名称。 最终用户在浏览其设备的可用 Wi-FI 连接时将看到此名称。 例如，输入 Contoso WiFi  。
- **SSID**：输入**服务集标识符**，它是设备连接到的无线网络的真实名称。 但是，用户在选择连接时只会看到你已配置的网络名称  。
- 隐藏网络  ：选择“启用”  以在设备上的可用网络列表中隐藏此网络。 不广播 SSID。 选择“禁用”  以在设备上的可用网络列表中显示此网络。
- Wi-Fi 类型  ：选择要用于对 Wi-Fi 网络进行身份验证的安全协议。 选项包括：

  - 开放(无身份验证)：仅在网络未受保护的情况下使用此选项  。
  - WEP- 预共享密钥  ：在预共享密钥中输入此密码  。 设置或配置组织的网络后，还要配置密码或网络密钥。 输入此密码或网络密钥作为 PSK 值。
  - WPA 预共享密钥  ：在预共享密钥中输入此密码  。 设置或配置组织的网络后，还要配置密码或网络密钥。 输入此密码或网络密钥作为 PSK 值。

### <a name="enterprise"></a>企业

- Wi-Fi 类型  ：选择“企业”  。
- **SSID**：输入**服务集标识符**，它是设备连接到的无线网络的真实名称。 但是，用户在选择连接时只会看到你已配置的网络名称  。
- 隐藏网络  ：选择“启用”  以在设备上的可用网络列表中隐藏此网络。 不广播 SSID。 选择“禁用”  以在设备上的可用网络列表中显示此网络。
- EAP 类型  ：选择用于对安全无线连接进行身份验证的可扩展身份验证协议 (EAP) 类型。 选项包括：

  - EAP-TLS  ：此外请输入：

    - 服务器信任   - 用于服务器验证的根证书  ：选择现有的受信任根证书配置文件。 当客户端连接到网络时，此证书向服务器显示，并对连接进行身份验证。

    - **客户端身份验证** - **用于客户端身份验证的客户端证书（标识证书）** ：选择同时被部署到设备的 SCEP 客户端证书配置文件。 此证书是由设备呈现给服务器以用于对连接进行身份验证的标识。

    - 标识隐私（外部标识）  ：输入为响应 EAP 标识请求而发送的文本。 此文本可以是任何值，例如 `anonymous`。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。

  - EAP-TTLS  ：此外请输入：

    - 服务器信任   - 用于服务器验证的根证书  ：选择现有的受信任根证书配置文件。 当客户端连接到网络时，此证书向服务器显示，并对连接进行身份验证。

    - **客户端身份验证**：选择一种身份验证方法  。 选项包括：

      - 用户名和密码  ：提示用户输入用户名和密码以对连接进行身份验证。 此外请输入：
        - 非 EAP 方法（内部标识）  ：选择验证连接的方式。 请确保选择在你的 Wi-Fi 网络上配置同一协议。 选项包括：

          - **未加密的密码 (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP 版本 2 (MS-CHAP v2)**

      - **证书**：选择同时被部署到设备的 SCEP 客户端证书配置文件。 此证书是由设备呈现给服务器以用于对连接进行身份验证的标识。

      - 标识隐私（外部标识）  ：输入为响应 EAP 标识请求而发送的文本。 此文本可以是任何值，例如 `anonymous`。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。

  - PEAP  ：此外请输入：

    - 服务器信任   - 用于服务器验证的根证书  ：选择现有的受信任根证书配置文件。 当客户端连接到网络时，此证书向服务器显示，并对连接进行身份验证。

    - **客户端身份验证**：选择一种身份验证方法  。 选项包括：

      - 用户名和密码  ：提示用户输入用户名和密码以对连接进行身份验证。 此外请输入：
        - 用于进行身份验证的非 EAP 方法（内部标识）  ：选择验证连接的方式。 请确保选择在你的 Wi-Fi 网络上配置同一协议。 选项包括：

          - **无**
          - **Microsoft CHAP 版本 2 (MS-CHAP v2)**

      - **证书**：选择同时被部署到设备的 SCEP 客户端证书配置文件。 此证书是由设备呈现给服务器以用于对连接进行身份验证的标识。

      - 标识隐私（外部标识）  ：输入为响应 EAP 标识请求而发送的文本。 此文本可以是任何值，例如 `anonymous`。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。

## <a name="work-profile-only"></a>仅工作配置文件

### <a name="basic"></a>基本

- Wi-Fi 类型  ：选择“基本”  。
- **SSID**：输入**服务集标识符**，它是设备连接到的无线网络的真实名称。 但是，用户在选择连接时只会看到你已配置的网络名称  。
- 隐藏网络  ：选择“启用”  以在设备上的可用网络列表中隐藏此网络。 不广播 SSID。 选择“禁用”  以在设备上的可用网络列表中显示此网络。

### <a name="enterprise"></a>企业

- Wi-Fi 类型  ：选择“企业”  。
- **SSID**：输入**服务集标识符**，它是设备连接到的无线网络的真实名称。 但是，用户在选择连接时只会看到你已配置的网络名称  。
- 隐藏网络  ：选择“启用”  以在设备上的可用网络列表中隐藏此网络。 不广播 SSID。 选择“禁用”  以在设备上的可用网络列表中显示此网络。
- EAP 类型  ：选择用于对安全无线连接进行身份验证的可扩展身份验证协议 (EAP) 类型。 选项包括：

  - EAP-TLS  ：此外请输入：

    - 服务器信任   - 用于服务器验证的根证书  ：选择现有的受信任根证书配置文件。 当客户端连接到网络时，此证书向服务器显示，并对连接进行身份验证。

    - 客户端身份验证   - 用于客户端身份验证的客户端证书（标识证书）  ：选择同时被部署到设备的 SCEP 或 PKCS 客户端证书配置文件。 此证书是由设备呈现给服务器以用于对连接进行身份验证的标识。

    - 标识隐私（外部标识）  ：输入为响应 EAP 标识请求而发送的文本。 此文本可以是任何值，例如 `anonymous`。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。

  - EAP-TTLS  ：此外请输入：

    - 服务器信任   - 用于服务器验证的根证书  ：选择现有的受信任根证书配置文件。 当客户端连接到网络时，此证书向服务器显示，并对连接进行身份验证。

    - **客户端身份验证**：选择一种身份验证方法  。 选项包括：

      - 用户名和密码  ：提示用户输入用户名和密码以对连接进行身份验证。 此外请输入：
        - 非 EAP 方法（内部标识）  ：选择验证连接的方式。 请确保选择在你的 Wi-Fi 网络上配置同一协议。 选项包括：

          - **未加密的密码 (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP 版本 2 (MS-CHAP v2)**

      - 证书  ：选择同时被部署到设备的 SCEP 或 PKCS 客户端证书配置文件。 此证书是由设备呈现给服务器以用于对连接进行身份验证的标识。

      - 标识隐私（外部标识）  ：输入为响应 EAP 标识请求而发送的文本。 此文本可以是任何值，例如 `anonymous`。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。

  - PEAP  ：此外请输入：

    - 服务器信任   - 用于服务器验证的根证书  ：选择现有的受信任根证书配置文件。 当客户端连接到网络时，此证书向服务器显示，并对连接进行身份验证。

    - **客户端身份验证**：选择一种身份验证方法  。 选项包括：

      - 用户名和密码  ：提示用户输入用户名和密码以对连接进行身份验证。 此外请输入：
        - 用于进行身份验证的非 EAP 方法（内部标识）  ：选择验证连接的方式。 请确保选择在你的 Wi-Fi 网络上配置同一协议。 选项包括：

          - **无**
          - **Microsoft CHAP 版本 2 (MS-CHAP v2)**

      - 证书  ：选择同时被部署到设备的 SCEP 或 PKCS 客户端证书配置文件。 此证书是由设备呈现给服务器以用于对连接进行身份验证的标识。

      - 标识隐私（外部标识）  ：输入为响应 EAP 标识请求而发送的文本。 此文本可以是任何值，例如 `anonymous`。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但未执行任何操作。 下一步是[分配此配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。

此外，还可以为 [Android](wi-fi-settings-android.md)、[iOS](wi-fi-settings-ios.md)、[macOS](wi-fi-settings-macos.md)、[Windows 10](wi-fi-settings-windows.md) 和 [Windows 8.1](wi-fi-settings-import-windows-8-1.md) 创建 Wi-Fi 配置文件。
