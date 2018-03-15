---
title: "创建具有预共享密钥的 Wi-Fi 配置文件"
titleSuffix: Microsoft Intune
description: "使用 Intune 自定义配置文件创建具有预共享密钥的 Wi-Fi 配置文件。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8229ac82e6854d75f569b7bbf04dd2f5e14856c7
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2018
---
# <a name="use-a-custom-device-profile-to-create-a-wi-fi-profile-with-a-pre-shared-key"></a>使用自定义设备配置文件，创建具有预共享密钥的 Wi-Fi 配置文件
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

下面介绍了如何使用 Intune 的“自定义设备配置文件”创建具有预共享密匙的 Wi-Fi 配置文件。 本主题还有一个如何创建基于 EAP 的 Wi-Fi 配置文件的示例。

> [!NOTE]
-   如下所述，你可能会发现从连接到网络的计算机复制代码更加轻松。
- 对于 Android，还可以选择使用此由 Johnathon Biersack 提供的 [Android PSK 生成器](http://intunepskgenerator.johnathonb.com/)。
-   可以通过添加更多的 OMA-URI 设置来添加多个网络和密钥。
-  对于 iOS，在 Mac 工作站上使用 Apple Configurator 来设置配置文件。 或者，使用此由 Johnathon Biersack 提供的 [iOS PSK 移动配置生成器](http://intunepskgenerator.johnathonb.com/)。


1.  若要为 Android 或 Windows 创建具有预共享密钥的 Wi-Fi 配置文件或基于 EAP 的配置文件，则在创建设备配置文件时，为该设备平台选择“自定义”，而不是 Wi-Fi 配置文件。

2.  提供名称和说明。
3.  添加新的 OMA-URI 设置：

   a.   输入此 Wi-Fi 网络设置的名称。

   b.   输入 OMA-URI 设置的说明或留空。

   c.   **数据类型**：设置为“字符串”。

   d.   **OMA-URI**：

    - **对于 Android**：./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **对于 Windows**：./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
请务必在开头包括点字符。

    SSID 是你为其创建策略的 SSID。 例如，`./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`

  e. **值字段**：这是粘贴 XML 代码的位置。 此处为一个示例。 每个值都应适于你的网络设置。 参阅代码的注释部分以获取一些指针。
4. 选择“确定”，保存并分配策略。

    > [!NOTE]
    > 只能将此策略分配到用户组。

每个设备在下次签入时，将应用该策略，且将在设备上创建 Wi-Fi 配置文件。 设备将能够自动连接到网络。

## <a name="android-or-windows-wi-fi-profile"></a>Android 或 Windows Wi-Fi 配置文件

下面是一个针对 Android 或 Windows Wi-Fi 配置文件的 XML 代码示例：

> [!IMPORTANT]
>
> `<protected>false</protected>` 必须设置为 **false**，因为 **ture** 可能导致设备需要加密密码并尝试进行解密，这可能导致连接失败。
>
>  `<hex>53534944</hex>` 应设置为 `<name><SSID of wifi profile></name>` 的十六进制值。
>  Windows 10 设备可能会返回误报的“0x87D1FDE8 修正失败”错误，但仍可以使用该配置文件进行预配。

```
<!--
<Name of wifi profile> = Name of profile
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Password to connect to the network
x>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
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
        <keyType>networkKey</keyType>
        <protected>false</protected>
        <keyMaterial>MyPassword</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## <a name="eap-based-wi-fi-profile"></a>基于 EAP 的 Wi-Fi 配置文件
下面是一个针对基于 EAP 的 Wi-Fi 配置文件的 XML 代码示例：

```
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
还可以从现有的 Wi-Fi 连接创建 XML 文件：
1. 在连接到或最近连接到无线网络的计算机上，打开下列文件夹：C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\\{guid}。

    最好使用尚未连接到许多无线网络的计算机，因为必须搜索每个配置文件以找到正确的文件。
3.     搜索 XML 文件以找到具有正确名称的那一个。
4.     找到了正确的 XML 文件后，复制 XML 代码并将其粘贴到 OMA-URI 设置页的数据字段中。

## <a name="best-practices"></a>最佳做法
在部署具有 PSK 的 Wi-Fi 配置文件前，请验证该设备能否直接连接到终结点。

在轮换密钥（密码或通行短语）时，预计故障时间并进行相应的部署规划。 考虑在非工作时间段推送新 Wi-Fi 配置文件。 此外，警告用户连接性可能会受到影响。

若要确保能够进行流畅的转换，请确保最终用户的设备已有到 Internet 的备用连接。 例如，最终用户必须可以切换回来宾 WiFi（或其他一些 WiFi 网络）或者必须有手机网络连接来与 Intune 通信。 这使用户可以在公司 WiFi 配置文件在设备上更新时继续接收策略更新。
