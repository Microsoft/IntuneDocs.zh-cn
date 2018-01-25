---
title: "在 Intune 中注册 Android 设备 | Microsoft Docs"
titlesuffix: Azure portal
description: "了解如何在 Intune 中注册 Android 设备。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 632a5b2a5f6f5188ef034bdcff927af6a7fe1a59
ms.sourcegitcommit: 53d272defd2ec061dfdfdae3668d1b676c8aa7c6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="enroll-android-devices"></a>注册 Android 设备

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

作为 Intune 管理员，你可以管理 Android 设备，包括 Samsung Knox 标准版设备。 也可以管理 [Android for Work 设备](#enable-enrollment-of-android-for-work-devices)工作配置文件。

运行 Samsung Knox 标准版的设备支持 Intune 进行多用户管理。 即是说，用户可以使用其 Azure AD 凭据登录和注销设备。 该设备仍然受中央管理，无论是否正在使用。 当用户登录时，他们可以访问应用，还可以获得已应用的任何策略。 用户注销时，会清除所有应用数据。

## <a name="prerequisite"></a>先决条件

若准备管理移动设备，必须将移动设备管理 MDM 机构设置为“Microsoft Intune”。 请参阅[设置 MDM 机构](mdm-authority-set.md)，了解有关说明。 第一次设置 Intune 以进行移动设备管理时，只需设置一次此项目。

## <a name="set-up-android-enrollment"></a>设置 Android 注册

默认情况下，Intune 允许注册 Android 和 Samsung Knox 标准版设备。

若要阻止 Android 设备注册或仅阻止个人拥有的 Android 设备注册，请参阅 [Set device type restrictions](enrollment-restrictions-set.md)（设置设备类型限制）。

若要启用设备管理，用户必须通过下载 Intune 公司门户应用（Google Play 中提供），然后打开该应用并按照提示来注册其设备。 托管 Android 设备后，可[分配符合性策略](compliance-policy-create-android.md)、[管理应用](app-management.md)等。

## <a name="enable-enrollment-of-android-for-work-devices"></a>启用 Android for Work 设备的注册

若要启用对[支持 Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) 的设备上的工作配置文件的管理，必须将 Android for Work 绑定添加到 Intune。 若要注册支持 Android for Work、但以前已作为常规 Android 设备注册的设备，这些设备必须取消注册，然后重新注册。

如果使用[设备注册管理器](device-enrollment-manager-enroll.md)帐户注册 Android for Work 设备，则每个帐户最多可注册 10 台设备。

## <a name="add-android-for-work-binding-for-intune"></a>为 Intune 添加 Android for Work 绑定

1. **设置 Intune MDM**<br>
如果你尚未准备就绪，请将[移动设备管理机构设置](mdm-authority-set.md)为“Microsoft Intune”。
2. **配置 Android for Work 绑定**<br>
    作为 Intune 管理员，在“Azure 门户”中，选择“更多服务” > “监视 + 管理” > “Intune”。

   a. 在“Intune”边栏选项卡上，选择“设备注册” > “Android for Work 注册”，然后选择“配置”打开 Google Play 的 Android for Work 网站。 网站将在浏览器的新选项卡中打开。
   ![显示用于配置 Android for Work 绑定的链接的屏幕快照](./media/android-work-bind.png)

   b. 登录到 Google<br>
   在 Google 的登录页上，输入将与此租户的所有 Android for Work 管理任务相关联的 Google 帐户。 这是在公司的 IT 管理员之间共享的 Google 帐户，用于在 Play for Work 控制台中管理和发布应用。 可以使用现有 Google 帐户或创建新帐户。  所选帐户不能与 G-Suite 域相关联。

   c. **提供组织详细信息**<br>
   对于“组织名称”，提供你公司的名称。 对于企业移动性管理 (EMM) 提供程序，应显示 Microsoft Intune。 同意 Android for Work 协议，然后选择“确认”。 你的请求会进行处理。

## <a name="specify-android-for-work-enrollment-settings"></a>指定 Android for Work 注册设置
   Android for Work 仅在特定 Android 设备上受支持。 请参阅 Google 的 [Android for Work 要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")。 支持 Android for Work 的任何设备也支持传统的 Android 管理。 Intune 允许你指定应如何管理支持 Android for Work 的设备：

   - 将所有设备作为 Android 管理。 所有 Android 设备（包括支持 Android for Work 的设备）均将注册为传统的 Android 设备。
   - 将受支持设备作为 Android for Work 管理。 将支持 Android for Work 的所有设备均注册为 Android for Work 设备。 不支持 Android for Work 的任何 Android 设备都注册为传统的 Android 设备。
   - 仅为这些用户组中的用户将受支持设备作为 Android for Work 管理。 可以将 Android for Work 管理目标定位到有限的一组用户。 只有所选组中注册支持 Android for Work 的设备的成员才会注册为 Android for Work 设备。 所有其他成员都会注册为 Android 设备。 这在 Android for Work 试验期间很有用。

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>在托管的 Google Play 商店中批准公司门户应用
需要在托管的 Google Play 商店中批准适用于 Android 的公司门户应用，确保该应用收到自动应用更新。 如不批准，公司门户最终会过时，并无法在 Microsoft 发布重要的 bug 修补程序或新功能时收到它们。

请按以下步骤批准 Intune 公司门户：

1.  在[托管的 Google Play 商店](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal)中浏览到公司门户应用。
2.  使用配置 Android for Work 绑定时所用的 Google 帐户登录托管的 Google Play 商店。
3.  单击“批准”。  此时会打开一个新对话框。
4.  在此对话框中查看各权限，然后单击“批准”。 需要批准这些权限，才能允许公司门户应用管理设备上的工作配置文件。
5.  选择“应用请求新的权限时始终批准”，然后单击“保存”。

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告诉用户如何注册其设备以访问公司资源

请告知最终用户转到 Google Play 下载 Intune 公司门户应用，然后打开该应用并按照提示注册其设备。 该应用会引导用户完成注册过程，说明用户将遇到的情况，以及 IT 管理员在其设备上可以看到和不能看到的内容。

还可以向他们发送有关在线注册步骤的链接：[在 Intune 中注册 Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)。

有关其他用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](end-user-educate.md)
- [通过 Intune 使用 Android 设备](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbind-your-android-for-work-administrative-account"></a>取消绑定 Android for Work 管理帐户

可以关闭 Android for Work 注册和管理。 在 Intune 管理控制台中选择“取消绑定”将从注册中删除所有已注册的 Android for Work 设备。 还将删除 Android for Work 帐户与 Intune 之间的关系。

### <a name="to-unbind-an-android-for-work-account"></a>取消绑定 Android for Work 帐户

1. **取消绑定 Android for Work 绑定**<br>
    作为 Intune 管理员，在“Azure 门户”中，选择“更多服务” > “监视 + 管理” > “Intune”。  在“Intune”边栏选项卡上，选择“设备注册”>“Android for Work 注册”，然后选择“取消绑定”。

2. **同意删除 Android for Work 绑定**<br>
  选择“是”以删除绑定并从 Intune 取消注册所有 Android for Work 设备。
