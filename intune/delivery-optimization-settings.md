---
title: Intune 的 Windows 10 传递优化设置 |Microsoft Docs
description: 你可以使用 Intune 部署的 Windows 10 设备的传递优化设置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6e90828da8c209b534b830af7fe522b254374bf
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57695273"
---
# <a name="delivery-optimization-settings-for-intune"></a>Intune 的交付优化设置

本文列出了 Intune 支持的运行 Windows 10 或更高版本的设备的传递优化设置。  

在 Intune 控制台中的大多数选项直接映射到在 Windows 文档中，为其提供指向相关内容的深入介绍的传递优化设置。  设置或特定于 Intune 的选项不包含指向其他内容。  

下表包括：  

- **设置**: 设置，因为它将显示在 Intune 中。 链接的设置，请打开中的相关条目[配置传递优化适用于 Windows 10 更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)可从中了解有关设置的详细信息的 Windows 文档中。

- **Windows 版本**： 包括对此设置支持的 Windows 10 的最低版本。  

- **详细信息**: Intune 如何实现的设置，包括 Intune 默认的简短说明。 如果可用，则有链接指向[交付优化策略配置服务提供程序](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization)(CSP) 条目。  

若要配置 Intune 以使用这些设置，请参阅[提供更新](delivery-optimization-windows.md)。  

## <a name="delivery-optimization"></a>传递优化  

|Setting  |Windows 版本  |详细信息  |
|---------|-----------------|---------|
| [下载模式](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode)     | 1511         | 指定的下载方法，传递优化用于下载内容。<br><ul><li>**未配置**：最终用户使用自己的方法更新其设备，可能使用的是 Windows 更新或操作系统提供的传递优化设置。 </li> <li> **仅 HTTP，无对等互连 (0)**：仅从 Internet 获取更新。 不从其他计算机 （对等） 在网络上获取更新。 </li> <li> **与相同 NAT (1) 后面的对等互连混合的 HTTP**： 从 internet 和网络上的其他计算机获取更新。 </li> <li> **与跨专用组 (2) 对等互连混合的 HTTP**: Active Directory 站点 （如果存在） 或同一个域对等互连在同一个设备上发生。 在选中此选项后，在整个网络地址转换 (NAT) IP 地址中进行对等互连。 </li> <li> **与 Internet 对等互连混合的 HTTP (3)**：从 Internet 和网络上的其他计算机获取更新。 </li> <li> **无对等互连的简单下载模式 (99)**：直接从更新所有者（如 Microsoft）通过 Internet 获取更新。 它不会联系传递优化云服务。 </li> <li> **Bypass 模式 (100)**：使用后台智能传送服务 (BITS) 获取更新。 请勿使用传递优化。 </li></ul> **默认**： 未配置  <br><br> 策略 CSP: [DODownloadMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)  <br><br>  |
| [限制对等方所选内容](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#select-a-method-to-restrict-peer-selection)          | 1803        | 需要**下载模式**设置为*与相同 NAT (1) 后面的对等互连混合的 HTTP*或*与跨专用组 (2) 对等互连混合的 HTTP*。<br/><br/>将对等方所选内容限制为特定的设备组。<br/><br/>**默认**： 未配置 <br/><br/>策略 CSP: [DORestrictPeerSelectionBy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dorestrictpeerselectionby)<br><br>      |
| [组 ID 源](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#select-the-source-of-group-ids)     | 1803        | 需要**下载模式**设置为*与跨专用组对等互连混合的 HTTP*。<br><br>将对等方所选内容限制为特定的源的设备组。<br><br>如果选择**自定义**，然后配置**组 ID (GUID)**。 如果你需要为本地网络对等互连 for 分支在不同的域或不在同一 LAN 上创建一个组将 GUID 用作组 ID。<br><br>**默认**： 未配置 <br><br>策略 CSP: [DOGroupId](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dogroupid)     |

## <a name="bandwidth"></a>带宽  

|Setting  |Windows 版本  |详细信息  |
|---------|---------|---------|
|带宽优化类型     | 查看详情        | 选择 Intune 如何确定最大带宽的传递优化可以使用所有的并发下载活动中。<br><br>选项包括：<br><ul><li>未配置</li><br><li>**绝对**– 指定[（以 KB/秒） 的最大下载带宽](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-download-bandwidth)和[（以 KB/秒） 的最大上传带宽](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-upload-bandwidth)设备可以使用跨所有其并发传递优化下载活动。<br><br>要求使用 Windows 1607<br><br>策略 CSP: [DOMaxDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxdownloadbandwidth)和[DOMaxUploadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxuploadbandwidth)</li><br><li>**Percent** – 指定[最大前台下载带宽 （%）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-foreground-download-bandwidth)并[最大后台下载带宽 （%）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-foreground-download-bandwidth) ，设备可以使用它跨所有其并发交付优化下载活动。<br><br>要求使用 Windows 1803<br><br>策略 CSP: [DOPercentageMaxForegroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth)和[DOPercentageMaxBackgroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)    <br><br><li>**营业时间的百分比**– 最多[前台](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#set-business-hours-to-limit-foreground-download-bandwidth)下载带宽和最多[背景](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#set-business-hours-to-limit-background-download-bandwidth)下载带宽、 配置营业时间内开始和结束时间，然后若要使用你的工作时间内外的带宽的百分比。 <br><br>要求使用 Windows 1803 <br><br>策略 CSP: [DOSetHoursToLimitBackgroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth)和[DOSetHoursToLimitForegroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)<br><br>   |
|[延迟 （以秒为单位） 的背景 HTTP 下载](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#delay-background-download-from-http-in-secs) | 1803        | 使用此设置来配置通过 HTTP 延迟后台下载内容的最长时间。 这仅适用于支持对等下载源的下载。 在这种延迟，设备将搜索包含可用内容的对等方。 在等待对等源，同时下载似乎为最终用户。   <br><br>**默认值**:*配置没有值*  <br><br>**建议**: 60 秒   <br><br>策略 CSP: [DODelayBackgroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaybackgrounddownloadfromhttp) <br><br>    |
| [延迟 （以秒为单位） 的前景色 HTTP 下载](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#delay-foreground-download-from-http-in-secs)      | 1803       | 配置通过 HTTP 延迟内容的前景色 （交互式） 下载的最长时间。 这仅适用于支持对等下载源的下载。 在这种延迟，设备将搜索包含可用内容的对等方。 在等待对等源，同时下载似乎为最终用户。   <br><br>**默认值**:*配置没有值*  <br><br>**建议**: 60 秒   <br><br>策略 CSP: [DODelayForegroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelayforegrounddownloadfromhttp) <br><br>         |


## <a name="caching"></a>正在缓存  

|Setting  |Windows 版本  |详细信息  |
|---------|---------|---------|
|[所需的对等缓存 （以 gb 为单位） 的最小 RAM](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-ram-allowed-to-use-peer-caching)      | 1703        | 指定的最小 RAM 大小以 gb 为单位，设备必须使用对等缓存。 <br><br>**默认值**:*配置没有值*  <br><br>**建议**：4 GB <br><br>策略 CSP: [DOMinRAMAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominramallowedtopeer) <br><br>        |
|[最小磁盘大小所需的对等缓存 （以 gb 为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-disk-size-allowed-to-use-peer-caching)      | 1703        | 指定最小磁盘大小以 gb 为单位，设备必须使用对等缓存。 <br><br>**默认值**:*配置没有值*  <br><br>**建议**：32 GB   <br><br>策略 CSP: [DOMinDiskSizeAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domindisksizeallowedtopeer) <br><br>    |
|[对等缓存 （以 mb 为单位） 的最小的内容文件大小](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-peer-caching-content-file-size)      | 1703        | 指定以 mb 为单位的文件必须满足或超过为使用对等缓存的最小大小。  <br><br>**默认值**:*配置没有值*  <br><br>**建议**: 10 MB   <br><br>策略 CSP: [DOMinFileSizeToCache](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominfilesizetocache)  <br><br>      |
|[（在 %） 上传所需的最小电池电量水平](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level)      | 1709        | 指定为百分比，设备必须将数据上传到对等节点的最小电池电量水平。 如果电池电量降到指定的值，所有活动上载都将自动暂停。   <br><br>**默认值**:*配置没有值*  <br><br>**建议**：40%   <br><br>策略 CSP: [DOMinBatteryPercentageAllowedToUpload](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominbatterypercentageallowedtoupload) <br><br>        |
|[修改缓存驱动器](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#modify-cache-drive)        | 1607        | 指定的驱动器的传递优化用于其缓存。 可以使用环境变量、 驱动器号或完整路径。  <br><br>**默认**: %systemdrive% <br><br>策略 CSP: [DOModifyCacheDrive](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domodifycachedrive) <br><br>        |
| [最大缓存长保留期限 （以天为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-cache-age)    | 1511         | 指定如何，每个文件已成功下载该文件保存在设备上的传递优化缓存后很长时间。   <br><br>使用 Intune 在天配置的缓存老化。 您定义的天数转换到适用的秒数，即 Windows 定义的方式这此设置。 例如，Intune 配置为 3 天将转换为 259200 秒 （3 天） 设备上。  <br><br>**默认值**:*配置没有值*     <br><br>**建议**：7   <br><br>策略 CSP: [DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)  <br><br>          |
| 最大缓存大小类型  | 查看详情    | 选择如何管理由传递优化的设备上的磁盘空间量。 如果未配置，缓存大小默认为 20%的可用磁盘空间可用。  <br><ul><li>**未配置**（默认）</li><br><li>**绝对**– 指定[绝对最大缓存大小 （以 gb 为单位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#absolute-max-cache-size)若要配置的最大设备可用于传递优化的驱动器空间量。 设置为 0 （零） 时，缓存大小不受限制，尽管当设备的磁盘空间不足时，传递优化将清除缓存。 <br><br>要求使用 Windows 1607<br><br> 策略 CSP: [DOAbsoluteMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-doabsolutemaxcachesize) </li><br><li>**百分比**– 指定[最大缓存大小 （%）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-cache-size)若要配置的最大设备可用于传递优化的驱动器空间量。 百分比是可用的驱动器空间，并传递优化不断地评估可用的驱动器空间，并将清除缓存，以保持下设置的百分比的最大缓存大小。 <br><br>要求使用 Windows 1511<br><br>策略 CSP: [DOMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcachesize)  |
| [VPN 对等缓存](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#enable-peer-caching-while-the-device-connects-via-vpn)  | 1709  | 选择**已启用**若要将设备配置为参与对等缓存通过 VPN 连接到域网络时。 已启用的设备可以从下载或上传到其他域的网络设备，VPN 或公司域网络上。  <br><br>**默认**： 未配置  <br><br>策略 CSP: [DOAllowVPNPeerCaching](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)    |

## <a name="next-steps"></a>后续步骤

[在 Intune 中配置传递优化](delivery-optimization-windows.md)
