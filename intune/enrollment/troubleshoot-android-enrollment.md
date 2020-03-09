---
title: 对 Microsoft Intune 中的 Android 企业设备进行故障排除
description: 对在 Intune 中注册 Android 设备时解决一些最常见问题的建议。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04c726c1dc6af7e92b75335d105de605ef00e712
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652362"
---
# <a name="troubleshoot-android-enterprise-device-problems-in-microsoft-intune"></a>对 Microsoft Intune 中的 Android Enterprise 设备问题进行故障排除

本文可帮助 Intune 管理员了解在使用 Intune 中的 Android Enterprise 设备时出现的问题并对其进行故障排除。

## <a name="apps-on-android-enterprise-devices"></a>Android Enterprise 设备上的应用

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>未通过 Intune 部署的托管 Google Play 应用会显示在工作配置文件中
创建工作配置文件时，设备 OEM 可以在工作配置文件中启用系统应用。 这不受 MDM 提供商控制。

要进行故障排除，请执行下列步骤：

  1. 收集公司门户日志。
  2. 请注意意外出现在工作配置文件中的应用。
  3. 从 Intune 取消注册设备并卸载公司门户。
  4. 安装 [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) 应用，以便在不使用用于测试的 EMM 的情况下创建工作配置文件。
  5. 按照 [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) 中的说明在设备上创建工作配置文件。
  6. 查看工作配置文件中显示的应用。 
  7. 如果 Test DPC 应用中显示了相同的应用程序，则该设备的 OEM 需要应用。

### <a name="unapproved-managed-google-play-for-work-store-apps-arent-being-removed-from-the-client-apps-page-in-intune"></a>不会从 Intune 中的客户端应用页面删除未经批准的托管 Google Play for Work 商店应用
这是预期行为。

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>在 Intune 门户中，不会在“发现的应用”边栏选项卡下报告托管 Google Play 应用
这是预期行为。 “发现的应用”边栏选项卡中仅列出工作配置文件中安装的系统应用。 若要查看已安装的托管 Google Play 应用程序，请使用“托管应用”边栏选项卡  。

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>已注册工作配置文件的设备是否支持 Web 应用？
是。 有关详细信息，请参阅[托管 Google Play Web 链接](../apps/apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="device-management"></a>设备管理

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>已注册工作配置文件的设备上缺少文件路径 Internal storage/Android/Data.com.microsoft.windowsintune.companyportal/files

  **答案**：这是预期行为。 此路径仅为设备管理员（旧版 Android 注册）方案创建。

  若要收集公司门户日志，请执行以下步骤：

  1. 在带有徽章的公司门户应用中，点击“菜单” > “帮助” > “电子邮件支持”，然后点击“发送电子邮件和上传日志”     。 
  2. 如果系统提示“发送帮助请求”，请选择其中一个电子邮件应用  。
  3. 系统会向 IT 管理员生成一封电子邮件，其中包含可提供给 Microsoft 产品支持的事件 ID。

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>托管 Google Play 的上次同步时间好几天没有更新了
这是预期行为。 手动执行此操作时，才会触发同步。

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>注册设备时，需要加密。 是否可以将其关闭？
否，Google 要求对设备进行加密才能创建工作配置文件。 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>Samsung 设备禁止使用 SwiftKey 等第三方键盘
Samsung 开始在 Android 8.0 及更高版本设备上强制执行此限制。 Microsoft 当前正在与 Samsung 合作解决此问题，并将在新信息可用时发布这些信息。

## <a name="remote-actions"></a>远程操作

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>擦除（恢复出厂设置）选项不适用于已注册工作配置文件的设备
这是预期行为。 在工作配置文件方案中，MDM 提供商无法完全控制设备。 唯一可用的选项是“停用”（删除公司数据），此选项将删除整个工作配置文件及其所有内容。

### <a name="is-device-passcode-reset-supported"></a>是否支持设备密码重置？
对于已注册工作配置文件的设备，仅可在以下情况下重置 Android 8.0 或更高版本设备上的工作配置文件密码：
- 管理工作配置文件密码时
- 最终用户允许重置密码。

对于专用设备 (COSU) 和完全托管，支持设备密码重置。


## <a name="next-steps"></a>后续步骤

- [Intune 中的设备注册问题疑难解答](../troubleshoot-device-enrollment-in-intune.md)
- [在 Intune 论坛中提问](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [查看 Microsoft Intune 支持团队博客](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [查看 Microsoft 企业移动性和安全性博客](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)