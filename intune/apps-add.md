---
title: "如何将应用添加到 Microsoft Intune"
titlesuffix: Azure portal
description: "这些过程可助你将应用添加到 Intune，做好分配到用户和设备的准备。 \""
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f84adced59d2057cd4d18f05ff6953293f7c44cc
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>如何向 Microsoft Intune 添加应用

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

必须首先将应用添加到 Intune 中，才可以分配、监视、配置或保护它们。 Intune 支持多种不同的应用类型。 为每种应用类型提供的可用选项有所不同。

Intune 支持添加并分配以下类型的应用：
| 应用类型                                  | 安装                                                                  | 更新                       |
|------------------------------------------ |----------------------------------------------------------------------------   |---------------------------    |
| Web 上的应用                           | Intune 在设备主屏幕上创建一个到 Web 应用的快捷方式          | 应用是自动更新的     |
| 内部编写的应用（业务线）  | Intune 在设备上安装应用（你需要提供安装文件）    | 必须手动更新应用       |
| 应用商店中的应用                       | Intune 在设备上安装应用                                       | 应用是自动更新的     |


除了 Web 应用，Intune 还支持以下适用于应用商店应用和 LOB 应用的特定平台：
- 应用商店应用
    - Android 应用商店应用
    - iOS App Store 应用
    - Windows Phone 8.1 应用商店应用
    - Windows 应用商店应用
    - Android for Work 应用
    - 适用于 Windows 的 Office 365 应用
    - 适用于 macOS 的 Office 365 应用
- 生成你的应用 - 业务线 (LOB)
    - Android 业务线 (LOB) 应用
    - iOS 业务线 (LOB) 应用
    - Windows Phone 业务线 (LOB) 应用（.xap 文件）
    - Windows 业务线 (LOB) 应用（仅限 .msi 文件）

>[!TIP]
> 业务线 (LOB) 应用是从应用安装文件添加的应用。 例如，若要安装 iOS LOB 应用，可以通过从“添加应用”边栏选项卡选择“业务线应用”作为“应用类型”以添加应用程序。 然后，选择应用包文件（扩展名为 .ipa）。 这些应用类型通常为内部编写。

## <a name="assess-application-requirements"></a>评估应用程序要求 
作为 IT 管理员，不仅必须确定你的组必须要使用的应用，而且必须确定每个组和子组所需的功能。 对于每个应用，必须确定所需平台、需要应用的用户组、要为这些组应用的配置策略和要应用的保护策略。  

此外，还必须确定是否需要将重点放在移动设备管理 (MDM) 上或者仅放在移动应用程序管理 (MAM) 上。 使用 Intune 来管理设备（移动设备管理）在以下情况中非常有用：
- 用户需要 WiFi 或 VPN 企业连接配置文件以实现高效工作。
- 用户需要一组应用推送到他们的设备。
- 组织需要符合强调特定移动设备管理 (MDM) 控制（例如安全性或加密）的法规或其他策略。

当不管理设备时，使用 Intune 来管理应用（移动应用程序管理）在以下情况中非常有用：
- 需要使用户能够使用他们自己的设备 (BYOD)。
- 需要提供一次性弹出窗口，让用户了解 MAM 保护已就绪，而不是提供持续的设备级通知。
- 需要符合一些策略，这些策略对个人设备的管理功能需要较少。 例如，需要管理应用的公司数据，而不是管理整个设备的公司数据。

有关详细信息，请参阅[比较 MDM 和 MAM](byod-technology-decisions.md)。

### <a name="determine-who-will-use-the-app"></a>确定谁将使用应用
将应用添加到 Intune 后，则可以分配一组能够使用此应用的用户。 首先，必须根据应用所包含数据的敏感性确定应该有权访问应用合适的组。 可能需要包括或排除组织中某些类型的角色。 例如，销售组可能仅需要某些 LOB 应用，而侧重于工程、财务、人力资源或法律的人员可能不需要使用 LOB 应用。 此外，销售组人员的移动设备上可能需要额外的数据保护以及对内部公司服务的访问权。 必须确定此组将如何使用应用连接到资源。 应用访问的数据将保留在云中还是本地？ 同时，用户将如何使用应用连接到资源。 Intune 还支持对需要安全访问本地数据的移动应用（例如业务线应用服务器）启用访问权限。 实现此类型的访问通常需要将用于访问控制的 [Intune 托管证书](certificates-configure.md)与外围中的标准 VPN 网关或代理（例如 Microsoft Azure Active Directory 应用程序代理）结合使用。 可以借助 Intune 的[应用包装工具和应用 SDK](apps-prepare-mobile-application-management.md) 将已访问的数据包含在业务线应用中，这样它就不能将公司数据传递给使用者应用或服务。

使用 [Intune 部署规划、设计和实施指南](planning-guide.md)帮助确定如何标识与每个用例和子用例方案相关联的组织组。 有关将应用分配到组的详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。 

### <a name="determine-the-type-of-app-for-your-solution"></a>为解决方案确定应用的类型
可以在以下应用类型中进行选择：
- **Web 上的应用** - Web 应用是客户端-服务器应用程序。 服务器提供 Web 应用，其中包括 UI、内容和功能。 此外，新式 Web 托管平台通常会提供安全性、负载均衡和其他优势。 此应用类型是在 Web 上单独进行维护的。 可以使用 Intune 指向此应用类型。 还可以分配哪组用户可以访问此应用。 请注意，Android 不支持 Web 应用。
- **内部编写的应用（业务线）** - 内部创建的应用是业务线 (LOB) 应用。 此应用类型的功能已为一些支持 Intune 的平台创建，例如 Windows、iOS 或 Android。 组织创建更新并将这些更新作为单独的文件提供给你。 可以通过使用 Intune 添加和部署更新为用户提供应用更新。 
- **应用商店中的应用** - 应用商店应用是上传到 Windows 应用商店、iOS 应用商店或 Android 应用商店的应用。 应用商店应用的提供者对应用进行维护并提供更新。 从应用商店列表选择应用，并使用 Intune 将其添加为用户的可用应用。

确定组织的所需应用时，请考虑这些应用如何与云服务集成，应用访问什么数据，应用是否对 BYOD 用户可用以及应用是否需要 Internet 访问。

有关确定组织所需应用类型的详细信息，请参阅[创建设计](planning-guide-design.md#feature-requirements)的“功能要求”部分中的“应用”。

### <a name="understanding-app-management-and-protection-policies"></a>了解应用管理和保护策略
通过 Intune 可以修改所部署应用程序的功能，帮助这些应用符合公司的符合性和安全性策略。 此操作使你可以确定如何保护公司数据。 Intune 托管应用是通过一组丰富的移动应用程序保护策略启用的，例如：

- 限制“复制和粘贴”和“另存为”功能
- 将 Web 链接配置为在 Intune Managed Browser 应用中打开
- 启用多标识使用和应用级条件访问

Intune 托管应用还可以启用应用保护，而无需注册，使你能够在不管理用户设备的情况下即可应用数据丢失防护策略。 此外，可以使用 Intune App 软件开发工具包和应用包装工具在移动和业务线应用中进行移动应用管理。 有关这些工具的详细信息，请参阅 [Intune App SDK 概述](app-sdk.md)。

### <a name="understanding-licensed-apps"></a>了解获得许可的应用
除了 Web 应用、应用商店应用和 LOB 应用，还应该注意批量采购计划的应用和获得许可的应用的区别，例如：     
- **适用于企业的 Apple 批量采购计划（iOS 和 MacOS）** - 在 iOS 应用商店中，可以购买要在公司中运行的应用的多个许可证。 购买多个副本可帮助你有效地管理公司的应用。 有关详细信息，请参阅[管理批量购买的 iOS 应用](vpp-apps-ios.md)。
- **Android for Work (Android)** - 可采用与将应用分配到标准 Android 设备不同的方式，将应用分配到 Android for Work 设备。 为 Android for Work 安装的所有应用都来自 Google Play for Work 商店。 登录到该商店，浏览查找所需应用，然后批准它们。 应用随后会出现在 Azure 门户的“获得许可的应用”节点中。 在这里，可以采用与分配任何其他应用相同的方式管理应用的分配。
- **适用于企业的 Windows Store (Windows 10)** - 可在适用于企业的 Microsoft Store 中为组织查找和购买应用（单个或批量）。 通过将此应用商店与 Microsoft Intune 相连，可以在 Azure 门户中管理批量购买的应用。 有关详细信息，请参阅[管理来自适用于企业的 Microsoft Store 的应用](windows-store-for-business.md)。 

## <a name="before-you-start"></a>准备工作
在开始添加和分配应用之前，请考虑以下几点。

- 如果要从应用商店添加和分配应用，最终用户必须具有该应用商店的帐户才能安装应用。
- 某些分配的应用或项目可能依赖于内置的 iOS 应用。 例如，如果要从 iOS 应用商店分配一本书，则 iBooks 应用必须在设备上存在。 如果已经删除了 iBooks 内置应用，则无法使用 Intune 将其恢复。

## <a name="cloud-storage-space"></a>云存储空间
使用软件安装程序安装类型（例如，业务线应用）创建的所有应用都必须打包并上载到 Intune 云存储中。 Intune 的试用订阅包括 2 GB 的云存储空间，用于存储托管应用和更新。 完整订阅包括 20 GB 的存储空间。

可以使用原始购买方式购买额外的 Intune 存储空间。  如果是通过发票或信用卡付款，请访问[订阅管理门户](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)。  否则，请联系合作伙伴或销售内勤。

云存储空间的要求如下：

-   所有应用安装文件都必须位于同一文件夹内。
-   上载的任意文件的文件大小不得超过 2 GB。

## <a name="how-to-create-and-edit-categories-for-apps"></a>如何创建和编辑应用类别

应用类别可用于对应用进行排序，让用户在公司门户中更容易查找应用。 可以向应用分配一个或多个类别（例如，“开发者应用”或“通信应用”）。
向 Intune 添加应用时，可以视需要选择所需的类别。 请参阅平台专属主题，了解如何添加应用并分配类别。 若要创建和编辑你自己的类别，请按以下过程操作：

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“移动应用”。
4. 在“移动应用”工作负荷中，选择“设置” > “应用类别”。
5. “应用类别”边栏选项卡上显示当前类别列表。 选择执行下列操作之一：
    - **创建类别** - 选择“添加”以显示“创建类别”边栏选项卡，然后为新类别添加名称。 只能使用一种语言输入名称，并且 Intune 不会进行翻译。 完成后，单击“创建”。
    - **编辑类别** - 对于列表中的任意一个类别，选择“...”。 此选项显示一个弹出菜单，可以通过此菜单“固定到仪表板”或“删除”类别。

## <a name="apps-added-automatically-by-intune"></a>Intune 自动添加的应用

之前，Intune 包含了一些可供快速分配的内置应用。 根据你的反馈，此列表已被删除，你将不再看到内置应用。
但是，如果已分配任何内置应用，则在应用列表中仍会看到这些应用。 你可以根据需要继续分配这些应用。
在后续版本中，我们计划提供一种方法，以便用户可以更轻松地在 Azure 门户中选择并分配内置应用。

## <a name="next-steps"></a>后续步骤

请参阅下列主题之一，了解如何将各平台相关应用添加到 Intune 中：

- [Android 应用商店应用](store-apps-android.md)
- [Android LOB 应用](lob-apps-android.md)
- [iOS App Store 应用](store-apps-ios.md)
- [iOS LOB 应用](lob-apps-ios.md)
- [Web 应用（适用于所有平台）](web-app.md)
- [Windows Phone 8.1 应用商店应用](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB 应用](lob-apps-windows-phone.md)
- [Windows 应用商店应用](store-apps-windows.md)
- [Windows LOB 应用](lob-apps-windows.md)
- [适用于 Windows 10 的 Office 365 应用](apps-add-office365.md)

