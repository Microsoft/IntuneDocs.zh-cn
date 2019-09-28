---
title: 技术支持疑难解答门户
titleSuffix: Microsoft Intune
description: 支持人员使用疑难解答门户来解决用户的技术问题。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a4e6cbf2d9edcff83ae756c2dbcf098cae0ae54
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2019
ms.locfileid: "71301860"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>使用疑难解答门户帮助公司的用户

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

通过故障排除门户，技术支持人员和 Intune 管理员可查看用户信息，处理用户求助请求。 设有支持人员的组织可以为一组用户分配技术支持人员  。 技术支持人员可使用“疑难解答”窗格  。

“疑难解答”窗格中也显示用户注册问题  。 问题的相关详细信息和建议的修正步骤可帮助管理员和支持人员排查问题。 某些注册问题可能无法捕获，还有某些错误可能没有修正建议。

有关添加技术支持人员角色的相关步骤，请参阅 [Intune 的基于角色的管理控制 (RBAC)](/intune/role-based-access-control)

当用户就 Intune 技术问题联系支持人员时，技术支持人员会输入该用户的名字。 Intune 可显示有助于解决许多第 1 层问题的有用数据，包括：

- 用户状态
- 分配
- 合规性问题
- 设备未响应
- 设备不具有 VPN 或 Wi-fi 设置
- 应用安装失败

## <a name="to-review-troubleshooting-details"></a>查看疑难解答详细信息

在“疑难解答”窗格中，选择“选择用户”以查看用户信息  。 用户信息可以帮助你了解用户及其设备的当前状态。  

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格中，选择“疑难解答”   。
4. 单击“选择”，选择要进行故障排除的用户  。
5. 通过键入名称或电子邮件地址选择用户。 单击“选择”  。 有关用户的疑难解答信息将显示在“疑难解答”窗格中。 下表介绍了相关信息。

> [!Note]  
> 还可通过浏览器前往 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) 来访问“疑难解答”窗格  。

## <a name="areas-of-troubleshooting-dashboard"></a>疑难解答仪表板区域

可使用“疑难解答”窗格来查看用户信息  。

![故障排除仪表板，其中包含下表描述的编号区域](/intune/media/troubleshooting-dash.png)

| 领域 | 名称 | 描述 |
| ---  | ---  | ---         |
| 1.   | 帐户状态  | 显示当前 Intune 租户状态为“活动”或“非活动”   。       |
| 2.   | 用户选择  | 当前所选用户的名称。 单击“更改用户”可选择新用户  。       |
| 3.   | 用户状态  | 显示用户的 Intune 许可证状态、设备数目、每个设备的符合性、应用数目以及应用的符合性。       |
| 4.   | 用户信息  | 使用该列表在窗格中选择要查看的详细信息。 <br>可选内容如下： <ul><li>客户端应用<li>相容性策略<li> 配置策略<li>应用保护策略 <li>注册限制</ul>      |
| 5.   | 组成员资格  | 显示所选用户所属的当前组。       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>注册失败参考

注册失败表列出了失败的注册尝试。 下表中列出的设备可能随后会在另一次尝试中成功注册。 部分失败的尝试可能没有列出。 并非所有失败的操作都有缓解信息。

| 表列 | 描述 |
|-------------|----------|
| 注册开始 | 用户首次注册的开始时间。 |
| 操作系统 | 设备的操作系统。 |
| OS 版本 | 设备的操作系统版本。 |
| 失败 | 失败原因。 |

### <a name="failure-details"></a>失败详细信息

选择失败行时，可以获取更多详细信息。

| 部分 | 描述 |
|-------------|----------|
| 失败详细信息 | 对失败更详细的说明。 |
| 可能有效的修正措施 | 解决该错误的推荐步骤。 部分失败可能没有对应的修正措施。 |
| 资源（可选） | 延伸阅读材料或门户中执行操作的区域的链接。 |

### <a name="enrollment-errors"></a>注册错误

| 错误 | 详细信息 |
|-------------|----------|
| iOS 超时或失败 | 用户在完成注册时用时过长导致设备与 Intune 之间出现超时。 |
| 未找到用户或用户未得到授权 | 用户缺少许可证或已从该服务中删除。 |
| 设备已注册 | 有人试图在仍由其他用户注册的设备上使用公司门户注册设备。 |
| 未能载入至 Intune | 尝试注册时未配置 Intune 移动设备管理 (MDM) 机构。 |
| 注册授权失败 | 尝试注册时使用的是旧版公司门户。 |
| 设备不受支持 | 设备不符合 Intune 注册的最低要求。 |
| 不符合注册限制 | 管理员配置的注册限制导致此注册被阻止。 |
| 设备版本太低 | 管理员配置的注册限制需要更高版本的设备。 |
| 设备版本太高 | 管理员配置的注册限制需要更低版本的设备。 |
| 不能以个人身份注册设备 | 管理员配置的注册限制阻止个人注册，且失败的设备未预定义为企业设备。 |
| 已阻止设备平台 | 管理员配置了阻止此设备平台的注册限制。 |
| 批量令牌过期 | 预配包中的批量令牌已过期。 |
| 找不到 Autopilot 设备或详细信息 | 尝试注册时，找不到 Autopilot 设备。 |
| 找不到或未分配 Autopilot 配置文件 | 设备没有有效的 Autopilot 配置文件。 |
| 意外的 Autopilot 注册方法 | 设备尝试使用不受允许的方法注册。 |
| 已删除 Autopilot 设备 | 已从此帐户的 Autopilot 中删除尝试注册的设备。 |
| 已达到设备上限 | 管理员配置的设备限制导致此注册被阻止。 |
| Apple 载入 | 目前所有 iOS 设备注册都被阻止，因为 Intune 中缺少 Apple MDM 推送证书，或该证书已过期。 |
| 设备未预先注册 | 设备未预先注册为公司，且所有个人注册都已被管理员阻止。 |
| 功能不受支持 | 用户可能试图通过与 Intune 配置不兼容的方法进行注册。 |

## <a name="collect-available-data-from-mobile-device"></a>从移动设备收集可用数据

对用户设备问题进行故障排除时，请使用以下资源帮助收集设备数据：
- [将 iOS 注册错误发送给 IT 管理员](/intune-user-help/send-errors-to-your-it-admin-ios)
- [利用详细日志记录帮助公司支持人员修复设备问题](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
- [使用 USB 电缆将 Android 日志发送给公司支持人员](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
- [使用电子邮件将 Android 诊断数据日志发送给 IT 管理员](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
- [将 Android 注册错误发送给 IT 管理员](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>后续步骤

可了解有关基于角色的管理控制 (RBAC) 的详细信息，以便在组织设备、移动应用程序管理和数据保护任务中定义角色。 有关详细信息，请参阅 [Intune 的基于角色的管理控制 (RBAC)](/intune/role-based-access-control)。

了解 Microsoft Intune 中的任何已知问题。 有关详细信息，请参阅 [Microsoft Intune 中的已知问题](/intune/known-issues)。

了解如何创建支持票证，并在需要时获取帮助。 [获取支持](/intune/get-support)。
