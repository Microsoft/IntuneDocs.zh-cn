---
title: "停用 Windows 电脑 | Microsoft Intune"
description: "如何停用 Intune 管理的 Windows 电脑。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 19e8e2b6a7eaa3cf02e4296a6fd147baa1472b61


---

# <a name="retire-a-windows-pc"></a>停用 Windows 电脑
按照以下步骤停用由 Intune 管理的电脑。

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**组**&gt;**所有设备**（或包含需停用的计算机的另一个组）。

2.  选择要停用的设备，然后选择**停用/擦除**。

若要将计算机重新注册到 Intune 中，请使用[使用 Microsoft Intune 安装 Windows 电脑客户端](install-the-windows-pc-client-with-microsoft-intune.md)中的指南在电脑上重新安装软件客户端。

如果计算机无法连接到 Intune，则“仪表板”工作区中会显示一条消息。

在停用计算机时：

-   将会从 Intune 管理和清单中删除该计算机，并且与该计算机关联的许可证将可供重用。 停用/擦除会删除 Intune 软件客户端，但不会从计算机中删除应用或数据。 此停用不会在计算机上执行完全擦除。

-   其状态不再显示在 Intune 控制台中。

-   Intune 将从计算机中删除软件客户端。 如果计算机未连接到 Intune 服务，在它下次连接时将会删除软件客户端。

-   Microsoft Intune Endpoint Protection 将从计算机中删除。 如果计算机安装了另一个终结点应用程序，并且此应用程序处于禁用状态，则删除 Microsoft Intune Endpoint Protection 之后，可以重新启用该应用程序以确保计算机得到保护。

-   将从计算机中删除任何策略，并且策略设置的值将更改。

-   计算机不再从 Intune 服务接收软件更新或恶意软件定义更新。

-   根据停用的计算机的配置情况，停用的计算机可能会继续使用 Windows Server Update Services、Windows 更新或 Microsoft 更新接收更新。

    > [!IMPORTANT]
    > 如果客户端软件是通过使用组策略对象 (GPO) 安装的，则你必须删除组策略对象 (GPO)，然后才能删除客户端软件以防止软件重新安装。

    如果未能卸载客户端，请阅读 [Endpoint Protection 疑难解答](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune)以获取更多帮助。

### <a name="see-also"></a>另请参阅

[使用 Intune 软件客户端的常见 Windows 电脑管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


