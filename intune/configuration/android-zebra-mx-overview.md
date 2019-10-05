---
title: 在 Microsoft Intune 中的 Android 设备上使用 Zebra Mobility Extensions - Azure | Microsoft Docs
description: 使用 Microsoft Intune，通过 Zebra Mobility Extensions (MX) 来管理和使用运行 Android 的 Zebra 设备。 查看所有步骤，包括安装公司门户应用、旁加载应用、分配设备管理员角色、创建 StageNow 配置文件等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: beeef8775e6399b252d612f2b5f944d230fe1dd4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735215"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>通过 Microsoft Intune 中的 Zebra Mobility Extensions 来使用和管理 Zebra 设备

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 提供丰富的功能，包括管理应用和配置设备设置。 这些内置功能和设置管理 Zebra Technologies 公司制造的 Android 设备，这些设备也称为“Zebra 设备”。

在 Android 设备上，使用“Mobility Extensions (MX)”配置文件来自定义或添加更多 Zebra 特定设置  。

本文介绍如何在 Microsoft Intune 中的 Zebra 设备上使用 Zebra Mobility Extensions (MX)。

此功能适用于：

- Android

公司可能会将 Zebra 设备用于零售、工厂车间等。 假设你是一名零售商，你的环境中有销售人员使用的数千种 Zebra 移动设备。 Intune 可以帮助管理这些设备，这是移动设备管理 (MDM) 解决方案的一部分。

使用 Intune，可以注册 Zebra 设备，将业务线应用部署到设备。 通过“设备配置”配置文件，可以创建 MX 配置文件，用于管理 Zebra 特定的设置。

> [!NOTE]
> 默认情况下，斑马 MX Api 在设备上未锁定。 在 Intune 中注册设备之前，设备可能会受到恶意攻击。 当设备处于干净状态时，建议使用访问管理器（AccessMgr）锁定 MX Api。 例如，你可以选择仅允许公司门户应用和你信任的应用调用 MX Api。
>
> 有关详细信息，请参阅在斑马的网站上[锁定设备](https://developer.zebra.com/community/home/blog/2017/04/11/locking-down-your-device)。

## <a name="before-you-begin"></a>在开始之前

- 请确保拥有 Zebra Technologies 公司最新版的 StageNow 桌面应用。
- 请务必检查 [Zebra 的完整 MX 功能矩阵](http://techdocs.zebra.com/mx/compatibility)（打开 Zebra 网站），确认创建的配置文件与设备的 MX 版本、OS 版本和型号兼容。
- 某些设备（如 TC20/25 设备）不支持 StageNow 中的所有可用 MX 功能。 请务必检查 [Zebra 的功能矩阵](http://techdocs.zebra.com/mx/tc2x/)（打开 Zebra 的网站），获取更新的支持信息。

## <a name="step-1-install-the-latest-company-portal-app"></a>步骤 1：安装最新的公司门户应用

在设备上，打开 Google Play 存储。 从 Microsoft 下载并安装 Intune 公司门户应用。 从 Google Play 安装后，公司门户应用会自动获取更新和修复程序。

如果无法使用 Google Play，请下载[适用于 Android 的 Microsoft Intune 公司门户](https://www.microsoft.com/download/details.aspx?id=49140)（打开另一个 Microsoft 网站），然后[进行旁加载](#sideload-the-company-portal-app)（本文有介绍）。 以这种方式进行安装，应用不会自动接收更新或修复程序。 确保定期更新并手动修补应用。

### <a name="sideload-the-company-portal-app"></a>旁加载公司门户应用

“旁加载”是指不使用 Google Play 安装应用。 要旁加载公司门户应用，请使用 StageNow。 

以下是大概步骤。 有关具体步骤，请参阅 Zebra 的文档。 可使用：[使用 StageNow 在 MDM 中注册](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/)（打开 Zebra 的网站）。

1. 在 StageNow 中，为“在 MDM 中注册”创建配置文件  。
2. 在“部署”中，选择下载 MDM 代理文件  。
3. 将“支持应用”和“下载配置”步骤设置为“否”    。
4. 在“下载 MDM”中，选择“传输/复制文件”   。 添加公司门户 Android 包 (APK) 的源和目标。
5. 在“启动 MDM”中，按原样保留默认值  。 添加以下详细信息：

    - **程序包名称**：`com.microsoft.windowsintune.companyportal`
    - **类名称**：`com.microsoft.windowsintune.companyportal.views.SplashActivity`

继续发布配置文件，并在设备上的 StageNow 应用中使用该文件。 公司门户应用已在设备上安装并打开。

> [!TIP]
> 有关 StageNow 及其功能的更多信息，请参阅 [StageNow Android 设备暂存](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html)（打开 Zebra 的网站）。

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>步骤 2：确认公司门户应用具有设备管理员角色

公司门户应用需要使用设备管理员来管理 Android 设备。 为激活设备管理员角色，一些 Zebra 设备上会包含用户界面 (UI)。 如果设备包含 UI，则公司门户应用会在[注册](#step-3-enroll-the-device-in-to-intune)期间提示最终用户授予设备管理员权限（本文有介绍）。

如果 UI 不可用，请使用 StageNow 中的“DevAdmin 管理员”创建一个配置文件，手动向公司门户应用授予设备管理员权限  。

以下是大概步骤。 有关具体步骤，请参阅 Zebra 的文档。 
可使用：[以设备管理员身份设置电池交换模式](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool)（打开 Zebra 的网站）。

1. 在 StageNow 中，创建一个配置文件，然后选择“Xpert 模式”  。
2. 将“DevAdmin 管理员”添加到配置文件  。
3. 将“设备管理操作”设置为“以设备管理员身份打开”   。
4. 将“设备管理员包名称”设置为 `com.microsoft.windowsintune.companyportal`  。
5. 将“设备管理员类名”设置为 `com.microsoft.omadm.client.PolicyManagerReceiver`  。

继续发布配置文件，并在设备上的 StageNow 应用中使用该文件。 对公司门户应用授予设备管理员角色。

## <a name="step-3-enroll-the-device-in-to-intune"></a>步骤 3：将设备注册到 Intune

完成前两个步骤后，设备上即安装公司门户应用。 设备已准备好注册到 Intune。

[注册 Android 设备](../enrollment/android-enroll.md)列出了相关步骤。 如果有多个 Zebra 设备，建议使用[设备注册管理器 (DEM) 帐户](../enrollment/device-enrollment-manager-enroll.md)。 使用 DEM 帐户还会删除“从公司门户应用取消注册”选项，以便用户不会轻易取消注册设备。

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>步骤 4：在 StageNow 中创建设备管理配置文件

使用 StageNow 创建配置文件，用于配置要在设备上管理的设置。 有关具体步骤，请参阅 Zebra 的文档。 可使用：[配置文件](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/)（打开 Zebra 网站）。

在 StageNow 中创建配置文件时，在最后一步中，选择“导出到 MDM”  。 此步骤将生成一个 XML 文件。 请保存该文件。 在后面的步骤中需要使用该文件。

- 建议在将配置文件部署到组织中的设备之前对其进行测试。 要对其进行测试，在计算机上使用 StageNow 创建配置文件时，最后一步请使用“测试”选项  。 然后，通过设备上的 StageNow 应用使用 StageNow 生成的文件。

  设备上的 StageNow 应用会显示测试配置文件时生成的日志。 [使用 StageNow 登录 Intune 中运行 Android 的 Zebra 设备](android-zebra-mx-logs-troubleshoot.md)中介绍了如何使用 StageNow 日志来获取错误信息。

- 如果在 StageNow 配置文件中引用应用、更新包或其他文件，设备需要获取这些更新。 要获取更新，设备必须在应用配置文件后连接到 StageNow 部署服务器。 

  或者，可以使用 Intune 中的内置功能来获取这些更改，包括：

  - 用于[添加](../apps/apps-add.md)、[部署](../apps/apps-deploy.md)、更新和[监视](../apps/apps-monitor.md)应用等的应用管理功能。
  - 在运行 Android Enterprise 的设备上管理[系统和应用更新](device-restrictions-android-for-work.md#device-owner-only)

测试文件后，下一步是使用 Intune 将配置文件部署到设备。

- 可以将一个或多个 MX 配置文件部署到设备。
- 还可以导出多个 StageNow 配置文件，并将设置合并为单个 XML 文件。 然后，将 XML 文件上传到 Intune，以便部署到设备。

  > [!WARNING]
  > 如果将多个 MX 配置文件作为同一组的目标，并配置相同的属性，则设备上会出现冲突。
  >
  > 如果在单个 MX 配置文件中多次配置相同的属性，则最后一个配置入选。

## <a name="step-5-create-a-profile-in-intune"></a>步骤 5：在 Intune 中创建配置文件

在 Intune 中，创建设备配置文件：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择 Android  。
    - **配置文件类型**：选择“MX 配置文件”（仅限 Zebra）  。

4. 在“格式为 .xml 的 MX 配置文件”中  ，添加[从 StageNow 导出](#step-4-create-a-device-management-profile-in-stagenow)的 XML 配置文件（本文有介绍）。
5. 选择“确定”   > “创建”  以保存所做的更改。 此时，策略创建完成，并出现在列表中。

    > [!TIP]
    > 出于安全原因，保存后无法看到配置文件 XML 文本。 文本已加密，只能看到星号 (`****`)。 为了便于参考，建议在将 MX 配置文件添加到 Intune 之前保存其副本。

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

下次设备检查配置更新时，MX 配置文件会部署到设备。 设备注册时，会与 Intune 进行同步，然后约每隔 8 小时同步一次。 还可以[在 Intune 中强制执行同步](../remote-actions/device-sync.md)。 或者，在设备上，打开“公司门户应用” > “设置” > “同步”    。 

## <a name="update-a-zebra-mx-configuration-after-its-assigned"></a>在分配斑马 MX 配置后更新该配置

若要更新斑马设备的 MX 特定配置，可以执行以下操作： 

- 创建更新的 StageNow XML 文件，编辑现有 Intune MX 配置文件，并上传新的 StageNow XML 文件。 此新文件将覆盖配置文件中的以前的策略，并替换以前的配置。
- 创建一个新的 StageNow XML 文件，该文件配置不同的设置，创建新的 Intune MX 配置文件，上传新的 StageNow XML 文件，并将其分配给同一个组。 部署了多个配置文件。 如果新配置文件配置了现有配置文件中已存在的设置，则会发生冲突。

## <a name="next-steps"></a>后续步骤

- [分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
- [使用 StageNow 日志对 Zebra 设备进行故障排除](android-zebra-mx-logs-troubleshoot.md)。
