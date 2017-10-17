---
title: "对比 Windows 电脑管理选项"
description: "使用 Apple 设备注册程序 (DEP) 或 Apple 配置器注册企业自有的 iOS 设备"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 66c528ce018b99a7263fb1e8395125f50d5670b3
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>对比作为计算机或移动设备管理 Windows 电脑

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

组织可以使用 Microsoft Intune 作为具有移动设备管理 (MDM) 的移动设备或具有 Intune 软件客户端的计算机来管理 Windows 电脑。  Microsoft 建议客户尽可能使用 MDM 管理解决方案。 但是，为了帮助你更好地了解这些选项之间的差异，以下图表对两个管理选项做了比较：

|**功能/方案** |**Windows 作为计算机**<br>Intune 软件客户端 | **Windows 作为移动设备**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**操作系统** |Windows 10、Windows 8+、Windows 7、Windows Vista | Windows 10+ |
|**Intune 门户支持** |[Silverlight 控制台](https://manage.microsoft.com)|[Azure 门户](https://portal.azure.com) |
|**条件性访问**|不可用|可用 <br>[什么是条件访问？](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**批量注册**|不可用|可用 <br>[Windows 设备的批量注册](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**设备配置文件**|不可用|可用 <br>[什么是 Microsoft Intune 设备配置文件？](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**无代理注册**|不可用 |可用<br>[注册 Windows 设备](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**软件更新管理**| Windows 更新和 Microsoft 应用更新<br>[利用软件更新使 Windows 电脑保持最新版本](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|针对 Windows 10 和 Microsoft 应用更新的适用于企业的 Microsoft 应用商店<br> [配置 Windows 更新商业版设置](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**软件许可证管理**|可用 <br>[管理 Windows 电脑软件的许可协议](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|适用于企业的 Microsoft 应用商店（仅 .appx 应用）<br>[管理从适用于企业的 Microsoft 应用商店购买的应用](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**清单**|可用 <br>[查看 Windows 电脑的硬件和软件清单](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|可用 <br>[如何监视应用信息](https://docs.microsoft.com/intune/apps-monitor)<br>[什么是设备管理](https://docs.microsoft.com/intune/device-management)|
|**Windows 防火墙策略**|可用 <br>[使用 Windows 防火墙策略帮助保护 Windows 电脑](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |不可用|
|**反恶意软件保护**|Endpoint Protection<br>[使用 Endpoint Protection 帮助保障 Windows 电脑的安全](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows Defender<br>[Windows Defender 设置](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**远程协助** |TeamViewer<br>[请求并提供 Windows 电脑的远程协助](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|不可用 |
|**应用程序部署** | 不可用于适用于企业的 Microsoft 应用商店，<br>仅限 .exe、.appx 和多文件 .msi 格式<br>[为运行 Intune 软件客户端的 Windows 电脑添加应用](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|可用于 Microsoft 应用商店应用和业务线应用<br>[如何添加 Windows 应用商店应用](https://docs.microsoft.com/intune/store-apps-windows)<br>[如何添加 Windows 业务线 (LOB) 应用](https://docs.microsoft.com/intune/lob-apps-windows)|
|**应用保护**|不可用|可用 <br>[什么是应用保护策略？](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|


### <a name="advantages-of-mdm-windows-pc-management"></a>MDM Windows 电脑管理的优点
使用现代移动设备管理的 Windows 电脑管理具有以下优点：
- **可伸缩性** - MDM 管理可随着 Intune 云管理伸缩。 Intune 软件客户端仅限于 7,000 台电脑。
- **简洁性** - 使用在操作系统中包含的现代管理功能，无需依赖已下载软件客户端
- **一致性** - 像管理组织中所有其他移动设备一样管理 Windows 电脑
<!-- - **Cloud optimization** - -->
