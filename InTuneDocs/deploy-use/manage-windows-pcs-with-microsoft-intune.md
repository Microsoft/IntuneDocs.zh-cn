---
title: "使用客户端软件管理电脑 | Microsoft Docs"
description: "安装 Intune 客户端软件来管理 Windows 电脑。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 2e7062169ceb855f03a13d1afb4b4de41af593ac
ms.openlocfilehash: 10ba007095182c9cb07710656ba5f275e254d92e
ms.lasthandoff: 02/15/2017


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>使用 Intune 电脑客户端软件管理 Windows 电脑
[将 Windows 电脑注册为移动设备](set-up-windows-device-management-with-microsoft-intune.md)是将 Windows 电脑注册到 Intune 中的首选方法，但也可选择按本主题中所述，通过安装 Intune 客户端软件来注册和管理 Windows 电脑。

Intune 使用与 Windows Server Active Directory 域服务 (AD DS) 组策略对象 (GPO) 执行方式类似的策略来管理 Windows 电脑。 如果要使用 Intune 管理 Active Directory 加入域的计算机，请[确保 Intune 策略不与组织中存在的任何 GPO 冲突](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。 可以阅读有关 [GPO](https://technet.microsoft.com/library/hh147307.aspx) 的详细信息。

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>用于 Intune 软件客户端的策略和应用部署

虽然 Intune 客户端软件通过管理软件更新、Windows 防火墙和 Endpoint Protection 支持[帮助保护电脑的管理功能](policies-to-protect-windows-pcs-in-microsoft-intune.md)，但由 Intune 客户端软件管理的电脑不能以其他 Intune 策略为目标，包括特定于移动设备管理的 **Windows** 策略设置。 

在使用 Intune 客户端软件管理 Windows 电脑时，只能使用“计算机管理”部分下显示的策略。

  ![为新的 Windows 电脑策略选择模板](../media/select-template-for-pc-policy.png)

有关可以设置的策略的详细说明，请参阅：

- [使用策略帮助保护运行 Intune 客户端软件的 Windows 电脑](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)
- [在 Microsoft Intune 中利用软件更新使 Windows 电脑保持最新版本](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)
- [在 Microsoft Intune 中使用 Windows 防火墙策略帮助保护 Windows 电脑](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)
- [使用 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

此外，在部署应用时，只能使用 Windows Installer（.exe、.msi）。

  ![选择平台和电脑客户端软件文件的位置](../media/select-platform-of-software-files-for-pc-agent.png)

> [!NOTE]
> 可使用 Intune 客户端软件将 Windows 8.1 或更高版本设备作为电脑管理，也可使用移动设备管理 (MDM) 功能将 Windows 8.1 或更高版本设备作为移动设备管理。 不能同时使用这两种方法，因此在决定使用 Intune 客户端软件管理电脑之前，请慎重考虑。 本主题仅适用于通过运行 Intune 客户端软件将设备作为电脑管理。

## <a name="requirements-for-intune-pc-client-management"></a>Intune 电脑客户端管理要求

**硬件**：安装 Intune 客户端软件的最低硬件要求如下：

|要求|更多信息|
|---------------|--------------------|
|网络|客户端要求 PC 具有 Internet 连接。|
|处理器和内存|请参阅 PC 操作系统的处理器和 RAM 要求。|
|硬盘空间|安装客户端软件之前必须有&200; MB 可用磁盘空间。|

**软件**：安装该客户端软件的软件要求如下：

|要求|更多信息|
|---------------|--------------------|
|操作系统 | 运行 Windows Vista 或更高版本的 Windows 设备。 </br></br>**不支持家庭版各版本。**|
|管理权限|安装客户端软件的帐户必须具有该设备的本地管理员权限。|
|Windows Installer 3.1|PC 至少必须安装 Windows Installer 3.1。<br /><br />查看 PC 上 Windows Installer 的版本：<br /><br />  在电脑上，右键单击 **%windir%\System32\msiexec.exe**，然后单击“属性”。<br /><br />你可以从 Microsoft Developer Network 网站上的 [Windows Installer Redistributables（Windows Installer 可再分发文件）](http://go.microsoft.com/fwlink/?LinkID=234258) 中下载最新版本的 Windows Installer。|
|删除不兼容的客户端软件|安装 Intune 客户端软件之前，需从该电脑卸载任何 Configuration Manager、Operations Manager、Operations Management Suite 和 Service Manager 客户端软件。|

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>使用 Intune 客户端软件时具有的计算机管理功能

安装 Intune 客户端软件后，管理功能包括： 

- [应用程序管理](deploy-apps-in-microsoft-intune.md)

- [实时监视和 Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) - Endpoint Protection 与 Windows Defender 是同一个产品。 Endpoint Protection 适用于 Windows 7 和 Windows 8。 对于 Windows 10 及更高版本，产品名称已更改为 Windows Defender。

- [Windows 防火墙设置管理](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)、硬件和软件清单以及远程控制（通过远程协助请求）

- [软件更新设置](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- 合规性设置报告

在 Intune 管理控制台中，只有在已使用 Intune 客户端软件注册设备后，才会显示某些部分，例如“更新”、“保护”和“许可证”。

  ![仅为电脑客户端显示的管理控制台项](../media/admin-console-settings-only-for-pc-agent.png)

还可以使用 Intune 管理控制台在安装了客户端的 Windows 电脑上执行其他常见的计算机管理任务：

-   查看有关托管计算机的硬件和软件清单信息
-   远程重启计算机
-   停用计算机以卸载客户端软件并删除它，使其不再受 Intune 管理
-   将用户链接到特定托管计算机
-   响应远程协助请求

有关上述任务的详细信息，请参阅[常见的计算机管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。

## <a name="management-limitations-of-the-intune-client-software"></a>Intune 客户端软件的管理限制

某些管理选项（可用于将电脑作为移动设备管理）不能用于使用 Intune 客户端软件管理的电脑：

-   完全擦除（选择性擦除可用）

-   条件性访问

## <a name="help-with-troubleshooting"></a>故障排除帮助

Intune 客户端软件通常在后台静默运行，无需许多用户交互或故障排除。 如果需要解决电脑管理问题，可以检查日志。 Intune 客户端软件和相应的日志安装在 %Program Files%\Microsoft\OnlineManagement 目录下。

还可以查看[故障排除 Microsoft Intune 中的客户端安装问题](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)来检查可能出现的问题以及任何解决方案或解决方法。

