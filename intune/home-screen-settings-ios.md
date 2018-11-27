---
title: 适用于运行 iOS 的设备的 Microsoft Intune 主屏幕布局设置
titleSuffix: ''
description: 了解可用于在运行 iOS 的设备上自定义主屏幕和停靠的 Microsoft Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 65ecff2a21fa814c3b3518eb92e0378301dbd606
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189244"
---
# <a name="microsoft-intune-home-screen-layout-settings-for-devices-running-ios"></a>适用于运行 iOS 的设备的 Microsoft Intune 主屏幕布局设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用这些设置，可配置运行 iOS 的设备的停靠和主屏幕上应用和文件夹的布局。

如果向运行 iOS 的设备分配了配置文件，则该设备必须处于监督模式下，并运行 iOS 9.3 或更高版本。

1. 从 [Azure 门户中的 Intune](https://portal.azure.com)，导航到[设备配置区域中的“设备功能”](device-features-configure.md)。
2. 在“设备功能”窗格中，选择“主屏幕布局(仅限监督的设备)”。
3. 在“主屏幕布局(仅限监督的设备)”窗格中，选择是想要配置“停靠”还是“页面”布局。

## <a name="add-items-to-the-dock"></a>向停靠添加项目

在“停靠”窗格中，可以向 iOS 屏幕的停靠添加最多 6 个项目或文件夹。 但是，许多设备支持的项目更少，例如，iPhone 设备最多支持 4 个项目。 在这种情况下，在设备上仅显示配置的前四个项目。

1. 选择“添加”向停靠添加项目。
2. 在“添加行”窗格中，选择是要添加“应用”还是“文件夹”。
3. 使用本主题中的信息，配置要显示在停靠面板上的应用和文件夹。
4. 继续添加项目。 完成后，单击每个窗格中的“确定”，直到返回到“创建配置文件”窗格。 选择“创建”。

>[!TIP]
> 可以拖放任何主屏幕和页面列表中的项，以对其重新排序。

### <a name="example"></a>示例

在此示例中，你将停靠屏幕配置为仅显示 Safari、邮件和股票应用。 在下图中，选中了邮件应用，以说明其属性：

![示例 iOS 停靠设置](./media/FfFiUcP.png)

向 iPhone 分配策略时，结果是类似于此屏幕截图的停靠：

![iPhone 上的示例 iOS 停靠布局](./media/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>添加主屏幕页面

添加想要在主屏幕上显示的页面，以及想要在每个页面上显示的应用。 添加到页面的应用按从左到右的方式，以列表中指定的顺序排列。 如果添加了超过页面能够容纳的应用，则该应用将被移动到后续页面。

1. 在“页面”窗格中，选择“添加”。
2. 在“添加行”窗格中，输入“页面名称”。 此名称在 Azure 门户中显示，以供参考，但不在 iOS 设备上显示。
3. 选择“添加”，然后选择是否想要将“应用”或“文件夹”添加到页面。
4. 使用本主题中的信息，配置要显示在页面上的应用和文件夹。

### <a name="example"></a>示例

在此示例中，配置了名为“Contoso”的新页面。 该页面仅显示查找朋友和设置应用。 在下图中，选中了设置应用，以说明其属性：

![iOS 主屏幕设置示例](./media/Jc2OxyX.png)

向 iPhone 分配策略时，结果是类似于此屏幕截图的页面：

![使用修改后的主屏幕的 iOS 设备](./media/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>如何将应用添加到列表

1. 输入“应用名称”。 此名称在 Azure 门户中显示，以供参考，但不在 iOS 设备上显示。
2. 输入想要显示的应用的“应用捆绑 ID”。 请参阅本主题稍后部分中介绍的**适用于内置 iOS 应用的捆绑 ID 引用**，了解帮助信息。
3. 单击“确定”，然后继续添加项，对于设备停靠，最多能添加 **6** 个，对于设备页面，最多能添加 **60** 个。
4. 完成后单击“确定” 。

## <a name="how-to-add-a-folder-to-the-list"></a>如何将文件夹添加到列表

添加到文件夹中的页面的应用按从左到右的方式，以列表中指定的顺序排列。 如果添加了超过页面能够容纳的应用，则该应用将被移动到后续页面。

1. 输入**文件夹名称**。 该名称将显示在用户的设备上。
2. 选择“添加”以在文件夹中创建一个页面。 可以添加最多 20 页。
3. 在“添加行”窗格中，输入页面名称。 此名称在 Azure 门户中显示，以供参考，但不在 iOS 设备上显示。
3. 输入“应用名称”。 此名称在 Azure 门户中显示，以供参考，但不在 iOS 设备上显示。
2. 输入想要显示的应用的“应用捆绑 ID”。 请参阅“如何将应用添加到列表”的相关帮助。
3. 选择“添加”。 可以添加最多 60 项。
4. 完成后单击“确定” 。


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>内置 iOS 应用的捆绑 ID 引用

此列表显示了一些常见的内置 iOS 应用的捆绑 ID。 若要查找其他应用的捆绑 ID，请联系软件供应商。

|||
|-|-|
|应用程序名称|BundleID|
|App Store|com.apple.AppStore|
|计算器|com.apple.calculator|
|日历|com.apple.mobilecal|
|照相机|com.apple.camera|
|时钟|com.apple.mobiletimer|
|指南针|com.apple.compass|
|联系人|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|查找好友|com.apple.mobileme.fmf1|
|查找 iPhone|com.apple.mobileme.fmip1|
|游戏中心|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|运行状况|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes 商店|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|映射|com.apple.Maps|
|消息|com.apple.MobileSMS|
|音乐|com.apple.Music|
|新闻|com.apple.news|
|注意|com.apple.mobilenotes|
|数字|com.apple.Numbers|
|页面|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|照片|com.apple.mobileslideshow|
|播客|com.apple.podcasts|
|提醒|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|设置|com.apple.Preferences|
|股票|com.apple.stocks|
|提示|com.apple.tips|
|视频|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|电子钱包|com.apple.Passbook|
|观看|com.apple.Bridge|
|天气|com.apple.weather|


## <a name="next-steps"></a>后续步骤

现在可将设备配置文件分配到所选择的组。 有关详细信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。
