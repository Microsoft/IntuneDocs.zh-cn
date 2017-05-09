---
title: "Microsoft Intune VPN 配置文件的自定义配置 | Microsoft Docs"
description: "使用自定义配置在 Intune 中创建 VPN 配置文件。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: a8e44fced435193031d17860b13a03d084b5c6aa
ms.contentlocale: zh-cn
ms.lasthandoff: 04/24/2017


---

# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Microsoft Intune VPN 配置文件的自定义配置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>创建自定义配置
可以使用 Intune 自定义配置策略创建适用于以下设备的 VPN 配置文件：

* 运行 Android 4 和更高版本的设备
* Android for Work 设备
* 运行 Windows 8.1 及更高版本的已注册设备
* 运行 Windows Phone 8.1 和更高版本的设备
* 运行 Windows 10 桌面版的已注册设备
* 运行 Windows 10 移动版的设备

当标准 Intune VPN 策略中没有要使用的设置时，此类策略非常有用。

## <a name="to-create-a-custom-configuration-policy"></a>若要创建自定义配置策略，请执行以下操作：

   1. 在“Intune 管理员控制台”[](https://manage.microsoft.com)中，依次选择“策略” > “添加策略” > “扩展平台” > “自定义配置” > “创建策略”。
   2. 输入策略名称。
   3. 对于要指定的每个 URI 设置，选择“添加”，然后输入相应信息。 下面是一个示例：

   ![VPN 配置文件自定义配置对话框](./media/Intune_Add_VPN_URI.png)

   4.  输入所有 URI 设置后，选择“保存策略”，然后部署此策略。

然后，照常[部署策略](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)。

## <a name="example-uri-settings"></a>示例 URI 设置

这些设置可用于在 Contoso 虚构公司中创建 VPN 自定义配置。
若要详细了解可以使用的所有设置，请参阅 [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx)。

本机 Contoso VPN (IKEv2)：./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns="https://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="https://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="https://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="https://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="https://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="https://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="https://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

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

若对应如何使用这些设置有任何疑问，或要详细了解这些设置的作用，客户应参阅配置服务提供程序 (CSP) 文档：https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx。

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>PulseSecure 上 Android 每应用 VPN 的 URI 设置
### <a name="custom-uri-for-package-list"></a>包列表的自定义 URI
-  数据类型 = 字符串
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  值 = 分隔符分隔的包列表。
   - 分隔符：分号 (;)、冒号 (:)、逗号 (,)、竖线(|)

例如：
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>模式的自定义 URI（可选）
- 数据类型 = 字符串
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> 注意
> - 使用与分配给自定义配置文件相同的*名称*
> - 可取值：*GLOBAL*、*WHITELIST*、*BLACKLIST*
> - 如果未提供 PackageList，默认值为 *GLOBAL*（与全系统配置文件的向后兼容性）
> - 如果提供了 PackageList，默认值为 *WHITELIST*


### <a name="see-also"></a>另请参阅
[Microsoft Intune 中的 VPN 连接](vpn-connections-in-microsoft-intune.md)

