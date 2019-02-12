---
title: 什么是应用保护策略
titleSuffix: Microsoft Intune
description: 了解 Microsoft Intune 应用保护策略如何帮助保护公司数据，防止数据丢失。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbb6a8f159aebe837fabf671a84dd96223298227
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836347"
---
# <a name="what-are-app-protection-policies"></a>什么是应用保护策略？


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune 应用保护策略可帮助保护公司数据，防止数据丢失。

## <a name="how-you-can-protect-app-data"></a>如何保护应用数据
你的员工使用移动设备进行个人任务和工作任务。 你既要确保员工高效工作，又希望防止有意和无意的数据丢失。 你还需要保护他人设备（不由你管理的设备）访问的公司数据。

可使用 Intune 应用保护策略，该策略独立于任何移动设备管理 (MDM) 解决方案。 无论是否在设备管理解决方案中注册设备，均可借助此独立策略保护公司数据。 通过实现**应用级别策略**，即可限制对公司资源的访问，并让数据处于 IT 部门的监控范围之内。

可对运行在设备上的应用进行配置的应用保护策略包括：

- **已在 Microsoft Intune 中注册：** 这些设备通常是公司自有设备。

- **已在第三方移动设备管理 (MDM) 解决方案中注册：** 这些设备通常是公司自有设备。

  > [!NOTE]
  > 移动应用管理策略不应与第三方移动应用管理或安全容器解决方案一起使用。

- **未在任何移动设备管理解决方案中注册：** 此类设备通常是员工拥有的设备，且未在 Intune 或其他 MDM 解决方案中进行托管或注册。

> [!IMPORTANT]
> 可为连接到 Office 365 服务的 Office 移动应用创建移动应用管理策略。 此外，还可以通过为启用了混合现代身份验证的 Outlook for iOS 和 Outlook for Android 创建 Intune 应用保护策略来保护对 Exchange 本地邮箱的访问。 使用此功能之前，请确保满足[适用于 iOS 和 Android 的 Outlook 要求](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)。 连接到本地 Exchange 或 SharePoint 服务的其他应用不支持应用保护策略。

**使用应用保护策略的主要优点有**

-   在应用级别保护公司数据。 由于移动应用管理不需要设备管理，因此可在受管理和不受管理设备上保护公司数据。 管理以用户标识为中心，因而不再需要设备管理。

-   不会影响最终用户工作效率，且在个人环境中使用应用时不会应用策略。 这些策略仅应用于工作环境，能够在不接触个人数据的情况下保护公司数据。

将 MDM 与应用保护策略一起使用还有其他优点，公司可以同时使用应用保护策略与 MDM，也可以单独使用应用保护策略。 例如这样一种情况：员工同时使用公司电话和其个人平板电脑。 公司的手机在 MDM 中注册且受应用保护策略保护，而个人设备仅受应用保护策略保护。

- **MDM 确保该设备受到保护**。 例如，你可以要求使用 PIN 以访问设备，或将托管应用部署到设备。 还可通过 MDM 解决方案将应用部署到设备，以便更好地控制应用管理。

- **应用保护策略确保应用层保护措施到位**。 例如，你能够：
  - 规定在工作环境中打开应用时需使用 PIN 
  - 控制应用之间的数据共享 
  - 防止将公司应用数据保存到私人存储位置


### <a name="supported-platforms-for-app-protection-policies"></a>应用保护策略的受支持平台
Intune 应用保护策略平台支持与适用于 Android 和 iOS 设备的 Office 移动应用程序平台支持保持一致。 有关详细信息，请参阅 [Office 系统要求](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg)的“移动应用”部分。

目前不支持 Windows 设备。 但是，可以使用 Windows 信息保护，它提供了类似功能。 有关详细信息，请参阅[使用 Windows 信息保护 (WIP) 保护企业数据](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。


## <a name="how-app-protection-policies-protect-app-data"></a>应用保护策略如何保护应用数据

#### <a name="apps-without-app-protection-policies"></a>不具有应用保护策略的应用

![在没有策略的应用之间进行数据移动的概念图](./media/apps-without-protection-policies.png)

在无限制的情况下使用应用时，公司和个人数据可能混合。 公司数据可能最终位于个人存储空间等位置或传输到监控范围外的应用中，导致数据丢失。 上图中的箭头显示了公司应用和个人应用之间以及到存储位置的无限制数据移动。


### <a name="data-protection-with-app-protection-policies"></a>采用应用保护策略的数据保护

![显示公司数据受策略保护的概念图](./media/apps-with-protection-policies.png)


可使用应用保护策略以防将公司数据保存到设备的本地存储中。 还可限制将数据移动到不受应用保护策略保护的其他应用。 应用保护策略设置包括：
- 数据重定位策略，例如“防止另存为”、“限制剪切”、“复制”和“粘贴”。
- 访问策略设置，例如“需要简单的 PIN 才能访问”、“阻止在已越狱或取得 root 权限的设备上运行受管理的应用”。

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>在由移动设备管理解决方案管理的设备上，采用应用保护策略保护数据

![图像显示应用保护策略如何在 BYOD 设备上起作用](./media/app-protection-policies-with-mdm.png)

**对于在 MDM 解决方案中注册的设备**-

上图显示了 MDM 和应用保护策略共同提供的保护层。

MDM 解决方案：

-   注册设备

-   将应用部署到设备

-   提供持续的设备合规性和管理

**应用保护策略增加价值的方式：**

-   帮助防止公司数据泄露到使用者应用和服务

-   将限制（如“另存为”、“剪贴板”或“PIN”）应用到客户端应用

-   从应用擦除公司数据而不从设备删除这些应用


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>采用上适用于未注册设备的应用保护策略保护数据

![图像显示应用保护策略如何在受管理设备上起作用](./media/app-protection-policies-without-mdm.png)

上图显示在未实施 MDM 的情况下数据保护策略在应用级别的工作原理。

对于未在任何 MDM 解决方案中注册的 BYOD 设备，应用保护策略可在应用级别帮助保护公司数据。
但是，有一些限制需要注意，如：

-   无法将应用部署到设备。 最终用户必须从应用商店获取应用。

-   无法在这些设备上预配证书配置文件。

-   无法在这些设备上设置公司 Wi-Fi 和 VPN 设置。

## <a name="app-protection-global-policy"></a>应用保护全局策略

若 OneDrive 管理员浏览到 admin.office.com 并选择“设备”访问权限，则他们可为 OneDrive 和 SharePoint 客户端应用设置移动应用程序管理控件。 

这些设置可供 OneDrive 管理控制台使用，可配置名为全局策略的特殊 Intune 应用保护策略。 此全局策略适用于租户中的所有用户，且无法控制策略目标设定。 

启用后，默认情况下将使用所选设置保护适用于 iOS 和 Android 的 OneDrive 和 SharePoint 应用。 IT 专业人员可在 Intune 控制台中编辑此策略，以添加更多目标应用并修改任何策略设置。 

默认情况下，每个租户仅有一个全局策略。 然而，可使用 [Intune 图形 API](intune-graph-apis.md) 来为每个租户创建额外的全局策略，但不推荐这种做法。 不建议创建额外全局策略，因为对此类策略的实施进行故障排除会变得复杂。

虽然全局策略适用于租户中的所有用户，但任何标准的 Intune 应用保护政策都将覆盖这些设置。


## <a name="multi-identity"></a>多身份

支持多身份的应用允许用户使用不同的帐户（工作和个人）访问相同的应用，但仅当在工作环境中使用这些应用时，才会应用应用保护策略。

例如个人环境的情况：用户在 Word 中开始一个新文档，这被视为个人环境，因此不会应用 Intune 应用保护策略。 使用公司 OneDrive 帐户保存文档后，该文档将被视为工作环境，因此会应用 Intune 应用保护策略。

例如工作环境的情况：用户使用其工作帐户启动 OneDrive 应用。 在工作环境中，他们无法将文件移动到私人存储位置。 之后当用户通过其个人帐户使用 OneDrive 时，可无限制地从个人 OneDrive 复制和移动数据。

- 了解支持 Intune 的 [MAM 和多身份](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的应用的详细信息。

## <a name="next-steps"></a>后续步骤

[如何使用 Microsoft Intune 创建和部署应用保护策略](app-protection-policies.md)

## <a name="see-also"></a>另请参阅
第三方应用（例如 Salesforce 移动应用）与 Intune 一起以特定的方式来保护公司数据。 若要详细了解 Salesforce 应用专门与 Intune 合作的方式（包括 MDM 应用配置设置），请参阅 [Salesforce 应用和 Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf)。
