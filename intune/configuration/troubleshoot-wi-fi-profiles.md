---
title: Microsoft Intune 中的 Wi-Fi 设备配置文件日志查看和疑难解答 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，了解 Android、iOS 和 Windows 设备上的 Wi-Fi 设备配置文件问题并对其进行疑难解答。 查看日志，并了解一些常见问题和可能的解决方法。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77f5787509438ec3280f29be8449d78979806042
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74542658"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Microsoft Intune 中的 Wi-Fi 设备配置文件疑难解答

在 Intune 中，你可以创建包含 WiFi 网络的连接设置的设备配置文件。 使用这些设置将用户的 Android、iOS 和 Windows 设备连接到组织网络。

本文介绍了怎样才算将 Wi-Fi 配置文件成功应用于设备。 它还包括日志信息、常见问题等。 本文介绍了如何帮助你对 Wi-Fi 配置文件进行疑难解答。

有关 Intune 中 Wi-Fi 配置文件的详细信息，请参阅[在设备上添加和使用 Wi-Fi 设置](wi-fi-settings-configure.md)。

## <a name="before-you-begin"></a>在开始之前

本文中的示例对 Intune 配置文件使用 SCEP 证书身份验证。 它还假定受信任的根和 SCEP 配置文件在设备上正常工作。

## <a name="android"></a>Android

在本部分中，我们将逐步介绍在 Android 设备上安装配置文件时的最终用户体验。

### <a name="end-user-experience-example"></a>最终用户体验示例

此应用场景使用 Nokia 6.1 设备。 在设备上安装 Wi-Fi 配置文件之前，请安装受信任的根和 SCEP 配置文件。

1. 最终用户收到有关安装受信任的根证书配置文件的通知：

    > [!div class="mx-imgBorder"]
    > ![在 Android 上安装受信任的根证书配置文件的公司门户应用通知示例](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. 下一条通知将提示安装 SCEP 证书配置文件：

    > [!div class="mx-imgBorder"]
    > ![在 Android 上安装 SCEP 证书配置文件的公司门户应用通知示例](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > 使用设备管理员管理的 Android 设备时，可能会列出多个证书。 吊销或删除证书配置文件时，证书将保留在设备上。 在此应用场景中，选择最新的证书。 它通常是列表中显示的最后一个证书。
    >
    > 这种情况不会发生在 Android Enterprise 和 Samsung Knox 设备上。 有关详细信息，请参阅[管理 Android 工作配置文件设备](../enrollment/android-enterprise-overview.md)和[删除 SCEP 和 PKCS 证书](../protect/remove-certificates.md#android-knox-devices)。

3. 接下来，用户会收到有关安装 Wi-Fi 配置文件的通知：

    > [!div class="mx-imgBorder"]
    > ![在 Android 上安装 SCEP 证书配置文件的公司门户应用通知示例](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. 完成后，Wi-Fi 连接显示为已保存的网络：

    > [!div class="mx-imgBorder"]
    > ![Wi-Fi 连接显示为已保存的网络](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>查看公司门户应用日志

在 Android 上，Omadmlog.log  文件将在设备上安装 Wi-Fi 配置文件时详细说明该配置文件的活动。 最多可以有五个 Omadmlog 日志文件。 请确保获取上次同步的时间戳，因为它将帮助你找到相关的日志条目。

在下面的示例中，使用 [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) 读取日志，然后搜索“wifimgr”：

> [!div class="mx-imgBorder"]
> ![Wi-Fi 连接显示为已保存的网络](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

以下日志显示搜索结果，并显示已成功应用 Wi-Fi 配置文件：

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

在设备上安装 Wi-Fi 配置文件后，它将显示在“管理配置文件”  中：

> [!div class="mx-imgBorder"]
> ![iOS 设备上的管理配置文件](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![iOS 设备上的 Wi-Fi 连接显示为 Wi-Fi 网络](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>查看 iOS 控制台和设备日志

在 iOS 设备上，公司门户应用日志不包含有关 Wi-Fi 配置文件的信息。 若要查看 Wi-Fi 配置文件的安装详细信息，请使用控制台/设备日志：

1. 将 iOS 设备连接到 Mac。 转到“应用程序”   > “实用程序”  ，然后打开控制台应用。
2. 在“操作”  下，选择“包含信息消息”  和“包含调试消息”  ：

    > [!div class="mx-imgBorder"]
    > ![iOS 控制台应用中的“包含信息消息”和“包含调试消息”](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. 重现此应用场景，并将日志保存到文本文件中：

    1. 选择当前屏幕上的所有消息：“编辑”   > “全选”  。
    2. 复制消息：“编辑”   > “复制”  。
    3. 将日志数据粘贴到文本编辑器中，然后保存该文件。

4. 搜索已保存的日志文件以查看详细信息。 当配置文件成功安装时，你的输出类似于以下日志：

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

在设备上安装 Wi-Fi 配置文件后，依次转到“设置”   > “帐户”   > “访问工作或学校”  。 选择你的帐户 >“信息”  ：

> [!div class="mx-imgBorder"]
> ![在 Windows 设备上选择“访问工作或学校”和“信息”](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

在“由 Microsoft 管理的区域”  中，将显示“WiFi”  ：

> [!div class="mx-imgBorder"]
> ![在“由 Microsoft 管理的区域”中，查看在 Windows 上列出的 WiFi](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

若要查看 Wi-Fi 连接，请访问“设置”   > “网络和 Internet”    > “Wi-Fi”  ：

> [!div class="mx-imgBorder"]
> ![在 Windows 上，在“设置”中将 Wi-Fi 连接视为已知网络](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>查看事件查看器日志

在 Windows 设备上，有关 Wi-Fi 配置文件的详细信息记录在事件查看器中：

1. 打开“事件查看器”  应用。
2. 在“视图”  菜单上，选择“显示分析和调试日志”  。
3. 展开“应用程序和服务日志”   > “Microsoft”   > “Windows”   > “DeviceManagement-Enterprise-Diagnostic-Provider”   > “管理员” 

输出类似于以下日志：

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>常见问题

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>问题 1：Wi-Fi 配置文件未部署到设备

- 确认将 Wi-Fi 配置文件分配给了正确的组：

    1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “配置文件”  。
    2. 依次选择配置文件和“分配”  。 确认所选组正确。
    3. 在终结点管理器中，选择“疑难解答 + 支持”  。 查看“分配”  信息。

- 在终结点管理器中，选择“疑难解答 + 支持”  。 通过检查“上次签入”  时间，确认设备是否可以与 Intune 同步。

- 如果 Wi-Fi 配置文件链接到受信任的根和 SCEP 配置文件，请确认两个配置文件均已部署到设备。 Wi-Fi 配置文件依赖于这些配置文件。

- 在 Windows 10 及更高版本的设备上，查看 MDM 诊断信息日志：

  1. 转至“设置”   > “帐户”   > “访问工作或学校”  。
  2. 选择你的工作或学校帐户 >“信息”  。
  3. 在“设置”  页的底部，选择“创建报表”  。
  4. 此时会打开一个窗口，其中显示了日志文件的路径。 选择“导出”  。
  5. 转到 `\Users\Public\Documents\MDMDiagnostics` 路径，然后查看报表：

      > [!div class="mx-imgBorder"]
      > ![显示了 Windows 10 设备上 WiFi 配置文件配置的 MDM 诊断信息示例](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > 有关详细信息，请参阅[在 Windows 10 中诊断 MDM 故障](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)。

- 在 Android 设备上，如果设备上未安装受信任的根和 SCEP 配置文件，你将在公司门户应用 Omadmlog 文件中看到以下条目：

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - 当受信任的根和 SCEP 配置文件位于 Android 设备上且合规时，Wi-Fi 配置文件可能不在设备上。 当公司门户应用的 CertificateSelector  提供程序找不到与指定条件匹配的证书时，会发生此问题。 特定条件可能位于证书模板或 SCEP 配置文件中。

    如果找不到匹配的证书，则不会安装设备上的证书。 未应用 Wi-Fi 配置文件，因为它没有正确的证书。 在此应用场景中，你将在公司门户应用 Omadmlog 文件中看到以下条目：

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    下面的示例日志显示由于指定了“任何用途”  扩展密钥用法 (EKU) 条件而排除的证书。 但是，分配给设备的证书没有该 EKU：

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    以下示例显示了 SCEP 配置文件输入“任何用途”  EKU。 但它不会输入到证书颁发机构 (CA) 的证书模板中。 若要解决此问题，请将“任何用途”  选项添加到证书模板。 或者，从 SCEP 配置文件中删除“任何用途”  选项。

    > [!div class="mx-imgBorder"]
    > ![在 Android 上，将“任何用途”添加到证书颁发机构的证书模板中](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![在 Android 上，将“任何用途”添加到 Intune 中的 SCEP 证书配置文件中](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - 确认完整证书链中的所有必需证书都位于 Android 设备上。 否则，将无法在设备上安装 Wi-Fi 配置文件。 有关详细信息，请参阅[缺少中间证书颁发机构](https://developer.android.com/training/articles/security-ssl#MissingCa)（打开 Android 的网站）。
  - 使用关键字筛选 Omadmlog 以查找信息，如 Wi-Fi 配置文件中使用的证书，以及是否已成功应用配置文件。

    例如，使用 [CMTrace](https://docs.microsoft.com/sccm/core/support/cmtrace) 读取日志。 使用搜索字符串筛选“wifimgr”：

    > [!div class="mx-imgBorder"]
    > ![筛选 CMTrace 以查找 Android 设备上的 WiFiMgr 配置文件](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    输出类似于以下日志：

    > [!div class="mx-imgBorder"]
    > ![CMTrace 日志输出示例显示了已成功在设备上应用了 WiFi Intune 配置文件](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    如果日志中出现错误，请复制错误的时间戳并取消筛选日志。 然后，将“查找”选项与时间戳结合使用，查看错误发生之前所发生的情况。

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>问题 2：将 Wi-Fi 配置文件部署到设备，但设备无法连接到网络

通常情况下，此问题由 Intune 之外的事项引起。 以下任务可以帮助你了解和解决连接问题：

- 使用与 Wi-Fi 配置文件中的条件相同的证书，手动连接到网络。

  如果可以连接，请查看手动连接中的证书属性。 然后，更新具有相同证书属性的 Intune Wi-Fi 配置文件。
- 连接错误通常记录在 Radius 服务器日志中。 例如，它应显示设备是否尝试与 Wi-Fi 配置文件相连接。

## <a name="need-more-help"></a>需要更多帮助

- 使用 [Intune 用户论坛](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)或[从 Microsoft 获取支持](../fundamentals/get-support.md)。

- 有关 Microsoft Intune 中 Wi-Fi 配置文件的详细信息，请参阅以下文章：

  - 为运行 [Android](wi-fi-settings-android.md)、[iOS](wi-fi-settings-ios.md) 和 [Windows 10 及更高版本](wi-fi-settings-windows.md)的设备添加 Wi-Fi 设置。
  - [支持提示 - 如何在 Intune 中为 SCEP 证书部署配置 NDES](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - 对 [SCEP 证书配置文件部署](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune)和 [NDES 配置](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)进行疑难解答。

- 若要了解最新资讯、信息和技术提示，请查看官方博客：
  - [Microsoft Intune 支持团队博客](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Microsoft 企业移动性和安全性博客](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>后续步骤

[监视配置文件](device-profile-monitor.md)。
