---
title: "Android 应用保护策略设置"
titlesuffix: Microsoft Intune
description: "本主题介绍适用于 Android 设备的应用保护策略设置。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 26f81d8e6ba0fb433d714a5deeaadce9dd619c3f
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2018
---
# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 应用保护策略设置
本主题介绍适用于 Android 设备的应用保护策略设置。 可在 Azure 门户的“设置”边栏选项卡中为应用保护策略[配置](app-protection-policies.md)所述的策略设置。
有两种类别的策略设置：数据重定位设置和访问设置。 在本主题中，术语*策略托管应用*指使用应用保护策略配置的应用。

##  <a name="data-relocation-settings"></a>数据重定位设置

| Setting | 如何使用 | 默认值 |
|------|------|------|
| **阻止 Android 备份** | 选择“是”，阻止此应用将工作或学校数据备份到 [Android 备份服务](https://developer.android.com/google/backup/index.html)。选择“否”，允许此应用备份工作或学校数据。| 是 |
| **允许应用向其他应用传送数据** | 指定哪些应用可从此应用接收数据： <ul><li> **策略托管应用**：仅允许传输到其他策略托管应用。</li> <li>**所有应用**：允许传输到任何应用。 </li> <li>**无**：不允许将数据传输到任何应用，包括其他策略托管应用。</li></ul> <p>默认情况下，Intune 允许向一些豁免应用和服务传输数据。 此外，如果需要允许将数据传输到不支持 Intune APP 的应用，则可以创建自己的豁免项目。 有关详细信息，请参阅[数据传输豁免](#Data-transfer-exemptions)。<p>**注意：**Intune 目前不支持 Android Instant Apps 功能。 Intune 将阻止进/出该应用的任何数据连接。  有关 [Android Instant Apps](https://developer.android.com/topic/instant-apps/index.html) 的详细信息，请参阅 Android 开发人员文档。</p>| 所有应用 |
| **允许应用从其他应用接收数据** | 指定哪些应用可将数据传输到此应用： <ul><li>**策略托管应用**：仅允许从其他策略托管应用传输。</li><li>**所有应用**：允许从任何应用传输数据。</li><li>**无**：不允许从任何应用传输数据，包括其他策略托管应用。 </li></ul> <p>有一些豁免应用和服务，Intune 可能会允许从其传输数据。 有关应用和服务的完整列表，请参阅[数据传输豁免](#Data-transfer-exemptions)。 | 所有应用 |
| **阻止“另存为”** | 选择“是”，在此应用中禁用“另存为”选项。 如果你希望允许使用“另存为”，请选择“否”。 <p><br>**选择可保存公司数据的存储服务** <br>用户可以保存到所选的服务（OneDrive for Busines、SharePoint 和本地存储）中。 将阻止所有其他服务。</p> | 否 <br><br> 未选择任何项 |
| **限制剪切、复制和粘贴到其他应用程序** | 指定剪切、复制和粘贴操作何时可用于此应用。 选择： <ul><li>**阻止**：不允许在此应用和任何其他应用间进行剪切、复制和粘贴操作。</li><li>**策略托管应用**：允许在此应用和其他策略托管应用间进行剪切、复制和粘贴操作。</li><li>**带粘贴的策略托管应用**：允许在此应用和其他策略托管应用间进行剪切或复制。 允许将任何应用中的数据粘贴到此应用。</li><li>**任何应用**：不限制从此应用和对此应用进行剪切、复制和粘贴。 | 任何应用 |
|**限制显示在 Managed Browser 内的 Web 内容** | 选择“是”，强制在 Managed Browser 应用中打开应用中的 Web 链接。 <br><br> 对于未在 Intune 中注册的设备，策略托管应用中的 Web 链接将仅可在 Managed Browser 应用中打开。 <br><br> 如果正使用 Intune 管理设备，请参阅[使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问](app-configuration-managed-browser.md)。 | 否 |
| **加密应用数据** | 选择“是”，在此应用中启用工作或学校数据加密。 Intune 使用 OpenSSL 128 位 AES 加密方案和 Android Keystore 系统安全加密应用数据。 数据在文件 I/O 任务期间同步加密。 始终加密设备存储中的内容。 <br><br> 加密方法**没有**获得 FIPS 140-2 认证。  | 是 |
| **启用设备加密后禁用应用加密** | 选择“是”，在注册设备上检测到设备加密时，对内部应用存储禁用应用加密。 <br><br>注意：Intune 只能检测到注册到 Intune MDM 的设备。 外部应用存储仍需加密，以确保非托管的应用程序无法访问数据。 | 是 |
| **禁用联系人同步** | 选择“是”，阻止应用将数据保存到设备上的本机“联系人”应用。 如果选择“否”，应用可将数据保存到设备上的本机“联系人”应用。 <br><br>执行选择性擦除从应用删除工作或学校数据时，将删除从应用直接同步到本机“联系人”应用的联系人。 无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 目前仅适用于 Microsoft Outlook 应用。 | 否 |
| **禁用打印** | 选择“是”，阻止应用打印工作或学校数据。 | 否 |

  >[!NOTE]
  >**加密应用数据**设置的加密方法**没有**获得 FIPS 140-2 认证。

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
  | com.azure.authenticator | Azure 验证器应用，这是在许多情况下成功进行身份验证所必需的。 |
  | com.microsoft.windowsintune.companyportal | Intune 公司门户|

  ### <a name="conditional-exemptions"></a>有条件的豁免
  只有在某些条件下，才允许这些应用和服务向 Intune 托管应用传输数据或从其接收数据。

  |应用/服务名称 | 描述 | 豁免条件|
  | ------ | ---- | --- |
  | com.android.chrome | Google Chrome 浏览器 | Chrome 用于 Android 7.0 及更高版本上的某些 WebView 组件，并且永远不会从视图中隐藏。 但是，该应用发出和收到的数据流始终受限。
  | com.skype.raider | Skype | Skype 应用仅允许执行引发电话呼叫的某些操作。 |
  | com.android.providers.media | Android 媒体内容提供程序 | 媒体内容提供程序仅允许铃声选择操作。 |
  | com.google.android.gms;com.google.android.gsf | Google Play Services 包 | 这些包允许 Google Cloud Messaging 操作，例如推送通知。 |

有关详细信息，请参阅[应用的数据传输策略例外情况](app-protection-policies-exception.md)。

##  <a name="access-settings"></a>访问设置

| Setting | 如何使用 | 默认值 |
|------|------|------|
| **需要 PIN 才能进行访问** | 选择“是”，需要 PIN 才可使用此应用。 用户首次在工作或学校环境中运行应用时，将提示其设置此 PIN。 默认值 = **是**。<br><br> 为 PIN 强度配置以下设置： <ul><li>**PIN 重置前的尝试次数**：指定用户重置其 PIN 码前必须成功完成输入的尝试次数。 默认值 = **5**。</li><li> **允许简单 PIN**：选择“是”，允许用户使用简单的 PIN 序列，如 1234 或 1111。 选择“否”，阻止用户使用简单的序列。 默认值 = **是**。 </li><li> **PIN 长度**：指定 PIN 序列必须包含的最小位数。 默认值 = **4**。 <br><br> 此策略设置格式支持正整数。</li><li> **允许指纹而非 PIN (Android 6.0+)：**选择“是”，允许用户使用[指纹身份验证](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)而非 PIN 进行应用访问。 默认值 = **是**。</li></ul> 在 Android 设备上，可允许用户通过 [Android 指纹身份验证](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)而非 PIN 证明其身份。 用户尝试通过其工作或学校帐户使用此应用时，会提示他们提供其指纹标识而不是输入 PIN。 </li></ul>| 需要 PIN：是 <br><br> PIN 重置尝试次数：5 <br><br> 允许使用简单 PIN：是 <br><br> PIN 长度：4 <br><br> 允许使用指纹：是 |
| **访问需要公司凭据** | 选择“是”，要求用户使用其工作或学校帐户（而不是输入 PIN）登录进行应用访问。 如果将其设置为“是”，则此设置将替代 PIN 或 Touch ID 的要求。  | 否 |
| **阻止在已越狱或取得 root 权限的设备上运行托管应用** |选择“是”，阻止在已越狱或取得 root 权限的设备上运行此应用。 用户仍能够将此应用用于个人任务，但必须使用其他设备访问此应用中的工作或学校数据。 | 是 |
| **在一定时间后重新检查访问要求（分钟）** | 配置下列设置： <ul><li>**超时**：指重新检查访问要求（在前面的策略中定义）之前的分钟数。 例如，如果管理员在策略中启用 PIN，并阻止取得 root 权限的设备，则用户打开 Intune 托管的应用时，必须输入 PIN，且必须在未取得 root 权限的设备上使用应用。 使用此设置时，用户在 30 分钟（默认值）内无需在任何 Intune 托管应用上再次输入 PIN 或执行 root 检测检查。 <br><br> **注意：**在 Android 上，所有 Intune 托管应用均共享此 PIN。 应用离开设备主屏幕后，就会重置 PIN 计时器。 在此设置定义的超时期限内，用户无需在共享 PIN 的任何 Intune 托管应用上输入该 PIN。 <br><br> 此策略设置格式支持正整数。<br></li><li>**脱机宽限期**：指 MAM 应用可脱机运行的分钟数，需在重新检查应用访问要求之前指定该时间（以分钟为单位）。 默认值 = **720** 分钟（12 小时）。 此时间段到期后，应用将要求用户对 AAD 进行身份验证，以便应用可以继续运行。<br><br> 此策略设置格式支持正整数。</li></ul>| 超时：30 <br><br> 脱机：720 |
| **擦除应用数据前的脱机时间间隔(天)** | 经过数天（由管理员定义）的脱机运行后，应用会要求用户连接到网络并重新进行身份验证。 如果用户身份验证成功，则可继续访问其数据，且将重置脱机时间间隔。  如果用户未能通过身份验证，则应用会对用户帐户和数据执行选择性擦除。  请参阅[如何仅擦除 Intune 托管应用中的企业数据](https://docs.microsoft.com/intune/apps-selective-wipe)，详细了解选择性擦除所删除的数据。<br><br> 此策略设置格式支持正整数。 | 90 天 |
| **阻止屏幕捕获和 Android 助手 (Android 6.0+)** | 选择“是”，则在使用此应用时，阻止设备的屏幕捕获和“Android 助手”功能。 选择“是”还会在通过工作或学校帐户使用此应用时，导致应用切换器预览图像模糊。 | 否 |
| **托管设备 PIN 后禁用应用 PIN** | 在已注册设备上检测到设备锁后选择“是”禁用应用 PIN。 | 否 |
| **要求最低 Android 操作系统版本** | 选择“是”将要求要使用此应用需具备的最低 Android 操作系统版本。 如果设备上的 Android 版本不符合此要求，将阻止用户访问。<br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。| 否 |
| **要求最低 Android 操作系统版本(仅警告)** | 选择“是”将要求要使用此应用需具备的最低 Android 操作系统版本。 如果设备上的 Android 版本不符合此要求，用户将看到一个通知。 可忽略此通知。<br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。 | 否 |
| **要求最低应用版本** | 选择“是”将要求要使用此应用需具备的最低应用版本。 如果设备上的应用版本不符合此要求，将阻止用户访问。<br><br>由于应用的版本方案之间通常不同，因此，要创建一个针对一个应用的最低应用版本策略（例如“Outlook 版本策略”。 <br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。| 否 |
| **要求最低应用版本(仅警告)** | 选择“是”将建议要使用此应用需具备的最低应用版本。 如果设备上的应用版本不符合此要求，用户将看到一个通知。 可忽略此通知。<br><br>由于应用的版本方案之间通常不同，因此，要创建一个针对一个应用的最低应用版本策略（例如“Outlook 版本策略”。 <br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。| 否 |
| **要求最低 Android 修补版本** | 选择“是”，要求由 Google 发布的最低 Android 安全修补。 如果设备上的 Android 安全修补不符合此要求，将阻止用户访问。<br><br> 此策略设置格式支持日期格式 YYYY-MM-DD。 | 否 |
| **要求最低 Android 修补版本(仅警告)** | 选择“是”，要求由 Google 发布的最低 Android 安全修补。 如果设备上的 Android 安全修补不符合此要求，用户将看到一条通知。 可忽略此通知。<br><br> 此策略设置格式支持日期格式 YYYY-MM-DD。 | 否 |

> [!NOTE]
> 若要深入了解在“访问权限”部分配置给同一组应用和用户的多个 Intune 应用保护设置如何在 Android 上运行，请参阅 [Intune MAM 常见问题](mam-faq.md)。
