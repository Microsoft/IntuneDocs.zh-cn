---
title: "Intune 网络带宽使用 | Microsoft Docs"
description: "Intune 网络带宽使用"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0f5972171349325eeb750e552481cbcf903fdf95
ms.openlocfilehash: 9f1cd7ea3e92ac2e3a1b828e8185961060a7c619
ms.lasthandoff: 02/10/2017


---

# <a name="intune-network-bandwidth-use"></a>Intune 网络带宽使用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本指南适用于负责企业中的设备管理的系统管理员。 有关在移动设备上使用 Intune 的帮助，请参阅[有关 Intune 公司门户的常见问题](https://docs.microsoft.com/intune/enduser/company-portal-frequently-asked-questions)。

设置 Microsoft Intune 之前，请查看本主题以及[启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)中列出的其他要求。

使用下列部分中的信息来规划 Microsoft Intune 客户端的网络流量。

## <a name="average-network-traffic"></a>平均网络流量
该表列出了对于每个客户端在网络上传输的常见内容的近似大小和频率。

> [!NOTE]
> 若要确保计算机和移动设备可以从 Intune 服务接收必需的更新和内容，必须将其定期连接到 Internet。 接收更新和内容所花费的时间会有差异，但作为参考，他们应该每天保持至少 1 个小时的 Internet 连接。

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
你可以使用代理服务器，该代理服务器可以缓存内容来减少重复下载，并减少从 Internet 请求内容的客户端使用的网络带宽。

缓存代理服务器接收来自网络上的客户端计算机的内容请求，从 Internet 中检索该内容，然后缓存 HTTP 响应和二进制下载。 服务器使用缓存的信息来应答来自 Intune 客户端计算机的后续请求。

下面是针对缓存 Intune 客户端内容的代理服务器所使用的典型设置。

|设置|建议的值|详细信息|
|-----------|---------------------|-----------|
|缓存大小|5 GB 到 30 GB|该值因网络中客户端计算机的数量和你使用的配置而异。 为了防止文件被过早删除，请针对你的环境调整缓存的大小。|
|单个缓存文件大小|950 MB|此设置可能不会在所有缓存代理服务器中可用。|
|要缓存的对象类型|HTTP<br /><br />HTTPS<br /><br />BITS|Intune 包是通过 HTTP 执行的后台智能传输服务 (BITS) 下载检索的 CAB 文件。|
有关使用代理服务器来缓存内容的信息，请参阅代理服务器解决方案的文档。

### <a name="use-background-intelligent-transfer-service-on-computers"></a>在计算机上使用后台智能传输服务
Intune 支持在 Windows 计算机上使用后台智能传输服务 (BITS) 来减少配置期间使用的网络带宽。 可以在 Intune 代理策略的“网络带宽”页上为 BITS 配置策略。

要详细了解 BITS 和 Windows 计算机，请参阅 TechNet 库中的 [后台智能传输服务](http://technet.microsoft.com/library/bb968799.aspx)。

### <a name="use-branchcache-on-computers"></a>在计算机上使用 BranchCache
Intune 客户端可以使用 BranchCache 来减少广域网 (WAN) 流量。 作为客户端得到支持的下列操作系统也支持 BranchCache：

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

要使用 BranchCache，客户端计算机必须已启用 BranchCache，然后针对“分布式缓存模式”进行配置。

默认情况下，当安装 Intune 客户端时，会在计算机上启用 BranchCache 和分布式缓存模式。 但是，如果客户端已有禁用 BranchCache 的组策略，则 Intune 不会替代该策略，BranchCache 在该计算机上将保持禁用状态。

如果使用 BranchCache，你应与组织中负责管理组策略和 Intune 防火墙策略的其他管理员沟通，以确保他们不会部署禁用 BranchCache 或防火墙例外的策略。 有关 BranchCache 的详细信息，请参阅 [BranchCache 概述](http://technet.microsoft.com/library/hh831696.aspx)。

## <a name="network-communication-requirements"></a>网络通信要求

必须在管理和用于管理 Intune 订阅的设备与基于云的服务所需的网站之间启用网络通信。

Intune 不使用本地基础结构，如运行 Intune 软件的服务器，但有一些使用本地基础结构（包括 Exchange 和 Active Directory 同步工具）的选项。

要管理防火墙和代理服务器后面的计算机，则必须将防火墙和代理服务器设置为允许 Intune 的通信。

### <a name="requirements-for-proxy-servers"></a>代理服务器的要求
要管理代理服务器后面的计算机，应意识到：

-   由于 Intune 客户端使用 **HTTP** 和 **HTTPS**，因此代理服务器必须支持这两种协议
-   Intune 支持未经身份验证的代理服务器

你可以在单独的客户端计算机上修改代理服务器设置，或者可以使用组策略设置更改位于指定代理服务器后面的所有客户端计算机的设置。

### <a name="requirements-for-firewalls-ports-and-domains"></a>防火墙、端口和域的要求
托管的设备需要允许“所有用户”通过防火墙访问服务的配置。

下表列出了 Intune 客户端访问的端口和服务。

|**域**|**端口**|**IP 地址**|
|------|----|---|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>p.manage.microsoft.com<br>r.manage.microsoft.com|80 和 443|134.170.168.254<br>134.170.51.126
|m.manage.microsoft.com|80 和 443| 13.91.59.243<br>40.68.30.140
|portal.manage.microsoft.com|80 和 443|40.121.50.69<br>52.169.30.159
|account.manage.microsoft.com|80 和 443|157.56.13.59
|fef.msua01.manage.microsoft.com|80 和 443|138.91.243.97
|fef.msua02.manage.microsoft.com|80 和 443|23.96.112.46
|fef.msua04.manage.microsoft.com|80 和 443|23.96.112.28
|fef.msua05.manage.microsoft.com|80 和 443|138.91.244.151
|fef.msub01.manage.microsoft.com|80 和 443|137.135.128.214
|fef.msub02.manage.microsoft.com|80 和 443|137.135.130.29
|fef.msub03.manage.microsoft.com|80 和 443|23.97.165.17
|fef.msub05.manage.microsoft.com|80 和 443|23.97.166.52
|fef.msuc01.manage.microsoft.com|80 和 443|207.46.225.1
|fef.msuc02.manage.microsoft.com|80 和 443|23.98.66.118
|fef.msuc03.manage.microsoft.com|80 和 443|23.101.0.100
|fef.msuc05.manage.microsoft.com|80 和 443|207.46.154.33
|fef.msua06.manage.microsoft.com|80 和 443|104.42.188.1
|fei.msua01.manage.microsoft.com|80 和 443|138.91.240.131
|fei.msua02.manage.microsoft.com|80 和 443|23.96.112.143
|fei.msua04.manage.microsoft.com|80 和 443|23.96.112.147
|fei.msua05.manage.microsoft.com|80 和 443|138.91.240.163
|fei.msub01.manage.microsoft.com|80 和 443|137.135.130.85
|fei.msub02.manage.microsoft.com|80 和 443|137.135.132.149
|fei.msub03.manage.microsoft.com|80 和 443|23.97.160.232
|fei.msub05.manage.microsoft.com|80 和 443|23.97.162.250
|fei.msuc01.manage.microsoft.com|80 和 443|207.46.224.73
|fei.msuc02.manage.microsoft.com|80 和 443|23.98.66.194
|fei.msuc03.manage.microsoft.com|80 和 443|23.101.2.105
|fei.msuc05.manage.microsoft.com|80 和 443|207.46.147.126
|fei.msua06.manage.microsoft.com|80 和 443|138.91.149.190
|m.fei.msua01.manage.microsoft.com|80 和 443|138.91.240.131
|m.fei.msua02.manage.microsoft.com|80 和 443|23.96.112.143
|m.fei.msua04.manage.microsoft.com|80 和 443|23.96.112.147
|m.fei.msua05.manage.microsoft.com|80 和 443|138.91.240.163
|m.fei.msub01.manage.microsoft.com|80 和 443|137.135.130.85
|m.fei.msub02.manage.microsoft.com|80 和 443|137.135.132.149
|m.fei.msub03.manage.microsoft.com|80 和 443|23.97.160.232
|m.fei.msub05.manage.microsoft.com|80 和 443|23.97.162.250
|m.fei.msuc01.manage.microsoft.com|80 和 443|207.46.224.73
|m.fei.msuc02.manage.microsoft.com|80 和 443|23.98.66.194
|m.fei.msuc03.manage.microsoft.com|80 和 443|23.101.2.105
|m.fei.msuc05.manage.microsoft.com|80 和 443|207.46.147.126
|m.fei.msua06.manage.microsoft.com|80 和 443|138.91.149.190
|m.msua01.manage.microsoft.com|80 和 443|157.55.50.182
|m.msua02.manage.microsoft.com|80 和 443|134.170.49.121
|m.msua04.manage.microsoft.com|80 和 443|134.170.49.126
|m.msua05.manage.microsoft.com|80 和 443|157.55.240.190
|m.msua06.manage.microsoft.com|80 和 443|134.170.49.114
|m.msub01.manage.microsoft.com|80 和 443|94.245.121.50
|m.msub02.manage.microsoft.com|80 和 443|94.245.121.58
|m.msub03.manage.microsoft.com|80 和 443|94.245.121.56
|m.msub05.manage.microsoft.com|80 和 443|157.56.113.123
|m.msuc01.manage.microsoft.com|80 和 443|104.44.84.187
|m.msuc02.manage.microsoft.com|80 和 443|104.44.84.188
|m.msuc03.manage.microsoft.com|80 和 443|104.44.84.189
|m.msuc05.manage.microsoft.com|80 和 443|111.221.76.60
|msua01.manage.microsoft.com|80 和 443|157.55.50.182
|msua02.manage.microsoft.com|80 和 443|134.170.49.121
|msua04.manage.microsoft.com|80 和 443|134.170.49.126
|msua05.manage.microsoft.com|80 和 443|157.55.240.190
|msub01.manage.microsoft.com|80 和 443|94.245.121.50
|msub02.manage.microsoft.com|80 和 443|94.245.121.58
|msub03.manage.microsoft.com|80 和 443|94.245.121.56
|msub05.manage.microsoft.com|80 和 443|157.56.113.123
|msuc01.manage.microsoft.com|80 和 443|104.44.84.187
|msuc02.manage.microsoft.com|80 和 443|104.44.84.188
|msuc03.manage.microsoft.com|80 和 443|104.44.84.189
|msuc05.manage.microsoft.com|80 和 443|111.221.76.60
|msua06.manage.microsoft.com|80 和 443|134.170.49.114
|ncufun.account.manage.microsoft.com|80 和 443|157.55.252.224
|neufun.account.manage.microsoft.com|80 和 443|65.52.229.134
|portal.fei.msua01.manage.microsoft.com|80 和 443|138.91.240.131
|portal.fei.msua02.manage.microsoft.com|80 和 443|23.96.112.143
|portal.fei.msua04.manage.microsoft.com|80 和 443|23.96.112.147
|portal.fei.msua05.manage.microsoft.com|80 和 443|138.91.240.163
|portal.fei.msub01.manage.microsoft.com|80 和 443|137.135.130.85
|portal.fei.msub02.manage.microsoft.com|80 和 443|137.135.132.149
|portal.fei.msub03.manage.microsoft.com|80 和 443|23.97.160.232
|portal.fei.msub05.manage.microsoft.com|80 和 443|23.97.162.250
|portal.fei.msuc01.manage.microsoft.com|80 和 443|207.46.224.73
|portal.fei.msuc02.manage.microsoft.com|80 和 443|23.98.66.194
|portal.fei.msuc03.manage.microsoft.com|80 和 443|23.101.2.105
|portal.fei.msuc05.manage.microsoft.com|80 和 443|207.46.147.126
|portal.fei.msua06.manage.microsoft.com|80 和 443|138.91.149.190
|portal.msua01.manage.microsoft.com|80 和 443|157.55.50.182
|portal.msua02.manage.microsoft.com|80 和 443|134.170.49.121
|portal.msua04.manage.microsoft.com|80 和 443|134.170.49.126
|portal.msua05.manage.microsoft.com|80 和 443|157.55.240.190
|portal.msub01.manage.microsoft.com|80 和 443|94.245.121.50
|portal.msub02.manage.microsoft.com|80 和 443|94.245.121.58
|portal.msub03.manage.microsoft.com|80 和 443|94.245.121.56
|portal.msub05.manage.microsoft.com|80 和 443|157.56.113.123
|portal.msuc01.manage.microsoft.com|80 和 443|104.44.84.187
|portal.msuc02.manage.microsoft.com|80 和 443|104.44.84.188
|portal.msuc03.manage.microsoft.com|80 和 443|104.44.84.189
|portal.msuc05.manage.microsoft.com|80 和 443|111.221.76.60
|portal.msua06.manage.microsoft.com|80 和 443|134.170.49.114
|ssu2.manage.microsoft.com|80 和 443|157.55.99.181
|status.manage.microsoft.com|80 和 443|157.55.99.170
|swda01.manage.microsoft.com<br>swda02.manage.microsoft.com<br>swdb01.manage.microsoft.com<br>swdb02.manage.microsoft.com<br>swdc01.manage.microsoft.com<br>swdc02.manage.microsoft.com|80 和 443|93.184.215.200
|*.microsoftonline-p.com|80 和 443||
|has.spserv.microsoft.com<br>设备运行状况证明服务所需|443||
|*.microsoftonline-p.net|80 和 443||
|*.portal.office.com|80 和 443||
|*.spynet2.microsoft.com|443||
|c.microsoft.com|80 和 443||
|c1.microsoft.com|80 和 443||
|blob.core.windows.net|80 和 443||
|ajax.aspnetcdn.com|80 和 443||
|*.googleapis.com<br>当你使用公司门户网站时，JQuery 支持需要此域。|80 和 443||
|wustat.microsoft.com|80 和 443||
|Microsoft 更新服务|\*.update.microsoft.com<br>download.microsoft.com<br>update.microsoft.com<br>\*.download.windowsupdate.com<br>download.windowsupdate.com<br>\*.windowsupdate.com<br>windowsupdate.microsoft.com<br>ntservicepack.microsoft.com|80 和 443|
|DNS 查找请求|manage.microsoft.com.nsatc.net|80|
|通过防火墙的 Samsung KNOX 标准版设备通信|若要启用 Samsung KNOX 标准版设备通过防火墙联系 KNOX 标准版服务器，请遵循 Samsung KNOX 标准版常见问题中的说明。||
|条件性访问通信|443|204.79.197.200|
|文档、帮助和支持：</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||


>[!div class="step-by-step"]

>[&larr; **先决条件**](what-to-know-before-you-start-microsoft-intune.md)     [**订阅**&rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)  

