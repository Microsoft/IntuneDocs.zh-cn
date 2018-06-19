---
title: 使用客户端软件管理 PC
description: 安装 Intune 客户端软件来管理 Windows 电脑。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8790863f4cfb3b0b8fdcf4f7aedbfc338ae64667
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31028401"
---
# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>通过 Intune 软件客户端将 Windows 电脑作为计算机进行管理

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune 提供了可供组织管理移动设备的全面的解决方案。 Intune 可以使用 Windows 10 操作系统的内置新式设备管理功能将 Windows 电脑作为移动设备进行管理。 Intune 也可通过 Intune 软件客户端将 Windows 电脑作为计算机进行管理，从而满足组织的管理需求。 此管理方法使用旧版 Windows 操作系统中的传统计算机管理功能。

Intune 软件客户端最适合运行旧版操作系统（例如 Windows 7）且无法将其作为移动设备进行管理的 Windows 电脑。 Intune 软件客户端使用“组策略”等管理功能管理云中的电脑。

Intune 最多可支持使用该软件客户端将 7,000 台 Windows 电脑作为计算机进行管理。 对于更大规模的部署，可将 Windows 10 电脑作为移动设备进行管理。 Intune 的每个版本和 Windows 10 的每个更新均包含基于移动设备管理体系结构的管理功能。 强烈建议将你的组织迁移到作为移动设备进行管理的 Windows 10 中。


> [!NOTE]
> 可使用 Intune 客户端软件将 Windows 8.1 和更高版本设备作为电脑或移动设备进行管理。 但不能在同一个设备上同时使用这两种方法。 请在谨慎考虑后再决定是否通过 Intune 客户端软件管理电脑。 本主题仅适用于通过运行 Intune 客户端软件将设备作为电脑管理。

## <a name="requirements-for-intune-pc-client-management"></a>Intune 电脑客户端管理要求

**硬件**：安装 Intune 客户端软件的最低硬件要求如下：

|要求|详细信息|
|---------------|--------------------|
|Network (网络)|客户端要求 PC 具有 Internet 连接。|
|处理器和内存|请参阅 PC 操作系统的处理器和 RAM 要求。|
|磁盘空间|安装客户端软件之前必须有 200 MB 可用磁盘空间。|

**软件**：安装该客户端软件的软件要求如下：

|要求|详细信息|
|---------------|--------------------|
|操作系统 | 运行 Windows Vista 或更高版本的 Windows 设备。 </br></br>**不支持家庭版各版本。**|
|管理权限|安装客户端软件的帐户必须具有该设备的本地管理员权限。|
|Windows Installer 3.1|PC 至少必须安装 Windows Installer 3.1。<br /><br />查看 PC 上 Windows Installer 的版本：<br /><br />  在电脑上，右键单击 **%windir%\System32\msiexec.exe**，然后单击“属性”。<br /><br />你可以从 Microsoft Developer Network 网站上的 [Windows Installer Redistributables（Windows Installer 可再分发文件）](http://go.microsoft.com/fwlink/?LinkID=234258) 中下载最新版本的 Windows Installer。|
|删除不兼容的客户端软件|安装 Intune 客户端软件之前，需从该电脑卸载任何 Configuration Manager、Operations Manager、Operations Management Suite 和 Service Manager 客户端软件。|

## <a name="deploying-the-intune-software-client"></a>部署 Intune 软件客户端
可以以 Intune 管理员身份通过各种方式向用户提供 Intune 软件客户端。 请参阅[在 Windows 电脑上安装 Intune 软件客户端](install-the-windows-pc-client-with-microsoft-intune.md)，获取相关指南。

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>使用 Intune 客户端软件时具有的计算机管理功能
在大多数情况下，你将向 Microsoft Intune 注册设备，这样可提供更多的功能。 但是，你也可以通过使用 Intune 软件客户端来管理电脑，该客户端提供以下功能：

-   [软件更新管理](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune) - 可使电脑保持最新版本，并决定何时进行更新。

-   **[Windows 防火墙策略](/intune-classic/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)** - 可帮助确保公司所用电脑的 Windows 防火墙均处于活动状态且均配置正确。

-   **[反恶意软件保护](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)** - Intune 包括 Endpoint Protection，它有助于保护你的电脑免遭恶意软件侵害。

-   **[远程协助](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )** - Intune 允许用户与 IT 支持人员联系，后者可使用 Intune 附带的远程桌面功能来提供协助（需要 TeamViewer 软件）。

-   **[软件许可证管理](/intune-classic/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)** - 跟踪有多少软件许可证可用，以及有多少可用的许可证已使用。
-   **[应用部署](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)** - 将软件部署到你管理的 PC。 在使用软件客户端管理电脑时，一些应用管理功能不可用。

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>用于 Intune 软件客户端的策略和应用部署

虽然 Intune 客户端软件通过管理软件更新、Windows 防火墙和 Endpoint Protection 支持[帮助保护电脑的管理功能](policies-to-protect-windows-pcs-in-microsoft-intune.md)，但由 Intune 客户端软件管理的电脑不能以其他 Intune 策略为目标，包括特定于移动设备管理的 **Windows** 策略设置。

在使用 Intune 客户端软件管理 Windows 电脑时，只能使用“计算机管理”部分下显示的策略。

Intune 使用与 Windows Server Active Directory 域服务 (AD DS) 组策略对象 (GPO) 执行方式类似的策略来管理 Windows 电脑。 如果使用 Intune 管理 Active Directory 加入域的计算机，请[确保 Intune 策略不与组织中使用的其他 GPO 冲突](/intune-classic/deploy-use/resolve-gpo-and-microsoft-intune-policy-conflicts)。 请参阅[组策略入门](https://technet.microsoft.com/library/hh147307.aspx)了解详细信息。

  ![为新的 Windows 电脑策略选择模板](../media/select-template-for-pc-policy.png)

在部署应用时，只能使用 Windows Installer（.exe、.msi）。

  ![选择平台和电脑客户端软件文件的位置](../media/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Windows 电脑的常见任务

可以使用 Intune 管理控制台在安装了客户端的 Windows 电脑上执行其他常见的计算机管理任务：
- [使用策略简化电脑管理](use-policies-to-simplify-windows-pc-management.md) - 介绍 Intune 的**计算机管理**策略并列出 Microsoft Intune center 的设置。

- [查看 Windows 电脑的硬件和软件清单](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) - 说明如何创建一份报表，列出电脑硬件及其所安装软件的功能信息。 还说明了如何刷新电脑清单确保其最新。
- [停用 Windows 电脑](retire-a-windows-pc-with-microsoft-intune.md) - 列出停用 Windows 电脑的步骤并介绍停用电脑时发生的情况。
- [管理 Windows 电脑的用户设备链接](manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md) - 说明在向用户部署软件之前何时以及如何将用户链接到电脑。
- [请求并提供 Windows 电脑的远程协助](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) - 说明 Intune 电脑用户如何获取远程协助并介绍先决条件和 TeamViewer 设置。

有关上述任务的详细信息，请参阅[常见的计算机管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。

## <a name="management-limitations-of-the-intune-client-software"></a>Intune 客户端软件的管理限制

某些管理选项（可用于将电脑作为移动设备管理）不能用于使用 Intune 客户端软件管理的电脑：

-   完全擦除（选择性擦除可用）
-   条件性访问

还需注意，在 Intune 管理控制台中，只有在已使用 Intune 客户端软件注册设备后，才会显示某些部分，例如“更新”、“保护”和“许可证”。

  ![仅为电脑客户端显示的管理控制台项](../media/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>故障排除帮助

Intune 客户端软件通常在后台静默运行，无需许多用户交互或故障排除。 如果需要解决电脑管理问题，可以检查日志。 Intune 客户端软件和相应的日志安装在 %Program Files%\Microsoft\OnlineManagement 目录下。

还可以查看[故障排除 Microsoft Intune 中的客户端安装问题](/intune-classic/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)来检查可能出现的问题以及任何解决方案或解决方法。
