---
title: 如何配置公司门户应用
titleSuffix: Microsoft Intune
description: 了解如何将特定于公司的品牌应用到 Intune 公司门户应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 33f24a3d7b30973855bb303bb97bf703cd4dc5fa
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567265"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>如何配置 Microsoft Intune 公司门户应用

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Microsoft Intune 公司门户中，用户可以访问公司数据和执行常见任务，比如注册设备、安装应用，以及查找信息以从 IT 部门获得帮助。        

> [!Tip]        
> 当你自定义公司门户时，配置会同时应用于公司门户网站和公司门户应用。 请注意，必须为用户分配 Intune 许可证才能访问公司门户网站。

自定义公司门户有助于为最终用户提供熟悉且有用的体验。 为此，在 Intune 门户中，选择“客户端应用” > “品牌和自定义”，然后配置所需的设置。 

> [!Note]       
> 如果使用的是 Azure 政府，则会向最终用户提供应用日志，由其决定当启动启动获取问题帮助的进程时如何进行共享。 但是，如果使用的不是 Azure 政府，那么当用户启动获取问题帮助的进程时，Windows 10 公司门户将直接向 Microsoft 发送应用日志。 向 Microsoft 发送应用日志可更轻松地排除故障和解决问题。 

## <a name="company-information-and-privacy-statement"></a>公司信息和隐私声明        
公司名称显示为公司门户的标题。 当用户单击隐私链接时，将显示隐私声明。

标有星号 (*) 的字段是必填字段。       


| 字段名称 | 最大长度 | 更多信息 |
|---|---|---|
|**公司名称**| 40 | 此名称显示为公司门户的标题，并且以文本形式显示在整个 Intune 用户体验中。 |
| **隐私声明 URL** |     79     | 你可以指定自己的公司隐私声明，当用户从公司门户中单击隐私链接时，该隐私声明将出现。 必须以 `<https://www.contoso.com>` 格式输入有效的 URL。 |

## <a name="support-information"></a>支持信息      
输入公司的支持信息，为员工提供 Intune 相关问题的联系人。          

|字段名称|最大长度|更多信息|
|---|---|---|
|**联系人姓名** | 40 | 此名称显示在“联系 IT”页上。 |
|**电话号码** | 20 | 此联系人号码会显示在“联系 IT”页上，以便员工与你联系以获得支持。 |
|**电子邮件地址**| 40 | 此联系人地址显示在“联系 IT”页上。 必须以 `alias@domainname.com` 格式输入有效的电子邮件地址。 |
|**网站名称**| 40 | 此名称是为支持网站的 URL 显示的友好名称。 如果指定支持网站 URL 而不指定友好名称，则公司门户中的“联系 IT 部门”页上将显示“转到 IT 网站”。 |
|**网站 URL**| 150 | 如果你拥有希望用户可以使用的支持网站，请在此处指定 URL。 该 URL 必须采用 `https://www.contoso.com` 格式。 如果不指定 URL，则公司门户中的“联系 IT”页上将不会显示支持网站的任何内容。 |
| **其他信息**| 120 | 显示在“联系 IT”页上。 |


## <a name="company-identity-branding-customization"></a>公司标识品牌自定义      
你可以使用公司徽标、公司名称、主题颜色和背景来自定义公司门户。     

### <a name="theme-color-and-logo-in-the-company-portal"></a>公司门户中的主题颜色和徽标
向公司门户应用主题颜色。 选择一种标准颜色，或输入自定义颜色的六位十六进制代码。

|字段名称|更多信息|
|---|---|
|**选择一种标准颜色或输入六位十六进制代码**| 选择“标准”以直观地选择颜色。 选择“自定义”，根据十六进制代码值选择特定颜色。|
|**选择主题颜色**| 选择要应用于公司门户的主题颜色。 可以从标准颜色中选择，也可以输入特定的十六进制代码。 |
|**显示**| 选择是显示“公司徽标和名称”、“仅公司徽标”还是显示“仅公司名称”。 |
|**上传公司徽标**|可以上传公司徽标以在公司门户中显示。 请注意，文本颜色会自动进行选择以提供最高级别的对比度。 为获得最佳外观，请上传带透明背景的徽标。<p><ul><li>最大图像大小：400px x 400px</li><li>最大文件大小：750 KB</li><li>文件类型：PNG、JPG 或 JPEG</li></ul>|

上传徽标后，预览区域将显示带有主题颜色的徽标。 如果选择显示公司名称，该名称将在公司门户中以黑色或白色显示，并将根据主题颜色自动选择以提供最高级别的对比度。 屏幕上的预览区域不会显示公司名称。 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>要在白色或浅色背景上使用的徽标
选择在白色或浅色背景上看起来最佳的徽标。

|字段名称|更多信息|
|---|---|
|**上传徽标**| 如果选择显示公司徽标，则此选项可用。 为获得最佳外观，请上传带透明背景的徽标。<p><ul><li>最大图像大小：400px x 400px</li><li>最大文件大小：750 KB</li><li>文件类型：PNG、JPG 或 JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>公司门户的品牌图像

显示彰显公司品牌的品牌图像。 保存更改后，可以在边栏选项卡顶部的 Intune Web 门户中选择“预览设置”，以查看配置的外观。 请注意，只能在 iOS 设备上预览品牌图像，而不能在 Intune Web 门户上预览。 

|字段名称|更多信息|
|---|---|
|**上传品牌图像**| 使用此选项可以显示品牌图像。 在 iOS 公司门户中，它显示为用户个人资料页上的背景图像。<p><ul><li>建议图像宽度：低于 1125px，但不低于 640px</li><li>最大图像大小：1.3 MB</li><li>文件类型：PNG、JPG 或 JPEG</li></ul>|

合适的品牌图像可以表现出强大的公司品牌意识，增强用户对公司门户的信任。 建议考虑以下用于获取、选择和优化公司门户图像的一些提示。 

- 联系市场部或文艺部。 他们可能已经拥有一组被认可的品牌图像。 他们也可以根据需要帮助你优化图像。 

- 请同时考虑景观和肖像的构图。 图像背景应足以围绕焦点。 可以基于设备大小、方向和平台对图像进行不同的剪裁。 

- 避免使用通用的图库图像。 图像应彰显公司的品牌且能带给用户亲切感。 如果你没有，那么最好不要使用，这也比使用对用户没有任何意义的通用图像要好。 

- 删除不需要的元数据。 图像文件可以附带元数据，例如相机配置文件、地理位置、标题、字幕等。 使用图像优化工具去除此信息，以确保高质量并同时满足文件大小限制。 

在 Intune 中添加或更改品牌图像后，除非公司门户在启动时已识别更改，然后重新启动以显示品牌图像，否则最终用户在 iOS 设备上可能不会看到更改。 

### <a name="brand-image-examples"></a>品牌图像示例

下图显示了 iPad 品牌图像示例：

![iPhone 品牌图像示例的屏幕截图](media/company-portal-app/company-portal-app-03.png)

下图显示了 iPhone 品牌图像示例：

![iPad 品牌图像示例的屏幕截图](media/company-portal-app/company-portal-app-02.png)

## <a name="windows-company-portal-keyboard-shortcuts"></a>Windows 公司门户键盘快捷方式

最终用户可以使用键盘快捷方式（快捷键）在 Windows 公司门户中触发导航、应用和设备操作。

可以在 Windows 公司门户应用中使用以下键盘快捷方式。

| 领域 | 描述 | 键盘快捷方式 |
|:------------------:|:--------------:|:-----------------:|
| 导航菜单 | 导航 | Alt+M |
|  | 住宅 | Alt+H |
|  | 所有应用 | Alt+A |
|  | 已安装的应用 | Alt+I |
|  | 发送反馈 | Alt+F |
|  | 我的个人资料 | Alt+U |
|  | 设置 | Alt+T |
| 主页 - 设备磁贴 | 重命名 | F2 |
|  | 删除 | Ctrl+D 或 Delete |
|  | 检查访问 | Ctrl+M 或 F9 |
| 设备详细信息 | 重命名 | F2 |
|  | 删除 | Ctrl+D 或 Delete |
|  | 检查访问 | Ctrl+M 或 F9 |
| 应用详细信息 | 安装 | Ctrl+I |

最终用户还可以查看 Windows 公司门户应用中的可用快捷方式。

![Windows 公司门户中的可用快捷方式的屏幕截图](media/company-portal-app/company-portal-app-01.png)

## <a name="next-steps"></a>后续步骤

- [使用 Microsoft Intune 手动添加 Windows 10 公司门户应用](store-apps-company-portal-app.md)
