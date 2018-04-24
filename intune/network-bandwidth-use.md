---
title: Microsoft Intune 的网络要求和带宽详情
titlesuffix: ''
description: 查看 Intune 的网络配置要求和带宽详情。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c161d1ca120d5a0210cffca01e781f1ae9206fe4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
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


|          设置           |           建议的值           |                                                                                                  详细信息                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         缓存大小         |             5 GB 到 30 GB             | 该值因网络中客户端计算机的数量和你使用的配置而异。 为了防止文件被过早删除，请针对你的环境调整缓存的大小。 |
| 单个缓存文件大小 |                950 MB                 |                                                                     此设置可能不会在所有缓存代理服务器中可用。                                                                     |
|   要缓存的对象类型    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Intune 包是通过 HTTP 执行的后台智能传输服务 (BITS) 下载检索的 CAB 文件。                                               |

有关使用代理服务器来缓存内容的信息，请参阅代理服务器解决方案的文档。

### <a name="use-background-intelligent-transfer-service-on-computers"></a>在计算机上使用后台智能传输服务
Intune 支持在 Windows 计算机上使用后台智能传输服务 (BITS) 来减少配置期间使用的网络带宽。 可以在 Intune 代理策略的“网络带宽”页上为 BITS 配置策略。

要详细了解 BITS 和 Windows 计算机，请参阅 TechNet 库中的 [后台智能传输服务](http://technet.microsoft.com/library/bb968799.aspx)。

### <a name="use-branchcache-on-computers"></a>在计算机上使用 BranchCache
Intune 客户端可以使用 BranchCache 来减少广域网 (WAN) 流量。 以下操作系统支持 BranchCache：

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

要使用 BranchCache，客户端计算机必须已启用 BranchCache，然后针对“分布式缓存模式”进行配置。

默认情况下，当安装 Intune 客户端时，会在计算机上启用 BranchCache 和分布式缓存模式。 但是，如果组策略已禁用 BranchCache，则 Intune 不会替代该策略，并且 BranchCache 仍保持禁用状态。

如果使用 BranchCache，请与组织中的其他管理员一起协作来管理组策略和 Intune 防火墙策略。 确保他们不会部署禁用 BranchCache 或防火墙例外的策略。 有关 BranchCache 的详细信息，请参阅 [BranchCache 概述](http://technet.microsoft.com/library/hh831696.aspx)。

## <a name="network-communication-requirements"></a>网络通信要求

在所管理的设备与基于云的服务所需的网站之间启用网络通信。

Intune 不使用本地基础结构，如运行 Intune 软件的服务器，但有一些使用本地基础结构（包括 Exchange 和 Active Directory 同步工具）的选项。

若要管理防火墙和代理服务器后面的计算机，必须启用 Intune 的通信。

-   由于 Intune 客户端使用 **HTTP (80)** 和 **HTTPS (443)**，因此代理服务器必须支持这两种协议
-   对于某些任务（例如下载软件和更新），Intune 需要对 manage.microsoft.com 的未经身份验证的代理服务器访问权限

你可以在单独的客户端计算机上修改代理服务器设置，或者可以使用组策略设置更改位于指定代理服务器后面的所有客户端计算机的设置。


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

托管的设备需要允许“所有用户”通过防火墙访问服务的配置。

下表列出了 Intune 客户端访问的端口和服务：

|**域**|**IP 地址**|
|---------------------|-----------|
|login.microsoftonline.com | 详细信息 [Office 365 URL 和 IP 地址范围](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|23.97.165.17|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|

### <a name="apple-device-network-information"></a>Apple 设备网络信息

|         主机名         |                                        URL（IP 地址/子网）                                        |  协议  |     端口     |                          设备                           |
|--------------------------|-------------------------------------------------------------------------------------------------------|------------|--------------|-----------------------------------------------------------|
|      管理控制台       |                                  gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |                    Apple iOS 和 macOS                    |
|      管理控制台       |                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |                    Apple iOS 和 macOS                    |
|      管理控制台       | Apple iTunesitunes.apple.com、\*.mzstatic.com、\*.phobos.apple.com、\*.phobos.apple.com.edgesuite.net |    HTTP    |      80      |                    Apple iOS 和 macOS                    |
|        PI 服务器         |                gateway.push.apple.com(17.0.0.0/8) feedback.push.apple.com(17.0.0.0/8)                 |    TCP     |  2195、2196  |         针对 Apple iOS 和 macOS 云消息传送。          |
|     设备服务      |                                        gateway.push.apple.com                                         |    TCP     |     2195     |                           Apple                           |
|     设备服务      |                                        feedback.push.apple.com                                        |    TCP     |     2196     |                           Apple                           |
|     设备服务      |   Apple iTunesitunes.apple.com \*.mzstatic.com\*.phobos.apple.com \*.phobos.apple.com.edgesuite.net   |    HTTP    |      80      |                           Apple                           |
| 设备 (Internet/Wi-fi) |                                 #-courier.push.apple.com(17.0.0.0/8)                                  |    TCP     | 5223 和 443 | 仅限 Apple。 “#”是从 0 到 200 的随机数字。 |
| 设备 (Internet/Wi-fi) |                           phobos.apple.comocsp.apple.comax.itunes.apple.com                           | HTTP/HTTPS |  80 或 443   |                        仅限 Apple                         |

