---
title: 在 Intune 中注册 Android 企业展台设备
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中注册 Android 企业展台设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 637fe2d2c764cf78e67e728bfa77567cf12e88ce
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2018
ms.locfileid: "53031987"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-kiosk-devices"></a>设置 Android Enterprise 展台设备的 Intune 注册

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android 通过其公司拥有的一次性解决方案集支持展台型设备。 这些设备用于单一用途，例如数字签名、票据打印或库存管理等。 管理员会将设备的用途限制为有限的一组应用和 Web 链接。 它还可以防止用户在设备上添加其他应用或执行其他操作。

Intune 可帮助你将应用和设置部署到 Android 展台设备。 有关 Android 企业的特定详细信息，请参阅 [Android 企业要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

通过此方式管理的设备在没有用户帐户的情况下注册到 Intune，且不与任何最终用户关联。 它们不适用于个人使用的应用程序或非常需要 Outlook 或 Gmail 等特定于用户的帐户数据的应用。

## <a name="device-requirements"></a>设备要求

设备必须满足以下要求才能作为 Android 企业展台设备进行管理：

- Android OS 版本 5.1 及以上版本。
- 设备必须运行具有 Google Mobile Services (GMS) 连接性的 Android 发行版。 设备必须有可用的 GMS，并且必须能连接到 GMS。

## <a name="set-up-android-kiosk-management"></a>设置 Android 展台管理

若要设置 Android 展台管理，请执行以下步骤：

1. 若准备管理移动设备，必须[将移动设备管理 (MDM) 机构设置为“Microsoft Intune”](mdm-authority-set.md)以获取说明。 第一次设置 Intune 以进行移动设备管理时，只需设置一次此项。
2. [将 Intune 租户帐户连接到你的 Android 企业帐户](connect-intune-android-enterprise.md)。
3. [创建注册配置文件](#create-an-enrollment-profile)
4. [创建设备组](#create-a-device-group)。
5. [注册展台设备](#enroll-the-kiosk-devices)。

### <a name="create-an-enrollment-profile"></a>创建注册配置文件

必须创建注册配置文件，以便注册展台设备。 创建配置文件时，它会提供注册令牌（随机字符串）和 QR 码。 可使用令牌或 QR 码[注册展台设备](#enroll-the-kiosk-devices)，具体取决于 Android OS 和设备版本。

1. 转到 [Intune 门户](https://portal.azure.com)，然后选择“设备注册” > “Android 注册” > “展台和任务设备注册”。
2. 选择“创建”并填写必填字段。
    - **名称**：键入在将配置文件分配给动态设备组时使用的名称。
    - **令牌到期日期**：令牌到期日期。 Google 规定最长为 90 天。
3. 选择“创建”保存该配置文件。

### <a name="create-a-device-group"></a>创建设备组

可将应用和策略定位到已分配或动态设备组。 可按照以下步骤配置动态 AAD 设备组，以自动填充使用特定注册配置文件进行注册的设备：

1. 转到 [Intune 门户](https://portal.azure.com)，然后选择“组” > “所有组” > “新建组”。
2. 在“组”边栏选项卡中，填写必填字段，如下所示：
    - **组类型**：安全
    - **组名称**：键入直观名称（如“出厂 1 设备”）
    - **成员身份类型**：动态设备
3. 选择“添加动态查询”。
4. 在“动态成员身份规则”边栏选项卡中，填写如下字段：
    - **添加动态成员身份规则**：简单规则
    - **添加设备位置**enrollmentProfileName
    - 在中间的框中，选择“匹配”。
    - 在最后一个字段中，输入之前创建的注册配置文件名称。
    有关动态成员身份规则的详细信息，请参阅 [AAD 中的组动态成员身份规则](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)。 
5. 选择“添加查询” > “创建”。

### <a name="replace-or-remove-tokens"></a>替换或删除令牌

可替换或删除令牌和 QR 码。

- **替换令牌**：使用“替换令牌”，可以令牌快要到期时生成新的令牌/QR 码。
- **撤销令牌**：可以立即让令牌/QR 码到期。 从此时起，令牌/QR 码不再可用。 在以下情况下可使用此选项：
    - 意外地与未经授权的一方共享令牌/QR 码
    - 完成所有注册，不再需要令牌/QR 码

替换或撤销令牌/QR 码不会对已注册的设备产生任何影响。

1. 转到 [Intune 门户](https://portal.azure.com)，然后选择“设备注册” > “Android 注册” > “展台和任务设备注册”。
2. 选择要使用的配置文件。
3. 选择“令牌”。
4. 若要替换令牌，请选择“替换令牌”。
5. 若要撤销令牌，请选择“撤销令牌”。

## <a name="enroll-the-kiosk-devices"></a>注册展台设备

创建注册配置文件和动态设备组后，可注册展台设备。 Android 设备的注册方式取决于操作系统。

| 注册方法 | 支持的最低 Android OS 版本 |
| ----- | ----- |
| 近场通信 | 5.1 |
| 令牌输入 | 6.0 |
| QR 码 | 7.0 |
| Zero Touch | 8.0，参与制造商 |

### <a name="enroll-by-using-near-field-communication-nfc"></a>使用近场通信 (NFC) 注册

对于支持 NFC 的 Android 5.1 及更高版本的设备，可通过创建特殊格式的 NFC 标记来预配设备。 可使用自己的应用或任何 NFC 标记创建者工具。 有关详细信息，请参阅 [Google 的 Android Management API 文档](https://developers.google.com/android/management/provision-device#nfc_method)。

### <a name="enroll-by-using-a-token"></a>使用令牌注册

对于 Android 6 及更高版本的设备，可使用令牌注册设备。 **aft#setup** 注册方法时，Android 6.1 和更高版本还可利用 QR 码扫描。

1. 打开已擦除的设备。
2. 在“欢迎使用”屏幕上，选择语言。
3. 连接到 Wifi，然后选择“下一步”。
4. 接受 Google 条款和条件，然后选择“下一步”。
5. 在 Google 登录屏幕上，输入 afw#setup 而不是 Gmail 帐户，然后选择“下一步”。
6. 为“Android 设备策略”应用选择“安装”。
7. 继续安装此策略。  某些设备可能要求接受附加条款。 
8. 在“注册此设备”屏幕上，允许设备扫描 QR 码或选择手动输入令牌。
9. 请按照屏幕上的提示完成注册。 

### <a name="enroll-by-using-a-qr-code"></a>使用 QR 码注册

在 Android 7 及更高版本的设备上，可从注册配置文件中扫描 QR 码以注册设备。

> [!Note]
> 浏览器缩放可能使设备无法扫描 QR 码。 增加浏览器缩放比例可解决问题。

1. 要在 Android 设备上启动 QR 读取，请在擦除后看到的第一个屏幕上点击多次。
2. 对于 Android 7 和 Android 8 设备，系统会提示安装 QR 读取器。 Android 9 及更高版本的设备已安装了 QR 读取器。
3. 使用 QR 读取器扫描注册配置文件 QR 码，然后按照屏幕上的提示进行注册。

### <a name="enroll-by-using-google-zero-touch"></a>使用 Google Zero Touch 注册

要使用 Google 的 Zero Touch 系统，设备必须支持该系统，并且与该服务中的一个供应商关联。  有关详细信息，请参阅 [Google 的 Zero Touch 计划网站](https://www.android.com/enterprise/management/zero-touch/)。 


1. 在 Zero Touch 控制台中创建新配置。
2. 从 EMM DPC 下拉列表中选择“Microsoft Intune”。
3. 在 Google 的 Zero Touch 控制台中，将以下 JSON 复制/粘贴到 DPC 附加字段中。 将 YourEnrollmentToken 字符串替换为在注册配置文件中创建的注册令牌。 请务必给注册令牌加上双引号。

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. 选择“应用”。

## <a name="managing-apps-on-android-kiosk-devices"></a>在 Android 展台设备上管理应用

只有分配类型[设置为必需](apps-deploy.md#to-assign-an-app)的应用才能安装在 Android 展台设备上。 从托管的 Google Play 应用商店安装应用与从 Android 工作配置文件设备安装应用的方式相同。

当应用开发人员向 Google Play 发布更新时，托管设备上的应用会自动更新。

要从 Android 展台设备中删除应用，可执行以下任一操作：
-   删除所需的应用部署。
-   创建应用的卸载部署。


## <a name="next-steps"></a>后续步骤
- [部署 Android 展台应用](apps-deploy.md)
- [添加 Android 展台配置策略](device-profiles.md)
