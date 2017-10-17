---
title: "添加应用"
description: "在开始使用 Intune 部署应用之前，请花些时间来熟悉本主题中介绍的概念。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 788e8a7f15566c4b15fec09f3e861d9380278e3f
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="add-apps-with-microsoft-intune"></a>使用 Microsoft Intune 添加应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

在开始使用 Microsoft Intune 部署应用之前，请花些时间来熟悉本主题中介绍的概念。 这些概念有助于了解哪些应用可以部署到哪些平台。 此外，还有助于了解部署应用之前必须准备就绪的先决条件。

## <a name="app-types-that-you-can-deploy"></a>可以部署的应用类型

### <a name="software-installer"></a>软件安装程序

|应用类型|详细信息|
|----------------|-------|
|**Windows Installer (*.exe, *.msi)**|这种类型的应用必须支持无用户输入的无提示安装。 你的应用文档应包含用于无提示安装应用的相关命令行选项（如 **/q**）。 你可以在 [Microsoft Windows Installer 工具的命令行开关](https://support.microsoft.com/kb/227091)中找到常见命令行选项的列表。<br><br>应用的安装程序所需的所有其他文件和文件夹都必须从你为应用安装程序文件指定的位置中提供。<br><br>大多数情况下，Windows Installer (.msi) 和 Windows Installer 修补程序 (.msp) 文件不需要 Intune 安装任何命令行参数。 请查看应用文档。<br><br>如果需要命令行参数，则必须以“名称=值对”（如 TRANSFORMS=custom_transform.mst）形式输入参数。<br><br>此应用类型仅适用于运行 Intune 软件客户端的电脑。|
|**Android 应用包 (*.apk)**|若要部署 Android 应用，你必须拥有有效的 .apk 包。|
|**iOS 应用包 (*.ipa)**|若要部署 iOS 应用，你必须拥有有效的 .ipa 包。<br><br>.ipa 包必须由 Apple 签名，并且预配配置文件中的到期日期必须有效。 Intune 可分发企业证书 iOS 应用程序。<br><br>并非所有 Apple 开发人员证书应用都受支持。<br><br>必须向 iOS Developer Enterprise Program 注册你的公司。<br><br>确保组织的防火墙允许访问 iOS 预配和认证网站。<br><br>你不需要使用该应用部署清单文件 (.plist)。|
|**Windows Phone 应用包（*.xap、.appx、.appxbundle）**|若要部署应用，需要企业移动代码签名证书。 有关详细信息，请参阅[使用 Microsoft Intune 设置 Windows Phone 管理](set-up-windows-device-management-with-microsoft-intune.md)。|
|**Windows 应用包（.appx、.appxbundle）**|若要部署应用，需要企业移动代码签名证书。 有关详细信息，请参阅[使用 Microsoft Intune 设置 Windows 设备管理](set-up-windows-device-management-with-microsoft-intune.md)。|
|**通过 MDM 的 Windows Installer (*.msi)**|你可使用此应用创建基于 Windows Installer 的应用，并将其部署到运行 Windows 10 的已注册电脑。 通过移动设备管理 (MDM) 管理这些电脑。<br /><br />只能上载扩展名为 .msi 的单个文件。<br><br>该文件的产品代码和产品版本将用于应用检测。<br><br>使用该应用的默认重启行为。 Intune 不控制此行为。<br><br>为单个用户安装每用户 MSI 包。<br><br>为设备上的所有用户安装每计算机 MSI 包。<br><br>当前仅为设备上的所有用户安装双模式 MSI 包。<br><br>当每个版本的 MSI 产品代码相同时，支持应用更新。<br>
所有软件安装程序的应用类型都上载到你的云存储空间。

### <a name="external-link"></a>**外部链接**
在你具有以下项时使用外部链接：
- 让用户能从应用商店下载应用的 URL。
- 指向基于 Web 的应用的链接，该应用从 Web 浏览器中运行。

基于外部链接的应用不存储在 Intune 云存储空间中。
### <a name="managed-ios-app-from-the-app-store"></a>**来自应用商店的托管 iOS 应用程序**
你可以使用托管 iOS 应用管理和部署来自应用商店的免费 iOS 应用。 你还可使用托管 iOS 应用将[移动应用管理策略](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)与[兼容的应用](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)相关联，并在管理员控制台中查看它们的状态。<br /><br />托管 iOS 应用不存储在 Intune 云存储空间中。

> [!TIP]
> 在[设置 MDM 机构](prerequisites-for-enrollment.md)为 Intune 之前，移动设备选项将不可用。

## <a name="intune-software-publisher"></a>Intune 软件发行者
从 Intune 管理员控制台中添加或修改应用时，将启动“Microsoft Intune 软件发行者”。 从发行者中，可以选择并配置以下软件安装程序类型：

- 上载应用（适用于计算机的程序或移动设备的应用）以存储在 Intune 云存储中。
- 链接到在线商店或 Web 应用程序。

开始使用软件发行者之前，必须安装 [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851) 的完整版本。 安装之后，可能必须重启计算机，然后软件发行者才会正确打开。

## <a name="cloud-storage-space"></a>云存储空间
使用软件安装程序安装类型创建的所有应用都会上传到 Microsoft Intune 云存储。 Intune 的试用订阅包括 2 千兆字节 (GB) 基于云的存储，用于存储托管应用和更新。 完全订阅包括 20 GB 的存储空间。

可以在“**管理员**”工作区的“**存储空间使用量**”节点中查看所使用的空间量。 可以使用原始购买方法购买额外的 Intune 存储空间。  如果是通过发票或信用卡付款，请访问[订阅管理门户](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)。  否则，请联系合作伙伴或销售内勤。

云存储空间的要求如下：

-   所有应用安装文件都必须位于同一文件夹内。
-   上传的任意文件的最大文件大小是 2 GB。


## <a name="support-for-universal-windows-platform-uwp-apps"></a>对通用 Windows 平台 (UWP) 应用的支持
Windows 10 电脑安装业务线应用时无需旁加载密钥。 但是，注册表项 **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** 必须将值设置为“1”才能启用旁加载。

如果未配置此注册表项，Intune 在你第一次向设备部署应用时会自动将此值设置为“1”。 如果将此值设置为 0，则 Intune 无法自动更改此值，业务线应用部署将失败。

通用 Windows 平台业务线应用必须使用代码签名证书签名，并且该证书应在应用部署到的每个设备上受信任。 你可以使用内部公钥基础结构 (PKI) 中的证书，也可以使用设备上安装的第三方公共根证书中的证书。

在 Windows 10 移动版设备上，可以使用非 Symantec 代码签名证书对通用 **.appx** 应用签名。 对于 **.xap** 应用以及要在 Windows 10 移动版设备上安装且针对 Windows Phone 8.1 生成的 **.appx** 包，必须使用 Symantec 代码签名证书。

### <a name="dependencies-for-uwp-apps"></a>UWP 应用的依赖项

如果将 Windows 10 通用 appxbundle 包添加到 Intune，还必须确保应用的所有依赖项都已上传。
若要上传依赖项，请确保生成应用时创建的“依赖项”文件夹与 .appxbundle 文件本身位于同一文件夹中。
这样，将应用上传到 Intune 时，“依赖项”文件夹中的所有文件也会上传。 以下屏幕截图对此过程进行了说明：


![如何选择 Windows 10 UWP appxbundle 依赖关系](./media/w10-dependencies.png)


## <a name="next-steps"></a>后续步骤

需要先在 Intune 控制台中添加应用，然后才能部署这些应用。 你可以为[已注册设备](add-apps-for-mobile-devices-in-microsoft-intune.md)或[使用 Intune 客户端软件管理的 Windows 电脑](add-apps-for-windows-pcs-in-microsoft-intune.md)添加应用。
