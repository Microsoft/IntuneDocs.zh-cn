---
title: Microsoft Intune 中适用于 Windows 10 设备的 Wi-Fi 设置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 中适用于 Windows 10 及更高版本设备的 Wi-Fi 设置添加或创建 Wi-Fi 配置文件。 可以配置基本设置或企业级设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f6532c63612b806f9824f5b9ca98f1ebbbc943f
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321604"
---
## <a name="wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Intune 中适用于 Windows 10 及更高版本设备的 Wi-Fi 设置

Wi-Fi 设置在适用于运行 Windows 10 及更高版本的设备的配置文件中使用。 您的选择包括：

- 基本
- 企业

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](device-profile-create.md)。

## <a name="settings-for-basic-and-enterprise-profiles"></a>适用于基本和企业配置文件的设置

- Wi-Fi 名称 (SSID)：服务设置标识符的英文缩写。 该值是设备连接到的无线网络的真实名称。 但用户在选择连接时只会看到你配置的连接名称。
- 连接名称：输入此 Wi-Fi 连接的用户友好名称。 你输入的文本是用户在浏览其设备上的可用连接时看到的名称。
- 在范围内时自动连接：当为“是”时，设备在此网络范围内时自动连接。 当为“否”时，设备不会自动连接。
  - 如果可用，则连接到更适合的网络：如果设备位于更适合的网络范围内，则选择“是”可使用首选网络。 选择“否”则使用此配置文件中的 Wi-Fi 网络。

    例如，创建“ContosoCorp”Wi-Fi 网络，然后使用此配置文件中的“ContosoCorp”。 还可以在范围内创建“ContosoGuest”Wi-Fi 网络。 当公司设备在范围内时，你希望它们自动连接到“ContosoCorp”。 在此方案中，将“如果可用，连接到更适合的网络”属性设置为“否”。

  - 连接到此网络，即使它未广播其 SSID：选择“是”，则配置文件可自动连接到网络，即使网络处于隐藏状态（即未公开广播其 SSID）。 如果不希望此配置文件连接到隐藏网络，请选择“否”。

- 公司代理设置：选择使用组织内的代理设置。 选项包括：
  - 无：不配置任何代理设置。
  - 手动配置：输入“代理服务器 IP 地址”及其“端口号”。
  - 自动配置：输入指向代理自动配置 (PAC) 脚本的 URL。 例如，输入 `http://proxy.contoso.com/proxy.pac`。

## <a name="settings-for-basic-profiles-only"></a>仅适用于基本配置文件的设置

- 无线安全类型：输入用于对网络上的设备进行身份验证的安全协议。 你的选项为：
  - 开放(无身份验证)：仅在网络未受保护的情况下使用此选项。
  - WPA/WPA2-Personal

## <a name="settings-for-enterprise-profiles-only"></a>仅适用于企业配置文件的设置

- 单一登录 (SSO)：允许配置单一登录 (SSO)，其中凭据共享，以用于计算机和 Wi-Fi 网络登录。 你的选项为：
  - 禁用：禁用 SSO 行为。 用户需要单独向网络进行身份验证。
  - 在用户登录到设备之前启用：在用户登录过程之前使用 SSO 对网络进行身份验证。
  - 在用户登录到设备后启用：在用户登录过程完成后立即使用 SSO 对网络进行身份验证。
  - 身份验证超时前等待的最长时间：输入在对网络进行身份验证之前，可以等待的最长秒数，范围为 1-120 秒。
  - 允许 Windows 提示用户提供其他身份验证凭据：选择“是”，则允许 Windows 系统提示用户在身份验证方法需要时提供其他凭据。 选择“否”，则隐藏这些提示。

- 启用成对主密钥 (PMK) 缓存：选择“是”，则缓存身份验证中使用的 PMK。 此缓存通常可以加快完成对网络的身份验证。 选择“否”，则在每次连接到 Wi-Fi 网络时强制进行身份验证握手。

  - PMK 存储在缓存中的最长时间：输入成对主密钥 (PMK) 在缓存中存储的分钟数，范围为 5-1440 分钟。
  - 缓存中存储的最大 PMK 数：输入缓存中存储的密钥数，范围为 1-255 个。

- 启用预身份验证：预身份验证允许配置文件在连接之前对配置文件中网络的所有访问点进行身份验证。 在接入点之间移动时，预身份验证可以加快重新连接用户或设备的速度。 选择“是”，则配置文件对范围内此网络中的所有接入点进行身份验证。 选择“否”，则要求用户或设备对每个接入点单独进行身份验证。

  - 最大预身份验证尝试次数：输入预身份验证的尝试次数，范围为 1-16 次。

- EAP 类型：选择用于对安全无线连接进行身份验证的可扩展身份验证协议 (EAP) 类型。 选项包括：

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **受保护的 EAP** (PEAP)

### <a name="more-options-when-you-choose-the-eap-type"></a>选择 EAP 类型时的更多选项

> [!NOTE]
> 目前，使用 EAP 类型时仅支持 SCEP 证书配置文件。 不支持 PKCS 证书配置文件。 每当用户需要输入证书时，请务必选择 SCEP 证书。

#### <a name="server-trust"></a>服务器信任

|设置名|更多信息|使用时间|
|--------------|-------------|----------|
|**证书服务器名称**|输入由受信任的证书颁发机构 (CA) 颁发的证书中使用的一个或多个常用名称。 如果输入此信息，则可在用户设备连接到此 Wi-Fi 网络时，绕过该设备上显示的动态信任对话框。|EAP 类型为 **EAP-TLS**、**EAP-TTLS** 或 **PEAP**|
|**用于服务器验证的根证书**|选择用于对连接进行身份验证的受信任的根证书配置文件。 |EAP 类型为 **EAP-TLS**、**EAP-TTLS** 或 **PEAP**|
|**标识隐私（外部标识）**|请输入为响应 EAP 标识请求而发送的文本。 此文本可以是任何值。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。|EAP 类型为 **PEAP**|

#### <a name="client-authentication"></a>客户端身份验证

| 设置名 | 更多信息 | 使用时间 |
|---|---|---|
| **用于客户端身份验证的客户端证书（身份证书）** |  选择用于对连接进行身份验证的 SCEP 证书配置文件。 | EAP 类型为 **EAP-TLS** |
| **身份验证方法** | 选择连接的身份验证方法：<br><br>- 证书：选择要作为标识证书提交给服务器的 SCEP 客户端证书。<br><br>- 用户名和密码：输入用于身份验证的“非 EAP 方法（内部标识）”方法。 选项包括：<br><br>- **未加密的密码 (PAP)**<br>- 质询握手 (CHAP)<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP 版本 2 (MS-CHAP v2)**<br><br>- 标识隐私（外部标识）：输入为响应 EAP 标识请求而发送的文本。 此文本可以是任何值。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。 | EAP 类型为 EAP-TTLS |

## <a name="use-an-imported-settings-file"></a>使用已导入的设置文件

对于 Intune 中不可用的任何设置，可以从其他 Windows 设备导出 Wi-Fi 设置。 此导出会创建包含所有设置的 XML 文件。 然后，将此文件导入 Intune，并将其用作 Wi-Fi 配置文件。 请参阅[导出和导入 Windows 设备的 Wi-Fi 设置](wi-fi-settings-import-windows-8-1.md)。

## <a name="next-steps"></a>后续步骤
[在 Intune 中配置 Wi-Fi 设置](wi-fi-settings-configure.md)
