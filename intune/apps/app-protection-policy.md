---
title: 应用保护策略概述
titleSuffix: Microsoft Intune
description: 了解 Microsoft Intune 应用保护策略如何帮助保护公司数据，防止数据丢失。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31bb0e2ff4379c55829afc65fb99b768c9099a47
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72498949"
---
# <a name="app-protection-policies-overview"></a>应用保护策略概述

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

应用保护策略 (APP) 是可确保组织数据在托管应用中保持安全或受到控制的规则。 策略可以是在用户尝试访问或移动“公司”数据时强制执行的规则，或在用户位于应用内时受到禁止或监视的一组操作。 受管理应用是一种自身执行应用保护策略的应用，可由 Intune 管理。

借助移动应用管理 (MAM) 应用保护策略，可以管理和保护应用程序内的组织数据。 通过无需注册的 MAM (MAM-WE)，可以在几乎任何[设备](app-management.md#app-management-capabilities-by-platform)上管理包含敏感数据的工作或学校相关应用，包括自带设备办公 (BYOD) 场景下的个人设备。   许多生产型应用，例如 Microsoft Office 应用，都可以通过 Intune MAM 进行管理。 请参阅可供公众使用的 [Microsoft Intune 保护的应用](apps-supported-intune-apps.md)的官方列表。

## <a name="how-you-can-protect-app-data"></a>如何保护应用数据
你的员工使用移动设备进行个人任务和工作任务。 你既要确保员工高效工作，又希望防止有意和无意的数据丢失。 你还需要保护他人设备（不由你管理的设备）访问的公司数据。

可使用 Intune 应用保护策略，该策略独立于任何移动设备管理 (MDM) 解决方案  。 无论是否在设备管理解决方案中注册设备，均可借助此独立策略保护公司数据。 通过实现**应用级别策略**，即可限制对公司资源的访问，并让数据处于 IT 部门的监控范围之内。

### <a name="app-protection-policies-on-devices"></a>设备上的应用保护策略

可对运行在设备上的应用进行配置的应用保护策略包括：

- **已在 Microsoft Intune 中注册：** 这些设备通常是公司自有设备。

- **已在第三方移动设备管理 (MDM) 解决方案中注册：** 这些设备通常是公司自有设备。

  > [!NOTE]
  > 移动应用管理策略不应与第三方移动应用管理或安全容器解决方案一起使用。

- **未在任何移动设备管理解决方案中注册：** 此类设备通常是员工拥有的设备，且未在 Intune 或其他 MDM 解决方案中进行托管或注册。

> [!IMPORTANT]
> 可为连接到 Office 365 服务的 Office 移动应用创建移动应用管理策略。 此外，还可以通过为启用了混合现代身份验证的 iOS 和 Android 的 Outlook 创建 Intune 应用保护策略来保护对 Exchange 本地邮箱的访问。 使用此功能之前，请确保满足[适用于 iOS 和 Android 的 Outlook 要求](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)。 连接到本地 Exchange 或 SharePoint 服务的其他应用不支持应用保护策略。

## <a name="benefits-of-using-app-protection-policies"></a>使用应用保护策略的优点

以下是使用应用保护策略的主要优点：

- **在应用级别保护公司数据。** 由于移动应用管理不需要设备管理，因此可在受管理和不受管理设备上保护公司数据。 管理以用户标识为中心，因而不再需要设备管理。

- **不会影响最终用户工作效率，且在个人环境中使用应用时不会应用策略。** 这些策略仅应用于工作环境，能够在不接触个人数据的情况下保护公司数据。

- **应用保护策略确保应用层保护措施到位。** 例如，你能够：
  - 规定在工作环境中打开应用时需使用 PIN 
  - 控制应用之间的数据共享 
  - 防止将公司应用数据保存到私人存储位置

- **MDM 和 MAM 确保该设备受到保护**。 例如，你可以要求使用 PIN 以访问设备，或将托管应用部署到设备。 还可通过 MDM 解决方案将应用部署到设备，以便更好地控制应用管理。

将 MDM 与应用保护策略一起使用还有其他优点，公司可以同时使用应用保护策略与 MDM，也可以单独使用应用保护策略。 例如这样一种情况：员工同时使用公司电话和其个人平板电脑。 公司的手机在 MDM 中注册且受应用保护策略保护，而个人设备仅受应用保护策略保护。

如果在不设置设备状态的情况下将 MAM 策略应用于用户，用户将同时在 BYOD 设备和 Intune 托管设备上获得 MAM 策略。 还可以根据托管状态应用 MAM 策略。 因此，在创建应用保护策略时，应在“面向所有应用类型”旁边选择“否”。   然后，执行以下任意操作：
- 将不太严格的 MAM 策略应用于 Intune 托管设备，并将更严格的 MAM 策略应用于未注册 MDM 的设备。
- 将 MAM 策略仅应用于未注册的设备。

## <a name="supported-platforms-for-app-protection-policies"></a>支持应用保护策略的平台

Intune 提供各种功能，用于在设备上获取所需的应用，以便在其中运行。 有关详细信息，请参阅[按平台分类的应用管理功能](app-management.md#app-management-capabilities-by-platform)。

Intune 应用保护策略平台支持与适用于 Android 和 iOS 设备的 Office 移动应用程序平台支持保持一致。 有关详细信息，请参阅 [Office 系统要求](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg)的“移动应用”部分  。

> [!IMPORTANT]
> 接收 Android 应用保护策略的设备必须安装有 Intune 公司门户。 有关详细信息，请参阅 [Intune 公司门户访问应用要求](../fundamentals/end-user-mam-apps-android.md#access-apps)。

## <a name="how-app-protection-policies-protect-app-data"></a>应用保护策略如何保护应用数据

### <a name="apps-without-app-protection-policies"></a>不具有应用保护策略的应用

在无限制的情况下使用应用时，公司和个人数据可能混合。 公司数据可能最终位于个人存储空间等位置或传输到监控范围外的应用中，导致数据丢失。 下图中的箭头显示了公司应用和个人应用之间以及到存储位置的无限制数据移动。

![在没有策略的应用之间进行数据移动的概念图](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>采用应用保护策略 (APP) 的数据保护

可使用应用保护策略以防将公司数据保存到设备的本地存储中（请参阅下图）。 还可限制将数据移动到不受应用保护策略保护的其他应用。 应用保护策略设置包括：
- 数据重定位策略，例如“防止另存为”和“限制剪切、复制和粘贴”   。
- 访问策略设置，例如“需要简单的 PIN 才能访问”、“阻止在已越狱或取得 root 权限的设备上运行受管理的应用”   。

![显示公司数据受策略保护的概念图](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>在由 MDM 解决方案管理的设备上，采用 APP 保护数据

下图显示了 MDM 和应用保护策略共同提供的保护层。

![图像显示应用保护策略如何在 BYOD 设备上起作用](./media/app-protection-policy/app-protection-policies-with-mdm.png)

MDM 解决方案通过提供以下功能增值：

- 注册设备
- 将应用部署到设备
- 提供持续的设备合规性和管理

应用保护策略通过提供以下功能增值：

- 帮助防止公司数据泄露到使用者应用和服务
- 将限制（如“另存为”、“剪贴板”或“PIN”）应用到客户端应用   
- 必要时，从应用擦除公司数据而不从设备删除这些应用

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>采用适用于未注册设备的 APP 保护数据

下图显示在未实施 MDM 的情况下数据保护策略在应用级别的工作原理。

![图像显示应用保护策略如何在未注册设备（非托管设备）上起作用](./media/app-protection-policy/app-protection-policies-without-mdm.png)

对于未在任何 MDM 解决方案中注册的 BYOD 设备，应用保护策略可在应用级别帮助保护公司数据。
但是，有一些限制需要注意，如：

- 无法将应用部署到设备。 最终用户必须从应用商店获取应用。
- 无法在这些设备上预配证书配置文件。
- 无法在这些设备上设置公司 Wi-Fi 和 VPN 设置。

## <a name="apps-you-can-manage-with-app-protection-policies"></a>可使用应用保护策略进行管理的应用

任何已与 [Intune App SDK](../developer/app-sdk.md) 集成或通过 [Intune 应用包装工具](../developer/apps-prepare-mobile-application-management.md)包装的应用都可使用 Intune 应用保护策略进行管理。 请参阅使用以下工具构建并可供公众使用的 [Microsoft Intune 保护的应用](apps-supported-intune-apps.md)的官方列表。

Intune SDK 开发团队主动测试和维护对使用本机 Android、iOS（Obj-C、Swift）、Xamarin、Xamarin.Forms 和 Cordova 平台生成的应用的支持。 虽然某些客户已成功将 Intune SDK 与 React Native 和 NativeScript 等其他平台集成，但我们不会使用受支持平台之外的任何方式为应用开发人员提供明确的指导或插件。

[Intune App SDK](../developer/app-sdk.md) 将 [Azure Active Directory 身份验证库](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) 中的一些高级新式身份验证功能用于此 SDK 的第一方和第三方版本。 因此，[Microsoft 身份验证库](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) 不适用于我们的许多核心方案，例如向 Intune 应用保护服务进行身份验证和条件启动。 鉴于来自 Microsoft 标识团队的全面指导是切换到适用于所有 Microsoft Office 应用的 MSAL，因此 [Intune App SDK](../developer/app-sdk.md) 最终需要支持它，但目前没有计划。

## <a name="end-user-requirements-to-use-app-protection-policies"></a>对于使用应用保护策略的最终用户要求

下面的列表说明对于在 Intune 托管应用上使用应用保护策略的最终用户要求：

- 最终用户必须具有 Azure Active Directory (AAD) 帐户。 请参阅[添加用户并授予对 Intune 的管理权限](../fundamentals/users-add.md)，了解如何在 Azure Active Directory 中创建 Intune 用户。

- 最终用户必须向其 Azure Active Directory 帐户分配 Microsoft Intune 许可证。 请参阅[管理 Intune 许可证](../fundamentals/licenses-assign.md)，以了解如何向最终用户分配 Intune 许可证。

- 最终用户必须属于应用保护策略所针对的安全组。 同一应用保护策略必须面向正在使用的特定应用。 可以在 [Azure 门户](https://portal.azure.com)的 Intune 控制台中创建和部署应用保护策略。 当前可以在 [Microsoft 365 管理中心](https://admin.microsoft.com)创建安全组。

- 最终用户必须使用其 AAD 帐户登录到应用。

## <a name="app-protection-policies-for-microsoft-office-apps"></a>适用于 Microsoft Office 应用的应用保护策略

将应用保护策略用于 Microsoft Office 应用时，有一些其他需要注意的要求。

### <a name="outlook-mobile-app"></a>Outlook 移动应用
对于使用 [Outlook 移动应用](https://products.office.com/outlook)的其他要求包括：

- 最终用户必须将 Outlook 移动应用安装到其设备上。
- 最终用户必须具有链接到其 Azure Active Directory 帐户的 [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) 邮箱和许可证。

  >[!NOTE]
  > Outlook 移动应用当前仅支持适用于 Microsoft Exchange Online 的 Intune 应用保护和[使用混合新式身份验证的 Exchange Server](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)，不支持 Office 365 Dedicated 中的 Exchange。

### <a name="word-excel-and-powerpoint"></a>Word、Excel 和 PowerPoint
对于使用 [Word、Excel 和 PowerPoint](https://products.office.com/business/office) 应用的其他要求包括：

- 最终用户必须具有链接到其 Azure Active Directory 帐户的 [Office 365 商业版或企业版](https://products.office.com/business/compare-more-office-365-for-business-plans)许可证。 订阅必须包括移动设备上的 Office 应用，可以包括 [OneDrive for Business](https://onedrive.live.com/about/business/) 云存储帐户。 遵循这些[说明](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)可在 [Microsoft 365 管理中心](https://admin.microsoft.com)分配 Office 365 许可证。

- 最终用户必须具有使用粒度另存为功能进行配置的托管位置（该功能位于“阻止另存为”应用程序保护策略设置下）。 例如，如果托管位置为 OneDrive，则应在最终用户的 Word、Excel 或 PowerPoint 应用中对 [OneDrive](https://onedrive.live.com/about/) 应用进行配置。

- 如果托管的位置为 OneDrive，则部署到最终用户的应用保护策略必须针对该应用。

  >[!NOTE]
  > Office 移动应用当前仅支持 SharePoint Online，不支持本地 SharePoint。

### <a name="managed-location-needed-for-office"></a>Office 所需的托管位置
Office 所需的托管位置（即 OneDrive）。 Intune 会将应用中的所有数据标记为“公司”或“个人”。 数据源于业务位置时会被视为“公司”数据。 对于 Office 应用，Intune 将以下数据视为业务位置：电子邮件 (Exchange) 或云存储（包含 OneDrive for Business 帐户的 OneDrive 应用）。

### <a name="skype-for-business"></a>Skype for Business
对于使用 Skype for Business 有其他要求。 请参阅 [Skype for Business](https://products.office.com/skype-for-business/it-pros) 许可证要求。 对于 Skype for Business (SfB) 混合配置和本地配置，请分别参阅[正式发布适用于 SfB 和 Exchange 的混合新式身份验证](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756)和[使用 AAD 实现适用于 SfB OnPrem 的新式身份验证](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910)。

## <a name="app-protection-global-policy"></a>应用保护全局策略

若 OneDrive 管理员浏览到 admin.office.com 并选择“设备”访问权限，则他们可为 OneDrive 和 SharePoint 客户端应用设置移动应用程序管理控件    。 

这些设置可供 OneDrive 管理控制台使用，可配置名为全局策略的特殊 Intune 应用保护策略  。 此全局策略适用于租户中的所有用户，且无法控制策略目标设定。 

启用后，默认情况下将使用所选设置保护适用于 iOS 和 Android 的 OneDrive 和 SharePoint 应用。 IT 专业人员可在 Intune 控制台中编辑此策略，以添加更多目标应用并修改任何策略设置。 

默认情况下，每个租户仅有一个全局策略  。 然而，可使用 [Intune 图形 API](../developer/intune-graph-apis.md) 来为每个租户创建额外的全局策略，但不推荐这种做法。 不建议创建额外全局策略，因为对此类策略的实施进行故障排除会变得复杂。

虽然全局策略适用于租户中的所有用户，但任何标准的 Intune 应用保护政策都将覆盖这些设置  。

## <a name="app-protection-features"></a>应用保护功能

### <a name="multi-identity"></a>多身份

借助多身份支持，应用可以支持多个受众。 这些受众既是“公司”用户，也是“个人”用户。 “公司”受众使用工作和学校帐户，而个人帐户用于使用者受众，如 Microsoft Office 用户。 支持多身份的应用可以公开发布，只有在工作和学校（“公司”）环境中使用应用时应用保护策略才适用。 多身份支持使用 [Intune App SDK](../developer/app-sdk.md) 来仅将应用保护策略应用于已登录到应用的工作或学校帐户。 如果个人帐户登录到应用，数据将保持不变。

例如个人环境的情况：用户在 Word 中开始一个新文档，这被视为“个人”环境，因此不会应用 Intune 应用保护策略。 使用“公司”OneDrive 帐户保存文档后，该文档将被视为“公司”环境，因此会应用 Intune 应用保护策略。

例如工作或“公司”环境的情况：用户使用其工作帐户启动 OneDrive 应用。 在工作环境中，他们无法将文件移动到私人存储位置。 之后当用户通过其个人帐户使用 OneDrive 时，可无限制地从个人 OneDrive 复制和移动数据。

Outlook 提供“个人”和“公司”电子邮件的电子邮件组合视图。 在这种情况下，Outlook 应用会在启动时提示输入 Intune PIN。

有关 Intune 中的多身份的详细信息，请参阅 [MAM 和多身份](apps-supported-intune-apps.md)。

### <a name="intune-app-pin"></a>Intune 应用 PIN

个人标识号 (PIN) 是一种密码，用于验证是否是正确的用户在应用程序中访问组织的数据。

**PIN 提示**<br>
当用户要访问“公司”数据时，Intune 才会提示输入用户的应用 PIN。 在诸如 Word、Excel、PowerPoint 等多身份应用中，当用户尝试打开“公司”文档或文件时，会向他们提示输入 PIN。 在单身份应用中，例如使用 [Intune 应用包装工具](../developer/apps-prepare-mobile-application-management.md)托管的业务线应用，会在启动时提示输入 PIN，因为 [Intune App SDK](../developer/app-sdk.md) 知道用户在应用中的体验始终是针对“公司”的。

**PIN 提示频率**<br>
IT 管理员可在 Intune 管理控制台中定义 Intune 应用保护策略设置“以下时间过后重新检查访问要求(分钟)”。  此设置指定在设备上检测访问要求，并再次显示应用程序 PIN 屏幕之前的时长。 但是，请注意以下关于 PIN 的重要详细信息，它们会影响用户收到提示的频率：

- **在同一发布者的应用之间共享 PIN 以提高可用性：**<br> 在 iOS 上，同一应用发布者  的所有应用之间共享一个应用 PIN 码。 在 Android 上，所有应用共享一个应用 PIN。
  - **在设备重启后“以下时间过后重新检查访问要求(分钟)”的行为： **<br> “PIN 计时器”跟踪确定何时显示下一个 Intune 应用 PIN 的不活动分钟数。 在 iOS 上，PIN 计时器不受设备重启影响。 因此，设备重启对用户在使用 Intune PIN 策略的 iOS 应用中处于非活动状态的分钟数没有影响。 在 Android 上，PIN 计时器在设备重启后重置。 因此，使用 Intune PIN 策略的 Android 应用可能提示输入应用 PIN，设备重启后的“以下时间过后重新检查访问要求(分钟)”设置值对此没有影响  。  
  - **与 PIN 关联的计时器的滚动特性：**<br> 输入 PIN 以访问应用（应用 A）后，该应用会离开设备主屏幕（主输入焦点），并且该 PIN 的 PIN 计时器会进行重置。 共享此 PIN 的任何应用（应用 B）均不会提示用户输入 PIN，因为计时器已重置。 再次达到“以下时间过后重新检查访问要求(分钟)”值后，就会再次显示该提示。

对于 iOS 设备，即使在不同发行商的应用之间共享 PIN，当不是主要输入焦点的应用再次满足“在一定时间后重新检查访问要求(分钟)”  值时，也会再次显示提示。 因此，例如，某一用户具有来自发行商 X  的应用 A  和来自发行商 Y  的应用 B  ，并且这两个应用共享相同 PIN。 该用户将焦点置于应用 A  （前景），并最小化应用 B  。 当满足“在一定时间后重新检查访问要求(分钟)”  值并且用户切换到应用 B  时，将需要此 PIN。

  >[!NOTE]
  > 为了更频繁地验证用户的访问要求（即 PIN 提示），尤其是针对常用应用的访问，建议减小“以下时间过后重新检查访问要求(分钟)”设置的值。

**Outlook 和 OneDrive 的内置应用 PIN**<br>
Intune PIN 基于非活动状态计时器（“以下时间过后重新检查访问要求(分钟)”的值）执行操作。  因此，Intune PIN 提示与 Outlook 和 OneDrive 的内置应用 PIN 提示（默认情况下与应用启动直接关联）相互独立显示。 如果用户同时收到两个 PIN 提示，预期行为应以 Intune PIN 为准。

**Intune PIN 安全性**<br>
PIN 仅允许正确的用户在应用中访问其组织数据。 因此，最终用户必须使用其工作或学校帐户登录，然后才能设置或重置其 Intune 应用 PIN。 这种身份验证通过安全的令牌交换由 Azure Active Directory 执行，且不对 [Intune App SDK](../developer/app-sdk.md) 公开。 从安全性的角度来看，保护工作或学校数据的最佳方法便是对其进行加密。 加密与应用 PIN 无关，它本身是一项应用保护策略。

**Intune PIN - 防止暴力攻击**<br>
作为应用 PIN 策略的一部分，IT 管理员可以设置在锁定应用之前用户可尝试验证其 PIN 的最大次数。 达到最大尝试次数后，[Intune App SDK](../developer/app-sdk.md) 可以擦除应用中的“公司”数据。
  
**要在来自同一个发布者的应用上设置 PIN 两次？**<br>
目前，MAM（在 iOS 上）允许使用包含字母数字和特殊字符（称为“密码”）的应用程序级 PIN，该功能需要一些应用程序（即 WXP、Outlook、Managed Browser、Yammer）的参与，以便集成 [Intune APP SDK for iOS](../developer/app-sdk-ios.md)。 如果没有应用程序的参与，将无法对目标应用程序正确执行密码设置。 这是在 Intune SDK for iOS 版本 7.1.12 中发布的功能 。

为了支持此功能，并确保与旧版 Intune SDK for iOS 的向后兼容性，版本 7.1.12 及更高版本中的所有 PIN（数字或密码）都与旧版 SDK 中的数字 PIN 分开处理。 因此，如果设备中同一发布者的应用使用了版本低于和高于 7.1.12 的 Intune SDK for iOS，就需要设置两个 PIN。 这两个 PIN（对于每个应用）不以任何方式相关（即必须遵守应用到应用的应用保护策略）。 这样，只有  当应用 A 和 B 都应用了相同的策略（对于 PIN），用户才需要设置相同的 PIN 两次。 

此行为只针对于使用 Intune 移动应用管理 (MAM) 启用的 iOS 应用程序上的 PIN。 日后，随着应用采用更高版本的 Intune SDK for iOS，必须在同一发布者的应用上设置 PIN 两次就不再是个问题了。 有关示例，请参阅下面的注意事项。

  >[!NOTE]
  > 例如，如果应用 A 使用版本低于 7.1.12 的 SDK 生成，同一发布者的应用 B 使用版本不低于 7.1.12 的 SDK 生成，且这两个应用都安装在 iOS 设备上，那么最终用户需要为应用 A 和 B 单独设置 PIN。
  > 如果在此设备上安装了包含 SDK 版本 7.1.9 的应用 C，那么它与应用 A 共用同一 PIN。使用 7.1.14 构建的应用 D 将与应用 B 共享同一个 PIN。  
  > 如果仅在设备上安装了应用 A 和 C，需要设置一个 PIN。 如果仅在设备上安装了应用 B 和 D，情况也是如此，即需要设置一个 PIN。

### <a name="app-data-encryption"></a>应用数据加密
IT 管理员可以部署要求对应用数据进行加密的应用保护策略。 作为该策略的一部分，IT 管理员还可指定何时加密内容。

**Intune 数据加密过程**<br> 请参阅 [Android 应用保护策略设置](app-protection-policy-settings-android.md)和 [iOS 应用保护策略设置](app-protection-policy-settings-ios.md)，获取有关加密应用保护策略设置的详细信息。

**加密的数据**<br>
根据 IT 管理员的应用保护策略，仅对标记为“公司”的数据进行加密。 数据源于业务位置时会被视为“公司”数据。 对于 Office 应用，Intune 将以下内容视为业务位置：

- 电子邮件 (Exchange) 
- 云存储（有 OneDrive for Business 帐户的 OneDrive 应用）

对于由 [Intune 应用包装工具](../developer/apps-prepare-mobile-application-management.md)托管的业务线应用，所有应用数据都会被视为“公司”数据。

**远程擦除数据**<br>

Intune 可以通过以下三种不同方式擦除应用数据： 
- 完全设备擦除
- MDM 选择性擦除 
- MAM 选择性擦除

有关 MDM 远程擦除的详细信息，请参阅[使用“擦除”或“停用”操作删除设备](../remote-actions/devices-wipe.md)。 有关使用 MAM 进行选择性擦除的详细信息，请参阅[“停用”操作](../remote-actions/devices-wipe.md#retire)和[如何仅擦除应用中的公司数据](apps-selective-wipe.md)。

[擦除](../remote-actions/devices-wipe.md)会通过将设备还原到其出厂默认设置，从设备  中删除所有用户数据和设置。 设备从 Intune 删除。

  >[!NOTE]
  > 擦除只有在注册了 Intune 移动设备管理 (MDM) 的设备上才能实现。

**MDM 选择性擦除**<br>
请参阅[删除设备 - 停用](../remote-actions/devices-wipe.md#retire)，了解删除公司数据的相关信息。

**MAM 选择性擦除**<br>
MAM 选择性擦除仅删除应用中的公司应用数据。 使用 Intune Azure 门户启动该请求。 若要了解如何启动擦除请求，请参阅[如何仅擦除应用中的公司数据](apps-selective-wipe.md)。

如果用户在启用了选择性擦除的情况下使用应用，那么 [Intune App SDK](../developer/app-sdk.md) 会每 30 分钟检查一次来自 Intune MAM 服务的选择性擦除请求。 它还会在用户第一次启动应用并使用其工作或学校帐户登录时检查选择性擦除。

**本地服务不适用于 Intune 保护的应用时**<br>
Intune 应用保护要求用户的身份在应用程序与 [Intune App SDK](../developer/app-sdk.md) 之间保持一致。 保证此种一致的唯一方法是通过新式身份验证。 在某些情况下应用可能适用于本地配置，但它们既不一致也无法得到保证。

**从托管应用中打开 Web 链接的安全方法**<br>
IT 管理员可以为 [Intune Managed Browser 应用](app-configuration-managed-browser.md)（一种由 Microsoft Intune 开发的可使用 Intune 轻松管理的 Web 浏览器）部署和设置应用保护策略。 IT 管理员可以要求 Intune 托管应用中的所有 Web 链接均使用 Managed Browser 应用打开。

## <a name="examples-of-app-protection-policies"></a>应用保护策略示例

请参阅 [Android 应用保护策略设置](app-protection-policy-settings-android.md)和 [iOS 应用保护策略设置](app-protection-policy-settings-ios.md)，以详细了解应用保护策略示例以及各个应用保护策略设置。

## <a name="app-protection-experience-for-ios-devices"></a>适用于 iOS 设备的应用保护体验

### <a name="device-fingerprint-or-face-ids"></a>设备指纹或 Face ID 
Intune 应用保护策略允许将应用访问权限控制在仅限 Intune 许可用户访问。 控制对应用的访问权限的方法之一是支持的设备上需要具有 Apple 的 Touch ID 或 Face ID。 Intune 执行某个行为后，如果对设备的生物识别数据库有任何更改，则在满足下一个非活动超时值时，Intune 会提示用户输入 PIN。 对生物识别数据的更改包括添加或删除指纹或人脸。 如果 Intune 用户未设置 PIN，则会引导他们设置 Intune PIN。
 
此过程旨在继续确保应用中的组织数据安全并在应用级别受保护。 此功能仅适用于 iOS，并且需要集成了 Intune APP SDK for iOS 版本 9.0.1 或更高版本的应用程序参与。 必须集成 SDK，以便可以在目标应用程序上强制执行行为。 此集成陆续进行，取决于特定应用程序团队。 参与的一些应用包括 WXP、Outlook、Managed Browser 和 Yammer。
  
### <a name="ios-share-extension"></a>iOS 共享扩展
即使将数据传输策略设置为“仅托管应用”  或“无应用”  ，也可使用 iOS 共享扩展在非托管应用中打开工作或学校数据。 在不管理设备的情况下，Intune 应用保护策略不能控制 iOS 共享扩展。 因此，Intune _**会在对“公司”数据进行应用外共享之前对其进行加密**_ 。 可以通过在托管应用外部打开“公司”文件来验证此加密行为。 该文件应进行加密，且无法在托管应用外打开。

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>适用于同一组应用和用户的多个 Intune 应用保护访问设置
当用户尝试从公司帐户访问目标应用时，系统将在最终用户设备上按特定顺序应用 Intune 应用访问保护策略。 通常先访问擦除，然后是块，再是可取消的警告。 例如，如果适用于特定用户/应用，则先应用阻止用户访问的最低 iOS 操作系统设置，再应用警告用户更新其 iOS 版本的最低 iOS 操作系统设置。 因此，如果 IT 管理员将最低 iOS 操作系统配置为 11.0.0.0 并将最低 iOS 操作系统（仅限警告）配置为 11.1.0.0，则当尝试访问该应用的设备具有 iOS 10 时，系统将基于更严格的最低 iOS 操作系统版本设置阻止最终用户的访问。

处理不同类型的设置时，先处理 Intune App SDK 版本要求，其次是应用版本要求，再是 iOS 操作系统版本要求。 然后，按相同顺序检查各类型设置的所有警告。 建议仅根据 Intune 产品团队针对关键阻止方案提供的指导配置 Intune App SDK 版本要求。

## <a name="app-protection-experience-for-android-devices"></a>适用于 Android 设备的应用保护体验

### <a name="company-portal-app-and-intune-app-protection"></a>公司门户应用和 Intune 应用保护
应用保护的许多功能都内置于公司门户应用中。 虽然始终需要公司门户应用，但设备注册是不必要的  。 对于无需注册的移动应用管理 (MAM-WE)，最终用户只需在设备上安装公司门户应用即可。

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>适用于同一组应用和用户的多个 Intune 应用保护访问设置
当用户尝试从公司帐户访问目标应用时，系统将在最终用户设备上按特定顺序应用 Intune 应用访问保护策略。 通常是先访问块，再访问可取消的警告。 例如，如果适用于特定用户/应用，则先应用阻止用户访问的 Android 修补程序最低版本设置，再应用警告用户进行修补程序升级的 Android 修补程序最低版本设置。 因此，如果 IT 管理员将 Android 修补程序最低版本配置为 2018-03-01，并将 Android 修补程序最低版本（仅限警告）配置为 2018-02-01，则当尝试访问该应用的设备具有 2018-01-01 版修补程序时，系统将基于更严格的 Android 修补程序最低版本设置阻止最终用户的访问。 

处理不同类型的设置时，先处理应用版本要求，其次是 Android 操作系统版本要求，再是 Android 修补程序版本要求。 然后，按相同顺序检查各类型设置的所有警告。

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Intune 应用保护策略和 Google 的适用于 Android 设备的 SafetyNet 认证 
凭借 Intune 应用保护策略，管理员能够要求最终用户设备通过 Google 的适用于 Android 设备的 SafetyNet 认证。 新的 Google Play 服务决定将按照 Intune 服务确定的时间间隔报告给 IT 管理员。 由于负载原因，服务调用频率受限，因此该值在内部维护，并且不可配置。 IT 管理员针对 Google SafetyNet 认证设置配置的任何操作都将在条件启动时根据最后报告的结果发送到 Intune 服务。 如果没有数据，若无其他条件启动检查失败，则允许访问，用于确定认证结果的 Google Play 服务“往返”将在后端开始，并在设备失败时以异步方式提示用户。 如果数据过时，将根据最后报告的结果阻止或允许访问，同样，用于确定认证结果的 Google Play 服务“往返”将开始，并在设备失败时以异步方式提示用户。

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Intune 应用保护策略和 Google 的适用于 Android 设备的 Verify Apps API
凭借 Intune 应用保护策略，管理员能够要求最终用户设备通过 Google 的适用于 Android 设备的 Verify Apps API 发送信号。 如何执行此操作的说明根据设备略有不同。 常规流程包括转到 Google Play 商店，然后单击“我的应用和游戏”，单击最后一次应用扫描的结果，然后你会转到“Play 保护”菜单  。 确保“扫描设备以检测安全隐患”开关为开启状态  。

### <a name="googles-safetynet-attestation-api"></a>Google 的 SafetyNet 认证 API 
Intune 利用 Google Play 保护 SafetyNet API 添加到我们对未注册设备的现有 root 权限检测检查。 Google 开发并维护此 API 集，当它们不希望应用在已取得 root 权限的设备上运行时，Android 应用可以采用这些 API。 例如，Android Pay 应用已将此合并。 尽管 Google 不公开共享所进行的全部 root 权限检测检查，但是我们希望这些 API 能够检测出已取得其设备 root 权限的用户。 然后，可以阻止这些用户访问，或者可以从启用策略的应用中擦除其公司帐户。 “检查基本完整性”描述设备的总体完整性。  已取得根权限的设备、模拟器、虚拟设备以及具有篡改迹象的设备无法通过基本完整性检查。 “检查基本完整性和认证设备”描述设备与 Google 服务的兼容性。  只有经过 Google 认证的未修改的设备才能通过此检查。 以下设备将无法通过检查：

- 基本完整性检查未通过的设备
- 具有未锁定引导装入程序的设备
- 具有自定义系统映像/ROM 的设备
- 制造商未申请或未通过 Google 认证的设备
- 系统映像直接通过 Android 开源程序源文件生成的设备
- 具有 beta 版本/开发者预览版系统映像的设备

请参阅 [Google 的 SafetyNet 认证文档](https://developer.android.com/training/safetynet/attestation)，获取技术详细信息。

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>“SafetyNet 设备认证”设置和“已越狱/已获得 root 权限的设备”设置
Google Play 保护的 SafetyNet API 检查要求最终用户保持在线状态，至少是在执行“往返”以确定认证结果期间。 如果最终用户为离线状态，IT 管理员仍可通过“已越狱/已获得 root 权限的设备”设置强制执行结果。  不过，如果最终用户长时间离线，“脱机宽限期”值就会发挥作用，在达到计时器值后将阻止所有对工作或学校数据的访问，直至网络访问可用。  同时开启这两个设置就可以通过分层方法来保持最终用户设备正常运行，这在最终用户通过移动设备访问工作或学校数据时非常重要。

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play 保护 API 和 Google Play Services
利用 Google Play 保护 API 的应用保护策略设置需要 Google Play Services 才能运行。 “SafetyNet 设备认证”和“应用威胁扫描”设置都需要 Google 确定的 Google Play Services 版本才能正常运行。   由于这些设置属于安全领域，如果最终用户是这些设置的目标，并且未使用适当版本的 Google Play Services，或者没有 Google Play Services 的访问权限，则将被阻止。

## <a name="next-steps"></a>后续步骤

[如何使用 Microsoft Intune 创建和部署应用保护策略](app-protection-policies.md)

## <a name="see-also"></a>另请参阅
第三方应用（例如 Salesforce 移动应用）与 Intune 一起以特定的方式来保护公司数据。 若要详细了解 Salesforce 应用专门与 Intune 合作的方式（包括 MDM 应用配置设置），请参阅 [Salesforce 应用和 Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf)。
