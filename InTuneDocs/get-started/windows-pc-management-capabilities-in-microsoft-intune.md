---
title: "Intune 电脑软件客户端功能 | Microsoft Docs"
description: "了解使用 Intune 软件客户端管理 Windows 电脑时的 Intune 功能。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f268cf29461447306d0f5c3ca06d541d9a03a49d
ms.openlocfilehash: 36a20feed1756ea8dde2230db81099b6c5f8c7f6


---

# <a name="windows-pc-management-capabilities-when-you-use-the-intune-software-client"></a>使用 Intune 软件客户端时的 Windows 电脑管理功能

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

在大多数情况下，你将向 Microsoft Intune 注册设备，这样可提供更多的功能。 但是，你也可以通过使用 Intune 软件客户端来管理电脑，该客户端提供以下功能：

-   **[软件更新管理](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)** - 可使电脑保持最新版本，并决定何时进行更新。

-   **[Windows 防火墙策略](/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)** - 可帮助确保公司所用电脑的 Windows 防火墙均处于活动状态且均配置正确。

-   **[反恶意软件保护](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)** - Intune 包括 Endpoint Protection，它有助于保护你的电脑免遭恶意软件侵害。

-   **[远程协助](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )** - Intune 允许用户与 IT 支持人员联系，后者可使用 Intune 附带的远程桌面功能来提供协助（需要 TeamViewer 软件）。

-   **[软件许可证管理](/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)** - 跟踪有多少软件许可证可用，以及有多少可用的许可证已使用。
-   **[应用部署](/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)** - 将软件部署到你管理的 PC。 在使用软件客户端管理电脑时，一些应用管理功能不可用。


Intune 支持最多在 7,000 台 Windows 设备上安装软件客户端。

## <a name="operating-system-requirements"></a>操作系统要求
Intune 可以管理运行以下 Windows 版本（32 位和 64 位）的电脑：


-   **Windows Vista** - 商用版、企业版和旗舰版

-   **Windows 7** - 专业版、企业版和旗舰版（不带 Service Pack 或带 SP1）

-   **Windows 8** - 专业版和企业版

-   **Windows 8.1** - 专业版和企业版

- **Windows 10** - 专业版、教育版和企业版


## <a name="minimum-hardware-requirements"></a>最低硬件需求
安装 Intune 软件客户端的最低硬件要求如下：

|要求|详细信息|
|---------------|--------------------|
|Network (网络)|客户端要求 PC 具有 Internet 连接。|
|处理器和内存|请参阅 PC 操作系统的处理器和 RAM 要求。|
|硬盘空间|安装客户端软件之前必须有 200 MB 可用磁盘空间。|

## <a name="further-requirements"></a>其他要求
安装 Intune 软件客户端的软件要求如下：

|要求|详细信息|
|---------------|--------------------|
|管理权限|安装客户端软件的帐户必须具有该电脑的本地管理员权限。|
|Windows Installer 3.1|PC 至少必须安装 Windows Installer 3.1。|
|删除不兼容的客户端软件|在安装 Intune PC 客户端软件之前，你必须从该 PC 中卸载下列客户端软件：<br /><br />- 任何版本的 Configuration Manager<br />- 任何版本的 Microsoft Systems Management Server (SMS)|

### <a name="see-also"></a>另请参阅
[Microsoft Intune 的已注册设备管理功能](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


