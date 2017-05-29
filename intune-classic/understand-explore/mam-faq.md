---
title: "有关 MAM 和应用保护的常见问题"
description: "本文提供了针对 Intune 移动应用程序管理 (MAM) 和 Intune 应用保护的一些常见问题解答。"
keywords: 
author: oydang
ms.author: oydang
manager: mtillman
ms.date: 01/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 32446d9a6f9383b5449dbabf288b0eac0b483ebb
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>有关 MAM 和应用保护的常见问题

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本文提供了针对 Intune 移动应用程序管理 (MAM) 和 Intune 应用保护的一些常见问题解答。

## <a name="mam-basics"></a>MAM 基础知识


**什么是 MAM？** [Intune 移动应用程序管理](../deploy-use/overview-of-app-lifecycle-in-microsoft-intune.md)指的是 Intune 管理功能套件，通过它能够为用户发布、推送、配置、保护、监视和更新移动应用。

**使用 MAM 应用保护有什么好处？** MAM 可保护应用程序内组织的数据。 通过 MAM-WE，可以在几乎任何设备上管理包含敏感数据的工作或学校相关应用，包括自带设备办公 (BYOD) 场景下的个人设备。 许多生产型应用，例如 Microsoft Office 应用，都可以通过 Intune MAM 进行管理。 请参阅可供公众使用的 [Intune 启用的应用](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的官方列表。

**MAM 支持哪些设备配置？** Intune MAM 支持两种配置：
  1. **Intune MDM + MAM**：这是首次启动 MAM 时它所支持的第一个配置。 IT 管理员仅可在已进行 Intune 移动设备管理 (MDM) 注册的设备上使用 MAM 和应用保护策略管理应用。 若要使用 MDM + MAM 管理应用，客户应使用 https://manage.microsoft.com 上的 Intune 独立控制台。

  2. **无需设备注册的 MAM**：无需设备注册的 MAM 或 MAM-WE 使 IT 管理员可以在未进行 Intune MDM 注册的设备上使用 MAM 和应用保护策略管理应用。 这意味着可以在进行了第三方 EMM 提供程序注册的设备上通过 Intune 管理应用。 若要使用 MAM-WE 管理应用，客户应使用 http://portal.azure.com 上的 Azure 门户中的 Intune 控制台。


## <a name="app-protection-policies"></a>应用保护策略

**什么是应用保护策略？** 应用保护策略是可确保组织数据在管理的应用中保持安全或受到控制的规则。 策略可以是在用户尝试访问或移动“公司”数据时强制执行的规则，或在用户位于应用内时受到禁止或监视的一组操作。

**应用保护策略的示例有哪些？** 请参阅 [Android 应用保护策略设置](../deploy-use/android-mam-policy-settings.md)和 [iOS 应用保护策略设置](../deploy-use/ios-mam-policy-settings.md)，获取有关每种应用保护策略设置的详细信息。

## <a name="apps-you-can-manage-with-app-protection-policies"></a>可使用应用保护策略进行管理的应用

**可通过应用保护策略管理哪些应用？** 已通过 [Intune App SDK](../develop/intune-app-sdk.md) 启用的或通过 [Intune 应用包装工具](../deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)包装的任何应用都可使用 Intune 应用保护策略进行管理。 请参阅可供公众使用的 [Intune 启用的应用](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的官方列表。

**在 Intune 启用的应用上使用应用保护策略的基本要求有哪些？**
  1. 最终用户必须具有 Azure Active Directory (AAD) 帐户。 请参阅[添加用户并授予对 Intune 的管理权限](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md)，了解如何在 Azure Active Directory 中创建 Intune 用户。

  2. 最终用户必须具有分配给其 Azure Active Directory 帐户的 Microsoft Intune 许可证。 请参阅[管理 Intune 许可证](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4.md)，了解如何将 Intune 许可证分配给最终用户。

  3. 最终用户必须属于应用保护策略所面向的一个安全组。 同一应用保护策略必须面向正在使用的特定应用。 可以在 [Azure 门户](http://portal.azure.com)的 Intune 控制台中创建和部署应用保护策略。 当前可以在 [Office 门户](http://portal.office.com)中创建安全组。

  4. 最终用户必须使用其 AAD 帐户登录到应用。

**使用 [Outlook 移动应用](https://www.microsoft.com/outlook-com/mobile/)有什么其他要求？**

  1. 最终用户必须将 Outlook 移动应用安装到其设备上。

  2. 最终用户必须具有链接到其 Azure Active Directory 帐户的 [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) 邮箱和许可证。

  >[!NOTE]
  > Outlook 移动应用当前仅支持 Microsoft Exchange Online，不支持 Exchange 内部部署或 Office 365 Dedicated 中的 Exchange。

**使用 [Word、Excel 和 PowerPoint](https://products.office.com/business/office) 应用有什么其他要求？**

  1. 最终用户必须具有链接到其 Azure Active Directory 帐户的 [Office 365 商业版或企业版](https://products.office.com/business/compare-more-office-365-for-business-plans)许可证。 订阅必须包括移动设备上的 Office 应用和 [OneDrive for Business](https://onedrive.live.com/about/business/) 云存储帐户。 遵循这些[说明](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)可在 [Office 门户](http://portal.office.com)中分配 Office 365 许可证。

  2. 最终用户必须将 [OneDrive](https://onedrive.live.com/about/) 应用安装到其设备上并使用 AAD 帐户进行登录。

  3. 部署到最终用户的应用保护策略必须面向 OneDrive 应用。

  >[!NOTE]
  > Office 移动应用当前仅支持 SharePoint Online，不支持本地 SharePoint。

**为什么 Office 需要 OneDrive？** Intune 会将应用中的所有数据标记为“公司”或“个人”。 数据源于业务位置时会被视为“公司”数据。 对于 Office 应用，Intune 将以下数据视为业务位置：电子邮件 (Exchange) 或云存储（包含 OneDrive for Business 帐户的 OneDrive 应用）。

**使用 Skype for Business 有什么其他要求？** 请参阅 [Skype for Business](https://products.office.com/skype-for-business/it-pros) 许可证要求。
  >[!NOTE]
  > Skype for Business 移动应用当前仅支持 Skype for Business Online。

## <a name="app-protection-features"></a>应用保护功能

**什么是多身份支持？** 多身份支持可使 Intune App SDK 仅将应用保护策略应用于已登录到应用的工作或学校帐户。 如果个人帐户登录到应用，数据将保持不变。

**多身份支持的用途是什么？** 多身份支持使得能够公开发布具有“公司”和消费者受众的应用（如 Office 应用），同时让“公司”帐户具有 Intune 应用保护功能。

**PIN 屏幕何时出现？** 仅当用户尝试访问应用中的“公司”数据时，Intune PIN 屏幕才会出现。 例如在 Word/Excel/PowerPoint 应用中，当最终用户尝试从 OneDrive for Business 打开文档（假定已成功部署强制执行 PIN 的应用保护策略）时，它才会出现。

**Outlook 和多身份呢？** 由于 Outlook 具有个人和“公司”电子邮件的混合电子邮件视图，Outlook 应用会在启动时提示输入 Intune PIN。

**Intune 应用 PIN 是什么？** 个人标识号 (PIN) 是一种密码，用于验证是否是正确的用户在应用程序中访问组织的数据。

  1. **何时提示用户输入其 PIN？** 仅当用户要访问“公司”数据时，Intune 才会提示输入用户的应用 PIN。 在诸如 Word/Excel/PowerPoint 等多身份应用中，当用户尝试打开“公司”文档或文件时，会向他们提示输入 PIN。 在单身份应用中，例如使用 Intune 应用包装工具启用的业务线应用，会在启动时提示输入 PIN，因为 Intune App SDK 知道用户在应用中的体验始终是针对“公司”的。

  2. **PIN 安全吗？** PIN 仅允许正确的用户在应用中访问其组织数据。 因此，最终用户必须使用其工作或学校帐户登录，然后才能设置或重置其 Intune 应用 PIN。 这种身份验证通过安全的令牌交换由 Azure Active Directory 执行，且不对 Intune App SDK 公开。 从安全性的角度来看，保护工作或学校数据的最佳方法便是对其进行加密。 加密与应用 PIN 无关，它本身是一项应用保护策略。

  3. **Intune 如何保护 PIN 免遭暴力破解攻击？** 作为应用 PIN 策略的一部分，IT 管理员可以设置在锁定应用之前用户可尝试验证其 PIN 的最大次数。 达到最大尝试次数后，Intune App SDK 可以擦除应用中的“公司”数据。

**加密呢？** IT 管理员可以部署要求对应用数据进行加密的应用保护策略。 作为该策略的一部分，IT 管理员还可指定何时加密内容。

  1. **Intune 如何加密数据？** 请参阅 [Android 应用保护策略设置](../deploy-use/android-mam-policy-settings.md)和 [iOS 应用保护策略设置](../deploy-use/ios-mam-policy-settings.md)，获取有关加密应用保护策略设置的详细信息。

  2. **对哪些内容进行加密？** 根据 IT 管理员的应用保护策略，仅对标记为“公司”的数据进行加密。 数据源于业务位置时会被视为“公司”数据。 对于 Office 应用，Intune 将以下数据视为业务位置：电子邮件 (Exchange) 或云存储（包含 OneDrive for Business 帐户的 OneDrive 应用）。 对于由 Intune 应用包装工具启用的业务线应用，所有应用数据都会被视为“公司”数据。

**Intune 如何远程擦除数据？** Intune 能够使用 3 种不同方式擦除应用数据：完全设备擦除、MDM 选择性擦除和 MAM 选择性擦除。 有关 MDM 远程擦除的详细信息，请参阅[使用 Microsoft Intune 的完全擦除或选择性擦除帮助保护数据](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)。 有关使用 MAM 的选择性擦除的详细信息，请参阅[使用 Microsoft Intune 擦除托管公司应用数据](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

  1. **什么是完全擦除？** [完全擦除](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)会通过将设备还原到其出厂默认设置，从**设备**中删除所有用户数据和设置。 设备从 Intune 删除。
  >[!NOTE]
  > 完全擦除只有在注册了 Intune 移动设备管理 (MDM) 的设备上才能实现。

  2. **什么是 MDM 选择性擦除？** 请参阅[使用 Microsoft Intune 的完全擦除或选择性擦除帮助保护数据](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)，以了解选择性擦除。

  3. **什么是 MAM 选择性擦除？** MAM 选择性擦除仅删除应用中的公司应用数据。 使用 Intune Azure 门户启动该请求。 若要了解如何启动擦除请求，请参阅[使用 Microsoft Intune 擦除托管公司应用数据](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

  4. **MAM 选择性擦除多久发生一次？** 如果用户在启用了选择性擦除的情况下使用应用，那么 Intune App SDK 会每 30 分钟检查一次来自 Intune MAM 服务的选择性擦除请求。 它还会在用户第一次启动应用并使用其工作或学校帐户登录时检查选择性擦除。

**为什么本地服务不适用于 Intune 保护的应用？** Intune 应用保护要求用户的身份在应用程序与 Intune App SDK 之间保持一致。 保证此种一致的唯一方法是通过新式身份验证。 在某些情况下应用可能适用于本地配置，但它们既不一致也无法得到保证。

**是否有一种安全的方法可以从管理的应用中打开 Web 链接？** 可以！ IT 管理员可以为 [Intune Managed Browser 应用](../deploy-use/manage-internet-access-using-managed-browser-policies.md)（一种由 Microsoft Intune 开发的可使用 Intune 轻松管理的 Web 浏览器）部署和设置应用保护策略。 IT 管理员可以要求 Intune 启用的应用中所有 Web 链接均使用 Managed Browser 应用打开。


## <a name="app-experience-on-android"></a>Android 上的应用体验

**为什么在 Android 设备上使用 Intune 应用保护需要公司门户应用？** 应用保护的许多功能都内置于公司门户应用中。 虽然始终需要公司门户应用，但设备注册是不必要的。 对于 MAM-WE，最终用户只需在设备上安装有公司门户应用即可。

## <a name="app-experience-on-ios"></a>iOS 上的应用体验

**即使将数据传输策略设置为“仅管理的应用”或“无应用”，我也可以使用 iOS 共享扩展在非管理应用中打开工作或学校数据。这样不会泄漏数据吗？** 在不管理设备的情况下，Intune 应用保护策略不能控制 iOS 共享扩展。 因此，Intune _**会在对“公司”数据进行应用外共享之前对其进行加密**_。 可通过尝试在管理的应用外打开“公司”文件对此进行验证。 该文件应该已加密，且无法在托管应用外打开。

### <a name="see-also"></a>另请参阅
- [Microsoft Intune 中的 Android 移动应用管理策略设置](../deploy-use/android-mam-policy-settings.md)
- [iOS 移动应用管理策略设置](../deploy-use/ios-mam-policy-settings.md)
- [验证移动应用管理设置](../deploy-use/validate-mobile-application-management.md)
- [准备好使用 Microsoft Intune 配置移动应用管理策略](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [如何获取对 Microsoft Intune 的支持](../troubleshoot/how-to-get-support-for-microsoft-intune.md)

