---
title: "Intune 网络带宽使用 | Microsoft Intune"
description: "Intune 网络带宽使用"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d422b421c3716ad576c4fc565b181dec28c947e
ms.openlocfilehash: 18007f598f4182fd90592d4aeb365b834a73fc72


---

# Intune 网络带宽使用

设置 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 之前，请查看本主题以及 [Microsoft Intune 启动前须知](what-to-know-before-you-start-microsoft-intune.md)中列出的其他要求。

使用下列部分中的信息来规划 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 客户端的网络流量。

## 平均网络流量
该表列出了对于每个客户端在网络上传输的常见内容的近似大小和频率。

> [!NOTE]
> 若要确保计算机和移动设备可以从 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 服务接收必须的更新和内容，他们必须定期连接到 Internet。 接收更新和内容所花费的时间会有差异，但作为参考，他们应该每天保持至少 1 个小时的 Internet 连接。

|内容类型|近似大小|频率和详细信息|
|----------------|--------------------|-------------------------|
|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 客户端安装<br /><br />**除了 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 客户端安装外，还有下列要求**|125 MB|**一次**<br /><br />客户端下载的大小因客户端计算机的操作系统而异。|
|客户端注册程序包|15 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|Endpoint Protection 代理|65 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|Operations Manager 代理|11 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|策略代理|3 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|Remote Assistance via Microsoft Easy Assist 代理|6 MB|**一次**<br /><br />如果此内容类型存在更新，还可能有额外的下载。|
|每天的客户端操作|6 MB|**每天**<br /><br />[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 客户端定期与 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 服务通信以检查更新和策略，以及向服务报告客户端的状态。|
|Endpoint Protection 恶意软件定义更新|变化不定<br /><br />通常 40 KB 至 2 MB|**每天**<br /><br />最多一天三次。|
|Endpoint Protection 引擎更新|5 MB|**每月**|
|软件更新|变化不定<br /><br />大小取决于你部署的更新。|**每月**<br /><br />通常，软件更新在每月的第二个星期二发布。<br /><br />新注册或部署的计算机在下载一整套以前发布的更新时可能会使用更多网络带宽。|
|Service Pack|变化不定<br /><br />大小对于你部署的每个 Service Pack 各不相同。|**变化不定**<br /><br />取决于你何时部署 Service Pack。|
|软件分发|变化不定<br /><br />大小取决于你部署的软件。|**变化不定**<br /><br />取决于你何时部署软件。|

## 减少网络带宽使用的方式
你可以使用下列一种或多种方法来减少 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 客户端的网络带宽使用。

### 使用代理服务器来缓存内容请求
你可以使用代理服务器，该代理服务器可以缓存内容来减少重复下载，并减少从 Internet 请求内容的客户端使用的网络带宽。

缓存代理服务器接收来自网络上的客户端计算机的内容请求，从 Internet 中检索该内容，然后缓存 HTTP 响应和二进制下载。 服务器使用缓存的信息来应答来自 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 客户端计算机的后续请求。

下面是用于将缓存 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 客户端内容的代理服务器的典型设置。

|设置|建议的值|详细信息|
|-----------|---------------------|-----------|
|缓存大小|5 GB 到 30 GB|该值因网络中客户端计算机的数量和你使用的配置而异。 为了防止文件被过早删除，请针对你的环境调整缓存的大小。|
|单个缓存文件大小|950 MB|此设置可能不会在所有缓存代理服务器中可用。|
|要缓存的对象类型|HTTP<br /><br />HTTPS<br /><br />BITS|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 包是通过 HTTP 执行的后台智能传输服务 (BITS) 下载检索的 CAB 文件。|
有关使用代理服务器来缓存内容的信息，请参阅代理服务器解决方案的文档。

### 在计算机上使用后台智能传输服务
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 支持在 Windows 计算机上使用后台智能传输服务 (BITS) 来减少配置期间使用的网络带宽。 你可以在 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 代理策略的“网络带宽”页上为 BITS 配置策略。

要详细了解 BITS 和 Windows 计算机，请参阅 TechNet 库中的 [后台智能传输服务](http://technet.microsoft.com/library/bb968799.aspx)。

### 在计算机上使用 BranchCache
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 客户端可以使用 BranchCache 来减少广域网 (WAN) 流量。 作为客户端得到支持的下列操作系统也支持 BranchCache：

-   [!INCLUDE[nextref_client_7](../includes/nextref_client_7_md.md)]

-   [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]

-   [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]

要使用 BranchCache，客户端计算机必须已启用 BranchCache，然后针对“分布式缓存模式”进行配置。

默认情况下，当安装 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 客户端时，BranchCache 和分布式缓存模式在计算机上已启用。 但是，如果客户端已有禁用 BranchCache 的组策略，则 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 不会覆盖该策略，BranchCache 在该计算机上将保持禁用状态。

如果使用 BranchCache，你应与组织中负责管理组策略和 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 防火墙策略的其他管理员沟通，以确保他们不会部署禁用 BranchCache 或防火墙例外的策略。 有关 BranchCache 的详细信息，请参阅 [BranchCache 概述](http://technet.microsoft.com/library/hh831696.aspx)。

### 另请参阅
[启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Oct16_HO4-->


