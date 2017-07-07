---
title: "保护发送到 Exchange 内部部署的电子邮件"
description: "使用条件访问保护和控制对本地 Exchange 的公司电子邮件的访问。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 58d89fed98994c3c1bf77118a26592c855e8498e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="protect-email-access-to-exchange-on-premises-and-legacy-exchange-online-dedicated-with-intune"></a>使用 Intune 保护对 Exchange 内部部署和旧版 Exchange Online Dedicated 的电子邮件访问

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

可通过 Microsoft Intune 配置对 Exchange 内部部署或旧版 Exchange Online Dedicated 的条件性访问，以控制电子邮件的访问。
若要了解有关条件性访问如何工作的详细信息，请阅读文章[保护对电子邮件和 O365 服务的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。

> [!NOTE]
> 如果具有 Exchange Online Dedicated 环境并需要确定其采用的是新配置还是旧配置，请与帐户管理员联系。

## <a name="before-you-begin"></a>在开始之前

请务必验证以下各项：

-   你的 Exchange 版本必须是 **Exchange 2010 或更高版本**。 支持 Exchange Server 客户端访问服务器 (CAS) 阵列。

-   必须使用 [Intune 本地 Exchange Connector](intune-on-premises-exchange-connector.md)，该连接器可将 Intune 连接到 Exchange 本地环境。 这样就可以通过 Intune 控制台管理设备。

    -   Intune 控制台中可供你使用的本地 Exchange Connector 特定于你的 Intune 租户，且不能用于其他任何租户。 建议你同时确保**仅在一台计算机上**安装适用于你的租户的 Exchange Connector。

        可从 Intune 管理控制台下载连接器。 有关如何配置本地 Exchange Connector 的演练，请参阅[为本地或托管 Exchange 配置 Exchange 本地连接器](intune-on-premises-exchange-connector.md)。

    -   可在任何计算机上安装该连接器，只要该计算机可与 Exchange 服务器通信。

    -   此连接器支持 **Exchange CAS 环境**。 从技术上讲，如果你愿意，可直接在 Exchange CAS 服务器上安装该连接器。 但不建议这样做，因为这样做会增加服务器上的负载。 配置连接器时，必须对其进行设置，以便与其中一个 Exchange CAS 服务器通信。

-   必须使用基于证书的身份验证或用户凭据条目来配置 **Exchange ActiveSync**。

### <a name="device-compliance-requirements"></a>设备合规性要求

配置条件性访问策略并将它们面向用户时，在用户可以连接到其电子邮件前，他们使用的**设备**必须：

-  是已加入域的电脑或已向 Intune **注册**。

-  **已在 Azure Active Directory 中注册**。 此外，还必须向 Azure Active Directory 注册客户端 Exchange ActiveSync ID。

  Azure Active Directory 设备注册服务自动对 Intune 和 Office 365 客户激活。 已经部署了 ADFS 设备注册服务的用户不会在本地 Active Directory 上看到已注册的设备。 **这不适用于 Windows 电脑和 Windows Phone 设备**。

-   **符合**任何部署到该设备的 Intune 符合性策略。

### <a name="how-conditional-access-works-with-exchange-on-premises"></a>条件性访问对 Exchange 内部部署的作用方式

下图显示了 Exchange 内部部署的条件性访问策略用于评估是允许还是阻止设备的流程。

![图示显示了确定是允许访问还是阻止设备访问 Exchange 内部部署的决策点](../media/ConditionalAccess8-2.png)

如果未满足条件访问策略，则用户在登录时，收到以下隔离邮件之一与设备被阻止之间的时间间隔为 10 分钟：

- 如果设备未向 Intune 注册，或未在 Azure Active Directory 中注册，则会显示一条消息，其中包含有关如何安装公司门户应用、注册设备和激活电子邮件的说明。 此过程也将设备的 Exchange ActiveSync ID 和 Azure Active Directory 中的设备记录相关联。

-   如果设备不符合策略，则会显示一条消息，将用户定向到 Intune 公司门户网站或公司门户应用，用户可在其中找到有关该问题及其修正方法的信息。

## <a name="support-for-mobile-devices"></a>对移动设备的支持
支持以下设备：
-   Windows Phone 8.1 及更高版本。

-   iOS 上的本机电子邮件应用。

-   Exchange ActiveSync 邮件客户端（如 Android 4 或更高版本上的 Gmail）。
-   **Android for Work 设备上的 Exchange ActiveSync 邮件客户端：**Android for Work 设备上仅支持**工作配置文件**中的 **Gmail** 和 **Nine Work** 应用。 若要使条件访问可适用于 Android for Work，必须为 Gmail 或 Nine Work 应用部署电子邮件配置文件，还要将这些应用部署为必需安装。 

> [!NOTE]
> 不支持 Android 和 iOS 上的 Microsoft Outlook 应用。

## <a name="support-for-pcs"></a>对 PC 的支持
支持以下项：
-   Windows 8.1 及更高版本上的**邮件**应用程序（向 Intune 注册电脑时）。

##  <a name="configure-a-conditional-access-policy"></a>配置条件性访问策略

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择**策略**  >  **条件性访问**  >  **Exchange 本地策略**。
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  使用所需的设置来配置策略：![Exchange 内部部署策略页面的屏幕截图](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **如果设备不符合策略或未向 Microsoft Intune 注册，则阻止电子邮件应用访问本地 Exchange**：选择此选项时，会阻止未受 Intune 管理的设备或不符合策略的设备访问 Exchange 服务。

  - **替代默认规则 - 始终允许已注册并符合要求的设备访问 Exchange**：选择此选项时，允许已在 Intune 中注册并符合合规性策略的设备访问 Exchange。
  此规则将替代“默认规则”，这意味着，即使将“默认规则”设置为隔离或阻止访问，已注册并符合要求的设备也仍然能够访问 Exchange。

  - **目标组**：选择 Intune 用户组，这些用户组必须先向 Intune 注册其设备，然后才能访问 Exchange。

  - **免除组**：选择将从条件性访问策略中免除的 Intune 用户组。 此列表中的用户将会被免除，即使它们也位于“目标组”列表中。

  - **平台例外**：选择“添加规则”配置一个规则，为指定的移动设备系列和模型定义访问级别。 因为这些设备可为任何类型，所以还可配置不受 Intune 支持的设备类型。

  - **默认规则**：对于不受其他任何规则约束的设备，可选择允许或阻止其访问 Exchange，也可以隔离它。 对于已注册并合规的设备，如果将该规则设置为允许访问，将会自动向 iOS、Windows 和 Samsung KNOX 设备授予电子邮件访问权限。 用户不必执行任何过程即可获取其电子邮件。
      - 在不运行 Samsung KNOX 的 Android 设备上，用户会收到一封包含指导性演练的隔离电子邮件，用于验证注册和合规性，验证后他们才能访问电子邮件。 如果将该规则设置为阻止访问或隔离设备，将阻止所有设备访问 Exchange，无论设备是否已在 Intune 中注册。 若要防止已注册并符合要求的设备受此规则影响，请选中“替代默认规则”框。
>[!TIP]
>如果想在授予电子邮件访问权限之前先阻止所有设备，请选择“阻止访问”规则或“隔离”规则。 默认规则适用于所有设备类型，因此作为平台例外配置且不受 Intune 支持的设备类型也会受到影响。

  - **用户通知**：除了 Exchange 发送的通知电子邮件之外，Intune 还将发送一封包含取消阻止设备的步骤的电子邮件。 你可以根据需求来自定义编辑默认消息。 如果用户的设备在接收包含修正说明的 Intune 通知电子邮件之前已被阻止（此电子邮件发送到用户的 Exchange 邮箱），则用户可使用取消阻止的设备或其他方法来访问 Exchange 并查看该邮件。
      - 当“默认规则”设置为阻止或隔离时尤其如此。 在这种情况下，用户必须转到其应用商店，下载 Microsoft 公司门户应用并注册其设备。 这适用于 iOS、Windows 和 Samsung KNOX 设备。 对于不运行 Samsung KNOX 的设备，需要将隔离电子邮件发送到备用电子邮件帐户。 用户必须将电子邮件复制到其被阻止的设备，以完成注册和符合性过程。
  > [!NOTE]
  > 若要让 Exchange 能够发送通知电子邮件，必须指定用于发送通知电子邮件的帐户。
  >
  > 有关详细信息，请参阅[为本地或托管 Exchange 配置 Exchange 内部部署连接器](intune-on-premises-exchange-connector.md)。

3.  完成后，选择“保存”。

-   不需要部署条件访问策略—它会立即生效。

-   用户设置 Exchange ActiveSync 配置文件后，可能需要 1-3 小时设备才会被阻止（如果它不由 Intune 管理）。

-   如果被阻止的用户随后向 Intune 注册设备并更正不符合性，将在两分钟内解除电子邮件访问阻止。

-   如果用户从 Intune 取消注册，可能需要 1-3 小时设备才会被阻止。

**若要查看如何配置条件性访问策略以保护设备访问的示例方案，请参阅[保护电子邮件访问的示例方案](restrict-email-access-example-scenarios.md)。**

## <a name="next-steps"></a>后续步骤
-   [保护对 SharePoint Online 的访问](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

-   [保护对 Skype for Business Online 的访问](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
