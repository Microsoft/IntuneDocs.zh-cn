---
# required metadata

title: 使用 Microsoft Intune 启用对使用证书配置文件的公司资源的访问 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性
当你通过 VPN、Wi-Fi 或电子邮件配置文件启用对公司资源的访问时，你可以选择使用每个用户设备上安装的证书保护该访问权限。 以下是它的工作原理：

1. 请确保你拥有正确的证书基础结构，如[配置证书基础结构](configure-certificate-infrastructure.md)中所述

2. 在每台设备上安装根证书（或中间 CA 证书），以便该设备识别证书颁发机构的合法性。 可通过创建并部署**受信任的证书配置文件**实现此操作。 在部署此配置文件时，使用 Intune 托管的设备将请求并接收根证书。 必须为每个平台创建单独的配置文件。 **受信任的证书配置文件**可用于以下这些平台：
 -  iOS 7.1 及更高版本
 -  Mac OS X 10.9 及更高版本
 -  Android 4.0 及更高版本
 -  Windows 8.1 及更高版本
 -  Windows Phone 8.1 及更高版本

3. 使每台设备请求一个将用于对电子邮件、VPN 和 Wi-Fi 访问进行身份验证的证书，如[配置 Intune 证书配置文件](configure-intune-certificate-profiles.md)中所述。 可以为以下这些平台上的设备创建并部署 **PKCS #12 (.PFX) 证书配置文件**或 **SCEP 证书配置文件**：
 
-  Android 4.0 及更高版本
-  iOS 7.1 及更高版本
-  Windows 10（桌面版和移动版）及更高版本 

**SCEP 证书配置文件**用于：
-   Mac OS X 10.9 及更高版本
-   Windows Phone 8.1 及更高版本

必须为每个平台创建单独的配置文件。 在创建配置文件时，将其与已创建的**受信任的根证书配置文件**关联。

> [!NOTE]           
> -    如果没有企业证书颁发机构，则必须创建一个。 
>- 如果你决定基于你的设备平台使用简化的证书注册协议 (SCEP) 配置文件，你还需要配置网络设备注册服务 (NDES) 服务器。
>-  无论你计划使用 SCEP 配置文件还是 PFX 配置文件，都必须下载并配置 Microsoft Intune 证书连接器。
> 主题[配置证书基础结构](configure-certificate-infrastructure.md)中介绍了所有这些配置

### 后续步骤
- [配置证书基础结构](configure-certificate-infrastructure.md)
- [配置 Itune 证书配置文件](configure-intune-certificate-profiles.md)



<!--HONumber=May16_HO2-->


