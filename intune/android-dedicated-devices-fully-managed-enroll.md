---
title: 在 Intune 中注册 Android Enterprise 专用设备或完全托管设备
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中注册 Android Enterprise 专用设备或完全托管设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4012dc4046eccf836c73e15409dae182eaf12231
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163256"
---
# <a name="enroll-your-android-enterprise-dedicated-devices-or-fully-managed-devices"></a>注册 Android Enterprise 专用设备或完全托管设备

在 Intune 中设置好 [Android Enterprise 专用设备](android-kiosk-enroll.md)或[完全托管设备](android-fully-managed-enroll.md)之后，即可注册设备。 Android Enterprise 设备的注册方式取决于操作系统。

| 注册方法 | 适用于专用设备和完全托管设备的最低 Android OS 版本 |
| ----- | ----- |
| 近场通信 | 5.1 |
| 令牌输入 | 6.0 |
| QR 码 | 7.0 |
| Zero Touch  | 8.0\* |

\* 参与制造商。

## <a name="enroll-by-using-near-field-communication-nfc"></a>使用近场通信 (NFC) 注册

对于支持 NFC 的设备，可通过创建特殊格式的 NFC 标记来预配设备。 可使用自己的应用或任何 NFC 标记创建者工具。 有关详细信息，请参阅[使用 Microsoft Intune 进行基于 C 的 Android 企业设备注册](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/)和 [Google 的 Android 管理 API 文档](https://developers.google.com/android/management/provision-device#nfc_method)。

## <a name="enroll-by-using-a-token"></a>使用令牌注册

对于 Android 6 及更高版本的设备，可使用令牌注册设备。 使用 afw#setup 注册方法时，Android 6.1 和更高版本还可利用 QR 码扫描。

1. 打开已擦除的设备。
2. 在“欢迎使用”屏幕上，选择语言。
3. 连接到 Wifi，然后选择“下一步”。
4. 接受 Google 条款和条件，然后选择“下一步”。
5. 在 Google 登录屏幕上，输入 afw#setup 而不是 Gmail 帐户，然后选择“下一步”。
6. 为“Android 设备策略”应用选择“安装”。
7. 继续安装此策略。  某些设备可能要求接受附加条款。
8. 在“注册此设备”屏幕上，允许设备扫描 QR 码或选择手动输入令牌。
9. 请按照屏幕上的提示完成注册。

## <a name="enroll-by-using-a-qr-code"></a>使用 QR 码注册

在 Android 7 及更高版本的设备上，可从注册配置文件中扫描 QR 码以注册设备。

> [!Note]
> 浏览器缩放可能使设备无法扫描 QR 码。 增加浏览器缩放比例可解决问题。

1. 要在 Android 设备上启动 QR 读取，请在擦除后看到的第一个屏幕上点击多次。
2. 对于 Android 7 和 Android 8 设备，系统会提示安装 QR 读取器。 Android 9 及更高版本的设备已安装了 QR 读取器。
3. 使用 QR 读取器扫描注册配置文件 QR 码，然后按照屏幕上的提示进行注册。

## <a name="enroll-by-using-google-zero-touch"></a>使用 Google Zero Touch 注册

要使用 Google 的 Zero Touch 系统，设备必须支持该系统，并且与该服务中的一个供应商关联。  有关详细信息，请参阅 [Google 的 Zero Touch 计划网站](https://www.android.com/enterprise/management/zero-touch/)。

1. 在 Zero Touch 控制台中创建新配置。
2. 从 EMM DPC 下拉列表中选择“Microsoft Intune”。
3. 在 Google 的 Zero Touch 控制台中，将以下 JSON 复制/粘贴到 DPC 附加字段中。 将 YourEnrollmentToken 字符串替换为在注册配置文件中创建的注册令牌。 请务必给注册令牌加上双引号。

    ```json
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


## <a name="next-steps"></a>后续步骤
- [部署 Android 应用](apps-deploy.md)
- [添加 Android 配置策略](device-profiles.md)

