---
title: "如何将 Windows 应用商店应用添加到 Intune"
titleSuffix: Azure portal
description: "了解如何将 Windows 应用商店应用添加到 Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cdc1696175f26dc4bb89fcdd005d88bc0948f86d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>如何将 Windows 应用商店应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


1. 登录到 Azure 门户中。
2. 依次选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”边栏选项卡中，选择“应用信息”。
7. 在“编辑应用”边栏选项卡中，配置以下信息。 完成后，单击“添加”。 根据所选择的应用，此边栏选项卡中的某些值可能已自动填充：
    - **应用名称** - 输入应用的名称，该名称将显示在公司门户中。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **应用描述** - 为应用输入描述。 这将在公司门户中向用户显示。
    - **发行者** — 输入应用的发行者名称。
    - **应用商店 URL** - 输入要创建的应用的应用商店 URL。
    - **最低操作系统** - 从列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别（可选）**- 选择一个或多个内置应用类别或你创建的类别。 这可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **开发者** -（可选）输入应用开发者的名称。
    - **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
    - **说明** - 输入要与此应用关联的任何备注。
    - **上传图标** - 上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
8. 完成后，在“添加应用”边栏选项卡上，选择“保存”。

创建的应用将显示在应用列表中，可在该列表中将其分配到所选择的组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

## <a name="manually-assign-windows-10-company-portal-app"></a>手动分配 Windows 10 公司门户应用
最终用户可从 Microsoft 应用商店安装公司门户应用，用于管理设备和安装应用。 但是，如果业务需求需要分配公司门户应用，即使尚未将 Intune 与适用于企业的 Microsoft 应用商店集成，也可以直接从 Intune 手动分配 Windows 10 公司门户应用。

 > [!NOTE]
 > 每次发布应用更新时，此选项都需要分配手动更新。

1. 在[适用于企业的 Microsoft 应用商店](https://www.microsoft.com/business-store)中登录到帐户，并获取公司门户应用的脱机许可证版本。  
2. 获得应用之后，选择“**清单**”页中的应用。  
3. 选择“**Windows 10 所有设备**”作为“**平台**”，然后选择相应的**体系结构**并下载。 此应用不需要应用许可证文件。
![Windows 10 所有设备和供下载的体系结构 X86 包详细信息的图像](./media/Win10CP-all-devices.png)
4. 下载“所需框架”下的所有包。 必须对 x86、x64 和 ARM 体系结构完成此操作，并生成如下所示的共 9 个包。

![要下载的依赖项文件的图像 ](./media/Win10CP-dependent-files.png)
5. 将公司门户应用上载到 Intune 之前，按以下方式创建一个包含构建的包的文件夹（例如，C:\Company Portal）：
  1. 将公司门户包放置在 C:\Company Portal 中。 并在此位置创建一个 Dependencies 子文件夹。  
  ![随 APPXBUN 文件一起保存的 Dependencies 文件夹的图像](./media/Win10CP-Dependencies-save.png)
  2. 将九个依赖项包置于 Dependencies 文件夹中。  
  如果依赖项未按此格式放置，Intune 将无法在包上载期间将其识别并上载，从而导致上载失败并出现以下错误。  
  ![在应用程序文件夹中找不到此软件安装程序的 Windows 应用依赖项。 你可以继续创建和分配此应用程序，但直到提供缺少的 Windows 应用依赖项后，此应用程序才能运行。](./media/Win10CP-error-message.png)
6. 返回到 Intune，然后将公司门户作为新的应用上载。 将其作为所需的应用分配到所需的目标用户集。  

有关 Intune 如何处理通用应用的依赖项的详细信息，请参阅[通过 Microsoft Intune MDM 部署具有依赖项的 appxbundle](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)。  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>如果已从应用商店安装旧版应用，那么如何更新用户设备上的公司门户？
如果你的用户已从应用商店安装 Windows 8.1 或 Windows Phone 8.1 公司门户应用，那么它们应自动更新到新版本，你或你的用户无需执行任何操作。 如果未更新，则要求用户检查他们是否在设备上启用了应用商店应用的自动更新。   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何将我的旁加载 Windows 8.1 公司门户应用升级到 Windows 10 公司门户应用？
我们推荐的迁移途径是通过将分配操作设置为“卸载”，删除 Windows 8.1 公司门户应用的分配。 完成此操作后，可以使用上面任意选项分配 Windows 10 公司门户应用。  

如果需要旁加载应用并且在未使用 Symantec 证书进行签名的情况下分配了 Windows 8.1 公司门户，则直接通过上面的 Intune 部分按照“分配”中的步骤完成升级。

如果需要旁加载应用，并且使用 Symantec 代码签名证书签名和分配了 Windows 8.1 公司门户，请按照以下部分内容的步骤操作。  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何将已签名和旁加载的 Windows Phone 8.1 公司门户应用或 Windows 8.1 公司门户应用升级到 Windows 10 公司门户应用？
我们推荐的迁移路径是通过将分配操作设置为“卸载”，删除 Windows Phone 8.1 公司门户应用或 Windows 8.1 公司门户应用的现有分配。 完成此操作后，Windows 10 公司门户应用便可以正常分配。  

否则，Windows 10公司门户应用需要进行相应更新和签名，以确保遵循升级过程。  

如果 Windows 10 公司门户应用已按此方式签名和分配，则需要在应用商店中可用时为每个新的应用更新重复此过程。 应用商店更新时，应用不会自动更新。  

以下是签名和分配应用的方式：

1. 从 [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) 下载 Microsoft Intune Windows 10 公司门户应用签名脚本。  此脚本需要在主计算机上安装适用于 Windows 10 的 Windows SDK。 若要下载适用于 Windows 10 的 Windows SDK，请访问 [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 如上所述，从适用于企业的 Microsoft 应用商店下载 Windows 10 公司门户应用。  
3. 运行在脚本标头中详细说明了其输入参数的脚本，对 Windows 10 公司门户应用进行签名（以下进行了提取）。 不需要将依赖项传入该脚本。 只有在应用上载到 Intune 管理控制台时才需要依赖项。

|Parameter | 说明|
| ------------- | ------------- |
|InputWin10AppxBundle |定位到源 appxbundle 文件所在位置的路径 |
|OutputWin10AppxBundle |已签名的 appxbundle 文件 Win81Appx 的输出路径。  定位到 Windows 8.1 或 Windows Phone 8.1 公司门户 (.APPX) 文件所在位置的路径。|
|PfxFilePath |Symantec 企业移动代码签名证书 (.PFX) 文件的路径。 |
|PfxPassword| Symantec 企业移动代码签名证书的密码。 |
|PublisherId |企业的发布者 ID。 如果不存在，则使用 Symantec 企业移动代码签名证书的“使用者”字段。|
|SdkPath | 适用于 Windows 10 的 Windows SDK 的根文件夹路径。 此参数为可选，默认为 ${env:ProgramFiles(x86)}\Windows Kits\10|
在运行结束时，该脚本将输出签名版本的 Windows 10 公司门户应用。 然后可以通过 Intune 将签名版应用分配为 LOB 应用，后者会将当前分配的版本升级到此新的应用。  
