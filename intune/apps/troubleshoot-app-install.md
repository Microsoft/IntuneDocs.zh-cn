---
title: 排查应用安装问题
titleSuffix: Microsoft Intune
description: Microsoft Intune 疑难解答窗格有助于排查应用安装问题。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be66f99006b06dce9f9bfe21eafa9f2be302e7b9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540973"
---
# <a name="troubleshoot-app-installation-issues"></a>排查应用安装问题

在 Microsoft Intune MDM 托管的设备上，有时应用安装可能会失败。 当这些应用安装失败时，可能难以了解失败原因或解决此问题。 Microsoft Intune 提供应用安装失败详细信息，以便支持人员和 Intune 管理员能够查看应用信息，从而根据请求为用户提供帮助。 Intune 疑难解答窗格提供失败详细信息，包括用户设备上托管应用的详细信息。 在“托管应用”  窗格中，可以在各个设备下详细了解应用的端到端生命周期。 可查看安装问题，如应用的创建时间、修改时间、定目标时间以及传递给设备的时间。 

> [!NOTE]
> 有关特定应用安装错误代码的信息，请参阅 [Intune 应用安装错误参考](~/apps/app-install-error-codes.md)。

## <a name="app-troubleshooting-details"></a>应用疑难解答详细信息

Intune 根据特定用户设备上安装的应用，提供应用疑难解答详细信息。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 选择“故障排除和支持”  。
4. 单击“选择用户”  ，选择要对其排查问题的用户。 此时，“选择用户”  窗格显示。
5. 通过键入名称或电子邮件地址选择用户。 单击窗格底部的“选择”  。 此用户的疑难解答信息显示在“疑难解答”  窗格中。 
6. 在“设备”  列表中，选择要对其排查问题的设备。
    ![Intune 疑难解答窗格。](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. 在选定设备窗格中，选择“托管应用”  。 此时，托管应用列表显示。
    ![Intune 托管的特定设备的详细信息。](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. 在列表中，选择“安装状态”  为“失败”的应用。
    ![显示安装失败详细信息的选定应用。](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > 可以将同一应用分配到多个组，但应用的预期操作（意向）应不同。 例如，如果在应用分配期间对用户排除了应用，那么应用的解析意向显示为“已排除”  。 有关详细信息，请参阅[如何解决不同应用意向之间的冲突](apps-deploy.md#how-conflicts-between-app-intents-are-resolved)。<br><br>
    > 如果所需应用安装失败，用户或用户的支持人员可以同步设备并重试应用安装。

应用安装错误详细信息指出问题所在。 根据这些详细信息，可以确定解决问题的最佳措施。 有关排查应用安装问题的详细信息，请参阅 [Android 应用安装错误](app-install-error-codes.md#android-app-installation-errors)和 [iOS 应用安装错误](app-install-error-codes.md#ios-app-installation-errors)。

> [!Note]  
> 还可通过浏览器前往 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) 来访问“疑难解答”窗格  。

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>面向用户组的应用安装无法访问设备
如果安装应用程序时遇到问题，请考虑下列操作：
- 如果公司门户中未显示应用，请确保使用“可用”意向部署应用，并确保用户使用应用支持的设备类型访问公司门户  。
- 对于 Windows BYOD 设备，用户需要将工作帐户添加到设备。
- 检查用户是否超出 AAD 设备限制：
  1. 导航到 [Azure Active Directory 设备设置](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId)。
  2. 记下为“每用户最多设备数”设置的值  。
  3. 导航到 [Azure Active Directory 用户](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers)。
  4. 选择受影响的用户，然后单击“设备”  。
  5. 如果用户超过所设置的限制，则删除不再需要的所有过时记录。
- 对于 iOS DEP 设备，请确保用户在 Intune 设备概述窗格中列为“注册的用户”  。 如果显示为 NA，则为 Intune 公司门户部署配置策略。 有关详细信息，请参阅[配置公司门户应用](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices)。

## <a name="win32-app-installation-troubleshooting"></a>Win32 应用安装疑难解答

选择使用 Intune 管理扩展部署的 Win32 应用。 Win32 应用安装失败时，可选择“收集日志”选项  。 

> [!IMPORTANT]
> 如果 Win32 应用已在设备上成功安装，则不会启用“收集日志”选项  。<p>Intune 管理扩展必须先安装在 Windows客户端上，才能收集 Win32 应用日志信息。 将 PowerShell 脚本或 Win32 应用部署到用户或设备安全组后，将安装 Intune 管理扩展。 有关详细信息，请参阅 [Intune 管理扩展 - 先决条件](intune-management-extension.md#prerequisites)。

### <a name="collect-log-file"></a>收集日志文件

若要收集 Win32 应用安装日志，请先按照[应用疑难解答详细信息](troubleshoot-app-install.md#app-troubleshooting-details)部分中提供的步骤进行操作。 然后，继续执行以下步骤：

1. 单击“安装详细信息”窗格上的“收集日志”选项   。

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. 使用包含日志文件名的文件路径以开始日志文件收集过程，然后单击“确定”  。

    > [!NOTE]
    > 日志收集需要最多两小时。 支持的文件类型：.log、.txt、.dmp、.cab、.zip、.xml、.evtx 和 .evtl  。 最多允许 25 个文件路径。

3. 收集日志文件后，可选择“日志”链接来下载日志文件  。

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > 将显示通知，指示应用日志收集成功。

#### <a name="win32-log-collection-requirements"></a>Win32 日志收集要求

收集日志文件时必须遵循特定要求：

- 必须指定完整的日志文件路径。 
- 可为日志收集指定环境变量，例如：<br>
  %PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP% 
- 只允许使用精确的文件扩展名，例如：<br>
  .log、.txt、dmp、.cab、.zip、.xml 
- 上传的最大日志文件为 60 MB 或 25 个文件，以先达到者为准。 
- 为满足需要的、可用和卸载应用分配意图的应用启用 Win32 应用安装日志收集。
- 存储的日志已加密，以保护日志中包含的任何个人身份信息。
- 如果开立 Win32 应用支持票证失败，请使用上面提供的步骤附加相关的失败日志。

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>对 Microsoft 应用商店中的应用进行故障排除

[排除 Microsoft 应用商店应用的打包、部署和查询故障](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx)主题中的信息有助于解决使用 Intune 或其他方式从 Microsoft 应用商店安装应用时可能会遇到的问题。

## <a name="app-troubleshooting-resources"></a>应用疑难解答资源
- [将 Visio 和 Project 部署为 Office Pro Plus 部署的一部分](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [采取措施，确保通过 Intune 部署的 MSfB 应用在 Windows 10 1903 上进行安装](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Microsoft Intune 中的 MSI 应用部署疑难解答](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [将软件分发到 Intune 经典 Windows PC 代理的最佳做法](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>后续步骤

- 有关其他 Intune 疑难解答信息，请参阅[使用疑难解答门户为公司用户提供帮助](../fundamentals/help-desk-operators.md)。 
- 了解 Microsoft Intune 中的任何已知问题。 有关详细信息，请参阅 [Intune 客户成功](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)。
- 需要更多帮助？ 请参阅[如何获取对 Microsoft Intune 的支持](../fundamentals/get-support.md)。
