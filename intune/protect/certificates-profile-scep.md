---
title: 在 Microsoft Intune 中使用 SCEP 证书配置文件 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建和分配简单证书注册协议 (SCEP) 证书配置文件。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a3cfcc4ac0c5125324102c55dc7bc887006df6b
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801425"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>在 Intune 中创建和分配 SCEP 证书配置文件

[配置基础结构](certificates-scep-configure.md)以支持简单证书注册协议 (SCEP) 证书之后，即可创建 SCEP 证书配置文件，然后将其分配给 Intune 中的用户和设备。

> [!IMPORTANT]  
> 对于将使用 SCEP 证书配置文件的设备，在创建 SCEP 证书配置文件之前，该设备必须信任受信任的根证书颁发机构 (CA)。 在 Intune 中使用受信任的证书配置文件为用户和设备预配受信任的根 CA 证书  有关受信任证书配置文件的信息，请参阅“在 Intune 中使用证书进行身份验证”中的[导出受信任的根 CA 证书](certificates-configure.md#export-the-trusted-root-ca-certificate)和[创建受信任的证书配置文件](certificates-configure.md#create-trusted-certificate-profiles)  。


## <a name="create-a-scep-certificate-profile"></a>创建 SCEP 证书配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “配置文件”   > “创建配置文件”  。

3. 输入以下属性：

4. 为 SCEP 证书配置文件输入“名称”和“说明”   。

5. 从“平台”  下拉列表中，为此 SCEP 证书选择[支持的设备平台](certificates-configure.md#supported-platforms-and-certificate-profiles)。

6. 从“配置文件类型”下拉列表中，选择“SCEP 证书”   。  

   对于 Android Enterprise 平台，配置文件类型分为以下两类   ：“仅限设备所有者”  和“仅限工作配置文件”  。 确保为所管理的设备选择正确的 SCEP 证书配置文件。  

   “仅限设备所有者”  配置文件的 SCEP 证书配置文件具有以下限制：

   1. 不支持以下变量：

      - CN={{OnPrem_Distinguished_Name}}
      - CN={{onPremisesSamAccountName}}

   2. 在“监视”下，证书报表不可用于设备所有者 SCEP 证书配置文件。

   3. 不能使用 Intune 撤销由 SCEP 证书配置文件为设备所有者预配的证书。 可以通过外部进程或直接通过证书颁发机构来实现撤销。 

7. 选择“设置”，然后完成以下配置  ：

   - **证书类型**：

     （适用对象：  Android、Android Enterprise、iOS、macOS、Windows 8.1 和更高版本以及 Windows 10 和更高版本。）

     根据证书配置文件的使用方式选择类型：

     - **用户**：“用户”证书类型可包含证书使用者和 SAN 中的用户和设备属性  。  
     - **设备**：“设备”证书只能在证书主题和 SAN 中包含设备属性  。

       “设备”适用于无用户设备的情况（如展台）或 Windows 设备  。 在 Windows 设备上，证书位于本地计算机证书存储中。

   - **使用者名称格式**：

     选择 Intune 如何自动创建证书请求中的使用者名称。 使用者名称格式的选项取决于所选的证书类型，即“用户”或“设备”   。

     > [!NOTE]
     > 当生成的证书签名请求 (CSR) 中的使用者名称包含以下字符之一作为转义字符（后跟反斜杠 \\）时，使用 SCEP 获取证书存在[已知问题](#avoid-certificate-signing-requests-with-escaped-special-characters)：
     > - \+
     > - ;
     > - 、
     > - =

     - **“用户”证书类型**

       “使用者名称格式”的格式选项包括  ：

       - 未配置 
       - 公用名称 
       - 包含电子邮件地址的公用名称 
       - 作为电子邮件地址的公用名称 
       - IMEI（国际移动设备标识） 
       - **序列号**
       - **自定义**：选中此选项时，也会显示“自定义”文本框  。 使用此字段输入一个自定义使用者名称格式，包括变量。 自定义格式支持两种变量：公用名 (CN)  和电子邮件 (E)  。 可将“公用名(CN)”设置为以下任何变量  ：

         - **CN={{UserName}}** ：用户的用户主体名称，例如 janedoe@contoso.com。
         - **CN={{AAD_Device_ID}}** ：在 Azure Active Directory (AD) 中注册设备时分配的 ID。 此 ID 通常用于向 Azure AD 进行身份验证。
         - **CN={{SERIALNUMBER}}** ：制造商通常用于标识设备的唯一序列号 (SN)。
         - **CN={{IMEINumber}}** ：用于标识移动电话的国际移动设备标识 (IMEI)。
         - **CN={{OnPrem_Distinguished_Name}}** ：用逗号分隔的一系列相对可分辨名称，如 CN=Jane Doe、OU=UserAccounts、DC=corp、DC=contoso、DC=com  。

           要使用 {{OnPrem_Distinguished_Name}} 变量，请确保使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 将onpremisesdistinguishedname 用户属性与 Azure AD 同步   。

         - **CN={{onPremisesSamAccountName}}** ：管理员可以使用 Azure AD 连接到名为 onPremisesSamAccountName 的属性，将 Active Directory 中的 samAccountName 属性同步到 Azure AD  。 Intune 可以将该变量替换为证书使用者中的证书颁发请求的一部分。 samAccountName 属性是指用户登录名，该名称用于支持早期版本的 Windows（Windows 2000 之前）中的客户端和服务器。 用户登录名的格式为：DomainName\testUser，或仅 testUser   。

            要使用 {{onPremisesSamAccountName}} 变量，请确保使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 将 onPremisesSamAccountName 用户属性与 Azure AD 同步   。

         通过使用这些变量的一个或多个与静态字符串的组合，可以创建一个自定义使用者名称格式，例如：  
         - CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US 

         该示例包含使用者名称格式，其中除了不仅使用了 CN 和 E 变量，还使用了组织单元、组织、位置、省/直辖市/自治区和国家/地区值的字符串。 [CertStrToName 函数](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)介绍此函数及其支持的字符串。

      - **“设备”证书类型**

        “使用者名称格式”的格式选项包括以下变量：

        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}** （仅适用于 Windows 和加入域的设备） 
        - **{{MEID}}**

        可在文本框中指定这些变量，后跟变量的文本。 例如，可以将名为 Device1 的设备的公用名添加为 CN={{DeviceName}}Device1   。

        > [!IMPORTANT]
        > - 指定变量时，请将变量名称括在大括号 {} 中（如示例中所示），以避免出现错误。  
        > - 在设备证书的使用者或 SAN 中使用的设备属性（例如 IMEI、SerialNumber 和 FullyQualifiedDomainName）可能被有权访问设备的人员仿造      。
        > - 设备必须支持在证书配置文件中为该配置文件指定的所有变量，才能在该设备上安装。  例如，如果在 SCEP 配置文件的使用者名称中使用 {{IMEI}} 并将其分配给没有 IMEI 号码的设备，则配置文件安装将失败  。

   - **使用者备用名称**：选择 Intune 在证书请求中自动创建使用者可选名称 (SAN) 的方式。 SAN 的选项取决于所选的证书类型，即“用户”或“设备”   。

      - **“用户”证书类型**

        从可用属性中进行选择：

        - **电子邮件地址**
        - **用户主体名称 (UPN)**

        例如，用户证书类型可以在使用者可选名称中包含用户主体名称 (UPN)。 如果使用客户端证书向“网络策略服务器”进行身份验证，则要将使用者可选名称设置为 UPN。

      - **“设备”证书类型**

        使用“属性”下拉列表并选择一个属性，分配一个值并将该值添加到证书配置文件中    。 可以通过选择其他属性来添加多个值。

        可用的属性包括：

        - **电子邮件地址**
        - **用户主体名称 (UPN)**
        - **DNS**

        凭借“设备”证书类型，可以对值使用以下设备证书变量  ：

        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        要为属性指定一个值，请用大括号将变量名称括起来，后跟该变量的文本。 例如，可以为 DNS 属性添加一个值 {{AzureADDeviceId}}.domain.com，其中 .domain.com 是文本   。 对于名为 User1 的用户，电子邮件地址可能显示为 {{FullyQualifiedDomainNameUser1@Contoso.com}}  。

        > [!IMPORTANT]
        > - 使用设备证书变量时，请将变量名称括在大括号 { } 内。
        > - 请勿在变量后面的文本中使用大括号“{ }”、竖线符号“|”以及分号“;”    。
        > - 在设备证书的使用者或 SAN 中使用的设备属性（例如 IMEI、SerialNumber 和 FullyQualifiedDomainName）可能被有权访问设备的人员仿造      。
        > - 设备必须支持在证书配置文件中为该配置文件指定的所有变量，才能在该设备上安装。  例如，如果在 SCEP 配置文件的 SAN 中使用 {{IMEI}} 并将其分配给没有 IMEI 号码的设备，则配置文件安装将失败  。

   - **证书有效期**：

     可以在证书模板中输入低于（但不能高于）有效期的值。 如果将证书模板配置为[支持可从 Intune 控制台设置的自定义值](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template)，请使用此设置来指定证书过期之前的剩余时间量。

     例如，如果证书模板中的证书有效期为 2 年，则输入值可以为 1 年，但不能为 5 年。 该值还必须小于发证 CA 证书的剩余有效期。

   - **密钥存储提供程序 (KSP)** ：

     （适用对象：  Windows 8.1 和更高版本以及 Windows 10 和更高版本）

     指定存储证书密钥的位置。 从下面的值中进行选择：

     - 注册到受信任的平台模块(TPM) KSP (若有); 否则，注册到软件 KSP 
     - 注册到受信任的平台模块(TPM) KSP，否则失败 
     - 注册到 Passport，否则失败(Windows 10 及更高版本) 
     - **注册到软件 KSP**

   - **密钥用法**：

     选择证书的密钥用法选项：

     - **数字签名**：仅当数字签名有助于保护密钥时才允许密钥交换。
     - **密钥加密**：仅在密钥已加密时才允许密钥交换。

   - **密钥大小（位）** ：

     选择密钥中包含的位数。

   - **哈希算法**：

     （适用对象：Android、Android Enterprise、Windows Phone 8.1、Windows 8.1 和更高版本以及 Windows 10 和更高版本。  ）

     选择要与此证书一起使用的可用哈希算法类型之一。 选择连接设备支持的最高级别安全性。

   - **根证书**：

     选择受信任的证书配置文件，该配置文件是之前被配置并分配给此 SCEP 证书配置文件的适用用户和设备  。 受信任的证书配置文件用于预配具有受信任的根 CA 证书的用户和设备。 有关受信任证书配置文件的信息，请参阅“在 Intune 中使用证书进行身份验证”中的[导出受信任的 CA 证书](certificates-configure.md#export-the-trusted-root-ca-certificate)和[创建受信任的证书配置文件](certificates-configure.md#create-trusted-certificate-profiles)  。 如果具有根证书颁发机构和证书发证机构，请选择与证书发证机构关联的受信任的根证书配置文件。

   - **扩展密钥用法**：

     为证书的预期目的添加值。 大多数情况下，证书需要“客户端身份验证”以便用户或设备能够向服务器进行验证  。 可根据需要添加其他密钥用法。

   - **续订阈值 (%)** ：

     输入设备请求证书续订之前剩余的证书有效期限的百分比。 例如，如果输入“20”，将在证书的有效期限已使用 80% 时尝试续订证书。 将持续尝试续订，直到续订成功。 续订会生成新的证书，从而生成新的公钥/私钥对。

   - **SCEP 服务器 URL**：

     为通过 SCEP 颁发证书的 NDES 服务器输入 1 个或多个 URL。 例如，输入类似于 https://ndes.contoso.com/certsrv/mscep/mscep.dll 的内容  。 可根据需要添加其他用于负载均衡的 SCEP URL，因为 URL 会被随机推送到具有配置文件的设备。 如果某台 SCEP 服务器不可用，则 SCEP 请求将会失败，并且在稍后的设备签入中，可能针对这台已关闭的服务器发出证书请求。

8. 选择“确定”，然后选择“创建”   。 该配置文件已创建并显示在“设备配置 - 配置文件”  列表中。

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>避免证书签名请求中包含转义的特殊字符

包含用以下一个或多个特殊字符作为转义字符的使用者名称 (CN) 的 SCEP 和 PKCS 证书请求存在一个已知问题。 将其中一个特殊字符作为转义字符的使用者名称将导致 CSR 中使用者名称不正确。 错误的使用者名称会导致 Intune SCEP 质询验证失败，并且不会颁发证书。

特殊字符为：
- \+
- 、
- ;
- =

当使用者名称包含一个特殊字符时，请使用以下选项之一来解决此限制：

- 用引号封装包含特殊字符的 CN 值。  
- 删除 CN 值中的特殊字符。

例如，使用者名称显示为 Test user (TestCompany, LLC)   。  如果 CSR 包含一个 CN，该 CN 在 TestCompany 和 LLC 之间有逗号，则会出现问题   。  可以通过在整个 CN 周围加上引号，或者删除 TestCompany 和 LLC   之间的逗号来避免这一问题：

- **添加引号**：*CN=* ”Test User (TestCompany, LLC)”,OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **删除逗号**：*CN=Test User (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 但是，使用反斜杠字符转义逗号的尝试将失败，CRP 日志中出现错误：
 
- **转义的逗号**：*CN=Test User (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

此错误类似于以下错误：

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>分配证书配置文件

分配 SCEP 证书配置文件的方法与[部署设备配置文件](../configuration/device-profile-assign.md)以实现其他目的相同。 但在继续之前，请考虑以下事项：

- 将 SCEP 证书配置文件分配给组时，将在设备上安装受信任的根 CA 证书文件（如“受信任的证书配置文件”中所述）  。 设备使用 SCEP 证书配置文件来为该受信任的根 CA 证书创建证书请求。

- SCEP 证书配置文件仅安装在特定设备上，该设备可运行你在创建证书配置文件时指定的平台。

- 可以向用户集合或设备集合分配证书配置文件。

- 若要在注册设备后向设备快速发布证书，请将证书配置文件分配给用户组（而不是设备组）。 如果分配到设备组，则需要在设备接收策略前进行完整的设备注册。

- 如果使用 Intune 和 Configuration Manager 的共同管理，请在 Configuration Manager 中将资源访问策略的[工作负载滑块](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)设置为“Intune”或“试点 Intune”   。 此设置允许 Windows 10 客户端启动请求证书的过程。

- 尽管可单独创建和分配受信任的证书配置文件和 SCEP 证书配置文件，但必须分配这两种配置文件。 如果未在同一台设备上安装这两者，SCEP 证书策略将失败。 请确保所有受信任的根证书配置文件也都部署到 SCEP 配置文件所在的组。

> [!NOTE]
> 在 iOS 设备上，当 SCEP 证书配置文件与其他配置文件（如 Wi-Fi 或 VPN 配置文件）相关联，设备将收到其他每个配置文件的证书。 这会使 iOS 设备拥有 SCEP 证书请求提供的多个证书。  如果需要单个证书，则必须使用 PKCS 证书，而不是 SCEP 证书。  这是因为 SCEP 和 PKCS 证书传递到设备的方式不同。

## <a name="next-steps"></a>后续步骤

[分配配置文件](../configuration/device-profile-assign.md)
