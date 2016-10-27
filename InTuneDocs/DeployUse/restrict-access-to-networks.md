---
title: "使用 Cisco ISE 限制对网络的访问 | Microsoft Intune"
description: "将 Cisco ISE 与 Intune 配合使用，以便设备在访问由 Cisco ISE 控制的 Wi-Fi 和 VPN 前已注册 Intune 并且符合策略。"
keywords: 
author: nbigman
ms.author: nbigman
manager: angrobe
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 625d0851446c9cf54e704a62c9afe79cac263665
ms.openlocfilehash: 44dc8ce90537580ef30ba4b8c9f3ee2dd5e20c24


---

# 将 Cisco ISE 与 Microsoft Intune 配合使用
将 Intune 与 Cisco 身份服务引擎 (ISE) 集成使你能够使用 Intune 设备注册和合规性状态在 ISE 环境中编写网络策略。 你可使用这些策略确保对公司网络的访问权限仅限于由 Intune 托管并符合 Intune 策略的设备。

## 配置步骤

你无需在 Intune 租户中进行任何设置即可启用此集成。 你需要为 Cisco ISE 服务器提供访问你的 Intune 租户的权限。 完成此操作后，设置的剩余步骤将在你的 Cisco ISE 服务器中进行。 本文提供有关为 ISE 服务器提供对 Intune 租户的访问权限的说明。

### 步骤 1：管理证书
从 Azure Active Directory (Azure AD) 控制台导出证书，然后将其导入 ISE 控制台的受信任证书存储：

#### Internet Explorer 11


   a. 以管理员身份运行 Internet Explorer 并登录到 Azure AD 控制台。

   b。 在地址栏中选择锁定图标，然后选择“查看证书”。

   c. 在证书属性的“详细信息”选项卡上，选择“复制到文件”。

   d. 在“证书导出向导”欢迎页上，选择“下一步”。

   e. 在“导出文件格式”页上，保留默认值“DER 二进制编码 x.509 (.CER)”，然后选择“下一步”。  

   f. 在“要导出的文件”页上，选择“浏览”以选取要在其中保存文件的位置，并提供文件名。 尽管看起来似乎是你在选择要导出的文件，但实际上是在为导出的证书将要保存到的文件命名。 选择“下一步”&gt;“完成”。

   g. 从 ISE 控制台范围中，将 Intune 证书（你导出的文件）导入到“受信任的证书”存储中。

#### Safari

 a. 登录 Azure AD 控制台。

b。 选择锁定图标&gt;“详细信息”。

   c. 选择“查看证书”&gt;“详细信息”。

   d. 选择证书，然后选择“导出”。 

   e. 从 ISE 控制台范围中，将 Intune 证书（你导出的文件）导入到“受信任的证书”存储中。

> [!IMPORTANT]
>
> 请检查该证书的到期日期，因为当它过期时，将必须导出该证书并导入新证书。


### 从 ISE 中获取自签名证书 

1.  在 ISE 控制台中，转到“管理” > “证书” > “系统证书” > “生成自签名证书”。  
2.       导出自签名证书。
3. 在文本编辑器中，编辑导出的证书：[注释]：<> 在这两个语句的末尾不要加入句号，我认为这可能引起混淆。
 - 删除 ** -----BEGIN CERTIFICATE-----**
 - 删除 ** -----END CERTIFICATE-----**
 
确保所有文本都只占一行


### 步骤 2：在 Azure AD 租户中创建用于 ISE 的应用
1. 在 Azure AD 控制台中，选择“应用程序” > “添加应用程序” > “添加我的组织正在开发的应用程序”。
2. 提供应用的名称和 URL。 URL 可以是你的公司网站。
3. 下载应用清单（JSON 文件）。
4. 编辑清单 JSON 文件。 在名为“keyCredentials”的设置中，提供步骤 1 中经过编辑的证书文本作为设置值。
5. 保存该文件，但不更改其名称。
6. 为你的应用提供针对 Microsoft Graph 和 Microsoft Intune API 的权限。

 a. 对于 Microsoft Graph，选择以下各项：
    - **应用程序权限**：读取目录数据
    - **委托的权限**：
        - 随时访问用户的数据
        - 让用户登录

 b。 对于 Microsoft Intune API，在“应用程序权限”中，选择“从 Intune 获取设备状态和合规性”。

7. 选择“查看终结点”，并复制以下值以便在配置 ISE 设置时使用：

|Azure AD 门户中的值|ISE 门户中的对应字段|
|-------------------|---------------------------------|
|Microsoft Azure AD Graph API 终结点|自动发现 URL|
|Oauth 2.0 令牌终结点|令牌颁发 URL|
|使用你的客户端 ID 更新你的代码|客户端 ID|

### 步骤 4：将自签名证书从 ISE 上传到在 Azure AD 中创建的 ISE 应用
1.     获取 .cer X509 公用证书文件中的 base64 编码证书值和指纹。 此示例使用 PowerShell：
   
      
      $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2    $cer.Import(“mycer.cer”)    $bin = $cer.GetRawCertData()    $base64Value = [System.Convert]::ToBase64String($bin)    $bin = $cer.GetCertHash()    $base64Thumbprint = [System.Convert]::ToBase64String($bin)    $keyid = [System.Guid]::NewGuid().ToString()
 
    存储 $base64Thumbprint、$base64Value 和 $keyid 值，在下一步中使用。
2.       通过清单文件上传证书。 登录到 [Azure 管理门户](https://manage.windowsazure.com)
2.      在 Azure AD 管理单元中，找出想要配置 X.509 证书的应用程序。
3.      下载应用程序清单文件。 
5.      使用以下 JSON 替换空的“KeyCredentials”: [] 属性。  [实体和复杂类型参考](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType)中描述了 KeyCredentials 的复杂类型。

 
    “keyCredentials“: [ { “customKeyIdentifier“: “$base64Thumbprint_from_above”, “keyId“: “$keyid_from_above“, “type”: “AsymmetricX509Cert”, “usage”: “Verify”, “value”:  “$base64Value_from_above” }2. 
     ]， 
 
例如：
 
    “keyCredentials“: [
    {
    “customKeyIdentifier“: “ieF43L8nkyw/PEHjWvj+PkWebXk=”,
    “keyId“: “2d6d849e-3e9e-46cd-b5ed-0f9e30d078cc”,
    “type”: “AsymmetricX509Cert”,
    “usage”: “Verify”,
    “value”: “MIICWjCCAgSgAwIBA***omitted for brevity***qoD4dmgJqZmXDfFyQ”
    }
    ],
 
6.      保存更改到应用程序清单文件。
7.      通过 Azure 管理门户上传已编辑应用程序清单文件。
8.      可选：再次下载清单文件，检查应用程序上是否存在 X.509 证书。

>[!NOTE]
>
> KeyCredentials 证书是一个集合，因此可上传多个 X.509 证书以适应变更方案，或在泄露方案中删除证书。


### 步骤 4：配置 ISE 设置
在 ISE 管理控制台中，提供以下设置值：
  - “服务器类型”：移动设备管理器
  - “身份验证类型”：OAuth – 客户端凭据
  - “自动发现”：是
  - **自动发现 URL**：*输入步骤 1 中的值。*
  - **客户端 ID**：*输入步骤 1 中的值。*
  - **令牌颁发 URL**：*输入步骤 1 中的值。*



## Intune 租户和 Cisco ISE 服务器之间共享的信息
此表列出了你的 Intune 租户和用于由 Intune 托管的设备的 Cisco ISE 服务器之间共享的信息。

|属性|  描述|
|---------------|------------------------------------------------------------|
|complianceState|指示设备是否合规的 true 或 false 字符串。|
|isManaged|指示客户端是否由 Intune 托管的 true 或 false 字符串。|
|macAddress|设备的 MAC 地址。|
|serialNumber|设备的序列号。 仅适用于 iOS 设备。|
|imei|IMEI（15 个十进制数字：14 个数字加上 1 个校验数字）或 IMEISV（16 个数字）编号包含有关设备的来源、型号和序列号的信息。 3GPP TS 23.003 中指定了此编号的结构。 仅适用于有 SIM 卡的设备。|
|udid|唯一的设备标识符，这是一个包含 40 个字母和数字的序列。 它特定于 iOS 设备。|
|meid|移动设备标识符，是用于标识 CDMA 移动台设备的物理组成部分的全球唯一编号。 3GPP2 report S. R0048 定义此编号的格式。 但实际上，可将它视为十六进制数字的 IMEI。 MEID 的长度为 56 位（14 个十六进制数字）。 它由三个字段组成，包括一个 8 位区域代码 (RR)、一个 24 位制造商代码和一个 24 位制造商分配的序列号。|
|osVersion|设备的操作系统版本。
|model|设备型号。
|制造商|设备制造商。
|azureDeviceId|工作区加入 Azure AD 后的设备 ID。 对于未加入的设备，它为空 GUID。|
|lastContactTimeUtc|设备上次签入到 Intune 管理服务时的日期和时间。


## 用户体验

当用户尝试使用未注册的设备访问资源时，会收到注册提示，如下所示：

![注册提示示例](../media/cisco-ise-user-iphone.png)

当用户选择注册时，将被重定向到 Intune 注册过程。 以下主题中描述了 Intune 的用户注册体验：

- [在 Intune 中注册 Android 设备](/intune/enduser/enroll-your-device-in-Intune-android)</br>
- [在 Intune 中注册 iOS 设备](/intune/enduser/enroll-your-device-in-intune-ios)</br>
- [在 Intune 中注册 Mac OS X 设备](/intune/enduser/enroll-your-device-in-intune-mac-os-x)</br>
- [在 Intune 中注册 Windows 设备](/intune/enduser/enroll-your-device-in-intune-windows)</br>

此外，还可以使用 [downloadable set of enrollment instructions](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)（注册说明的可下载集）来为你的用户体验创建自定义指导。


### 另请参阅

[Cisco 标识服务引擎管理员指南，版本 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)



<!--HONumber=Oct16_HO1-->


