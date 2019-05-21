---
title: 包含文件
description: 包含文件
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732606"
---
本文中的通知提供了重要信息，可以帮助你为未来的 Intune 更改和功能做好准备。 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>通过设置助理进行身份验证的公司 iOS 设备上的 Intune 公司门户注册工作流的更改内容 <!-- 1927359 -->
使用设置助理进行身份验证时，通过以下任一 Apple 公司设备注册方式注册 iOS 设备的工作流将发生变化：Apple Configurator、Apple Business Manager、Apple School Manager 或 Apple 设备注册计划 (DEP)。 此更改仅适用于注册了用户关联的设备。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
此更改推出时，将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 通过上述方法注册 iOS 设备的工作流也会得到改进。 

- 注册新设备并使用设置助理进行身份验证时，将能够选择是否自动部署公司门户应用。 最终用户将无法再在注册流程中看到“识别你的设备”屏幕和“确认你的设备”屏幕。  
- 对于已通过 Apple 公司设备注册方法之一借助设置助理注册的设备，如果需要启用条件访问，必须执行相应操作。 必须使用特定的 xml [配置应用配置策略](https://aka.ms/enrollment_setup_assistant)，以便将公司门户推送到这些设备。  如果选择以这种方式推送公司门户，最终用户将无法再在注册流程中看到“识别你的设备”屏幕和“确认你的设备”屏幕。 
- 在此更改推出之后，如果你还没有使用上述应用配置文件部署公司门户，并且最终用户从 App Store 下载公司门户应用，那么，他们可以登录，但会收到一条错误消息。 他们将无法使用该应用进行条件访问。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
如果计划使用修改后的工作流，则需要更新最终用户指南，以表明：

- 最终用户将无法再在注册流程中看到上述两个屏幕。 
- 他们需要在公司门户自动部署时登录到该门户，而不是从 App Store 下载。 

如有需要，现在可以选择创建一个应用配置策略，为此更改做好准备。 推出这个新的工作流后，你将能够在控制台中看到更新的注册配置文件。 我们还会通过消息中心向你发送有关此推出的通知。 然后，需要执行操作，以便最终用户可以在借助设置助理进行身份验证后，通过 DEP 进行注册，并且你可以使用公司门户进行条件访问。

#### <a name="additional-information"></a>其他信息 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>将 Android 公司门户应用更新到最新版本 <!--4536963-->
Intune 定期发布 Android 公司门户应用的更新。 在 2018 年 11 月，我们发布了一次公司门户更新，其中包括后端开关，以便为 Google 从现有通知平台更改为 Google 的 Firebase 云消息传递 (FCM) 做好准备。 随着 Google 停用其现有通知平台并迁移到 FCM，最终用户需要将他们的公司门户应用至少更新到 2018 年 11 月版本，以便继续与 Google Play 商店通信。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
我们的遥测显示，你的设备的公司门户版本低于 5.0.4269.0。 如果未安装该版本或更高版本的公司门户应用，那么，由 IT 专业人员发起的设备操作（如擦除、重置密码）、可用和所需的应用安装以及证书注册可能无法按预期方式工作。 如果设备是在 Intune 中注册的 MDM，可以通过依次进入“客户端应用”、“发现的应用”查看公司门户版本和用户。 选择早期版本的公司门户，可以查看哪些最终用户的设备尚未更新公司门户。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
要求尚未更新的 Android 设备的最终用户通过 Google Play 更新公司门户。 如果某个用户未自动更新公司门户应用，请通知支持人员。 有关 Google FCM 平台和更改的更多信息，请参阅“其他信息”中的链接。

#### <a name="additional-information"></a>其他信息
https://firebase.google.com/docs/cloud-messaging/