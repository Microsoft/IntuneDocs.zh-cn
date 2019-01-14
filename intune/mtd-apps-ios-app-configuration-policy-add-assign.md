---
title: 向 Microsoft Intune 添加并分配 MTD 应用 | Microsoft Intune
description: 在 Azure 门户中使用 Intune 添加移动威胁防御 (MTD) 应用、Microsoft Authenticator 应用和 iOS 配置策略。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d08a7332ba96f552b488ad3f5d00004d0445d7ec
ms.sourcegitcommit: 6058c611d5a54076121af1d327a43ad861a43f8a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2019
ms.locfileid: "53995991"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>使用 Intune 添加和分配移动威胁防御 (MTD) 应用

> [!NOTE] 
> 本主题适用于所有移动威胁防御合作伙伴。

可以使用 Intune 添加和部署 Mobile Threat Defense (MTD) 应用，以便最终用户可以在其移动设备中确定某个威胁时接收通知，并接收指导来解除威胁。


## <a name="before-you-begin"></a>在开始之前

需要在 [Azure 门户](https://portal.azure.com/)中完成以下步骤。 请务必熟悉以下过程：

  -   [将应用添加到 Intune](apps-add.md)。
  -   [将 iOS 应用配置策略添加到 Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。
  -   [使用 Intune 分配应用](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)。

> [!TIP]
> Intune 公司门户在 Android 设备上以中转站的方式工作，以便用户能够让 Azure AD 检查自己的标识。

## <a name="configure-microsoft-authenticator-for-ios"></a>配置适用于 iOS 的 Microsoft Authenticator
对于 iOS 设备，需要 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)，这样用户便可让 Azure AD 检查自己的标识。 此外，需要 iOS 应用配置策略，用于设置要与 Intune 配合使用的 MTD iOS 应用。

请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 使用“配置应用信息”部分下步骤 12 中的此 [Microsoft Authenticator 应用商店 URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)。

## <a name="configure-mtd-applications"></a>配置 MTD 应用程序

请选择与你的 MTD 提供程序对应的部分：

  - [Lookout for Work](#configure-lookout-for-work-apps)
  - [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
  - [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
  - [Zimperium](#configure-zimperium-apps)
  - [Pradeo](#configure-pradeo-apps)
  - [Better Mobile](#configure-better-mobile-apps)

### <a name="configure-lookout-for-work-apps"></a>配置 Lookout for Work 应用

- **Outlook Web Access (OWA)**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在步骤 7 中使用此 [Lookout for Work Google 应用商店 URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise)。

- **iOS**

  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 使用“配置应用信息”部分下的步骤 12 中的此 [Lookout for Work iOS 应用商店 URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8)。

-   **Apple 应用商店之外的 Lookout for Work 应用**
    - 需要对 Lookout for Work iOS 应用进行重新签名。 Lookout 会在 iOS 应用商店之外分发其 Lookout for Work iOS 应用。 分发应用之前，必须使用 iOS 企业开发者证书对应用重新签名。
    - 有关对 Lookout for Work iOS 应用重新签名的详细说明，请参阅 Lookout 网站上的 [Lookout for Work iOS 应用重新签名过程](https://personal.support.lookout.com/hc/articles/114094038714)。

    - **为 Lookout for Work iOS 应用用户启用 Azure AD 身份验证。**

        1. 转到 [Azure 门户](https://portal.azure.com)，使用自己的凭据登录，然后导航到应用程序页。

        2. 添加 **Lookout for Work iOS 应用**作为**本机客户端应用程序**。

        3. 将 **com.lookout.enterprise.yourcompanyname** 替换为对 IPA 签名时选择的客户捆绑 ID。

        4.  添加其他重定向 URI：**&lt;companyportal://code/>**，后跟原始重定向 URI 的 URL 编码形式版本。

        5.  将**委托的权限**添加到应用。

        > [!NOTE] 
        > 有关详细信息，请参阅[使用 Azure AD 配置本机客户端应用程序](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)。

     - **添加 Lookout for Work ipa 文件。**

        - 按照[使用 Intune 添加 iOS LOB 应用](lob-apps-ios.md)主题中所述，上传重新签名的 .ipa 文件。 还需将最低操作系统版本设为 iOS 8.0 或更高版本。

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>配置 Symantec Endpoint Protection Mobile 应用

 - **Outlook Web Access (OWA)**

    - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在步骤 7 中，使用此 [SEP Mobile 应用商店 URL](https://play.google.com/store/apps/details?id=com.skycure.skycure)。  对于“最低操作系统”，请选择“Android 4.0 (Ice Cream Sandwich)”。

 - **iOS**

    - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 在步骤 12 中使用“配置应用信息”部分下的此 [SEP Mobile 应用商店 URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8)。

### <a name="configure-check-point-sandblast-mobile-apps"></a>配置 Check Point SandBlast Mobile 应用

 - **Outlook Web Access (OWA)**

    - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在“步骤 7”中使用此 [Check Point SandBlast Mobile 应用商店 URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox)。

 - **iOS**

    - 联系 [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) 以获取 iOS 应用。 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md) 的说明，然后使用“配置应用信息”部分下的“步骤 12”中的 Apple 应用商店 URL。

### <a name="configure-zimperium-apps"></a>配置 Zimperium 应用

 - **Outlook Web Access (OWA)**

    - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在步骤 7 中使用此 [Zimperium 应用商店 URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en)。

 - **iOS**

    - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 使用“配置应用信息”部分下的步骤 12 中的此 [Zimperium 应用商店 URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8)。

### <a name="configure-pradeo-apps"></a>配置 Pradeo 应用

 - **Outlook Web Access (OWA)**

    - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在步骤 7 中使用此 [Pradeo 应用商店 URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US)。

 - **iOS**

    - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 在“配置应用信息”部分下的步骤 12 中使用此 [Pradeo 应用商店 URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8)。

### <a name="configure-better-mobile-apps"></a>配置 Better Mobile 应用

 - **Outlook Web Access (OWA)**

    - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](store-apps-android.md)，查看相关操作说明。 在第 7 步中使用此 [Active Shield 应用商店 URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise)。

 - **iOS**

    - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](store-apps-ios.md)，查看相关说明。 在“配置应用信息”部分下的步骤 12 中使用此[应用商店 URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4)。

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>使用 iOS 应用配置策略配置 MTD 应用

### <a name="lookout-for-work-app-configuration-policy"></a>Lookout for Work 应用配置策略

- 按照[使用 iOS 应用配置策略](app-configuration-policies-use-ios.md)一文中所述的步骤，创建 iOS 应用配置策略。

### <a name="sep-mobile-app-configuration-policy"></a>SEP 移动应用配置策略

-   使用以前在 [Symantec Endpoint Protection 管理控制台](https://aad.skycure.com)中配置的相同 Azure AD 帐户，这也应是用于登录 Intune 经典门户的相同帐户。

-   需要**下载** iOS 应用配置策略文件： 
    -   转到 [Symantec Endpoint Protection 管理控制台](https://aad.skycure.com)并使用管理员凭据登录。

    -   转到“设置”，然后在“集成”下选择 Intune。 选择“EMM 集成选择”。 选择 Microsoft，然后保存你的选择。

    -   单击“集成设置文件”链接，然后保存生成的 \*.zip 文件。 该 .zip 文件包含 *.plist 文件，该文件用于在 Intune 中创建 iOS 应用配置策略。

    -   请参阅[将 Microsoft Intune 应用配置策略用于 iOS](app-configuration-policies-use-ios.md)，查看相关操作说明，添加 SEP Mobile iOS 应用配置策略。

    - 在“步骤 8”中，使用选项“输入 XML 数据”，复制 *.plist 文件中的内容并粘贴到配置策略正文。

> [!NOTE]
> 如果无法检索文件，请联系 [Symantec Endpoint Protection Mobile 企业支持部门](https://support.symantec.com/en_US/contact-support.html)。

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Check Point SandBlast Mobile 应用配置策略

- 请参阅[将 Microsoft Intune 应用配置策略用于 iOS](app-configuration-policies-use-ios.md)，查看相关操作说明，以添加 Check Point SandBlast Mobile iOS 应用配置策略。
    - 在“步骤 8”中，使用选项“输入 XML 数据”，复制下列内容并粘贴到配置策略正文。

```
<dict><key>MDM</key><string>INTUNE</string></dict>
```

### <a name="zimperium-app-configuration-policy"></a>Zimperium 应用配置策略

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

### <a name="better-mobile-app-configuration-policy"></a>Better Mobile 应用配置策略

- 请参阅[将 Microsoft Intune 应用配置策略用于 iOS](app-configuration-policies-use-ios.md)，查看相关操作说明，添加 Better Mobile iOS 应用配置策略。
    - 在“步骤 8”中，使用选项“输入 XML 数据”，复制下列内容并粘贴到配置策略正文。 使用相应的控制台 URL 替换 `https://client.bmobi.net` URL。

```
<dict>
<key>better_server_url</key>
<string>https://client.bmobi.net</string>
<key>better_udid</key>
<string>{{aaddeviceid}}</string>
<key>better_user</key>
<string>{{userprincipalname}}</string>
</dict>
```

## <a name="assign-apps-to-groups"></a>将应用分配给组

- 此步骤适用于所有 MTD 合作伙伴。 请参阅[使用 Intune 向组分配应用](apps-deploy.md)，查看相关操作说明。

## <a name="next-steps"></a>后续步骤

- [为 MTD 配置设备符合性策略](mtd-device-compliance-policy-create.md)
