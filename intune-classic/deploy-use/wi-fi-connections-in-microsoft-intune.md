---
title: "Wi-Fi 连接"
description: "使用 Wi-Fi 配置文件来帮助用户连接到 Wi-Fi 网络。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99ac426d2210aa22a7c0151aea59e14b848bbe1f
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2017
---
# <a name="configure-devices-to-connect-to-your-corporate-wi-fi-networks"></a>配置设备以连接到公司 Wi-Fi 网络

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune Wi-Fi 配置文件将无线网络设置部署到组织中的用户和设备。 部署 Wi-Fi 配置文件时，你的用户有权访问你公司的 Wi-Fi，而无需自行配置。

例如，安装名为 **Contoso Wi-Fi** 的新 Wi-Fi 网络，并且想要将所有 iOS 设备设置为连接到此网络。 过程如下：

![Wi-Fi 配置文件过程摘要](..\media\wi-fi-process-diagram.png)

1.   创建包含连接到 **Contoso Wi-Fi** 无线网络所必需的设置的 Wi-Fi 配置文件。

2.   使用 iOS 设备将配置文件部署到用户组。

3.   用户在无线网络列表中找到新的“Contoso Wi-Fi”网络，然后即可轻松连接到此网络。


## <a name="create-a-wi-fi-profile"></a>创建 Wi-fi 配置文件

你可以将 Wi-Fi 配置文件部署到以下平台：

-   Android 4.0 及更高版本

-   Android for Work   

-   iOS 8.0 及更高版本

-   Mac OS X 10.9 及更高版本

对于运行 Windows 8.1 或 Windows 10 桌面版或移动版操作系统的设备，可以导入之前导出到文件的 Wi-Fi 配置文件。 有关详细信息，请参阅[导出或导入 Wi-Fi 配置的配置文件（适用于 Windows 设备）](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices)。

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“策略”&gt;“添加策略”。

2.  选择以下策略类型之一，然后选择“创建策略”：

    -   Wi-fi 配置文件（Android 4 及更高版本）

    -   Wi-Fi 配置文件 (Android for Work)

    -   Wi-Fi 配置文件（iOS 8.0 及更高版本）

    -   Wi-Fi 配置文件（Mac OS X 10.9 及更高版本）


没有针对此策略类型的建议设置。 必须创建自定义策略。

3.  提供配置文件的名称和描述。

4. 指定“**网络连接**”值。
 - **SSID (服务设置标识符)**：如果希望用户看到网络名称而看不到 SSID，请选择此选项。
 - **在网络未广播其名称 (SSID) 时连接**：选择此选项以使设备可以在网络列表中未显示某网络时连接到该网络（因其处于隐藏状态且未广播其名称）。

5. 为选定的平台配置 **“安全设置”** 。 可用的设置取决于你选择的安全类型。 在[安全设置](#security-settings)中对其进行了说明。

6. 配置**代理设置**（仅 iOS 和 MAC OS X）。

    |设置名|更多信息|何时使用|
    |----------------|-------------------|-------------|
    |**此 Wi-Fi 连接的代理设置**|选择代理设置类型：<br /><br />-   **无**（默认值）<br />-   **手动** - 手动指定代理服务器的 URL 和端口号。<br />-   **自动** - 使用配置文件配置代理服务器。|始终|
    |“代理服务器地址”和“端口号”|指定代理服务器的 URL 和端口号。|如果将“此 Wi-Fi 连接的代理设置”设置为“手动”|
    |**代理服务器 URL**|指定包含代理服务器设置的文件的 URL。|如果将“此 Wi-Fi 连接的代理设置”设置为“自动”|

7.  保存 Wi-Fi 配置文件

新的策略将在“策略”工作区的“配置策略”节点处显示。 有关部署配置文件的信息，请参阅**接下来的步骤**。

## <a name="export-or-import-a-wi-fi-configuration-profile-for-windows-devices"></a>导出或导入 Wi-Fi 配置的配置文件（适用于 Windows 设备）

对于运行 Windows 8.1 或 Windows 10 桌面版或移动版操作系统的设备，可以导入之前导出到文件的 Wi-Fi 配置文件。

### <a name="export-a-wi-fi-profile"></a>导出 Wi-Fi 配置文件
在 Windows 中，可以使用 **netsh wlan** 实用程序将现有的 Wi-Fi 配置文件导出为 Intune 可读取的 XML 文件。 如果 Windows 计算机上已安装了所需的 Wi-Fi 配置文件，请执行以下步骤：

1.  为导出的 Wi-Fi 配置文件创建本地文件夹。 例如，创建名为 **c:\WiFi.** 的文件夹。

2.  以管理员身份打开命令提示符。

3.  运行 `netsh wlan show profiles` 命令，并记下想导出的配置文件的名称。  在此示例中，配置文件的名称是 **WiFiName**。

4.  运行以下命令：`netsh wlan export profile name="ProfileName" folder=c:\Wifi`。这会在目标文件夹中创建一个名为 **Wi-Fi-WiFiName.xml** 的 Wi-Fi 配置文件。

### <a name="import-a-wi-fi-profile"></a>导入 Wi-Fi 配置文件
使用“Windows Wi-Fi 导入策略”导入一组你可以随后部署到所需用户或设备组的 Wi-Fi 设置。


1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，单击**策略**&gt;**添加策略**。

2.  配置类型为“Windows”&gt;“Wi-Fi 导入（Windows 8.1 及更高版本）”的策略。

    此策略可以应用于运行 Windows 8.1 和 Windows 10 桌面版和移动版操作系统的设备。

    你仅可以创建和部署*自定义* Windows Wi-Fi 导入策略。 建议的设置不可用。

3.  为 Windows Wi-Fi 导入策略指定以下常规值：

    |设置名|更多信息|
    |----------------|--------------------|
    |**Name**|输入 Wi-Fi 配置文件的唯一名称，以在 Intune 控制台中识别。|
    |**描述**|提供对 Wi-Fi 配置文件的描述和其他可帮助你找到它的相关信息。|

4.  在“自定义 Wi-Fi 配置文件”的标题下指定以下值：

    |设置名|更多信息|
    |----------------|--------------------|
    |**配置的配置文件**|选择“导入”以选择包含想要导入 Intune 的 Wi-Fi 配置文件设置的 XML 文件。|
    |**自定义配置的配置文件名称（对用户显示）**|选择 Wi-Fi 配置的配置文件名称的显示方式，因为它会显示在用户的设备上。|
    |**配置的配置文件详细信息**|选择所选配置文件的 XML 代码的显示方式。|

5.  完成后，请选择“保存策略”。

6.  新的策略将在“策略”  工作区的“配置策略”  节点处显示。

## <a name="deploy-the-profile"></a>部署配置文件

因为配置文件是一种策略，因此使用“策略”工作区来对其进行部署。

1.  在“策略”工作区中，选择想要部署的策略，然后选择“管理部署”。

2.  在“管理部署”  对话框中：

    -   **部署策略**：选择要向其中部署策略的一个或多个组。 然后选择“添加”&gt;“确定”。

    -   **关闭对话框而不部署**：单击“取消”。


“策略”工作区的“概述”页显示需要关注的策略问题。 此外，状态摘要会显示在“仪表板”工作区中。

## <a name="security-settings"></a>安全设置
这些表具有适用于 Android、iOS 和 Mac OS X Wi-Fi 配置文件的安全设置的详细信息。

### <a name="security-settings-for-android-devices"></a>适用于 Android 设备的安全设置

  |设置名|更多信息|何时使用|
|----------------|--------------------|-------------|
|**安全类型**|选择无线网络的安全协议：<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   如果网络不安全，则为 **无身份验证（开放式）**。|始终|
|**EAP 类型**|请选择用于验证安全无线连接的可扩展身份验证协议 (EAP) 类型：<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|如果选择“WPA-Enterprise/WPA2-Enterprise”安全类型。|
|**请选择用于服务器验证的根证书**|选择“选择”，然后选择用于对连接进行身份验证的受信任根证书配置文件。 有关创建受信任的根证书配置文件的详细信息，请转到[使用证书配置文件保护资源访问的安全](secure-resource-access-with-certificate-profiles.md)。|如果选择任意“EAP 类型”。|
|**身份验证方法**|请选择用于连接的身份验证方法：<br /><br />-   **证书**可指定客户端证书<br />-   **用户名和密码**可指定进行身份验证的不同方法|“EAP 类型”是 **PEAP** 或 **EAP-TTLS**。|
|**选择一个用于身份验证的非 EAP 方法（内部识别）**|选择对连接进行身份验证的方法：<br /><br />-   **无**<br />-   **未加密的密码 (PAP)**<br />-   **质询握手身份验证协议 (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP 版本 2 (MS-CHAP v2)**<br /><br />可用的选项取决于所选择的 EAP 类型。|**“身份验证方法”** 是 **“用户名和密码”**。|
|**启用标识隐私（外部识别）**|请指定为响应 EAP 标识请求而发送的文本。 此文本可以是任何值。 在身份验证期间，首先会发送该匿名标识。 然后会在安全隧道中发送真实标识。|如果“EAP 类型”是“PEAP”或“EAP-TTLS”。|
|**选择客户端证书用于客户端身份验证（身份证书）**|选择“选择”，然后选择用于对连接进行身份验证的 SCEP 证书配置文件。 有关创建 SCEP 根证书配置文件的详细信息，请转到[使用证书配置文件保护资源访问的安全](secure-resource-access-with-certificate-profiles.md)。|如果安全类型为“WPA-Enterprise/WPA2-Enterprise”，并选择了任意“EAP 类型”。|

### <a name="security-settings-for-ios-and-mac-os-x-devices"></a>适用于 iOS 和 Mac OS X 设备的安全设置

  |设置名|更多信息|何时使用|
|----------------|--------------------|-------------|
|**安全类型**|选择无线网络安全协议：<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   如果网络不安全，则为 **无身份验证（开放式）**。|始终|
|**EAP 类型**|请选择用于验证安全无线连接的可扩展身份验证协议 (EAP) 类型：<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|如果选择的安全类型为“WPA-Enterprise/WPA2-Enterprise”。|
|**受信任的服务器证书名称**|选择用于对连接进行身份验证的受信任的根证书配置文件。 有关创建受信任的根证书配置文件的详细信息，请转到[使用证书配置文件保护资源访问的安全](secure-resource-access-with-certificate-profiles.md)。|如果选择的 EAP 类型为“EAP-TLS”、“PEAP”、“EAP-TTLS”或“EAP-FAST”。|
|**使用受保护的访问凭证 (PAC)**|选择以使用受保护的访问凭证来建立客户端和身份验证服务器之间经过身份验证的隧道。 如果存在一个现有的 PAC 文件，则使用它。|如果“EAP 类型”为“EAP-FAST”。|
|**预配 PAC**|在设备上设置 PAC 文件。<br /><br />使用时，你也可以选择“以匿名方式配置 PAC”以确保在不进行服务器身份验证的情况下设置 PAC 文件。|如果选择“安全访问凭证 (PAC)”。|
|**身份验证方法**|请选择用于连接的身份验证方法：<br /><br /><ul><li>**“证书”** 可指定客户端证书</li><li>**用户名和密码**可指定以下非 EAP 方法之一用于身份验证（也称为内部标识）：<br /><br /><ul><li>**无**</li><li>**未加密的密码 (PAP)**</li><li>**质询握手身份验证协议 (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP 版本 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|如果“EAP 类型”是“PEAP”或“EAP-TTLS”。|
|**选择客户端证书用于客户端身份验证（身份证书）**|选择用于对连接进行身份验证的 SCEP 证书配置文件。 有关创建 SCEP 根证书配置文件的详细信息，请转到[使用证书配置文件保护资源访问的安全](secure-resource-access-with-certificate-profiles.md)。|如果安全类型为“WPA-Enterprise/WPA2-Enterprise”并且“EAP 类型”为“EAP-TLS”、“PEAP”或“EAP-TTLS”。|
|**启用标识隐私（外部识别）**|请指定为响应 EAP 标识请求而发送的文本。 此文本可以是任何值。<br /><br />在身份验证期间，首先会发送该匿名标识。 然后会在安全隧道中发送真实标识。|如果“EAP 类型”设置为“PEAP”、“EAP-TTLS”或“EAP-FAST”。|


### <a name="see-also"></a>另请参阅
在[预共享密钥 Wi-Fi 配置文件](pre-shared-key-wi-fi-profile.md)中了解如何创建具有预共享密钥的 Wi-Fi 配置文件。
