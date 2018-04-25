---
title: 手动添加 Windows 10 公司门户应用
titleSuffix: Microsoft Intune
description: 了解如何手动添加 Windows 10 公司门户应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f2c7e449e9931bccd5e736bd09c33e0b42c623e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-using-microsoft-intune"></a>使用 Microsoft Intune 手动添加 Windows 10 公司门户应用

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

最终用户可从 Microsoft 应用商店安装公司门户应用，用于管理设备和安装应用。 但是，如果业务需求需要分配公司门户应用，即使尚未将 Intune 与适用于企业的 Microsoft 应用商店集成，也可以直接从 Intune 手动分配 Windows 10 公司门户应用。

 > [!NOTE]
 > 每次发布应用更新时，此选项都需要分配手动更新。

## <a name="configure-settings-to-show-offline-apps"></a>配置设置以显示脱机应用
1. 转至[适用于企业的 Microsoft Store](https://www.microsoft.com/business-store)，并确保是使用管理员帐户登录的。
2. 选择窗口顶部附近的“管理”选项卡。
3. 在左侧的导航列中选择“设置”。
4. 将“购物体验”部分中的“显示脱机应用”设置为“开”。 这将在适用于企业的 Microsoft Store 中显示脱机许可应用。

## <a name="download-the-offline-company-portal-app"></a>下载脱机公司门户应用
1. 搜索并选择“公司门户”应用。
2. 将“许可证类型”设置为“脱机”。
3. 单击“获取应用”以获取脱机公司门户应用，并将它添加到清单中。
4. 在“公司门户”应用页面上单击“管理”。
5. 选择“Windows 10 所有设备”作为“平台”，然后选择适合的“最低版本”、“体系结构”，并下载应用元数据值。 
6. 单击“下载”，将文件保存到本地计算机。

    ![Windows 10 所有设备和“下载”体系结构 X86 包详细信息的图像](./media/Win10CP-all-devices.png)

7. 下载“所需框架”下的所有包。 必须为 x86、x64 和 ARM 体系结构完成此操作 – 生成共 12 个包。
8. 将公司门户应用上传到 Intune 之前，创建一个文件夹（例如，C:&#92;Company Portal），其中包含按以下方式已结构化的包：
   - 将公司门户包放置在 C:\Company Portal 中。 并在此位置创建一个 Dependencies 子文件夹。  

     ![随 APPXBUN 文件一起保存的 Dependencies 文件夹的图像](./media/Win10CP-Dependencies-save.png)

   - 将依赖项包放置在“Dependencies”文件夹中。 

     > [!NOTE]
     > 如果依赖项未按正确格式放置，Intune 则无法在包上传期间识别并上传文件，从而导致上传失败并出现错误。

9. 在 Azure 门户中返回到 Microsoft Intune。
10. 将公司门户应用作为新应用上传。 将其作为所需的应用分配到所需的目标用户集。  

有关 Intune 如何处理通用应用的依赖项的详细信息，请参阅[通过 Microsoft Intune MDM 部署具有依赖项的 appxbundle](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)。  

## <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>如果已从应用商店安装旧版应用，那么如何更新用户设备上的公司门户？
如果你的用户已从应用商店安装 Windows 8.1 或 Windows Phone 8.1 公司门户应用，那么它们应自动更新到新版本，你或你的用户无需执行任何操作。 如果未更新，则要求用户检查他们是否在设备上启用了应用商店应用的自动更新。   

## <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何将我的旁加载 Windows 8.1 公司门户应用升级到 Windows 10 公司门户应用？
我们推荐的迁移途径是通过将分配操作设置为“卸载”，以删除 Windows 8.1 公司门户应用的分配。 完成此设置后，便可使用上述的任意选项分配 Windows 10 公司门户应用。  

如果需要旁加载应用并且在未使用 Symantec 证书进行签名的情况下分配了 Windows 8.1 公司门户，则直接通过上面的 Intune 部分按照“分配”中的步骤完成升级。

如果需要旁加载应用，并且使用 Symantec 代码签名证书签名和分配了 Windows 8.1 公司门户，请按照以下部分内容的步骤操作。  

## <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何将已签名和旁加载的 Windows Phone 8.1 公司门户应用或 Windows 8.1 公司门户应用升级到 Windows 10 公司门户应用？
我们推荐的迁移路径是通过将分配操作设置为“卸载”，删除 Windows Phone 8.1 公司门户应用或 Windows 8.1 公司门户应用的现有分配。 完成此设置后，便可正常分配 Windows 10 公司门户应用。  

否则，Windows 10公司门户应用需要进行相应更新和签名，以确保遵循升级过程。  

如果 Windows 10 公司门户应用已按此方式签名和分配，则需要在应用商店中可用时为每个新的应用更新重复此过程。 应用商店更新时，应用不会自动更新。  

以下是签名和分配应用的方式：

1. 从 [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) 下载 Microsoft Intune Windows 10 公司门户应用签名脚本。  此脚本需要在主计算机上安装适用于 Windows 10 的 Windows SDK。 要下载用于 Windows 10 的 Windows SDK，请访问 [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 如上所述，从适用于企业的 Microsoft 应用商店下载 Windows 10 公司门户应用。  
3. 运行在脚本标头中详细说明了其输入参数的脚本，对 Windows 10 公司门户应用进行签名（以下进行了提取）。 不需要将依赖项传入该脚本。 只有在应用上载到 Intune 管理控制台时才需要依赖项。

|       参数       |                                                                        描述                                                                        |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                                  定位到源 appxbundle 文件所在位置的路径                                                  |
| OutputWin10AppxBundle | 已签名的 appxbundle 文件 Win81Appx 的输出路径。  定位到 Windows 8.1 或 Windows Phone 8.1 公司门户 (.APPX) 文件所在位置的路径。 |
|      PfxFilePath      |                                       Symantec 企业移动代码签名证书 (.PFX) 文件的路径。                                        |
|      PfxPassword      |                                         Symantec 企业移动代码签名证书的密码。                                          |
|      PublisherId      |          企业的发布者 ID。 如果不存在，则使用 Symantec 企业移动代码签名证书的“使用者”字段。           |
|        SdkPath        |     适用于 Windows 10 的 Windows SDK 的根文件夹路径。 此参数为可选，默认为 ${env:ProgramFiles(x86)}\Windows Kits\10     |

在运行结束时，该脚本将输出签名版本的 Windows 10 公司门户应用。 然后可以通过 Intune 将签名版应用分配为 LOB 应用，后者会将当前分配的版本升级到此新的应用。  

## <a name="next-steps"></a>后续步骤

- [如何将应用分配到组](apps-deploy.md)

