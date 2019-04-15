---
title: 手动添加 Windows 10 公司门户应用
titleSuffix: Microsoft Intune
description: 了解工作人员如何将 Windows 10 公司门户应用从 Microsoft Store 手动添加到其电脑。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a55993e564297016c6c926c6d3be46c32fe1d86b
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57394497"
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>使用 Microsoft Intune 手动添加 Windows 10 公司门户应用

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

若要管理设备和安装应用，你的用户可从 Microsoft Store 安装公司门户应用。 但是，如果业务需求需要将公司门户应用分配给他们，可直接从 Intune 手动分配 Windows 10 公司门户应用。 即使尚未将 Intune 与适用于企业的 Microsoft Store 集成，也可执行此操作。

 > [!NOTE]
 > 本文中介绍的选项需要你在每次发布应用更新时都手动分配更新。

## <a name="configure-settings-to-show-offline-apps"></a>配置设置以显示脱机应用
1. 使用管理员帐户登录到[适用于企业的 Microsoft Store](https://www.microsoft.com/business-store)。
2. 选择窗口顶部附近的“管理”选项卡。
3. 在左窗格中，选择“设置”。
4. 在“购物体验”下，将“显示脱机应用”设置为“开”。  
    将显示脱机许可的应用。

## <a name="download-the-offline-company-portal-app"></a>下载脱机公司门户应用
1. 搜索并选择“公司门户”应用。
2. 将“许可证类型”设置为“脱机”。
3. 选择“获取应用”以获取脱机公司门户应用，并将其添加到清单中。
4. 在“公司门户”应用页上，选择“管理”。
5. 对于“平台”，选择“Windows 10 所有设备”，然后选择适合的“最低版本”、“体系结构”和“下载应用元数据”值。 
6. 选择“下载”，将文件保存到本地计算机。

    ![会选择体系结构为 X86 的 Windows 10 设备](./media/Win10CP-all-devices.png)

7. 选择“下载”以下载“所需框架”下的所有包。  
    必须为 x86、x64 和 ARM 体系结构完成此操作 – 共生成 12 个包。
8. 在将公司门户应用上载到 Intune 前，创建一个文件夹（例如：C:\Company Portal），其中包含使用以下方式构建的包：
   - 将公司门户包放置在 C:\Company Portal 中。 在此位置也创建一个 Dependencies 子文件夹。  

     ![Dependencies 文件夹与 APPXBUN 文件一起保存](./media/Win10CP-Dependencies-save.png)

   - 将依赖项包放置在“Dependencies”文件夹中。 

     > [!NOTE]
     > 如果依赖项未按正确格式放置，Intune 则无法在包上传期间识别并上传文件，从而导致上传失败并出现错误。

9. 在 Azure 门户的 Microsoft Intune 中，将公司门户应用作为新应用上传。 
10. 将公司门户应用作为所需应用分配到你所选的一组目标用户。  

有关 Intune 如何处理通用应用的依赖项的详细信息，请参阅 [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)（通过 Microsoft Intune MDM 部署具有依赖项的 appxbundle）。  

## <a name="frequently-asked-questions"></a>常见问题 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>如果用户已从 Microsoft Store 安装旧版公司门户应用，那么如何更新其设备上的应用？
如果你的用户已从 Microsoft Store 安装 Windows 8.1 或 Windows Phone 8.1 公司门户应用，则他们的应用会自动更新到最新版本，你或你的用户无需执行任何操作。 如果未更新，则要求用户确认他们是否在设备上启用了 Microsoft Store 应用的自动更新。   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何将我的旁加载 Windows 8.1 公司门户应用升级到 Windows 10 公司门户应用？
我们推荐的迁移途径是通过将分配操作设置为“卸载”，以删除 Windows 8.1 公司门户应用的分配。 选择此设置后，可使用任何前面讨论的选项来分配 Windows 10 公司门户应用。  

如果需要旁加载应用且在未通过 Symantec 证书进行签名的情况下分配了 Windows 8.1 公司门户，请通过完成本文前面各节中的步骤来完成升级。

如果需要旁加载应用，并且使用 Symantec 代码签名证书签名并分配了 Windows 8.1 公司门户应用，请按照下一节内容中的步骤进行操作。

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何将已签名和旁加载的 Windows Phone 8.1 公司门户应用或 Windows 8.1 公司门户应用升级到 Windows 10 公司门户应用？
我们推荐的迁移路径是通过将分配操作设置为“卸载”，以删除 Windows Phone 8.1 公司门户应用或 Windows 8.1 公司门户应用的现有分配。 选择此设置后，可正常分配 Windows 10 公司门户应用。  

否则，Windows 10 公司门户应用必须进行相应更新和签名，以确保遵循升级路径。  

如果以此方式签名和分配 Windows 10 公司门户应用，需要在应用商店中提供每个新应用更新时重复此过程。 应用商店更新时，应用不会自动更新。  

以下是签名和分配应用的方式：

1. 下载 [Microsoft Intune Windows 10 公司门户应用签名脚本](https://aka.ms/win10cpscript)。  
    此脚本需要在主计算机上安装适用于 Windows 10 的 Windows SDK。 [下载适用于 Windows 10 的 Windows SDK](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 如上所述，从适用于企业的 Microsoft Store 下载 Windows 10 公司门户应用。  
3. 若要签名 Windows 10 公司门户应用，请使用脚本标头中详细说明的输入参数运行脚本，如下表所示。  
    不需要将依赖项传入该脚本。 只有将应用上传到 Intune 管理控制台时才需要依赖项。

| 参数 |  描述  |
|---|---|
| InputWin10AppxBundle  |  源 appxbundle 文件的路径。 |
| OutputWin10AppxBundle | 已签名的 appxbundle 文件 Win81Appx 的输出路径。 
| Win81Appx  | Windows 8.1 或 Windows Phone 8.1 公司门户 (.APPX) 文件的路径。 |
| PfxFilePath  |  Symantec 企业移动代码签名证书 (.PFX) 文件的路径。  |
| PfxPassword  | Symantec 企业移动代码签名证书的密码。 |
| PublisherId | 企业的发布者 ID。 如果不存在，则使用 Symantec 企业移动代码签名证书的“使用者”字段。 |
| SdkPath | 适用于 Windows 10 的 Windows SDK 的根文件夹路径。 此参数为可选，默认为 ${env:ProgramFiles(x86)}\Windows Kits\10。  |

脚本完成运行后，将输出签名版本的 Windows 10 公司门户应用。 然后可通过 Intune 将签名版应用分配为业务线 (LOB) 应用，后者将当前分配的版本升级到此新应用。  

## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)

