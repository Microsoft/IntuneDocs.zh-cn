---
title: "查看 Windows 电脑的硬件和软件清单 | Microsoft Intune"
description: "如何查看使用 Intune 管理的 Windows 电脑的硬件和软件信息。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 807599d4a6a979c88732ab969fdecb64552a83d5


---

# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>查看 Windows 电脑的硬件和软件清单

Intune 收集有关被管理的计算机的硬件和软件的详细信息。 使用下列过程中的信息来了解如何创建：

-   列出所管理计算机的硬件功能信息的报表。

-   列出每台计算机上所安装的软件的报表。

-   如何刷新计算机清单以确保报表中的数据为最新。

## <a name="to-display-information-about-computers-you-manage"></a>显示所管理计算机的信息

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**报表**&gt;**计算机清单报表**。

2.  在“创建新报表”  页上，接受默认值或对其进行自定义以筛选报表将返回的结果。 例如，你可以选择只在报表中显示运行 Windows 8.1 的计算机。

3.  选择“查看报表”，在新窗口中打开“计算机清单报表”。

    你可以选择各个列标题，按任何列（如“名称”、“底盘类型”或“制造商”）对报表进行排序。

## <a name="to-display-software-installed-on-computers-you-manage"></a>显示所管理计算机上安装的软件

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**报表**&gt;**检测到的软件报表**。

2.  在“创建新报表”  页上，接受默认值或对其进行自定义以筛选报表将返回的结果。 例如，你可以选择只在报表中显示 Microsoft 发布的软件。

3.  选择“查看报表”，在新窗口中打开“检测到的软件报表”。

    你可以选择各个列标题，按任何列（如“名称”、“发布者”或“类别”）对报表进行排序。 通过选择列表项旁边的方向箭头，可以展开列表中的更新以显示更多详细信息（例如安装了更新的计算机）。

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>刷新计算机清单以确保其为最新

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择**组**&gt;**所有设备**（或包含需刷新清单的计算机的另一个组）。

2.  选择一台计算机，或按住  “Ctrl”键以选择多台计算机。

3.  在任务栏上，选择**远程任务**&gt;**刷新清单**。

4.  若要查看任务状态，请选择页面右下角的“远程任务”。

    “任务状态”  对话框显示当前远程任务、任务状态、设备名称和任何报告的错误，并提供指向疑难解答信息的链接。

### <a name="see-also"></a>另请参阅

[使用 Intune 软件客户端的常见 Windows 电脑管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


