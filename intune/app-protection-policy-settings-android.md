---
title: Android 应用保护策略设置 | Microsoft Intune
titlesuffix: Microsoft Intune
description: 本主题介绍适用于 Android 设备的应用保护策略设置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 1/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 08848853a70d0fbdabeb123960f36dc19478e6c2
ms.sourcegitcommit: 0142020a7cd75348c6367facf072ed94238e667f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2019
ms.locfileid: "55230046"
---
# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 应用保护策略设置
本文介绍适用于 Android 设备的应用保护策略设置。 可在 Azure 门户的“设置”边栏选项卡中为应用保护策略[配置](app-protection-policies.md)所述的策略设置。
策略设置分为三类：数据保护设置、访问要求和条件启动。 在本文中，术语策略托管应用指使用应用保护策略配置的应用。

##  <a name="data-protection"></a>数据保护 
### <a name="data-transfer"></a>数据传输
| Setting | 如何使用 | 默认值 |
|------|------|------|
| **将组织数据备份到 Android 备份服务** | 选择“阻止”可阻止此应用将工作或学校数据备份到 [Android 备份服务](https://developer.android.com/google/backup/index.html)。<br><br> 选择“允许”可允许此应用备份工作或学校数据。| **允许** |
| 将组织数据发送到其他应用 | 指定哪些应用可从此应用接收数据： <ul><li> **策略托管应用**：仅允许传输到其他策略托管应用。</li> <li>**所有应用**：允许传输到任何应用。 </li> <li>**无**：不允许将数据传输到任何应用，包括其他策略托管应用。</li></ul> <p>默认情况下，Intune 允许向一些豁免应用和服务传输数据。 此外，如果需要允许将数据传输到不支持 Intune APP 的应用，则可以创建自己的豁免项目。 有关详细信息，请参阅[数据传输豁免](#Data-transfer-exemptions)。<p>此策略也适用于 Android 应用链接。  通用 Web 链接由“在 Intune Managed Browser 中打开应用链接”策略设置托管。<p>**注意：** Intune 目前不支持 Android Instant Apps 功能。Intune 将阻止进/出该应用的任何数据连接。有关详细信息，请参阅 Android 开发人员文档中的 [Android Instant Apps](https://developer.android.com/topic/instant-apps/index.html)。</p>| **所有应用** | 
|<ul><ui> **选择要豁免的应用** | 为上一选项选择“策略托管应用”时，此选项才可用。 | |
| **从其他应用接收数据** | 指定哪些应用可将数据传输到此应用： <ul><li>**策略托管应用**：仅允许从其他策略托管应用进行传输。</li><li>**所有应用**：允许从任何应用传输的数据。</li><li>**无**：不允许从任何应用传输数据，包括其他策略托管应用。 </li></ul> <p>有一些豁免应用和服务，Intune 可能会允许从其传输数据。 有关应用和服务的完整列表，请参阅[数据传输豁免](#data-transfer-exemptions)。 | **所有应用** |
| **保存组织数据的副本** | 选择“阻止”，在此应用中禁用使用“另存为”选项。 如果想要允许使用“另存为”，则选择“允许”。 **注意：** Microsoft Excel、OneNote、PowerPoint 和 Word 支持此设置。它也可能受第三方和 LOB 应用支持。| **允许** |  
|<ul><ui> **允许用户将副本保存到所选的服务** |用户可以保存到所选的服务（OneDrive for Business、SharePoint 和本地存储）中。 将阻止所有其他服务。  | **未选择任何项** |
| **限制在其他应用间进行剪切、复制和粘贴** | 指定剪切、复制和粘贴操作何时可用于此应用。 选择： <ul><li>**阻止**：不允许在此应用和任何其他应用间进行剪切、复制和粘贴操作。</li><li>**策略托管应用**：允许在此应用和其他策略托管应用间进行剪切、复制和粘贴操作。</li><li>**带粘贴的策略托管应用**：允许在此应用和其他策略托管应用间进行剪切或复制。 允许将任何应用中的数据粘贴到此应用。</li><li>**任何应用**：不限制从此应用和对此应用进行剪切、复制和粘贴。 | **任何应用** |
| **屏幕捕获和 Google 助手** | 选择“禁用”，则使用此应用时，会阻止设备的屏幕捕获和“Android 助手”功能。 选择“禁用”还会导致在通过工作或学校帐户使用此应用时应用切换器预览图像模糊。| **启用** |
  
### <a name="encryption"></a>加密
| Setting | 如何使用 | 默认值 |
|------|------|------|
| **对组织数据进行加密** | 选择“需要”，在此应用中启用工作或学校数据加密。 Intune 使用 OpenSSL 256 位 AES 加密方案和 Android Keystore 系统安全加密应用数据。 数据在文件 I/O 任务期间同步加密。 始终加密设备存储中的内容。 SDK 将继续提供 128 位密钥支持以与使用旧版 SDK 的内容和应用兼容。 <br><br> 加密方法**没有**获得 FIPS 140-2 认证。     |  **需要**|  



### <a name="functionality"></a>功能
| Setting | 如何使用 | 默认值 |
|------|------|------|
| **使用本机联系人应用同步应用** | 选择“禁用”，阻止应用将数据保存到设备上的本机“联系人”应用。 如果选择“启用”，应用可将数据保存到设备上的本机“联系人”应用。 <br><br>执行选择性擦除以从应用删除工作或学校数据时，将删除从应用直接同步到本机“联系人”应用的联系人。 无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 目前仅适用于 Microsoft Outlook 应用。 | **启用** |
| **打印组织数据** | 选择“禁用”，阻止应用打印工作或学校数据。 | **启用** |
|**使用策略托管浏览器共享 Web 内容** | 指定如何从策略管理的应用中打开 Web 内容（http/https 链接）。 选择：<ul><li>**需要**：允许 Web 内容仅在策略托管浏览器中打开。</li><li>**未配置**：允许在任何应用中使用网络链接 </li></ul><br><br> 如果正使用 Intune 管理设备，请参阅[使用 Microsoft Intune 的 Managed Browser 策略管理 Internet 访问](app-configuration-managed-browser.md)。<br><br>**策略托管的浏览器**<br>如果部署多个策略托管的浏览器，则只有一个将会启动。  启动顺序将为 Intune Managed Browser，然后才是 Microsoft Edge。  在 Android 上，如果未安装 Intune Managed Browser 和 Microsoft Edge，最终用户可以从支持 http/https 链接的其他策略托管应用中进行选择。<p>如果需要策略托管的浏览器，但未安装，系统将提示最终用户安装 Intune Managed Browser。<p>如果需要使用策略托管的浏览器，则将由“允许应用向其他应用传送数据”策略设置管理 Android 应用链接。<p>**Intune 设备注册**<br>如果使用 Intune 管理设备，请参阅“使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问”。 <p>**策略托管的 Microsoft Edge**<br>移动设备（iOS 和 Android）的 Microsoft Edge 浏览器支持 Intune 应用保护策略。 在 Microsoft Edge 浏览器应用程序中使用其企业 Azure AD 帐户登录的用户将受 Intune 保护。 Microsoft Edge 浏览器集成了 MAM SDK 并支持其除阻止以外的所有数据保护策略：<br><ul><li>**另存为**：Microsoft Edge 浏览器不允许用户向云存储提供商（如 OneDrive）添加直接的应用内连接。</li><li>**联系人同步**：Microsoft Edge 浏览器不会保存到本地联系人列表。</li></ul><br>**注意：** APP SDK 无法确定目标应用是否为浏览器。在 Android 设备上，允许使用支持 http/https 意向的其他托管浏览器应用。 | 未配置 |
| **第三方键盘** | 选择“禁用”，阻止在托管应用程序中使用第三方键盘。 <br><br>启用此设置后，用户将收到一次性消息，说明禁止使用第三方键盘。 用户首次需要使用键盘与组织数据进行交互时，将会出现此消息。 使用托管应用程序时，只能使用标准键盘，所有其他键盘选项都将禁用。 此设置不影响在非托管应用程序中使用第三方键盘。 | **启用** |



  ## <a name="data-transfer-exemptions"></a>数据传输豁免

  有一些豁免应用和平台服务，Intune 应用保护策略可能会允许向其或从其传输数据。 例如，Android 上所有 Intune 托管的应用都必须能够将数据传输至 Google 文本到语音转换或从中接收数据，这样使移动设备屏幕上的文本可以被朗读出来。 此列表可能会更改以反映有利于安全工作效率的服务和应用。

  ### <a name="full-exemptions"></a>完全豁免

  完全允许这些应用和服务向 Intune 托管应用传输数据或从其接收数据。

  |应用/服务名称 | 描述 |
  | ------ | ---- |
  | com.android.phone | 本机电话应用
  | com.android.vending | Google Play Store |
  | com.android.documentsui | Android 文档选取器|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html)，这是包括 Outlook 在内的许多应用所必需的。 |
  | com.android.webview |[Webview](https://developer.android.com/reference/android/webkit/WebView.html)，这是包括 Outlook 在内的许多应用所必需的。|
  | com.google.android.tts | Google 文本到语音转换 |
  | com.android.providers.settings | Android 系统设置 |
  | com.android.settings | Android 系统设置 |
  | com.azure.authenticator | Azure 验证器应用，这是在许多情况下成功进行身份验证所必需的。 |
  | com.microsoft.windowsintune.companyportal | Intune 公司门户|

  ### <a name="conditional-exemptions"></a>有条件的豁免
  只有在某些条件下，才允许这些应用和服务向 Intune 托管应用传输数据或从其接收数据。

  |应用/服务名称 | 描述 | 豁免条件|
  | ------ | ---- | --- |
  | com.android.chrome | Google Chrome 浏览器 | Chrome 用于 Android 7.0 及更高版本上的某些 WebView 组件，并且永远不会从视图中隐藏。 但是，该应用发出和收到的数据流始终受限。  |
  | com.skype.raider | Skype | Skype 应用仅允许执行引发电话呼叫的某些操作。 |
  | com.android.providers.media | Android 媒体内容提供程序 | 媒体内容提供程序仅允许铃声选择操作。 |
  | com.google.android.gms;com.google.android.gsf | Google Play Services 包 | 这些包允许 Google Cloud Messaging 操作，例如推送通知。 |

有关详细信息，请参阅[应用的数据传输策略例外情况](app-protection-policies-exception.md)。

##  <a name="access-requirements"></a>访问要求

| Setting | 如何使用 | 默认值 |
|------|------|------|
| **需要 PIN 才能进行访问** | 选择“需要”，要求使用 PIN 才能使用此应用。 用户首次在工作或学校环境中运行应用时，将提示其设置此 PIN。 <br><br> 为 PIN 强度配置以下设置：| **需要** |
|<ul><ui> **PIN 类型** | 在访问应用了应用保护策略的应用之前，为数值或密码类型 PIN 设置要求。 数值要求只涉及数字，而密码则可采用至少 1 个字母或至少 1 个特殊字符进行定义。 <br><br>**注意：** 允许的特殊字符包括 Android 英语键盘上的特殊字符和符号。| **数字** |
|<ul><ui> **简单 PIN** |选择“允许”，允许用户使用 1234、1111、abcd 或 aaaa 等简单的 PIN 序列。 选择“阻止”，阻止用户使用简单的序列。 <br><br>**注意：** 如果 PIN 类型配置为“密码”，并且“简单 PIN”设置为“允许”，则用户在其 PIN 中需要使用至少 1 个字母或至少 1 个特殊字符 *。* 如果 PIN 类型配置为“密码”，并且“简单 PIN”设置为“阻止”，则用户在其 PIN 中需要使用至少 1 个数字和 1 个字母以及至少 1 个特殊字符。 | **允许** |
| <ul><ui> **选择最小 PIN 长度** | 指定 PIN 序列必须包含的最小位数。  | **4** |
|<ul><ui> **用于访问的指纹而非 PIN (Android 6.0+)** | 选择“允许”，允许用户使用[指纹身份验证](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)而非 PIN 进行应用访问。 <br><br>**注意：** 此功能支持 Android 设备上的通用生物识别控件。不支持特定于 OEM 的生物识别设置，如 Samsung Pass。 <br><br>在 Android 设备上，可让用户通过 [Android 指纹身份验证](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)而非 PIN 证明其身份。 用户尝试通过其工作或学校帐户使用此应用时，系统会提示他们提供其指纹标识，而不是输入 PIN。 <br><br> Android 工作配置文件要求为强制执行的“允许使用指纹替代 PIN”策略注册单独的指纹。 此策略仅对在 Android 工作配置文件中安装的策略托管应用有效。 在公司门户注册以创建 Android 工作配置文件后，必须在设备中注册单独的指纹。 有关使用 Android 工作配置文件的工作配置文件指纹的详细信息，请参阅[锁定工作配置文件](https://support.google.com/work/android/answer/7029958)。 |**允许** |
| <ul><ul><ui>**超时后使用 PIN 替代指纹** |  设置为“需要”时，在应用处于空闲状态持续了指定超时时间段后，PIN 提示符将替代 Touch ID 提示符。   | **需要** |
| <ul><ul><ui>**超时(非活动状态的分钟数)** | 以分钟为单位，指定在 PIN 提示符替代 Touch ID 提示符之前，应用可以空闲的时间。  <br><br>此超时值应大于“在(活动状态的分钟数)后重新检查访问要求”下的指定值。| **30** |
|<ul><ui> **PIN 重置间隔的天数** | 选择“是”，要求用户在一段时间（以天为单位）后更改其应用 PIN。 <br><br> 默认值 = 否  <br><br> 设置为“是”时，可以配置重置所需的天数。 | **否**|
| <ul><ul><ui>**天数** | “PIN 重置间隔的天数”设置为“是”时，指定 PIN 重置所需的时间。 | **0** | 
|<ul><ui> **设置设备 PIN 时的应用 PIN** | 如果设置为“禁用”，则设置了设备 PIN 的 MDM 注册设备上不需要应用 PIN。   | **启用** |
| **用于访问的工作或学校帐户凭据** | 选择“需要”，要求用户使用其工作或学校帐户而非输入 PIN 进行登录以访问应用。 设置为“需要”并且 PIN 或生物识别提示已打开时，将同时显示公司凭据以及 PIN 或生物识别提示。 | **不需要** |
| **在(非活动状态的分钟数)后重新检查访问要求** | 配置应用要求用户再次指定访问要求之前必须经过的非活动状态的分钟数。  <br><br>**注意：** 在 Android 上，所有 Intune 托管应用均共享此 PIN。*应用离开设备主屏幕后，就会重置 PIN 计时器。在此设置中定义的超时期限内，用户无需在共享 PIN 的任何 Intune 托管应用上输入此 PIN。| **30** |


> [!NOTE]  
> 要详细了解在“访问权限”部分配置给同一组应用和用户的多个 Intune 应用保护设置如何在 Android 上运行，请参阅 [Intune MAM 常见问题](mam-faq.md)和[在 Intune 中使用应用保护策略访问操作选择性地擦除数据](app-protection-policies-access-actions.md)。


## <a name="conditional-launch"></a>条件启动
配置条件启动设置以设置访问保护策略的登录安全要求。 

默认情况下，向多个设置提供已预配置的值和操作。 可以删除“最小 OS 版本”等某些设置。 此外，还可以从“选择一个”下拉列表中选择其他设置。 

| Setting | 如何使用 |  
|---------|------------| 
| **最大 PIN 尝试次数** | 指定用户在执行配置操作之前必须成功输入其 PIN 的尝试次数。 此策略设置格式支持正整数。 *操作*包括： <br><ul><li>**重置 PIN** - 用户必须重置其 PIN。</li></ul> <ul><li>**擦除数据** - 从设备中擦除与应用程序关联的用户帐户。  </li></ul> </li></ul> 默认值 = 5 |
| **脱机宽限期** | MAM 应用可以脱机运行的分钟数。 指定重新检查应用访问要求之前的时间（以分钟为单位）。 *操作*包括： <br><ul><li>**阻止访问（分钟数）** - MAM 应用可以脱机运行的分钟数。 指定重新检查应用访问要求之前的时间（以分钟为单位）。 此期限到期后，该应用需要对 Azure Active Directory (Azure AD) 进行用户身份验证，以便该应用可以继续运行。 <br><br>此策略设置格式支持正整数。 <br><br>默认值 = 720 分钟（12 小时） </li></ul> <ul><li>**擦除数据（天数）** - 经过数天（由管理员定义）的脱机运行后，应用会要求用户连接到网络并重新进行身份验证。 如果用户身份验证成功，则可继续访问其数据，且将重置脱机时间间隔。  如果用户未能通过身份验证，则应用会对用户帐户和数据执行选择性擦除。 有关详细信息，请参阅[如何仅擦除 Intune 托管应用中的企业数据](https://docs.microsoft.com/intune/apps-selective-wipe)。</li></ul> 此策略设置格式支持正整数。 <br><br>  默认值 = 90 天 </li></ul> <br><br>  此项可以出现多次，每个实例支持不同的操作。 |   
| **已越狱/获得 root 权限的设备** |此设置没有可设置的值。 *操作*包括： <br><ul><li>**阻止访问** - 阻止在已越狱或已取得 root 权限的设备上运行此应用。 用户仍能够将此应用用于个人任务，但必须使用其他设备才能访问此应用中的工作或学校数据。</li></ul> <ul><li>**擦除数据** - 从设备中擦除与应用程序关联的用户帐户。  </li></ul> |
| **最低 OS 版本** | 指定要使用此应用所需的最低 Android 操作系统版本。 *操作*包括： <br><ul><li>**警告** - 如果设备上的 Android 版本不符合此要求，用户将看到一个通知。 可忽略此通知。  </li></ul> <ul><li>**阻止访问** - 如果设备上的 Android 版本不符合此要求，将阻止用户访问。</li></ul> <ul><li>**擦除数据** - 从设备中擦除与应用程序关联的用户帐户。  </li></ul> </li></ul>此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。 |
| **最低应用版本** | 指定最低操作系统值的值。 *操作*包括： <br><ul><li>**警告** - 如果设备上的应用版本不符合此要求，用户将会看到一个通知。 可忽略此通知。</li></ul> <ul><li>**阻止访问** - 如果设备上的应用版本不符合此要求，用户将会看到一个通知。 </li></ul> <ul><li>**擦除数据** - 从设备中擦除与应用程序关联的用户帐户。 </li></ul> </li></ul> 由于应用之间通常拥有不同的版本控制方案，因此，请创建针对一个应用的一个最低应用版本策略（例如 Outlook 版本策略）。<br><br> 此项可以出现多次，每个实例支持不同的操作。<br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。|
| **最低修补程序版本** | 要求设备具有由 Google 发布的最低 Android 安全修补程序。  <br><ul><li>**警告** - 如果设备上的 Android 版本不符合此要求，用户将看到一个通知。 可忽略此通知。  </li></ul> <ul><li>**阻止访问** - 如果设备上的 Android 版本不符合此要求，将阻止用户访问。</li></ul> <ul><li>**擦除数据** - 从设备中擦除与应用程序关联的用户帐户。  </li></ul></li></ul> 此策略设置支持日期格式 YYYY-MM-DD。 |
| **设备制造商** | 指定使用此应用所需的设备制造商。 *操作*包括： <br><ul><li>**允许指定项（阻止非指定项）** - 仅与指定制造商匹配的设备才能使用该应用。 所有其他设备将被阻止。 </li></ul> <ul><li>**允许指定项（擦除非指定项）** - 从设备中擦除与应用程序关联的用户帐户。 </li></ul> |
