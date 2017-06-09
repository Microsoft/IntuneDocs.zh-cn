---
title: "设置 Android for Work | Microsoft Docs"
description: "使用 Microsoft Intune 为 Android for Work 设备启用移动设备管理 (MDM)。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 644dd302abcb7bb943f1ce8239cd6b98f3e89e79
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="enable-enrollment-of-android-for-work-devices"></a>启用 Android for Work 设备的注册

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要启用 Android for Work 设备的管理，必须将 Android for Work 绑定添加到 Intune。 若要注册支持 Android for Work、但以前已作为常规 Android 设备注册的设备，这些设备必须取消注册，然后重新注册。

## <a name="add-android-for-work-binding-for-intune"></a>为 Intune 添加 Android for Work 绑定

1. 设置 Intune<br>
如果你尚未设置，请通过[将移动设备管理机构设置](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-8#enable-device-enrollment)为“Microsoft Intune”并设置 MDM，为管理移动设备做好准备。

2. 配置 Android for Work 绑定<br>
   以 Intune 管理员身份，打开 [Microsoft Intune 管理控制台](https://manage.microsoft.com)，转到****“管理” &gt; ****“移动设备管理” &gt; ****“Android for Work”，然后单击****“配置” 打开 Google Play 的 Android for Work 网站。  这会在浏览器的新选项卡中打开。

3. **登录到 Google**<br>
   在 Google 的登录页上，输入将与此租户的所有 Android for Work 管理任务相关联的 Google 帐户。 这是在组织的 IT 管理员之间共享的 Google 帐户，用于在 Play for Work 控制台中管理和发布应用。

4. **提供组织详细信息**<br>
   为“组织名称”提供你公司的名称。 对于企业移动性管理 (EMM) 提供程序，应显示 Microsoft Intune。 同意 Android for Work 协议，然后单击“确认”。 你的请求会进行处理。

## <a name="specify-android-for-work-enrollment-settings"></a>指定 Android for Work 注册设置
   Android for Work 仅在特定 Android 设备上受支持。 请参阅 Google 的 [Android for Work 要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")。  支持 Android for Work 的任何设备也支持传统的 Android 管理。  Intune 允许你指定应如何管理支持 Android for Work 的设备：

   - **将所有设备作为 Android 设备管理** - 所有 Android 设备（包括支持 Android for Work 的设备）均将注册为传统的 Android 设备。
   - **将支持的设备作为 Android for Work 设备管理** - 将支持 Android for Work 的所有设备均注册为 Android for Work 设备。 不支持 Android for Work 的任何 Android 设备都注册为传统的 Android 设备。
   - **仅对这些用户组中的用户将支持的设备作为 Android for Work 进行管理** - 使你可以针对一组有限的用户进行 Android for Work 管理。 只有所选组中注册支持 Android for Work 的设备的成员才会注册为 Android for Work 设备。 所有其他成员都会注册为 Android 设备。 这在 Android for Work 试验期间很有用。

## <a name="next-steps-for-android-for-work"></a>适用于 Android for Work 的后续步骤
配置 Android for Work 绑定和设置之后，可以执行以下操作：
- [部署 Android for Work 应用](android-for-work-apps.md)
- [添加 Android for Work 配置策略](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="unbinding-your-android-for-work-administrative-account"></a>取消绑定 Android for Work 管理帐户

可以关闭 Android for Work 注册和管理。 在 Intune 管理控制台中单击“取消绑定”可从注册中删除所有已注册的 Android for Work 设备，并删除 Android for Work 帐户与 Intune 之间的关系。

### <a name="how-to-unbind-an-android-for-work-account"></a>如何取消绑定 Android for Work 帐户

1. **取消绑定 Android for Work 绑定**<br>
   以管理用户身份，打开 [Microsoft Intune 管理控制台](https://manage.microsoft.com)，转到“管理”**** &gt; “移动设备管理”**** &gt; “Android for Work”**** ，然后单击“取消绑定”****。

2. **同意删除 Android for Work 绑定**<br>
  单击“是”可删除绑定并从 Intune 取消注册所有 Android for Work 设备。

