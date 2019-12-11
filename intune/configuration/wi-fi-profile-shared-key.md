---
title: 在 Microsoft Intune - Azure 中创建具有预共享密钥的 WiFi 配置文件 | Microsoft Docs
description: 在 Microsoft Intune 中使用自定义配置文件，创建具有预共享密钥的 Wi-Fi 配置文件并获取适用于 Android、Windows 的 XML 示例代码和基于 EAP 的 Wi-Fi 配置文件
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02d1311be0943d93f80f2f5a1c3f421d476af1e5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059822"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>使用自定义设备配置文件，在 Intune 中创建具有预共享密钥的 Wi-Fi 配置文件

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

预共享密钥 (PSK) 通常用于对 WiFi 网络或无线 LAN 的用户进行身份验证。 通过 Intune，可以创建使用预共享密钥的 WiFi 配置文件。 若要创建配置文件，请使用 Intune 中的“自定义设备配置文件”功能  。 本文还包含一些有关如何创建基于 EAP 的 Wi-Fi 配置文件的示例。

此功能支持：

- Android
- Windows
- 基于 EAP 的 Wi-Fi

> [!IMPORTANT]
> - 在 Windows 10 中使用预共享的密钥会导致 Intune 中出现修正错误。 出现这种情况时，Wi-Fi 配置文件已正确分配给设备，并且该配置文件可以正常工作。
> - 如果导出的 Wi-Fi 配置文件含有预共享密钥，请务必保管好该文件。 密钥为纯文本格式，你需负责保管好该密钥。

## <a name="before-you-begin"></a>在开始之前

- 如下所述，从连接到网络的计算机复制代码可能更加轻松。
- 可以通过添加更多的 OMA-URI 设置来添加多个网络和密钥。
- 对于 iOS，在 Mac 工作站上使用 Apple Configurator 来设置配置文件。
- PSK 需要 64 个十六进制数字的字符串，或 8 到 63 个可打印的 ASCII 字符的密码。 不支持某些字符，如星号 ( * )。

## <a name="create-a-custom-profile"></a>创建自定义配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入策略的描述性名称。 为策略命名，以便稍后可以轻松地识别它们。 例如，良好的策略名称是“适用于 Android 设备的自定义 OMA-URI Wi-fi 配置文件设置”  。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择平台。
    - **配置文件类型**：选择“自定义”  。

4. 在“设置”  中选择“添加”  。 输入具有以下属性的新 OMA URI 设置：

    1. **名称**：输入 OMA-URI 设置的名称。
    2. **说明**：输入 OMA-URI 设置的描述。 此设置是可选的，但建议进行。
    3. **OMA-URI**：使用以下选项之一：

        - **对于 Android**： `./Vendor/MSFT/WiFi/Profile/SSID/Settings`
        - **对于 Windows** ： `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`

        > [!NOTE]
        > 请务必在开头包括点字符。

        SSID 是你为其创建策略的 SSID。 例如，如果 Wi-Fi 命名为 `Hotspot-1`，则输入 `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`。

    4. **数据类型**：选择“字符串”  。

    5. **值**：粘贴 XML 代码。 请参阅本文中的[示例](#android-or-windows-wi-fi-profile-example)。 更新每个值以匹配你的网络设置。 请参阅代码的注释部分获取一些提示。

5. 完成后，选择“确定”   > “创建”  以保存所做的更改。

配置文件显示在配置文件列表中。 接下来，向用户组[分配此配置文件](../device-profile-assign.md)。 只能将此策略分配到用户组。

每个设备在下次签入时，将应用该策略，且将在设备上创建 Wi-Fi 配置文件。 然后设备便能够自动连接到网络。

## <a name="android-or-windows-wi-fi-profile-example"></a>Android 或 Windows Wi-Fi 配置文件示例

下面的示例包含针对 Android 或 Windows Wi-Fi 配置文件的 XML 代码。 该示例用于展示正确的格式并提供更多信息。 但它只是一个示例，并非推荐的环境配置。

### <a name="what-you-need-to-know"></a>须知内容

- `<protected>false</protected>` 必须设为 false  。 如果为 true，可能导致设备需要加密密码并尝试进行解密，这可能导致连接失败  。

- `<hex>53534944</hex>` 应设置为 `<name><SSID of wifi profile></name>` 的十六进制值。 Windows 10 设备可能会返回误报的 `x87D1FDE8 Remediation failed` 错误，但设备仍包含该配置文件。

- XML 包含特殊字符，例如 `&`（& 号）。 使用特殊字符可能会使 XML 无法按预期工作。 

### <a name="example"></a>示例

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>基于 EAP 的 Wi-Fi 配置文件示例
下面的示例包含针对基于 EAP 的 Wi-Fi 配置文件的 XML 代码：该示例用于展示正确的格式并提供更多信息。 但它只是一个示例，并非推荐的环境配置。


```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>从现有的 Wi-Fi 连接创建 XML 文件

还可以从现有的 Wi-Fi 连接创建 XML 文件。 在 Windows 计算机上，使用以下步骤：

1. 为导出的 W-Fi-配置文件创建本地文件夹，如 c:\WiFi。
2. 以管理员身份打开命令提示符（右键单击 `cmd` > “以管理员身份运行”  ）。
3. 运行 `netsh wlan show profiles`。 将列出所有配置文件的名称。
4. 运行 `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`。 此命令在 c:\Wifi 中创建一个名为 `Wi-Fi-YourProfileName.xml` 的文件。

    - 如果要导出包含预共享密钥的 Wi-Fi 配置文件，请将 `key=clear` 添加到命令：
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear` 以纯文本格式导出密钥，这是成功使用配置文件所必需的。

创建 XML 文件后，将 XML 语法复制并粘贴到“OMA-URI 设置”>“数据类型”  。 [创建自定义配置文件](#create-a-custom-profile)（本文中）列出了步骤。

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` 还包括 XML 格式的所有配置文件。

## <a name="best-practices"></a>最佳实践

- 在部署具有 PSK 的 Wi-Fi 配置文件前，请确认该设备能否直接连接到终结点。

- 在轮换密钥（密码或通行短语）时，预计故障时间并进行部署规划。 考虑在非工作时间段推送新 Wi-Fi 配置文件。 此外，警告用户连接性可能会受到影响。

- 为了能够进行流畅的转换，请确保最终用户的设备已有到 Internet 的备用连接。 例如，最终用户可以切换回来宾 WiFi（或其他一些 WiFi 网络）或者必须有手机网络连接来与 Intune 通信。 这个额外连接使用户可以在公司 WiFi 配置文件在设备上更新时接收策略更新。

## <a name="next-steps"></a>后续步骤

请务必[分配配置文件](device-profile-assign.md)，并[监视](device-profile-monitor.md)配置文件状态。
