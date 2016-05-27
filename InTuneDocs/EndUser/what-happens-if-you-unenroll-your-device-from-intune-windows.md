---
# required metadata

title: 从 Intune 取消注册设备会发生什么情况？ | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 从 Intune 取消注册设备会发生什么情况？

当你从设备上卸载公司门户应用时，它还将从 Intune 取消注册你的设备。 有关会发生什么情况的其他信息，请使用与你正在使用的设备的类型匹配的链接。

- [Windows 10 移动版、Windows 8.1、Windows 8、Windows 7、Vista](#windows-10-mobile--8-1,-windows-8,-windows-7,-vista)
- [Windows 10、Windows 8.1 或 Windows Phone 8](#windows-10--windows-8-1-or-windows-phone-8)
- [Windows RT 运行的 Windows 8.1 或 Windows RT](#windows-rt-running-windows-8-1-or-windows-rt)


## Windows 10、Windows 8.1、Windows 8、Windows 7、Vista

-   你的设备不会再显示在公司门户中，且不能再从公司门户中安装应用。

-   如果安装了 Intune 客户端软件，则会从计算机中删除该软件。

-   从计算机中删除 Intune Endpoint Protection 软件。 如果计算机安装了其他病毒保护软件，并且该软件处于禁用状态，则删除 Intune Endpoint Protection 之后，可能会重新启用该软件。 在从公司门户中将你的计算机删除之后，你应对其进行检查。

    > 如果未重新启用其他病毒保护软件或未安装其他病毒保护软件，你的计算机可能容易受到病毒和恶意软件的攻击。

-   将不再应用当你添加设备时在设备上更改的任何设置（例如禁用相机）。

-   你的计算机将不再从 Intune 服务接收自动软件更新或防病毒软件更新。 不过，根据计算机的配置情况，计算机可能仍会从 Windows Server Update Services、Windows 更新或 Microsoft 更新接收更新。

此外，对于 Windows 8.1：

-   你不再能使用设备上的公司应用和公司数据。

-   某些邮件应用（例如 Windows Mail）将不再能够访问设备上存储的公司电子邮件。

-   你可能无法使用 Wi-Fi 或虚拟专用网连接到公司网络。

-   你可能不再能够访问设备上的某些公司资源（例如文件共享或内部网站）。

## Windows 10 移动版、Windows Phone 8.1 或 Windows Phone 8

-   从你的设备上卸载公司门户应用，这意味着你的设备不会再出现在公司门户中，你也不能从公司门户应用或公司门户网站中安装应用。

-   你不再能使用设备上的公司应用和公司数据。

-   将不再应用当你添加设备时在设备上更改的任何设置（例如禁用相机，或需要一定的密码长度）。

    > [!IMPORTANT]
    > 此情况的唯一例外是加密策略，这些策略仍将应用。 如果公司策略要求对你的 Windows Phone 进行加密，则解密电话的唯一方式是使用 Windows Phone 上的“设置”菜单重置电话。

## Windows RT 运行的 Windows 8.1 或 Windows RT

-   从你的设备上卸载公司门户应用，这意味着你的设备不会再出现在公司门户中，你也不能从公司门户应用中安装应用。

-   你不再能使用设备上的公司应用和公司数据。

-   将不再应用当你添加设备时在设备上更改的任何设置（例如禁用相机，或需要一定的密码长度）。

-   你可能不再能够使用 Wi-Fi 或虚拟专用网连接到公司网络。

-   你可能不再能够访问设备上的某些公司资源（例如文件共享或内部网站）。

-   某些邮件应用（例如 Windows Mail）将不再能够访问设备上存储的公司电子邮件。

在删除 Windows RT 设备时，将发生下列情况：

-   从你的设备上卸载公司门户应用，这意味着你的设备不会再出现在公司门户中，你也不能从公司门户应用中安装应用。

-   你不再能使用设备上的公司应用和公司数据。

-   将不再应用当你添加设备时在设备上更改的任何设置（例如禁用相机，或需要一定的密码长度）。


### 另请参阅
[通过 Intune 使用 Windows 设备](using-your-windows-device-with-intune.md)

<!--HONumber=May16_HO2-->


