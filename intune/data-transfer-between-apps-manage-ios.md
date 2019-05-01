---
title: 管理 iOS 应用之间的数据传输
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中使用移动应用管理策略来管理应用之间的数据传输。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb109f8c837fe8848ad8cb19c930de765ed381d1
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509499"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>如何在 Microsoft Intune 中管理 iOS 应用之间的数据传输

若要帮助保护公司数据，请限制仅在你管理的应用之间进行文件传输。 可以通过以下方式管理 iOS 应用：

-   通过为应用配置应用保护策略来防止公司数据丢失，我们将这种应用称为“策略托管”应用。 请参阅 [all the Intune-managed apps you can manage with app protection policy](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)（所有可使用应用保护策略管理的 Intune 托管应用）

-   通过“MDM 通道”部署和管理应用需要设备注册移动设备管理 (MDM) 解决方案。 部署的应用可以是“策略托管”应用，也可以是其他托管应用。

适用于 iOS 设备的“打开方式管理”功能可以将文件传输限制为仅在使用“MDM 通道”部署的应用之间进行。 在配置设置中设置“打开方式管理”限制，然后使用 MDM 解决方案进行部署。  用户安装部署应用时，即会应用所设置的限制。

##  <a name="use-app-protection-with-ios-apps"></a>对 iOS 应用使用应用保护
可将应用保护策略与 iOS 的“打开方式管理”功能结合使用，从而通过以下方式保护公司数据：

-   **不由任何 MDM 解决方案管理的员工自带设备：** 可以将应用保护策略设置设置为“仅允许应用将数据传输到策略托管应用”。 策略托管应用中的“打开方式”行为只会将其他策略托管应用用作共享选项。 如果用户尝试在本机邮件应用中从 OneDrive 以附件形式发送受策略保护的文件，该文件将无法读取。

-   **由 Intune 管理的设备：** 对于在 Intune 中注册的设备，自动允许在具有应用保护策略的应用与其他通过 Intune 部署的托管 iOS 应用之间进行数据传输。 要指定数据传输到其他应用的方式，请启用“允许应用向其他应用传送数据”，然后选择首选的共享级别。 要指定应用从其他应用接收数据的方式，请启用“允许应用从其他应用接收数据”，然后选择首选的数据接收级别。 可使用“打开方式管理”功能控制在通过 Intune 部署的应用之间进行的数据传输。 有关如何接收和共享应用数据的详细信息，请参阅[数据重定位设置](app-protection-policy-settings-ios.md#data-protection)。   

-   **由第三方 MDM 解决方案管理的设备：** 可以使用 iOS 的“打开方式管理”功能将数据传输限制为仅在托管应用之间进行。
若要确保使用第三方 MDM 解决方案部署的应用也与 Intune 应用保护策略相关联，请按照下一部分[配置用户 UPN 设置](#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)演练中所述，配置用户 UPN 设置。 如果应用是使用用户 UPN 设置部署的，则会在用户使用工作帐户登录时将应用保护策略应用到该应用。

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>为 Microsoft Intune 或第三方 EMM 配置用户 UPN 设置
对于由 Intune 或第三方 EMM 解决方案管理的设备，配置用户 UPN 设置是必需的。 UPN 配置可与从 Intune 中部署的应用保护策略一同使用。 下述过程是配置 UPN 设置的一般流程以及该过程所产生的用户体验：

1.  在 [Azure 门户](https://portal.azure.com)中，为 iOS [创建并分配应用保护策略](app-protection-policies.md)。 根据公司要求配置策略设置，并选择应使用此策略的 iOS 应用。

2.  使用下面的常规步骤，通过 Intune 或第三方 MDM 解决方案，部署想要托管的应用和电子邮件配置文件。 示例 1 中也涵盖了这一体验。

3.  通过托管设备的下列应用配置设置来部署该应用：

      键 = IntuneMAMUPN，值 = <username@company.com>

      示例：[‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]
      
       > [!NOTE]
       > 在 Intune 中，应用配置策略必须针对“托管设备”这一注册类型。
       > 此外，如果设为可用，则需要从 Itune 公司门户安装应用；或者根据需要将应用推送到设备。 

4.  使用 Intune 或第三方 MDM 提供程序将“打开方式管理”策略部署到已注册设备。


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
   |ManageEngine 移动设备管理器 | IntuneMAMUPN | 字符串 | %upn% |


### <a name="example-2-end-user-experience"></a>示例 2：最终用户体验

1.  用户在设备上安装 Microsoft Word 应用。

2.  用户启动托管的本机电子邮件应用以访问其电子邮件。

3.  用户尝试在 Microsoft Word 中打开本机邮件中的文档。

4.  Word 应用启动时，将提示用户使用其工作帐户进行登录。 用户输入的工作帐户必须与与你在 Microsoft Word 应用的应用配置设置中指定的帐户匹配。

    > [!NOTE]
    > 用户可以添加个人帐户并通过该帐户使用 Word。 用户在工作环境之外使用 Word 时，不会应用应用保护策略。 

5.  登录后，应用保护策略设置将应用到 Word 应用。

6.  现在数据传输成功，并且已在应用中使用企业标识标记了该文档。  将在工作环境下处理数据并应用策略设置。 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>为第三方 EMM 验证用户 UPN 设置

配置用户 UPN 设置后，验证 iOS 应用接收和遵守 Intune 应用保护策略的能力。

例如，对“需要应用 PIN”策略设置进行测试较为容易。 如果策略设置测试结果为“是”，则用户在可以访问公司数据之前，应会看到提示，要求设置或输入 PIN。

首先，向 iOS 应用[创建和分配应用保护策略](app-protection-policies.md)。 有关如何测试应用保护策略的详细信息，请参阅[验证应用保护策略](app-protection-policies-validate.md)。


### <a name="see-also"></a>另请参阅
[什么是 Intune 应用保护策略](app-protection-policy.md)
