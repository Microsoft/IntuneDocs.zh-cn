---
title: "Intune 的常见使用方式"
description: "列出了 Intune 可提供帮助的六个最常见任务"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: robstackmsft
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: d83f2c2e410d23297dad7f046f8053225c988abc
ms.openlocfilehash: 237e141eacb413eb130b17217116b6d0c7e085f8
ms.contentlocale: zh-cn
ms.lasthandoff: 06/15/2017


---

# <a name="common-ways-to-use-intune"></a>Intune 的常见使用方式

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

在深入探讨实现任务之前，务必使公司的企业移动性利益干系人在业务目标上保持一致。  不管你是全新购买企业移动性产品还是迁移自另一个产品，这一点都很重要。  

对企业移动性的需求在不断地动态演化，用于解决这些需求的 Microsoft 方法有时可能不同于市场上的其他解决方案。 在业务目标上保持一致的最好办法是，从你想要为员工、合作伙伴和 IT 部门实现的方案的角度，来表达你的目标。  

下面简单介绍了六种依赖于 Intune 的最常见的方案，并附有关于如何规划和部署其中每个方案的详细信息的链接。

>[!NOTE]
>是否想了解 Microsoft IT 如何使用 Intune 来允许 Microsoft 访问其移动设备上的公司资源，同时保护公司数据？ 若要详细了解 Microsoft IT 如何使用 Intune 和其他服务来管理标识、设备、应用及数据，请[阅读本技术案例研究](https://www.microsoft.com/itshowcase/Article/Content/588)。  

>[!IMPORTANT]
>我们希望确保移动设备紧随 iOS 设备上最新的“Trident”恶意软件攻击保持最新状态。 因此我们发布了一篇博客文章，名为[使用 Microsoft Intune 确保移动设备保持最新](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/)。 它提供有关 Intune 以不同方式帮助保持设备处于安全和最新状态的信息。

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>保护本地电子邮件和数据以供移动设备安全访问
大多数企业移动性战略的第一步是制定一项计划，让使用连接到 Internet 的移动设备的员工能够安全地访问电子邮件。 许多组织仍然在公司网络上托管了本地数据和应用程序服务器（如 Microsoft Exchange）。


Intune 和 Microsoft 企业移动性 + 安全性 (EMS) 为 Exchange Server 提供了一种独特的集成[条件性访问解决方案](conditional-access.md)（[经典门户](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)），可确保在设备通过 Intune 注册之前，没有任何移动应用可以访问电子邮件。 而这一切无需在公司网络边缘部署其他网关计算机即可完成！

Intune 还支持对需要安全访问本地数据的移动应用（例如业务线应用服务器）启用访问权限。 为此，通常需要将用于访问控制的 [Intune 托管证书](certificates-configure.md)（[经典门户](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)）与外围中的标准 VPN 网关或代理（如 Microsoft Azure Active Directory 应用程序代理）结合使用。  

在这些情况下，访问公司数据的唯一方法是将设备注册到管理系统中。 当设备注册后，管理系统可确保只有符合公司策略的设备才能访问公司数据。 此外，可以借助 Intune 的[应用包装工具和应用 SDK](apps-prepare-mobile-application-management.md) 将已访问的数据包含在业务线应用中，这样它就不能将公司数据传递给消费者应用或服务。

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->


## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>保护 Office 365 电子邮件和数据以供移动设备安全访问
在 Office 365 中保护公司数据（电子邮件、文档、即时消息、联系人）既方便了你，又给用户带来了更加顺畅的体验。


Intune 和 Microsoft 企业移动性 + 安全性提供了独一无二的集成式条件性访问解决方案，确保用户、应用或设备在符合公司的合规性要求（已执行[多重身份验证](/intune-classic/deploy-use/multi-factor-authentication-azure-active-directory)，已向 Intune 注册，使用托管应用、受支持的 OS 版本、设备 PIN 和低用户风险配置文件等等）之前无法访问 Office 365 数据。


相应应用商店中的 Office 移动应用备有可通过 Intune 配置的数据包含策略。 这使你能够避免与未由 IT 管理的应用（例如本机电子邮件应用）和存储位置（例如 Dropbox）共享数据。 此功能完全内置于 Office 365 和 EMS 中。 无需部署其他基础结构便可获得此功能。

在常见的 Office 365 部署做法中，如果需要使用公司应用/证书/Wi-Fi/VPN 配置来完全设置设备（公司拥有设备常见方案），则必须将设备注册到管理系统中。  


但是，如果用户只需访问公司电子邮件和文档（通常是个人拥有的设备），则可要求用户使用 Office 移动应用（已向其应用[应用保护策略](app-protection-policies.md)（[经典门户](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune)）），并且完全跳过设备注册！  



无论哪种方式，Office 365 数据都将受到已定义策略的保护。

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->


## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>为所有员工提供“自带设备办公”计划
自带设备办公 (BYOD) 可以降低硬件开销或增加员工的移动工作效率选择，因此受到越来越多组织的青睐。 现如今几乎人手一部手机，因此为什么还要往他们的口袋里再添一个？ 公司一直以来的主要难题就是说服员工将其个人设备注册到管理系统中，因为他们担心 IT 部门能看到其设备中的信息并对其设备进行处理。  

在设备注册不可行的情况下，Intune 可提供一个替代的 BYOD 方法，用来简单地[管理包含公司数据的应用](app-protection-policies.md)（[经典门户](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune)）。 与 Office 移动应用一样，即使是有问题的应用访问公司和个人数据，Intune 也能保护公司数据。  

作为管理员，可以要求用户从 Office 移动应用访问 Office 365 并使用可保护数据的策略（如加密、利用 pin 进行保护等等）配置应用。 这些策略可防止在不受管理的应用和存储位置中丢失数据 — 无论是在这些应用的内部还是外部。 例如，这些策略会阻止用户将公司电子邮件配置文件中的文本复制到消费者电子邮件配置文件，即使这两个配置文件都是在 Outlook Mobile 中配置的。 可以为 BYOD 用户所需的其他服务和应用程序部署类似的配置。

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-employees"></a>向员工发放公司拥有的手机
现在很多员工都是移动办公，这使得移动设备上的工作效率成为提高竞争力的必要途径。 这些员工需要随时随地无缝访问所有公司应用和数据。 需要确保公司数据是安全的并且管理成本较低。  

Intune 提供了[批量预配和管理解决方案](device-enrollment.md)（[经典门户](/intune-classic/deploy-use/manage-corporate-owned-devices)），可与当今市场上的主流公司设备管理平台集成，包括 Apple 设备注册计划和 Samsung KNOX 移动安全平台。 通过使用 Intune 集中创作设备配置，可帮助实现公司设备预配的高度自动化。  

想象一下：将一个未开封的 iPhone 手机盒发放给员工。 员工打开手机后，完成公司自创的设置流程，在此过程中他必须进行身份验证。 此 iPhone 经[安全策略](device-profiles.md)（[经典门户](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)）无缝配置。

然后，员工启动 Intune 公司门户应用来访问提供给他们的可选公司应用。

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-employees"></a>向员工发放使用受限的共享平板电脑
员工开始越来越多地使用移动技术。 例如，零售店员工现在广泛使用共享平板电脑。  无论是用于处理销售还是即时检查库存，平板电脑都有助于创造良好的顾客交互体验。

在这种情况下，用户体验的简单性至关重要。 出于此原因，发放给员工的平板电脑通常采用使用受限模式，使员工只能与单个业务线应用交互。 Intune 可让你批量预配、保护和集中管理这些可配置为在此使用受限模式下运行的共享 [iOS 和 Android](device-profiles.md)（[经典门户](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)）设备。

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>允许你的员工从不受管理的公用网亭安全访问 Office 365
有时，你的员工需要使用你无法管理的设备、应用或浏览器，例如展销会和酒店大堂的公用计算机。

你是否应该允许你的员工通过这些设备访问公司电子邮件？ 答案只能是“不允许”。借助 Intune 和 Microsoft 企业移动性 + 安全性解决方案，即可将此[限制为只允许受组织管理的设备访问电子邮件](conditional-access.md)（[经典门户](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)）。 这样可确保经过强身份验证的员工不会无意中将公司数据留在不受信任的计算机上。

