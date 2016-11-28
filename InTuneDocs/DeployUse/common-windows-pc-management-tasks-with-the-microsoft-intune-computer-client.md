---
title: "常见 Windows 电脑管理任务 | Microsoft Intune"
description: "查看本主题中的任务，了解如何管理运行 Intune 软件客户端的 Windows 电脑。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cf6b4c0fbc8a739f205173f39093ce5550cb8321
ms.openlocfilehash: 075ed3f7d8b5f8283b7936c1c89d20081a9264a6


---

# <a name="common-windows-pc-management-tasks-with-the-intune-software-client"></a>使用 Intune 软件客户端的常见 Windows 电脑管理任务
查看本主题中的任务，了解如何管理运行 Intune 软件客户端的计算机。 如果尚未在计算机上安装客户端，请参阅[安装 Intune 软件客户端](install-the-windows-pc-client-with-microsoft-intune.md)。


## <a name="use-policies-to-simplify-pc-management"></a>使用策略来简化电脑管理

可以使用 Intune 的**计算机管理**策略来管理运行 Intune 软件客户端的 Windows 电脑。

![用于 Windows 电脑的策略模板](../media/pc_policy_template.png)

### <a name="manage-the-microsoft-intune-center"></a>管理 Microsoft Intune Center
用户可以看到 Intune 软件客户端作为 **Microsoft Intune 中心**。 Microsoft Intune Center 使用户能够：

-   从公司门户中获取应用程序。

-   检查更新。

-   管理 Microsoft Intune Endpoint Protection。

-  请求远程协助。

Microsoft Intune Center 安装在所有被管理的计算机上。 可以在 Intune 策略中配置下列设置，并且这些设置将在 Microsoft Intune Center 中向用户显示：

|策略设置|详细信息|
|------------------|--------------------|
|**Name**|负责管理计算机的管理员的名称。<br />最大长度：40 个字符|
|**电话号码**|负责管理计算机的管理员的电话号码。<br />最大长度：20 个字符|
|**电子邮件地址**|负责管理计算机的管理员的电子邮件地址。<br />最大长度：40 个字符|
|**网站名称**|用户的支持网站的名称。<br />>最大长度：40 个字符|
|**网站 URL**|支持网站的 URL。<br />最大长度：150 个字符|
|**注意**|向用户显示的注释。<br />最大长度：120 个字符|

有关可对 Windows 电脑配置的策略和设置的相关信息，请参阅以下资源：

- [在 Microsoft Intune 中利用软件更新使 Windows 电脑保持最新状态](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) - 这些策略使托管计算机检查软件更新，并从 Microsoft 和第三方下载软件更新。 这些更新不包括操作系统更新（例如，从 Windows 7 升级到 Windows 10，或从一个 Windows 10 版本升级到更高版本）。

- [使用适用于 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) - 这些设置包括检测到恶意软件时要实施的扫描计划和操作。

- [在 Microsoft Intune 中使用 Windows 防火墙策略帮助保护 Windows 电脑](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) - 这些策略可简化托管计算机上 Windows 防火墙设置的管理。

## <a name="view-hardware-and-software-inventory"></a>查看硬件和软件清单
Intune 收集有关被管理的计算机的硬件和软件的详细信息。 使用下列过程中的信息来了解如何创建：

-   列出有关计算机硬件性能的信息的报表。

-   列出每台计算机上所安装的软件的报表。

-   如何刷新计算机清单以确保报表中的数据为最新。

### <a name="to-display-information-about-your-computers"></a>显示有关你的计算机的信息

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**报表**&gt;**计算机清单报表**。

2.  在“创建新报表”  页上，接受默认值或对其进行自定义以筛选报表将返回的结果。 例如，你可以选择只在报表中显示运行 Windows 8.1 的计算机。

3.  选择“查看报表”，在新窗口中打开“计算机清单报表”。

    你可以选择各个列标题，按任何列（如“名称”、“底盘类型”或“制造商”）对报表进行排序。

### <a name="to-display-software-installed-on-your-computers"></a>显示你的计算机上安装的软件

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**报表**&gt;**检测到的软件报表**。

2.  在“创建新报表”  页上，接受默认值或对其进行自定义以筛选报表将返回的结果。 例如，你可以选择只在报表中显示 Microsoft 发布的软件。

3.  选择“查看报表”，在新窗口中打开“检测到的软件报表”。

    你可以选择各个列标题，按任何列（如“名称”、“发布者”或“类别”）对报表进行排序。 通过选择列表项旁边的方向箭头，可以展开列表中的更新以显示更多详细信息（例如安装了更新的计算机）。

### <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>刷新计算机清单以确保其为最新

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**组**&gt;**所有设备**（或包含需刷新清单的计算机的另一个组）。

2.  选择一台计算机，或按住  “Ctrl”键以选择多台计算机。

3.  在任务栏上，选择**远程任务**&gt;**刷新清单**。

4.  若要查看任务状态，请选择页面右下角的“远程任务”。

    “任务状态”  对话框显示当前远程任务、任务状态、设备名称和任何报告的错误，并提供指向疑难解答信息的链接。


## <a name="remotely-restart-a-windows-pc"></a>远程重启 Windows 电脑

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**组**&gt;**所有设备**（或包含需重新启动的计算机的另一个组）。

2.  选择一台或多台计算机，然后选择**远程任务**&gt;**重新启动计算机**。

3.  若要查看任务状态，请选择页面右下角的“远程任务”。

4.  在“任务状态”  对话框中，查看当前远程任务、任务状态、设备名称以及报告的任何错误。

## <a name="retire-a-computer"></a>停用计算机

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

## <a name="manage-user-device-linking"></a>管理用户-设备链接
你必须将用户链接到计算机，然后才能将软件部署到用户。 你可以将某个用户链接到多台计算机，但每台计算机只能链接到一个用户。 用户会自动链接到他们使用公司门户在 Intune 中注册的任何计算机。

### <a name="to-link-a-user-to-a-computer"></a>将用户链接到计算机

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**组**&gt;**所有设备**（或包含需链接到用户的计算机的另一个组）。

2.  选择要链接用户的计算机，然后选择**链接用户**。

    “链接用户”  对话框显示可用用户的列表，将显示用户的显示名称、用户 ID 和每个用户当前链接到的计算机的数量。 如果用户已链接到所选计算机，则该用户的名称和用户 ID 会显示在“当前用户” 下面。 如果计算机未链接到任何用户，则“当前用户”  下面将显示“无用户” 。

3.  执行以下操作之一：

    -   若要使计算机与其当前用户（如果存在当前用户）链接，请选择**取消**。

    -   若要删除指向当前用户的链接（如果有），请选择**删除链接**&gt;**确定**。

    -   要将计算机链接到新用户，请在“所有用户”  列表中，选择用户。 确认用户数据正确，然后选择**确定**。

> [!TIP]
> 如果想要限制最终用户将自己链接到计算机的能力，则启用“Microsoft Intune 代理设置”策略中的“限制用户将自己链接到计算机的能力”选项。

## <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>请求并提供 Windows 电脑的远程协助

Microsoft Intune 可使用 [TeamViewer](https://www.teamviewer.com) 软件（单独购买）使运行 Intune 软件客户端的电脑用户获得由你提供的远程协助帮助。 当用户从 Microsoft Intune Center 请求帮助时，你会收到警报通知，可接受请求并提供帮助。
此功能将替换 Intune 中现有的 Windows 远程协助功能。


### <a name="before-you-start"></a>开始之前

开始建立并响应远程协助请求之前，必须先确保以下先决条件已就绪：

- 若要登录到 TeamViewer 网站，必须先[注册 TeamViewer 帐户](https://login.teamviewer.com/LogOn#register)。
- 想要管理的 Windows 电脑必须[由 Windows 电脑客户端管理](manage-windows-pcs-with-microsoft-intune.md)
- 可管理所有 Intune 支持的 Windows 电脑操作系统。

### <a name="configure-the-teamviewer-connector"></a>配置 TeamViewer 连接器

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择**管理员**。
2. 在**管理员**工作区中，选择 **TeamViewer**。
3. 在 **TeamViewer** 页面中 **TeamViewer 连接器**下，选择**启用**。
4. 在**启用 TeamViewer** 对话框中，查看然后**接受**许可条款。 如果你尚未拥有 TeamViewer 许可证，选择**购买 TeamViewer 许可证**。
5. TeamViewer 浏览器窗口打开后，使用 TeamViewer 凭据登录到此网站。
6. 阅读并接受 TeamViewer 网站上的选项以允许 Intune 连接TeamViewer。
7. 在 Intune 控制台中，验证 **TeamViewer 连接器**项是否显示为**已启用**。


### <a name="open-a-remote-assistance-request-end-user"></a>打开远程协助请求（最终用户）

1. 在客户端 Windows 电脑上，打开 **Microsoft Intune Center**。
2. 在**远程协助**下，选择**请求远程协助**。
3. 批准请求（参见下文）后，客户端上的 TeamViewer 将会打开。 用户必须接受任何表明 Web 浏览器正尝试打开 TeamViewer 应用程序的消息。
4. 用户会看到询问你是否能控制其电脑的消息。 用户必须接受此消息才可继续。
5. 远程协助会话期间，用户将看到一个显示你已连接的窗口。 如果用户关闭此窗口，远程会话将结束。

### <a name="respond-to-a-remote-assistance-request"></a>响应远程协助请求

1. 当用户提交远程协助请求时，你可在**监视** > **远程协助**下的**警报**工作区中查看。 例如：
> ![远程协助请求屏幕截图](./media/team-viewer.png)

<br>如果请求超过 4 小时未获得应答，则会被删除。
2. 若要接受请求，请选择**批准请求并启动远程协助**。
3. 在**新的远程协助请求正等待处理**对话框中，选择**接受远程协助请求**。 如尚未安装，TeamViewer 将会在计算机上安装任何必要的应用。
4. 然后 TeamViewer 会通知最终用户你想控制其电脑。 用户接受该请求后，TeamViewer 窗口将打开，然后就可控制其电脑。

在远程协助会话中，你可使用所有可用的 TeamViewer 命令来控制远程电脑。 有关这些命令的帮助，请从 TeamViewer 网站下载[远程控制指南](http://www.teamviewer.com/en/support/documents/)。

### <a name="close-the-remote-assistance-session"></a>关闭远程协助会话

从 **TeamViewer** 窗口的**操作**菜单中，选择**结束会话**。



<!--HONumber=Nov16_HO3-->


