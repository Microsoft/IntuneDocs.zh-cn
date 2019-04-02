---
title: 在 Microsoft Intune-Azure 中的 Android 设备上使用斑马移动扩展 |Microsoft Docs
description: 使用 Microsoft Intune 来管理和使用斑马斑马移动扩展 (MX) 运行 Android 的设备。 查看所有的步骤，包括安装公司门户应用旁, 加载应用、 将设备管理员角色分配、 创建 StageNow 配置文件，和的详细信息。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490598"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>使用和管理斑马设备使用 Microsoft Intune 中的斑马移动扩展

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 提供一套丰富的功能，包括管理应用和配置设备设置。 这些内置功能和设置用于管理 Android 设备制造的 Zebra Technologies，也称为"斑马设备"。

如果你想要自定义或添加更多特定于斑马的设置，您还可以使用斑马**移动扩展 (MX)** 在这些设备上。 

此功能适用于：

- Android

你的公司可能使用斑马设备零售，在工厂车间，和的详细信息。 例如，是一家零售商和您的环境包括数千个斑马销售助理分组所用的移动设备。 Intune 可帮助管理这些设备作为移动设备管理 (MDM) 解决方案的一部分。

使用 Intune，可注册斑马设备以将你的业务线应用部署到设备。 "设备配置"配置文件，可以创建 MX 配置文件，以管理特定于斑马的设置。

本文介绍如何在 Microsoft Intune 中的斑马设备上使用斑马移动扩展 (MX)。

## <a name="before-you-begin"></a>开始之前

- 请确保您拥有从 Zebra Technologies StageNow 桌面应用程序的最新版本。
- 请务必检查[斑马的完整 MX 功能矩阵](http://techdocs.zebra.com/mx/compatibility)（打开斑马的网站） 以确认你创建的配置文件是与设备的 MX 版本、 OS 版本和模型兼容。
- 某些设备，例如 TC20 月 25 日设备不支持的所有可用的 MX 功能在 StageNow 中。 请务必检查[斑马的功能矩阵](http://techdocs.zebra.com/mx/tc2x/)（打开斑马的 web 站点） 的更新的支持信息。

## <a name="step-1-install-the-latest-company-portal-app"></a>步骤 1： 安装最新的公司门户应用

在设备上，转到 Google Play 商店，下载并安装 Microsoft Intune 公司门户应用。 从 Google Play 安装时，公司门户应用获取更新，并自动修复。

如果没有 Google Play，下载[适用于 Android 的 Microsoft Intune 公司门户](https://www.microsoft.com/download/details.aspx?id=49140)（将打开另一个 Microsoft 网站），并[旁加载它](#sideload-the-company-portal-app)（在这篇文章）。 安装这种方式，应用程序不会收到更新或自动修复。 你应定期更新并手动修补应用程序。

### <a name="sideload-the-company-portal-app"></a>旁加载公司门户应用

当不使用 Google Play 安装应用时，"旁加载"。 旁加载公司门户应用，使用 StageNow。 

以下步骤概述。 有关特定详细信息，请参阅斑马的文档。 [在使用 StageNow MDM 中注册](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/)（打开斑马的网站） 可能会很好的资源。

1. 在 StageNow，创建的配置文件**在 MDM 中的注册**。
2. 在中**部署**，选择下载 MDM 代理文件。
3. 设置**支持应用程序**并**下载配置**步骤**否**。
4. 在中**下载 MDM**，选择**传输/复制文件**。 添加源和目标的 Android 公司门户的程序包 (APK)。
5. 在中**启动 MDM**，保留默认值为-是。 添加以下详细信息：

    - **程序包名称**：`com.microsoft.windowsintune.companyportal`
    - **类名称**：`com.microsoft.windowsintune.companyportal.views.SplashActivity`

继续发布配置文件，并使用与 StageNow 应用在设备上。 安装并在设备上打开公司门户应用。

> [!TIP]
> StageNow，和它的功能的详细信息，请参阅[StageNow Android 设备临时](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html)（打开斑马的 web 站点）。

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>步骤 2： 确认公司门户应用提供设备管理员角色

公司门户应用需要设备管理员才能管理 Android 设备。 若要激活设备管理员角色，一些斑马设备包括在设备上的用户界面 (UI)。 如果设备包含一个 UI，公司门户应用将提示最终用户授予在设备管理员[注册](#step-3-enroll-the-device-in-to-intune)（在这篇文章）。

如果一个用户界面不可用，请使用**DevAdmin Manager** StageNow 创建手动授予到公司门户应用的设备管理员的配置文件中。

以下步骤概述。 有关特定详细信息，请参阅斑马的文档。 
[设置电池交换模式以设备管理员身份](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool)（打开斑马的网站） 可能会很好的资源。

1. 在 StageNow，创建一个配置文件并选择**Xpert 模式**。
2. 添加**DevAdmin Manager**到配置文件。
3. 设置**设备管理操作**到**开启以设备管理员身份**。
4. 设置**设备管理包名称**到`com.microsoft.windowsintune.companyportal`。
5. 设置**设备管理的类名**到`com.microsoft.omadm.client.PolicyManagerReceiver`。

继续发布配置文件，并使用与 StageNow 应用在设备上。 公司门户应用被授予设备的管理员角色。

## <a name="step-3-enroll-the-device-in-to-intune"></a>步骤 3： 注册到 Intune 中的设备

完成前两个步骤后，在设备上安装公司门户应用。 设备已准备好在注册到 Intune。

[注册 Android 设备](android-enroll.md)列出的步骤。 如果有多个斑马设备，你可能想要使用[设备注册管理员帐户](device-enrollment-manager-enroll.md)。

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>步骤 4： 在 StageNow 中创建的设备管理配置文件

使用 StageNow 创建配置文件，用于配置你想要在设备上管理的设置。 有关特定详细信息，请参阅斑马的文档。 [配置文件](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/)（打开斑马的网站） 可能会很好的资源。

上的最后一步中 StageNow，创建配置文件，选择**导出到 MDM**。 这将生成一个 XML 文件。 保存此文件。 在后面的步骤中需要它。

> [!TIP]
> 建议您将其部署到设备中你的组织之前测试配置文件。 若要测试你的计算机上使用 StageNow 创建配置文件时的最后一步中使用**测试**选项。 然后，使用 StageNow 生成的文件与 StageNow 应用在设备上。 
> 
> StageNow 应用在设备上的将显示测试配置文件时生成的日志。 [使用 StageNow 登录斑马设备在 Intune 中运行 Android](android-zebra-mx-logs-troubleshoot.md)具有使用 StageNow 日志以了解错误的信息。

> [!NOTE]
> 引用应用程序、 更新包，或更新其他文件，StageNow 配置文件中，如果想要获取这些更新的设备。 若要获取更新，设备必须连接到 StageNow 部署服务器时应用的配置文件。 
> 
> 或者，可以在 Intune 中使用内置功能来获取这些更改，包括： 
> - 应用管理功能与[添加](apps-add.md)，[部署](apps-deploy.md)，更新，并且[监视器](apps-monitor.md)应用。
> - 管理[系统和应用更新](device-restrictions-android-for-work.md#device-owner-only)在设备上运行 Android 企业版

在测试该文件后下, 一步是将该配置文件部署到使用 Intune 的设备。

> [!NOTE]
> 将一个配置文件部署到每个设备。 如果你想要部署的设备上的多个 StageNow 配置文件，然后导出 StageNow 配置文件，并组合到单个 XML 文件的设置，然后将其添加到 Intune。 
> 
> 您不希望在相同的 XML 文件中配置相同的属性的两个设置。 其目的是为了防止设备上的设置之间的冲突。

## <a name="step-5-create-a-profile-in-intune"></a>步骤 5： 在 Intune 中创建一个配置文件

在 Intune 中，创建设备配置文件：

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择 Android。
    - **配置文件类型**： 选择**MX 配置文件 （仅斑马）**。

4. 在中**MX.xml 格式的配置文件**，添加 XML 配置文件[从 StageNow 导出](#step-4-create-a-device-management-profile-in-stagenow)（在这篇文章）。
5. 选择“确定” > “创建”以保存所做的更改。 创建策略并将其显示在列表中。

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

配置更新，下一次设备检查 MX 配置文件部署到设备。 当设备注册，设备与 Intune 同步，然后每隔大约 8 小时。 此外可以[强制在 Intune 中的同步](device-sync.md)。 或者，在设备上，打开**公司门户应用** > **设置** > **同步**。 

> [!TIP]
> - 出于安全原因，不会看到配置文件的 XML 文本后将其保存。 对文本进行加密，并且你只会看到星号 (`****`)。 为了便于参考，建议保存 MX 配置文件的副本，然后将它们添加到 Intune。
> 
> - 若要更新配置文件分配给斑马设备后，创建更新的 StageNow XML 文件、 编辑现有的 Intune 配置文件，并添加新的 StageNow XML 文件。 此新文件将覆盖以前的 StageNow 策略配置文件中。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

[使用 StageNow 日志来解决斑马设备](android-zebra-mx-logs-troubleshoot.md)。
