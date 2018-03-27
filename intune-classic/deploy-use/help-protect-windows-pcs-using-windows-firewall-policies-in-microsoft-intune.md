---
title: 适用于 Windows 电脑的防火墙策略
description: Intune 可通过多种方式帮助你保护使用 Intune 客户端管理的电脑，其中包括帮助你配置 Windows 防火墙设置。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3be77c1042d695ed0bed6ee7cbbc442342e91d8b
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>在 Microsoft Intune 中使用 Windows 防火墙策略帮助保护 Windows PC

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可通过多种方式帮助你保护使用 Intune 客户端管理的 Windows 电脑。 其中的一种方法是提供使你能够在电脑上配置 Windows 防火墙设置的策略。

如果你尚未在计算机上安装 Intune Windows 电脑客户端，请参阅[使用 Microsoft Intune 安装 Windows 电脑客户端](install-the-windows-pc-client-with-microsoft-intune.md)。

以下各部分的信息可帮助你在 Windows 电脑上配置和部署 Windows 防火墙策略并进行监视。

## <a name="use-intune-policies-to-manage-windows-firewall"></a>使用 Intune 策略来管理 Windows 防火墙
利用 Windows 防火墙策略，你能够创建和部署用于在被管理的电脑上控制 Windows 防火墙的设置。 你无法管理 Windows 防火墙的自定义例外，这些设置不影响第三方防火墙。

> [!NOTE]
> 如果将 Microsoft Intune 策略和组策略都配置为管理 PC 上的相同设置，则组策略设置将替代 Microsoft Intune 策略。 有关如何避免 Intune 策略与组策略之间的冲突的信息，请参阅[解决 GPO 与 Microsoft Intune 之间的策略冲突](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。
>
> 如果你想要将 Windows 防火墙设置部署到运行 Windows Vista 的计算机，则必须先安装[热修复补丁 KB971800](http://support2.microsoft.com/kb/971800) 到这些计算机上。

> [!IMPORTANT]
> 若要使用 Intune 管理 Windows 防火墙，请确保在要托管的计算机上启用以下两项服务：
>
> -   Windows 防火墙
> -   IPsec 策略代理

## <a name="configure-a-windows-firewall-policy"></a>配置 Windows 防火墙策略

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择“策略”&gt;“添加策略”。

2.  配置和部署 **Windows 防火墙设置**策略。 你可以使用建议的设置，或对设置进行自定义。 如果你需要有关如何创建和部署策略的详细信息，请参阅[使用 Microsoft Intune 计算机客户端的常见 Windows 电脑管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。

    以下部分列出你可在策略中配置的值，还列出将在你未自定义策略的情况下使用的默认值。

部署 Windows 防火墙策略之后，你可以在“策略”工作区的“所有策略”页上查看其状态。

## <a name="specify-policy-settings-for-windows-firewall"></a>指定 Windows 防火墙策略设置

### <a name="turn-on-windows-firewall"></a>启用 Windows 防火墙

这些策略设置允许在托管的计算机上启用 Windows 防火墙，这些托管的计算机：
- 连接到域（例如，在工作区）
- 连接到专用（受信任的）网络（例如家庭网络）
- 连接到不受信任的公用网络（例如咖啡店）

以上每个设置的默认值都是“是”，这是最安全的值。



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>阻止所有传入连接，包括位于允许程序列表中的程序

这些策略设置在托管的计算机上配置 Windows 防火墙以阻止传入网络流量，这些托管的计算机：
- 连接到域（例如，在工作区）
- 连接到专用（受信任的）网络（例如家庭网络）
- 连接到不受信任的公用网络（例如咖啡店）

以上每个设置的默认值都是“是”，这是最安全的值。

> [!IMPORTANT]
> 如果你的环境中包括运行 Windows Vista（未安装 Service Pack）的被管理的计算机，则必须安装与 Microsoft 知识库[文章 971800](http://go.microsoft.com/fwlink/?LinkId=188405) 相关的更新，或在部署到这些计算机的策略中禁用“阻止所有传入连接”策略设置。

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>Windows 防火墙阻止新程序时通知用户

当托管的计算机为以下情况时，Windows 防火墙将在阻止传入网络流量时决定是否通知电脑用户：
- 连接到域（例如，在工作区）
- 连接到专用（受信任的）网络（例如家庭网络）
- 连接到不受信任的公用网络（例如咖啡店）

以上每个设置的默认值都是“是”。


### <a name="configure-predefined-exceptions"></a>配置预定义的例外

你可以配置例外以允许特定类型的网络流量通过防火墙，而无需考虑先前配置的值。 默认情况下，不会配置其中任何设置。

|设置名|详细信息|
|------------------|--------------------|
|**BranchCache - 内容检索**<br>（Windows 7 或更高版本）|允许 BranchCache 客户端使用 HTTP 从分布模式中的另一个 BranchCache 客户端以及从托管缓存模式中的托管缓存中检索内容。 此设置使用 HTTP。|
|**BranchCache - 托管缓存客户端**<br>（Windows 7 或更高版本）|允许 BranchCache 客户端使用托管缓存。 此设置使用 HTTPS。|
|**BranchCache - 托管缓存服务器**|允许 BranchCache 客户端使用托管缓存来与其他客户端通信。 此设置使用 HTTPS。|
|**BranchCache - 对等机发现**<br>（Windows 7 或更高版本）|允许 BranchCache 客户端使用 Web 服务动态发现 (WS-Discovery) 协议在本地子网上查看内容可用性。|
|**BITS 对等缓存**|允许客户端使用后台智能传输服务 (BITS) 在同一子网中的客户端上查找和共享存储在 BITS 缓存中的文件。 此设置使用基于设备的 Web 服务 (WSDAPI) 和远程过程调用 (RPC)。|
|**连接到网络投影仪**|允许用户通过有线网络或无线网络连接到投影仪以投影演示文稿。 此设置使用 WSDAPI。|
|**核心网络**|允许客户端使用 IPv4 和 IPv6 连接到网络资源。|
|**分布式事务处理协调器**|启用被管理的计算机以协调用于更新受事务保护的资源（如数据库、消息队列和文件系统）的事务。|
|**文件和打印机共享**|允许用户与网络上的其他用户共享本地文件和打印机。 此设置使用 NetBIOS、链路本地多播名称解析 (LLMNR)、服务器消息块 (SMB) 协议和 RPC。|
|**家庭组**<br>（Windows 7 或更高版本）|启用被管理的计算机以加入家庭组网络。|
|**iSCSI 服务**|启用被管理的计算机以连接到 iSCSI 服务器和设备。|
|**密钥管理服务**|在企业环境中针对许可证合规性对计算机进行计数。|
|**Media Center Extender**|启用 Media Center Extenders 以与运行 Windows Media Center 的计算机进行通信。 此设置使用简单服务发现协议 (SSDP) 和 qWave。|
|**Netlogon 服务**|配置域客户端与域控制器之间用于验证用户和服务的安全通道。 此设置使用 RPC。|
|**网络发现**|允许计算机发现其他设备以及被网络上的其他设备发现。 此设置使用功能发现主机和发布服务以及 SSDP、NetBIOS、LLMNR 和 UPnP 网络协议。|
|**性能日志和警报**|允许以远程方式管理性能日志和警报服务。 此设置使用 RPC。|
|**远程管理**|允许对计算机进行远程管理。|
|**远程协助**|允许被管理的计算机的用户向网络上的其他用户请求远程协助。 此设置使用 SSDP、对等名称解析协议 (PNRP)、Teredo 和 UPnP 网络协议。|
|**远程桌面**|允许计算机使用远程桌面来访问其他计算机。|
|**远程事件日志管理**|允许以远程方式查看和管理客户端事件日志。 此设置使用命名管道和 RPC。|
|**远程计划任务管理**|启用对任务计划服务的远程管理。 此设置使用 RPC。|
|**远程服务管理**|启用对客户端上的本地服务的远程管理。 此设置使用命名管道和 RPC。|
|**远程卷管理**|启用远程软件和硬件磁盘卷管理。 此设置使用 RPC。|
|**路由和远程访问**|启用进入计算机的传入 VPN 和远程访问连接。|
|**安全套接字隧道协议**|启用使用安全套接字隧道协议 (SSTP) 进入被管理的计算机的传入 VPN 连接。 此设置使用 HTTPS。|
|**SNMP 陷阱**|允许被管理的计算机接收简单网络管理协议 (SNMP) 陷阱服务流量。|
|**UPnP 框架**|在计算机上配置 UPnP 框架服务，以允许这些计算机发现和使用 UPnP 认证设备。|
|**Windows 协作计算机名注册服务**|允许计算机通过使用 SSDP 和 PNRP 查找其他计算机并与之通信。|
|**Windows Media Player**|允许用户通过用户数据报协议 (UDP) 接收流媒体。|
|**Windows Media Player 网络共享服务**|允许用户通过网络共享媒体。 此设置使用 SSDP、qWave 和 UPnP 网络协议。|
|**Windows Media Player 网络共享服务(Internet)**<br>（Windows 7 或更高版本）|允许用户通过 Internet 共享家庭媒体。|
|**Windows 会议室**|允许用户通过网络进行协作以共享文档、程序及其桌面。 此设置使用分布式文件系统复制 (DFSR) 和 P2P。|
|**Windows 对等协作基础**|配置各种对等程序和技术以允许它们连接。 此设置使用 SSDP 和 PNRP。|
|**Windows 远程管理(兼容性)**|启用使用 WS-Management（一种基于 Web 服务的协议，用于远程管理操作系统和设备）对被管理的计算机进行远程管理。|
|**Windows 远程管理**<br>（Windows 8 或更高版本）|启用使用 WS-Management（一种基于 Web 服务的协议，用于远程管理操作系统和设备）对被管理的计算机进行远程管理。|
|**Windows Virtual PC**<br>（Windows 7 或更高版本）|允许虚拟机与其他计算机通信。|
|**无线便携设备**|启用使用媒体传输协议 (MTP) 从启用网络的照相机或媒体设备向被管理的计算机传输媒体。 此设置使用 SSDP 和 UPnP 网络协议。|

### <a name="see-also"></a>另请参阅
[保护 Windows 电脑的策略](policies-to-protect-windows-pcs-in-microsoft-intune.md)
