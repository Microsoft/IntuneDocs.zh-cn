---
# required metadata

title: 使用 PSK 的 Wi-Fi | Microsoft Intune
description: 
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e977c7c7-e204-47a6-b851-7ad7673ceaab

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:


---
# 创建具有预共享密钥的 Wi-Fi 配置文件
下面介绍了如何使用 Intune 的**自定义配置**创建具有预共享密匙的 Wi-Fi 配置文件。 本主题还有一个如何创建基于 EAP 的 Wi-Fi 配置文件的示例。

注意：
-   如下所述，你可能会发现从连接到网络的计算机复制代码更加轻松。
- 对于 Android，还可以选择使用此由 Johnathon Biersack 提供的 [Android PSK 生成器](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/)。
-   可以通过添加更多的 OMA-URI 设置来添加多个网络和密匙。
-  对于 iOS，在 Mac 工作站上使用 Apple 配置器来对配置文件进行配置。 或者，使用此由 Johnathon Biersack 提供的 [iOS PSK 移动配置生成器](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/)。


1.  若要为 Android 或 Windows 创建具有预共享密匙的 Wi-Fi 配置文件或基于 EAP 的配置文件，则在你创建策略时为该设备平台选择“自定义配置”，而不是 Wi-Fi 配置文件。

2.  提供名称和说明。
3.  添加新的 OMA-URI 设置：

   a.   输入此 Wi-Fi 网络设置的名称。

   b。   输入 OMA-URI 设置的说明或留空。

   c.   **数据类型**：设置为“String(XML)”

   d.   **OMA-URI**：./Vendor/MSFT/Wi-Fi /Profile/<SSID>/Settings

注意：请务必在开头包括点字符。

SSID 是你为其创建策略的 SSID。 例如，
`./Vendor/MSFT/Wi-Fi/Profile/Hotspot-1/Settings`

  e.    值字段：这是粘贴 XML 代码的位置。 此处为一个示例。 每个值都应适于你的网络设置。 参阅代码的注释部分以获取一些指针。


    <!--
    <Name of wifi profile> = Name of profile
    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
    <nonBroadcast><true/false></nonBroadcast>
    <Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
    <Type of encryption> = Type of encryption used by the network
    <protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
    <password> = Password to connect to the network
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

## 基于 EAP 的 Wi-Fi 配置文件
下面是一个针对基于 EAP 的 Wi-Fi 配置文件的 XML 代码示例：

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

4.  单击“确定”，然后保存并部署策略。
注意。 只可以将此策略部署到用户组

每个设备在下次签入时，将应用该策略，且将在设备上创建 Wi-Fi 配置文件。 设备将能够自动连接到网络。
## 从现有的 Wi-Fi 连接创建 XML 文件
还可以从现有的 Wi-Fi 连接创建 XML 文件：
1.     在连接到或最近连接到无线网络的计算机上，打开下列文件夹：C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}。 最好使用尚未连接过许多无线网络的计算机，因为你必须搜索每个配置文件以找到正确的那个。
3.     搜索 XML 文件以找到具有正确名称的那一个。
4.     一旦找到了正确的 XML 文件后，复制 XML 代码并将其粘贴到 OMA-URI 设置页的数据字段中。

## 部署策略

1.  在“策略”工作区中，选择想要部署的策略，然后单击“管理部署”

2.  在“管理部署”  对话框中：

    -   **部署策略** — 选择要向其部署策略的一个组或多个组，然后单击“添加” &gt; “确定”

    -   **关闭对话框而不部署** — 单击“取消”

如果你选择的是已部署的策略，则可以在策略列表的下半部分查看有关部署的详细信息。

### 另请参阅
[Microsoft Intune 中的 Wi-Fi 连接](wi-fi-connections-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


