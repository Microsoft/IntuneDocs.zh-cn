---
title: 旁加载 Windows 和 Windows Phone 应用
titleSuffix: Microsoft Intune
description: 了解如何对业务线应用进行签名，以便可以使用 Intune 部署它们。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a4c6d40dc729fb72210c455c7819baaf89de3b
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691829"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>对业务线应用进行签名，以便可以将其部署到具有 Intune 的 Windows 设备

作为 Intune 管理员，可以将业务线 (LOB) 通用应用部署到 Windows 8.1 桌面版或 Windows 10 桌面版和移动版设备，包括公司门户应用。 若要将 .appx 应用部署到 Windows 8.1 桌面版或 Windows 10 桌面版和移动版设备，你可以使用 Windows 设备已信任的公共证书颁发机构颁发的代码签名证书，也可以使用自己的证书颁发机构。

 > [!NOTE]
 > Windows 8.1 桌面版需要使用企业策略来启用旁加载或使用旁加载密钥（对于加入域的设备，自动启用）。 有关详细信息，请参阅 [Windows 8 旁加载](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/)。

## <a name="windows-10-sideloading"></a>Windows 10 旁加载

在 Windows 10 中，旁加载不同于早期版本的 Windows：

- 可以使用企业策略解锁设备以进行旁加载。 Intune 提供名为“受信任的应用安装”的设备配置策略。 对于已经信任用来对 appx 应用进行签名的证书的设备，只需要将此策略设置为 <allow>。

- 不需要 Symantec 电话证书和旁加载许可证密钥。 但是，如果本地证书颁发机构不可用，则可能需要从公共证书颁发机构获取代码签名证书。 有关详细信息，请参阅[代码签名简介](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing)。

### <a name="code-sign-your-app"></a>对你的应用进行代码签名

第一步是对 appx 包进行代码签名。 有关详细信息，请参阅[如何使用 SignTool 对应用包进行签名](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool)。

### <a name="upload-your-app"></a>上传应用

接下来，必须上传已签名的 appx 文件。 有关详细信息，请参阅[将 Windows 业务线应用添加到 Microsoft Intune](lob-apps-windows.md)。

如果按要求将应用部署到用户或设备，则不需要 Intune 公司门户应用。 但是，如果你将应用部署为可供用户使用，则他们可以使用公共 Microsoft Store 中的公司门户应用，使用私有的适用于企业的 Microsoft Store 中的公司门户应用，否则你将需要签署并手动部署 Intune 公司门户应用。

### <a name="upload-the-code-signing-certificate"></a>上传代码签名证书

如果 Windows 10 设备尚未信任证书颁发机构，则在你签署了 appx 包并将其上传到 Intune 服务后，需要将代码签名证书上传到 Intune 门户：

1. 单击“客户端应用”
2. 单击“Windows 企业证书”
3. 选择代码签名证书下的“选择文件”
4. 选择 .cer 文件，然后单击“上传”

现在，任何使用 Intune 服务进行 appx 部署的 Windows 10 桌面版和移动版设备将自动下载相应的企业证书，允许在安装后启动应用程序。

Intune 只部署上传的最新 .cer 文件。 如果你的多个 appx 文件是由不与你的组织关联的不同开发人员创建的，则需要让他们提供未签名的 appx 文件以使用证书进行签名，或者向其提供你的组织使用的代码签名证书。

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>如何续订 Symantec 企业代码签名证书

用于部署 Windows Phone 8.1 移动应用的证书已于 2019 年 2 月 28 日停用，不再可从 Symantec 续订。 如果要部署到 Windows 10 移动版，则可以按照 [Windows 10 旁加载](app-sideload-windows.md#windows-10-sideloading)说明继续使用 Symantec Desktop Enterprise 代码签名证书。

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>如何为业务线 (LOB) 应用安装更新的证书

Windows Phone 8.1

一旦现有的 Symantec Mobile Enterprise 代码签名证书过期，Intune 服务就不能再为此平台部署 LOB 应用。 仍可以使用 SD 卡或通过将文件下载到设备来旁加载未签名的 XAP/APPX 文件。 有关详细信息，请参阅[如何在 Windows Phone 上安装 XAP 文件](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280)。

Windows 8.1 桌面版/Windows 10 桌面版和移动版

如果证书期限已过期，则 appx 文件可能会停止启动。 你应当获得新的 .cer 文件，并按照说明对每个已部署的 appx 文件进行代码签名，然后将所有 appx 文件和更新的 .cer 文件重新上传到 Intune 门户的“Windows 企业证书”部分

## <a name="manually-deploy-windows-10-company-portal-app"></a>手动部署 Windows 10 公司门户应用

如果你不想提供 Microsoft Store 的访问权限，即使尚未将 Intune 与适用于企业的 Microsoft Store (MSFB) 集成，也可以直接从 Intune 手动部署 Windows 10 公司门户应用。 或者，如果已集成，则可以通过[使用 MSFB 部署应用](store-apps-windows.md)部署公司门户应用。

 > [!NOTE]
 > 每次发布应用更新时，此选项都需要部署手动更新。

1. 在[适用于企业的 Microsoft Store](https://www.microsoft.com/business-store) 中登录到帐户，并获取公司门户应用的脱机许可证  版本。  
2. 获得应用之后，选择“**清单**”页中的应用。  
3. 选择“**Windows 10 所有设备**”作为“**平台**”，然后选择相应的**体系结构**并下载。 此应用不需要应用许可证文件。
   ![可供下载的 Windows 10 X86 包详细信息的图像](./media/app-sideload-windows/Win10CP-all-devices.png)
4. 下载“所需框架”下的所有包。 必须对 x86、x64 和 ARM 体系结构完成此操作，并生成如下所示的共 9 个包。

   ![要下载的依赖项文件的图像 ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. 将公司门户应用上载到 Intune 之前，按以下方式创建一个包含构建的包的文件夹（例如，C:\Company Portal）：
   1. 将公司门户包放置在 C:\Company Portal 中。 并在此位置创建一个 Dependencies 子文件夹。  
      ![随 APPXBUN 文件一起保存的 Dependencies 文件夹的图像](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. 将九个依赖项包置于 Dependencies 文件夹中。  
      如果依赖项未按此格式放置，Intune 将无法在包上载期间将其识别并上载，从而导致上载失败并出现以下错误。  
      ![错误消息 - 必须提供 Windows 应用依赖项。](./media/app-sideload-windows/Win10CP-error-message.png)
6. 返回到 Intune，然后将公司门户作为新的应用上载。 将其作为所需的应用部署到所需的目标用户集。  

有关 Intune 如何处理通用应用的依赖项的详细信息，请参阅[通过 Microsoft Intune MDM 部署具有依赖项的 appxbundle](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)。  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>如果已从应用商店安装旧版应用，那么如何更新用户设备上的公司门户？

如果你的用户已从应用商店安装 Windows 8.1 或 Windows Phone 8.1 公司门户应用，那么它们应自动更新到新版本，你或你的用户无需执行任何操作。 如果未更新，则要求用户检查他们是否在设备上启用了应用商店应用的自动更新。

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何将我的旁加载 Windows 8.1 公司门户应用升级到 Windows 10 公司门户应用？

我们推荐的迁移途径是通过将部署操作设置为“卸载”，删除 Windows 8.1 公司门户应用的部署。 完成此操作后，可以使用上面任意选项部署 Windows 10 公司门户应用。  

如果需要旁加载应用并且在未使用 Symantec 证书进行签名的情况下部署了 Windows 8.1 公司门户，则直接通过上面的 Intune 部分按照“部署”中的步骤完成升级。

如果需要旁加载应用，并且使用 Symantec 代码签名证书签名和部署了 Windows 8.1 公司门户，请按照以下部分内容的步骤操作。  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何将已签名和旁加载的 Windows Phone 8.1 公司门户应用或 Windows 8.1 公司门户应用升级到 Windows 10 公司门户应用？

我们推荐的迁移路径是通过将部署操作设置为“卸载”，删除 Windows Phone 8.1 公司门户应用或 Windows 8.1 公司门户应用的现有部署。 完成此操作后，Windows 10 公司门户应用便可以正常部署。  

否则，Windows 10公司门户应用需要进行相应更新和签名，以确保遵循升级过程。  

如果 Windows 10 公司门户应用已按此方式签名和部署，则需要在应用商店中可用时为每个新的应用更新重复此过程。 应用商店更新时，应用不会自动更新。  

以下是签名和部署应用的方式：

1. 从 [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) 下载 Microsoft Intune Windows 10 公司门户应用签名脚本。  此脚本需要在主计算机上安装适用于 Windows 10 的 Windows SDK。 要下载用于 Windows 10 的 Windows SDK，请访问 [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 如上所述，从适用于企业的 Microsoft 应用商店下载 Windows 10 公司门户应用。  
3. 运行在脚本标头中详细说明了其输入参数的脚本，对 Windows 10 公司门户应用进行签名（以下进行了提取）。 不需要将依赖项传入该脚本。 只有在应用上载到 Intune 管理控制台时才需要依赖项。

|       参数       |                                                                    说明                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             定位到源 appxbundle 文件所在位置的路径。                                              |
| OutputWin10AppxBundle |                                                  已签名的 appxbundle 文件 Win81Appx 的输出路径。                                                  |
|       Win81Appx       |                          定位到 Windows 8.1 或 Windows Phone 8.1 公司门户 (.APPX) 文件所在位置的路径。                           |
|      PfxFilePath      |                                   Symantec 企业移动代码签名证书 (.PFX) 文件的路径。                                    |
|      PfxPassword      |                                     Symantec 企业移动代码签名证书的密码。                                      |
|      PublisherId      |      企业的发布者 ID。 如果不存在，则使用 Symantec 企业移动代码签名证书的“使用者”字段。       |
|        SdkPath        | 适用于 Windows 10 的 Windows SDK 的根文件夹路径。 此参数为可选，默认为 ${env:ProgramFiles(x86)}\Windows Kits\10 |

在运行结束时，该脚本将输出签名版本的 Windows 10 公司门户应用。 然后可以通过 Intune 将签名版应用部署为 LOB 应用，后者会将当前部署的版本升级到此新的应用。  
