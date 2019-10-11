---
title: 在 Microsoft Intune 中使用 Android 斑马设备上的 StageNow 日志-Azure |Microsoft Docs
description: 请参阅在 Android 设备上使用 StageNow 时的常见问题和解决方法 Microsoft Intune。 还了解如何获取日志，并查看有关如何读取日志以获取成功或错误的示例。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 324550836cd8e7c8ea2786d15618d5f5010a043f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735241"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>排查和查看 Microsoft Intune 中的 Android 斑马设备上出现的潜在问题

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

在 Microsoft Intune 中，可以使用[斑马移动扩展（MX）来管理 Android 斑马设备](android-zebra-mx-overview.md)。 使用斑马设备时，可在 StageNow 中创建配置文件来管理设置，并将其上传到 Intune。 Intune 使用 StageNow 应用来应用设备上的设置。 StageNow 应用还会在设备上创建用于排除故障的详细日志文件。

此功能适用于：

- Android

例如，在 StageNow 中创建配置文件以配置设备。 创建 StageNow 配置文件时，最后一步会生成一个文件，用于测试配置文件。 将此文件与设备上的 StageNow 应用一起使用。

在另一个示例中，将在 StageNow 中创建一个配置文件，并对其进行测试。 在 Intune 中添加 StageNow 配置文件，然后将其分配给斑马设备。 检查分配的配置文件的状态时，配置文件将显示高级状态。

在这两种情况下，你都可以从 StageNow 日志文件中获取更多详细信息，该日志文件会在每次应用 StageNow 配置文件时保存在设备上。

某些问题与 StageNow 配置文件的内容不相关，并且不会反映在日志中。

本文介绍了如何读取 StageNow 日志，并列出了可能不会在日志中反映的斑马设备的一些其他潜在问题。

[使用和管理斑马移动扩展的斑马设备](android-zebra-mx-overview.md)包含有关此功能的详细信息。

## <a name="get-the-logs"></a>获取日志

### <a name="use-the-stagenow-app-on-the-device"></a>在设备上使用 StageNow 应用
当你在计算机上使用 StageNow 直接测试配置文件，而不是使用[Intune 部署配置文件](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)时，设备上的 StageNow 应用将保存测试中的日志。 若要获取日志文件，请在设备上的 StageNow 应用中使用 "**更多（...）** " 选项。

### <a name="get-logs-using-android-debug-bridge"></a>使用 Android Debug Bridge 获取日志
若要在配置文件已使用 Intune 部署后获取日志，请将设备连接到具有[Android Debug Bridge （adb）](https://developer.android.com/studio/command-line/adb)的计算机（打开 Android 的网站）。

在设备上，日志保存在 `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>从电子邮件获取日志
若要在配置文件已使用 Intune 部署后获取日志，最终用户可以使用设备上的电子邮件应用通过电子邮件向你发送日志。 在斑马设备上，打开公司门户应用并[发送日志](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。 使用 "发送日志" 功能还会创建 PowerLift 事件 ID，如果联系 Microsoft 支持部门，你可以参考该 ID。

## <a name="read-the-logs"></a>读取日志

查看日志时，只要看到 `<characteristic-error>` 标记，就会出错。 错误详细信息将写入 `<parm-error>` 标记 > `desc` 属性。

## <a name="error-types"></a>错误类型

斑马设备包含不同的错误报告级别：

- 设备上不支持 CSP。 例如，设备不是移动设备，也没有移动电话管理器。
- MX 或 OSX 版本不匹配。 每个 CSP 都是版本控制的。 有关完整的支持矩阵，请参阅[斑马的文档](http://techdocs.zebra.com/mx/)（打开斑马的网站）。
- 设备报告其他问题或错误。

## <a name="examples"></a>示例

例如，你有以下输入配置文件：

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

在日志中，XML 与输入完全相同。 此匹配输出表示配置文件已成功应用到设备且无错误：

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

在另一个示例中，你具有以下输入：

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

日志显示错误，因为它包含 `<characteristic-error>` 的标记。 在此方案中，配置文件尝试安装给定路径中不存在的 Android 包（APK）：

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

本部分列出了在将斑马设备与设备管理员一起使用时可能会遇到的其他问题。 StageNow 日志中不报告这些问题。

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView 过期

当旧设备使用公司门户应用登录时，用户可能会看到一条消息，指出系统 Web 视图组件已过期，需要升级。 如果设备已安装 Google Play，请将其连接到 internet，然后检查更新。 如果设备未安装 Google Play，请获取组件的更新版本，并将其应用于设备。 或者，更新到由斑马颁发的最新设备操作系统。

### <a name="management-actions-take-a-long-time"></a>管理操作需要很长时间

如果 Google Play 服务不可用，则一些任务最多需要8小时才能完成。 [适用于 Android 的 Intune 公司门户应用程序](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china)（打开另一个 Microsoft 网站）的限制可能是一个不错的资源。

### <a name="device-spoofing-suspected-shows-in-intune"></a>Intune 中显示了 "怀疑设备欺骗"

此错误表示，Intune 怀疑某个非斑马的 Android 设备将其模型和制造商报告为斑马设备。

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>公司门户应用早于所需最低版本

Intune 可能会更新公司门户应用程序所需的最低版本。 如果设备上未安装 Google Play，则公司门户应用不会自动更新。 如果所需的最低版本比安装的版本更新，则公司门户应用将停止工作。 使用[斑马设备上的旁加载](android-zebra-mx-overview.md#sideload-the-company-portal-app)更新到最新的公司门户应用。

## <a name="next-steps"></a>后续步骤

[斑马讨论板](https://developer.zebra.com/community/home/discussions)（打开斑马的网站）

[通过 Intune 中的 Zebra Mobility Extensions 使用和管理 Zebra 设备](android-zebra-mx-overview.md)
