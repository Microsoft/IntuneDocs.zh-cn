---
title: 排查 Microsoft Intune 证书连接器策略模块问题 | Microsoft Docs
description: 当使用 SCEP 证书配置文件将证书部署到 Intune 时，如果模块处理证书请求，则对 NDES 策略模块的操作进行故障排除。
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915832"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>在 Microsoft Intune 中对 NDES 策略模块进行故障排除

本文中的信息可帮助你验证随 Microsoft Intune 证书连接器一起安装的网络设备注册服务 (NDES) 策略模块的操作。 当 NDES 收到证书请求时，它会将请求转发到策略模块，该模块将验证请求是否对设备有效。 验证完成后，NDES 会与证书颁发机构 (CA) 联系，以代表该设备请求证书。

本文适用于 [SCEP 通信工作流](troubleshoot-scep-certificate-profiles.md)的步骤 3 和步骤 4。

## <a name="ndes-communication-to-the-policy-module"></a>与策略模块的 NDES 通信

从设备收到证书请求后，NDES 通过随 Microsoft Intune 证书连接器一同安装的策略模块验证通过 Intune 发出的请求。 这些条目引用证书注册点  。

**指示成功的日志条目**：

若要确认验证请求是否已提交到模块，请在 NDES 服务器上的日志中查找类似于以下示例的条目：

- **IIS 日志**：

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **NDESPlugin 日志**：

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  下面的示例说明设备质询请求验证成功，NDES 现在可以联系 CA：

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**：

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**当成功指示器不存在**：

如果找不到这些条目，请先查看[从设备到 NDES 服务器的通信](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors)的故障排除指南。

如果本文中的信息不能帮助你解决问题，以下是可以指示问题的其他条目。

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log 包含错误 12175

如果日志中包含类似于以下内容的错误 12175，则 SSL 证书可能存在问题：

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

移动设备上的新式浏览器和浏览器会忽略 SSL 证书上的公用名  ，前提是存在使用者备用名称  。

**解决方法**：使用以下属性为“公用名”  和“使用者备用名称”  颁发 Web 服务器 SSL 证书，然后将其绑定到 IIS 中的端口 443：

  - **使用者名称**  
    CN = 外部服务器名称
  - **使用者可选名称**  
     名称 = 外部服务器名称  
     DNS 名称 = 内部服务器名称

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log 包含错误 403 – 禁止访问：“访问被拒绝”

如果以下日志包含类似于以下内容的错误 403，则客户端证书可能不受信任或无效：

**NDESPlugin.log**：

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**IIS 日志**：

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

如果 NDES 服务器的“受信任的根证书颁发机构”证书存储中存在中间 CA 证书，则会出现此问题。

如果证书具有相同的“颁发对象”  和“颁发机构”  值，则它是一个根证书。 否则，它是中间证书。

**解决方法**：若要解决此问题，请从“受信任的根证书颁发机构”证书存储中标识并删除中间 CA 证书。

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>NDESPlugin.log 指示质询返回 false

如果质询结果返回 false  ，请检查 CertificateRegistrationPoint  错误。 例如，你可能会看到类似于以下条目的“无法检索签名证书”错误：

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**解决方法**：在安装了连接器的服务器上，打开注册表编辑器，找到 `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` 注册表项，然后检查 SigningCertificate 值是否存在。

如果此值不存在，请在 services.msc 中重新启动 Intune 连接器服务，然后检查该值是否显示在注册表中。 如果仍缺少该值，通常是因为 NDES 与 Intune 服务之间的服务器存在网络连接问题。

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES 传递请求以颁发证书

证书注册点（策略模块）成功验证后，NDES 会代表设备将证书请求传递给 CA。

**指示成功的日志条目**：

- **NDESPlugin 日志**：

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **IIS 日志**：

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**：

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**当成功指示器不存在**：

如果看不到指示成功的条目，请执行以下步骤：

1. 当证书注册点验证质询时，请查找 CertificateRegistrationPoint.svclog  中记录的问题。 查找以下行之间的条目：

   - VerifyRequest 已启动。
   - VerifyRequest 已完成，状态为 False

2. 打开 CA 上的证书颁发机构 MMC，选择“失败的请求”  以查找有助于识别问题的错误。 下图是一个示例：

   ![失败请求示例](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. 检查 CA 上的应用程序事件日志是否有错误。 通常，你会看到与上一步中的“失败请求”  中看到的错误相匹配的错误。 下图是一个示例：

   ![查看应用程序日志](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>后续步骤

如果 NDES 策略模块验证请求，并将请求转发到证书颁发机构，则下一步是查看[将证书传送到设备](troubleshoot-scep-certificate-delivery.md)。
