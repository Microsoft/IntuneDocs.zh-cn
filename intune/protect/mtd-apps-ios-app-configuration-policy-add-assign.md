---
title: 向 Microsoft Intune 添加并分配 MTD 应用
titleSuffix: Microsoft Intune
description: 在 Azure 门户中使用 Intune 添加移动威胁防御 (MTD) 应用、Microsoft Authenticator 应用和 iOS 配置策略。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04a18befe73ce63f5619c3efc6def4189db9c8df
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188484"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>使用 Intune 添加和分配移动威胁防御 (MTD) 应用

可以使用 Intune 添加和部署 Mobile Threat Defense (MTD) 应用，以便最终用户可以在其移动设备中确定某个威胁时接收通知，并接收指导来解除威胁。

> [!NOTE]
> 本文适用于所有移动威胁防御合作伙伴。

## <a name="before-you-begin"></a>在开始之前

在 Intune 中完成以下步骤。 请务必熟悉以下过程：

- [将应用添加到 Intune](../apps/apps-add.md)。
- [将 iOS 应用配置策略添加到 Intune](../apps/app-configuration-policies-use-ios.md)。
- [使用 Intune 分配应用](../apps/apps-deploy.md)。

> [!TIP]
> Intune 公司门户在 Android 设备上以中转站的方式工作，以便用户能够让 Azure AD 检查自己的标识。

## <a name="configure-microsoft-authenticator-for-ios"></a>配置适用于 iOS 的 Microsoft Authenticator

对于 iOS 设备，需要 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)，这样用户便可让 Azure AD 检查自己的标识。 此外，需要 iOS 应用配置策略，用于设置要与 Intune 配合使用的 MTD iOS 应用。

请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 当配置“应用信息”时，使用此 [Microsoft Authenticator 应用商店 URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)  。

## <a name="configure-mtd-applications"></a>配置 MTD 应用程序

请选择与你的 MTD 提供程序对应的部分：

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>配置 Lookout for Work 应用

- **Android**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 将此 [Lookout for Work Google 应用商店 URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) 用于“应用商店 URL”。 

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 将此 [Lookout for Work iOS 应用商店 URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) 用于“应用商店 URL”。 

- **Apple 应用商店之外的 Lookout for Work 应用**
  - 必须重新签署 Lookout for Work iOS 应用。 Lookout 会在 iOS 应用商店之外分发其 Lookout for Work iOS 应用。 分发应用之前，必须使用 iOS 企业开发者证书对应用重新签名。  
  - 有关对 Lookout for Work iOS 应用重新签名的详细说明，请参阅 Lookout 网站上的 [Lookout for Work iOS 应用重新签名过程](https://personal.support.lookout.com/hc/articles/114094038714)。

  - **为 Lookout for Work iOS 应用用户启用 Azure AD 身份验证。**

    1. 转到 [Azure 门户](https://portal.azure.com)，使用自己的凭据登录，然后导航到应用程序页。

    2. 添加 **Lookout for Work iOS 应用**作为**本机客户端应用程序**。

    3. 将 **com.lookout.enterprise.yourcompanyname** 替换为对 IPA 签名时选择的客户捆绑 ID。

    4. 添加其他重定向 URI： **&lt;companyportal://code/>** ，后跟原始重定向 URI 的 URL 编码形式版本。

    5. 将**委托的权限**添加到应用。

    > [!NOTE]
    > 有关详细信息，请参阅[使用 Azure AD 配置本机客户端应用程序](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)。

  - **添加 Lookout for Work ipa 文件。**

    - 按照文章[使用 Intune 添加 iOS LOB 应用](../apps/lob-apps-ios.md)中所述，上传重新签名的 .ipa 文件。 还需将最低操作系统版本设为 iOS 8.0 或更高版本。

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>配置 Symantec Endpoint Protection Mobile 应用

- **Android**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 将此 [SEP Mobile 应用商店 URL](https://play.google.com/store/apps/details?id=com.skycure.skycure) 用于“应用商店 URL”。   对于  “最低操作系统”，请选择“Android 4.0 (Ice Cream Sandwich)”  。

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 将此 [SEP Mobile 应用商店 URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) 用于“应用商店 URL”。 

### <a name="configure-check-point-sandblast-mobile-apps"></a>配置 Check Point SandBlast Mobile 应用

- **Android**  
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 将此 [Check Point SandBlast Mobile 应用商店 URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) 用于“应用商店 URL”  。

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 将此 [Check Point SandBlast Mobile 应用商店 URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) 用于“应用商店 URL”  。  

### <a name="configure-zimperium-apps"></a>配置 Zimperium 应用

- **Android**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 将此 [Zimperium 应用商店 URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) 用于“应用商店 URL”。 

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 将此 [Zimperium 应用商店 URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) 用于“应用商店 URL”。   
 
### <a name="configure-pradeo-apps"></a>配置 Pradeo 应用

- **Android**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 将此 [Pradeo 应用商店 URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) 用于“应用商店 URL”。 

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 将此 [Pradeo 应用商店 URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) 用于“应用商店 URL”。 

### <a name="configure-better-mobile-apps"></a>配置 Better Mobile 应用

- **Android**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 将此 [Active Shield 应用商店 URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) 用于“应用商店 URL”。 

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 将此 [ActiveShield 应用商店 URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) 用于“应用商店 URL”。 

### <a name="configure-sophos-apps"></a>配置 Sophos 应用

- **Android**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 将此 [Sophos 应用商店 URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) 用于“应用商店 URL”。 

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 将此 [ActiveShield 应用商店 URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) 用于“应用商店 URL”。 

### <a name="configure-wandera-apps"></a>配置 Wandera 应用

- **Android**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 将此 [Wandera Mobile 应用商店 URL](https://play.google.com/store/apps/details?id=com.wandera.android) 用于“应用商店 URL”  。 对于  “最低操作系统”，请选择“Android 5.0”  。

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 将此 [Wandera Mobile 应用商店 URL](https://itunes.apple.com/app/wandera/id605469330) 用于“应用商店 URL”  。

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>使用 iOS 应用配置策略配置 MTD 应用

### <a name="lookout-for-work-app-configuration-policy"></a>Lookout for Work 应用配置策略

按照[使用 iOS 应用配置策略](../apps/app-configuration-policies-use-ios.md)一文中所述的步骤，创建 iOS 应用配置策略。

### <a name="sep-mobile-app-configuration-policy"></a>SEP 移动应用配置策略

使用以前在 [Symantec Endpoint Protection 管理控制台](https://aad.skycure.com)中配置的同一 Azure AD 帐户，这也应是用于登录 Intune 的同一帐户。

- 下载 iOS 应用配置策略文件： 
  - 转到 [Symantec Endpoint Protection 管理控制台](https://aad.skycure.com)并使用管理员凭据登录。

  - 转到  “设置”，然后在  “集成”下选择 Intune  。 选择“EMM 集成选择”  。 选择  Microsoft，然后保存你的选择。

  - 单击“集成设置文件”  链接，然后保存生成的 \*.zip 文件。 该 .zip 文件包含 *.plist  文件，该文件用于在 Intune 中创建 iOS 应用配置策略。

  - 请参阅[将 Microsoft Intune 应用配置策略用于 iOS](../apps/app-configuration-policies-use-ios.md)，查看相关操作说明，添加 SEP Mobile iOS 应用配置策略。

    - 对于“配置设置格式”  ，选择“输入 XML 数据”  ，复制 *.plist  文件中的内容并将其粘贴到配置策略正文。

> [!NOTE]
> 如果无法检索文件，请联系 [Symantec Endpoint Protection Mobile 企业支持部门](https://support.symantec.com/en_US/contact-support.html)。

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Check Point SandBlast Mobile 应用配置策略

请参阅[将 Microsoft Intune 应用配置策略用于 iOS](../apps/app-configuration-policies-use-ios.md)，查看相关操作说明，以添加 Check Point SandBlast Mobile iOS 应用配置策略。

- 对于“配置设置格式”  ，选择“输入 XML 数据”  ，复制以下内容并将其粘贴到配置策略正文。

  `<dict><key>MDM</key><string>INTUNE</string></dict>`


### <a name="zimperium-app-configuration-policy"></a>Zimperium 应用配置策略

请参阅[将 Microsoft Intune 应用配置策略用于 iOS](../apps/app-configuration-policies-use-ios.md)，查看相关操作说明，添加 Zimperium iOS 应用配置策略。

- 对于“配置设置格式”  ，选择“输入 XML 数据”  ，复制以下内容并将其粘贴到配置策略正文。

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

### <a name="pradeo-app-configuration-policy"></a>Pradeo 应用配置策略

Pradeo 在 iOS 上不支持应用程序配置策略。  相反，若要获取已配置的应用，请与 Pradeo 合作以实现已预先配置了所需设置的自定义 IPA 或 APK 文件。

### <a name="better-mobile-app-configuration-policy"></a>Better Mobile 应用配置策略

请参阅[将 Microsoft Intune 应用配置策略用于 iOS](../apps/app-configuration-policies-use-ios.md)，查看相关操作说明，添加 Better Mobile iOS 应用配置策略。

- 对于“配置设置格式”  ，选择“输入 XML 数据”  ，复制以下内容并将其粘贴到配置策略正文。 使用相应的控制台 URL 替换 `https://client.bmobi.net` URL。

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

### <a name="sophos-mobile-app-configuration-policy"></a>Sophos Mobile 应用配置策略

按照[使用 iOS 应用配置策略](../apps/app-configuration-policies-use-ios.md)一文中所述的步骤，创建 iOS 应用配置策略。

### <a name="wandera-app-configuration-policy"></a>Wandera 应用配置策略

请参阅[将 Microsoft Intune 应用配置策略用于 iOS](../apps/app-configuration-policies-use-ios.md)，查看相关操作说明，添加 Wandera iOS 应用配置策略。

- 对于“配置设置格式”  ，请选择“输入 XML 数据”  。

登录到 RADAR Wandera 门户并浏览到“设置”   > “EMM 集成”   > “应用推送”  。 选择“Intune”  ，然后复制下列内容并粘贴到配置策略正文。  

  ```
  <dict><key>secretKey</key>
  <string>SeeRADAR</string>
  <key>apiKey</key>
  <string> SeeRADAR </string>
  <key>customerId</key>
  <string> SeeRADAR </string>
  <key>email</key>
  <string>{{mail}}</string>
  <key>firstName</key>
  <string>{{username}}</string>
  <key>lastName</key>
  <string></string>
  <key>activationType</key>
  <string>PROVISION_THEN_AWP</string></dict>
  ```

## <a name="assign-apps-to-groups"></a>将应用分配给组

此步骤适用于所有 MTD 合作伙伴。 请参阅[使用 Intune 向组分配应用](../apps/apps-deploy.md)，查看相关操作说明。

## <a name="next-steps"></a>后续步骤

- [为 MTD 配置设备符合性策略](mtd-device-compliance-policy-create.md)
