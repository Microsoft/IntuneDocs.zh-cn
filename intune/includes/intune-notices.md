---
title: 包含文件
description: 包含文件
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 1073a38da8a5b2467b1ff8c97b32b93f92e34e4c
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454120"
---
本文中的通知提供了重要信息，可以帮助你为未来的 Intune 更改和功能做好准备。 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>将 Android 公司门户应用更新到最新版本 <!--4536963-->
Intune 定期发布 Android 公司门户应用的更新。 在 2018 年 11 月，我们发布了一次公司门户更新，其中包括后端开关，以便为 Google 从现有通知平台更改为 Google 的 Firebase 云消息传递 (FCM) 做好准备。 随着 Google 停用其现有通知平台并迁移到 FCM，最终用户需要将他们的公司门户应用至少更新到 2018 年 11 月版本，以便继续与 Google Play 商店通信。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
我们的遥测显示，你的设备的公司门户版本低于 5.0.4269.0。 如果未安装该版本或更高版本的公司门户应用，那么，由 IT 专业人员发起的设备操作（如擦除、重置密码）、可用和所需的应用安装以及证书注册可能无法按预期方式工作。 如果设备是在 Intune 中注册的 MDM，可以通过依次进入“客户端应用”、“发现的应用”查看公司门户版本和用户。 选择早期版本的公司门户，可以查看哪些最终用户的设备尚未更新公司门户。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
要求尚未更新的 Android 设备的最终用户通过 Google Play 更新公司门户。 如果某个用户未自动更新公司门户应用，请通知支持人员。 有关 Google FCM 平台和更改的更多信息，请参阅“其他信息”中的链接。

#### <a name="additional-information"></a>其他信息
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Intune 即将推出新的全屏幕体验 <!--4593669-->
我们将在 Azure 门户中向 Intune 推出更新的创建和编辑 UI 体验。 此新体验将使用压缩在一个边栏选项卡中的向导样式格式简化现有工作流。 此更新将消除“边栏选项卡扩展”或需要向下钻取到深度边栏选项卡体验的任何创建和编辑流。 创建工作流也将更新为包含分配（应用分配除外）。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
接下来的几个月里，将同时在 portal.azure.com 和 devicemanagement.microsoft.com 推出 Intune 全屏幕体验。 此 UI 更新不会影响现有策略和配置文件的功能，但你将看到一个稍经修改的工作流。 例如，创建新策略时，你将能够将某些分配设置为此流的一部分，而不是在创建策略后执行此操作。 有关控制台中新体验的屏幕截图，请参阅附加信息中的博客文章。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
不需要执行任何操作，但可以考虑在必要时更新 IT 专业人员指南。 当在 Azure 门户上向 Intune 中的各种边栏选项卡推出此体验时，我们将更新文档。

#### <a name="additional-information"></a>其他信息 
https://aka.ms/intune_fullscreen
