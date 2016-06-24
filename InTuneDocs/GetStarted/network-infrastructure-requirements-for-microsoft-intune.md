---
# required metadata

title: 网络基础结构要求 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 074de65b-84a5-4a01-a824-18ffd838eab0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 的网络基础结构要求
设置 Microsoft Intune 之前，请查看本主题以及[启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)中列出的其他要求。

本主题列出了要求，这些要求启用你的网络基础结构以在你管理和用于管理 Intune 订阅的设备与 Internet 上基于云的服务所使用的网站之间传递通信。

没有使用本地基础结构（如你必须在其中安装软件的服务器）的要求，但有一些使用本地基础结构（包括 Exchange 和 Active Directory 同步工具）的选项。

要管理防火墙和代理服务器后面的计算机，则必须将防火墙和代理服务器设置为允许 Intune 的通信。

## 防火墙、端口和域的要求
被管理的设备需要允许“所有用户”通过防火墙访问各个服务的配置。

下表列出了 Intune 客户端访问的端口和服务。


|**Domain**|**端口**|**IP 地址**|
|------|----|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>m.manage.microsoft.com<br>p.manage.microsoft.com<br>portal.manage.microsoft.com<br>r.manage.microsoft.com|80 和 443|134.170.168.254<br>134.170.51.126
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
|通过防火墙的 Samsung KNOX 设备通信|若要启用 Samsung KNOX 设备通过防火墙联系 KNOX 服务器，请遵循 Samsung KNOX 常见问题中的说明。||
|文档、帮助和支持：</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||



## 代理服务器的要求
要管理代理服务器后面的计算机，应意识到：

-   由于 Intune 客户端使用 **HTTP** 和 **HTTPS**，因此代理服务器必须支持这两种协议。

-   Intune 支持未经身份验证的代理服务器。

你可以在单独的客户端计算机上修改代理服务器设置，或者可以使用组策略设置更改位于指定代理服务器后面的所有客户端计算机的设置。

你还可以使用对内容进行缓存以减少 Intune 客户端使用的[网络宽带](network-bandwidth-use.md)的代理服务器。


### 另请参阅
[启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO2-->


