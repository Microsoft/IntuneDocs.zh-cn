---
title: "通过 Microsoft Intune 启用 BYOD"
description: 
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: vlpetros
ms.suite: ems
ms.openlocfilehash: 880b83a63eefe13a96ab8838c7092c185aa32cd0
ms.sourcegitcommit: ce363409d1206e4a3d669709863ccc9eb22b7d5f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2017
---
# <a name="enable-byod-with-intune"></a>通过 Intune 实现 BYOD

本主题提供用于设置 Intune 的高级别工作流，以便为组织启用自带设备办公 (BYOD) 解决方案。 该工作流将任务分为 3 个流程，并提供相应操作说明主题的链接。

工作流分为以下 3 个流程。 可根据组织的需求自定义每个流程的各个方面。

-   [注册设备和检查符合性](#enroll-devices-and-check-for-compliance)介绍了如何让用户将个人设备注册到 Intune 以进行管理。 Intune 可管理 iOS、macOS、Android 和 Windows 设备。 本部分还介绍如何向设备部署策略，并确保其满足基本的安全要求。

- [提供对公司资源的访问](#provide-access-to-company-resources)演示了 IT 如何使用户轻松安全地访问公司资源。 为此，可将访问配置文件部署到托管设备。 本部分还介绍如何使用 Intune 管理批量采购的应用部署。

-   [保护公司数据](#protect-company-data)有助于了解如何提供对公司资源的条件访问、防止数据丢失，以及当设备上的公司应用和数据不再需要或丢失被盗时如何将其删除。

[![通过 Microsoft Intune 启用 BYOD 的高级别工作流图示](./media/workflow-diagram-for-byod.png)](./media/workflow-diagram-for-byod.png)

<!--- > <sup>You can download this infographic at https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup> --->

## <a name="before-you-begin"></a>在开始之前
需要先准备 Intune 服务本身，用户才能注册设备。 为此，请[向用户分配许可证](licenses-assign.md)并[设置移动设备管理机构](mdm-authority-set.md)。

执行这些操作时，还应该[自定义公司门户](company-portal-customize.md)。 添加公司品牌，并向用户提供支持信息。 这将为用户创造值得信赖的注册和支持体验。

## <a name="enroll-devices-and-check-for-compliance"></a>注册设备和检查符合性

Intune 服务准备就绪后，需要满足要管理的不同设备类型的各种注册需求。 这时，注册设备进行管理的过程就非常直接了，但注册过程因设备类型而略有不同。

-   iOS 和 Mac 设备 - 注册 iPad、iPhone 或 MacOS 设备需要[获取 Apple Push Notification 服务 (APN) 证书](apple-mdm-push-certificate-get.md)。 将 APN 证书上传到 Intune 后，用户可使用公司门户应用[注册 iOS 设备](/intune-user-help/enroll-your-device-in-intune-ios)，并使用公司门户网站[注册 MacOS 设备](/intune-user-help/enroll-your-device-in-intune-macos)。

-   Android 设备 - 将 Intune 服务注册到 Android 设备无需任何准备工作。 用户可使用 Google Play 提供的公司门户应用[将 Android 设备注册](/intune-user-help/enroll-your-device-in-intune-android.md)到管理。

-   Windows Phone 和电脑 - 若要更轻松地注册 Windows 设备，应[设置注册服务器的 DNS 别名](windows-enroll.md#enable-windows-enrollment-without-azure-ad-premium)。 另外，用户可以通过添加工作或学校帐户[注册 Windows 设备](/intune-user-help/enroll-your-w10-phone-or-w10-pc-windows)。

  - 如果拥有 Azure AD Premium，则用户可通过[启用自动注册](windows-enroll.md)更轻松地注册 Windows 设备。 用户添加工作或学校帐户来注册自己的个人设备时，此功能将自动向 Intune 注册设备。 它还适用于加入组织 Azure AD 的公司拥有的设备。


### <a name="make-sure-that-managed-devices-meet-basic-security-requirements"></a>确保托管设备符合基本安全要求

用户将设备注册到管理后，IT 需要确保用于访问公司应用和数据的设备符合基本安全要求。 这些规则可能包括使用 PIN 访问设备和加密存储在设备上的数据。 一组这样的规则就称为[合规性策略](device-compliance.md)。

向用户[部署符合性策略](device-compliance-get-started.md)时，Intune 将检查由它管理的所有用户设备，查看其是否满足定义为 BYOD 策略一部分的基本安全要求。 对设备进行策略符合性评估后，系统会将其状态报告回 Intune。 在某些情况下，系统可能要求用户修复设置，例如 PIN 或设备加密。 其他情况下，公司门户应用仅会通知用户任何与策略不符的设置。

## <a name="provide-access-to-company-resources"></a>提供对公司资源的访问

大多数员工希望通过其移动设备做的第一件事是访问公司电子邮件和文档。 他们希望设置步骤简单，不需要询问支持人员。 使用 Intune，可轻松为预安装在移动设备上的本机电子邮件应用[创建和部署电子邮件设置](conditional-access-intune-common-ways-use.md)。
<!--- this was old link: (https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune). check with Andre--->

> [!NOTE]
> Intune 支持 Google Play 商店中的 Gmail 和 Nine Work 电子邮件应用使用 Android for Work 电子邮件配置文件配置。

用户在公司外办公时，Intune 还可用来控制和保护对本地公司数据的访问。 结合使用 Intune [Wi-Fi](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune)、[VPN](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#create-a-vpn-profile) 和电子邮件配置文件，用户无论身在何处，都能获得完成工作所需的文件和资源的访问权限。 使用 Azure Active Directory 应用程序代理和条件性访问，也可实现对公司 Web 应用程序和本地托管服务的安全访问和保护。

### <a name="manage-volume-purchased-apps"></a>管理批量采购的应用
使用 Intune，轻松完成如下操作：
* 从任意 App Store 导入批量许可证信息
* 跟踪已使用的许可证数目
* 防止用户安装的应用副本数超过你所拥有的数目
* [向托管设备传递应用商店应用](apps-deploy.md)
* 使用公司门户网站将应用定位到非托管设备

使用 Intune，还可以管理和部署从 iOS App Store 和适用于企业的 Windows 应用商店批量购买的应用。 这有助于降低跟踪批量购买应用的管理成本。

> [!TIP]
> 可以[使用 Azure AD Connect 配置单一登录 (SSO)](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。 通过 SSO，用户可凭借在本地使用的域用户名和密码来登录应用。 此外，还可使用 Azure Active Directory 应用程序代理来[提供对本地托管 Web 应用的基于 Internet 的访问](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)。

-   [管理批量采购的适用于 iOS 设备的应用](vpp-apps-ios.md)。 通过 [Apple Volume Purchase Program 企业版](http://www.apple.com/business/vpp/)购买多个 iOS 应用许可证。 需要在 Apple 网站设置一个 Apple VPP 帐户，并将 Apple VPP 令牌上传到 Intune。 然后，可将批量购买信息与 Intune 同步，并追踪批量购买应用的使用情况。

-   [管理从适用于企业的 Windows 应用商店购买的应用](windows-store-for-business.md)。 可在[适用于企业的 Windows 应用商店](https://www.microsoft.com/business-store)中为组织查找和购买应用（单个或批量）。 通过将此应用商店连接到 Intune，可在 Intune 门户中管理批量购买的应用。

## <a name="protect-company-data"></a>保护公司数据

Intune 通过多个技术层保护公司数据。 在标识层上，条件访问可保护对服务的访问。 条件访问仅允许托管设备和合规设备访问公司资源。 在客户端应用程序层上，移动应用管理 (MAM) 可防止数据丢失。  应用保护策略可防止数据移动到不受保护的应用或存储位置。 借助这些策略，还可在设备丢失或被盗时擦除公司数据。

### <a name="enforce-conditional-access-to-company-resources"></a>强制执行对公司资源的条件访问

可结合使用符合性策略与[条件访问策略](device-compliance.md)，检查设备是否符合 BYOD 策略所需的基本安全要求。 如果设备不符合要求，系统将强制执行规则并拒绝其访问，直至设备符合策略要求。 这可确保仅托管设备和合规设备才能从 Exchange（[Exchange 内部部署](exchange-connector-install.md)或 [Exchange Online](conditional-access-exchange-create.md)）、SharePoint Online、Skype for Business Online 等服务访问公司数据。
<!---first link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)
third link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune). check with Andre--->

> [!IMPORTANT]
> 如果用于验证合规性的合规性策略未准备就绪，则无法使用条件访问策略。

### <a name="prevent-data-loss-of-company-data-with-application-protection-policies"></a>使用应用程序保护策略防止公司数据丢失

利用 Intune 应用程序保护策略，可选择访问数据的方式（无论设备注册与否）。 这种多功能性可以保护公司数据，即使用户没有在 Intune 中注册其设备，也能安全地访问公司数据。

可使用 [Intune 应用保护策略](app-protection-policies.md)帮助保护由用户的 iOS 和 Android 设备访问的公司数据。 使用这些应用级策略时，即使设备本身不受 Intune 管理，你也可以控制员工使用和共享公司数据的方式

使用 [Windows 信息保护 (WIP) 策略](app-protection-policies-configure-windows-10.md)对托管的 Windows 10 设备可执行相同操作。 这些策略不会影响员工体验。 无需更改网络环境或其他应用。

### <a name="wipe-company-data-while-leaving-personal-data-intact"></a>在保留个人数据完整的同时，擦除公司数据

如果不再需要某设备用于办公、设备改变用途或丢失，则需要从此设备删除公司的应用和数据。 为此，可使用 Intune 的选择性擦除和完全擦除功能。 用户也可从 Intune 公司门户远程擦除注册到 Intune 的自有设备。

[完全擦除](devices-wipe.md)将设备还原为出厂默认设置，同时删除用户数据和设置。 [选择性擦除](devices-wipe.md#selective-wipe)仅删除设备上的公司数据，但会完整保留用户的个人数据。

启动后，设备会立即开始选择性擦除流程，从管理中删除数据。 流程完成后，便已删除所有公司数据，设备名称也从 Intune 管理员控制台中删除。 设备管理生命周期结束。
