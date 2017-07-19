---
title: "在 Intune 中注册 Android 设备"
titleSuffix: Intune on Azure
description: "了解如何在 Intune 中注册 Android 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 295315dae52662c386055747862717b85ed4b877
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-android-devices"></a>注册 Android 设备

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可借助 Intune 以 Intune 管理员身份管理 Android 设备，包括 Samsung Knox 标准版设备。 也可以管理 [Android for Work 设备](#enable-enrollment-of-android-for-work-devices)上的工作配置文件。

运行 Samsung KNOX 标准版的设备支持 Intune 进行多用户管理。 这意味着最终用户可以使用其 Azure AD 凭据登录和注销设备，并且无论是否正在使用，都会集中管理设备。 当最终用户登录时，他们可以访问应用，还可以获得已应用的任何策略。 用户注销时，会清除所有应用数据。

## <a name="prerequisite"></a>先决条件

必须将 MDM 机构设置为“Microsoft Intune”以便为管理移动设备做好准备。 请参阅[设置 MDM 机构](mdm-authority-set.md)，了解有关说明。 第一次设置 Intune 以进行移动设备管理时，只需设置一次此项目。

## <a name="set-up-android-enrollment"></a>设置 Android 注册

默认情况下，Intune 允许注册 Android 和 Samsung Knox 标准版设备。

若要阻止 Android 设备注册或仅阻止个人拥有的 Android 设备注册，请参阅 [Set device type restrictions](enrollment-restrictions-set.md)（设置设备类型限制）。

若要启用设备管理，用户必须下载 Intune 公司门户应用（Google Play 中提供），然后打开该应用并按照注册提示来注册其设备。 托管 Android 设备后，可[分配符合性策略](compliance-policy-create-android.md)、[管理应用](app-management.md)等。

## <a name="enable-enrollment-of-android-for-work-devices"></a>启用 Android for Work 设备的注册

若要启用对[支持 Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) 的设备上的工作配置文件的管理，必须将 Android for Work 绑定添加到 Intune。 若要注册支持 Android for Work、但以前已作为常规 Android 设备注册的设备，这些设备必须取消注册，然后重新注册。

## <a name="add-android-for-work-binding-for-intune"></a>为 Intune 添加 Android for Work 绑定

1. **设置 Intune MDM**<br>
如果你尚未准备就绪，请将[移动设备管理机构设置](mdm-authority-set.md)为“Microsoft Intune”。

2. **配置 Android for Work 绑定**<br>
    作为 Intune 管理员，在“Azure 门户”中，选择“更多服务” > “监视 + 管理” > “Intune”。

    1. 在“Intune”边栏选项卡上，选择“设备注册”>“Android for Work 注册”，然后单击“配置”打开 Google Play 的 Android for Work 网站。 这会在浏览器的新选项卡中打开。
  ![显示用于配置 Android for Work 绑定的链接的屏幕快照](./media/android-work-bind.png)

    2. **登录到 Google**<br>
   在 Google 的登录页上，输入将与此租户的所有 Android for Work 管理任务相关联的 Google 帐户。 这是在组织的 IT 管理员之间共享的 Google 帐户，用于在 Play for Work 控制台中管理和发布应用。

    3. **提供组织详细信息**<br>
   为“组织名称”提供你公司的名称。 对于企业移动性管理 (EMM) 提供程序，应显示 Microsoft Intune。 同意 Android for Work 协议，然后单击“确认”。 你的请求会进行处理。

## <a name="specify-android-for-work-enrollment-settings"></a>指定 Android for Work 注册设置
   Android for Work 仅在特定 Android 设备上受支持。 请参阅 Google 的 [Android for Work 要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")。 支持 Android for Work 的任何设备也支持传统的 Android 管理。  Intune 允许你指定应如何管理支持 Android for Work 的设备：

   - **将所有设备作为 Android 设备管理** - 所有 Android 设备（包括支持 Android for Work 的设备）均将注册为传统的 Android 设备。
   - **将支持的设备作为 Android for Work 设备管理** - 将支持 Android for Work 的所有设备均注册为 Android for Work 设备。 不支持 Android for Work 的任何 Android 设备都注册为传统的 Android 设备。
   - **仅对这些用户组中的用户将支持的设备作为 Android for Work 进行管理** - 使你可以针对一组有限的用户进行 Android for Work 管理。 只有所选组中注册支持 Android for Work 的设备的成员才会注册为 Android for Work 设备。 所有其他成员都会注册为 Android 设备。 这在 Android for Work 试验期间很有用。

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告诉用户如何注册其设备以访问公司资源

需告知最终用户转到 Google Play 下载 Intune 公司门户应用，然后打开该应用并按照提示注册其设备。 该应用会引导用户完成注册过程，说明用户将遇到的情况，以及 IT 管理员在其设备上可以看到和不能看到的内容。

还可以向他们发送有关在线注册步骤的链接：[在 Intune 中注册 Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)。

有关其他最终用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](end-user-educate.md)
- [通过 Intune 使用 Android 设备](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbinding-your-android-for-work-administrative-account"></a>取消绑定 Android for Work 管理帐户

可以关闭 Android for Work 注册和管理。 在 Intune 管理控制台中单击“取消绑定”可从注册中删除所有已注册的 Android for Work 设备，并删除 Android for Work 帐户与 Intune 之间的关系。

### <a name="how-to-unbind-an-android-for-work-account"></a>如何取消绑定 Android for Work 帐户

1. **取消绑定 Android for Work 绑定**<br>
    作为 Intune 管理员，在“Azure 门户”中，选择“更多服务” > “监视 + 管理” > “Intune”。  在“Intune”边栏选项卡上，选择“设备注册”>“Android for Work 注册”，然后单击“取消绑定”。

2. **同意删除 Android for Work 绑定**<br>
  单击“是”可删除绑定并从 Intune 取消注册所有 Android for Work 设备。
