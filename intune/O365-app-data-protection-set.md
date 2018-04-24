---
title: Microsoft Intune 中 Office 365 应用的数据管理
titlesuffix: ''
description: 了解 Microsoft Intune 中 Office 365 应用的数据管理。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 242ee454ec42c54bb9437fbdf0a7efeca926d193
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps-in-microsoft-intune"></a>你的用户将如何在 Microsoft Intune 中的托管 Office 365 应用上体验基本保护

“管理 Office 365 应用”向导为每个设备平台创建应用保护策略。

该向导将启用以下策略：

**iOS**
* 加密应用数据

**Outlook Web Access (OWA)**
* 加密应用数据
* 访问需要简单 PIN

这些策略确保你可以管理 Office 365 应用，能够在需要时从 Office 应用中擦除工作数据。 它们还确保如若发生设备丢失或被盗时的基本保护，方法是确保加密你的工作数据且必须输入 PIN 才能查看 Office 365 应用中的数据。


本文使用 OneDrive for Business 作为示例来演示 Intune 管理的应用程序的用户体验。


>[!NOTE]
>在个人设备上，最终用户通常要下载应用。 如果设备由移动设备管理 (MDM) 解决方案管理，则你可将应用部署到该设备。

## <a name="user-experience-on-an-ios-device"></a>iOS 设备上的用户体验

1. 启动 OneDrive for Business 应用以打开登录页。  
2. 键入你的工作帐户用户名。 你将会重定向到“Office 365 身份验证”页，以便输入工作凭据。 
3. 凭据成功通过 Azure Active Directory 的身份验证后，将应用应用保护策略，并要求重启 OneDrive for Business 应用。 

   > [!NOTE]
   > “需要重启”消息仅在未注册 Intune 的设备上显示。

4. 重启 OneDrive for Business 应用。 该应用启动时将启用应用保护策略，并提示设置设备的 PIN（如果尚未为设备配置 PIN）。  

   > [!NOTE]
   > 大多数用户不会看到此提示。 只有尚未在其 iOS 设备上启用 PIN 的用户才会看到此提示。

5. 设置 PIN 并进行确认后，返回到 OneDrive for Business 应用。 将看到一个一次性通知，表明你的 IT 管理员正在保护 OneDrive 中的工作数据。 
6. 单击关闭此通知以访问 OneDrive for Business 上的文件。 

>[!NOTE]
>更改已部署策略时，将在下次打开该应用时应用更改。

## <a name="user-experience-on-an-android-device"></a>Android 设备上的用户体验

1. 启动 OneDrive for Business 应用以打开登录页。  <br/> ![OneDrive 应用欢迎屏幕的图像](./media/onedrive-android-welcome.png)
2. 键入你的工作帐户用户名。 你将会重定向到“Office 365 身份验证”页，以便输入工作凭据。 <br/> ![Android 上的 O365 登录的图像](./media/o365-sign-in-android.png)
3. 凭据成功通过 Azure Active Directory 的身份验证后，如果尚未在设备上安装公司门户应用，则会看到一条消息指示你进行安装。 点击“转至应用商店”以继续。 <br/> ![获取公司门户应用的消息的图像](./media/get-company-portal-android.png) <br/>如果已经在手机上安装了公司门户应用，则 OneDrive for Business 应用将自动启动，并且你可以跳到尾注。   

   > [!IMPORTANT]
   > 在 Android 上将 Office 应用设置为由应用保护策略管理后，设备用户必须安装公司门户应用才能访问工作电子邮件和文档，即使最终用户不需要打开或登录到应用来实际阅读电子邮件或文档也是如此。

4. 你现在位于 Google Play 应用商店，可在其中下载和安装公司门户应用。 该应用有助于保护数据安全。 <br/> ![Google Play 应用商店中应用的图像](./media/google-play-get-app-android.png)
5. 完成应用安装后，选择“接受”以接受条款。 OneDrive for Business 应用将自动启动。


>[!NOTE]
>下次打开 OneDrive for Business 时，如果 IT 需要 PIN，则可能会要求你设置 PIN。 设置并确认 PIN 后，便可以继续使用 OneDrive for Business。

![提示输入 PIN 的图像](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>此向导设置哪些策略？

|     |       | |
|----|--------|-|
|**名称**|管理 Office 365 应用| |
| **描述**|由“管理 Office 365 应用”向导创建| |
| |  | |
| **设置名称** |**iOS 策略值** | **Android 策略值** |
|阻止 iTunes 和 iCloud 备份| 否 | N/A |
|阻止 Android 备份 |N/A | 否|
|允许应用向其他应用传送数据 | 所有应用 | 所有应用|
|允许应用从其他应用接收数据| 所有应用 | 所有应用|
|防止“另存为” | 否 | 否|
|限制使用其他应用剪切、复制和粘贴 | 任何应用 | 任何应用 |
|限制显示在企业托管浏览器内的 Web 内容 | 否| 否|
|加密应用数据 | 当设备锁定 | 是|
|禁用联系人同步 | 否| 否|
|禁用打印 | 否 | 否|
|访问需要 PIN | 否 | 是|
|重置 PIN 前的尝试次数 | N/A |5|
|允许使用简单 PIN | N/A |是|
|PIN 长度 | N/A | 4|
|允许使用指纹而不是 PIN | N/A | 是 |
|访问需要公司凭据 | 否 | 否|
|阻止在已越狱或取得 root 权限的设备上运行托管应用 | 否 | 否|
|在一定时间后重新检查访问要求（分钟）- 超时 | 30 | 30|
|在一定时间后重新检查访问要求（分钟）- 脱机宽限期 | 720 |720|
|擦除应用数据之前的脱机间隔时间（天） | 90 | 90|
|阻止屏幕捕获（仅限于 Android 设备） | N/A | 否 |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>为什么只为 Android 设备配置了应用 PIN 策略？
加密在 iOS 和 Android 上的工作方式不同。

在 iOS 上，对于与 Intune 应用保护策略关联的应用，将使用操作系统提供的设备级别的加密对数据进行静态加密。 因此，在启用应用加密策略后，还将自动要求用户具有并输入设备 PIN 才能访问工作数据。 将会提示尚未在设备上配置设备 PIN 的用户创建设备 PIN。

在 Android 上，对于与 Intune 应用保护策略关联的应用，将会在文件 I/O 任务期间对数据进行同步加密。 始终加密设备存储中的内容。 在非 MDM 管理的设备上，应用保护策略不能强制要求设备 PIN。 若要确保用户需要使用某些 PIN 才能访问工作数据，可通过向导启用应用 PIN 策略。

你始终可以编辑这些策略设置以满足你组织的要求。

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>如何查看和编辑由向导创建的策略？
若要查看或更新这些策略，或在 Intune Azure 门户中创建的任何策略，请从仪表板中选择“管理应用” > “应用保护策略”。 策略列表将在右侧打开。 选择想要查看的策略以查看和编辑设置。 <br/>
![用于查看策略的用户界面路径的图像](./media/image-for-faq.png)

## <a name="next-steps"></a>后续步骤
- 详细了解[应用保护策略](app-protection-policy.md)。
