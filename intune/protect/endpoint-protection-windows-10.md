---
title: Microsoft Intune 中适用于 Windows 10 设备的保护设置 - Azure | Microsoft Docs
description: 在 Windows 10 设备上，使用或配置 Endpoint Protection 设置，以在 Microsoft Intune 中对本地设备启用 Windows Defender 功能，包括应用程序防护、防火墙、SmartScreen、加密和 BitLocker、攻击防护、应用程序控制、安全中心和安全性。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22e3779cd0772753ccd8843cd1f1ff38617298d6
ms.sourcegitcommit: 884654da8e72a63bfaea6b5def6c7891b065f251
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163583"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Windows 10（及更高版本）设置，用于保护使用 Intune 的设备  

[!INCLUDE [azure_portal](../includes/azure_portal.md)]  

Microsoft Intune 包括许多设置，可帮助保护设备。 本文介绍可以在 Windows 10 和更高版本的设备中启用和配置的所有设置。 这些设置是在 Intune 中的 Endpoint Protection 配置文件中创建的，用于控制安全性，包括 BitLocker 和 Windows Defender。  

若要配置 Windows Defender 防病毒软件，请参阅 [Windows 10 设备限制](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)。  

## <a name="before-you-begin"></a>开始之前  

[创建 Endpoint Protection 设备配置配置文件](endpoint-protection-configure.md)。  

有关配置服务提供程序（Csp）的详细信息，请参阅[配置服务提供程序参考](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)。  

## <a name="windows-defender-application-guard"></a>Windows Defender 应用程序防护  

使用 Microsoft Edge 时，Windows Defender 应用程序防护可保护环境免受组织不信任的站点的影响。 用户访问独立网络边界中未列出的站点时，这些站点将在 Hyper-V 虚拟浏览会话中打开。 受信任的站点由在设备配置中配置的网络边界定义。  

应用程序防护仅适用于 Windows 10（64 位）设备。 使用此配置文件将安装用于激活应用程序防护的 Win32 组件。  

- **应用程序防护**  
  **默认值**：未配置  
   应用程序防护 CSP：[设置/AllowWindowsDefenderApplicationGuard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **针对 Edge 启用** - 打开此功能，在 Hyper-V 虚拟化浏览容器中打开不受信任的站点。  
  - **未配置**-可在设备上打开任何站点（可信和不受信任）。  

- **剪贴板行为**  
  **默认值**：未配置  
   应用程序防护 CSP：[设置/ClipboardSettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  选择允许在本地电脑和应用程序防护虚拟浏览器之间执行的复制和粘贴操作。  
  - 未配置   
  - **仅允许从 PC 复制和粘贴到浏览器**  
  - **仅允许从浏览器复制和粘贴到 PC**  
  - **允许在电脑和浏览器之间进行复制和粘贴**  
  - **阻止在 PC 和浏览器之间进行复制和粘贴**  

- **剪贴板内容**  
  仅当 "*剪贴板行为*" 设置为 "*允许*" 设置之一时，此设置才可用。  
  **默认值**：未配置  
  应用程序防护 CSP：[设置/ClipboardFileType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  选择允许的剪贴板内容。  
  - 未配置   
  - **Text**  
  - **图像**  
  - **文本和图像**  

- **企业网站上的外部内容**  
  **默认值**：未配置  
  应用程序防护 CSP：[设置/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **阻止** - 阻止加载未经批准的网站中的内容。  
  - **未配置** - 可以在设备上打开非企业站点。  
 
- **从虚拟浏览器打印**  
  **默认值**：未配置  
  应用程序防护 CSP：[设置/PrintingSettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **允许**-允许从虚拟浏览器打印选定内容。  
  - **未配置**禁用所有打印功能。  

  *允许*打印时，可以配置以下设置：
  - **打印类型**选择以下一个或多个选项：  
    - PDF  
    - XPS  
    - 本地打印机
    - 网络打印机  

- **收集日志**  
  **默认值**：未配置  
  应用程序防护 CSP： [Audit/AuditApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **允许** - 收集应用程序防护浏览会话内发生的事件的日志。  
  - **未配置** - 不会收集浏览会话内的任何日志。  

- **保留用户生成的浏览器数据**  
  **默认值**：未配置  
  应用程序防护 CSP：[设置/AllowPersistence](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **允许**：保存应用程序防护虚拟浏览会话期间创建的用户数据（如密码、收藏和 cookie）。  
  - **未配置**：在设备重启或用户注销时放弃用户下载的文件和数据。  

- **图形加速**  
 **默认值**：未配置  
  应用程序防护 CSP：[设置/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **启用** - 通过获取对虚拟图形处理单元的访问权限来提升加载图形密集型网站和视频的速度。  
  - **未配置**将设备的 CPU 用于图形;不要使用虚拟图形处理单元。  

- **将文件下载到主机文件系统**  
  **默认值**：未配置  
  应用程序防护 CSP：[设置/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **启用** - 用户可以从虚拟化浏览器将文件下载到主机操作系统。  
  - **未配置** - 将文件本地保存在设备上，而不会下载到主机文件系统。  

## <a name="windows-defender-firewall"></a>Windows Defender 防火墙  
 
### <a name="global-settings"></a>全局设置  

以下设置适用于所有网络类型。  

- **文件传输协议**  
  **默认值**：未配置  
   防火墙 CSP： [MdmStore/Global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **阻止** - 禁用有状态 FTP。  
  - **未配置** - 防火墙会筛选监控状态的 FTP 以允许辅助连接。  

- **删除前的安全关联空闲时间**  
  **默认值**：未配置   
   防火墙 CSP： [MdmStore/Global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   指定删除安全关联的空闲时间（以秒为单位）。   

- **预共享密钥编码**  
  **默认值**：未配置  
   防火墙 CSP： [MdmStore/Global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **Enable** -使用 utf-8 编码 presheared 密钥。  
   - **未配置**-使用本地存储值对 presheared 密钥进行编码。  

- **IPsec 免除**  
  **默认值**：*选择 0*  
   防火墙 CSP： [MdmStore/Global/IPsecExempt](https://go.microsoft.com/fwlink/?linkid=872547)

   选择以下一种或多种类型的流量，将其从 IPsec 中排除：  
   - **邻居发现 IPv6 ICMP 类型代码**  
   - **ICMP**  
   - **路由器发现 IPv6 ICMP 类型代码**  
   - **IPv4 和 IPv6 DHCP 流量**  

- **证书吊销列表验证**  
  **默认值**：未配置  
  防火墙 CSP： [MdmStore/Global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  选择设备验证证书吊销列表的方式。 选项包括：  
  - **禁用 CRL 验证**  
  - **仅对吊销的证书进行 CRL 验证失败**  
  - **对遇到的任何错误进行 CRL 验证失败**。  
 

- **适时地按每个密钥模块匹配身份验证集**  
  **默认值**：未配置  
  防火墙 CSP： [MdmStore/Global/OpportunisticallyMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **启用**：密钥模块必须仅忽略它们不支持的身份验证套件。  
  - **未配置**：如果密钥模块不支持此集中指定的所有身份验证套件，则必须忽略整个身份验证集。  


- **数据包排队**  
  **默认值**：未配置  
  防火墙 CSP： [MdmStore/Global/EnablePacketQueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  指定如何针对 IPsec 隧道网关方案为加密接收和明文转发启用接收端上的软件缩放。 此设置可确保数据包顺序得到保留。 选项包括：  
  - 未配置   
  - **禁用所有数据包队列**  
  - **仅对入站加密的数据包排队**  
  - **执行解密后的队列数据包仅用于转发**  
  - **配置入站和出站数据包**  

### <a name="network-settings"></a>网络设置  

以下设置分别在本文中列出，但全部适用于三种特定网络类型：  
- **域（工作区）网络**  
- **专用（可发现）网络**  
- **公共（不可发现）网络**  

#### <a name="general-settings"></a>常规设置  

- **Windows Defender 防火墙**  
  **默认值**：未配置  
  防火墙 CSP： [EnableFirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **启用** - 打开此防火墙并提升安全性。 
  - **未配置**：允许所有流量，而不考虑任何其他策略设置。  

- **隐藏模式**  
  **默认值**：未配置  
  防火墙 CSP： [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - 未配置   
  - **阻止防火墙**在隐藏模式下运行。 阻止隐藏模式还可以阻止“IPsec 安全数据包免除”  。  
  - **Allow** -防火墙在隐藏模式下运行，这有助于防止响应探测请求。  

- **具有隐形模式的 IPsec 安全数据包免除**  
  **默认值**：未配置  
  防火墙 CSP： [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  如果将*隐形模式*设置为 "*阻止*"，则会忽略此选项。  

  - 未配置   
  - **阻止**IPSec 保护的数据包不会收到例外。  
  - **Allow** -启用例外。 防火墙的秘密模式不得阻止主机响应受 IPsec 保护的未经请求的网络流量。  

- **受防护**  
  **默认值**：未配置  
  防火墙 CSP：[受防护](https://go.microsoft.com/fwlink/?linkid=872561)  
    - 未配置   
    - **阻止**-当 Windows Defender 防火墙打开且此设置设置为 "*阻止*" 时，无论其他策略设置如何，都将阻止所有传入流量。 
    - **允许**-如果设置为 "*允许*"，则关闭此设置，并根据其他策略设置允许传入流量。

- **针对多播广播的单播响应**  
  **默认值**：未配置  
  防火墙 CSP： [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  通常，你不希望接收针对多播或广播消息的单播响应。 这些响应可能表示拒绝服务 (DOS) 攻击，或攻击者尝试探测已知的实时计算机。  
  - 未配置   
  - **阻止** - 阻止针对多播广播的单播响应。  
  - **允许** - 允许针对多播广播的单播响应。  

- **入站通知**  
  **默认值**：未配置  
  防火墙 CSP： [DisableInboundNotifications](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - 未配置   
  - **阻止**-隐藏在阻止应用侦听端口时使用的通知。  
  - **允许** - 启用此设置，且可能会在阻止应用侦听某个端口时向用户显示一条通知。  

- **出站连接默认操作**  
  **默认值**：未配置  
  防火墙 CSP： [DefaultOutboundAction](https://aka.ms/intune-firewall-outboundaction)  
  
  配置防火墙对出站连接执行的默认操作。 此设置将应用于 Windows 版本1809及更高版本。  

  - 未配置   
  - **阻止**-默认防火墙操作不会对出站流量运行，除非显式指定为不阻止。  
  - **允许**-默认防火墙操作在出站连接上运行。  

- **入站连接默认操作**  
  **默认值**：未配置  
  防火墙 CSP： [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - 未配置   
  - **阻止** - 不会在入站连接上运行默认的防火墙操作。  
  - **允许**-默认防火墙操作在入站连接上运行。  

#### <a name="rule-merging"></a>规则合并  

- **来自本地存储的已授权应用程序 Windows Defender 防火墙规则**  
  **默认值**：未配置  
  防火墙 CSP： [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - 未配置   
  - **阻止** - 忽略且不会强制执行本地存储中已授权的应用程序防火墙规则。  
  - **允许** -
   选择“启用”可应用本地存储中的防火墙规则，以便识别和强制执行它们 **** 。  

- **来自本地存储的全局端口 Windows Defender 防火墙规则**  
  **默认值**：未配置  
  防火墙 CSP： [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - 未配置   
  - **阻止**-本地存储中的全局端口防火墙规则将被忽略且不会强制执行。  
  - **允许** - 应用本地存储中要识别和强制执行的全局端口防火墙规则。  

- **来自本地存储的 Windows Defender 防火墙规则**  
  **默认值**：未配置  
  防火墙 CSP： [AllowLocalPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - 未配置   
  - 将忽略本地存储区中的**阻止**防火墙规则，并且不强制执行这些规则。
  - **允许** - 应用本地存储中要识别和强制执行的防火墙规则。  

- **来自本地存储的 IPsec 规则**  
  **默认值**：未配置  
  防火墙 CSP： [AllowLocalIpsecPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - 未配置   
  - **阻止** -  忽略且不会强制执行本地存储中的连接安全规则，而不考虑架构版本和连接安全规则版本。  
  - **允许** - 应用本地存储中的连接安全规则，而不考虑架构或连接安全规则版本。  

### <a name="firewall-rules"></a>防火墙规则  

可以**添加**一个或多个自定义防火墙规则。 有关详细信息，请参阅[添加适用于 Windows 10 设备的自定义防火墙规则](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)。  

自定义防火墙规则支持以下选项：  

#### <a name="general-settings"></a>常规设置：  

- **名称**  
  **默认值**：*无名称*  

  指定规则的友好名称。 此名称将显示在规则列表中以帮助你识别它。  

- **描述**  
  **默认值**：*无说明*  

  提供规则的说明。  

- **方向**   
  **默认值**：未配置  
  防火墙 CSP： [FirewallRules/*FirewallRuleName*/Direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  指定此规则是否适用于**入站**或**出站**流量。 如果设置为 "**未配置**"，则规则将自动应用于出站流量。  

- **操作**  
  **默认值**：未配置  
  防火墙 CSP： [FirewallRules/*FirewallRuleName*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)和[FirewallRules/*FirewallRuleName*/Action/Type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  选择 "**允许**" 或 "**阻止**"。 如果设置为 "**未配置**"，则规则默认为允许流量。  

- **网络类型**  
  **默认值**：选择0  
  防火墙 CSP： [FirewallRules/*FirewallRuleName*/Profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  选择此规则所属的最多三种类型的网络类型。 选项包括 "**域**"、"**专用**" 和 "**公共**"。  如果未选择任何网络类型，则规则适用于所有三种网络类型。  

#### <a name="application-settings"></a>应用程序设置  

- **应用程序**  
  **默认值**：全部  

  控制应用程序或程序的连接。 选择以下选项之一，然后完成其他配置：  
  - **包系列名称**–指定包系列名称。 若要查找包系列名称，请使用 PowerShell 命令**add-appxpackage**。   
    防火墙 CSP： [FirewallRules/*FirewallRuleName*/App/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - **文件路径**–必须指定客户端设备上应用的文件路径，该路径可以是绝对路径或相对路径。 例如： C:\Windows\System\Notepad.exe 或%WINDIR%\Notepad.exe。  
    防火墙 CSP： [FirewallRules/*FirewallRuleName*/App/FilePath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Windows 服务**–指定 windows 服务的短名称（如果它是服务，而不是发送或接收流量的应用程序）。 若要查找服务的短名称，请使用 PowerShell 命令**获取服务**。  
    防火墙 CSP： [FirewallRules/*FirewallRuleName*/App/ServiceName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **全部**-*无其他配置可用*。  

#### <a name="ip-address-settings"></a>IP 地址设置  

指定此规则应用到的本地和远程地址。  

- **本地地址**    
  **默认值**：任何地址  
  防火墙 CSP： [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  选择**任何地址**或**指定的地址**。  

  使用指定的*地址*时，可以添加一个或多个地址作为规则涵盖的本地地址的逗号分隔列表。 有效的令牌包括：  
  - 对*任何*本地地址使用星号 "*"。 如果使用星号，则它必须是所使用的唯一令牌。  
  - 若要指定子网，请使用子网掩码或网络前缀表示法。 如果不指定子网掩码和网络前缀，子网掩码默认为255.255.255.255。  
  - 有效 IPv6 地址。  
  - 包含不带空格的 "起始地址-结束地址" 格式的 IPv4 地址范围。  
  - 包含不带空格的 "起始地址-结束地址" 格式的 IPv6 地址范围。  

- **远程地址**  
  **默认值**：任何地址  
  防火墙 CSP： [FirewallRules/*FirewallRuleName*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  选择**任何地址**或**指定的地址**。  

  使用指定的*地址*时，可以添加一个或多个地址作为规则涵盖的远程地址的逗号分隔列表。 标记不区分大小写。 有效的令牌包括：  
  - 对*任何*远程地址使用星号 "*"。 如果使用星号，则它必须是所使用的唯一令牌。  
  - Defaultgateway  
  - "DHCP"  
  - "DNS"  
  - "WINS"  
  - "Intranet" （在 Windows 版本1809及更高版本上受支持）  
  - "RmtIntranet" （在 Windows 版本1809及更高版本上受支持）  
  - "Internet" （在 Windows 版本1809及更高版本上受支持）  
  - "Ply2Renders" （在 Windows 版本1809及更高版本上受支持）  
  - "LocalSubnet" 指示本地子网上的任何本地地址。  
  - 若要指定子网，请使用子网掩码或网络前缀表示法。 如果不指定子网掩码和网络前缀，子网掩码默认为255.255.255.255。  
  - 有效 IPv6 地址。  
  - 包含不带空格的 "起始地址-结束地址" 格式的 IPv4 地址范围。  
  - 包含不带空格的 "起始地址-结束地址" 格式的 IPv6 地址范围。  

#### <a name="port-and-protocol-settings"></a>端口和协议设置  
指定此规则应用到的本地和远程端口。  

- **协议**  
  **默认值**： Any  
  防火墙 CSP： [FirewallRules/*FirewallRuleName*/Protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  从以下项中选择，并完成任何所需的配置：  
  - **全部**-无其他配置可用。  
  - **TCP** –配置本地端口和远程端口。 这两个选项都支持所有端口或指定端口。 使用以逗号分隔的列表输入指定端口。  
    - **本地端口**-防火墙 CSP： [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **远程端口**-防火墙 CSP： [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** –配置本地端口和远程端口。 这两个选项都支持所有端口或指定端口。 使用以逗号分隔的列表输入指定端口。  
    - **本地端口**-防火墙 CSP： [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **远程端口**-防火墙 CSP： [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **自定义**–指定从0到255的自定义**协议**号。  

#### <a name="advanced-configuration"></a>高级配置  
- **接口类型**  
  **默认值**：选择0  
  防火墙 CSP： [FirewallRules/*FirewallRuleName*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  选择从以下选项：  
  - **远程访问**  
  - **无线**  
  - **局域网**  

- **仅允许来自这些用户的连接**  
  **默认值**：所有用户 *（在未指定列表时默认为 "所有*用户"）  
  防火墙 CSP： [FirewallRules/*FirewallRuleName*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  指定此规则的已授权本地用户的列表。 如果此规则适用于 Windows 服务，则不能指定授权用户的列表。  


## <a name="windows-defender-smartscreen-settings"></a>Windows Defender SmartScreen 设置  
 
必须在设备上安装 Microsoft Edge。  

- **用于应用和文件的 SmartScreen**  
  **默认值**：未配置  
   SmartScreen CSP： [smartscreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **未配置**-禁止使用 SmartScreen。  
  - **启用** - 启用 Windows SmartScreen 用于执行文件和运行应用。 SmartScreen 是一种基于云的防网络钓鱼和反恶意软件组件。  

- **未经验证的文件执行**  
  **默认值**：未配置  
   SmartScreen CSP： [smartscreen/PreventOverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **未配置** - 禁用此功能，并允许最终用户运行未经验证的文件。  
  - **阻止** - 阻止最终用户运行未经 Windows SmartScreen 验证的文件。  

## <a name="windows-encryption"></a>Windows 加密  
 
### <a name="windows-settings"></a>Windows 设置  

这些加密设置适用于所有版本的 Windows 10。  

- **加密设备**  
  **默认值**：未配置  
  BitLocker CSP： [RequireDeviceEncryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **需要** - 提示用户启用设备加密。 根据不同的 Windows 版本和系统配置，用户可能需要执行不同的操作：  
    - 确认未启用来自其他提供程序的加密功能。  
    - 需要关闭 BitLocker 驱动器加密，然后重新开启 BitLocker。  
  - 未配置   
  
  如果 Windows 加密开启时另一种加密方法处于活动状态，设备可能会变得不稳定。  

- **加密存储卡（仅限移动设备）**  
  *此设置仅适用于 Windows 10 移动设备。*  
  **默认值**：未配置  
  BitLocker CSP： [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - 选择“需要”可对设备使用的任何可移动存储卡进行加密  。  
  - **未配置** - 不需要存储卡加密，也不会提示用户开启它。  

### <a name="bitlocker-base-settings"></a>BitLocker 基本设置  

基本设置是适合所有数据驱动器类型的通用 BitLocker 设置。 这些设置用于管理最终用户可以在所有类型的数据驱动器中修改哪些驱动器加密任务或配置选项。  

- **其他磁盘加密的警告**  
  **默认值**：未配置  
  BitLocker CSP： [AllowWarningForOtherDiskEncryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **阻止** - 禁用关于设备上存在其他磁盘加密服务的警告。  
  - **未配置**-允许显示其他磁盘加密的警告。  

  设置为 "*阻止*" 时，可以配置以下设置：  

  - **允许标准用户在 Azure AD 加入期间启用加密**  
    *此设置仅适用于 Azure Active Directory 联接（Azure 调整）设备，并且取决于以前的设置，`Warning for other disk encryption`。*  
    **默认值**：未配置  
    BitLocker CSP： [AllowStandardUserEncryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **允许**-标准用户（非管理员）可以在登录时启用 BitLocker 加密。  
     - **未配置**：仅允许管理员在设备上启用 BitLocker 加密。  

- **配置加密方法**  
  **默认值**：未配置  
  BitLocker CSP： [EncryptionMethodByDriveType](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **启用** - 配置操作系统、数据和可移动驱动器的加密算法。  
  - **未配置** - BitLocker 将 XTS-AES 128 位用作默认加密方法，或使用任何安装脚本指定的加密方法。  

  设置为“启用”时，可以配置以下设置：   

  - **操作系统驱动器加密**  
    **默认值**： XTS-AES 128 位  
   
    选择操作系统驱动器的加密方法。 建议使用 XTS-AES 算法。  
    - **AES-CBC 128 位**  
    - **AES-CBC 256 位**  
    - **XTS-AES 128 位**  
    - **XTS-AES 256 位**  

  - **固定数据驱动器的加密**  
    **默认值**： AES-CBC 128 位  
   
    选择固定（内置）数据驱动器的加密方法。 建议使用 XTS-AES 算法。  
    - **AES-CBC 128 位**  
    - **AES-CBC 256 位**  
    - **XTS-AES 128 位**  
    - **XTS-AES 256 位**  

  - **可移动数据驱动器的加密**  
    **默认值**： AES-CBC 128 位  

    选择可移动数据驱动器的加密方法。 如果在不运行 Windows 10 的设备上使用可移动驱动器，建议使用 AES-CBC 算法。  
    - **AES-CBC 128 位**  
    - **AES-CBC 256 位**  
    - **XTS-AES 128 位**  
    - **XTS-AES 256 位**  

### <a name="bitlocker-os-drive-settings"></a>BitLocker OS 驱动器设置  

以下设置仅适用于操作系统数据驱动器。  

- **启动时的其他身份验证**  
  **默认值**：未配置  
  BitLocker CSP： [SystemDrivesRequireStartupAuthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **需要** - 配置计算机启动时的身份验证要求，包括使用受信任的平台模块 (TPM)。  
  - **未配置**-仅在带有 TPM 的设备上配置基本选项。  

  设置为“需要”时，可以配置以下设置：   

  - **包含非兼容 TPM 芯片的 BitLocker**  
    **默认值**：未配置  

    - **阻止** - 在设备不具备兼容 TPM 芯片时禁止使用 BitLocker。  
    - **未配置** - 用户能在不具备兼容 TPM 芯片的情况下使用 BitLocker。 BitLocker 可能需要密码或启动密钥。  

  - **兼容的 TPM 启动**  
    **默认值**：允许 TPM  

    配置是否允许、需要或不允许使用 TPM。  

    - **允许 TPM**  
    - **不允许 TPM**  
    - **需要 TPM**  

  - **兼容的 TPM 启动 PIN**  
    **默认值**：允许 TPM 启动 PIN  

    选择是允许、不允许还是要求使用带有 TPM 芯片的启动 PIN。 启用启动 PIN 需要最终用户进行交互。  

    - **允许 TPM 的启动 PIN**  
    - **不允许 TPM 启动 PIN**  
    - **需要 TPM 的启动 PIN**

  - **兼容的 TPM 启动密钥**  
    **默认值**：允许 TPM 启动密钥  

    选择是允许、不允许还是要求使用带有 TPM 芯片的启动密钥。 启用启动密钥需要最终用户进行交互。  

    - **允许 TPM 的启动密钥**  
    - **不允许 TPM 启动密钥**  
    - **需要 TPM 的启动密钥**  

  - **兼容的 TPM 启动密钥和 PIN**  
    **默认**：允许启动密钥和与 TPM 的 PIN  

    选择是允许、不允许还是要求使用带有 TPM 芯片的启动密钥和 PIN。 启用启动密钥和 PIN 需要最终用户进行交互。  
    - **允许具有 TPM 的启动密钥和 PIN**  
    - **不允许带 TPM 的启动密钥和 PIN**  
    - **需要具有 TPM 的启动密钥和 PIN**   

- **最小 PIN 长度**  
    **默认值**：未配置  
    BitLocker CSP： [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **启用**配置 TPM 启动 PIN 的最小长度。  
    - **未配置** - 用户可以配置 6 到 20 位之间任何长度的启动 PIN。  

  设置为“启用”时，可以配置以下设置：   

  - **最少字符数**  
    **默认**：*未配置*BitLocker CSP： [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)  

    输入启动 PIN 所需的字符数（介于 4-20）   。  

- **OS 驱动器恢复**  
  **默认值**：未配置   
  BitLocker CSP： [SystemDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **启用** - 控制在所需启动信息不可用时如何恢复受 BitLocker 保护的操作系统驱动器。  
  - **未配置** - BitLocker 恢复支持默认的恢复选项。 默认情况下允许使用 DRA，由用户选择恢复选项（包括恢复密码和恢复密钥），并且不会将恢复信息备份至 AD DS。  

  设置为“启用”时，可以配置以下设置：   

  - **基于证书的数据恢复代理**  
    **默认值**：未配置  
     
    - **阻止**-阻止将数据恢复代理与受 BitLocker 保护的 OS 驱动器一起使用。  
    - **未配置**-允许将数据恢复代理与受 BitLocker 保护的操作系统驱动器一起使用。  

  - **用户创建恢复密码**  
    **默认值**：允许48位数的恢复密码  

    选择是允许、要求还是不允许用户生成 48 位数的恢复密码。  
    - **允许48位数的恢复密码**  
    - **不允许48位数的恢复密码**  
    - **需要48位数的恢复密码**  

  - **用户创建恢复密钥**  
    **默认值**：允许256位恢复密钥  

    选择是允许、要求还是不允许用户生成 256 位数的恢复密钥。  
    - **允许256位恢复密钥**  
    - **不允许256位恢复密钥**  
    - **需要256位恢复密钥**  

  - **BitLocker 安装向导中的恢复选项**  
    **默认值**：未配置  

    - **阻止** - 用户无法查看和更改恢复选项。 如果设置为 
    - **未配置** - 用户可以在开启 BitLocker 时查看并更改恢复选项。 
 
  - **将 BitLocker 恢复信息保存到 Azure Active Directory**  
    **默认值**：未配置  

    - **启用** - 将 BitLocker 恢复信息存储到 Azure Active Directory (Azure AD)。  
    - **未配置-不会**将 BitLocker 恢复信息存储在 AAD 中。  

  - **存储到 Azure Active Directory 的 BitLocker 恢复信息**  
    **默认值**：备份恢复密码和密钥包  

    配置将 BitLocker 恢复信息的哪些部分存储到 Azure AD 中。 选择：  
    - “备份恢复密码和密钥包”   
    - “仅备份恢复密码”   

  - **客户端驱动的恢复密码轮换**  
    **默认值**：已为 Azure AD 联接的设备启用密钥轮换  
    BitLocker CSP： [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    此设置在操作系统驱动器恢复之后（通过使用 bootmgr 或 WinRE）启动客户端驱动的恢复密码轮替。  

    - 未配置  
    - 已禁用密钥轮替  
    - 为 Azure AD 联接的设备启用的密钥轮换  
    - 为 Azure AD 和混合加入设备启用的密钥轮换  

  - **在启用 BitLocker 前将恢复信息存储在 Azure Active Directory**  
    **默认值**：未配置  
 
     阻止用户启用 BitLocker，除非计算机成功将 BitLocker 恢复信息备份到 Azure Active Directory。  

    - **需要** - 阻止用户启用 BitLocker，除非 BitLocker 恢复信息已成功存储在 Azure AD 中。  
    - **未配置** - 用户可以开启 BitLocker，即使未能成功将恢复信息存储在 Azure AD 中。  

- **预启动恢复消息和 URL**  
  **默认值**：未配置  
  BitLocker CSP： [SystemDrivesRecoveryMessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **启用**-配置在预启动密钥恢复屏幕上显示的消息和 URL。  
  - **未配置** - 禁用此功能。  
  
  设置为“启用”时，可以配置以下设置：   
  - **预启动恢复消息**  
    **默认值**：使用默认恢复消息和 URL   
 
    配置如何向用户显示预启动恢复消息。 选择：  
    - “使用默认恢复消息和 URL”   
    - “使用空的恢复消息和 URL”   
    - “使用自定义恢复消息”   
    - “使用自定义恢复 URL”   

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 固定数据驱动器设置  

这些设置专门适用于固定的数据驱动器。  

- **对不受 BitLocker 保护的固定驱动器的写访问**  
  **默认值**：未配置  
  BitLocker CSP： [FixedDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **阻止** - 对不受 BitLocker 保护的数据驱动器授予只读访问权限。  
  - **未配置**-默认情况下，对未加密的数据驱动器的读取和写入访问权限。  

- **固定驱动器恢复**  
  **默认值**：未配置  
  BitLocker CSP： [FixedDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **启用** - 控制在所需启动信息不可用时如何恢复受 BitLocker 保护的固定驱动器。  
  - **未配置** - 禁用此功能。  

  设置为“启用”时，可以配置以下设置：   

  - **数据恢复代理**  
    **默认值**：未配置  
 
    - **阻止** - 阻止受 BitLocker 保护的固定驱动器策略编辑器使用数据恢复代理。 
    - **未配置** - 允许将数据恢复代理用于受 BitLocker 保护的固定驱动器。  

  - **用户创建恢复密码**  
    **默认值**：允许48位数的恢复密码  

    选择是允许、要求还是不允许用户生成 48 位数的恢复密码。  
    - **允许48位数的恢复密码**  
    - **不允许48位数的恢复密码**  
    - **需要48位数的恢复密码**  

  - **用户创建恢复密钥**  
    **默认值**：允许256位恢复密钥

    选择是允许、要求还是不允许用户生成 256 位数的恢复密钥。
    - **允许256位恢复密钥**  
    - **不允许256位恢复密钥**  
    - **需要256位恢复密钥**  

  - **BitLocker 安装向导中的恢复选项**  
    **默认值**：未配置  

    - **阻止** - 用户无法查看和更改恢复选项。 如果设置为 
    - **未配置** - 用户可以在开启 BitLocker 时查看并更改恢复选项。
 
  - **将 BitLocker 恢复信息保存到 Azure Active Directory**  
    **默认值**：未配置  

    - **启用** - 将 BitLocker 恢复信息存储到 Azure Active Directory (Azure AD)。  
    - **未配置-不会**将 BitLocker 恢复信息存储在 AAD 中。

  - **存储到 Azure Active Directory 的 BitLocker 恢复信息**  
    **默认值**：备份恢复密码和密钥包  

    配置将 BitLocker 恢复信息的哪些部分存储到 Azure AD 中。 选择：  
    - “备份恢复密码和密钥包”   
    - “仅备份恢复密码”   

  - **客户端驱动的恢复密码轮换**  
    **默认值**：已为 Azure AD 联接的设备启用密钥轮换  
    BitLocker CSP： [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    此设置在操作系统驱动器恢复之后（通过使用 bootmgr 或 WinRE）启动客户端驱动的恢复密码轮替。  

    - 未配置  
    - 已禁用密钥轮替  
    - 为 Azure AD 联接的设备启用的密钥轮换  
    - 为 Azure AD 和混合加入设备启用的密钥轮换  

  - **在启用 BitLocker 前将恢复信息存储在 Azure Active Directory**  
    **默认值**：未配置  
 
    阻止用户启用 BitLocker，除非计算机成功将 BitLocker 恢复信息备份到 Azure Active Directory。  

    - **需要** - 阻止用户启用 BitLocker，除非 BitLocker 恢复信息已成功存储在 Azure AD 中。  
    - **未配置** - 用户可以开启 BitLocker，即使未能成功将恢复信息存储在 Azure AD 中。  

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 可移动数据驱动器设置  

这些设置专门适用于可移动数据驱动器。  

- **对不受 BitLocker 保护的可移动数据驱动器的写权限**  
  **默认值**：未配置  
  BitLocker CSP： [RemovableDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **阻止** - 对不受 BitLocker 保护的数据驱动器授予只读访问权限。  
  - **未配置**-默认情况下，对未加密的数据驱动器的读取和写入访问权限。  

  设置为“启用”时，可以配置以下设置：   

  - **对其他组织中配置的设备的写权限**  
    **默认值**：未配置  

    - **阻止** - 允许对其他组织中配置的设备的写权限。  
    - **未配置**-拒绝写入访问权限。  
 
## <a name="windows-defender-exploit-guard"></a>Windows Defender 攻击防护  

使用[exploit protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection)来管理和减少员工使用的应用的受攻击面。  

### <a name="attack-surface-reduction"></a>攻击面减少  

攻击面减少规则可帮助防止恶意软件通常使用来感染具有恶意代码的计算机。  

#### <a name="attack-surface-reduction-rules"></a>攻击面减少规则  

- **标记从 Windows 本地安全机构子系统窃取的凭据**  
  **默认值**：未配置  
  规则：[阻止从 Windows 本地安全机构子系统 (lsass.exe) 中窃取凭据](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe)

  帮助防止操作和应用（通常被寻找漏洞的恶意软件所利用）感染计算机。  

  - 未配置   
  - **启用** - 标记从 Windows 本地安全机构子系统 (lsass.exe) 窃取的凭据。  
  - **仅审核**  

- **从 Adobe Reader （beta 版本）创建进程**  
  **默认值**：未配置  
  规则：[阻止 Adobe Reader 创建子进程](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - 未配置   
  - **Enable** -阻止从 Adobe Reader 创建的子进程。  
  - **仅审核**  

#### <a name="rules-to-prevent-office-macro-threats"></a>防止 Office 宏威胁的规则  

阻止 Office 应用执行下列操作：  

- **Office 应用插入其他进程（无异常）**  
  **默认值**：未配置  
  规则：[阻止 Office 应用程序将代码注入其他进程](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)  

  - 未配置   
  - **阻止**Office 应用插入其他进程。  
  - **仅审核**  

- **Office 应用/宏创建可执行内容**  
  **默认值**：未配置  
  规则：[阻止 Office 应用程序创建可执行内容](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)  

  - 未配置   
  - **阻止**Office 应用和宏创建可执行内容。  
  - **仅审核**  

- **Office 应用启动子进程**  
  **默认值**：未配置  
  规则：[阻止所有 Office 应用程序创建子进程](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - 未配置   
  - **阻止**Office 应用启动子进程。  
  - **仅审核**  
  
- **Win32 从 Office 宏代码导入**  
  **默认值**：未配置  
  规则：[阻止来自 Office 宏的 Win32 API 调用](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)  

  - 未配置   
  - **块**区 Win32 从 Office 中的宏代码导入。  
  - **仅审核**  
  
- **从 Office communication 产品创建进程**  
  **默认值**：未配置  
  规则：[阻止 Office 通信应用程序创建子进程](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - 未配置   
  - **Enable** -阻止从 Office communication apps 创建子进程。  
  - **仅审核**  

#### <a name="rules-to-prevent-script-threats"></a>防止脚本威胁的规则  

阻止以下内容以帮助防止脚本威胁：  

- **不确定的 js/vbs/ps/宏代码**  
  **默认值**：未配置  
  规则：[阻止执行可能经过模糊处理的脚本](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)    

  - 未配置   
  - **Block** -阻止任何模糊的 js/vbs/ps/宏代码。  
  - **仅审核**  

- **js/vbs 执行从 Internet 下载的有效负载（无异常）**  
  **默认值**：未配置  
  规则：[阻止 JavaScript 或 VBScript 启动下载的可执行内容](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)  

  - 未配置   
  - **块**区 js/vbs 执行从 Internet 下载的有效负载。  
  - **仅审核**  

- **来自 PSExec 和 WMI 命令的进程创建**  
  **默认值**：未配置  
  规则：[阻止来自 PSExec 和 WMI 命令的进程创建](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)  

  - 未配置   
  - **阻止** - 阻止来自 PSExec 和 WMI 命令的进程创建。  
  
  - **仅审核**  

- **从 USB 运行的不受信任和未签名的进程**  
  **默认值**：未配置  
  规则：[阻止从 USB 运行的不受信任和未签名的进程](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)    

  - 未配置   
  - **阻止** - 阻止从 USB 运行的不受信任和未签名的进程。  
  - **仅审核**  
  
- **不符合普及程度、年龄或信任列表条件的可执行文件**  
  **默认值**：未配置  
  规则：[阻止可执行文件的运行，除非这些文件符合普及程度、年龄或信任列表条件](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    

  - 未配置   
  - **阻止** - 阻止可执行文件的运行，除非这些文件符合普及程度、年龄或信任列表条件。  
  - **仅审核**  

#### <a name="rules-to-prevent-email-threats"></a>防止电子邮件威胁的规则  

阻止以下行为以帮助防止电子邮件威胁：  

- **执行从电子邮件（webmail/邮件客户端）中删除的可执行内容（exe、dll、ps、js、vbs 等）（无异常）**  
  **默认值**：未配置  
  规则：[阻止来自电子邮件客户端和 Web 邮件的可执行内容](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)  

  - 未配置   
  - **阻止** - 阻止执行从电子邮件（webmail/邮件客户端）中删除的可执行内容（exe、dll、ps、js、vbs 等）。  
  - **仅审核**  

#### <a name="rules-to-protect-against-ransomware"></a>预防勒索软件的规则  

- **高级勒索软件防护**  
  默认值：未配置  
  规则：[对勒索软件启用高级防护](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware)  

  - 未配置   
  - **启用** - 使用激进的勒索软件防护。  
  - **仅审核**  

#### <a name="attack-surface-reduction-exceptions"></a>攻击面减少例外情况

- **要从攻击面减少规则中排除的文件和文件夹**  
  Defender CSP： [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - **导入**一个 .csv 文件，其中包含要从攻击面减少规则中排除的文件和文件夹。  
  - 手动**添加**本地文件或文件夹。  

> [!IMPORTANT]  
> 为了能够正确安装和执行 LOB Win32 应用，反恶意软件设置应不扫描以下目录：  
> **在 X64 客户端计算机上**：  
> C:\Program Files (x86)\Microsoft Intune Management Extension\Content   
> C:\windows\IMECache   
>  
> **在 X86 客户端计算机上**：  
> C:\Program Files\Microsoft Intune Management Extension\Content   
> C:\windows\IMECache   

### <a name="controlled-folder-access"></a>受控文件夹访问权限  

帮助[防止重要数据](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders)受到恶意应用和威胁（如勒索软件）的攻击。  

- **文件夹保护**  
  **默认值**：未配置  
  Defender CSP： [EnableControlledFolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  阻止不友好应用对文件和文件夹进行未经授权的更改。  

  - 未配置   
  - **启用**  
  - **仅审核**  
  - **阻止磁盘修改**  
  - **审核磁盘修改**  

  如果选择的配置不是 "*未配置*"，则可以配置：  
  - **有权访问受保护文件夹的应用列表**  
    Defender CSP： [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - **导入**包含应用列表的 .csv 文件。  
    - 手动**将应用添加**到此列表。  

  - **需要保护的其他文件夹的列表**  
    Defender CSP： [ControlledFolderAccessProtectedFolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - **导入**包含文件夹列表的 .csv 文件。  
    - 手动**将文件夹添加**到此列表。  

### <a name="network-filtering"></a>网络筛选  

阻止从任何应用到 IP 地址或域的出站连接，但信誉较低。 审核和阻止模式都支持网络筛选。  

- **网络保护**  
  **默认值**：未配置  
  Defender CSP： [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  此设置的目的是保护最终用户，使其能够访问 Internet 上的网页仿冒欺诈、利用中托管的网站和恶意内容。 它还阻止第三方浏览器连接到危险站点。  

  - **未配置** - 禁用此功能。 不会阻止用户和应用连接到危险域。 管理员不能在 Windows Defender 安全中心看到此活动。  
  - **启用**-启用网络保护，并阻止用户和应用连接到危险域。 管理员可在 Windows Defender 安全中心看到此活动。  
  - **仅审核**：-不阻止用户和应用连接到危险域。 管理员可在 Windows Defender 安全中心看到此活动。  

### <a name="exploit-protection"></a>Exploit Protection  
 

- **上传 XML**  
  **默认值**：未配置   

  若要使用利用防护来[保护设备免受攻击](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)，请创建一个包含所需的系统和应用程序缓解设置的 XML 文件。 可以通过两种方法来创建 XML 文件：  

  - *PowerShell* - 使用一个或多个 Get-ProcessMitigation、Set-ProcessMitigation 和 ConvertTo-ProcessMitigationPolicy PowerShell cmdlet    。 这些 cmdlet 配置缓解设置并导出它们的 XML 表示形式。  

  - *Windows Defender 安全中心 UI* - 在 Windows Defender 安全中心，单击“应用和浏览器”控件，然后向下滚动到所看到的屏幕底部，找到 Exploit Protection。 首先，使用“系统”设置和“程序”设置选项卡来配置缓解措施设置。 然后，找到屏幕底部的“导出”设置链接，导出其 XML 表示形式。  

- **用户编辑 exploit protection 接口**  
  **默认值**：未配置  
  ExploitGuard CSP： [ExploitProtectionSettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **阻止**-上传可用于配置内存、控制流和策略限制的 XML 文件。 XML 文件中的设置可用于阻止应用程序遭受攻击。  
  - **未配置**-不使用自定义配置。  

## <a name="windows-defender-application-control"></a>Windows Defender 应用程序控制  

选择需要审核的其他应用，或者可以信任它以由 Windows Defender 应用程序控件运行。 自动信任 Windows 组件和来自 Windows 应用商店的所有应用运行。  


- **应用程序控制代码完整性策略**  
  **默认值**：未配置  
   CSP： [APPLOCKER CSP](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **强制**-为用户的设备选择应用程序控制代码完整性策略。  
  
    在设备上启用“应用程序控制”后，只能通过将模式从“强制实施”  更改为“仅审核”  来禁用。 如果将模式从“强制实施”  更改为“不配置”  ，则会继续在分配的设备上强制执行“应用程序控制”。  

  - **未配置**-应用程序控制未添加到设备。 不过，先前添加的设置仍会在分配的设备上强制实施。 
 
  - **仅审核**-不阻止应用程序。 所有事件都记录在本地客户端的日志中。  

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard  

Windows Defender Credential Guard 可防止凭据盗窃攻击。 它可隔离密码，以便仅特权系统软件才可以进行访问。  

- **Credential Guard**  
  **默认值**：禁用  
  [DeviceGuard CSP](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **禁用** - 远程关闭 Credential Guard（如果之前已使用“无 UEFI 锁启用”选项启用）  。  

  - **使用 UEFI 锁启用** - 无法使用注册表项或组策略远程禁用 Credential Guard。  

    > [!NOTE]
    > 如果使用此设置，并且稍后想要禁用 Credential Guard，必须将组策略设置为“禁用”。  并且，从每台计算机以物理方式清除 UEFI 配置信息。 只要 UEFI 配置仍然存在，Credential Guard 就会保持启用状态。  

  - **无 UEFI 锁启用** - 允许使用组策略远程禁用 Credential Guard。 使用此设置的设备必须运行 Windows 10 1511 及更新的版本。  

  启用 Credential Guard 时，还会启用以下必需的功能  ：  
  
  - **基于虚拟化的安全** (VBS)  
    下次重新启动期间启用。 基于虚拟化的安全性使用 Windows 虚拟机监控程序提供对安全服务的支持。  
  - **安全启动和直接内存访问**  
    通过“安全启动”和直接内存访问 (DMA) 保护启用 VBS。 DMA 保护需要硬盘支持并且将仅在正确配置的设备上启用。  

## <a name="windows-defender-security-center"></a>Windows Defender 安全中心  

Windows Defender 安全中心作为独立应用或每个单项功能中的进程运行。 它通过“操作中心”显示通知。 它用作收集器或查看状态和为每个功能运行某项配置的一个位置。 有关详细信息，请参阅 [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) 文档。  

### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender 安全中心应用和通知  

阻止最终用户访问 Windows Defender 安全中心应用的各个区域。 隐藏某个部分还会阻止相关通知。  

- **病毒和威胁防护**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [DisableVirusUI](https://go.microsoft.com/fwlink/?linkid=873662)  

  配置最终用户是否可以在 Windows Defender 安全中心查看病毒和威胁防护区域。 隐藏此部分也会阻止与病毒和威胁防护相关的所有通知。  

  - 未配置   
  - **隐藏**  

- **勒索软件防护**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  配置最终用户是否可以在 Windows Defender 安全中心查看勒索软件防护区域。 隐藏此部分也会阻止与勒索软件保护相关的所有通知。  

  - 未配置   
  - **隐藏**  

- **帐户保护**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [DisableAccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  配置最终用户是否可以在 Windows Defender 安全中心查看帐户保护区域。 隐藏此部分也会阻止与帐户保护相关的所有通知。  

  - 未配置   
  - **隐藏**  

- **防火墙和网络保护**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  配置最终用户是否可以在 Windows Defender 安全中心查看防火墙和网络保护区域。 隐藏此部分也会阻止与防火墙和网络保护相关的所有通知。  

  - 未配置   
  - **隐藏**  

- **应用和浏览器控制**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [DisableAppBrowserUI](https://go.microsoft.com/fwlink/?linkid=873669)  

  配置最终用户是否可以在 Windows Defender 安全中心查看应用和浏览器控制区域。 隐藏此部分也会阻止与应用和浏览器控制相关的所有通知。  

  - 未配置   
  - **隐藏**  

- **硬件保护**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [DisableDeviceSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  配置最终用户是否可以在 Windows Defender 安全中心查看硬件保护区域。 隐藏此部分也会阻止与硬件保护相关的所有通知。  

  - 未配置   
  - **隐藏**  

- **设备性能和运行状况**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [DisableHealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  配置最终用户是否可以在 Windows Defender 安全中心查看设备性能和运行状况区域。 隐藏此部分也会阻止与设备性能和运行状况相关的所有通知。  
  
  - 未配置   
  - **隐藏**  

- **产品系列选项**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [DisableFamilyUI](https://go.microsoft.com/fwlink/?linkid=873673)  

  配置最终用户是否可以在 Windows Defender 安全中心查看 "家族选项" 区域。 隐藏此部分也会阻止与系列选项相关的所有通知。  
  
  - 未配置   
  - **隐藏**  

- **应用的显示区域中的通知**  
  **默认值**：未配置  
  WindowsDefenderSecurityCenter CSP： [DisableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  选择要向最终用户显示的通知。 非关键通知包括 Windows Defender 防病毒活动摘要（包括扫描完成时的通知）。 所有其他通知被视为是关键通知。  

  - 未配置   
  - **阻止非关键通知**  
  - **阻止所有通知**  

- **系统任务栏中的 Windows 安全中心图标**  
  **默认值**：未配置  

  配置通知区域控件的显示。 用户需要注销，然后登录或重新启动计算机，此设置才会生效。  
  
  - 未配置   
  - **隐藏**  

- **清除 TPM 按钮**  
  **默认值**：未配置  

  配置 "清除 TPM" 按钮的显示。  
  
  - 未配置   
  - **禁用**  

- **TPM 固件更新警告**  
  **默认值**：未配置  
  
  配置在检测到有漏洞的固件时，更新 TPM 固件的显示。  

  - 未配置   
  - **隐藏**  

- **篡改保护**  
  **默认值**：未配置

  启用或禁用设备上的防篡改保护。 若要使用防篡改保护，你必须将[Microsoft Defender 高级威胁防护与 Intune 集成](advanced-threat-protection.md)，并[企业移动性 + 安全性 E5 许可证](../fundamentals/licenses.md)。  
  - **未配置**-不会对设备设置进行任何更改。
  - **已启用-已启用**防篡改保护，并在设备上强制实施限制。
  - **禁用**-防篡改保护已关闭，并且不强制实施限制。

### <a name="it-contact-information"></a>IT 联系信息  

提供要在 Windows Defender 安全中心应用和应用通知中显示的 IT 联系信息。  

可以选择“在应用和通知中显示”、“仅在应用中显示”、“仅在通知中显示”或“不显示”     。 输入“IT 组织名称”和至少以下一项联系选项  ：  


- **IT 联系信息**  
  **默认值**：不显示  
  WindowsDefenderSecurityCenter CSP： [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  配置向最终用户显示 IT 联系人信息的位置。  
  
  - **在应用和通知中显示**  
  - **仅在应用中显示**  
  - **仅在通知中显示**  
  - **不显示**  

  配置为显示时，可以配置以下设置：  

  - **IT 组织名称**  
    **默认值**：未配置   
    WindowsDefenderSecurityCenter CSP：[公司名称](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **IT 部门的电话号码或 Skype ID**  
    **默认值**：未配置   
    WindowsDefenderSecurityCenter CSP：[手机](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **IT 部门的电子邮件地址**  
    **默认值**：未配置   
    WindowsDefenderSecurityCenter CSP：[电子邮件](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **IT 支持网站 URL**  
    **默认值**：未配置   
    WindowsDefenderSecurityCenter CSP： [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>本地设备安全选项  

使用这些选项可配置 Windows 10 设备上的本地安全设置。  

### <a name="accounts"></a>帐户  

- **添加新的 Microsoft 帐户**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **阻止** - 阻止用户向此设备添加新的 Microsoft 帐户。  
  - **未配置**-用户可以在设备上使用 Microsoft 帐户。  

- **免密码远程登录**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **阻止** - 仅允许带空白密码的本地帐户使用设备键盘进行登录。  
   - **未配置** - 允许带空白密码的本地帐户从物理设备之外的其他位置登录。  

#### <a name="admin"></a>管理员  

- **本地管理员帐户**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **块**禁止使用本地管理员帐户。  
  - 未配置   

- **重命名管理员帐户**  
  **默认值**：未配置   
  LocalPoliciesSecurityOptions CSP： [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  定义与“管理员”帐户的安全标识符 (SID) 关联的其他帐户名称。  

 #### <a name="guest"></a>Guest  

- **来宾帐户**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [LocalPoliciesSecurityOptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **阻止**-防止使用来宾帐户。  
  - 未配置   

- **重命名来宾帐户**  
  **默认值**：未配置   
  LocalPoliciesSecurityOptions CSP： [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  定义与“来宾”帐户的安全标识符 (SID) 关联的其他帐户名称。  

### <a name="devices"></a>设备  

- **免登录移除设备**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **阻止** - 用户可以按下已插接便携设备的物理弹出按钮，从而安全地移除该设备。  
  - **未配置**-用户必须登录到该设备，并接收对该设备的脱开的权限。  

- **为共享打印机安装打印机驱动程序**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **启用** - 任何用户都能在连接到共享打印机的过程中安装打印机驱动程序。  
  - **未配置** - 只有管理员可以在连接到共享打印机的过程中安装打印机驱动程序。  

- **限制对本地活动用户的 CD-ROM 访问**  
  **默认值**：未配置  
  CSP： [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **启用** - 仅允许以交互方式登录的用户使用 CD-ROM 媒体。 如果启用此策略，并且没有以交互方式登录的用户，则会通过网络访问 CD-ROM。  
  - **未配置**-任何人都有权访问 cd-rom。  

- **格式化和弹出可移动媒体**  
  **默认值**： Administrators  
  CSP： [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  定义可以格式化和弹出可移动 NTFS 媒体的用户：  
  - 未配置   
  - **管理员**  
  - **管理员和超级用户**  
  - **管理员和交互式用户**  

### <a name="interactive-logon"></a>交互式登录  

- **激活屏幕保护程序前锁屏界面保持不活动状态的分钟数**  
  **默认值**：未配置   
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  输入屏幕保护程序启动前，交互式桌面的登录屏幕保持不活动状态的最长分钟数。 (**0** - **99999**)  

- **需要按 CTRL+ALT+DEL 登录**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **启用** - 用户不需要按 CTRL+ALT+DEL 登录。  
  - **未配置** - 用户需要在登录 Windows 之前按 CTRL+ALT+DEL。  

- **智能卡移除行为**  
  **默认值**：锁定工作站   
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  确定从智能卡读卡器中取下登录用户的智能卡时发生的情况。 选项包括：  

  - **锁定工作站** - 取下智能卡时锁定工作站。 使用此选项，用户可以携带智能卡离开该区域，并维持受保护的会话。  
  - **无操作**  
  - **强制注销** - 取下智能卡时自动注销用户。  
  - **如果是远程桌面服务会话，则断开连接** - 取下智能卡会断开会话，但不会注销用户。 使用此选项，用户可以稍后插入智能卡并恢复会话，或者在另一台配备智能卡读卡器的计算机上恢复会话，而无需再次登录。 如果是本地会话，则此策略与“锁定工作站”的功能相同。  

#### <a name="display"></a>显示器  

- **锁定屏幕上的用户信息**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  配置会话锁定时显示的用户信息。 如果未配置，则显示用户显示名称、域和用户名。  

  - 未配置   
  - **用户显示名称、域和用户名**  
  - **仅限用户显示名称**  
  - **不显示用户信息**  

- **隐藏上次登录的用户**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **启用**-隐藏用户名。  
  - **未配置**-显示最后一个用户名。  

- **登录时隐藏用户名**
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **启用**-隐藏用户名。  
  - **未配置**-显示最后一个用户名。  

- **登录消息标题**  
  **默认值**：未配置   
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  设置登录用户的消息标题。  

- **登录消息正文**  
  **默认值**：未配置   
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  设置登录用户的消息正文。  
  
### <a name="network-access-and-security"></a>网络访问和安全性

- **匿名访问命名管道和共享**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **未配置** - 限制对共享和命名管道设置的匿名访问。 适用于可以匿名访问的设置。  
  - **阻止**-禁用此策略，使匿名访问可用。  

- **SAM 帐户的匿名枚举**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **未配置**-匿名用户可以枚举 SAM 帐户。  
  - **阻止** - 阻止匿名枚举软件资产管理帐户。  

- **匿名枚举 SAM 帐户和共享**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **未配置** - 匿名用户可以枚举域帐户和网络共享的名称。  
  - **阻止** - 阻止匿名枚举软件资产管理帐户和共享。 

- **密码更改时存储 LAN 管理器哈希值**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  确定在下一次更改密码时是否存储密码的哈希值。 
  - **未配置**-哈希值未存储  
  - **阻止**-LAN MANAGER （LM）存储新密码的哈希值。  

- **PKU2U 身份验证请求**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **未配置**-允许 PU2U 请求。  
  - **Block** -阻止 PKU2U 对设备的身份验证请求。  

- **将远程 RPC 连接限制为 SAM**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **未配置**-使用默认的安全描述符，它可能允许用户和组向 SAM 发出远程 RPC 调用。
  - **允许**-拒绝用户和组对存储用户帐户和密码的安全帐户管理器（SAM）进行远程 RPC 调用。 "**允许**" 还允许您更改默认安全描述符定义语言（SDDL）字符串，以显式允许或拒绝用户和组进行这些远程调用。  

    - **安全描述符**  
      **默认值**：未配置   
    
- **基于 NTLM SSP 的客户端的最低会话安全性**  
  **默认值**：无  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  此安全设置允许服务器要求对 128 位加密和/或 NTLMv2 会话安全性进行协商。  

  - **无**  
  - **需要 NTLMv2 会话安全性**  
  - **需要 128 位加密**  
  - **NTLMv2 和 128 位加密**  
 
- **基于 NTLM SSP 的服务器的最低会话安全性**  
  **默认值**：无  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  此安全设置确定用于网络登录的质询/响应身份验证协议。  

  - **无**  
  - **需要 NTLMv2 会话安全性**  
  - **需要 128 位加密**  
  - **NTLMv2 和 128 位加密**  

- **LAN 管理器身份验证级别**  
  **默认值**： LM 和 NTLM  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM 和 NTLM**  
  - **LM、NTLM 和 NTLMv2**  
  - **NTLM**  
  - **NTLMv2**  
  - **NTLMv2 而非 LM**  
  - **NTLMv2 而非 LM 或 NTLM**  
  
- **不安全的来宾登录**  
  **默认值**：未配置  
  LanmanWorkstation CSP： [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  如果启用此设置，SMB 客户端将拒绝不安全的来宾登录。  

  - 未配置   
  - **阻止**-SMB 客户端拒绝不安全的来宾登录。  

### <a name="recovery-console-and-shutdown"></a>恢复控制台和关闭  

- **在关闭时清除虚拟内存页面文件**  
  **默认值**：未配置  
   LocalPoliciesSecurityOptions CSP： [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **启用** - 在设备关机时清除虚拟内存页面文件。  
  - **未配置** - 不会清除虚拟内存。  

- **免登录关闭**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **阻止** - 隐藏 Windows 登录屏幕上的关闭选项。 用户必须登录设备才能关闭。  
  - **未配置** - 允许用户从 Windows 登录屏幕关闭设备。  

### <a name="user-account-control"></a>用户帐户控制  

- **无安全位置的 UIA 完整性**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - **块**-位于文件系统中的安全位置的应用将仅使用 UIAccess 完整性运行。  
  - **未配置** - 让应用按 UIAccess 完整性运行，即使应用不在文件系统中的安全位置。  

- **将文件和注册表写入错误虚拟化到每用户位置**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **启用** - 将数据写入受保护位置的应用程序将会无法执行。  
  - **未配置** - 在运行时将应用程序写入错误重定向到文件系统和注册表的已定义用户位置。  

- **只提升已签名并验证的可执行文件**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **启用** - 在运行可执行文件之前，强制对其执行 PKI 证书路径验证。  
  - **未配置** - 在某个可执行文件可以运行之前不会强制对其执行 PKI 证书路径验证。  

#### <a name="uia-elevation-prompt-behavior"></a>UIA 提升提示行为  

- **管理员的提升提示**  
  **默认值**：非 Windows 二进制文件的同意提示  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  在管理员批准模式下定义管理员的提升提示行为。  

  - 未配置   
  -  不提示，直接提升  
  -  在安全桌面上提示凭据  
  -  提示凭据  
  -  同意提示  
  - **非 Windows 二进制文件的同意提示**  


- **标准用户的提升提示**  
  **默认值**：提示提供凭据  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  定义标准用户的提升提示行为。  

  - 未配置   
  -  自动拒绝提升请求  
  -  在安全桌面上提示凭据  
  -  提示凭据  

- **将提升权限提示路由到用户的交互式桌面**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **已启用**-所有提升请求都将转向交互式用户的桌面，而不是安全桌面。 使用针对管理员和标准用户的任何提示行为策略设置。  
  - **未配置** - 无论针对管理员和标准用户的提示行为策略如何设置，所有提升权限请求都会强制转到安全桌面。

- **应用安装的提升权限提示**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **启用** - 不检测应用程序安装包或提示提升权限。
   - **未配置** - 当某个应用程序安装包需要提升权限时，将提示用户输入管理用户名和密码。

- **在不使用安全桌面的情况下提示 UIA 提升权限**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **启用** - 允许 UIAccess 应用在不使用安全桌面的情况下提示提升权限。  
- **未配置**-提升提示使用安全桌面。  

#### <a name="admin-approval-mode"></a>管理员批准模式  

- **内置管理员的管理员批准模式**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **启用** - 允许内置管理员帐户使用管理员批准模式。 任何需要提升权限的操作都将提示用户批准该操作。  
  - **未配置** - 以完整的管理员权限运行所有应用。  

- **以管理员批准模式运行所有管理员**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **已启用**-启用管理员批准模式。  
  - **未配置** - 禁用管理员批准模式以及所有相关的 UAC 策略设置。  

### <a name="microsoft-network-client"></a>Microsoft 网络客户端  

- **对通信进行数字签名(若服务器允许)**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  确定 SMB 客户端是否协商 SMB 数据包签名。  
  - **阻止**-smb 客户端从不协商 smb 数据包签名。
  - **未配置** - Microsoft 网络客户端请求服务器在设置会话时执行 SMB 数据包签名。 如果在服务器上启用了数据包签名，则会协商数据包签名。  

- **将未加密的密码发送到第三方 SMB 服务器**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **阻止** - 服务器消息块 (SMB) 重定向程序可以将明文密码发送给在身份验证期间不支持密码加密的非 Microsoft SMB 服务器。  
  - **未配置**-阻止发送纯文本密码。 密码已加密。  

- **对通信进行数字签名(始终)**  
  **默认值**：未配置  
  LocalPoliciesSecurityOptions CSP： [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **启用** - Microsoft 网络客户端不会与 Microsoft 网络服务器进行通信，除非该服务器接受 SMB 数据包签名。  
  - **未配置**-在客户端和服务器之间协商 SMB 数据包签名。  

### <a name="microsoft-network-server"></a>Microsoft 网络服务器  
  
- **对通信进行数字签名(如果客户端允许)**  
  **默认值**：未配置  
  CSP： [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **启用** - Microsoft 网络服务器根据客户端的请求协商 SMB 数据包签名。 也就是说，如果在客户端上启用了数据包签名，则会协商数据包签名。  
  - **未配置**-smb 客户端从不协商 smb 数据包签名。  

- **对通信进行数字签名(始终)**  
  **默认值**：未配置  
  CSP： [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **启用** - Microsoft 网络服务器不会与 Microsoft 网络客户端进行通信，除非该客户端接受 SMB 数据包签名。  
  - **未配置**-在客户端和服务器之间协商 SMB 数据包签名。  

## <a name="xbox-services"></a>Xbox 服务

- **Xbox 游戏保存任务**  
  **默认值**：未配置  
  CSP： [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  此设置确定是否启用或禁用 Xbox 游戏保存任务。  
  - **Enabled**
  - 未配置 

- **Xbox 附件管理服务**  
  **默认值**：手动  
  CSP： [SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  此设置确定附件管理服务的启动类型。  
  - **手动**
  - **自动**
  - **禁用**

- **Xbox Live 身份验证管理器服务**  
  **默认值**：手动  
  CSP： [SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  此设置确定实时身份验证管理器服务的启动类型。  
  - **手动**
  - **自动**
  - **禁用**
 
- **Xbox Live 游戏保存服务**  
  **默认值**：手动  
  CSP： [SystemServices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  此设置确定实时游戏保存服务的启动类型。  
  - **手动**
  - **自动**
  - **禁用**

- **Xbox Live 网络服务**  
  **默认值**：手动  
  CSP： [SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  此设置确定网络服务的启动类型。  
  - **手动**
  - **自动**
  - **禁用**

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](../configuration/device-profile-assign.md)并[监视其状态](../configuration/device-profile-monitor.md)。  

在 [macOS](endpoint-protection-macos.md) 设备上配置 Endpoint Protection 设置。  
