---
title: 使用 StageNow 登录 Microsoft Intune-Azure 中的 Android 斑马设备 |Microsoft Docs
description: 在使用 Microsoft Intune 的 Android 设备上使用 StageNow 时，请参阅常见问题和解决方法。 此外了解如何获取日志，并查看有关如何读取成功或错误日志的示例。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490535"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>进行故障排除和 Microsoft Intune 中 Android 斑马设备上看到的潜在问题

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您可以使用 Microsoft Intune[斑马移动扩展 (MX) 来管理 Android 斑马设备](android-zebra-mx-overview.md)。 使用斑马设备时，StageNow 管理设置，在创建配置文件并将其上载到 Intune。 Intune 使用 StageNow 应用在设备上应用的设置。 StageNow 应用还会创建用于进行故障排除的设备上的详细的日志文件。

此功能适用于：

- Android

例如，StageNow 将设备配置为在创建配置文件。 当创建 StageNow 配置文件时，最后一步将生成一个文件，为测试配置文件。 使用此文件，其 StageNow 应用在设备上。

在另一个示例中，在 StageNow，创建配置文件并对其进行测试。 在 Intune 中，添加 StageNow 配置文件，并再将其分配给斑马设备。 检查分配的配置文件的状态，该配置文件将显示高级状态。

在这两个这些情况下，可以从 StageNow 日志文件每次 StageNow 配置文件应用在设备保存获取更多详细信息。

某些问题 StageNow 配置文件的内容不相关，不会反映在这些日志。

本文演示如何读取 StageNow 日志，并与在日志中可能不会反映出来的斑马设备列出其他潜在的问题。

[使用和管理与斑马移动扩展斑马设备](android-zebra-mx-overview.md)具有此功能的详细信息。

## <a name="get-the-logs"></a>获取日志

### <a name="use-the-stagenow-app-on-the-device"></a>在设备上使用 StageNow 应用
在您测试的配置文件在计算机上的而不是使用上直接使用 StageNow [Intune 部署配置文件](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)，StageNow 应用在设备上的从测试保存日志。 若要获取的日志文件，请使用**详细 （...）** StageNow 应用在设备上的选项。

### <a name="get-logs-using-android-debug-bridge"></a>获取日志使用 Android 调试桥
若要获取日志配置文件已使用 Intune 部署后，请将设备连接到的计算机[Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) （打开 Android 的 web 站点）。

在设备上日志保存在 `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>从电子邮件获取日志
若要获取日志配置文件已使用 Intune 部署后，最终用户可以发送电子邮件将电子邮件应用使用设备上的日志。 斑马设备上打开公司门户应用，并[将日志发送](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。 使用发送日志功能还会创建 PowerLift 事件 ID，如果联系 Microsoft 支持部门可以引用。

## <a name="read-the-logs"></a>读取日志

查看日志时，只要存在着错误，请参阅`<characteristic-error>`标记。 错误详细信息将写入`<parm-error>`标记 >`desc`属性。

## <a name="error-types"></a>错误类型

斑马设备包括不同的错误报告级别：

- 在设备上不支持 CSP。 例如，设备不是移动电话的设备并不会有移动电话网络管理器。
- MX 或 OSX 版本不匹配。 每个 CSP 受版本控制。 有关完全支持矩阵，请参阅[斑马的文档](http://techdocs.zebra.com/mx/)（打开斑马的 web 站点）。
- 设备将报告另一个问题或错误。

## <a name="examples"></a>示例

例如，您具有以下输入配置文件：

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

在日志中，XML 是与输入相同的。 此匹配输出表明已成功应用到设备并且没有错误的配置文件：

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

在另一个示例中，您具有以下输入：

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

该日志显示错误，因为它包含`<characteristic-error>`标记。 在此方案中，尝试在给定的路径中安装 Android 包 (APK) 不存在的配置文件：

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>斑马设备的其他潜在问题

本部分列出了使用斑马设备通过设备管理器时可能会看到其他可能的问题。 StageNow 日志中不会报告这些问题。

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView 已过期

当使用公司门户应用登录较旧的设备时，用户可能会看到一条消息 System WebView 组件已过时，并需要升级。 如果该设备已安装 Google Play 中，将其连接到 internet，并检查更新。 如果设备没有安装 Google Play、 获取更新的版本的组件，并将其应用到设备。 或者，更新到最新的设备颁发的 Zebra 的操作系统。

### <a name="management-actions-take-a-long-time"></a>管理操作需要很长时间

如果通过 Google Play services 不可用，某些任务需要 8 小时才能完成。 [适用于 Android 的限制的 Intune 公司门户应用](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china)（将打开另一个 Microsoft 网站上） 可能会很好的资源。

### <a name="device-spoofing-suspected-shows-in-intune"></a>在 Intune 中显示了"欺骗怀疑有问题的设备"

此错误意味着 Intune 怀疑其型号和制造商为斑马设备报告非斑马 Android 设备。

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>公司门户应用是早于所需最低版本

Intune 可能会更新公司门户应用要求的最低版本。 如果在设备上未安装 Google Play，公司门户应用不会获取自动更新。 如果所需的最低版本高于已安装的版本，公司门户应用将停止工作。 更新到最新的公司门户应用程序使用[斑马设备上的旁加载](android-zebra-mx-overview.md#sideload-the-company-portal-app)。

## <a name="next-steps"></a>后续步骤

[斑马讨论板](https://developer.zebra.com/community/home/discussions)（打开斑马的 web 站点）

[使用和管理斑马斑马移动扩展在 Intune 中的设备](android-zebra-mx-overview.md)
