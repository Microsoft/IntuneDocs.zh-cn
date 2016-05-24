---
# required metadata

title: Wi-Fi 连接 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的 Wi-Fi 连接
使用 Microsoft Intune Wi-Fi 配置文件将无线网络设置部署到组织中的用户和设备。 这些设置可以简化到无线网络的用户连接。

例如，安装名为 **Contoso Wi-Fi** 的新 Wi-Fi 网络，并且想要将所有 iOS 设备设置为连接到此网络。 过程如下：

1.   创建包含连接到 **Contoso Wi-Fi** 无线网络所必需的设置的 Wi-Fi 配置文件。

2. 使用 iOS 设备将配置文件部署到用户组。

3.   用户在无线网络列表中找到新的“Contoso Wi-Fi”网络，然后即可轻松连接到此网络。

你可以将 Wi-Fi 配置文件部署到以下平台：

-   Android 4.0 及更高版本

-   iOS 7.1 及更高版本

-   Mac OS X 10.9 及更高版本

对于运行 Windows 8.1 及更高版本的设备，你可以导入之前导出到文件的 Wi-Fi 配置的配置文件。 有关详细信息，请参阅本主题中后面的导入 Wi-Fi 配置文件。

## 如何创建 Wi-Fi 配置文件

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，单击“策略” &gt; “添加策略”

2.  选择以下策略类型之一，然后单击 **“创建策略”**：

    -   **Wi-fi 配置文件（Android 4 及更高版本）**

    -   **Wi-Fi 配置文件（iOS 7.1 及更高版本）**

    -   **Wi-Fi 配置文件（Mac OS X 10.9 及更高版本）**

    没有针对此策略类型的建议设置。 必须创建自定义策略。

3.  提供配置文件的名称和描述。

4. 指定 **“网络连接”** 值：

  |设置|详细信息| **网络名称**|指定无线网络的描述性名称。 这是当他们选择无线网络时显示在用户设备上的名称。|

5. **SSID（服务设置标识符）**|指定你的设备要连接到的无线网络的 (SSID)。 SSID 区分大小写，并且不会向用户显示。|

  #### **当此网络处于范围内则自动连接**|选择此选项以当设备在范围内时自动将其连接到无线网络。|

  **在网络未广播其名称 (SSID) 时连接**|选择此选项以允许设备在网络列表中未显示某网络时连接到该网络（因其处于隐藏状态且未广播其名称）。|<br /><br />-   **为选定的平台配置 **“安全设置”** 。**<br />-   可用的设置取决于你选择的安全类型。<br /><br />-   **对于 Android 设备**<br />-   **|设置名称|详细信息|何时使用：|**<br />-   **安全类型**|选择无线网络的安全协议： WPA-Enterprise/WPA2-Enterprise<br /><br />-   如果网络不安全，则为**“无身份验证（开放式）”**。|始终|<br />-   **EAP 类型**|选择用于对安全无线连接进行身份验证的可扩展身份验证协议 (EAP) 类型：<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   ****EAP-TTLS**|选择**“WPA-Enterprise/WPA2-Enterprise”**安全类型。|**<br />-   ****选择用于服务器验证的根证书**|单击“选择”，然后选择用于对连接进行身份验证的可信根证书配置文件。**<br />-   ****重要提示：**若要创建受信任的根证书配置文件，请参阅[使用证书配置文件的安全资源访问](secure-resource-access-with-certificate-profiles.md)。|选中任意 **EAP 类型**。|**<br /><br />**身份验证方法**|选择该连接的身份验证方法： **“证书”** 可指定客户端证书 **用户名和密码**可指定进行身份验证的不同方法|该 **EAP 类型**为 **PEAP** 或 **EAP-TTLS** **选择用于进行身份验证（内部标识）的非 EAP 方法**|选择将如何对连接进行身份验证：

  #### 无

  未加密的密码 (PAP)<br /><br />-   **质询握手身份验证协议 (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP 版本 2 (MS-CHAP v2)**<br />-   可用的选项取决于你选择的 EAP 类型。|**身份验证方法**是**用户名和密码**<br /><br />-   ****启用标识隐私（外部识别）**|指定为响应 EAP 标识请求而发送的文本。**<br />-   **此文本可以是任何值。**<br />-   **在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。|该 **EAP 类型**为 **PEAP** 或 **EAP-TTLS****<br />-   ****选择用于进行客户端身份验证的客户端证书（身份证书）**|单击“选择”，然后选择用于对连接进行身份验证的 SCEP 证书配置文件。**<br />-   ****重要提示：**要创建 SCEP 证书配置文件，请参阅[使用证书配置文件的安全资源访问](secure-resource-access-with-certificate-profiles.md)。|安全类型为 **WPA-Enterprise/WPA2-Enterprise**，且已选中任意 **EAP 类型**。|**<br />-   对于 iOS 和 Mac OS X 设备 |设置名称|详细信息|何时使用：| **安全类型**|选择无线网络安全协议：<br /><br />WPA-Personal/WPA2-Personal<br /><br /><ul><li>WPA-Enterprise/WPA2-Enterprise</li><li>WEP<br /><br /><ul><li>**如果网络不安全，则为**“无身份验证（开放式）”**。|始终|**</li><li>****EAP 类型**|选择用于对安全无线连接进行身份验证的可扩展身份验证协议 (EAP) 类型：**</li><li>**EAP-TLS**</li><li>**PEAP**</li><li>**EAP-TLS**</li><li>**EAP-AST**</li></ul></li></ul>LEAP **EAP-SIM**|选择的安全类型为 **WPA-Enterprise/WPA2-Enterprise** **受信任的服务器证书名称**|选择用于对连接进行身份验证的受信任根证书配置文件。<br /><br />**重要提示：**若要创建受信任的根证书配置文件，请参阅[使用证书配置文件的安全资源访问](secure-resource-access-with-certificate-profiles.md)。|选择的 EAP 类型为 **EAP-TLS**、**PEAP**、**EAP-TTLS** 或 **EAP-FAST**

6. **使用受保护的访问凭证 (PAC)**|选择以使用受保护的访问凭证来建立客户端和身份验证服务器之间经过身份验证的隧道。

    |如果存在一个现有的 PAC 文件，则使用它。|**EAP 类型**为 **EAP-FAST**|**设置 PAC**|对你的设备设置 PAC 文件。|使用时，你也可以选择“以匿名方式设置 PAC”以确保在不对服务器进行身份验证的情况下设置 PAC 文件。|选中了使用受保护的访问凭证 (PAC)。||
    |----------------|-------------------|-------------|
    |****身份验证方法**|选择用于该连接的身份验证方法：**|**“证书”** 可指定客户端证书<br /><br />-   **用户名和密码**可指定以下非 EAP 方法之一用于身份验证（也称为内部标识）：<br />-   无<br />-   未加密的密码 (PAP)|质询握手身份验证协议 (CHAP)|
    |Microsoft CHAP (MS-CHAP)|Microsoft CHAP 版本 2 (MS-CHAP v2)|EAP-TLS|
    |**|**EAP 类型**是 **PEAP** 或 **EAP-TTLS****|**选择用于进行客户端身份验证的客户端证书（身份证书）**|选择用于对连接进行身份验证的 SCEP 证书配置文件。|**重要提示：**要创建 SCEP 证书配置文件，请参阅[使用证书配置文件的安全资源访问](secure-resource-access-with-certificate-profiles.md)。|当安全类型是 **WPA-Enterprise/WPA2-Enterprise** 并且 **EAP 类型**是 **EAP-TLS**、**PEAP** 或 **EAP-TTLS** 时|

7.  **启用标识隐私（外部识别）**|请指定为响应 EAP 标识请求而发送的文本。

此文本可以是任何值。 在身份验证过程中，将首先发送此匿名标识，然后在安全隧道内发送真实标识。|当 **EAP 类型**设置为 **PEAP**、**EAP-TTLS** 或 **EAP-FAST** 时

## （仅限 iOS 和 MAC OS X）配置**代理设置**

### 设置名
更多信息 何时使用：

1.  此 Wi-Fi 连接的代理设置

2.  选择代理设置类型：

3.  **无**（默认值）  **手动** - 手动指定代理服务器的 URL 和端口号。

4.  **自动** – 使用配置文件配置代理服务器。

## 始终
“代理服务器地址”和“端口号” 指定代理服务器的 URL 和端口号。

1.  将“Wi-Fi 连接的代理设置”设置为“手动”

2.  代理服务器 URL

    指定包含代理服务器设置的文件的 URL。 将“Wi-Fi 连接的代理设置”设置为“自动”

3.  保存 Wi-Fi 配置文件

    |新的策略将在“策略”工作区的“配置策略”节点处显示。|有关部署配置文件的信息，请参阅**接下来的步骤**。|
    |----------------|--------------------|
    |**导出或导入 Wi-Fi 配置文件（仅 Windows 8.1 及更高版本）**|导出 Wi-Fi 配置文件|
    |**在 Windows 中，你可以使用 **netsh wlan** 实用程序将现有的 Wi-Fi 配置文件导出为 Intune 可读取的 XML 文件。**|如果 Windows 计算机上已安装了所需的 WiFi 配置文件，请遵循以下过程。|

4.  为导出的 W-Fi-配置文件创建本地文件夹，如 c:\WiFi

    |以管理员身份打开命令提示符。|运行 `netsh wlan show profiles` 命令，并记下想导出的配置文件的名称。|
    |----------------|--------------------|
    |**在此示例中，配置文件名称是 *WiFiName***|运行以下命令：`netsh wlan export profile name="ProfileName" folder=c:\Wifi`。这将在目标文件夹中创建一个名为“Wi-Fi-WiFiName.xml”的 Wi-Fi 配置文件。|
    |**导入 Wi-Fi 配置文件**|使用“Windows Wi-Fi 导入策略”导入一组你可以随后部署到所需用户或设备组的 Wi-Fi 设置。|
    |**导出 Wi-Fi 配置文件的过程在下面内容中进行介绍：**|在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，单击“策略” &gt; “添加策略”|

5.  要配置该类型的策略，请转到“Windows” &gt; “Windows Wi-Fi 导入策略”

6.  你仅可以创建和部署自定义的 Windows Wi-Fi 导入策略。

## 建议的设置不可用。

1.  为 Windows Wi-Fi 导入策略指定以下常规值：

2.  设置名

    -   更多信息

    -   Name


输入 Wi-Fi 配置文件的唯一名称，以在 Intune 控制台中识别。 说明


<!--HONumber=May16_HO2-->


