---
title: Microsoft Intune 的网络要求和带宽详情
titleSuffix: ''
description: 查看 Intune 的网络配置要求和带宽详情。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b4983031d0e5d0723e306a1b9cbefadac2f91fe
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727423"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune 网络配置要求和带宽

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

你可以使用此信息来了解你的 Intune 部署的带宽要求。

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
在进行配置的数小时内，可以在 Windows 计算机上使用 BITS 来减少网络带宽。 可以在 Intune 代理策略的“网络带宽”  页上配置 BITS 策略。

> [!NOTE]
> 对于 Windows 上的 MDM 管理，只有 OS 的 MobileMSI 应用类型的管理界面使用 BITS 进行下载。 AppX/MsiX 使用自己的非 BITS 下载堆栈，通过 Intune 代理的 Win32 应用使用传递优化而不是 BITS。

要详细了解 BITS 和 Windows 计算机，请参阅 TechNet 库中的 [后台智能传输服务](https://technet.microsoft.com/library/bb968799.aspx)。

### <a name="delivery-optimization"></a>传递优化
借助传递优化，可使用 Intune 来减少 Windows 10 设备下载应用程序和更新时的带宽消耗。 通过使用自组织分布式缓存，可以从传统服务器和备用源（如网络对等）中提取下载内容。

若要查看传递优化支持的 Windows 10 版本和内容类型的完整列表，请参阅 [Windows 10 更新的传递优化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements)一文。

可以将[传递优化设置](../configuration/delivery-optimization-settings.md)为设备配置文件的一部分。


### <a name="use-branchcache-on-computers"></a>在计算机上使用 BranchCache
Intune 客户端可以使用 BranchCache 来减少广域网 (WAN) 流量。 以下操作系统支持 BranchCache：

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

要使用 BranchCache，客户端计算机必须已启用 BranchCache，然后针对“分布式缓存模式”  进行配置。

默认情况下，在计算机上安装 Intune 客户端时，会启用 BranchCache 和分布式缓存模式。 但是，如果组策略已禁用 BranchCache，则 Intune 不会替代该策略，并且 BranchCache 仍保持禁用状态。

如果使用 BranchCache，请与组织中的其他管理员一起协作来管理组策略和 Intune 防火墙策略。 确保他们不会部署禁用 BranchCache 或防火墙例外的策略。 有关 BranchCache 的详细信息，请参阅 [BranchCache 概述](https://technet.microsoft.com/library/hh831696.aspx)。

> [!NOTE]
> 你可以使用 Microsoft Intune [作为具有移动设备管理 (MDM) 的移动设备](../enrollment/windows-enroll.md)或具有 Intune 软件客户端的计算机来管理 Windows 电脑。 Microsoft 建议客户尽可能[使用 MDM 管理解决方案](../enrollment/windows-enroll.md)。 当以这种方式进行管理时，不支持 BranchCache。 有关详细信息，请参阅[对比作为计算机或移动设备管理 Windows 电脑](../pc-management-comparison.md)。


## <a name="next-steps"></a>后续步骤

[查看 Intune 终结点](../intune-endpoints.md)

