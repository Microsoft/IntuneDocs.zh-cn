---
title: 使用 Microsoft Intune 中适用于 Windows 10 设备的模板 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 中的管理模板为 Windows 10 设备创建多组设置。 在设备配置的配置文件中使用这些设置来控制 Office 程序、Microsoft Edge、保护 Internet Explorer 中的功能、控制对 OneDrive 的访问、使用远程桌面功能、启用自动播放、设置电源管理设置、使用 HTTP 打印、使用不同的用户登录选项以及控制事件日志大小。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca087ec67542102a0cd3111d27a860500b23d3c4
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547987"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>使用 Windows 10 模板在 Microsoft Intune 中配置组策略设置

管理组织中的设备时，你希望创建几组应用于不同设备组的设置。 例如，你有多个设备组。 对于 GroupA，要分配一组特定设置。 对于 GroupB，要分配另一组设置。 此外，还需要可配置设置的简单视图。

可以使用 Microsoft Intune 中的“管理模板”完成此任务  。 管理模板包括数百个设置，这些设置可控制 Microsoft Edge 版本 77 及更高版本、Internet Explorer、Microsoft Office 程序、远程桌面、OneDrive 中的功能，以及密码和 PIN 等等。 这些设置允许组管理员使用云来管理组策略。

Windows 设置类似于 Active Directory (AD) 中的组策略 (GPO) 设置。 这些设置内置于 Windows 中，是使用 XML 的[支持 ADMX 的设置](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)。 Office 和 Microsoft Edge 设置为 ADMX 引入的设置，并使用 [Office 管理模板文件](https://www.microsoft.com/download/details.aspx?id=49030)和 [Microsoft Edge 管理模板文件](https://www.microsoftedgeinsider.com/enterprise)中的 ADMX 设置。 但是，Intune 模板是 100% 基于云。 它们提供简单和直接的方法来配置设置，并可查找所需设置。

“管理模板”内置于 Intune 中，不需要任何自定义（包括使用 OMA-URI）  。 作为移动设备管理 (MDM) 解决方案的一部分，请将这些模板设置用作一站式服务，以管理 Windows 10 设备。

本文列出为 Windows 10 设备创建模板的步骤，并演示如何筛选 Intune 中的所有可用设置。 创建模板时，模板会创建设备配置配置文件。 然后，可以将此配置文件分配或部署到贵组织中的 Windows 10 设备。

## <a name="before-you-begin"></a>在开始之前

- 其中一些设置从 Windows 10 版本 1703 (RS2) 开始提供。 所有 Windows 版本中均不包含某些设置。 为获得最佳体验，建议使用 Windows 10 企业版 1903 (19H1) 及更高版本。

- Windows 设置使用 [Windows 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies)。 CSP 适用于不同版本的 Windows，例如家庭版、专业版和企业版等。 要查看 CSP 是否适用于特定版本，请转到 [Windows 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies)。

## <a name="create-a-template"></a>创建模板

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入配置文件的名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Windows 10 及更高版本”  。
    - **配置文件类型**：选择“管理模板”  。

4. 选择“创建”  。 在新窗口中，选择“设置”  。 每个设置均会列出，你可以使用前后箭头查看更多设置：

    ![请查看设置的示例列表，并使用“上一页”和“下一页”按钮](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Intune 中的 Windows 设置与你在本地组策略编辑器中看到的本地组策略路径相关 (`gpedit`)。

5. 在下拉列表中，选择“所有产品”  。 还可以从列表中筛选设置以仅显示 Windows  设置、仅显示 Office  设置，或仅显示 Microsoft Edge 版本 77 或更高版本设置  ：

    ![筛选列表以显示 Intune 中管理模板中的所有 Windows 或所有 Office 设置](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > Microsoft Edge 设置适用于：
    >
    > - Microsoft Edge 版本 77 及更高版本。 若要配置 Microsoft Edge 版本 45 及更早版本，请参阅 [Microsoft Edge 浏览器设备限制设置](device-restrictions-windows-10.md#microsoft-edge-browser)。
    > - 已安装 [KB 4512509](https://support.microsoft.com/kb/4512509) 的 Windows 10 RS4 和更高版本
    > - 已安装 [KB 4512534](https://support.microsoft.com/kb/4512534) 的 Windows 10 RS5 和更高版本
    > - 已安装 [KB 4512941](https://support.microsoft.com/kb/4512941) 的 Windows 10 19H1 和更高版本

6. 选择任意设置。 例如，在 Office  上筛选，然后选择“激活受限浏览”  。 列出设置的详细描述。 选择“启用”  、“禁用”  或将设置保留为“未配置”  （默认）。 详细说明还会介绍选择“启用”  、“禁用”  或“未配置”  时发生的情况。
7. 选择“确定”，保存所做更改  。

继续浏览设置列表，并在环境中配置所需设置。 下面是一些示例：

- 使用“VBA 宏通知设置”设置，在不同的 Microsoft Office 程序（包括 Word 和 Excel）中处理 VBA 宏  。
- 使用“允许文件下载”设置，允许或阻止从 Internet Explorer 下载  。
- 使用“唤醒计算机时需要密码(接通电源)”  ，在从睡眠模式唤醒设备时提示用户输入密码。
- 使用“下载未签名的 ActiveX 控件”设置，阻止用户从 Internet Explorer 下载未签名的 ActiveX 控件  。
- 使用“关闭系统还原”设置，许可或阻止用户在设备上运行系统还原  。
- 使用“允许导入收藏夹”设置，允许或阻止用户将另一个浏览器中的收藏夹导入 Microsoft Edge  。
- 还有更多...

## <a name="find-some-settings"></a>查找某些设置

这些模板提供数百个设置。 为了更容易查找特定设置，请使用内置功能：

- 在模板中，选择“设置”  、“状态”  、“设置类型”  或“路径”  列，对列表进行排序。 例如，选择“路径”列，查看 `Microsoft Excel` 路径中的所有设置  ：

  ![单击路径以显示按 Intune 的管理模板中的组策略或 ADMX 路径分组的所有设置](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- 在模板中，请使用“搜索”框查找特定设置  。 可以通过设置标题或路径进行搜索。 例如，搜索 `copy`。 具有 `copy` 的所有设置均会显示：

  ![搜索 copy 以显示 Intune 管理模板中的所有 Windows 和 Office 设置](./media/administrative-templates-windows/search-copy-settings.png) 

  在另一个示例中，搜索 `microsoft word`。 随即便可看到可以为 Microsoft Word 程序设置的所有设置。 搜索 `explorer` 查看所有可以添加到模板的 Internet Explorer 设置。

## <a name="next-steps"></a>后续步骤

模板已创建，但它尚未起到任何作用。 接下来，[分配模板（也称为配置文件）](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

[使用管理模板更新 Office 365](administrative-templates-update-office.md)。
