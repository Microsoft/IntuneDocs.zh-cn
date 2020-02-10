---
title: 在 Microsoft Intune 中排查向设备部署 SCEP 证书配置文件的问题 | Microsoft Docs
description: 排查在 Intune 中将 SCEP 证书配置文件发送到设备的问题。
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
ms.openlocfilehash: 3dae74321b6825a1b94551addfd7621450fd8ae4
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916040"
---
# <a name="troubleshoot-deployment-of-a-scep-certificate-profile-to-devices-in-microsoft-intune"></a>排查在 Microsoft Intune 中向设备部署 SCEP 证书配置文件的问题

使用以下信息来帮助你排查在 Intune 中部署简单证书注册协议 (SCEP) 证书配置文件的问题。

本文引用 [SCEP 通信流概述](troubleshoot-scep-certificate-profiles.md)的步骤 1。


## <a name="android"></a>Android

适用于 Android 的 SCEP 证书配置文件将作为 SyncML 出现在设备，并记录在 [OMADM 日志](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)中。

### <a name="validate-that-the-android-device-was-sent-the-policy"></a>验证是否已向 Android 设备发送策略

若要验证配置文件是否已发送到所需设备，请在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)转到“故障排除 + 支持”   > “故障排除”  。  在“故障排除”  窗口，将“分配”  设置为“配置文件”  ，然后验证以下配置：

1. 指定应接收 SCEP 证书配置文件的用户。

2. 查看用户组成员身份，确保它们位于与 SCEP 证书配置文件一起使用的安全组中。

3. 查看设备上次签入到 Intune 的时间。

![验证策略](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-android.png)

### <a name="validate-the-policy-reached-the-android-device"></a>验证策略是否已到达 Android 设备

查看[设备 OMADM 日志](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)。 查找类似于以下内容的条目，当设备从 Intune 获取配置文件时，会记录这些条目：

```
Time    VERB    Event     com.microsoft.omadm.syncml.SyncmlSession     9595        9    <?xml version="1.0" encoding="utf-8"?><SyncML xmlns="SYNCML:SYNCML1.2"><SyncHdr><VerDTD>1.2</VerDTD><VerProto>DM/1.2</VerProto><SessionID>1</SessionID><MsgID>6</MsgID><Target><LocURI>urn:uuid:UUID</LocURI></Target><Source><LocURI>https://a.manage.microsoft.com/devicegatewayproxy/AndroidHandler.ashx</LocURI></Source><Meta><MaxMsgSize xmlns="syncml:metinf">524288</MaxMsgSize></Meta></SyncHdr><SyncBody><Status><CmdID>1</CmdID><MsgRef>6</MsgRef><CmdRef>0</CmdRef><Cmd>SyncHdr</Cmd><Data>200</Data></Status><Replace><CmdID>2</CmdID><Item><Target><LocURI>./Vendor/MSFT/Scheduler/IntervalDurationSeconds</LocURI></Target><Meta><Format xmlns="syncml:metinf">int</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>28800</Data></Item></Replace><Replace><CmdID>3</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseIDs</LocURI></Target><Data>contoso.onmicrosoft.com</Data></Item></Replace><Exec><CmdID>4</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseApps/ClearNotifications</LocURI></Target></Item></Exec><Add><CmdID>5</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Root/{GUID}/EncodedCertificate</LocURI></Target><Data>Data</Data></Item></Add><Add><CmdID>6</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Enroll/ModelName=AC_51…%2FLogicalName_39907…%3BHash=-1518303401/Install</LocURI></Target><Meta><Format xmlns="syncml:metinf">xml</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>&lt;CertificateRequest&gt;&lt;ConfigurationParametersDocument&gt;&amp;lt;ConfigurationParameters xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/2012/03/07/CertificateEnrollment/ConfigurationParameters"&amp;gt;&amp;lt;ExpirationThreshold&amp;gt;20&amp;lt;/ExpirationThreshold&amp;gt;&amp;lt;RetryCount&amp;gt;3&amp;lt;/RetryCount&amp;gt;&amp;lt;RetryDelay&amp;gt;1&amp;lt;/RetryDelay&amp;gt;&amp;lt;TemplateName /&amp;gt;&amp;lt;SubjectNameFormat&amp;gt;{ID}&amp;lt;/SubjectNameFormat&amp;gt;&amp;lt;SubjectAlternativeNameFormat&amp;gt;{ID}&amp;lt;/SubjectAlternativeNameFormat&amp;gt;&amp;lt;KeyStorageProviderSetting&amp;gt;0&amp;lt;/KeyStorageProviderSetting&amp;gt;&amp;lt;KeyUsage&amp;gt;32&amp;lt;/KeyUsage&amp;gt;&amp;lt;KeyLength&amp;gt;2048&amp;lt;/KeyLength&amp;gt;&amp;lt;HashAlgorithms&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-1&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-2&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;/HashAlgorithms&amp;gt;&amp;lt;NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls&amp;gt;&amp;lt;CAThumbprint&amp;gt;{GUID}&amp;lt;/CAThumbprint&amp;gt;&amp;lt;ValidityPeriod&amp;gt;2&amp;lt;/ValidityPeriod&amp;gt;&amp;lt;ValidityPeriodUnit&amp;gt;Years&amp;lt;/ValidityPeriodUnit&amp;gt;&amp;lt;EKUMapping&amp;gt;&amp;lt;EKUMap&amp;gt;&amp;lt;EKUName&amp;gt;Client Authentication&amp;lt;/EKUName&amp;gt;&amp;lt;EKUOID&amp;gt;1.3.6.1.5.5.7.3.2&amp;lt;/EKUOID&amp;gt;&amp;lt;/EKUMap&amp;gt;&amp;lt;/EKUMapping&amp;gt;&amp;lt;/ConfigurationParameters&amp;gt;&lt;/ConfigurationParametersDocument&gt;&lt;RequestParameters&gt;&lt;CertificateRequestToken&gt;PENlcnRFbn... Hash: 1,010,143,298&lt;/CertificateRequestToken&gt;&lt;SubjectName&gt;CN=name&lt;/SubjectName&gt;&lt;Issuers&gt;CN=FourthCoffee CA; DC=fourthcoffee; DC=local&lt;/Issuers&gt;&lt;SubjectAlternativeName&gt;&lt;SANs&gt;&lt;SAN NameFormat="ID" AltNameType="2" OID="{OID}"&gt;&lt;/SAN&gt;&lt;SAN NameFormat="ID" AltNameType="11" OID="{OID}"&gt;john@contoso.onmicrosoft.com&lt;/SAN&gt;&lt;/SANs&gt;&lt;/SubjectAlternativeName&gt;&lt;NDESUrl&gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&lt;/NDESUrl&gt;&lt;/RequestParameters&gt;&lt;/CertificateRequest&gt;</Data></Item></Add><Get><CmdID>7</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/SCEP</LocURI></Target></Item></Get><Add><CmdID>8</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Add><Replace><CmdID>9</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Replace><Get><CmdID>10</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr</LocURI></Target></Item></Get><Get><CmdID>11</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/CacheVersion</LocURI></Target></Item></Get><Get><CmdID>12</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/ChangedNodes</LocURI></Target></Item></Get><Get><CmdID>13</CmdID><Item><Target><LocURI>./DevDetail/Ext/Microsoft/LocalTime</LocURI></Target></Item></Get><Get><CmdID>14</CmdID><Item><Target><LocURI>./Vendor/MSFT/DeviceLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Get><CmdID>15</CmdID><Item><Target><LocURI>./Vendor/MSFT/WorkProfileLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Final /></SyncBody></SyncML>
```

密钥条目示例：

- `ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c%3BHash=-1518303401`
- `NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls`

## <a name="ios-and-ipados"></a>iOS 和 iPadOS

### <a name="validate-that-the-ios-or-ipados-device-was-sent-the-policy"></a>验证是否已向 iOS 或 iPadOS 设备发送策略

若要验证配置文件是否已发送到所需设备，请在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)转到“故障排除 + 支持”   > “故障排除”  。  在“故障排除”  窗口，将“分配”  设置为“配置文件”  ，然后验证以下配置：

1. 指定应接收 SCEP 证书配置文件的用户。

2. 查看用户组成员身份，确保它们位于与 SCEP 证书配置文件一起使用的安全组中。

3. 查看设备上次签入到 Intune 的时间。

![验证策略](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-ios.png)

### <a name="validate-the-policy-reached-the-ios-or-ipados-device"></a>验证策略是否已到达 iOS 或 iPadOS 设备

查看[设备调试日志](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)。 查找类似于以下内容的条目，当设备从 Intune 获取配置文件时，会记录这些条目：

```
debug    18:30:54.638009 -0500    profiled    Adding dependent ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 to parent 636572740000000000000012 in domain PayloadDependencyDomainCertificate to system\
```

密钥条目示例：

- `ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295`
- `PayloadDependencyDomainCertificate`

## <a name="windows"></a>Windows

### <a name="validate-that-the-windows-device-was-sent-the-policy"></a>验证是否已向 Windows 设备发送策略

若要验证配置文件是否已发送到所需设备，请在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)[Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，转到“故障排除 + 支持”   > “故障排除”  。  在“故障排除”  窗口，将“分配”  设置为“配置文件”  ，然后验证以下配置：

1. 指定应接收 SCEP 证书配置文件的用户。

2. 查看用户组成员身份，确保它们位于与 SCEP 证书配置文件一起使用的安全组中。

3. 查看设备上次签入到 Intune 的时间。

![验证策略](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-windows.png)

### <a name="validate-the-policy-reached-the-windows-device"></a>验证策略是否已到达 Windows 设备

配置文件策略的到达方式记录在“DeviceManagement-Enterprise-Diagnostics-Provider”   > “管理”  日志中，事件 ID 为“306”  。 

要打开日志，请执行以下操作：

1. 在设备上，运行 eventvwr.msc  以打开 Windows 事件查看器。

2. 展开“应用程序和服务日志”   > “Microsoft”   > “Windows”   > “DeviceManagement-Enterprise-Diagnostic-Provider”   > “管理员”  。

3. 查找事件“306”  ，如以下示例所示：

   ```
   Event ID:      306
   Task Category: None
   Level:         Information
   User:          SYSTEM
   Computer:      <Computer Name>
   Description:
   SCEP: CspExecute for UniqueId : (ModelName_<ModelName>_LogicalName_<LogicalName>_Hash_<Hash>) InstallUserSid : (<UserSid>) InstallLocation : (user) NodePath : (clientinstall)  KeyProtection: (0x2) Result : (Unknown Win32 Error code: 0x2ab0003).
   ```

   0x2ab0003  错误代码转换为 DM_S_ACCEPTED_FOR_PROCESSING  。

   不成功的错误代码可能会指示根本问题。

## <a name="next-steps"></a>后续步骤

如果配置文件到达设备，下一步是查看[设备与 NDES 服务器之间的通信](troubleshoot-scep-certificate-device-to-ndes.md)。
