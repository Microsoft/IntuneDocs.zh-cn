---
title: 在 Microsoft Intune 中排查使用 SCEP 证书配置文件预配证书的故障 | Microsoft Docs
description: 排查设备使用 SCEP 请求证书与 Intune 配合使用的故障，包括设备与 NDES、NDES 与证书颁发机构，以及 Intune 证书连接器与 Intune 服务之间的通信。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38bc86b1b9ba85eb7885a0e00673e551821063c1
ms.sourcegitcommit: 459b0ee01eb6e69cc0ce66d4c4b81d73f510f96d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034237"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>在 Microsoft Intune 中对 SCEP 证书配置文件进行故障排除概述

使用简单证书注册协议 (SCEP) 证书配置文件在 Intune 中进行故障排除可能较为棘手。 本文提供的概要将帮助你通过以下方法解决问题：

- 介绍 SCEP 进程的体系结构和通信流
- 帮助你缩小问题在该通信流中的位置范围
- 标识后续文章中用于排查证书配置文件问题的关键日志文件

本文和相关 SCEP 证书排除故障文章中的信息适用于在 Android、iOS/iPad 和 Windows 设备上使用 SCEP 证书配置文件。 MacOS 的类似信息目前不可用。

若要排查网络设备注册服务 (NDES) 问题，请参阅 support.microsoft.com 中的以下文章：

- [在 Intune 中验证 SCEP 证书的本地 NDES 配置](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [对与 Microsoft Intune 证书配置文件一起使用的 NDES 配置进行故障排除]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)

在继续之前，请确保已满足[使用 SCEP 证书配置文件的先决条件](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates)，包括通过受信任的证书配置文件部署根证书。

## <a name="scep-communication-flow-overview"></a>SCEP 通信流概述

下图演示了 Intune 中的 SCEP 通信进程的基本概述。

![SCEP 证书配置文件流](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [部署 SCEP 证书配置文件](troubleshoot-scep-certificate-profile-deployment.md)。 Intune 会生成一个质询字符串，该字符串需要特定用户、证书用途和证书类型。

2. [从设备到 NDES 服务器的通信](troubleshoot-scep-certificate-device-to-ndes.md)。 设备使用配置文件中 NDES 的 URI 来与 NDES 服务器联系，以便它能够提出质询。

3. [从 NDES 到策略模块的通信](troubleshoot-scep-certificate-ndes-policy-module.md)。 NDES 将质询转发到服务器上的 Intune 证书连接器策略模块，该模块用于验证请求。

4. [从 NDES 到证书颁发机构](troubleshoot-scep-certificate-ndes-policy-module.md)。 NDES 向证书颁发机构 (CA) 传递颁发证书的有效请求。

5. [将证书传送到设备](troubleshoot-scep-certificate-delivery.md)。 将证书传送到设备。

6. [向 Intune 报告部署](troubleshoot-scep-certificate-reporting.md)。 Intune 证书连接器向 Intune 报告证书颁发事件。

## <a name="log-files"></a>日志文件

若要确定通信和证书预配工作流的问题，请查看来自服务器基础结构和设备的日志文件。 有关对 SCEP 证书配置文件进行故障排除的后续部分将引用本部分中提到的日志文件。

- [基础结构和服务器日志](#logs-for-on-premises-infrastructure)

设备日志取决于设备平台：  

- [iOS 和 iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>本地基础结构日志
  
支持对证书部署使用 SCEP 证书配置文件的本地基础结构包括 Microsoft Intune 证书连接器、在 Windows Server 上运行的 NDES 和证书颁发机构。

这些角色的日志文件包括 Windows 事件查看器、证书控制台和特定于 Intune 证书连接器、NDES 或及本地基础结构中的其他角色和操作的各种日志文件。

以下列表包含后续 SCEP 故障排除文章中引用的日志或控制台。 

- **NDESConnector_date_time.svclog**：

  此日志显示从 Microsoft Intune 证书连接器到 Intune 云服务的通信。 可使用[服务跟踪查看器工具](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)查看此日志文件。

  相关注册表项：*HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  位置：在承载 NDES 的服务器上，位置为 %program_files%\Microsoft intune\ndesconnectorsvc\logs\logs 

- **CertificateRegistrationPoint_date_time.svclog**：

  此日志显示接收和验证证书请求的 NDES 策略模块。 可使用[服务跟踪查看器工具](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)查看此日志文件。

  位置：在承载 NDES 的服务器上，位置为 %program_files%\Microsoft intune\ndesconnectorsvc\logs\logs 

- **NDESPlugin.log**：

  此日志显示向证书注册点传递证书请求的情况，以及这些请求的验证结果。

  位置：在承载 NDES 的服务器上，位置为 %program_files%\Microsoft Intune\NDESPolicyModule\logs 

- **IIS 日志**：

  IIS 日志显示来自进入 NDES 的移动设备的证书请求。

  位置：在承载 NDES 的服务器上，位置为 c:\inetpub\logs\LogFiles\W3SVC1 

- **Windows 应用程序日志**：

  此日志在调查 IIS 问题（如 SCEP 应用程序池）时很有用。

  位置：在承载 NDES 的服务器上：运行 eventvwr.msc  以打开 Windows 事件查看器




### <a name="logs-for-android-devices"></a>适用于 Android 设备的日志

对于运行 Android 的设备，请使用“Android 公司门户”  应用日志文件“OMADM.log”  。 收集和查看日志之前，请确保已启用[详细日志记录](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)，然后重现该问题。

若要从设备收集 OMADM.log，请参阅[使用 USB 电缆上传日志和通过电子邮件发送日志](/intune-user-help/send-logs-to-your-it-admin-using-cable-android)。

还可以参阅[上传日志和通过电子邮件发送日志](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app)来获取支持。

### <a name="logs-for-ios-and-ipados-devices"></a>适用于 iOS 和 iPadOS 设备的日志

对于运行 iOS 或 iPadOS 的设备，请使用在 Mac 计算机上运行的调试日志和 Xcode  ：

1. 将 iOS 设备连接到 Mac，然后转到“应用程序”   > “实用程序”  以打开控制台应用程序。 

2. 在“操作”  下，选择“包含信息消息”  和“包含调试消息”  。

   ![选择日志选项](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. 重现该问题，然后将日志保存到文本文件中：
   1. 选择“编辑”   > “选择全部”  以选择当前屏幕上的所有消息，然后选择“编辑”   > “复制”  将消息复制到剪贴板。 
   2. 打开 TextEdit 应用程序，将复制的日志粘贴到新文本文件中，然后保存该文件。


适用于 iOS 和 iPadOS 设备的公司门户日志不包含有关 SCEP 证书配置文件的信息。

### <a name="logs-for-windows-devices"></a>Windows 设备日志

对于运行 Windows 的设备，请使用 Windows 事件日志诊断使用 Intune 管理的设备的注册或设备管理问题。

在设备上，打开“事件查看器”   > “应用程序和服务日志”   > “Microsoft”   > “Windows”   > “DeviceManagement-Enterprise-Diagnostics-Provider” 

![Windows 事件日志](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>后续步骤

查看 [SCEP 证书配置文件部署](troubleshoot-scep-certificate-profile-deployment.md) 
