---
title: "使用客户端软件管理电脑 | Microsoft Intune"
description: "安装 Intune 客户端软件来管理 Windows 电脑。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4cc8b7e34e8809eebd7fdec8ffac0599c96d309
ms.openlocfilehash: ce27fc737fdf47903d7554eb15f24f07b3524406


---

# 使用 Intune 电脑客户端软件管理 Windows 电脑
你可以通过安装 Intune 客户端软件注册和管理 Windows 电脑，而无需[将 Windows 电脑注册为移动设备](set-up-windows-device-management-with-microsoft-intune.md)。

Intune 使用与 Windows Server Active Directory 域服务 (AD DS) 组策略对象 (GPO) 执行方式类似的策略来管理 Windows PC。 如果你要使用 Intune 管理 Active Directory 加入域的计算机，则应该[确保 Intune 策略不与组织中存在的任何 GPO 冲突](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。

虽然 Intune 软件客户端通过管理软件更新、Windows 防火墙和 Endpoint Protection 支持[帮助保护 PC 的管理功能](policies-to-protect-windows-pcs-in-microsoft-intune.md)，由 Intune 软件客户端管理的 PC 不能以其他 Intune 策略为目标，包括特定于移动设备管理的 **Windows** 策略设置。

> [!NOTE]
> 运行 Windows 8.1 或更高版本的设备可由 Intune 客户端或作为移动设备管理。 本主题适用于运行 Intune 软件客户端的计算机。 不支持安装 Intune 客户端和注册移动设备管理。

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
|操作系统 | 运行 Windows Vista 或更高版本的 Windows 设备。 不支持家庭版各版本。|
|管理权限|安装客户端软件的帐户必须具有该设备的本地管理员权限。|
|Windows Installer 3.1|PC 至少必须安装 Windows Installer 3.1。<br /><br />查看 PC 上 Windows Installer 的版本：<br /><br />- 在电脑上，右键单击“%windir%\System32\msiexec.exe”，然后单击“属性”。<br /><br />你可以从 Microsoft Developer Network 网站上的 [Windows Installer Redistributables（Windows Installer 可再分发文件）](http://go.microsoft.com/fwlink/?LinkID=234258) 中下载最新版本的 Windows Installer。|
|删除不兼容的客户端软件|在安装 Intune 客户端软件之前，你必须从该 PC 卸载任何 Configuration Manager 或 System Management Server 客户端软件。|

## 使用 Intune 计算机客户端进行计算机管理
安装 Intune 客户端软件后，管理功能包括：[应用程序管理](deploy-apps-in-microsoft-intune.md)、[实时监视和 Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)、[Windows 防火墙设置管理](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)、硬件和软件清单、远程控制（通过远程协助请求）、[软件更新设置](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)和合规性设置报告。

适用于作为移动设备进行管理的电脑但不适用于软件客户端管理的电脑的某些管理选项包括：

-   完全擦除（选择性擦除可用）
-   条件性访问
-   Windows 策略（**计算机管理**策略除外）

![用于 Windows 电脑的策略模板](../media/pc_policy_template.png)

除了在各台计算机上本地执行的 Intune 客户端代理操作，还可以使用 Intune 管理控制台在安装了客户端的计算机上执行其他[常见计算机管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)，以便实现以下目的：

-   查看有关托管计算机的硬件和软件清单信息

-   远程重启计算机

-   停用计算机以卸载客户端软件并删除它，使其不再受 Intune 管理

-   将用户链接到特定托管计算机

-   响应远程协助请求

Intune 客户端代理通常在后台静默运行，无需许多用户交互或故障排除。 但是，如果需要帮助解决计算机管理问题，这里有一些[可以帮助你解决这些问题的资源](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)。



<!--HONumber=Sep16_HO2-->


