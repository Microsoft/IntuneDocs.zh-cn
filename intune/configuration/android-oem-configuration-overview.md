---
title: 在 Microsoft Intune 中使用 Android Enterprise 设备上的 OEMConfig - Azure | Microsoft Docs
description: 使用 Microsoft Intune 管理和使用通过 OEMConfig 运行 Android 企业版的设备。 查看所有步骤（包括概述），查看先决条件，在 Intune 中创建配置文件，并查看受支持的 OEMConfig 应用列表。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cc568cbadb683f632ffd2365ab7023cd796f231
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886688"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>在 Microsoft Intune 中通过 OEMConfig 使用和管理 Android 企业版设备

在 Microsoft Intune 中，可使用 OEMConfig 添加、创建和自定义适用于 Android 企业版设备的特定于 OEM 的设置。 OEMConfig 通常用于配置未内置到 Intune 的设置。 不同的原始设备制造商 (OEM) 包含不同的设置。 可用设置取决于 OEM 在其 OEMConfig 应用中包含的内容。

此功能适用于：  

- Android Enterprise

本文介绍 OEMConfig，列出了先决条件，演示了如何创建配置文件，并列出了 Intune 中支持的 OEMConfig 应用。

## <a name="overview"></a>概述

OEMConfig 策略是一种特殊类型的设备配置策略，类似于[应用配置策略](../apps/app-configuration-policies-overview.md)。 OEMConfig 是 Google 定义的一种标准，它使用 Android 中的应用配置将设备设置发送到由 OEM（原始设备制造商）编写的应用。 此标准允许 OEM 和 EMM（企业移动性管理）按照标准方式构建和支持特定于 OEM 的功能。 [了解有关 OEMConfig 的详细信息](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/)。

在过去，EMM（如 Intune）在其由 OEM 进行引入后，会手动构建对特定于 OEM 功能的支持。 此方法会导致重复工作、降低采用速度。

通过 OEMConfig，OEM 可创建架构来定义特定于 OEM 的管理功能。 OEM 将该架构嵌入应用，然后将此应用上架 Google Play。 EMM 从应用读取架构，并在 EMM 管理员控制台中公开该架构。 Intune 管理员可通过该控制台配置架构中的设置。

当 OEMConfig 应用安装在设备上时，它将使用在 EMM 管理员中配置的设置来管理设备。 设备设置由 OEMConfig 应用（而不是 EMM 构建的 MDM 代理）执行。

当 OEM 添加并改进管理功能时，该 OEM 也会在 Google Play 中更新该应用。 作为管理员，你可以获取这些新功能和更新（包括修补程序），而无需等待 EMM 包含这些更新。

> [!TIP]
> 只能将 OEMConfig 用于支持此功能且具有相应 OEMConfig 应用的设备。 请咨询 OEM 了解具体的详细信息。

## <a name="before-you-begin"></a>在开始之前

使用 OEMConfig 时，请注意以下信息：

- Intune 公开了 OEMConfig 应用的架构，因此你可以对其进行配置。 Intune 不会验证或更改应用提供的架构。 因此，如果架构不正确或数据不准确，此数据仍将发送到设备。 如果你发现起源于架构的问题，请联系 OEM 以获得指导。
- Intune 不会影响或控制应用架构的内容。 例如，Intune 不能控制字符串、语言、允许的操作等。 建议联系 OEM 以获取有关通过 OEMConfig 管理设备的详细信息。
- OEM 可随时更新其支持的功能和架构，并将新应用上传到 Google Play。 Intune 会始终从 Google Play 同步最新版本的 OEMConfig 应用。 Intune 不维护旧版本的架构或应用。 如果遇到版本冲突，建议联系 OEM 获取详细信息。
- 向设备分配一个 OEMConfig 配置文件。 如果将多个配置文件分配给同一个设备，则可能会出现不一致的行为。 OEMConfig 模型仅支持每台设备一个策略。

## <a name="prerequisites"></a>必备条件

若要在设备上使用 OEMConfig，请确保满足以下要求：

- 在 Intune 中注册的 Android 企业版设备。
- 由 OEM 构建并上传到 Google Play 的 OEMConfig 应用。 如果其未在 Google Play 上，请与 OEM 联系以获取详细信息。
- Intune 管理员对“移动应用”、“设备配置”和“Android for Work”下的“读取”权限具有基于角色的访问控制 (RBAC) 权限    。 这些权限是必需的，因为 OEMConfig 配置文件使用托管的应用配置来管理设备配置。

## <a name="prepare-the-oemconfig-app"></a>准备 OEMConfig 应用

请确保设备支持 OEMConfig，正确的 OEMConfig 应用已添加到 Intune，且应用已安装在设备上。 请与 OEM 联系以获取此信息。

> [!TIP] 
> OEMConfig 应用特定于 OEM。 例如，安装在 Zebra Technologies 设备上的 Sony OEMConfig 应用不会执行任何操作。

1. 从托管的 Google Play 商店获取 OEMConfig 应用。 [将托管 Google Play 应用添加到 Android 企业设备](../apps/apps-add-android-for-work.md)列出了步骤。
2. 某些 OEM 可能会附带预装了 OEMConfig 应用的设备。 如果未预安装该应用，请使用 Intune [将应用添加并部署到设备](../apps/apps-deploy.md)。

## <a name="create-an-oemconfig-profile"></a>创建 OEMConfig 配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **平台**：选择“Android Enterprise”  。
    - **配置文件类型**：选择“OEMConfig”  。

4. 选择“创建”。 
5. 在“基本信息”  中，输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **描述**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **OEMConfig 应用**：选择“选择 OEMConfig 应用”  。

6. 在“已关联应用”中，选择以前添加的现有 OEMConfig 应用 >“选择”   。 请确保为要为其分配策略的设备选择正确的 OEMConfig 应用。

    如果未看到列出任何应用，请设置托管 Google Play，并从托管 Google Play 商店获取应用。 [将托管 Google Play 应用添加到 Android 企业设备](../apps/apps-add-android-for-work.md)列出了步骤。

    > [!IMPORTANT]
    > 如果你添加了 OEMConfig 应用并将其同步到 Google Play，但该应用未列出为“已关联应用”，那么你可能必须联系 Intune 来载入该应用  。 请参阅[添加新应用](#supported-oemconfig-apps)（在本文中）。

7. 选择“下一步”  。
8. 在“配置设置”中，选择“配置设计器”或“JSON 编辑器”    ：

    > [!TIP]
    > 请阅读 OEM 文档，确保你已正确配置了属性。 这些应用属性包含在 OEM 而不是 Intune 中。 Intune 对属性或输入的内容进行最低程度的验证。 例如，如果输入 `abcd` 作为端口号，则配置文件将按原样保存，并使用你配置的值部署到设备。 请确保输入正确的信息。

    - **配置设计器**：如果选择此选项，则会显示应用架构中的可用属性，以便你进行配置。

      - 配置设计器中的上下文菜单指示有更多可用选项。 例如，也许可通过上下文菜单添加、删除和重新排列设置。 这些选项包含在 OEM 中。 要了解如何使用这些选项来创建配置文件，请务必阅读 OEM 应用文档。

      - 许多设置都具有 OEM 提供的默认值。 若要查看是否有默认值，请将鼠标悬停在该设置旁边的“信息”图标上。 工具提示将显示该设置的默认值（如果适用），以及 OEM 提供的更多详细信息。

      - 单击“清除”将从配置文件中删除设置  。 如果配置文件中没有设置，则应用配置文件时，设备上的值不会更改。

      - 如果在配置设计器中创建空的（未配置的）捆绑，切换到 JSON 编辑器时会将其删除。

    - **JSON 编辑器**：选择此选项时，将打开 JSON 编辑器，其中包含应用中嵌入的完整配置架构的模板。 在编辑器中，使用不同设置的值来自定义该模板。 如果使用“配置设计器”来更改值，则 JSON 编辑器将使用配置设计器中的值覆盖模板  。

      - 如果要更新现有的配置文件，则 JSON 编辑器会显示上次与该配置文件一起保存的设置。

      - OEMConfig 架构可能很大且很复杂。 如果希望使用其他编辑器更新这些设置，请选择“下载 JSON 模板”按钮  。 使用所选的编辑器，将配置值添加到模板。 然后，将更新后的 JSON 复制并粘贴到“JSON 编辑器”属性中  。

      - 你可以使用 JSON 编辑器来创建配置的备份。 配置设置后，请使用此功能获取带有值的 JSON 设置。 将 JSON 复制并粘贴到文件中，并保存该文件。 现在，你有了一个备份文件。

    在配置设计器中所做的任何更改也会在 JSON 编辑器中自动进行。 同样，在 JSON 编辑器中所做的任何更改都将在配置设计器中自动进行。 如果输入包含无效值，则在解决该问题之前无法在配置设计器和 JSON 编辑器之间切换。

9. 选择“下一步”  。
10. 在“作用域标记”（可选）中，分配一个标记以将配置文件筛选到特定 IT 组（如 `US-NC IT Team` 或 `JohnGlenn_ITDepartment`）  。 有关范围标记的详细信息，请参阅[将 RBAC 和范围标记用于分布式 IT](../fundamentals/scope-tags.md)。

    选择“下一步”  。

11. 在“分配”中，选择将接收配置文件的用户或组  。 向每个设备分配一个配置文件。 OEMConfig 模型仅支持每台设备一个策略。

    有关分配配置文件的详细信息，请参阅[分配用户和设备配置文件](device-profile-assign.md)。

    选择“下一步”  。

12. 在“查看并创建”中查看设置  。 选择“创建”时，将保存所做的更改并分配配置文件  。 该策略也会显示在配置文件列表中。

下次设备检查配置更新时，你配置的特定于 OEM 的设置将应用到 OEMConfig 应用。

> [!NOTE]
> OEMConfig 标准当前不包含状态报告。 因此，默认情况下，配置文件显示“挂起”状态  。

## <a name="supported-oemconfig-apps"></a>支持的 OEMConfig 应用

与标准应用相比，OEMConfig apps 扩展了 Google 授予的托管配置特权，以支持更复杂的架构。 Intune 当前支持以下 OEMConfig 应用：

-----------------

| OEM | 捆绑 ID | OEM 文档（如果可用） |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Knox 服务插件管理员指南](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra Technologies | com.zebra.oemconfig.common | [Zebra OEMConfig 概述](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [Datalogic OEMConfig 用户文档](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink - 条形码 | com.spectralink.barcode.service |  |
| Spectralink - 按钮 | com.spectralink.buttons |  |
| Spectralink - 设备 | com.spectralink.slnkdevicesettings  |  |
| Spectralink - 日志记录 | com.spectralink.slnklogger |  |
| Spectralink - VQO | com.spectralink.slnkvqo |  |
| HMD 全球 | com.hmdglobal.app.oemconfig.ironman |  |

-----------------

如果存在适用于你的设备的 OEMConfig 应用程序，但它未显示在上表中，或未显示在 Intune 控制台中，请发送电子邮件到 `IntuneOEMConfig@microsoft.com`。

> [!NOTE]
> OEMConfig 应用必须先由 Intune 进行载入，然后才能使用 OEMConfig 配置文件进行配置。 应用受支持后，你无需就在租户中对其进行设置与 Microsoft 联系。 只须按照此页面上的指令进行操作即可。

## <a name="next-steps"></a>后续步骤

[监视配置文件状态](device-profile-monitor.md)。
