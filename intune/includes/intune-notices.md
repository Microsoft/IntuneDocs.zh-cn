---
title: 包含文件
description: 包含文件
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 373aeea9ab4fcbd075ac2ab18f205f3ddd191a39
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609295"
---
本文中的通知提供了重要信息，可以帮助你为未来的 Intune 更改和功能做好准备。

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>Microsoft Intune 对 Windows 10 移动版的支持即将结束<!--3544938-->
Microsoft 对 Windows 10 移动版的主流支持已于 2019 年 12 月结束。 如本支持声明所述，Windows 10 移动版用户将不再有资格从 Microsoft 接收新的安全更新、非安全修补程序、免费的辅助支持选项或联机技术内容更新。 基于对移动 OS 的全面支持，Microsoft Intune 现在将于 2020 年 5 月 11 日结束对 Windows 10 移动版应用的公司门户和 Windows 10 移动版操作系统的支持。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果贵组织中已部署 Windows 10 移动版设备，那么从现在到 2020 年 5 月 11 日，你可以注册新设备、添加或删除策略和应用，或更新任何管理设置。 5 月 11 日之后，我们将停止新的注册，并最终从 Intune UI 中删除 Windows 10 移动版管理。 设备将不再签入 Intune 服务，我们将删除设备和策略数据。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要如何准备应对此项变化？
你可以查看 Intune 报告，了解可能受影响的设备或用户。 转到“设备”   > “所有设备”  ，并按“OS”进行筛选。 你可以添加附加列，帮助确定你的组织中哪些人员的设备正在运行 Windows 10 移动版。 要求最终用户升级其设备或停止使用这些设备进行公司访问。



### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>更改计划：在 Intune 中注册 Android Enterprise 专用设备体验的更改<!--6114580-->
我们在 11 月版中介绍过，我们已添加对 SCEP 证书部署到 Android Enterprise 专用设备的支持，以便启用对 Wi-Fi 配置文件的基于证书的访问。 此更改涉及 Android Enterprise 专用设备的一些较小的注册流更改。 随着即将推出的 3 月服务更新或 2003 的发布，我们希望你了解一些其他更改。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果在你的环境中管理 Android Enterprise 专用设备，你会开始看到一些更改将于 3 月推出。
- 对于 2019 年 11 月 22 日或 1911 服务更新之前注册的现有 Android 专用设备：这些设备上安装了 Microsoft Intune 应用。 在 3 月 Intune 服务中推出后端更改后，部署到设备并与 Wi-Fi 配置文件关联的 SCEP 证书将开始应用。
- 对于 2019 年 11 月 22 日之后且在 3 月推出更改之前注册的设备：这些设备上安装了 Microsoft Intune 应用。 部署到设备并与 Wi-Fi 配置文件关联的 SCEP 证书将继续适用。
- 对于 3 月推出更改之后的新 Android Enterprise 专用设备注册：最终用户会在注册过程中在设备上看到一组不同的步骤。 注册仍将以当前的方式开始（使用 QR、NFC、零接触或设备标识符），但没有强制应用安装步骤。 相反，Microsoft Intune 应用将自动安装在设备上。 此外，最终用户无需在流中点击“启用 Intune 代理”。 可以将与 WiFi 配置文件关联的 SCEP 证书部署到这些设备。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>针对此更改，我可以做什么准备？
可以更新最终用户指南，并使支持人员了解此更改。 我们将更新“新增功能”页面，并在开始推出此更改时通过消息中心通知你。

#### <a name="additional-information"></a>其他信息
[支持 Android Enterprise 专用设备中的 SCEP 证书](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>针对“Adobe Acrobat Reader for Intune”移动应用的更新支持声明<!--5746776-->
我们在 8 月底的 MC188653 上得知，Adobe Acrobat Reader for Intune 移动应用将于 2019 年 12 月 1 日到期，且 Adobe 计划在其主要的 Acrobat Reader 应用中支持 Intune 应用保护策略。 自那以后，我们收到客户反馈，我们需要提供更多的时间来继续允许 IT 管理员瞄准目标，并让最终用户开始使用 Adobe Acrobat Reader for Intune。 鉴于 Adobe Acrobat Reader for Intune 在最终用户设备上的高使用率及其在企业场景中的重要性，我们希望确保任何体验都能满足组织的应用保护需求。 

虽然由于 Acrobat Reader 移动应用支持应用保护策略并且已经集成了 Intune SDK，我们仍然建议在策略中面向一般的 Acrobat Reader 移动应用，但 Adobe Acrobat Reader for Intune 应用将继续得到支持至 2020 年 3 月 31 日。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
你收到此消息是因为我们的报告表明，贵组织中的一个或多个策略针对的是 Adobe Acrobat Reader for Intune 应用程序，并且/或者你可能已经收到了我们以前的 EOL 通信。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要如何准备应对此项变化？
让最终用户和技术支持人员得知晓此更改。 可以使用[公司门户的支持信息功能](../apps/company-portal-app.md#support-information)来建立与 Intune 相关的问题通道。

#### <a name="additional-information"></a>其他信息
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>执行操作：使用 Microsoft Edge 获取受保护的 Intune 浏览器体验<!--5728447-->
正如我们在过去一年中一直分享的那样，Microsoft Edge 移动版支持与 Managed Browser 相同的一组管理功能，同时提供了更好的最终用户体验。 为了让 Microsoft Edge 提供强大的体验，我们将停用 Intune Managed Browser。 自 2020 年 1 月 27 日开始，Intune 将不再支持 Intune Managed Browser。  

#### <a name="how-does-this-affect-me"></a>这对我有何影响？ 
自 2020 年 2 月 1 日开始，Google Play 商店或 iOS 应用商店中将不再提供 Intune Managed Browser。 届时，虽然新用户将无法下载 Intune Managed Browser 应用，但你仍可以将新的应用保护策略定向到 Intune Managed Browser。 此外，在 iOS 上，向下推送到已注册 MDM 设备的新 Web 剪辑将在 Microsoft Edge 中打开，而不是在 Intune Managed Browser 中打开。  

2020 年 3 月 31 日，Intune Managed Browser 将从 Azure 控制台中删除。 这意味着你将无法再为 Intune Managed Browser 创建新策略。 现有的 Intune Managed Browser 策略不会受到影响。 Intune Managed Browser 将在控制台中显示为无图标的 LOB 应用程序，但现有策略将仍显示为应用的定向策略。 届时，我们还会在“应用程序保护策略”的“数据保护”部分中删除将 Web 内容重定向到 Intune Managed Browser 的选项。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要如何准备应对此项变化？ 
若要确保从 Intune Managed Browser 平稳过渡到 Microsoft Edge，我们建议你主动执行以下步骤： 

1. 使用应用保护策略（也称为 MAM）和应用配置设置，将 Microsoft Edge 定向到 iOS 和 Android。 将这些现有策略定向到 Microsoft Edge，即可对 Microsoft Edge 重复使用 Intune Managed Browser 策略。  
2. 确保环境中所有受 MAM 保护的应用都将应用保护策略设置“限制与其他应用的 Web 内容传输”设置为“策略托管浏览器”。 
3. 通过将托管应用配置设置“com.microsoft.intune.useEdge”设置为 true 来定位所有受 MAM 保护的应用。 从下个月的 1911 版本开始，只需配置“限制与其他应用的 Web 内容传输”设置，以在应用保护策略的“数据保护”部分中选中“Microsoft Edge”，即可完成步骤 2 和步骤 3。 

即将支持 iOS 和 Android 上的 Web 剪辑。 发布此支持后，你需要重定向预先存在的 Web 剪辑，以确保它们在 Microsoft Edge 中而不是在 Managed Browser 中打开。 

#### <a name="additional-information"></a>其他信息
如需了解更多信息，请访问有关[将 Microsoft Edge 与应用保护策略结合使用](../apps/manage-microsoft-edge.md)的文档，或查看我们的[支持博客文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269)。


### <a name="end-of-support-for-legacy-pc-management"></a>停止支持旧版 PC 管理

将于 2020 年 10 月 15 日停止支持旧版 PC 管理。 请将设备升级到 Windows 10，并将它们重新注册为“移动设备管理”(MDM) 设备，以便继续由 Intune 托管它们。

[了解详细信息](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator--5857738--"></a>减少对 Android 设备管理员的支持<!--5857738-->
Android 设备管理员（有时称为“旧版”Android 管理，随 Android 2.2 发布）是一种管理 Android 设备的方法。 不过，[Android Enterprise](../enrollment/connect-intune-android-enterprise.md)（随 Android 5.0 发布）现在提供改进的管理功能。 为了实现更现代化、更丰富、更安全的设备管理，Google 正在减少新 Android 版本中对设备管理员的支持。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
由于 Google 的这些变化，Intune 用户将受到以下几个方面的影响：  
- Intune 将只能在 2020 年第二季度之前为运行 Android 10 及更高版本的设备管理员管理的 Android 设备提供完全支持。 在此之后运行 Android 10 或更高版本的设备管理员管理的设备将无法再进行完全管理。 特别是，受影响的设备将不会收到新的密码要求。
    - Samsung Knox 设备在此期间不受影响，因为通过 Intune 与 Knox 平台的集成提供了扩展支持。 这使你有更多时间来规划过渡弃用设备管理员管理。    
- 设备管理员管理的仍在低于 Android 10 的 Android 版本上运行的 Android 设备将不会受到影响，可以继续完全由设备管理员进行管理。    
- 对于运行 Android 10 及更高版本的所有设备，Google 限制了设备管理员管理代理（如公司门户）访问设备标识符信息的能力。 在设备更新到 Android 10 或更高版本后，此限制将影响以下 Intune 功能：  
    - VPN 的网络访问控制将不再有效。   
    - 使用 IMEI 或序列号将设备识别为公司拥有的设备将不会自动将设备标记为公司拥有的设备。  
    - 在 Intune 中，IMEI 和序列号将不再对 IT 管理员可见。 
        > [!NOTE]
        > 这只会影响 Android 10 及更高版本上设备管理员管理的设备，并且不会影响作为 Android Enterprise 管理的设备。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要如何准备应对此项变化？
为避免在即将到来的 2020 年第三季度出现功能降低的情况，建议采取如下操作：
- 不要将新设备加入设备管理员管理中。
- 如果希望设备接收到 Android 10 的更新，请将其从设备管理员管理迁移到 Android Enterprise 管理和/或应用保护策略。

#### <a name="additional-information"></a>其他信息
- [从设备管理员迁移到 Android Enterprise 的 Google 指南](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [弃用设备管理员 API 计划的 Google 文档](https://developers.google.com/android/work/device-admin-deprecation)



