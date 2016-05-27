---
# required metadata

title: Microsoft Intune 中的 Windows 电脑管理功能 |Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Windows 电脑管理功能（使用 Microsoft Intune 电脑客户端）
在大多数情况下，你将向 Microsoft Intune 注册设备，这样可提供比 Intune 电脑客户端更多的功能。 但是，你也可以通过使用 Intune 电脑客户端来管理电脑，该客户端提供以下功能：

-   **管理软件更新** - 你可以使电脑保持最新版本，并管理何时应用更新。

-   **Windows 防火墙策略** - 可帮助确保公司所用电脑的 Windows 防火墙均处于活动状态且均配置正确。

-   **反恶意软件保护** - Intune 包括 Endpoint Protection，它有助于保护你的电脑免遭恶意软件侵害。

-   **远程协助** - Intune 允许用户与 IT 支持人员联系，随后他们可使用 Intune 附带的远程桌面功能来提供协助。

-   **软件许可证管理** - 跟踪有多少软件许可证可用，以及有多少可用的许可证已使用。
-   **应用部署** - 将软件部署到你管理的 PC。 在使用客户端软件管理 PC 时，一些应用管理功能不可用。


## 操作系统要求
Intune 可以管理运行以下 Windows 版本（x86 和 x64）的 PC：


-   **Windows Vista** - 商用版、企业版和旗舰版。

-   **Windows 7** - 专业版、企业版和旗舰版（不带 Service Pack 或带 SP1）。

-   **Windows 8** - 专业版和企业版。

-   **Windows 8.1** - 专业版和企业版。


## 最低硬件需求
安装 Intune PC 客户端的最低硬件要求如下：

|要求|详细信息|
|---------------|--------------------|
|Network (网络)|客户端要求 PC 具有 Internet 连接。|
|处理器和内存|请参阅 PC 操作系统的处理器和 RAM 要求。|
|硬盘空间|安装客户端软件之前必须有 200 MB 可用磁盘空间。|

## 其他要求
安装 Intune PC 客户端的软件要求如下：

|要求|详细信息|
|---------------|--------------------|
|管理权限|安装客户端软件的帐户必须具有该 PC 的本地管理员权限。|
|Windows Installer 3.1|PC 至少必须安装 Windows Installer 3.1。|
|删除不兼容的客户端软件|在安装 Intune PC 客户端软件之前，你必须从该 PC 中卸载下列客户端软件：<br /><br />- 任何版本的 Configuration Manager<br />- 任何版本的 Microsoft Systems Management Server (SMS)|

### 另请参阅
[Microsoft Intune 中的移动设备管理功能](/intune/understand/mobile-device-management-capabilties-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


