---
title: 使用 Samsung 的 Knox 移动注册自动注册 Android 设备
titlesuffix: Microsoft Intune
description: 了解如何使用 Samsung KME 注册 Android 设备
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 88cb733c688019b2fc5455a0184e968d91e77806
ms.sourcegitcommit: b0ad42fe5b5627e5555b2f9e5bb81bb44dbff078
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2018
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>使用 Samsung 的 Knox 移动注册自动注册 Android 设备

本主题可帮助你使用 Samsung Knox 移动注册 (KME) 来设置 Intune，以注册支持的 Android 设备。 将 Intune 与 Samsung KME 结合使用，可以在最终用户首次打开其设备并连接到 WiFi 或蜂窝网络时注册大量公司自有的 Android 设备。 此外，在使用 Knox 部署应用时，可使用蓝牙或 NFC 来注册设备。

若要使用 Samsung KME 启用 Intune 注册，请按此顺序使用 Intune 和 Samsung Knox 门户：

1. 在 Knox 门户中：
    1. [创建 MDM 配置文件](#create-mdm-profile)
    2. [添加设备](#add-devices)
    3. [向设备分配 MDM 配置文件](#assign-an-mdm-profile-to-devices)
2. 在 Azure 门户中，[将设备标识为“公司自有”](#identify-devices-as-corporate-owned)。
3. 在 Knox 门户中，[配置最终用户登录](#configure-how-end-users-sign-in)。
4. [分配设备](#distribute-devices)。


当从加入 Knox 部署计划的授权经销商购买设备时，设备标识符（序列号和 IMEI）的列表将被自动添加到 Knox 门户。


## <a name="prerequisites"></a>必备条件

若要使用 KME 注册到 Intune，必须首先通过执行以下步骤在 Samsung Knox 门户上注册你的公司：
1.  [确保 KME 在你所在的区域可用](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries)：KME 可用于超过 55 个国家/地区。 确保支持你所在的国家/地区的部署。

2.  [支持的设备](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+)：KME 可用于 Knox 2.4 以上的所有 Samsung 设备。

3.  [网络要求](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm)：请确保你的网络允许必要的防火墙和网络访问规则。

4.  [注册 Samsung 帐户](https://www2.samsungknox.com/en/user/register)：需要使用 Samsung 帐户才能注册和启用 KME，并在一个位置管理所有 Knox Enterprise 权利。

5.  注册审阅：完成并提交你的配置文件后，Samsung 将审阅你的应用程序并立即批准或将其置于待定审阅状态，以进一步跟进。 帐户获得批准后，可以继续执行后续步骤。

## <a name="create-mdm-profile"></a>创建 MDM 配置文件

公司成功注册后，可以使用以下信息在 Knox 门户中为 Microsoft Intune 创建 MDM 配置文件。 有关分步指南，请参阅 [Samsung Knox 配置文件安装向导](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm)说明。

| MDM 配置文件字段| 是否必需？ | 值 |
|-------------------|-----------|-------|
|MDM Server URI     | 否        |将其留空。
|配置文件名称       | 是       |输入选择的配置文件名称。
|description        | 否        |输入说明配置文件的文本。
|MDM 代理 APK      | 是       |https://aka.ms/intune_kme
|跳过安装向导  | 否        |选择此选项以代表最终用户跳过标准设备安装提示。
|允许最终用户取消注册 | 否 | 选择此选项以允许用户取消 KME。
|自定义 JSON        | 否        |将其留空。
| EULA，服务条款和用户协议| 否 | 选择此选项以显示用户接受的与 Knox 相关的协议。
将 Knox 许可证与此配置文件关联 | 否 | 将此选项保持未选定状态。 使用 KME 注册 Intune 不需要使用 Knox 许可证。

## <a name="add-devices"></a>添加设备

若要向设备分配 MDM 配置文件，必须使用以下方法之一将支持的 Samsung Knox 设备添加到 Knox 门户：
- 使用 Samsung 批准的经销商：如果从 Samsung 批准的经销商之一购买设备，请使用此方法。 经销商在获得批准后可以自动为你上载设备。 [访问 Samsung Knox 注册用户指南以了解如何添加经销商](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm)。

- 使用 Knox 部署应用 (KDA)：如果你有现有设备需要使用 KME 进行注册，请使用此方法。 使用此方法，可通过蓝牙或 NFC 将设备添加到 Knox 门户。 [访问 Samsung Knox 注册用户指南以了解如何使用 KDA](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm)。

## <a name="assign-an-mdm-profile-to-devices"></a>将 MDM 配置文件分配给设备
在注册设备前，必须在 Knox 门户中将 MDM 配置文件分配给添加的设备。 [访问 Samsung Knox 注册用户指南以了解设备配置](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm)。

## <a name="identify-devices-as-corporate-owned"></a>将设备标识为“公司自有”
可将使用 KME 注册的设备标识为“公司自有”。 必须在注册设备前执行此操作。 这将允许你执行其他管理任务并收集其他信息，例如完整的电话号码和应用清单。

执行以下步骤以将设备标识为“公司自有”：

1. 将 Knox 门户中的设备列表导出为 CSV 文件。

2. 使用 IMEI 或序列号将 CSV 文件格式化，如[此处](https://docs.microsoft.com/en-us/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number)所示。

3. 在 Azure 门户中，将 CSV 文件上载到“设备注册” > “公司设备标识符” > “添加”。

现在，标识的注册设备将被标记为“公司自有”。

> [!NOTE]
>Intune 将“公司自有”状态自动分配给使用[设备注册管理器](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll)帐户注册的设备。

## <a name="configure-how-end-users-sign-in"></a>配置最终用户的登录方式

对于使用 KME 在 Intune 中注册的设备，可以将最终用户的登录方式配置为如下所示：

- 不含用户名关联：在 Knox 门户上的“设备详细信息”下，将添加的设备的“用户 ID”和“密码”字段留空。 这需要最终用户在注册到 Intune 时输入用户名和密码。

- 含有用户名关联：在 Knox 门户上的“设备详细信息”下，提供添加的设备的“用户 ID”（例如，已分配用户的用户名或[设备注册管理器](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll)帐户）。 这将预填充用户名并需要最终用户在注册到 Intune 时输入密码。

> [!NOTE]
>
>在定义用户关联后，只有关联的用户才可以使用 KME 来注册设备。 即使对设备恢复出厂设置后，也是如此。 当未在 Knox 门户中定义用户关联时，拥有有效的 Intune 许可证的任何用户都可以使用 KME 来注册设备。
>

## <a name="distribute-devices"></a>分配设备

创建和分配 MDM 配置文件后，关联用户名称并在 Intune 中将设备标识为“公司自有”，可以向用户分配设备。

仍需帮助？ 查看完整的 [Knox 移动注册用户指南](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm)。

## <a name="frequently-asked-questions"></a>常见问题
- Google Play 帐户：将设备注册到 Microsoft Intune 无需使用 Google Play 帐户。 但未来对 Intune 公司门户应用的更新可能会要求在设备上使用 Google Play 帐户。

- Google 设备所有者模式：在此预览版中，不支持使用 KME 以 Google 设备所有者模式进行注册。 当前正在调查此方案。

- “密码”字段被忽略：如果“密码”字段使用 Knox 门户中的“设备详细信息”进行填充，则该字段将被 Intune 公司门户应用忽略。 最终用户必须在设备上输入密码才能完成设备注册。

## <a name="getting-support"></a>获取支持
详细了解[如何获取 Samsung KME 的支持](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm)。


