---
title: 早期版本 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 的早期版本
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 8cd32a7ec99064a36d58a5a714406659d9d16675
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072433"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Microsoft Intune 的早期版本 - 2019 年 1 月

> [!Note]
> NDA 通知：下面的更改依据 Intune 开发。 此信息在 NDA 下共享，但具有严格限制。 请勿在 Twitter、UserVoice、Reddit 等社交媒体或公共网站上发布此信息。 

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表（在 NDA 下共享）。 此信息的提供具有条件限制，并且会不断变化。 请勿发布推文、在 UserVoice 上发帖，或者以其他方式在公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1901 start -->


### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>部署获得许可的适用于企业的 Microsoft Store 联机应用 <!-- 1672660  -->
你将能够在设备上下文中分配所需的适用于企业的 Microsoft Store 联机应用，这些应用已获得许可。 如果以这种方式部署适用于企业的 Microsoft Store 应用，则可在设备上为所有用户安装该应用。 这仅适用于 Windows 10 RS4+ 桌面版设备。 对于获得许可的适用于企业的 Microsoft Store 联机应用，可在客户端应用分配页面中选择安装在设备上下文中。


<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE 应用部署 <!-- 1171203 -->
对于没有注册 (APP-WE) 部署方案的未注册应用保护策略中的 Android 设备，能够使用托管的 Google Play 将应用商店应用和 LOB 应用部署到用户。 具体而言，IT 管理员可以向最终用户提供应用目录以及不再需要最终用户通过允许从未知源进行安装来放宽其设备的安全状况的安装体验。 此外，此部署方案将改进最终用户体验。

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK 将支持 256 位加密密钥 <!-- 1832174 -->
应用保护策略启用加密时，适用于 Android 的 Intune App SDK 将使用 256 位加密密钥。 SDK 将继续提供 128 位密钥支持以与使用旧版 SDK 的内容和应用兼容。


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 策略更新身份验证方法和公司门户应用安装  <!-- 1927359 -->
在已通过 Apple 公司设备注册方法之一经由“设置助理”注册的设备上，Intune 将不再支持由最终用户从应用商店手动安装的公司门户。 仅当在注册过程中使用 Apple 设置助理进行身份验证时，此更改才适用。 此更改也只会影响通过以下方式注册的 iOS 设备：  
* Apple 配置器
* Apple Business Manager
* Apple School Manager
* Apple 设备注册计划 (DEP)

如果用户从应用商店安装公司门户应用，然后尝试通过该应用注册这些设备，则他们将收到错误。 在注册过程中由 Intune 自动推送公司门户时，这些设备应仅使用公司门户。 将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 如果希望 DEP 设备用户具有公司门户，则需要在注册配置文件中指定你的首选项。 此外，公司门户应用中的“标识设备”屏幕很快就会过时。  
若要在已注册的 DEP 设备上安装公司门户，需要转到“Intune”>“客户端应用”，并将其作为具有应用配置策略的托管应用进行推送。 未来的文档中将详细概述执行这些步骤的方式。


### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理模板为公共预览版，并移动到其自己的配置文件 <!-- 3322847 -->
Intune 中的管理模板（“设备配置” > “管理模板”）目前为个人预览版。 借助此更新：管理模板包括可在 Intune 中管理的大约 300 个设置。 以前，这些设置仅存在于组策略编辑器中。
管理模板现已推出公共预览版，管理模板从“设备配置” > “管理模板”移动到“设备配置” > “配置文件” >“创建配置文件”> 在“平台”中，选择“Windows 10 及更高版本”，在“配置文件类型”中，选择“管理模板”。
“已启用报告”适用于：Windows 10 及更高版本

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune macOS 公司门户深色模式 <!-- 3300524 -->
Intune macOS 公司门户现在支持 macOS 的深色模式。 如果在 macOS 10.14+ 设备上启用了深色模式，公司门户会将其外观调整为能反映该模式的颜色。

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995 -->
将更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，以更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一个 MDM 使用的 Apple VPP 令牌 <!-- 1488946 -->
Intune 会检测是否 Intune 和另一个 MDM 同时在使用同一个 Apple 批量采购计划 (VPP) 令牌，并显示相关详细信息。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>“设备符合性仪表板”中的停用设备 <!-- 1981119 -->
未来的某个更新将从设备符合性仪表板中删除已停用的设备。 这会改变符合性数字。


## <a name="notices"></a>通知

此时没有任何活动通知。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。



