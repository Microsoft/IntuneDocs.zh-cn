---
title: 在 Microsoft Intune 中使用 Android Enterprise 设备上的 OEMConfig - Azure | Microsoft Docs
description: 使用 Microsoft Intune 管理和使用 OEMConfig 的 Android 企业版的设备。 查看所有步骤，包括概述，查看在 Intune 中创建配置文件的先决条件，并查看受支持的 OEMConfig 应用的列表。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
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
ms.openlocfilehash: 8c46caf4d1c9f9a32a7f324fc5e1734dbe8043bd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735254"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>在 Microsoft Intune 中使用和管理 Android 企业设备 OEMConfig

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

在 Microsoft Intune 中，可以使用 OEMConfig 添加、创建和自定义适用于 Android 企业设备的 OEM 特定设置。 OEMConfig 通常用于配置未内置到 Intune 的设置。 不同的原始设备制造商（OEM）包含不同的设置。 可用的设置取决于 OEM 在其 OEMConfig 应用中包含的内容。

此功能适用于：  

- Android Enterprise

本文介绍 OEMConfig，列出了先决条件，演示了如何创建配置文件，并在 Intune 中列出了受支持的 OEMConfig 应用。

## <a name="overview"></a>概述

OEMConfig 策略是一种特殊类型的设备配置策略，类似于[应用配置策略](../apps/app-configuration-policies-overview.md)。 OEMConfig 是 Google 定义的一种标准，该标准利用 Android 中的应用配置将设备设置发送到 Oem 编写的应用（原始设备制造商）。 此标准允许 Oem 和 Emm （企业移动性管理）以标准化的方式构建和支持 OEM 特定功能。 [了解有关 OEMConfig 的详细信息](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/)。

在过去，Emm （如 Intune）在 OEM 引入后，手动构建对 OEM 特定功能的支持。 此方法会导致重复的工作并降低采用速度。

使用 OEMConfig，OEM 可创建定义 OEM 特定管理功能的架构。 OEM 将架构嵌入应用，然后将此应用置于 Google Play 上。 EMM 从应用读取架构，并在 EMM 管理员控制台中显示该架构。 控制台允许 Intune 管理员配置架构中的设置。

当 OEMConfig 应用安装在设备上时，它将使用在 EMM 管理员控制台中配置的设置来管理设备。 设备上的设置由 OEMConfig 应用程序执行，而不是由 EMM 构建的 MDM 代理。

当 OEM 添加并改进管理功能时，OEM 还会更新 Google Play 中的应用程序。 作为管理员，你可以获取这些新功能和更新（包括修补程序），而无需等待 Emm 包含这些更新。

> [!TIP]
> 只能将 OEMConfig 用于支持此功能的设备，并且必须具有相应的 OEMConfig 应用。 请咨询 OEM 了解具体的详细信息。

## <a name="before-you-begin"></a>在开始之前

使用 OEMConfig 时，请注意以下信息：

- Intune 公开 OEMConfig 应用的架构，因此可以对其进行配置。 Intune 不会验证或更改应用提供的架构。 如果架构不正确或数据不准确，则此数据仍将发送到设备。 如果发现架构中出现问题，请联系 OEM 以获得指导。
- Intune 不会影响或控制应用程序架构的内容。 例如，Intune 不能控制字符串、语言、允许的操作，等等。 建议联系 OEM 以获取用 OEMConfig 管理设备的详细信息和最佳实践。
- Oem 可随时更新其支持的功能和架构，并将新应用上传到 Google Play。 Intune 始终从 Google Play 同步最新版本的 OEMConfig 应用。 Intune 不维护旧版本的架构或应用。 如果遇到版本冲突，我们建议联系 OEM 获取详细信息。
- 向设备分配一个 OEMConfig 配置文件。 如果将多个配置文件分配给同一个设备，则可能会出现不一致的行为。 OEMConfig 模型仅支持每个设备一个策略。

## <a name="prerequisites"></a>必备条件

若要在设备上使用 OEMConfig，请确保满足以下要求：

- 在 Intune 中注册的 Android 企业设备。
- 由 OEM 生成并上载到 Google Play 的 OEMConfig 应用。 如果未 Google Play，请与 OEM 联系以获取详细信息。
- Intune 管理员对**移动应用**和**DeviceConfigurations**具有基于角色的访问控制（RBAC）权限。 这些权限是必需的，因为 OEMConfig 配置文件使用托管应用配置来管理设备配置。

## <a name="prepare-the-oemconfig-app"></a>准备 OEMConfig 应用

请确保设备支持 OEMConfig，将正确的 OEMConfig 应用添加到 Intune，并在设备上安装该应用。 请联系 OEM 获取此信息。

> [!TIP] 
> OEMConfig 应用特定于 OEM。 例如，在斑马技术设备上安装的索尼 OEMConfig 应用不会执行任何操作。

1. 从托管 Google Play 商店获取 OEMConfig 应用。 [将托管 Google Play 应用添加到 Android 企业设备](../apps/apps-add-android-for-work.md)列出了步骤。
2. 某些 Oem 可能会附带预装了 OEMConfig 应用的设备。 如果未预安装应用，请使用 Intune[将应用添加到设备并将其部署到设备](../apps/apps-deploy.md)。

## <a name="create-an-oemconfig-profile"></a>创建 OEMConfig 配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Android Enterprise”  。
    - **配置文件类型**：选择**OEMConfig**。

4. 选择 "**关联应用**"，选择之前添加的现有 OEMConfig 应用 > **"确定"** 。 请确保为要将策略分配到的设备选择正确的 OEMConfig 应用。

    如果看不到列出的任何应用，请设置托管 Google Play，并从托管的 Google Play 存储获取应用。 [将托管 Google Play 应用添加到 Android 企业设备](../apps/apps-add-android-for-work.md)列出了步骤。

    > [!IMPORTANT]
    > 如果添加了 OEMConfig 应用并将其同步到 Google Play，但未将其作为关联的**应用**列出，则可能必须联系 Intune 来载入应用。 请参阅[添加新应用](#supported-oemconfig-apps)（在本文中）。

5. 在 "**配置设置**" 中，选择使用**配置设计器**或**JSON 编辑器**：

    > [!TIP]
    > 阅读 OEM 文档，确保你配置的属性正确。 这些应用属性由 OEM 而不是 Intune 提供。 Intune 对属性或输入的内容进行最低限度的验证。 例如，如果为端口号输入 `abcd`，则配置文件将按原样保存，并使用配置的值将其部署到设备。 请确保输入正确的信息。

    - **配置设计器**：如果选择此选项，则会显示应用程序架构中的可用属性，以便您进行配置。

      - 配置设计器中的上下文菜单指示有更多可用选项。 例如，上下文菜单可能允许你添加、删除和重新排列设置。 这些选项由 OEM 提供。 要了解如何使用这些选项来创建配置文件，请务必阅读 OEM 应用文档。

      - 许多设置都具有 OEM 提供的默认值。 若要查看是否有默认值，请将鼠标悬停在该设置旁边的 "信息" 图标上。 工具提示将显示该设置的默认值（如果适用），以及 OEM 提供的更多详细信息。

      - 单击 "**清除**" 将从配置文件中删除设置。 如果配置文件中没有设置，则应用配置文件时，设备上的值不会更改。
        
      - 如果在配置设计器中创建了一个空的（未配置的）捆绑，则在切换到 JSON 编辑器时，会将其删除。

    - **Json 编辑器**：选择此选项时，将打开一个 JSON 编辑器，其中包含应用中嵌入的完整配置架构的模板。 在编辑器中，用不同设置的值自定义模板。 如果使用**配置设计器**来更改值，则 JSON 编辑器将使用配置设计器中的值覆盖模板。
    
      - 如果要更新现有的配置文件，则 JSON 编辑器会显示上次与该配置文件一起保存的设置。

      - OEMConfig 架构可能很大且很复杂。 如果希望使用其他编辑器更新这些设置，请选择 "**下载 JSON 模板**" 按钮。 使用所选的编辑器，将配置值添加到模板。 然后，将更新的 JSON 复制并粘贴到 " **JSON 编辑器**" 属性中。

      - 可以使用 JSON 编辑器创建配置的备份。 配置设置后，请使用此功能获取值的 JSON 设置。 将 JSON 复制并粘贴到文件中，并保存该文件。 现在，你有了一个备份文件。

    在配置设计器中所做的任何更改也会在 JSON 编辑器中自动进行。 同样，在 JSON 编辑器中所做的任何更改都将自动在配置设计器中进行。 如果输入包含无效值，则在解决问题之前无法在配置设计器和 JSON 编辑器之间切换。

6. 选择 **"确定"**  >  "**添加**" 保存更改。 此时，策略创建完成，并出现在列表中。

请务必[分配配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。

 > [!NOTE]
 > 向每个设备分配一个配置文件。 OEMConfig 模型仅支持每个设备一个策略。

下次设备检查配置更新时，你配置的 OEM 特定设置将应用到 OEMConfig 应用。

> [!NOTE]
> OEMConfig 标准当前不包含状态报告。 因此，默认情况下，配置文件显示**挂起**状态。

## <a name="supported-oemconfig-apps"></a>支持的 OEMConfig 应用

与标准应用相比，OEMConfig apps 扩展了 Google 授予的托管配置特权，以支持更复杂的架构。 Intune 当前支持以下 OEMConfig 应用：

-----------------

| OEM | 捆绑 ID | OEM 文档（如果可用） |
| --- | --- | ---|
| Samsung | kpu （.com） | [Knox 服务插件管理员指南](https://docs.samsungknox.com/knox-service-plugin/admin-guide/welcome.htm) |
| 斑马技术 | 斑马. oemconfig | [斑马 OEMConfig 概述](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | datalogic. oemconfig | [Datalogic OEMConfig 的用户文档](https://datalogic.github.io/oemconfig/) |
| Honeywell | honeywell. oemconfig |  |

-----------------

如果设备上存在 OEMConfig 应用程序，但它不在上表中，或未显示在 Intune 控制台中，请通过电子邮件 `IntuneOEMConfig@microsoft.com`。

> [!NOTE]
> OEMConfig 应用必须由 Intune 在载入上进行配置，然后才能使用 OEMConfig 配置文件进行配置。 在应用受支持后，你无需联系 Microsoft，就在你的租户中设置它。 只需按照本页上的说明操作即可。

## <a name="next-steps"></a>后续步骤

- [分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
