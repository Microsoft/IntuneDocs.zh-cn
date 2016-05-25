---
# required metadata

title: 你的计算机已注册 |Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8d3a40f5-99e9-48dc-9706-f7a3a23e5704

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 你的计算机已注册
看到此页是因为你运行了 Intune 客户端软件的安装程序。 但是，你的计算机上已安装了此软件，安装程序无法继续。

这可能是因为£؛

-   之前已安装客户端软件，而安装程序再次运行。

-   安装程序在 IT 管理员已从 Intune 停用设备后在计算机上运行。 设备停用后，可能需要几小时才能从计算机中删除客户端软件。

-   安装程序检测到最近未能安装或未能删除客户端软件。

## 安装程序在你的计算机上安装的内容
安装程序安装 Intune 客户端。 安装程序完成后，客户端软件继续在后台运行，配置你的计算机与 Intune 一起使用。 此过程可能需要一些时间才能完成，包括：

-   使用 Intune 注册你的计算机

-   提交有关计算机硬件和已安装软件的清单

-   配置 Intune 策略，包括 Endpoint Protection 的安装（如已配置）

-   安装 Intune 中心

安装 Intune 中心后，你可用它来访问公司门户，你可在此门户中将计算机链接到单位帐户。

## Microsoft Intune 中心
计算机成功安装客户端软件和使用 Intune 注册你的计算机之后，Intune 中心将作为应用程序安装在计算机上。 你可使用 Intune 中心执行以下操作：

-   **从公司门户获取应用程序** - 查找和安装由 IT 管理员部署的应用。 在新注册的计算机上首次登录到公司门户时，可以选择将你的工作帐户与该计算机相链接。

-   **检查软件更新** – 查找由 Intune 管理员部署的软件更新。

-   **开始计算机的 Endpoint Protection 扫描** – 你可以开始在计算机上进行恶意软件扫描。

-   **寻求远程协助** – 此选项仅在你的计算机操作系统支持远程协助时可用。

## 验证是否已安装或已删除客户端软件
**验证是否已安装客户端：**
当以下应用在计算机上可用时，Intune 客户端安装完成：

-   **Intune 中心**

-   **Intune Endpoint Protection**（如果你的 IT 管理员启用了 Endpoint Protection）

如果你熟悉任务管理器的使用，则可以搜索 Intune 客户端服务，此服务应运行：

-   **OmcSvc**

**验证是否已删除客户端：**
Intune 客户端从计算机上卸载之后，将删除客户端安装时安装的应用，包括 Intune 中心。

Intune 客户端服务 **OmcSvc** 已删除。

## 如何从计算机中删除客户端软件
默认情况下，在 IT 管理员从 Intune 管理控制台停用计算机的数小时后，将卸载 Intune 客户端软件。

若要从计算机手动卸载 Intune 客户端软件，可使用以下步骤进行强制卸载：

1.  在计算机上，在管理员模式中打开命令提示符。

2.  转到文件夹 **%programfiles%\Microsoft\OnlineManagement\Common**

3.  运行以下命令：**ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune**

这将安排删除客户端软件。



<!--HONumber=May16_HO1-->


