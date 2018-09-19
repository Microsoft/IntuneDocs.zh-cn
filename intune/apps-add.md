---
title: 将应用添加到 Microsoft Intune
titlesuffix: ''
description: 了解如何将应用添加到 Microsoft Intune，以便可将应用分配给用户和设备。 Intune 支持多种不同的应用类型。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b5395ed4095280230c9cf678395df03bbce41ea
ms.sourcegitcommit: 8fdddb684ecf5eabf071907168413bcd89a2f702
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141671"
---
# <a name="add-apps-to-microsoft-intune"></a>将应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

必须首先将应用添加到 Microsoft Intune 中，才可分配、监视、配置或保护它们。

公司的应用和设备用户（即公司员工）可能具有多个应用要求。 必须首先评估和了解若干应用基础知识，然后才能将应用添加到 Intune 并向员工提供。 必须了解适用于 Intune 的各种应用。 必须评估应用要求，如员工所需的平台和功能。 必须确定是要使用 Intune 管理设备（包括应用），还是要使用 Intune 管理应用（不包括设备）。 最后，必须确定员工所需的应用和功能，以及需要这些应用和功能的具体人员。 本文的信息可帮助你开始使用。

## <a name="app-types-in-microsoft-intune"></a>Microsoft Intune 中的应用类型

Intune 支持多种不同的应用类型。 为每种应用类型提供的可用选项有所不同。 Intune 支持添加并分配以下类型的应用：

| 应用类型 | 安装 | Updates |
|---|---|---|
| 应用商店中的应用（应用商店应用） | Intune 在设备上安装应用。  | 应用是自动更新的。   |
| 内部编写的应用（业务线）  | Intune 在设备上安装应用（需要提供安装文件）。     | 必须更新应用。  |
| 内置的应用（内置应用）    | Intune 在设备上安装应用。  | 应用是自动更新的。  |
| Web 上的应用（Web 链接） | Intune 在设备主屏幕上创建一个到 Web 应用的快捷方式。  | 应用是自动更新的。    |

### <a name="specific-app-type-details"></a>特定应用类型详细信息
 
下表列出了特定应用类型，以及如何在 Intune 的“添加应用”窗格中添加它们：

| **特定于应用的类型** | **常规类型** | **特定于应用的过程** |
| --- | --- | --- |
| Android 应用商店应用  | 应用商店应用  | 选择“Android”作为“应用类型”，然后输入应用的 Google Play 应用商店 URL。 |
| iOS App Store 应用  | 应用商店应用  | 选择“iOS”作为“应用类型”，搜索应用，然后在 Intune 内选择该应用。 |
| Windows Phone 8.1 应用商店应用  | 应用商店应用  | 选择“Windows Phone 8.1”作为“应用类型”，然后输入应用的 Microsoft 应用商店 URL。 |
| Microsoft 应用商店应用  | 应用商店应用  | 选择“Windows”作为“应用类型”，然后输入应用的 Microsoft 应用商店 URL。 |
| Android 工作配置文件应用 | 应用商店应用  | 从托管 Google Play 商店中找到并批准 Android 工作配置文件应用。  |
| 适用于 Windows 10 的 Office 365 应用  | 应用商店应用 (Office 365) | 在“Office 365 套件”下选择“Windows 10”作为“应用类型”，然后选择要安装的 Office 365 应用。  |
| 适用于 macOS 的 Office 365 应用 | 应用商店应用 (Office 365) | 在“Office 365 套件”下选择“macOS”作为“应用类型”，然后选择 Office 365 应用套件。 |
| Android 业务线 (LOB) 应用 | LOB 应用 | 选择“业务线应用”作为“应用类型”，选择“应用包文件”，然后输入扩展名为 .apk 的 Android 安装文件。  |
| iOS LOB 应用 | LOB 应用 | 选择“业务线应用”作为“应用类型”，选择“应用包文件”，然后输入扩展名为 .ipa 的 iOS 安装文件。  |
| Windows Phone LOB 应用 | LOB 应用 | 选择“业务线应用”作为“应用类型”，选择“应用包文件”，然后输入扩展名为 .xap 的 Windows Phone 安装文件。  |
| Windows LOB 应用 | LOB 应用 | 选择“业务线”应用作为应用类型，选择“应用包文件”，然后输入扩展名为 .msi、.appx、.appxbundle、.msix 和 .msixbundle 的 Windows 安装文件。 |
| 内置的 iOS 应用  | 内置应用 | 选择“内置应用”作为“应用类型”，然后从提供的应用列表中选择内置应用。  |
| 内置的 Android 应用  | 内置应用 | 选择“内置应用”作为“应用类型”，然后从提供的应用列表中选择内置应用。  |
| Web 应用  | Web 应用  | 选择“Web 链接”作为应用类型，然后输入指向该 Web 应用的有效 URL。  |

可以在 Microsoft Intune 中添加应用，方法是通过选择“客户端应用” > “应用” > “添加”。 将显示“添加应用”窗格，可选择“应用类型”。 

>[!TIP]
> LOB 应用是从应用安装文件添加的应用。 例如，若要安装 iOS LOB 应用，可以通过在“添加应用”窗格选择“业务线应用”作为“应用类型”来添加应用程序。 然后，选择应用包文件（扩展名为 .ipa）。 这些应用类型通常为内部编写。

## <a name="assess-app-requirements"></a>评估应用要求
作为 IT 管理员，不仅可以确定你的组必须要使用的应用，而且可以确定每个组和子组所需的功能。 对于每个应用，应确定所需平台、需要应用的用户组、要为这些组应用的配置策略和要应用的保护策略。  

此外，还必须确定是否要将重点放在移动设备管理 (MDM) 上或者仅放在移动应用程序管理 (MAM) 上。 

使用 Intune 以通过 MDM 管理设备在以下情况下非常有用：
- 用户需要 Wi-Fi 或 VPN 企业连接配置文件以实现高效工作。
- 用户需要一组应用推送到他们的设备。
- 组织需要符合强调特定 MDM 控制（例如安全性或加密）的法规或其他策略。

当不管理设备时，使用 Intune 以通过 MAM 管理应用在以下情况下非常有用：
- 需要使用户能够使用他们自己的设备 (BYOD)。
- 需要提供一次性弹出消息，让用户了解 MAM 保护已就绪，而不是提供持续的设备级通知。
- 需要符合一些策略的要求，这些策略对个人设备需要较少的管理功能。 例如，需要管理应用的公司数据，而不是管理整个设备的公司数据。

有关详细信息，请参阅[比较 MDM 和 MAM](byod-technology-decisions.md)。

### <a name="determine-who-will-use-the-app"></a>确定谁将使用应用

在确定员工需要哪些应用时，请考虑各种用户组以及他们使用的各种应用。 在添加应用之后，了解这些组也很有用。 添加应用后，可以分配一组能够使用此应用的用户。 

首先，必须根据应用所包含数据的敏感性确定应该有权访问应用的组。 可能需要包括或排除组织中某些类型的角色。 例如，销售组可能仅需要某些 LOB 应用，而侧重于工程、财务、人力资源或法律的人员可能不需要使用 LOB 应用。 此外，销售组人员的移动设备上可能需要额外的数据保护以及对内部公司服务的访问权。 必须确定此组将如何使用应用连接到资源。 应用访问的数据将保留在云中还是本地？ 同时，用户将如何使用应用连接到资源？ 

Intune 还支持对需要安全访问本地数据的移动应用（例如业务线应用服务器）启用访问权限。 提供此类型的访问通常需要将用于访问控制的 [Intune 托管证书](certificates-configure.md)与外围中的标准 VPN 网关或代理（例如 Azure Active Directory 应用程序代理）结合使用。 可以借助 Intune 的[应用包装工具和应用 SDK](apps-prepare-mobile-application-management.md) 将已访问的数据包含在业务线应用中，这样它就不能将公司数据传递给使用者应用或服务。

使用 [Intune 部署规划、设计和实施指南](planning-guide.md)帮助确定如何标识与每个用例和子用例方案相关联的组织组。 有关将应用分配到组的信息，请参阅[使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

### <a name="determine-the-type-of-app-for-your-solution"></a>为解决方案确定应用的类型

可从以下应用类型中进行选择：
- 应用商店中的应用：上传到 Microsoft 应用商店、iOS 应用商店或 Android 应用商店的应用是应用商店应用。 应用商店应用的提供者对应用进行维护并提供更新。 在应用商店列表选择应用，并使用 Intune 将其添加为用户的可用应用。
- 内部编写的应用（业务线）：内部创建的应用是业务线 (LOB) 应用。 此应用类型的功能已为一些支持 Intune 的平台创建，例如 Windows、iOS 或 Android。 组织创建更新并将这些更新作为单独的文件提供给你。 可以通过使用 Intune 添加和部署更新为用户提供应用更新。
- Web 上的应用：Web 应用是客户端-服务器应用程序。 服务器提供 Web 应用，其中包括 UI、内容和功能。 此外，新式 Web 托管平台通常会提供安全性、负载均衡和其他优势。 此应用类型是在 Web 上单独进行维护的。 可以使用 Intune 指向此应用类型。 还可以指定哪组用户可以访问此应用。 请注意，Android 不支持 Web 应用。

确定组织需要的应用时，请考虑这些应用如何与云服务集成，应用访问什么数据，应用是否对 BYOD 用户可用以及应用是否需要 Internet 访问。

有关组织需要的应用类型的详细信息，请参阅[创建设计](planning-guide-design.md#feature-requirements)的“功能要求”部分中的“应用”部分。

### <a name="understanding-app-management-and-protection-policies"></a>了解应用管理和保护策略
通过 Intune 可以修改所部署应用程序的功能，帮助这些应用符合公司的符合性和安全性策略。 此操作使你可以确定如何保护公司数据。 Intune 托管应用是通过一组丰富的移动应用程序保护策略启用的，例如：

- 限制“复制和粘贴”和“另存为”功能。
- 将 Web 链接配置为在 Intune Managed Browser 应用中打开。
- 启用多标识使用和应用级条件访问。

Intune 托管应用还可以启用应用保护，而无需注册，使你能够在不管理用户设备的情况下即可应用数据丢失防护策略。 此外，还可以使用 Intune App SDK 和应用包装工具在移动和业务线应用中进行移动应用管理。 有关这些工具的详细信息，请参阅 [Intune App SDK 概述](app-sdk.md)。

### <a name="understanding-licensed-apps"></a>了解获得许可的应用
除了了解 Web 应用、应用商店应用和 LOB 应用，还应注意批量采购计划的应用和获得许可的应用的目标，例如： 
- 适用于企业的 Apple 批量采购计划 (iOS)：在 iOS 应用商店中，可以购买要在公司中运行的应用的多个许可证。 购买多个副本可帮助你有效地管理公司的应用。 有关详细信息，请参阅[管理批量购买的 iOS 应用](vpp-apps-ios.md)。
- Android 工作配置文件：可采用与将应用分配到标准 Android 设备不同的方式，将应用分配到 Android 工作配置文件设备。 为 Android 工作配置文件安装的所有应用都来自托管 Google Play 商店。 登录到该商店，浏览查找所需应用，然后批准它们。 然后，该应用会显示在 Azure 门户的“许可的应用”节点中，可以像管理任何其他应用一样管理应用的分配。
- 适用于企业的 Microsoft Store (Windows 10)：可在适用于企业的 Microsoft Store 中为组织查找和购买应用（单个或批量）。 通过将此应用商店与 Microsoft Intune 相连，可以在 Azure 门户中管理批量购买的应用。 有关详细信息，请参阅[管理来自适用于企业的 Microsoft Store 的应用](windows-store-for-business.md)。

    > [!NOTE]
    > Windows 应用的文件扩展名包括 .msi、.appx、.appxbundle、.msix 和 .msixbundle。  

## <a name="before-you-add-apps"></a>添加应用之前
在开始添加和分配应用之前，请考虑以下几点：

- 如果要从应用商店添加和分配应用，用户必须具有该应用商店的帐户才能安装应用。
- 某些分配的应用或项目可能依赖于内置的 iOS 应用。 例如，如果要在 iOS 应用商店分配一本书，则 iBooks 应用必须在设备上存在。 如果已经删除了 iBooks 内置应用，则无法使用 Intune 将其恢复。

> [!IMPORTANT]
> 如果在部署并安装应用后通过 Intune Azure 门户更改应用的名称，则将无法再使用命令来定位应用。

## <a name="cloud-storage-space"></a>云存储空间
使用软件安装程序安装类型（例如，业务线应用）创建的所有应用都必须打包并上载到 Intune 云存储中。 Intune 的试用订阅包括 2 GB 的云存储空间，用于存储托管应用和更新。 完整订阅不会限制存储空间总量。

云存储空间的要求如下：

- 所有应用安装文件都必须位于同一文件夹内。
- 上载的任意文件的文件大小不得超过 2 GB。

## <a name="create-and-edit-categories-for-apps"></a>创建和编辑应用类别

应用类别可用于对应用进行排序，让用户在公司门户中更容易查找应用。 可以向应用分配一个或多个类别（例如，“开发者应用”或“通信应用”）。

向 Intune 添加应用时，可以视需要选择所需的类别。 请参阅平台专属主题，了解如何添加应用并分配类别。 若要创建和编辑你自己的类别，请按以下过程操作：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“客户端应用”。
4. 在“客户端应用”工作负载窗格的“设置”下，选择“应用类别”。  
    “应用类别”窗格显示当前类别的列表。 
5. 执行以下任一操作：
    - 若要添加一个类别，在“创建类别”窗格中选择“添加”，然后输入类别的名称。  
    只能使用一种语言输入名称，并且 Intune 不会进行翻译。
    - 若要编辑类别，请选择类别旁边的省略号 (...)，然后选择“固定到仪表板”或“删除”。
6. 选择“创建”。

## <a name="apps-that-are-added-automatically-by-intune"></a>Intune 自动添加的应用

之前，Intune 包含了一些可供快速分配的内置应用。 根据 Intune 客户反馈，我们删除了此列表，并且不再显示内置应用。 但是，如果你已分配任何内置应用，则在应用列表中仍会看到这些应用。 可以根据需要继续分配这些应用。

> [!NOTE]
> 对于安装所需的非业务线应用，假定未检测到应用且应用的安装状态不是“安装挂起”，则 Intune 将尝试通过在每次设备签入时发送安装命令来安装该应用。

## <a name="installing-updating-or-removing-required-apps"></a>安装、更新或删除所需应用

Intune 将在 24 小时内自动重新安装、更新或删除所需应用，而不必等待 7 天的重新评估周期。

Intune 会根据以下条件自动重新安装、更新或删除所需应用：
- 如果最终用户卸载你要求安装在其设备上的应用，则在该时间计划过去时 Intune 将自动重新安装该应用。
- 如果必需的应用安装失败或设备上不存在该应用，Intune 将评估符合性并在此时间计划过后重新安装该应用。  
- 管理员将应用定位为可供用户组使用且最终用户可从设备上的公司门户安装的应用。 之后，管理员会将应用从 v1 更新到 v2。 Intune 会在此时间计划过去时更新应用，前提是应用的任何早期版本仍然在设备上。
- 如果管理员部署卸载意向并且该设备上存在此应用且卸载失败，Intune 会评估符合性，并在该时间计划过去时卸载该应用。   

## <a name="app-installation-errors"></a>应用安装错误

有关 Intune 应用安装错误的详细信息，请参阅[应用安装错误](troubleshoot-app-install.md#app-installation-errors)。

## <a name="next-steps"></a>后续步骤

若要了解如何将每个平台的应用添加到 Intune，请参阅：

- [Android 应用商店应用](store-apps-android.md)
- [Android LOB 应用](lob-apps-android.md)
- [iOS App Store 应用](store-apps-ios.md)
- [iOS LOB 应用](lob-apps-ios.md)
- [Web 应用（适用于所有平台）](web-app.md)
- [Windows Phone 8.1 应用商店应用](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB 应用](lob-apps-windows-phone.md)
- [Microsoft Store 应用](store-apps-windows.md)
- [Windows LOB 应用](lob-apps-windows.md)
- [适用于 Windows 10 的 Office 365 应用](apps-add-office365.md)
- [适用于 macOS 的 Office 365 应用](apps-add-office365-macos.md)
- [内置应用](apps-add-built-in.md)
