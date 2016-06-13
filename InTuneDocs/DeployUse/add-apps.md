---
# required metadata

title: 添加应用 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 添加应用
在开始使用 Microsoft Intune 部署应用之前，请花些时间来熟悉本主题中介绍的概念。 这些概念将帮助你了解哪些应用可以部署到哪个平台，并了解这样做之前必须具备的先决条件。

## 使用 Intune 可以部署的应用类型
可以将应用部署到 Intune 支持的所有设备类型。 根据你想部署的应用类型，过程和支持的设备将有所不同。 使用以下信息可帮助你了解可以部署和不可以部署的应用类型：


### **Windows Installer（&#42;.exe、&#42;.msi）**
- 这种类型的应用必须支持无用户输入的无提示安装。 你的应用文档应包含用于无提示安装应用的相关命令行选项（如 **/q**）。 可在[此处](https://support.microsoft.com/en-us/kb/227091)找到公共命令行选项的列表。
- 你为应用安装程序文件指定的位置中必须提供应用的安装程序所需的所有其他文件和文件夹。
- 大多数情况下，Windows Installer (.msi) 和 Windows Installer 修补程序 (.msp) 文件不需要任何命令行参数即可通过 Intune 进行安装。 请查看应用文档。 如果需要命令行参数，则必须以“名称=值对”（如 TRANSFORMS=custom_transform.mst）形式输入参数。

这种类型的应用将上载到云存储空间。
### **Android 应用包（&#42;.apk 文件）**
这种类型的应用将上载到云存储空间。
### **iOS 应用包（&#42;.ipa 文件）**
- 若要部署 iOS 应用，你必须拥有有效的 .ipa 包。
- .ipa 包必须由 Apple 签名，并且在预配配置文件中指明的到期日期必须有效。 Intune 可分发企业证书 iOS 应用程序。 并非所有 Apple 开发人员证书应用都受支持。
- 必须向 iOS Developer Enterprise Program 注册你的公司。
- 确保组织的防火墙允许访问 iOS 设置和认证网站。
- 清单文件 (.plist) 不需要与应用一起部署。

这种类型的应用将上载到云存储空间。

目前，最终用户无法直接从适用于 iOS 的 Intune 公司门户应用安装公司应用。 这是因为在 iOS 应用商店中发布的应用程序上放置限制 （请参阅 [应用程序存储区评审准则](https://developer.apple.com/app-store/review/guidelines/))。 用户可以通过在设备上启动公司门户应用并点击“公司应用”磁贴（将打开浏览器并将他们重定向到 Intune Web 门户）来访问公司应用（包括托管的应用商店应用和业务线应用包）。

### **Windows Phone 应用包（&#42;.xap、.appx、.appxbundle）**
- 若要部署应用，你需要一个企业移动代码签名证书。 有关详细信息，请参阅[使用 Microsoft Intune 设置 Windows Phone 管理](set-up-windows-phone-management-with-microsoft-intune.md)。

这种类型的应用将上载到云存储空间。

请参阅下面有关使用 Intune 安装业务线通用 Windows 平台 (UWP) 应用的信息。

### **Windows 应用包 (.appx、.appxbundle)**
- 若要部署应用，你需要一个企业移动代码签名证书。 有关详细信息，请参阅[使用 Microsoft Intune 设置 Windows 设备管理](set-up-windows-device-management-with-microsoft-intune.md)。

这种类型的应用将上载到云存储空间。
### **通过 MDM 的 Windows Installer (&#42;.msi)**
此安装程序类型允许你创建基于 Windows Installer 的应用，并将其部署到运行 Windows 10 的已注册电脑。<br /><br />使用此安装程序类型时，需要考虑下列注意事项：
- 只能上载扩展名为 .msi 的单个文件。
- 该文件的产品代码和产品版本将用于应用检测。
- 将使用该应用的默认重启行为。 Intune 不控制此行为。
- 将为单个用户安装每个用户 MSI 包。
- 将为设备上的所有用户安装每个计算机 MSI 包。
- 当前仅为设备上的所有用户安装双模式 MSI 包。
- 当每个版本的 MSI 产品代码相同时，支持应用更新。

这种类型的应用将上载到云存储空间。
### **外部链接**
在具有下列项目时使用：
- 让用户能从应用商店下载应用的 **URL**。
- 指向基于 Web 的应用的**链接**，该应用从 Web 浏览器中运行。

基于外部链接的应用不存储在 Intune 云存储空间中。
### **来自应用商店的托管 iOS 应用程序**
允许你管理和部署来自应用商店的免费 iOS 应用。 还允许你将[移动应用程序管理策略](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)与[兼容的应用](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)相关联，并在管理员控制台中查看它们的状态。<br /><br />托管 iOS 应用不存储在 Intune 云存储空间中。
> [!TIP]在将[移动设备管理机构设置](get-ready-to-enroll-devices-in-microsoft-intune.md)为 Intune 之前，移动设备选项将不可用。

## 对通用 Windows 平台 (UWP) 应用的支持
Windows 10 设备安装业务线应用时无需旁加载密钥。 但是，注册表项 **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** 必须将值设置为“1”才能启用旁加载。

如果未配置此注册表项，Intune 在你第一次向设备部署应用时会自动将此值设置为“1”。 如果将此值设置为“0”，则 Intune 将无法自动更改此值，业务线应用部署将失败。

通用 Windows 平台业务线应用必须使用代码签名证书签名，并且该证书应在应用部署到的每个设备上受信任。 你可以使用内部 PKI 基础结构中的证书，也可以使用设备上安装的第三方公共根证书中的证书。

在 Windows 10 移动版设备上，可以使用非 Symantec 代码签名证书对通用 **.appx** 应用签名。 对于 **.xap** 应用以及要在 Windows 10 移动版设备上安装且针对 Windows Phone 8.1 生成的 **.appx** 包，必须使用 Symantec 代码签名证书。

## 后续步骤 

接下来，你需要先在 Intune 控制台中添加应用，然后才能部署这些应用。 你可以为[已注册设备](add-apps-for-mobile-devices-in-microsoft-intune.md)或[使用 Intune 客户端软件管理的 Windows 电脑](add-apps-for-windows-pcs-in-microsoft-intune.md)添加应用。

<!--HONumber=May16_HO4-->


