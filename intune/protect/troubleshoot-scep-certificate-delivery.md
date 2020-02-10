---
title: 排查在 Microsoft Intune 中使用 SCEP 时，将证书传送到设备的问题 | Microsoft Docs
description: 排查在 Intune 中使用 SCEP 证书配置文件部署证书时，将证书从 CA 传送到设备的问题。
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
ms.openlocfilehash: 77be59d126dc7e73bee468ca938938c6bb1b2e1a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915871"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>排查在 Microsoft Intune 中将 SCEP 预配的证书传送到设备的问题

使用简单证书注册协议 (SCEP) 在 Intune 中预配证书时，请使用本文中的信息来帮助调查将证书传送到设备。 网络设备注册服务 (NDES) 服务器从证书颁发机构 (CA) 收到设备请求的证书后，它会将该证书传递回设备。

本文适用于 [SCEP 通信工作流](troubleshoot-scep-certificate-profiles.md)的步骤 5：将证书传送到提交证书请求的设备。

## <a name="review-the-certification-authority"></a>查看证书颁发机构

CA 颁发证书后，会在 CA 上看到类似于以下示例的条目：

![颁发的证书示例](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>查看设备

### <a name="android"></a>Android

对于设备管理员注册的设备，你将看到类似于下图的通知，该通知提示你安装证书：

![Android 通知](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

对于 Android Enterprise 或 Samsung Knox，将自动安装证书，无提示。

若要在 Android 上查看安装的证书，请使用第三方证书查看应用。

还可以查看[设备 OMADM 日志](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)。 查找类似于以下内容的条目，该条目是在安装证书时记录的：

**根证书**：

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**通过 SCEP 预配的证书**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="ios-and-ipados"></a>iOS 和 iPadOS

在 iOS 或 iPadOS 设备上，你可以在“设备管理配置文件”下查看证书。 深入了解已安装证书的详细信息。

![iOS 证书](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

还可以在 [iOS 调试日志](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)中查找类似于以下内容的条目：

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

在 Windows 设备上，验证是否已传送证书：

- 运行 eventvwr.msc  以打开“事件查看器”。 转到“应用程序和服务日志”   > “Microsoft”   > “Windows”   > “DeviceManagement-Enterprise-Diagnostic-Provider”   > “管理员”  并查找“事件 39”  。 此事件应具有以下内容的一般描述：**SCEP：已成功安装证书。**

   ![Windows 应用程序日志中的事件 39](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

若要查看设备上的证书，请运行 certmgr.msc  以打开“证书 MMC”，并验证是否在设备的个人存储中正确安装了根证书和 SCEP 证书：

   1. 转到“证书(本地计算机)”   > “受信任的根证书颁发机构”   > “证书”  ，并验证来自 CA 的根证书是否存在。 “颁发对象”  和“颁发者”  的值将相同。
   2. 在“证书 MMC”中，转到“证书 – 当前用户”   > “个人”   > “证书”  ，并验证请求的证书是否存在，该证书的“颁发者”  等于 CA 的名称。

## <a name="troubleshoot-failures"></a>排查失败

### <a name="android"></a>Android

若要解决此问题，请查看 OMA DM 日志中记录的错误。

### <a name="ios-and-ipados"></a>iOS 和 iPadOS

若要解决此问题，请查看设备调试日志中记录的错误。

### <a name="windows"></a>Windows

若要解决设备上未安装证书的问题，请查看 Windows 事件日志中提示问题的错误：

- 在设备上，运行 eventvwr.msc  以打开“事件查看器”，然后转到“应用程序和服务日志”   > “Microsoft”   > “Windows”   > “DeviceManagement-Enterprise-Diagnostic-Provider”   > “管理员”  。

传送和安装证书到设备的错误通常与 Windows 操作相关，与 Intune 不相关。

## <a name="next-steps"></a>后续步骤

当证书成功部署到设备，但 Intune 没有报告成功时，请参阅 [NDES 向 Intune 报告](troubleshoot-scep-certificate-reporting.md)来排除报告故障。
