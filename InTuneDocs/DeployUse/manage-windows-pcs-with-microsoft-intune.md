---
title: "使用客户端软件管理电脑 | Microsoft Intune"
description: "安装 Intune 客户端软件来管理 Windows 电脑。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cf471320f122eea7804ff6cd6cad208f8cd5a692
ms.openlocfilehash: f264dc3740ce9b117fcc01c39792904a2dc6e7ab


---

# 使用 Intune 电脑客户端软件管理 Windows 电脑
你可以通过安装 Intune 客户端软件注册和管理 Windows 电脑，而无需[将 Windows 电脑注册为移动设备](set-up-windows-device-management-with-microsoft-intune.md)。

Intune 使用与 Windows Server Active Directory 域服务 (AD DS) 组策略对象 (GPO) 执行方式类似的策略来管理 Windows PC。 如果你要使用 Intune 管理 Active Directory 加入域的计算机，则应该[确保 Intune 策略不与组织中存在的任何 GPO 冲突](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。

虽然 Intune 软件客户端通过管理软件更新、Windows 防火墙和 Endpoint Protection 支持[帮助保护电脑的管理功能](policies-to-protect-windows-pcs-in-microsoft-intune.md)，由 Intune 客户端托管的电脑不能以其他 Intune 策略为目标，包括特定于移动设备管理的 **Windows** 策略设置。

> [!NOTE]
> 运行 Windows 8.1 或更高版本的设备可使用 Intune 客户端进行管理，或者可将它们注册为移动设备。 下面的信息适用于运行 Intune 客户端的计算机。 不支持安装 Intune 电脑客户端和为移动设备管理注册 Windows 设备。

## Intune 电脑客户端管理要求

**硬件**：安装 Intune 客户端的最低硬件要求如下：

|要求|更多信息|
|---------------|--------------------|
|网络|客户端要求 PC 具有 Internet 连接。|
|处理器和内存|请参阅 PC 操作系统的处理器和 RAM 要求。|
|硬盘空间|安装客户端软件之前必须有 200 MB 可用磁盘空间。|

**软件**：安装该客户端的软件要求如下：

|要求|更多信息|
|---------------|--------------------|
|操作系统 | 运行 Windows 7 或更高版本的 Windows 设备。 |
|管理权限|安装客户端软件的帐户必须具有该设备的本地管理员权限。|
|Windows Installer 3.1|PC 至少必须安装 Windows Installer 3.1。<br /><br />查看 PC 上 Windows Installer 的版本：<br /><br />- 在电脑上，右键单击“%windir%\System32\msiexec.exe”，然后单击“属性”。<br /><br />你可以从 Microsoft Developer Network 网站上的 [Windows Installer Redistributables（Windows Installer 可再分发文件）](http://go.microsoft.com/fwlink/?LinkID=234258) 中下载最新版本的 Windows Installer。|
|删除不兼容的客户端软件|在安装 Intune 客户端软件之前，你必须从该 PC 卸载任何 Configuration Manager 或 System Management Server 客户端软件。|

## 安装 Intune 计算机客户端
Intune 客户端软件可以通过以下方式之一安装：

-  [手动部署 Microsoft Intune 客户端软件](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software)。 在此类型的部署中，管理员下载 Intune 客户端软件，并在每台 PC 上手动安装它。

  若要下载 Intune 客户端软件，请打开“[Intune 管理控制台](https://manage.microsoft.com)”，并选择“**管理**” > “**客户端软件下载**”，然后单击“**下载客户端软件**”。

-  使用下载的相同文件手动安装 Intune 客户端软件，以[将客户端部署到使用 Active Directory GPO 的已加入域的计算机](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)。

-  在[操作系统部署过程](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image)中将 Intune 客户端软件部署到计算机。

-  向用户发送附带 Intune 公司门户 URL ([https://portal.manage.microsoft.com](http://go.microsoft.com/fwlink/?LinkId=825632)) 的说明。 用户打开公司门户时，系统将提示用户下载并运行 Intune 客户端软件来注册他们的电脑。

## 使用 Intune 计算机客户端进行计算机管理
安装 Intune 客户端软件后，该客户端软件将启用多种计算机管理功能，包括：[应用程序管理](deploy-apps-in-microsoft-intune.md)、Endpoint Protection、硬件和软件清单、远程控制（通过远程协助请求）、软件更新和合规性设置报告。

由计算机客户端启用的一些计算机管理任务使用 Intune 策略进行管理，例如：

-   配置托管计算机上的 [Windows 防火墙设置](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)。

-   配置托管计算机的[软件更新设置](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)，以便检查和下载所需软件更新。

-   通过[实时监视和 Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)管理，帮助保护托管计算机免受潜在威胁和恶意软件侵害。

![用于 Windows 电脑的策略模板](../media/pc_policy_template.png)

除了在各台计算机上本地执行的 Intune 客户端代理操作，还可以使用 Intune 管理控制台在安装了客户端的计算机上执行其他[常见计算机管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)，以便实现以下目的：

-   查看有关托管计算机的硬件和软件清单信息

-   远程重启计算机

-   停用计算机以卸载客户端软件并删除它，使其不再受 Intune 管理

-   将用户链接到特定托管计算机

-   响应远程协助请求

Intune 客户端代理通常在后台静默运行，无需许多用户交互或故障排除。 但是，如果需要帮助解决计算机管理问题，这里有一些[可以帮助你解决这些问题的资源](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)。



<!--HONumber=Aug16_HO4-->


