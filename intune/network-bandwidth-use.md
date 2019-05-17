---
title: Microsoft Intune 的网络要求和带宽详情
titleSuffix: ''
description: 查看 Intune 的网络配置要求和带宽详情。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40f9ada715570de7b5b2f95292b7ed0d238242d2
ms.sourcegitcommit: 04d29d47b61486b3586a0e0e5e8e48762351f2a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59570788"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune 网络配置要求和带宽

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

本指南可帮助 Intune 管理员了解 Intune 服务的网络要求。 可以使用此信息了解代理设置所需的带宽要求和 IP 地址及端口设置。

## <a name="average-network-traffic"></a>平均网络流量
该表列出了对于每个客户端在网络上传输的常见内容的近似大小和频率。

> [!NOTE]
> 为了确保设备从 Intune 接收更新和内容，它们必须定期连接到 Internet。 接收更新和内容所需的时间可能有所不同，但它们应每天保持至少一个小时的 Internet 连接。

|内容类型|近似大小|频率和详细信息|
|----------------|--------------------|-------------------------|
|Intune 客户端安装<br /><br />**除了 Intune 客户端安装外，还有下列要求**|125 MB|**一次**<br /><br />客户端下载的大小因客户端计算机的操作系统而异。|
|客户端注册程序包|15 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|Endpoint Protection 代理|65 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|Operations Manager 代理|11 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|策略代理|3 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|Remote Assistance via Microsoft Easy Assist 代理|6 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|每天的客户端操作|6 MB|**每天**<br /><br />Intune 客户端定期与 Intune 服务通信以检查更新和策略，并向服务报告客户端的状态。|
|Endpoint Protection 恶意软件定义更新|变化不定<br /><br />通常 40 KB 至 2 MB|**每天**<br /><br />最多一天三次。|
|Endpoint Protection 引擎更新|5 MB|**每月**|
|软件更新|变化不定<br /><br />大小取决于你部署的更新。|**每月**<br /><br />通常，软件更新在每月的第二个星期二发布。<br /><br />新注册或部署的计算机在下载一整套以前发布的更新时可能会使用更多网络带宽。|
|Service Pack|变化不定<br /><br />大小对于你部署的每个 Service Pack 各不相同。|**变化不定**<br /><br />取决于你何时部署 Service Pack。|
|软件分发|变化不定<br /><br />大小取决于你部署的软件。|**变化不定**<br /><br />取决于你何时部署软件。|

## <a name="ways-to-reduce-network-bandwidth-use"></a>减少网络带宽使用的方式
可以使用下列一种或多种方法来减少 Intune 客户端的网络带宽使用。

### <a name="use-a-proxy-server-to-cache-content-requests"></a>使用代理服务器来缓存内容请求
代理服务器可以缓存内容来减少重复下载，并减少从 Internet 获取内容所使用的网络带宽。

从客户端接收内容请求的缓存代理服务器可以检索该内容，并缓存 Web 响应和下载。 服务器使用缓存的数据来应答来自客户端的后续请求。

下面是针对缓存 Intune 客户端内容的代理服务器所使用的典型设置。


|          Setting           |           建议的值           |                                                                                                  详细信息                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         缓存大小         |             5 GB 到 30 GB             | 该值因网络中客户端计算机的数量和你使用的配置而异。 为了防止文件被过早删除，请针对你的环境调整缓存的大小。 |
| 单个缓存文件大小 |                950 MB                 |                                                                     此设置可能不会在所有缓存代理服务器中可用。                                                                     |
|   要缓存的对象类型    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Intune 包是通过 HTTP 执行的后台智能传输服务 (BITS) 下载检索的 CAB 文件。                                               |
> [!NOTE]
> 如果使用代理服务器来缓存内容请求，则仅会对客户端和代理之间以及从代理到 Intune 的通信进行加密。 将不会对从客户端到 Intune 的连接进行端到端加密。

有关使用代理服务器来缓存内容的信息，请参阅代理服务器解决方案的文档。

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>在计算机上使用后台智能传输服务 (BITS)
在进行配置的数小时内，可以在 Windows 计算机上使用 BITS 来减少网络带宽。 可以在 Intune 代理策略的“网络带宽”页上配置 BITS 策略。

> [!NOTE]
> 对于 Windows 上的 MDM 管理，只有 OS 的 MobileMSI 应用类型的管理界面使用 BITS 进行下载。 AppX/MsiX 使用自己的非 BITS 下载堆栈，通过 Intune 代理的 Win32 应用使用传递优化而不是 BITS。

要详细了解 BITS 和 Windows 计算机，请参阅 TechNet 库中的 [后台智能传输服务](http://technet.microsoft.com/library/bb968799.aspx)。

### <a name="use-branchcache-on-computers"></a>在计算机上使用 BranchCache
Intune 客户端可以使用 BranchCache 来减少广域网 (WAN) 流量。 以下操作系统支持 BranchCache：

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

要使用 BranchCache，客户端计算机必须已启用 BranchCache，然后针对“分布式缓存模式”进行配置。

默认情况下，在计算机上安装 Intune 客户端时，会启用 BranchCache 和分布式缓存模式。 但是，如果组策略已禁用 BranchCache，则 Intune 不会替代该策略，并且 BranchCache 仍保持禁用状态。

如果使用 BranchCache，请与组织中的其他管理员一起协作来管理组策略和 Intune 防火墙策略。 确保他们不会部署禁用 BranchCache 或防火墙例外的策略。 有关 BranchCache 的详细信息，请参阅 [BranchCache 概述](http://technet.microsoft.com/library/hh831696.aspx)。

## <a name="network-communication-requirements"></a>网络通信要求

在管理的设备与基于云的服务所需的终结点之间启用网络通信。

作为仅限云的服务，Intune 不需要诸如服务器或网关的本地基础结构。

若要管理防火墙和代理服务器后面的设备，必须启用 Intune 的通信。

- 由于 Intune 客户端使用 **HTTP (80)** 和 **HTTPS (443)**，因此代理服务器必须支持这两种协议
- 对于某些任务（例如下载软件更新），Intune 需要对 manage.microsoft.com 的未经身份验证的代理服务器访问权限

可以修改单个客户端计算机上的代理服务器设置。 还可以使用“组策略”设置来更改位于指定代理服务器后面的所有客户端计算机的设置。


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

托管的设备需要允许“所有用户”通过防火墙访问服务的配置。

下表列出了 Intune 客户端访问的端口和服务：

|**域**|**IP 地址**|
|---------------------|-----------|
|login.microsoftonline.com | 详细信息 [Office 365 URL 和 IP 地址范围](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>fei.amsua0402.manage.microsoft.com <br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.amsub0202.manage.microsoft.com <br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>fei.amsub0302.manage.microsoft.com <br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration。windows。net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|






### <a name="apple-device-network-information"></a>Apple 设备网络信息


|用途|主机名（IP 地址/子网）|协议|Port|
|-----|--------|------|-------|
|通过 Apple Push Notification 服务 (APNS) 从 Intune 服务接收推送通知。 请参阅[此处](https://support.apple.com/en-us/HT203609)的 Apple 文档|                                    gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |
|通过 Apple Push Notification 服务 (APNS) 向 Intune 服务发送反馈|                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |
|检索并显示 Apple 服务器的内容|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|与 APNS 服务器之间的通信|#-courier.push.apple.com (17.0.0.0/8)<br>“#”是 0 到 50 范围内的一个随机数字。|    TCP     |  5223 和 443  |
|各种功能，包括访问万维网、iTunes 商店、macOS 应用商店、iCloud、消息等。 |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 或 443   |

有关详细信息，请参阅 Apple 的 [Apple 软件产品使用的 TCP 和 UDP 端口](https://support.apple.com/en-us/HT202944)、[关于 macOS、iOS 和 iTunes 服务器主机连接和 iTunes 后台进程](https://support.apple.com/en-us/HT201999)以及[如果你的 macOS 和 iOS 客户端不获取 Apple 推送通知](https://support.apple.com/en-us/HT203609)。
