---
title: 对 Microsoft Intune 中受管理设备到 NDES 的通信进行故障排除 | Microsoft Docs
description: 使用 SCEP 证书配置文件向 Intune 部署证书时，对受管理设备到 NDES 服务器的通信进行故障排除。
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
ms.openlocfilehash: 7945f1df3ddf1a6ff2c42a537e1071d1b5acff24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514262"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>对 Microsoft Intune 中用于 SCEP 证书配置文件的设备到 NDES 服务器的通信进行故障排除

使用以下信息来确定已接收并处理 Intune 简单证书注册协议 (SCEP) 证书配置文件的设备是否可以成功联系网络设备注册服务 (NDES) 以提出质询。 在设备上，将生成一个私钥，并将证书签名请求 (CSR) 和质询从设备传递到 NDES 服务器。 要与 NDES 服务器联系，设备将使用 SCEP 证书配置文件中的 URI。

本文引用 [SCEP 通信流概述](troubleshoot-scep-certificate-profiles.md)的步骤 2。

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>在 IIS 日志中查看来自设备的连接

IIS 日志包含所有平台的相同类型的条目。


1. 在 NDES 服务器上，打开在以下文件夹中找到的最新 IIS 日志文件：%SystemDrive%\inetpub\logs\logfiles\w3svc1 

2. 在日志中搜索类似于以下示例的条目。 这两个示例都包含状态 200  ，该状态显示在末尾处：

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   且

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. 当设备与 IIS 联系时，将记录对 mscep.dll 的 HTTP GET 请求。

   在此请求末尾处查看状态代码：
   - **状态代码 200**：此状态指示成功连接 NDES 服务器。
   - **状态代码 500**：IIS_IURS 组可能缺少正确的权限。 请参阅本文后面的[状态代码 500](#status-code-500)。
   - 如果状态码不是 200 或 500：

     - 请参阅本文后面的[测试 SCEP 服务器 URL](#test-the-scep-server-url)，以帮助验证配置。

     - 有关不太常见的错误代码的信息，请参阅 [IIS 7 和更高版本中的 HTTP 状态代码](https://support.microsoft.com/help/943891)。

   如果根本没有记录连接请求，则来自设备的联系人可能会在设备与 NDES 服务器之间的网络上受阻。

## <a name="review-device-logs-for-connections-to-ndes"></a>在设备日志中查看到 NDES 的连接

### <a name="android-devices"></a>Android 设备

查看[设备 OMADM 日志](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)。 查找类似于以下内容的条目，当设备连接到 NDES 时，会记录这些条目：

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

密钥条目包含以下示例文本字符串：

- 有 1 个请求
- 将 GetCACaps(ca) 发送到 https://\<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca 时收到“200 OK”
- 使用属于 [dn=CN=\<username>; serial=1] 的密钥登录 pkiMessage


该连接还由 IIS 记录在 NDES 服务器的 %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ 文件夹中。 下面是一个示例：

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="iosipados-devices"></a>iOS/iPadOS 设备

查看[设备调试日志](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)。 查找类似于以下内容的条目，当设备连接到 NDES 时，会记录这些条目：

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

密钥条目包含以下示例文本字符串：

- operation=GetCACert
- 尝试检索已颁发的证书
- 通过 GET 发送 CSR
- operation=PKIOperation

### <a name="windows-devices"></a>Windows 设备

在要与 NDES 建立连接的 Windows 设备上，可以查看设备 Windows 事件查看器并查找成功连接的指示。 连接在设备“DeviceManagement-Enterprise-Diagnostics-Provide”   > “管理员”  日志中记录为事件 ID“36”  。

要打开日志，请执行以下操作：

1. 在设备上，运行 eventvwr.msc  以打开 Windows 事件查看器。

2. 展开“应用程序和服务日志”   > “Microsoft”   > “Windows”   > “DeviceManagement-Enterprise-Diagnostic-Provider”   > “管理员”  。

3. 查找事件“36”  ，如以下示例所示，其键行为“SCEP：  已成功生成证书请求”：

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>解决常见问题

以下各节可帮助解决从所有设备平台到 NDES 的常见连接问题。

### <a name="status-code-500"></a>状态代码 500

与以下示例类似的连接（状态代码为 500）表示未向 NDES 服务器上的 IIS_IURS 组分配“身份验证后模拟客户端”  用户权限。 在末尾显示状态值 500  ：

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**要解决此问题**：

1. 在 NDES 服务器上，运行“secpol.msc”  以打开“本地安全策略”。

2. 展开“本地策略”  ，然后单击“用户权限分配”  。

3. 在右窗格中双击“身份验证后模拟客户端”  。

4. 单击“添加用户或组…”  ，在“输入要选择的对象名称”  框中键入 IIS_IURS  ，然后单击“确定”  。

5. 单击" **确定**"。

6. 重启计算机，然后再次尝试从设备进行连接。

### <a name="test-the-scep-server-url"></a>测试 SCEP 服务器 URL

使用以下步骤测试 SCEP 证书配置文件中指定的 URL。

1. 在 Intune 中，编辑 SCEP 证书配置文件并复制服务器 URL。 此 URL 看起来应该如下所示： *https://contoso.com/certsrv/mscep/msecp.dll* 。

2. 打开 Web 浏览器，然后浏览到该 SCEP 服务器 URL。 结果应为：**HTTP 错误 403.0 – 已禁止**。 此结果表示 URL 正常运行。

   如果未收到该错误，请选择与你看到的错误类似的链接，以查看问题特定的指南：
   - [我收到常规网络设备注册服务消息](#general-ndes-message)
   - [我收到“HTTP 错误 503。服务不可用”](#http-error-503)
   - [我收到“GatewayTimeout”错误](#gatewaytimeout)
   - [我收到“HTTP 414 请求 URI 太长”](#http-414-request-uri-too-long)
   - [我收到“无法显示此页”](#this-page-cant-be-displayed)
   - [我收到“500 - 内部服务器错误”](#internal-server-error)

#### <a name="general-ndes-message"></a>常规 NDES 消息

浏览到 SCEP 服务器 URL 时，你会收到以下网络设备注册服务消息：

![SCEP 服务器 URL](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **原因**：此问题通常是 Microsoft Intune 连接器安装的问题。

  Mscep.dll 是一个 ISAPI 扩展，可以截获传入的请求并在其安装正确时显示 HTTP 403 错误。
  
  **解决方法**：检查“SetupMsi.log”  文件，以确定是否成功安装了 Microsoft Intune 连接器。 在以下示例中，“已成功完成安装”  和“安装成功或错误状态：  0”表示安装成功：

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  如果安装失败，请删除 Microsoft Intune 连接器，然后重新安装它。

#### <a name="http-error-503"></a>HTTP 错误 503

浏览到 SCEP 服务器 URL 时，会收到以下错误：

![HTTP 错误 503。 此服务不可用](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

此问题通常是因为 IIS 中的 SCEP  应用程序池未启动。 在 NDES 服务器上，打开“IIS 管理器”  ，然后转到“应用程序池”  。 找到“SCEP”  应用程序池并确认它已启动。

如果未启动 SCEP 应用程序池，请检查服务器上的应用程序事件日志：

1. 在设备上，运行“eventvwr.msc”  以打开“事件查看器”  ，然后转到“Windows 日志”   > “应用程序”  。

2. 查找类似于以下示例的事件，这意味着接收到请求时，应用程序池崩溃：

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**导致应用程序池崩溃的常见原因**：

- **原因 1**：NDES 服务器的“受信任的根证书颁发机构”证书存储中存在中间 CA 证书（不是自签名证书）。

  **解决方法**：从“受信任的根证书颁发机构”证书存储中删除中间证书，然后重启 NDES 服务器。
  
  要在“受信任的根证书颁发机构”证书存储中标识所有中间证书，请运行以下 PowerShell cmdlet：`Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  具有相同的“颁发对象”  和“颁发机构”  值的证书是一个根证书。 否则，它是中间证书。

  删除证书并重启服务器后，再次运行 PowerShell cmdlet 以确认没有中间证书。 如果存在，请检查组策略是否将中间证书推送到 NDES 服务器。 如果是这样，请从组策略中排除 NDES 服务器，然后再次删除中间证书。

- **原因 2**：对于 Intune 证书连接器使用的证书，证书吊销列表 (CRL) 中的 URL 受阻或无法访问。

  **解决方法**：启用其他日志记录以收集详细信息：
  1. 打开事件查看器，单击“查看”  ，确保选中了“显示分析和调试日志”  选项。
  2. 转到“应用程序和服务日志”   > “Microsoft”   > “Windows”   > “CAPI2”   > “可操作”  ，右键单击“可操作”  ，然后单击“启用日志”  。
  3. 启用 CAPI2 日志记录后，重现问题，然后检查事件日志以解决问题。

- **原因 3**：CertificateRegistrationSvc  的 IIS 权限已启用“Windows 身份验证”  。

  **解决方法**：启用“匿名身份验证”  并禁用“Windows 身份验证”  ，然后重启 NDES 服务器。

  ![IIS 权限](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

浏览到 SCEP 服务器 URL 时，会收到以下错误：

![Gatewaytimeout 错误](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **原因**：Microsoft AAD 应用程序代理连接器  服务未启动。

  **解决方法**：运行“services.msc”  ，然后确保“Microsoft AAD 应用程序代理连接器”  服务正在运行，并且将“启动类型”  设置为“自动”  。

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 请求 URI 太长

浏览到 SCEP 服务器 URL 时，会收到以下错误：`HTTP 414 Request-URI Too Long`

- **原因**：未配置 IIS 请求筛选，以支持 NDES 服务收到的长 URL（查询）。 当[配置 NDES 服务](certificates-scep-configure.md#configure-the-ndes-service)以结合使用 SCEP 的基础结构时，就可以配置此支持。

- **解决方法**：配置对长网址的支持。

  1. 在 NDES 服务器中，打开 IIS 管理器，选择“默认网站” > “请求筛选” > “编辑功能设置”，以打开“编辑请求筛选设置”页面     。

  2. 配置下列设置：
     - 最大 URL 长度(字节) = 65534 
     - 最大查询字符串(字节) = 65534 

  3. 选择“确定”，保存此配置并关闭 IIS 管理器  。

  4. 定位以下注册表项以确认其具有指示的值，以验证此配置：

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     以下值设置为 DWORD 值：
     - 名称：MaxFieldLength  ，十进制值为 65534 
     - 名称：MaxRequestBytes  ，十进制值为 65534 

  5. 重启 NDES 服务器。

#### <a name="this-page-cant-be-displayed"></a>无法显示此页

已配置 Azure AD 应用程序代理。 浏览到 SCEP 服务器 URL 时，会收到以下错误：

`This page can't be displayed`

- **原因**：当应用程序代理配置中的 SCEP 外部 URL 不正确时，会发生此问题。 此 URL 的一个示例为 https://contoso.com/certsrv/mscep/mscep.dll 。

  **解决方法**：在应用程序代理配置中，为 SCEP 外部 URL 使用默认域 yourtenant.msappproxy.net  。

#### <a name="internal-server-error"></a>500 - 内部服务器错误

浏览到 SCEP 服务器 URL 时，会收到以下错误：

![500 - 内部服务器错误](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **原因 1**：NDES 服务帐户已锁定或其密码已过期。

  **解决方法**：解锁帐户或重置密码。

- **原因 2**：MSCEP-RA 证书已过期。

  **解决方法**：如果 MSCEP-RA 证书已过期，请重新安装 NDES 角色或请求新的“CEP 加密和 Exchange 注册代理(脱机请求)”证书。

  要请求新证书，请按照下列步骤操作：

  1. 在证书颁发机构 (CA) 上或颁发 CA 时，打开证书模板 MMC。 确保已登录的用户和 NDES 服务器对“CEP 加密和 Exchange 注册代理(脱机请求)”证书模板具有“读取”  和“注册”  权限。

  2. 检查 NDES 服务器上已过期的证书，从证书中复制“主题”  信息。

  3. 打开“计算机帐户”的证书 MMC  。

  4. 展开“个人”  ，右键单击“证书”  ，然后选择“所有任务”   > “申请新证书”  。

  5. 在“申请证书”  页上，选择“CEP 加密”  ，然后单击“注册此证书需要详细信息” **。单击这里以配置设置”** 。

     ![选择“CEP 加密”](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. 在“证书属性”  中，单击“主题”  选项卡，用在步骤 2 中收集的信息填充“主题名称”  ，单击“添加”  ，然后单击“确定”  。

  7. 完成证书注册。

  8. 打开“我的用户帐户”  的证书 MMC。

     在注册“Exchange 注册代理(脱机请求)”证书时，必须在用户上下文中完成注册。 因为此证书模板的“主题类型”  设置为“用户”  。

  9. 展开“个人”  ，右键单击“证书”  ，然后选择“所有任务”   > “申请新证书”  。

  10. 在“申请证书”  页面上，选择“Exchange 注册代理(脱机请求)”  ，然后单击“注册此证书需要详细信息” **。单击这里以配置设置”** 。

      ![选择“Exchange 注册代理”](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. 在“证书属性”  中，单击“主题”  选项卡，使用在步骤 2 中收集的信息填充“主题名称”  ，然后单击“添加”  。

      ![证书属性](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      选择“私钥”  选项卡，选择“使私钥可导出”  ，然后单击“确定”  。

      ![私钥](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. 完成证书注册。

  13. 从当前用户证书存储中导出“Exchange 注册代理(脱机请求)”证书。 在证书导出向导中，单击“是，导出私钥”  。

  14. 将证书导入到本地计算机证书存储。

  15. 在证书 MMC 中，对每个新证书执行以下操作：

      右键单击证书，单击“所有任务”   > “管理私钥”  ，向 NDES 服务帐户添加“读取”  权限。

  16. 运行“iisreset”  命令以重启 IIS。

## <a name="next-steps"></a>后续步骤

如果设备成功访问 NDES 服务器并提出证书申请，则下一步是检查 [Intune 证书连接器策略模块](troubleshoot-scep-certificate-ndes-policy-module.md)。
