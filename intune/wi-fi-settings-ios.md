---
title: "适用于 iOS 设备的 Intune Wi-Fi 设置"
titleSuffix: Intune on Azure
description: "了解可用于配置 iOS 设备上 Wi-Fi 连接的 Intune 设置。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89229a5e-3421-4221-a62f-fa800620cc0d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 001a65733d3565df8f4aea485c5a7488f2756a88
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 iOS 设备的 Wi-Fi 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]



## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>适用于基本配置文件和企业配置文件的 Wi-Fi 设置

- **网络名称** - 输入此 Wi-Fi 连接的名称。 用户浏览设备上的可用连接列表时，将看到该名称。
- **SSID** - 服务设置标识符的英文缩写。 这是设备将连接到的无线网络的真实名称。 但是，用户在选择连接时只会看到上面创建的网络名称。
- **自动连接** - 只要设备处于此网络的范围内，即进行连接。
- **隐藏网络** - 阻止此网络显示在设备上的可用网络列表中。
- **代理设置** - 从以下选项中选择：
    - **无** - 不配置任何代理设置。
    - **手动** - 输入**代理服务器地址**（作为 IP 地址）和关联的**端口号**。
    - **自动** - 使用文件配置代理服务器。 输入包含配置文件的**代理服务器 URL**（例如 **http://proxy.contoso.com**）。

## <a name="wi-fi-settings-for-basic-profiles-only"></a>仅适用于基本配置文件的 Wi-Fi 设置

- **安全类型** - 选择要用于对 Wi-Fi 网络进行身份验证的安全协议：
    - **开放(无身份验证)** - 仅在网络未受保护的情况下使用此选项。
    - **WPA/WPA2 - 个人版**
    - **WEP**

## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>仅适用于企业配置文件的 Wi-Fi 设置

- **EAP 类型** - 从以下项中选择用于对安全无线连接进行身份验证的可扩展身份验证协议 (EAP) 类型：
    - **EAP-FAST**
    - **EAP-SIM**
    - **EAP-TLS**
    - **EAP-TTLS**
    - **LEAP**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>选择 EAP 类型时的其他选项


|设置名|更多信息|使用时间|
|--------------|-------------|----------|
|**受保护的访问凭据 (PAC) 设置**|选择以使用受保护的访问凭证来建立客户端和身份验证服务器之间经过身份验证的隧道。 选择下列选项之一：<br>- **使用 PAC** - 如果存在现有的 PAC 文件，则使用它。<br>- **使用和配置 PAC** - 向设备配置 PAC 文件。<br>- **以匿名方式使用和配置 PAC** - 向设备配置 PAC 文件，并确保在不进行服务器身份验证的情况下配置 PAC 文件。|EAP 类型为 **EAP-FAST**|

#### <a name="server-trust"></a>服务器信任


|设置名|更多信息|使用时间|
|--------------|-------------|----------|
|**证书服务器名称**|指定由受信任的证书颁发机构 (CA) 颁发的证书中使用的一个或多个常用名称。 如果提供此信息，则可以在最终用户设备连接到此 Wi-Fi 网络时，绕过显示在设备上的动态信任对话框。|EAP 类型为 **EAP-TLS**、**EAP-TTLS** 或 **PEAP**。|
|**用于服务器验证的根证书**|选择用于对连接进行身份验证的受信任的根证书配置文件。 |EAP 类型为 **EAP-TLS**、**EAP-TTLS** 或 **PEAP**|
|**标识隐私（外部标识）**|请指定为响应 EAP 标识请求而发送的文本。 此文本可以是任何值。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。|EAP 类型为 **PEAP**|


#### <a name="client-authentication"></a>客户端身份验证


|设置名|更多信息|使用时间|
|--------------|-------------|----------|
|**用于客户端身份验证的客户端证书（身份证书）**|选择用于对连接进行身份验证的 SCEP 或 PKCS 证书配置文件。|EAP 类型为 **EAP-TLS**|
|**身份验证方法**|选择连接的身份验证方法：<br>- **证书** 选择要作为标识证书提交给服务器的 SCEP 或 PKCS 客户端证书。<br><br>- **用户名和密码** 可指定进行身份验证的其他方法。 <br><br>如果选择了“用户名和密码”，请配置：<br><br>-  **非 EAP 方法（内部标识）**，然后从以下项选择对连接进行身份验证的方式：<br>- **无**<br>- **未加密的密码 (PAP)**<br>- **质询握手身份验证协议 (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP 版本 2 (MS-CHAP v2)**<br>可用的选项取决于你选择的 EAP 类型。<br><br>**和**<br><br>- **标识隐私（外部标识）** - 指定为响应 EAP 标识请求而发送的文本。 此文本可以是任何值。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。|EAP 类型为 **EAP-TTLS** 或 *
