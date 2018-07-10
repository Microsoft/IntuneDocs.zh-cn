---
title: 对比 Windows 电脑管理选项
titlesuffix: Microsoft Intune
description: 使用 Apple 设备注册计划 (DEP) 或 Apple 配置器注册企业拥有的 iOS 设备。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic-keep
ms.openlocfilehash: 0643c9aaff2a795fa44a8ed6cac09cf143c4ce56
ms.sourcegitcommit: 116be0eaa44fd5518ff34780d39569224ef4746b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2018
ms.locfileid: "36310464"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>对比作为计算机或移动设备管理 Windows 电脑

[!INCLUDE [classic-portal](includes/classic-portal.md)]

组织可以使用 Microsoft Intune 作为具有移动设备管理 (MDM) 的移动设备或具有 Intune 软件客户端的计算机来管理 Windows 电脑。  Microsoft 建议客户尽可能使用 MDM 管理解决方案。 但是，为了帮助你更好地了解这些选项之间的差异，以下图表对两个管理选项做了比较：

|**功能/方案** |**Windows 作为计算机**<br>Intune 软件客户端 | **Windows 作为移动设备**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**操作系统** |Windows 10、Windows 8+、Windows 7、Windows Vista | Windows 10+ |
|**Intune 门户支持** |[Silverlight 控制台](https://manage.microsoft.com)|[Azure 门户](https://portal.azure.com) |
|**条件性访问**|不可用|可用 <br>[什么是条件访问？](conditional-access.md)|
|**批量注册**|不可用|可用 <br>[Windows 设备的批量注册](windows-bulk-enroll.md)|
|**设备配置文件**|不可用|可用 <br>[什么是 Microsoft Intune 设备配置文件？](device-profiles.md)|
|**无代理注册**|不可用 |可用<br>[注册 Windows 设备](windows-enroll.md)|
|**软件更新管理**| Windows 更新和 Microsoft 应用更新<br>[利用软件更新使 Windows 电脑保持最新版本](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|针对 Windows 10 和 Microsoft 应用更新的适用于企业的 Microsoft 应用商店<br> [配置 Windows 更新商业版设置](windows-update-for-business-configure.md) |
|**软件许可证管理**|可用 <br>[管理 Windows 电脑软件的许可协议](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|适用于企业的 Microsoft 应用商店（仅 .appx 应用）<br>[管理从适用于企业的 Microsoft 应用商店购买的应用](windows-store-for-business.md)|
|**清单**|可用 <br>[查看 Windows 电脑的硬件和软件清单](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|可用 <br>[如何监视应用信息](apps-monitor.md)<br>[什么是设备管理](device-management.md)|
|**Windows 防火墙策略**|可用 <br>[使用 Windows 防火墙策略帮助保护 Windows 电脑](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |可用 <br>[Windows Defender 防火墙](endpoint-protection-windows-10.md#windows-defender-firewall)|
|**反恶意软件保护**|Endpoint Protection<br>[使用 Endpoint Protection 帮助保障 Windows 电脑的安全](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows Defender<br>[启用 Windows Defender](advanced-threat-protection.md)|
|**远程协助** |TeamViewer<br>[请求并提供 Windows 电脑的远程协助](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [使用 TeamViewer 远程管理 Intune 设备](device-profile-android-teamviewer.md) |
|**应用程序部署** | 不可用于适用于企业的 Microsoft 应用商店，<br>仅限 .exe、.appx 和多文件 .msi 格式<br>[为运行 Intune 软件客户端的 Windows 电脑添加应用](add-apps-for-windows-pcs-in-microsoft-intune.md)|可用于 Microsoft 应用商店应用和业务线应用<br>[如何添加 Windows 应用商店应用](store-apps-windows.md)<br>[如何添加 Windows 业务线 (LOB) 应用](lob-apps-windows.md)|
|**应用保护**|不可用|可用 <br>[什么是应用保护策略？](app-protection-policy.md)|
|**运行状况证明**|不可用|可用|


### <a name="advantages-of-mdm-windows-pc-management"></a>MDM Windows 电脑管理的优点
使用现代移动设备管理的 Windows 电脑管理具有以下优点：
- **可伸缩性** - MDM 管理可随着 Intune 云管理伸缩。 Intune 软件客户端仅限于 7,000 台电脑。
- **简洁性** - 使用在操作系统中包含的现代管理功能，无需依赖已下载软件客户端
- **一致性** - 像管理组织中所有其他移动设备一样管理 Windows 电脑<!-- - **Cloud optimization** - -->
