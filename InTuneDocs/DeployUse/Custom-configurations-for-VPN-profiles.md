---
# required metadata

title: VPN 配置文件的自定义配置 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# VPN 配置文件的自定义配置

## 创建自定义配置
可以使用自定义配置在 Intune 中创建 VPN 配置文件。 若要创建自定义配置，请执行以下操作：

   1. 在 Intune 管理控制台中，单击“策略” -> “添加策略” -> *<Expand platform>* -> “自定义配置” -> “创建策略”.
   2. 提供策略的名称。
   3. 对于每个 URI 设置，单击“添加”并提供所需的信息。 下面是一个示例：

   ![VPN 配置文件自定义配置对话框](intune/media/Intune_Add_VPN_URI.png)

   4.  输入所有 URI 设置后，单击“保存策略”，然后部署策略。

## 部署配置策略

1.  在“策略”工作区中，选择想要部署的策略，然后单击“管理部署”.

2.  在“管理部署”  对话框中：

    -   **部署策略** — 选择要向其部署策略的一个组或多个组，然后单击“添加” &gt; “确定”.

    -   **关闭对话框而不部署** — 单击“取消”.

如果你选择的是已部署的策略，则可以在策略列表的下半部分查看有关部署的详细信息。

##自定义 VPN 配置文件配置的 URI 设置示例
以下是用于在名为 Contoso 的虚构公司为 VPN 创建自定义配置的 URI 值的示例条目。 有关详细信息，例如每个条目的数据类型，请参阅 [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx)

Native Contoso VPN (IKEv2):
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
&lt;EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**
True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

有关应如何使用这些设置的任何问题或者有关其作用的更多详细信息，客户应参考 CSP 文档：
https://msdn.microsoft.com/zh-cn/library/windows/hardware/dn914776(v=vs.85).aspx

## PulseSecure 上的 Android 每应用 VPN 的 URI 设置
### 包列表的自定义 URI 
-  数据类型 = 字符串
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/<Name>/PackageList 
-  值 = 分隔符分隔的包列表。
   - 分隔符：分号 (;)、冒号 (:)、逗号 (,)、竖线 (|)

例如： 
- com.android.chrome
- com.android.chrome;com.android.browser

### 模式的自定义 URI（可选）
- 数据类型 = 字符串
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode 

> 注意
> - 请使用分配给自定义配置文件的同一个*名称*
> - 可能的值：“全局”、“白名单”、“黑名单”
> - 如果未提供 PackageList，则默认为“全局”（与整个系统的配置文件向后兼容）
> - 如果提供了 PackageList，则默认为“白名单”


### 另请参阅
（Microsoft Intune 中的 VPN 连接）[vpn-connections-in-microsoft-intune.md]


<!--HONumber=May16_HO1-->


