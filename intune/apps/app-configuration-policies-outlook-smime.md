---
title: 在 Microsoft Intune 中为 Outlook for iOS 配置 S/MIME
description: 了解如何在 Microsoft Intune 中为 Outlook for iOS 配置 S/MIME。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 348d1fe2fd236a2af11f7e58dc11530a5ce397bc
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564192"
---
# <a name="configure-smime-with-outlook-for-ios"></a>为 Outlook for iOS 配置 S/MIME

安全/多用途 Internet 邮件扩展 (S/MIME) 可为 Exchange ActiveSync (EAS) 帐户中往来发送的电子邮件提供额外的安全层。 [Microsoft Outlook](https://aka.ms/omsmime) 可以利用 S/MIME 来允许用户对待发邮件和附件进行加密，从而确保只有预期的收件人可以在使用 Office 365 帐户时读取和访问邮件内容。 用户还可以对邮件进行数字签名，从而允许收件人验证发件人的身份，并确认该邮件未被篡改。 利用证书可以实现此功能。 有关详细信息，请参阅[了解 S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN)。

> [!NOTE]
> 本主题介绍了如何通过 [Microsoft 终结点管理器](https://go.microsoft.com/fwlink/?linkid=2109431)来部署受信任的根证书。 Microsoft 终结点管理器是用于管理所有终结点的单个集成式终结点管理平台。 此 Microsoft 终结点管理器管理中心集成了 ConfigMgr 和 Microsoft Intune。

## <a name="about-message-encryption"></a>关于消息加密
如果用户具有加密证书的公共部分，则用户可以将加密的邮件发送给其组织内外的人员。 与加密证书关联的私钥应始终由加密邮件的收件人进行保护。 加密证书的私钥允许收件人对邮件进行解密。

加密邮件只能由具有与加密邮件的证书相对应证书的收件人读取。 如果尝试将加密邮件发送给其加密证书不可用的收件人，则该应用将在发送电子邮件之前提示你删除这些收件人。

## <a name="about-digital-signatures"></a>关于数字签名
进行数字签名的邮件可使收件人确保邮件未被篡改，并且发件人身份可信。 如果收件人使用的电子邮件客户端支持 S/MIME，则只能验证数字签名。

## <a name="prerequisites"></a>必备条件
- Outlook for iOS 仅支持 Office 365 帐户上的 S/MIME。
- 必须为 Office 365 配置 S/MIME。 有关详细信息，请参阅[如何在 Office 365中配置 S/MIME](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516)。
- 你必须具有可颁发证书的证书颁发机构，其中该证书可用于签名和加密。
- 通过终结点管理器部署受信任的根证书。 有关详细信息，请参阅[创建受信任的证书配置文件](~/protect/certificates-configure.md#create-trusted-certificate-profiles)。
- 加密证书必须导入到终结点管理器中。 有关详细信息，请参阅[在 Intune 中配置和使用导入的 PKCS 证书](~/protect/certificates-imported-pfx-configure.md)。
- 安装和配置 Microsoft Intune 的 PFX 连接器。 有关详细信息，请参阅[下载、安装和配置 Microsoft Intune 的 PFX 证书连接器](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune)。
- 设备必须注册 MDM 才能从终结点管理器自动接收受信任的根和 S/MIME 证书。

> [!IMPORTANT]
> 必须下载并安装更新后的 PFX 连接器（版本 6.1911.11.0 或更高版本），Microsoft Intune 才能将 S/MIME 加密证书用于 Outlook for iOS。

## <a name="smime-support-in-outlook-for-ios"></a>Outlook for iOS 中的 S/MIME 支持
Outlook for iOS 支持使用证书对邮件进行 S/MIME 签名和加密。 许多客户具有不同的签名证书和加密证书，而不是具有同时支持签名和加密的单个证书。 签名证书通常在单个用户的已注册设备中是唯一的，而加密证书则在单个用户的已注册设备之间共享。 通常，用户会使用 S/MIME 多年，在续订证书时，将使用不同的加密证书。 加密证书历史记录（包括其私钥）必须存在于用户的设备上，以便可以读取过去可能已使用任何这些证书进行加密的电子邮件。 还可以具有支持签名和加密的单个证书。

Outlook for iOS 支持通过两种方式将证书传递到设备，以便可以将证书用于 S/MIME：

- “用户”  可以通过电子邮件将 S/MIME 证书发送给自己，并在其移动设备上通过 Outlook for iOS 中的附件进行安装。
- “管理员”  可以将来自任何证书颁发机构的加密证书历史记录导入到终结点管理器。 然后，终结点管理器会自动将这些证书传递给用户注册的任何设备。 通常，简单证书注册协议 (SCEP) 用于签名证书。 使用 SCEP，将生成私钥并将其存储在已注册的设备上，并将唯一证书传递给用户注册的每个设备，该证书可用于不可否认性。 管理员将其用户的加密证书历史记录导入到终结点管理器，后者随后将所有用户的加密证书传递给其注册的任何设备。 最后，终结点管理器为需要 NIST 800-157 标准支持的客户提供派生凭据支持。 在 iOS 上，公司门户用于从 Intune 检索签名和加密证书。

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>在终结点管理器中配置 Outlook for iOS S/MIME
若要在终结点管理器中配置 Outlook for iOS S/MIME（包括自动传递 Outlook for iOS 可以使用的 S/MIME 证书），请执行以下步骤：

### <a name="add-the-microsoft-outlook-app"></a>添加 Microsoft Outlook 应用
1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 将 Microsoft Outlook for iOS 应用从应用商店添加到终结点管理器，或从 Apple Volume Purchase Program 同步 Outlook for iOS。 有关详细信息，请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](~/apps/store-apps-ios.md)或[如何使用 Microsoft Intune 管理通过 Apple Volume Purchase Program 购买的 iOS 和 macOS 应用](~/apps/vpp-apps-ios.md)。

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>创建 Outlook for iOS S/MIME 配置策略

以下步骤允许你在终结点管理器中创建和配置 Outlook for iOS S/MIME 策略。 这些设置提供了签名和加密证书的自动传递。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并依次选择“应用”   > “应用配置策略”   > “添加”  。<br>
将显示“添加配置策略”  窗格。
2. 输入配置策略的“名称”  和“说明”  。
3. 对于“设备注册类型”  ，选择“托管设备”  。
4. 选择“iOS/iPadOS”  作为“平台”  。
5. 单击“选择所需应用”  以查找并关联先前添加的 Microsoft Outlook for iOS 应用。 
6. 单击“配置设置”  以添加配置设置。 
    - 选择“配置设置格式”  旁边的“使用配置设计器”  并接受默认设置。 有关详细信息，请参阅 [Microsoft Outlook 配置设置](~/apps/app-configuration-policies-outlook.md)。
7. 单击“S/MIME”  以显示“Outlook S/MIME 设置”  。

    ![Outlook for iOS S/MIME 设置的屏幕截图](./media/app-configuration-policies-outlook-smime/app-configuration-policies-outlook-smime-01.png)

8. 将“启用 S/MIME”  设置为“是”  。
9. 将“从 Intune 部署 S/MIME 证书”  设置为“是”  。
10. 在“证书配置文件类型”  旁边的“签名证书”  下，选择以下选项之一：
    - **SCEP** – 创建一个证书，该证书对于可由 Microsoft Outlook 用于签名的设备和用户是唯一的。 有关相关信息，请参阅[配置基础结构以支持在 Intune 中使用 SCEP](~/protect/certificates-scep-configure.md) 和[创建 SCEP 证书配置文件](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile)。 
    - **PKCS 导入的证书** – 使用用户独有的证书，但可以在设备之间共享，并由管理员代表用户导入到终结点管理器。 证书将传递给用户注册的任何设备。 终结点管理器将自动选择支持签名的已导入证书，以便将其传递到与已注册用户相对应的设备。
    - **派生凭据** – 使用设备上已有的可用于签名的证书。 必须使用 Intune 中的派生凭据流在设备上检索该证书。
11. 在“证书配置文件类型”  旁边的“加密证书”  下，选择以下选项之一：
    - **PKCS 导入的证书** – 通过管理员将任何已导入到终结点管理器的加密证书传递给任何设备，用户注册的终结点管理器将自动选择导入的证书或支持加密的证书，以便将其传递到与已注册用户相对应的设备。
    - **派生凭据** – 使用设备上已有的可用于签名的证书。 必须使用 Intune 中的派生凭据流在设备上检索该证书。
12. 在“最终用户通知”  旁边，选择“公司门户”  或“电子邮件”  为 Outlook for iOS 检索 S/MIME 证书，以便选择通知最终用户。

    在 iOS 上，用户必须使用公司门户应用检索其 S/MIME 证书。 终结点管理器将通知用户他们需要启动公司门户以通过公司门户的“通知”部分、推送通知和/或电子邮件检索其 S/MIME 证书。 单击其中一个通知会将用户转到登陆页，以告知他们检索证书的进度。 检索证书后，用户可以使用 Microsoft Outlook for iOS 中的 S/MIME 对电子邮件进行签名和加密。
    
    最终用户通知包括以下选项：
       - **公司门户** – 如果选择了此选项，用户将在其设备上收到推送通知，这会将其转到公司门户的登录页（其中将检索 S/MIME 证书）。
        - **电子邮件** – 向最终用户发送一封电子邮件，告知他们需要启动公司门户才能检索其 S/MIME 证书。 如果用户单击电子邮件中的链接时位于其已注册的 iOS 设备上，则会将用户重定向到公司门户以检索其证书。
    
13. 选择“分配”  以将应用配置策略分配到 Azure AD 组。 有关详细信息，请参阅[使用 Microsoft Intune 将应用分配到组](~/apps/apps-deploy.md)。

## <a name="next-steps"></a>后续步骤

- 有关详细信息，请参阅 [Microsoft Intune 的应用配置策略](app-configuration-policies-overview.md)。
