---
title: "Android MAM 策略设置"
description: "本主题介绍适用于 Android 设备的移动应用管理策略设置。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 04/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e818b6a365ebd4ab1b3c00e42a4dad341debdc75
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2017
---
# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 应用保护策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

可以在 Azure 门户的“设置”边栏选项卡上[配置](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)本主题所述的应用策略设置。
有两种类别的策略设置：数据重定位设置和访问设置。 在本主题中，术语_**策略托管应用**_指使用应用保护策略配置的应用。

##  <a name="data-relocation-settings"></a>数据重定位设置

| Setting | 如何使用 | 默认值 |
|------|------|------|
| **阻止 Android 备份** | 选择“是”，阻止此应用将工作或学校数据备份到 [Android 备份服务](https://developer.android.com/google/backup/index.html)。选择“否”，允许此应用备份工作或学校数据。| 是 |
| **允许应用向其他应用传送数据** | 指定哪些应用可从此应用接收数据： <ul><li> **策略托管应用**：仅允许传输到其他策略托管应用。</li> <li>**所有应用**：允许传输到任何应用。 </li> <li>**无**：不允许将数据传输到任何应用，包括其他策略托管应用。</li></ul> <p>有一些豁免应用和服务，Intune 可能会允许向其传输数据。 有关应用和服务的完整列表，请参阅[数据传输豁免](#Data-transfer-exemptions)。| 所有应用 |
| **允许应用从其他应用接收数据** | 指定哪些应用可将数据传输到此应用： <ul><li>**策略托管应用**：仅允许从其他策略托管应用传输。</li><li>**所有应用**：允许从任何应用传输数据。</li><li>**无**：不允许从任何应用传输数据，包括其他策略托管应用。 </li></ul> <p>有一些豁免应用和服务，Intune 可能会允许从其传输数据。 有关应用和服务的完整列表，请参阅[数据传输豁免](#Data-transfer-exemptions)。 | 所有应用 |
| **阻止“另存为”** | 选择“是”，在此应用中禁用“另存为”选项。 如果你希望允许使用“另存为”，请选择“否”。 <p><br>**选择可保存公司数据的存储服务** <br>用户可以保存到所选的服务（OneDrive for Busines、SharePoint 和本地存储）中。 将阻止所有其他服务。</p> | 否 <br><br> 未选择任何项 |
| **限制剪切、复制和粘贴到其他应用程序** | 指定剪切、复制和粘贴操作何时可用于此应用。 选择： <ul><li>**阻止**：不允许在此应用和任何其他应用间进行剪切、复制和粘贴操作。</li><li>**策略托管应用**：允许在此应用和其他策略托管应用间进行剪切、复制和粘贴操作。</li><li>**带粘贴的策略托管应用**：允许在此应用和其他策略托管应用间进行剪切或复制。 允许将任何应用中的数据粘贴到此应用。</li><li>**任何应用**：不限制从此应用和对此应用进行剪切、复制和粘贴。 | 任何应用 |
|**限制显示在 Managed Browser 内的 Web 内容** | 选择“是”，强制在 Managed Browser 应用中打开应用中的 Web 链接。 <br><br> 对于未在 Intune 中注册的设备，策略托管应用中的 Web 链接将仅可在 Managed Browser 应用中打开。 <br><br> 如果正使用 Intune 管理设备，请参阅[使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问](manage-internet-access-using-managed-browser-policies.md)。 | 否 |
| **加密应用数据** | 选择“是”，在此应用中启用工作或学校数据加密。 Intune 使用 OpenSSL 128 位 AES 加密方案和 Android Keystore 系统安全加密应用数据。 数据在文件 I/O 任务期间同步加密。 始终加密设备存储中的内容。 <br><br> 加密方法**没有**获得 FIPS 140-2 认证。  | 是 |
| **禁用联系人同步** | 选择“是”，阻止应用将数据保存到设备上的本机“联系人”应用。 如果选择“否”，应用可将数据保存到设备上的本机“联系人”应用。 <br><br>执行选择性擦除从应用删除工作或学校数据时，将删除从应用直接同步到本机“联系人”应用的联系人。 无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 目前仅适用于 Microsoft Outlook 应用。 | 否 |
| **禁用打印** | 选择“是”，阻止应用打印工作或学校数据。 | 否 |

  >[!NOTE]
  >**加密应用数据**设置的加密方法**没有**获得 FIPS 140-2 认证。


  ## <a name="data-transfer-exemptions"></a>数据传输豁免

  有一些豁免应用和平台服务，Intune 应用保护策略可能会允许向其或从其传输数据。 例如，Android 上所有支持 Intune 的应用都必须能够将数据传至 Google 文本到语音转换或从其接收数据，以便可以朗读移动设备屏幕上的文本。 此列表可能会更改以反映有利于安全工作效率的服务和应用。

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



##  <a name="access-settings"></a>访问设置

| Setting | 如何使用 | 默认值 |
|------|------|------|
| **需要 PIN 才能进行访问** | 选择“是”，需要 PIN 才可使用此应用。 用户首次在工作或学校环境中运行应用时，将提示其设置此 PIN。 默认值 = **是**。<br><br> 为 PIN 强度配置以下设置： <ul><li>**PIN 重置前的尝试次数**：指定用户重置其 PIN 码前必须成功完成输入的尝试次数。 默认值 = **5**。</li><li> **允许简单 PIN**：选择“是”，允许用户使用简单的 PIN 序列，如 1234 或 1111。 选择“否”，阻止用户使用简单的序列。 默认值 = **是**。 </li><li> **PIN 长度**：指定 PIN 序列必须包含的最小位数。 默认值 = **4**。 </li><li> **允许指纹而非 PIN (Android 6.0+)：**选择“是”，允许用户使用[指纹身份验证](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)而非 PIN 进行应用访问。 默认值 = **是**。</li></ul> 在 Android 设备上，可允许用户通过 [Android 指纹身份验证](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)而非 PIN 证明其身份。 用户尝试通过其工作或学校帐户使用此应用时，会提示他们提供其指纹标识而不是输入 PIN。 </li></ul>| 需要 PIN：是 <br><br> PIN 重置尝试次数：5 <br><br> 允许使用简单 PIN：是 <br><br> PIN 长度：4 <br><br> 允许使用指纹：是 |
| **访问需要公司凭据** | 选择“是”，要求用户使用其工作或学校帐户（而不是输入 PIN）登录进行应用访问。 如果将其设置为“是”，则此设置将替代 PIN 或 Touch ID 的要求。  | 否 |
| **阻止在已越狱或取得 root 权限的设备上运行托管应用** |选择“是”，阻止在已越狱或取得 root 权限的设备上运行此应用。 用户仍能够将此应用用于个人任务，但必须使用其他设备访问此应用中的工作或学校数据。 | 是 |
| **在一定时间后重新检查访问要求（分钟）** | 配置下列设置： <ul><li>**超时**：指重新检查访问要求（在前面的策略中定义）之前的分钟数。 例如，管理员在策略中启用 PIN，则用户打开 MAM 应用就必须输入 PIN。 使用此设置时，用户在 **30 分钟**（默认值）内无需在任何 MAM 应用上再次输入 PIN。</li><li>**脱机宽限期**：指 MAM 应用可脱机运行的分钟数，需在重新检查应用访问要求之前指定该时间（以分钟为单位）。 默认值 = **720** 分钟（12 小时）。 此时间段到期后，应用将要求用户对 AAD 进行身份验证，以便应用可以继续运行。</li></ul>| 超时：30 <br><br> 脱机：720 |
| **擦除应用数据前的脱机时间间隔(天)** | 在脱机运行相应天数（由管理员定义）后，应用会自行执行选择性擦除。 此选择性擦除功能与管理员可在 MAM 擦除工作流中启动的擦除相同。 <br><br> | 90 天 |
| **阻止屏幕捕获和 Android 助手 (Android 6.0+)** | 选择“是”，则在使用此应用时，阻止设备的屏幕捕获和“Android 助手”功能。 选择“是”还会在通过工作或学校帐户使用此应用时，导致应用切换器预览图像模糊。 | 否 |
| **托管设备 PIN 后禁用应用 PIN** | 在已注册设备上检测到设备锁后选择“是”禁用应用 PIN。 | 否 |
