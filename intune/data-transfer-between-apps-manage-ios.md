---
title: 管理 iOS 应用之间的数据传输
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中使用移动应用管理策略来管理应用之间的数据传输。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eaf381d6d7b6bf8e9508eac4ccfc5431aa008658
ms.sourcegitcommit: 89a973bbfa1702b2d275af6814874e4305bdcb77
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71140711"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>如何在 Microsoft Intune 中管理 iOS 应用之间的数据传输

若要帮助保护公司数据，请限制仅在你管理的应用之间进行文件传输。 可以通过以下方式管理 iOS 应用：

- 通过为应用配置应用保护策略来保护工作或学校帐户的组织数据。 我们称之为“策略托管应用”。  请参阅 [all the Intune-managed apps you can manage with app protection policy](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)（所有可使用应用保护策略管理的 Intune 托管应用）

- 通过 iOS 设备管理部署和管理应用需要设备注册移动设备管理 (MDM) 解决方案。 部署的应用可以是“策略托管应用”，也可以是其他 iOS 托管应用。

适用于已注册 iOS 设备的“打开方式管理”功能可以将文件传输限制为仅在 iOS 托管应用之间进行。 在配置设置中设置“打开方式管理”限制，然后使用 MDM 解决方案进行部署。  用户安装部署应用时，即会应用所设置的限制。

## <a name="use-app-protection-with-ios-apps"></a>对 iOS 应用使用应用保护
可将应用保护策略与 iOS 的“打开方式管理”功能结合使用，从而通过以下方式保护公司数据：

- **不由任何 MDM 解决方案管理的设备：** 可以设置应用保护策略设置，通过“打开方式”或“共享扩展”来控制数据与其他应用程序的共享。  为此，请将“将组织数据发送到其他应用”配置为“具有打开方式/共享筛选的策略托管应用”。  策略托管应用中的“打开方式/共享”行为只会将其他策略托管应用用作共享选项。 

- **由 MDM 解决方案托管的设备**：对于在 Intune 或第三方 MDM 解决方案中注册的设备，在具有应用保护策略的应用和通过 MDM 部署的其他托管 iOS 应用之间共享的数据由 Intune 应用策略和 iOS“打开方式管理”功能控制。 若要确保使用 MDM 解决方案部署的应用也与 Intune 应用保护策略相关联，请按照下一部分[配置用户 UPN 设置](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)中所述配置用户 UPN 设置。 要指定数据传输到其他应用的方式，请启用“将组织数据发送到其他应用”，然后选择首选的共享级别。 要指定应用从其他应用接收数据的方式，请启用“从其他应用接收数据”，然后选择首选的数据接收级别。 有关如何接收和共享应用数据的详细信息，请参阅[数据重定位设置](app-protection-policy-settings-ios.md#data-protection)。

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>为 Microsoft Intune 或第三方 EMM 配置用户 UPN 设置
需要配置用户 UPN 设置，才能使 Intune 或第三方 EMM 解决方案管理的设备识别已注册用户帐户。 UPN 配置可与从 Intune 中部署的应用保护策略一同使用。 下述过程是配置 UPN 设置的一般流程以及该过程所产生的用户体验：

1. 在 [Azure 门户](https://portal.azure.com)中，为 iOS [创建并分配应用保护策略](app-protection-policies.md)。 根据公司要求配置策略设置，并选择应使用此策略的 iOS 应用。

2. 使用下面的常规步骤，通过 Intune 或第三方 MDM 解决方案，部署想要托管的应用和电子邮件配置文件。 示例 1 中也涵盖了这一体验。

3. 通过托管设备的下列应用配置设置来部署该应用：

      键 = IntuneMAMUPN，值 = <username@company.com>

      示例：[‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > 在 Intune 中，应用配置策略注册类型必须设置为“托管设备”。
     > 此外，需要从 Itune 公司门户安装应用（如果设为可用）；或者根据需要将应用推送到设备。 

4. 使用 Intune 或第三方 MDM 提供程序将“打开方式管理”策略部署到已注册设备。


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>示例 1：Intune 或第三方 MDM 控制台中的管理体验

1. 转到 Intune 或第三方 MDM 提供程序的管理控制台。 转到将应用程序配置设置部署到已注册的 iOS 设备的控制台部分。

2. 在“应用程序配置”部分中，输入以下设置：

   键 = IntuneMAMUPN，值 = <username@company.com>

   键/值对的确切语法可能会因第三方 MDM 提供程序而异。 下表显示了第三方 MDM 提供程序和应为键/值对输入的确切值的示例。

   |第三方 MDM 提供程序| Configuration 注册表项 | 值类型 | 配置值|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | 字符串 | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | 字符串 | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | 字符串 | ${userUPN} **或** ${userEmailAddress} |
   |Citrix 终结点管理 | IntuneMAMUPN | 字符串 | ${user.userprincipalname} |
   |ManageEngine 移动设备管理器 | IntuneMAMUPN | 字符串 | %upn% |

> [!NOTE]  
> 对于 iOS 中的 Outlook 应用，如果通过“使用配置设计器”选项部署应用配置策略，将在后台自动为该策略配置 IntuneMAMUPN 配置键。 有关更多详细信息，请参阅[新的 Outlook for iOS 和 Outlook for Android 应用配置策略体验 – 常规应用配置](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481)中的常见问题解答部分。 


### <a name="example-2-end-user-experience"></a>示例 2：最终用户体验

使用 OS 共享从策略托管应用共享到其他应用程序

1. 用户在已注册的 iOS 设备上打开 Microsoft OneDrive 应用并登录到其工作帐户。  用户输入的工作帐户必须与你在 Microsoft OneDrive 应用的应用配置设置中指定的帐户 UPN 匹配。

2. 登录后，你的管理员配置的应用设置将应用到 Microsoft OneDrive 中的用户帐户。  这包括将“将组织数据发送到其他应用”设置配置为“具有 OS 共享的策略托管应用”值。

3. 用户预览工作文件，并尝试通过打开方式共享到 iOS 托管应用。  

4. 数据传输成功，数据现在受 iOS 托管应用中的“打开方式管理”保护。  Intune 应用不适用于非策略托管应用的应用程序。

从 iOS 托管应用共享到包含传入组织数据的策略托管应用

1. 用户使用托管电子邮件配置文件在已注册的 iOS 设备上打开本机邮件。  

1. 用户将本机邮件中的工作文档附件打开到 Microsoft Word。

1. 当 Word 应用启动时，会出现以下两种情况之一：
   1. 出现以下情况时，数据受 Intune 应用保护：
      - 用户登录了与你在 Microsoft Word 应用的应用配置设置中指定的帐户 UPN 匹配的工作帐户。 
      - 你的管理员配置的应用设置应用到 Microsoft Word 中的用户帐户。  这包括将“从其他应用接收数据”设置配置为“具有传入组织数据的所有应用”值。
      - 数据传输成功，并且已在应用中使用工作标识标记了该文档。  Intune APP 保护用户对文档进行的操作。
   1. 出现以下情况时，数据不受 Intune 应用保护：
      - 用户未登录到工作帐户。
      - 由于用户未登录，你的管理员配置的设置未应用于 Microsoft Word。
      - 数据传输成功，但未在应用中使用工作标识标记该文档。  Intune 应用不保护用户对文档进行的操作，因为它未处于活动状态。

    > [!NOTE]
    > 用户可以添加个人帐户并通过该帐户使用 Word。 用户在工作环境之外使用 Word 时，不会应用应用保护策略。 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>为第三方 EMM 验证用户 UPN 设置

配置用户 UPN 设置后，验证 iOS 应用接收和遵守 Intune 应用保护策略的能力。

例如，对“需要应用 PIN”策略设置进行测试较为容易。 如果策略设置等同于“需要”，则用户在可以访问公司数据之前，应会看到提示，要求设置或输入 PIN。

首先，向 iOS 应用[创建和分配应用保护策略](app-protection-policies.md)。 有关如何测试应用保护策略的详细信息，请参阅[验证应用保护策略](app-protection-policies-validate.md)。


## <a name="see-also"></a>另请参阅
[什么是 Intune 应用保护策略](app-protection-policy.md)
