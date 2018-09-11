---
title: 什么是应用保护策略
titleSuffix: Microsoft Intune
description: 了解 Microsoft Intune 应用保护策略如何帮助保护公司数据，防止数据丢失。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 08/16/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 4189e9357c7ed135ab219b38f22d34a09ebb5318
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253674"
---
# <a name="what-are-app-protection-policies"></a>什么是应用保护策略？


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune 应用保护策略可帮助保护公司数据，防止数据丢失。

## <a name="how-you-can-protect-app-data"></a>如何保护应用数据
你的员工使用移动设备进行个人任务和工作任务。  你既要确保员工高效工作，又希望防止有意和无意的数据丢失。  此外，还想要具备保护设备（即使在该设备不由你管理的情况下）所访问的公司数据的能力。

可使用 Intune 应用保护策略帮助保护公司数据。 由于 Intune 应用保护策略可以**独立于任何移动设备管理 (MDM) 解决方案**使用，所以无论是否在设备管理解决方案中注册设备，都可用它保护公司的数据。 通过实现**应用级别策略**，即可限制对公司资源的访问，并让数据处于 IT 部门的监控范围之内。

可对运行在设备上的应用进行配置的应用保护策略包括：

- **在 Microsoft Intune 中注册：** 此类别中的设备通常是公司自有设备。

- **在第三方移动设备管理 (MDM) 解决方案中注册：** 该类别中的设备通常为公司自有设备。

  > [!NOTE]
  > 移动应用管理策略不应与第三方移动应用管理或安全容器解决方案一起使用。

- **未在任何移动设备管理解决方案中注册：** 该类别中的设备通常为员工自有设备，且未在 Intune 或其他 MDM 解决方案中托管或注册。

> [!IMPORTANT]
> 可为连接到 Office 365 服务的 Office 移动应用创建移动应用管理策略。 此外，还可以通过为启用了混合现代身份验证的 Outlook for iOS 和 Outlook for Android 创建 Intune 应用保护策略来保护对 Exchange 本地邮箱的访问。 使用此功能之前，请确保满足[适用于 iOS 和 Android 的 Outlook 要求](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)。 连接到本地 Exchange 或 SharePoint 服务的其他应用不支持应用保护策略。

**使用应用保护策略的主要优点有**

-   在应用级别保护公司数据。  由于移动应用管理不需要设备管理，所以你可以在托管和非托管设备上保护公司数据。 管理以用户标识为中心，因而不再需要设备管理。

-   不会影响最终用户工作效率，且在个人环境中使用应用时不会应用策略。  这些策略仅应用于工作环境，让你能够保护公司数据而不接触个人数据。

将 MDM 与应用保护策略一起使用还有其他优点，公司可以同时使用应用保护策略与 MDM，也可以单独使用应用保护策略。 例如，员工可能使用公司分发的手机和个人平板电脑。  在这种情况下，公司的手机在 MDM 中注册且受应用保护策略保护，而个人设备仅受应用保护策略保护。

- **MDM 确保该设备受到保护**。  例如，你可以要求使用 PIN 以访问设备，或将托管应用部署到设备。 还可通过 MDM 解决方案将应用部署到设备，以便更好地控制应用管理。

- **应用保护策略确保应用层保护措施到位**。 例如，你可以要求在工作环境中使用 PIN 打开应用，要求应用之间是否可以共享数据，或要求阻止将公司应用数据保存到个人存储位置。


### <a name="supported-platforms-for-app-protection-polices"></a>应用保护策略的受支持平台
Intune 应用保护策略平台支持遵循 Office 应用程序平台支持。 有关详细信息，请参阅 [Office 系统要求](https://products.office.com/en-US/office-system-requirements)。

目前不支持 Windows 设备。 但是，使用 Intune 注册 Windows 10 设备时，可以使用 Windows 信息保护，它提供了类似功能。 有关详细信息，请参阅[使用 Windows 信息保护 (WIP) 保护企业数据](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。
##  <a name="how-app-protection-policies-protect-app-data"></a>应用保护策略如何保护应用数据

####  <a name="apps-without-app-protection-policies"></a>不具有应用保护策略的应用

![图像显示在未实施应用保护策略时，数据可在应用之间自由移动](./media/apps-without-protection-policies.png)

在无限制的情况下使用应用时，公司和个人数据可能混合。  公司数据可能最终位于个人存储空间等位置或传输到你监控范围外的应用中，导致数据丢失。 图中的箭头显示了（公司和个人）应用之间和移动到存储位置的无限制数据移动。


### <a name="data-protection-with-app-protection-policies"></a>采用应用保护策略的数据保护

![图像显示在应用应用保护策略时保护公司数据的方式 ](./media/apps-with-protection-policies.png)


可以使用应用保护策略来防止将公司数据保存到设备的本地存储器上，并限制将数据移动到不受应用保护策略保护的其他应用中。 应用保护策略设置包括：
- 数据重定位策略，例如**阻止另存为**、**限制剪切、复制和粘贴**。
- 访问策略设置，例如**访问需要简单 PIN**、**阻止在已越狱或取得 root 权限的设备上运行托管应用**。

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>在由 MDM 解决方案管理的设备上，采用应用保护策略保护数据

![图像显示应用保护策略如何在 BYOD 设备上起作用](./media/app-protection-policies-with-mdm.png)

**对于在 MDM 解决方案中注册的设备**-

上图显示了 MDM 和应用保护策略共同提供的保护层。

MDM 解决方案：

-   注册设备

-   将应用部署到设备

-   提供持续的设备合规性和管理

**应用保护策略增加价值的方式：**

-   帮助防止公司数据泄露到使用者应用和服务

-   将限制（另存为、剪贴板、PIN 等）应用到移动应用

-   从应用擦除公司数据而不从设备删除这些应用


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>采用上适用于未注册设备的应用保护策略保护数据

![图像显示应用保护策略如何在受管理设备上起作用](./media/app-protection-policies-without-mdm.png)

以上图示显示了在不没有 MDM 的情况下，数据保护策略如何在应用级别工作。

对于未在任何 MDM 解决方案中注册的 BYOD 设备，应用保护策略可在应用级别帮助保护公司数据。
但是，有一些限制需要注意，如：

-   无法将应用部署到设备。  最终用户必须从应用商店获取应用。

-   无法在这些设备上设置证书配置文件。

-   无法在这些设备上设置公司 Wi-Fi 和 VPN 设置。


## <a name="multi-identity"></a>多身份

支持多身份的应用允许用户使用不同的帐户（工作和个人）访问相同的应用，但仅当在工作环境中使用这些应用时，才会应用应用保护策略。

例如，当用户使用其工作帐户启动 OneDrive 应用时，无法将文件移到个人存储位置。 但是，当用户通过其个人帐户使用 OneDrive 时，可无限制地从个人 OneDrive 复制和移动数据。

- 了解支持 Intune 的 [MAM 和多身份](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的应用的详细信息。

##  <a name="next-steps"></a>后续步骤

[如何使用 Microsoft Intune 创建和部署应用保护策略](app-protection-policies.md)

## <a name="see-also"></a>另请参阅
第三方应用（例如 Salesforce 移动应用）与 Intune 一起以特定的方式来保护公司数据。 若要详细了解 Salesforce 应用专门与 Intune 合作的方式（包括 MDM 应用配置设置），请参阅 [Salesforce 应用和 Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf)。
