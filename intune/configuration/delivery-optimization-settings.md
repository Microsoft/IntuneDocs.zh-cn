---
title: Intune 的 Windows 10 传递优化设置
titleSuffix: Microsoft Intune
description: 可以使用 Intune 部署的适用于 Windows 10 设备的传递优化设置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81d0ff389acd2c7014b830bb7c24e336088c4f96
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506885"
---
# <a name="delivery-optimization-settings-for-intune"></a>Intune 的传递优化设置

本文针对运行 Windows 10 或更高版本的设备列出了 Intune 支持的传递优化设置。  

Intune 控制台中的大多数选项都直接映射到传递优化设置，Windows 文档中对此内容进行了深入的介绍并为其提供了相关内容的链接。  Intune 特有的设置或选项不包含指向其他内容的链接。  

下表包括：  

- **设置**：该设置与 Intune 中显示的设置一样。 链接设置打开 Windows 文档中[配置 Windows 10 更新传递优化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)的相关条目，可以在其中了解有关该设置的详细信息。

- **Windows 版本**：包括支持此设置的 Windows 10 最低版本。  

- **详细信息**：Intune 实现设置（包括 Intune 默认设置）的简要说明。 如果可用，则会有指向[传递优化策略配置服务提供程序](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization) (CSP) 条目的链接。  

要配置 Intune 以使用这些设置，请参阅[传递更新](delivery-optimization-windows.md)。  

## <a name="delivery-optimization"></a>传递优化  

|设置  |Windows 版本  |详细信息  |
|---------|-----------------|---------|
| [下载模式](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#download-mode)     | 1511         | 指定传递优化用于下载内容的下载方法。<br><ul><li>**未配置**：最终用户使用自己的方法更新其设备，可能使用的是 Windows 更新或操作系统提供的传递优化设置  。 </li> <li> **仅 HTTP，无对等互连 (0)** ：仅从 Internet 获取更新。 请勿从网络上的其他计算机（对等互联）获取更新。 </li> <li> **HTTP 与同一 NAT 背后的对等互连混合 (1)** ：从 Internet 和网络上的其他计算机获取更新。 </li> <li> **HTTP 与专用组间的对等互连混合 (2)** ：对等互连在同一 Active Directory 站点（如果存在）或同一域中的设备上发生。 在选中此选项后，在整个网络地址转换 (NAT) IP 地址中进行对等互连。 </li> <li> **与 Internet 对等互连混合的 HTTP (3)** ：从 Internet 和网络上的其他计算机获取更新。 </li> <li> **无对等互连的简单下载模式 (99)** ：直接从更新所有者（如 Microsoft）通过 Internet 获取更新。 它不会联系传递优化云服务。 </li> <li> **Bypass 模式 (100)** ：使用后台智能传送服务 (BITS) 获取更新。 请勿使用传递优化。 </li></ul> **默认值**：未配置  <br><br> 策略 CSP：[DODownloadMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)  <br><br>  |
| [限制对等选择](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-a-method-to-restrict-peer-selection)          | 1803        | 必须将“下载模式”设置为“HTTP 与同一 NAT 背后的对等互连混合 (1)”或“HTTP 与专用组间的对等互连混合 (2)”    。<br/><br/>将对等选择限制为特定的设备组。<br/><br/>**默认值**：未配置 <br/><br/>策略 CSP：[DORestrictPeerSelectionBy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dorestrictpeerselectionby)<br><br>      |
| [组 ID 源](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-the-source-of-group-ids)     | 1803        | 必须将“下载模式”设置为“HTTP 与专用组间的对等互连混合”   。<br><br>根据来源将对等选择限制为特定的设备组。<br><br>如果选择“自定义”，则需配置“组 ID（作为 GUID）”   。 如果需要为位于不同域或不在同一 LAN 上的分支创建本地网络对等互连的单个组，请使用 GUID 作为组 ID。<br><br>**默认值**：未配置 <br><br>策略 CSP：[DOGroupId](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dogroupid)     |

## <a name="bandwidth"></a>带宽  

|设置  |Windows 版本  |详细信息  |
|---------|---------|---------|
|带宽优化类型     | 查看详情         | 选择 Intune 如何确定传递优化可在所有并发下载活动中使用的最大带宽。<br><br>选项包括：<br><ul><li>未配置 </li><br><li>**绝对值** - 指定设备可以在其所有并发传递优化下载活动中使用的[最大下载带宽（以 KB/秒为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-download-bandwidth)和[最大上传带宽（以 KB/秒为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-upload-bandwidth)。<br><br>要求使用 Windows 1607<br><br>策略 CSP：[DOMaxDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxdownloadbandwidth) 和 [DOMaxUploadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxuploadbandwidth)</li><br><li>**百分比** - 指定设备可以在其所有并发传递优化下载活动中使用的[最大前台下载带宽（以百分比为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth)和[最大后台下载带宽（以百分比为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth)。<br><br>要求使用 Windows 1803<br><br>策略 CSP：[DOPercentageMaxForegroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth) 和 [DOPercentageMaxBackgroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)    <br><br><li>**营业时间百分比** - 要获得最大[前台](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-foreground-download-bandwidth)下载带宽和最大[后台](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-background-download-bandwidth)下载带宽，请配置营业时间的开始和结束时间，然后配置在营业时间内外使用的带宽百分比。 <br><br>要求使用 Windows 1803 <br><br>策略 CSP：[DOSetHoursToLimitBackgroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth) 和 [DOSetHoursToLimitForegroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)<br><br>   |
|[延迟后台 HTTP 下载（以秒为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-background-download-from-http-in-secs) | 1803        | 此设置用于配置通过 HTTP 延迟后台下载内容的最长时间。 这仅适用于支持对等互联下载源的下载。 在此延迟期间，设备将搜索附带可用内容的对等。 最终用户在等待对等源时，下载似乎会停滞。   <br><br>**默认值**：没有配置任何值   <br><br>**建议值**：60 秒   <br><br>策略 CSP：[DODelayBackgroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaybackgrounddownloadfromhttp) <br><br>    |
| [延迟前台 HTTP 下载（以秒为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-foreground-download-from-http-in-secs)      | 1803       | 配置通过 HTTP 延迟前台（交互式）下载内容的最长时间。 这仅适用于支持对等互联下载源的下载。 在此延迟期间，设备将搜索附带可用内容的对等。 最终用户在等待对等源时，下载似乎会停滞。   <br><br>**默认值**：没有配置任何值   <br><br>**建议值**：60 秒   <br><br>策略 CSP：[DODelayForegroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelayforegrounddownloadfromhttp) <br><br>         |


## <a name="caching"></a>正在缓存  

|设置  |Windows 版本  |详细信息  |
|---------|---------|---------|
|[对等缓存所需的最小 RAM（以 GB 为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-ram-inclusive-allowed-to-use-peer-caching)      | 1703        | 指定设备使用对等缓存必须具有的最小 RAM 大小（以 GB 为单位）。 <br><br>**默认值**：没有配置任何值   <br><br>**建议**：4 GB <br><br>策略 CSP：[DOMinRAMAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominramallowedtopeer) <br><br>        |
|[对等缓存所需的最小磁盘大小（以 GB 为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-disk-size-allowed-to-use-peer-caching)      | 1703        | 指定设备使用对等缓存必须具有的最小磁盘大小（以 GB 为单位）。 <br><br>**默认值**：没有配置任何值   <br><br>**建议**：32 GB   <br><br>策略 CSP：[DOMinDiskSizeAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domindisksizeallowedtopeer) <br><br>    |
|[对等缓存的最小内容文件大小（以 MB 为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-peer-caching-content-file-size)      | 1703        | 指定文件使用对等缓存必须达到或超过的最小大小（以 MB 为单位）。  <br><br>**默认值**：没有配置任何值   <br><br>**建议**：10 MB   <br><br>策略 CSP：[DOMinFileSizeToCache](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominfilesizetocache)  <br><br>      |
|[上传所需的最低电池剩余电量（以百分比为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level)      | 1709        | 以百分比形式指定设备将数据上传到对等所必须具有的最低电池剩余电量。 如果电池剩余电量下降到指定值，则任何活动上传都会自动暂停。   <br><br>**默认值**：没有配置任何值   <br><br>**建议**：40%   <br><br>策略 CSP：[DOMinBatteryPercentageAllowedToUpload](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominbatterypercentageallowedtoupload) <br><br>        |
|[修改缓存驱动器](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#modify-cache-drive)        | 1607        | 指定传递优化用于其缓存的驱动器。 可以使用环境变量、驱动器号或完整路径。  <br><br>**默认值**：%SystemDrive% <br><br>策略 CSP：[DOModifyCacheDrive](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domodifycachedrive) <br><br>        |
| [最长缓存期限（以天为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-cache-age)    | 1511         | 指定每个文件成功下载后，文件在设备的传递优化缓存中保存的期限。   <br><br>使用 Intune 配置缓存期限（以天为单位）。 定义的天数转换为相应秒数，这是 Windows 定义此设置的方式。 例如，Intune 配置为 3 天，在设备上会转换为 259200 秒（3 天）。  <br><br>**默认值**：没有配置任何值      <br><br>**建议**：7   <br><br>策略 CSP：[DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)  <br><br>          |
| 最大缓存大小类型  | 查看详情     | 选择如何管理传递优化使用的设备上的磁盘空间量。 如果未配置缓存大小，则默认为可用磁盘空间的 20%。  <br><ul><li>**未配置**（默认）</li><br><li>**绝对值** - 指定[最大缓存绝对大小（以 GB 为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#absolute-max-cache-size)，以配置设备可用于传递优化的最大驱动器空间量。 如果将其设置为 0（零），缓存大小将不受限制，但是当设备磁盘空间不足时，传递优化将清除缓存。 <br><br>要求使用 Windows 1607<br><br> 策略 CSP：[DOAbsoluteMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-doabsolutemaxcachesize) </li><br><li>**百分比** - 指定[最大缓存大小（以百分比为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-cache-size)，以配置设备可用于传递优化的最大驱动器空间量。 百分比是可用的驱动器空间，并且传递优化会不断评估可用的驱动器空间，并清除缓存以使最大缓存大小低于设置的百分比。 <br><br>要求使用 Windows 1511<br><br>策略 CSP：[DOMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcachesize)  |
| [VPN 对等缓存](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#enable-peer-caching-while-the-device-connects-via-vpn)  | 1709  | 选择“启用”可以将设备配置为在通过 VPN 连接到域网络时参与对等缓存  。 启用的设备可以从 VPN 或公司域网络上下载或上传到其他域网络设备。  <br><br>**默认值**：未配置  <br><br>策略 CSP：[DOAllowVPNPeerCaching](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)    |

## <a name="local-server-caching"></a>本地服务器缓存  

|设置  |Windows 版本  |详细信息  |
|---------|-----------------|---------|
|缓存服务器主机名 | 1809  |指定设备将用于传递优化的网络缓存服务器的 IP 地址或 FQDN，然后选择 "**添加**" 将该项添加到列表中。  <br><br>**默认值**：未配置  <br><br>策略 CSP： [DOCacheHost](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-docachehost)  |
|[延迟前台下载缓存服务器回退（秒）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-foreground-download-cache-server-fallback-in-secs) | 1903    |指定一个时间0-2592000 （以秒为单位），以将缓存服务器的回退延迟到用于前台内容下载的 HTTP 源。 当策略延迟从 http 进行前台下载时，它将首先应用（以允许从对等机下载）。 (0-2592000)    <br><br>**默认值**：0  <br><br>策略 CSP [DODelayCacheServerFallbackForeground](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaycacheserverfallbackforeground)  |
|[延迟后台下载缓存服务器回退（秒）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-background-download-cache-server-fallback-in-secs) | 1903    |指定一个时间0-2592000 （以秒为单位），以将缓存服务器的回退延迟到 HTTP 源以获取背景内容下载。 配置*延迟后台 HTTP 下载（以秒为单位）* 后，该设置将首先应用于允许来自对等方的下载。 (0-2592000)   <br><br>**默认值**：0 <br><br>策略 CSP： [DODelayCacheServerFallbackBackground](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaycacheserverfallbackbackground)  |


## <a name="next-steps"></a>后续步骤

[在 Intune 中配置传递优化](delivery-optimization-windows.md)
