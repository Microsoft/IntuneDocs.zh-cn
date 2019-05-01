---
title: 使用 Microsoft Intune 中适用于 Windows 10 设备的模板 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 中的管理模板为 Windows 10 设备创建多组设置。 在设备配置配置文件中使用这些设置来控制 Office 程序、保护 Internet Explorer 中的功能、控制对 OneDrive 的访问、使用远程桌面功能、启用自动播放、设置电源管理设置、使用 HTTP 打印、使用不同的用户登录选项以及控制事件日志大小。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 704abe5e03410b52d54c7729e1832e527ae4dfb6
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61504264"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>使用 Windows 10 模板在 Microsoft Intune 中配置组策略设置

管理贵组织中的设备时，你希望创建一组应用于不同设备组的设置。 例如，你有多个设备组。 对于 GroupA，要分配一组特定设置。 对于 GroupB，要分配另一组设置。 此外，还需要可配置设置的简单视图。

可以使用 Microsoft Intune 中的“管理模板”完成此任务。 管理模板包括数百个设置，这些设置可控制 Internet Explorer、Microsoft Office 程序和远程桌面中的功能以及对 OneDrive 的访问，并可使用图片密码或 PIN 进行登录等等。 这些模板类似于 Active Directory (AD) 中的组策略 (GPO) 设置，是使用 XML 且 [ADMX 支持的设置](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)（打开另一 Docs 站点）。 但是，Intune 中的模板 100% 基于云。 它们提供更为简单和直接的方法来配置设置，并可查找所需设置。

“管理模板”内置于 Intune 中，不需要任何自定义（包括使用 OMA-URI）。 作为移动设备管理 (MDM) 解决方案的一部分，请将这些模板设置用作一站式服务，以管理 Windows 10 设备。

本文列出为 Windows 10 设备创建模板的步骤，并演示如何筛选 Microsoft Intune 中的所有可用设置。 创建模板时，模板会创建设备配置配置文件。 然后，可以将此配置文件分配或部署到贵组织中的 Windows 10 设备。

## <a name="create-a-template"></a>创建模板

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下属性：

    - **名称**：输入配置文件的名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Windows 10 及更高版本”。
    - **配置文件类型**：选择“管理模板(预览版)”。

4. 选择“创建”。 在新窗口中，选择“设置”。 每个设置均会列出，你可以使用前后箭头查看更多设置：

    ![请查看设置的示例列表，并使用“上一页”和“下一页”按钮](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. 选择任意设置。 例如，选择“允许文件下载”。 列出设置的详细描述。 选择“启用”、“禁用”或将设置保留为“未配置”（默认）。 详细说明还会介绍选择“启用”、“禁用”或“未配置”时发生的情况。
6. 选择“确定”，保存所做更改。

继续浏览设置列表，并在环境中配置所需设置。 下面是一些示例：

- 使用“VBA 宏通知设置”设置，在不同的 Microsoft Office 程序（包括 Word 和 Excel）中处理 VBA 宏。
- 使用“允许文件下载”设置，允许或阻止从 Internet Explorer 下载。
- 使用“在计算机唤醒（插电模式）时请求密码”设置，在从睡眠模式唤醒设备时提示用户输入密码。
- 使用“下载未签名的 ActiveX 控件”设置，阻止用户从 Internet Explorer 下载未签名的 ActiveX 控件。
- 使用“关闭系统还原”设置，许可或阻止用户在设备上运行系统还原。
- 还有更多...

## <a name="find-some-settings"></a>查找某些设置

这些模板提供数百个设置。 为了更容易查找特定设置，请使用内置功能：

- 在模板中，选择“设置”、“状态”或“路径”列，对列表进行排序。 例如，选择“路径”列，查看 `Microsoft Excel` 路径中的所有设置：

  ![单击“路径”，按字母顺序进行排序](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- 在模板中，请使用“搜索”框查找特定设置。 例如，搜索 `copy`。 具有 `copy` 的所有设置均会显示：

  ![单击“路径”，按字母顺序进行排序](./media/administrative-templates-windows/search-copy-settings.png)

  在另一个示例中，搜索 `microsoft word`。 随即便可看到可以为 Microsoft Word 程序设置的所有设置。 搜索 `explorer` 查看所有可以添加到模板的 Internet Explorer 设置。

此功能使用 [Windows 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies)（打开另一 Docs 站点）。 CSP 适用于不同版本的 Windows，例如家庭版、专业版和企业版等。 要查看 CSP 是否适用于特定版本，请转到 [Windows 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies)（打开另一 Docs 站点）。

## <a name="next-steps"></a>后续步骤

模板已创建，但它尚未起到任何作用。 接下来，[分配模板（也称为配置文件）](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
