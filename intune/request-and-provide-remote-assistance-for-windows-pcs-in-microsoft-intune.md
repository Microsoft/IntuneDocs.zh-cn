---
title: 请求并提供 Windows 电脑的远程协助
titlesuffix: Microsoft Intune
description: 说明对作为电脑托管的 Windows 桌面寻求远程协助时最终用户和 IT 管理员需要执行的步骤，以及远程启动电脑的步骤。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.openlocfilehash: 21d9ad0b21b151d0131977a01e9d359735be4187
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181303"
---
# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>请求并提供 Windows 电脑的远程协助

[!INCLUDE [classic-portal](includes/classic-portal.md)]

本主题中的信息仅适用于通过使用 Intune 软件客户端作为电脑进行管理的 Windows 桌面。

Intune 可使用 [TeamViewer](https://www.teamviewer.com) 软件（单独购买）使运行 Intune 软件客户端的用户获得远程协助。 当用户从 Microsoft Intune Center 请求帮助时，你会收到警报通知，可接受请求并提供帮助。 此功能将替换 Intune 中现有的 Windows 远程协助功能。


## <a name="before-you-start"></a>开始之前

开始建立并响应远程协助请求之前，请先确保以下先决条件已就绪：

- 必须[注册 TeamViewer 帐户](https://login.teamviewer.com/LogOn#register)，以登录到 TeamViewer 网站。
- 想要管理的 Windows 电脑必须[由 Windows 软件客户端管理](manage-windows-pcs-with-microsoft-intune.md)
- 可管理所有 Intune 支持的 Windows 电脑操作系统。

## <a name="configure-the-teamviewer-connector"></a>配置 TeamViewer 连接器

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“管理员”。
2. 在**管理员**工作区中，选择 **TeamViewer**。
3. 在 **TeamViewer** 页面中 **TeamViewer 连接器**下，选择**启用**。
4. 在**启用 TeamViewer** 对话框中，查看然后**接受**许可条款。 如果你尚未拥有 TeamViewer 许可证，选择**购买 TeamViewer 许可证**。
5. TeamViewer 浏览器窗口打开后，使用 TeamViewer 凭据登录到此网站。
6. 阅读并接受 TeamViewer 网站上的选项以允许 Intune 连接TeamViewer。
7. 在 Intune 控制台中，验证 **TeamViewer 连接器**项是否显示为**已启用**。


## <a name="open-a-remote-assistance-request-end-user"></a>打开远程协助请求（最终用户）

1. 在客户端 Windows 电脑上，打开 **Microsoft Intune Center**。
2. 在**远程协助**下，选择**请求远程协助**。
3. 批准请求（参见下文）后，客户端上的 TeamViewer 将会打开。 用户必须接受任何表明 Web 浏览器正尝试打开 TeamViewer 应用程序的消息。
4. 用户会看到询问你是否能控制其电脑的消息。 用户必须接受此消息才可继续。
5. 远程协助会话期间，用户将看到一个显示你已连接的窗口。 如果用户关闭此窗口，远程会话将结束。

## <a name="respond-to-a-remote-assistance-request"></a>响应远程协助请求

1. 当用户提交远程协助请求时，你可在**监视** > **远程协助**下的**警报**工作区中查看。 例如：
   > ![远程协助请求屏幕截图](/intune/media/team-viewer.png)

<br>如果请求超过 4 小时未获得应答，则会被删除。
2. 若要接受请求，请选择**批准请求并启动远程协助**。
3. 在**新的远程协助请求正等待处理**对话框中，选择**接受远程协助请求**。 如尚未安装，TeamViewer 将在电脑上安装任何必要的应用。
4. 然后 TeamViewer 会通知最终用户你想控制其电脑。 用户接受该请求后，TeamViewer 窗口将打开，然后就可控制其电脑。

在远程协助会话中，你可使用所有可用的 TeamViewer 命令来控制远程电脑。 有关这些命令的帮助，请从 TeamViewer 网站下载[远程控制指南](http://www.teamviewer.com/en/support/documents/)。

## <a name="close-the-remote-assistance-session"></a>关闭远程协助会话

从 **TeamViewer** 窗口的**操作**菜单中，选择**结束会话**。

## <a name="remotely-restart-a-windows-pc"></a>远程重启 Windows 电脑
帮助用户解决问题时，可能需要不时远程重启其电脑。 请按照以下步骤远程重启 Windows 电脑。

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择“组”&gt;“所有设备”（或包含要重启的电脑的另一个组）。

2.  选择一台或多台电脑，然后选择“远程任务”&gt;“重启计算机”。

3.  若要查看任务状态，请选择页面右下角的“远程任务”。

4.  在“任务状态”  对话框中，查看当前远程任务、任务状态、设备名称以及报告的任何错误。

### <a name="see-also"></a>另请参阅

[使用 Intune 软件客户端的常见 Windows 电脑管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)