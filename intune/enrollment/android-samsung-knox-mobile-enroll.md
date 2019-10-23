---
title: 使用 Samsung 的 Knox Mobile Enrollment 自动注册 Android 设备
titleSuffix: Microsoft Intune
description: 了解如何使用 Samsung KME 注册 Android 设备
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f290370dd6ec05677a7073d9ca3edd854c9aa5e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505582"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>使用 Samsung 的 Knox 移动注册自动注册 Android 设备

本主题可帮助你使用 Samsung Knox 移动注册 (KME) 来设置 Intune，以注册支持的 Android 设备。 将 Intune 与 Samsung KME 结合使用，可以在最终用户首次打开其设备并连接到 WiFi 或蜂窝网络时注册大量公司自有的 Android 设备。 此外，在使用 Knox 部署应用时，可使用蓝牙或 NFC 来注册设备。

若要使用 Samsung KME 启用 Intune 注册，请按此顺序使用 Intune 和 Samsung Knox 门户：

1. 在 Knox 门户中：
    1. [创建 MDM 配置文件](#create-mdm-profile)
    2. [添加设备](#add-devices)
    3. [向设备分配 MDM 配置文件](#assign-an-mdm-profile-to-devices)
2. 在 Knox 门户中，[配置最终用户登录](#configure-how-end-users-sign-in)。
3. [分配设备](#distribute-devices)。


如果你从加入 Knox 部署计划的授权经销商购买设备，设备标识符（序列号和 IMEI）列表会自动添加到 Knox 门户。


## <a name="prerequisites"></a>必备条件

若要使用 KME 注册到 Intune，必须首先通过执行以下步骤在 Samsung Knox 门户上注册你的公司：
1. [确保 KME 适用于你所在的国家/地区](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries)：KME 适用于超过 55 个国家/地区。 请确保支持部署到你所在的国家/地区。

2. [受支持的设备](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+)：KME 适用于所有 Samsung 设备。若要进行 Android 注册，版本至少必须为 Knox 2.4；若要进行 Android Enterprise 注册，版本至少必须为 Knox 2.8。

3. [网络要求](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm)：请确保网络允许必要的防火墙和网络访问规则。

4. [注册 Samsung 帐户](https://www2.samsungknox.com/en/user/register)：必须使用 Samsung 帐户，才能注册和启用 KME，并在一处集中管理所有 Knox Enterprise 权利。

5. 注册审核：在你完成并提交配置文件后，Samsung 会审阅你的申请，然后要么立即批准它，要么将它置于待审阅状态，以供进一步跟进。 在你的帐户获准后，可以继续执行后续步骤。

## <a name="create-mdm-profile"></a>创建 MDM 配置文件

公司成功注册后，可以使用以下信息在 Knox 门户中为 Microsoft Intune 创建 MDM 配置文件。 可以在 Knox 门户中为 Android 和 Android Enterprise 创建 MDM 配置文件。 

### <a name="for-android-enterprise"></a>对于 Android Enterprise

| MDM 配置文件字段| 是否必需？ | 值 | 
|-------------------|-----------|-------| 
|MDM Server URI     | 否        |将其留空。 
|配置文件名称       | 是       |输入选择的配置文件名称。 
|描述        | 否        |输入说明配置文件的文本。 
|MDM 代理 APK      | 是       |https://aka.ms/intune_kme_deviceowner 
|将此应用设置为 Google 设备所有者 | 是 | 选择此选项以注册到 Android Enterprise。 
|支持的 MDM      | 是       |Microsoft Intune 
|保持启用所有系统应用 | 否 | 选择此选项可确保所有应用都已启用并可供配置文件使用。 如果你未选中此选项，设备的应用托盘中只会显示一组有限的系统应用。 电子邮件应用等应用仍然处于隐藏状态。 
|自定义 JSON        | 否        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN":“输入 Intune 注册令牌字符串”}。 了解[如何创建注册配置文件](android-kiosk-enroll.md)。 
| 添加法律协议 | 否 | 将其留空。 

### <a name="for-android"></a>适用于 Android

有关分步指南，请参阅 [Samsung Knox 配置文件安装向导](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm)说明。

| MDM 配置文件字段| 是否必需？ | 值 |
|-------------------|-----------|-------|
|MDM Server URI     | 否        |将其留空。
|配置文件名称       | 是       |输入选择的配置文件名称。
|description        | 否        |输入说明配置文件的文本。
|MDM 代理 APK      | 是       |https://aka.ms/intune_kme
|将此应用设置为 Google 设备所有者 | 否 | 对于 Android，请将此选项保持未选定状态。 此选项仅适用于 Android Enterprise。
|跳过安装向导  | 否        |选中此选项可以为最终用户跳过标准设备安装提示。
|允许最终用户取消注册 | 否 | 选择此选项以允许用户取消 KME。
|自定义 JSON        | 否        |将其留空。
| 添加法律协议 | 否 | 将其留空。
将 Knox 许可证与此配置文件关联 | 否 | 将此选项保持未选定状态。 使用 KME 注册 Intune 不需要使用 Knox 许可证。

## <a name="add-devices"></a>添加设备

若要向设备分配 MDM 配置文件，必须使用以下方法之一将支持的 Samsung Knox 设备添加到 Knox 门户：
- **使用 Samsung 批准的经销商：** 若要从 Samsung 核准经销商之一处购买设备，请使用这种方法。 经销商在获得批准后可以自动为你上载设备。 [访问 Samsung Knox 注册用户指南以了解如何添加经销商](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm)。

- **使用 Knox Deployment App (KDA)：** 如果需要使用 KME 注册现有设备，请使用此方法。 使用此方法，可通过蓝牙或 NFC 将设备添加到 Knox 门户。 [访问 Samsung Knox 注册用户指南以了解如何使用 KDA](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm)。

## <a name="assign-an-mdm-profile-to-devices"></a>将 MDM 配置文件分配给设备
在注册设备前，必须在 Knox 门户中将 MDM 配置文件分配给添加的设备。 [访问 Samsung Knox 注册用户指南以了解设备配置](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm)。

## <a name="configure-how-end-users-sign-in"></a>配置最终用户的登录方式

对于使用 Android KME 在 Intune 中注册的设备，可以将最终用户的登录方式配置为如下所示：

- **不含用户名关联：** 在 Knox 门户中，对于已添加设备，将“设备详细信息”  下的“用户 ID”  和“密码”  字段留空。 此选项要求最终用户必须在注册 Intune 时输入用户名和密码。

- **含用户名关联：** 在 Knox 门户中，对于已添加设备，填写“设备详细信息”  下的“用户 ID”  （如，已分配用户的用户名或[设备注册管理员](device-enrollment-manager-enroll.md)帐户）。 此选项预填充用户名，并要求最终用户必须在注册 Intune 时输入密码。

> [!NOTE]
>
>用户关联仅适用于 Android 设备管理员注册。 在定义用户关联后，只有关联的用户才可以使用 KME 来注册设备。 即使对设备恢复出厂设置后，也是如此。 当未在 Knox 门户中定义用户关联时，拥有有效 Intune 许可证的任何用户都可以使用 KME 来注册设备。
>对于 Android Enterprise 完全托管设备，即使定义了用户关联，也不会将其传递到该设备或将设备与用户关联。
>

## <a name="distribute-devices"></a>分配设备

创建和分配 MDM 配置文件后，关联用户名称并在 Intune 中将设备标识为“公司自有”，可以向用户分配设备。

仍需帮助？ 请查看完整的 [KME 用户指南](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm)。

## <a name="frequently-asked-questions"></a>常见问题

- **设备所有者支持：**  - **设备所有者支持：** Intune 支持使用 KME 门户注册专用设备和完全托管设备。 其他 Android Enterprise 设备所有者模式将在 Intune 中可用时受支持。

- **无工作配置文件支持：** KME 是公司设备注册方法，而在 Android 工作配置文件中注册的设备则确保工作数据和个人数据在个人设备上相互独立。 因此，Intune 不支持使用 KME 向工作配置文件注册设备。

- **恢复出厂设置才能注册到 Android Enterprise：** 若要重新利用已设置的设备，必须在注册到 Android Enterprise 时对设备恢复出厂设置。

- **使用 Google Play 帐户更新：** 向 Microsoft Intune 注册设备不需要使用 Google Play 帐户。 但是，对于 Android 设备管理员注册，未来对 Intune 公司门户应用的更新可能会要求在设备上使用 Google Play 帐户。 注册 Google 设备所有者不需要使用 Google Play 帐户。

- **“密码”字段被忽略：** 如果“密码”  字段是使用 Knox 门户中的“设备详细信息”  进行填充，它便会在 Android 注册期间被 Intune 公司门户应用忽略。 最终用户必须在设备上输入密码才能完成设备注册。


## <a name="getting-support"></a>获取支持
详细了解[如何获取 Samsung KME 的支持](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm)。


