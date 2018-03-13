---
title: "向 Intune 添加并分配 MTD 应用"
titleSuffix: Azure portal
description: "使用 Azure 门户中 Intune 添加 MTD 应用、Microsoft Authenticator 应用和 iOS 配置策略"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7afe03c635b63053ef0cc0f622bc9324f31ec68b
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>使用 Intune 添加和分配移动威胁防御 (MTD) 应用

> [!NOTE] 
> 本主题适用于所有移动威胁防御合作伙伴。

可以使用 Intune 来添加和部署 MTD 应用，以便最终用户可以在其移动设备中确定某个威胁时接收通知，并接收指导来解除威胁。

对于 iOS 设备，需要 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)，这样用户便可让 Azure AD 检查自己的标识。 此外，需要 iOS 应用配置策略，该策略指示要与 Intune 配合使用的 MTD iOS 应用。

> [!TIP]
> Intune 公司门户在 Android 设备上以中转站的方式工作，以便用户能够让 Azure AD 检查自己的标识。

## <a name="before-you-begin"></a>在开始之前

-   需要在 [Azure 门户](https://portal.azure.com/)中完成以下步骤。

-   请务必熟悉以下过程：

    -   [将应用添加到 Intune](apps-add.md)。

    -   [将 iOS 应用配置策略添加到 Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

    -   [使用 Intune 分配应用](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [添加 iOS 应用配置策略](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-add-apps"></a>若要添加应用

### <a name="all-mtd-partners"></a>所有 MTD 合作伙伴

#### <a name="microsoft-authenticator-app-for-ios"></a>适用于 iOS 的 Microsoft Authenticator 应用

- 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 使用“配置应用信息”部分步骤 5 中的 [Microsoft Authenticator 应用商店 URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)。

### <a name="lookout"></a>Lookout

#### <a name="android"></a>Android
- 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在步骤 7 中使用此 [Lookout for Work Google 应用商店 URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise)。

#### <a name="ios"></a>iOS

- 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 使用“配置应用信息”部分步骤 5 中的 [Lookout for Work iOS 应用商店 URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8)。

#### <a name="lookout-for-work-app-outside-the-apple-store"></a>Apple 应用商店之外的 Lookout for Work 应用

需要对 Lookout for Work iOS 应用进行重新签名。 Lookout 会在 iOS 应用商店之外分发其 Lookout for Work iOS 应用。 分发应用之前，必须使用 iOS 企业开发者证书对应用重新签名。

有关对 Lookout for Work iOS 应用重新签名的详细说明，请参阅 Lookout 网站上的 [Lookout for Work iOS 应用重新签名过程](https://personal.support.lookout.com/hc/articles/114094038714)。

##### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>为 Lookout for Work iOS 应用启用 Azure AD 身份验证

通过执行以下操作为 iOS 用户启用 Azure Active Directory 身份验证：

1. 转到 [Azure 门户](https://portal.azure.com)，使用自己的凭据登录，然后导航到应用程序页。
  
2. 添加 **Lookout for Work iOS 应用**作为**本机客户端应用程序**。

3. 将 **com.lookout.enterprise.yourcompanyname** 替换为对 IPA 签名时选择的客户捆绑 ID。

4.  添加其他重定向 URI：**&lt;companyportal://code/>**，后跟原始重定向 URI 的 URL 编码形式版本。

5.  将**委托的权限**添加到应用。

    > [!NOTE] 
    > 有关详细信息，请参阅[使用 Azure AD 配置本机客户端应用程序](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)。

##### <a name="add-the-lookout-for-work-ipa-file"></a>添加 Lookout for Work ipa 文件

- 按照[使用 Intune 添加 iOS LOB 应用](lob-apps-ios.md)主题中所述，上传重新签名的 .ipa 文件。 还需将最低操作系统版本设为 iOS 8.0 或更高版本。

### <a name="skycure"></a>Skycure

#### <a name="android"></a>Android

- 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在**步骤 7** 中使用此 [Skycure 应用商店 URL](https://play.google.com/store/apps/details?id=com.skycure.skycure)。

#### <a name="ios"></a>iOS

- 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 在“配置应用信息”部分的步骤 5 中使用此 [Skycure 应用商店 URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8)。

### <a name="check-point-sandblast-mobile"></a>Check Point SandBlast Mobile

#### <a name="android"></a>Android

- 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在“步骤 7”中使用此 [Check Point SandBlast Mobile 应用商店 URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox)。

#### <a name="ios"></a>iOS

- 联系 [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) 以获取 iOS 应用。 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md) 的说明，然后在“配置应用信息”部分下的“步骤 5”中使用 Apple 应用商店 URL。

### <a name="zimperium"></a>Zimperium

#### <a name="android"></a>Android

- 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在步骤 7 中使用此 [Zimperium 应用商店 URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en)。

#### <a name="ios"></a>iOS

- 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 在“配置应用信息”部分的步骤 5 中使用此 [Zimperium 应用商店 URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8)。

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>将 MTD 应用与 iOS 应用配置策略关联

### <a name="for-lookout"></a>对于 Lookout

- 按照[使用 iOS 应用配置策略](app-configuration-policies-use-ios.md)主题中所述的步骤，创建 iOS 应用配置策略。

### <a name="for-skycure"></a>对于 Skycure

-   使用以前在 [Skycure 管理控制台](https://aad.skycure.com)中配置的相同 Azure AD 帐户，这也应该是用于登录 Intune 经典门户的相同帐户。

-   需要**下载** iOS 应用配置策略文件： 
    -   转到 [Skycure 管理控制台](https://aad.skycure.com)并使用管理员凭据登录。
    
    -   转到“设置”&gt;“设备管理集成”&gt;“EMM 集成选择”，选择“Microsoft Intune”，然后保存所做选择。
    
    -   单击“集成设置文件”链接，然后保存生成的 \*.zip 文件。 该 .zip 文件包含 **skycure\_configuration.plist** 文件，该文件用于在 Intune 中创建 iOS 应用配置策略。
    
    -   请参阅[将 Microsoft Intune 应用配置策略用于 iOS](app-configuration-policies-use-ios.md)，查看相关操作说明，添加 Skycure iOS 应用配置策略。
    
    - 在“步骤 8”中，使用选项“输入 XML 数据”，复制 **skycure_configuration.plist** 文件中的内容并将粘贴到配置策略正文。

还可从此处复制 skycure_configuration.plist 内容：

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-check-point-sandblast-mobile"></a>有关 Check Point SandBlast Mobile 的信息

- 请参阅[将 Microsoft Intune 应用配置策略用于 iOS](app-configuration-policies-use-ios.md)，查看相关操作说明，以添加 Check Point SandBlast Mobile iOS 应用配置策略。
    - 在“步骤 8”中，使用选项“输入 XML 数据”，复制下列内容并粘贴到配置策略正文。

```
<dict><key>MDM</key><string>INTUNE</string></dict>

```

### <a name="for-zimperium"></a>对于 Zimperium

- 请参阅[将 Microsoft Intune 应用配置策略用于 iOS](app-configuration-policies-use-ios.md)，查看相关操作说明，添加 Zimperium iOS 应用配置策略。
    - 在“步骤 8”中，使用选项“输入 XML 数据”，复制下列内容并粘贴到配置策略正文。

```
<dict>
<key>provider</key><string>Intune</string>
<key>userprincipalname</key><string>{{userprincipalname}}</string>
<key>deviceid</key>
<string>{{deviceid}}</string>
<key>serialnumber</key>
<string>{{serialnumber}}</string>
<key>udidlast4digits</key>
<string>{{udidlast4digits}}</string>
</dict>

```

## <a name="to-assign-apps-all-mtd-partners"></a>分配应用（所有 MTD 合作伙伴）

- 请参阅[使用 Intune 向组分配应用](apps-deploy.md)，查看相关操作说明。

## <a name="next-steps"></a>后续步骤

- [添加设备符合性策略规则已实现 MTD](mtd-device-compliance-policy-create.md)
