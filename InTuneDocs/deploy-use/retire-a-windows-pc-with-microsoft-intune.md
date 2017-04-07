---
title: "停用 Windows 电脑 | Microsoft Docs"
description: "如何停用 Intune 管理的 Windows 电脑。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 10dd2caa9ce1b96424f55e373e904a778390eb15
ms.openlocfilehash: fbf188be16ca4a47ee369e3fdde8c0a7f799beab
ms.lasthandoff: 12/16/2016


---

# <a name="retire-a-windows-pc"></a>停用 Windows 电脑
使用以下步骤停用作为电脑管理的桌面，通过在桌面上运行 Intune 软件客户端实现。 停用一台电脑时，会从 Intune 管理中将其删除。 无法从 Intune 对电脑恢复出厂设置来将其设置回原始出厂设置。

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择“组”&gt;“所有设备”（或包含要停用的电脑的另一个组）。

2.  选择要停用的设备，然后选择**停用/擦除**。

若要将电脑重新注册到 Intune 中，请使用[使用 Microsoft Intune 安装 Windows 电脑客户端](install-the-windows-pc-client-with-microsoft-intune.md)中的指南在电脑上重新安装软件客户端。

如果电脑无法连接到 Intune，则“仪表板”工作区中会显示一条消息。

停用电脑时：

-   将会从 Intune 管理和清单中删除该电脑，并且与该计算机关联的许可证将可供重用。 停用/擦除会删除 Intune 软件客户端，但不会从电脑中删除应用或数据。 此停用不会在电脑上执行完全擦除。

-   其状态不再显示在 Intune 控制台中。

-   Intune 将从电脑中删除软件客户端。 如果电脑未连接到 Intune 服务，在它下次连接时将会删除软件客户端。

-   Microsoft Intune Endpoint Protection 将从电脑中删除。 如果电脑安装了另一个终结点应用程序，并且此应用程序处于禁用状态，则删除 Microsoft Intune Endpoint Protection 之后，可以重新启用该应用程序以确保电脑得到保护。

-   将从电脑中删除任何策略，并且策略设置的值将更改。

-   电脑不再从 Intune 服务接收软件更新或恶意软件定义更新。

-   根据停用的电脑的配置方式，停用的电脑可能会继续使用 Windows Server Update Services、Windows 更新或 Microsoft 更新来接收更新。

    > [!IMPORTANT]
    > 如果客户端软件是通过使用组策略对象 (GPO) 安装的，则你必须删除组策略对象 (GPO)，然后才能删除客户端软件以防止软件重新安装。

    如果未能卸载 Endpoint Protection 客户端，请阅读 [Endpoint Protection 疑难解答](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune)获取更多帮助。

### <a name="see-also"></a>另请参阅

[使用 Intune 软件客户端的常见 Windows 电脑管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
