---
title: "如何使用 Microsoft Intune 创建自定义 VPN 配置文件"
titleSuffix: Intune Azure preview
description: "使用自定义配置在 Intune 中创建 VPN 配置文件。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: 990f3ff6528b537d1ea62c82440f1e46bcde8c95
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>如何在 Microsoft Intune 中创建自定义 VPN 配置文件

## <a name="create-a-custom-configuration"></a>创建自定义配置
可使用 Intune 自定义配置策略为以下设备创建 VPN 配置文件：

* 运行 Android 4 和更高版本的设备
* 运行 Windows 8.1 和更高版本的已注册设备
* 运行 Windows Phone 8.1 和更高版本的设备
* 运行 Windows 10 桌面版的已注册设备 
* 运行 Windows 10 移动版的设备

此类型的策略在标准 Intune VPN 策略不包含要使用的设置时很有用。

## <a name="to-create-a-custom-configuration-policy"></a>创建自定义配置策略：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
4. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
5. 在配置文件边栏选项卡上，选择“创建配置文件”。
6. 在“创建配置文件”边栏选项卡上，输入 VPN 配置文件的“名称”和“说明”。
7. 从“平台”下拉列表中，选择要应用 VPN 设置的设备平台。 目前，可以为自定义设备设置选择以下平台之一：
    - **Android**
    - **iOS**（使用从 Apple Configurator 导出的文件配置）。
    - **macOS**（使用从 Apple Configurator 导出的文件配置）。
    - **Windows Phone 8.1**
    - **Windows 10 及更高版本**
6. 从“配置文件”类型下拉列表中，选择“自定义”。
7. 在“自定义 OMA-URI 设置”边栏选项卡上，对于要指定的每个 URI 设置，选择“添加”，提供所需的信息，然后选择“确定”。 下面是一个示例：

   ![VPN 配置文件自定义配置对话框](./media/Intune_Add_VPN_URI.png)

4.  输入所需的所有 URI 设置后，选择“确定”，然后在“创建配置文件”边栏选项卡上，选择“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](how-to-assign-device-profiles.md)。

## <a name="example-uri-settings"></a>示例 URI 设置

这些设置可用于在名为 Contoso 的虚构公司为 VPN 创建自定义配置。
有关可使用的所有设置的完整详细信息，请参阅 [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx)。

Native Contoso VPN (IKEv2): ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn** true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

有关应如何使用这些设置的任何问题或者有关其作用的更多详细信息，客户应参考配置服务供应商 (CSP) 文档：https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx。

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>PulseSecure 上的 Android 每应用 VPN 的 URI 设置
### <a name="custom-uri-for-package-list"></a>包列表的自定义 URI
-  数据类型 = 字符串
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  值 = 分隔符分隔的包列表。
   - 分隔符：分号 (;)、冒号 (:)、逗号 (,)、竖线 (|)

例如：
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>模式的自定义 URI（可选）
- 数据类型 = 字符串
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> 注意
> - 请使用分配给自定义配置文件的同一个*名称*
> - 可能的值：“全局”、“允许列表”、“阻止列表”
> - 如果未提供 PackageList，则默认为“全局”（与整个系统的配置文件向后兼容）
> - 如果提供了 PackageList，则默认为“允许列表”




