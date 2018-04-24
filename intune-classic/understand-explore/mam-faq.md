---
title: 有关 MAM 和应用保护的常见问题
description: 本文提供了针对 Intune 移动应用程序管理 (MAM) 和 Intune 应用保护的一些常见问题解答。
keywords: ''
author: oydang
ms.author: oydang
manager: dougeby
ms.date: 01/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 816a235136d91f2691e6be442036515544c004b2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>有关 MAM 和应用保护的常见问题

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本文提供了针对 Intune 移动应用程序管理 (MAM) 和 Intune 应用保护的一些常见问题解答。

## <a name="mam-basics"></a>MAM 基础知识


**什么是 MAM？** [Intune 移动应用程序管理](/intune/app-lifecycle)指的是 Intune 管理功能套件，通过它能够为用户发布、推送、配置、保护、监视和更新移动应用。

**使用 MAM 应用保护有什么好处？** MAM 可保护应用程序内组织的数据。 通过 MAM-WE，可以在几乎任何设备上管理包含敏感数据的工作或学校相关应用，包括自带设备办公 (BYOD) 场景下的个人设备。 许多生产型应用，例如 Microsoft Office 应用，都可以通过 Intune MAM 进行管理。 请参阅可供公众使用的 [Intune 托管应用](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的官方列表。

**MAM 支持哪些设备配置？** Intune MAM 支持两种配置：
  1. **Intune MDM + MAM**：这是首次启动 MAM 时它所支持的第一个配置。 IT 管理员仅可在已进行 Intune 移动设备管理 (MDM) 注册的设备上使用 MAM 和应用保护策略管理应用。 若要使用 MDM + MAM 管理应用，客户应使用 https://manage.microsoft.com 上的 Intune 独立控制台。

  2. **无需设备注册的 MAM**：无需设备注册的 MAM 或 MAM-WE 使 IT 管理员可以在未进行 Intune MDM 注册的设备上使用 MAM 和应用保护策略管理应用。 这意味着可以在进行了第三方 EMM 提供程序注册的设备上通过 Intune 管理应用。 若要使用 MAM-WE 管理应用，客户应使用 http://portal.azure.com 上的 Azure 门户中的 Intune 控制台。


## <a name="app-protection-policies"></a>应用保护策略

**什么是应用保护策略？** 应用保护策略是可确保组织数据在管理的应用中保持安全或受到控制的规则。 策略可以是在用户尝试访问或移动“公司”数据时强制执行的规则，或在用户位于应用内时受到禁止或监视的一组操作。

**应用保护策略的示例有哪些？** 请参阅 [Android 应用保护策略设置](../deploy-use/android-mam-policy-settings.md)和 [iOS 应用保护策略设置](../deploy-use/ios-mam-policy-settings.md)，获取有关每种应用保护策略设置的详细信息。

## <a name="apps-you-can-manage-with-app-protection-policies"></a>可使用应用保护策略进行管理的应用

**可通过应用保护策略管理哪些应用？** 已通过 [Intune App SDK](/intune/app-sdk) 启用的或通过 [Intune 应用包装工具](/intune/apps-prepare-mobile-application-management)包装的任何应用都可使用 Intune 应用保护策略进行管理。 请参阅可供公众使用的 [Intune 托管应用](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的官方列表。

**在 Intune 托管应用上使用应用保护策略的基本要求有哪些？**
  1. 最终用户必须具有 Azure Active Directory (AAD) 帐户。 请参阅[添加用户并授予对 Intune 的管理权限](/intune/users-permissions-add)，了解如何在 Azure Active Directory 中创建 Intune 用户。

  2. 最终用户必须具有分配给其 Azure Active Directory 帐户的 Microsoft Intune 许可证。 请参阅[管理 Intune 许可证](/intune/licenses-assign)，了解如何将 Intune 许可证分配给最终用户。

  3. 最终用户必须属于应用保护策略所面向的一个安全组。 同一应用保护策略必须面向正在使用的特定应用。 可以在 [Azure 门户](http://portal.azure.com)的 Intune 控制台中创建和部署应用保护策略。 当前可以在 [Office 门户](http://portal.office.com)中创建安全组。

  4. 最终用户必须使用其 AAD 帐户登录到应用。

**使用 [Outlook 移动应用](https://www.microsoft.com/outlook-com/mobile/)有什么其他要求？**

1. 最终用户必须将 Outlook 移动应用安装到其设备上。

2. 最终用户必须具有链接到其 Azure Active Directory 帐户的 [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) 邮箱和许可证。

   >[!NOTE]
   > Outlook 移动应用当前仅支持 Microsoft Exchange Online，不支持 Exchange 内部部署或 Office 365 Dedicated 中的 Exchange。

**使用 [Word、Excel 和 PowerPoint](https://products.office.com/business/office) 应用有什么其他要求？**

1. 最终用户必须具有链接到其 Azure Active Directory 帐户的 [Office 365 商业版或企业版](https://products.office.com/business/compare-more-office-365-for-business-plans)许可证。 订阅必须包括移动设备上的 Office 应用，可以包括 [OneDrive for Business](https://onedrive.live.com/about/business/) 云存储帐户。 遵循这些[说明](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)可在 [Office 门户](http://portal.office.com)中分配 Office 365 许可证。

2. 最终用户必须具有使用粒度另存为功能进行配置的托管的位置（该功能位于“阻止另存为”应用程序保护策略设置下）。 例如，如果托管的位置为 OneDrive，则应在最终用户的 Word、Excel 或 PowerPoint 应用中对 [OneDrive](https://onedrive.live.com/about/) 应用进行配置。

3. 如果托管的位置为 OneDrive，则部署到最终用户的应用保护策略必须面向该应用。

   >[!NOTE]
   > Office 移动应用当前仅支持 SharePoint Online，不支持本地 SharePoint。

**为什么 Office 需要托管的位置（例如 OneDrive）？** Intune 会将应用中的所有数据标记为“公司”或“个人”。 数据源于业务位置时会被视为“公司”数据。 对于 Office 应用，Intune 将以下数据视为业务位置：电子邮件 (Exchange) 或云存储（包含 OneDrive for Business 帐户的 OneDrive 应用）。

**使用 Skype for Business 有什么其他要求？** 请参阅 [Skype for Business](https://products.office.com/skype-for-business/it-pros) 许可证要求。
  >[!NOTE]
  > Skype for Business 移动应用当前仅支持 Skype for Business Online。

## <a name="app-protection-features"></a>应用保护功能

**什么是多身份支持？** 多身份支持可使 Intune App SDK 仅将应用保护策略应用于已登录到应用的工作或学校帐户。 如果个人帐户登录到应用，数据将保持不变。

**多身份支持的用途是什么？** 多身份支持使得能够公开发布具有“公司”和消费者受众的应用（如 Office 应用），同时让“公司”帐户具有 Intune 应用保护功能。

**Outlook 和多身份呢？** 由于 Outlook 具有个人和“公司”电子邮件的混合电子邮件视图，Outlook 应用会在启动时提示输入 Intune PIN。

**Intune 应用 PIN 是什么？** 个人标识号 (PIN) 是一种密码，用于验证是否是正确的用户在应用程序中访问组织的数据。

  1. **何时提示用户输入其 PIN？** 仅当用户要访问“公司”数据时，Intune 才会提示输入用户的应用 PIN。 在诸如 Word/Excel/PowerPoint 等多身份应用中，当用户尝试打开“公司”文档或文件时，会向他们提示输入 PIN。 在单身份应用中，例如使用 Intune 应用包装工具启用的业务线应用，会在启动时提示输入 PIN，因为 Intune App SDK 知道用户在应用中的体验始终是针对“公司”的。

2. **系统多久提示一次用户输入 Intune PIN？**
IT 管理员可在 Intune 管理控制台中定义 Intune 应用保护策略设置“以下时间过后重新检查访问要求(分钟)”。 此设置指定在设备上检测访问要求，并再次显示应用程序 PIN 屏幕之前的时长。 但是，请注意以下关于 PIN 的重要详细信息，它们会影响用户收到提示的频率： 

* **为了提高可用性，将在同一发布者的多个应用之间共享 PIN：**在 iOS 上，同一发布者的所有应用共享一个应用 PIN。 在 Android 上，所有应用共享一个应用 PIN。
* **与 PIN 关联的计时器的滚动特性：**输入 PIN 以访问应用（应用 A）后，该应用会离开设备主屏幕（主输入焦点），并且该 PIN 的 PIN 计时器会进行重置。 共享此 PIN 的任何应用（应用 B）均不会提示用户输入 PIN，因为计时器已重置。 再次达到“以下时间过后重新检查访问要求(分钟)”值后，就会再次显示该提示。 

>[!NOTE] 
> 为了更频繁地验证用户的访问要求（即 PIN 提示），尤其是针对常用应用的访问，建议缩小“以下时间过后重新检查访问要求(分钟)”值。 

  3. **PIN 安全吗？** PIN 仅允许正确的用户在应用中访问其组织数据。 因此，最终用户必须使用其工作或学校帐户登录，然后才能设置或重置其 Intune 应用 PIN。 这种身份验证通过安全的令牌交换由 Azure Active Directory 执行，且不对 Intune App SDK 公开。 从安全性的角度来看，保护工作或学校数据的最佳方法便是对其进行加密。 加密与应用 PIN 无关，它本身是一项应用保护策略。

  4. **Intune 如何保护 PIN 免遭暴力破解攻击？** 作为应用 PIN 策略的一部分，IT 管理员可以设置在锁定应用之前用户可尝试验证其 PIN 的最大次数。 达到最大尝试次数后，Intune App SDK 可以擦除应用中的“公司”数据。
  
  5. **为什么必须在同一发布者的应用上设置 PIN 两次？**
目前，MAM（在 iOS 上）允许使用包含字母数字和特殊字符（称为“密码”）的应用级 PIN，它需要有应用（即， WXP、Outlook、Managed Browser、Yammer）以集成 Intune APP SDK for iOS。 如果没有应用程序的参与，将无法对目标应用程序正确执行密码设置。 这是在 Intune SDK for iOS 版本 7.1.12 中发布的功能 。 <br> 为了支持此功能，并确保与旧版 Intune SDK for iOS 的向后兼容性，版本 7.1.12 及更高版本中的所有 PIN（数字或密码）都与旧版 SDK 中的数字 PIN 分开处理。 因此，如果设备中同一发布者的应用使用了版本低于和高于 7.1.12 的 Intune SDK for iOS，就需要设置两个 PIN。 <br><br> 也就是说，这两个 PIN（对于每个应用）不以任何方式相关，即必须遵守应用到应用的应用保护策略。 这样，只有当应用 A 和 B 都应用了相同的策略（对于 PIN），用户才需要设置相同的 PIN 两次。 <br><br> 此行为只针对于使用 Intune 移动应用管理 (MAM) 启用的 iOS 应用上的 PIN。 日后，随着应用采用更高版本的 Intune SDK for iOS，必须在同一发布者的应用上设置 PIN 两次就不再是个问题了。 有关示例，请参阅下面的注意事项。

>[!NOTE]
> 例如，如果应用 A 使用版本低于 7.1.12 的 SDK 生成，同一发布者的应用 B 使用版本不低于 7.1.12 的 SDK 生成，且这两个应用都安装在 iOS 设备上，那么最终用户需要为应用 A 和 B 单独设置 PIN。 <br> 如果在此设备上安装了包含 SDK 版本 7.1.9 的应用 C，那么它与应用 A 共用同一 PIN。 <br> 使用 SDK 版本 7.1.14 生成的应用 D 与应用 B 共用同一 PIN。 <br> 如果仅在设备上安装了应用 A 和 C，需要设置一个 PIN。 如果仅在设备上安装了应用 B 和 D，情况也是如此，即需要设置一个 PIN。

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

**是否有一种安全的方法可以从管理的应用中打开 Web 链接？** 可以！ IT 管理员可以为 [Intune Managed Browser 应用](../deploy-use/manage-internet-access-using-managed-browser-policies.md)（一种由 Microsoft Intune 开发的可使用 Intune 轻松管理的 Web 浏览器）部署和设置应用保护策略。 IT 管理员可以要求 Intune 托管应用中的所有 Web 链接均使用 Managed Browser 应用打开。


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
