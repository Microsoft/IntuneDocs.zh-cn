---
title: "如何使用 Intune 配置证书"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何使用 Intune 创建和分配证书，以保护 Wi-Fi、VPN 和其他连接的安全性。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 364534ad788466f8b268b4091decee5326b94163
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-configure-certificates-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置证书

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

通过 VPN、Wi-Fi 或电子邮件配置文件给予用户对公司资源的访问权限时，可以使用每个用户设备上安装的证书保护该访问权限。 高级工作流如下所示：

1. 确保具有正确的证书基础结构。 可以使用 [SCEP 证书](configure-certificate-infrastructure-for-scep.md)和 [PKCS 证书](configure-certificate-infrastructure-for-pfx.md)。
2. 在每台设备上安装根证书或中间证书颁发机构 (CA) 证书，以便该设备识别 CA 的合法性。 为此，创建并分配**受信任的证书配置文件**。 在分配此配置文件时，使用 Intune 托管的设备将请求并接收根证书。 必须为每个平台创建单独的配置文件。 受信任的证书配置文件可用于以下这些平台：
    - iOS 8.0 及更高版本
    - macOS 10.9 和更高版本
    - Android 4.0 和更高版本<!--Android for Work --->
    - Windows 8.1 及更高版本
    - Windows Phone 8.1 及更高版本
    - Windows 10 及更高版本
3. 创建证书配置文件以便设备请求&1; 个将用于对 VPN、Wi-Fi 和电子邮件访问进行身份验证的证书。 可以为运行以下平台的设备创建并部署 **PKCS** 或 **SCEP** 证书配置文件：
    - iOS 8.0 及更高版本
    - Android 4.0 及更高版本
    - Android for Work
    - Windows 10（桌面版和移动版）及更高版本

    对于以下平台只能使用 SCEP 证书配置文件：

-     macOS 10.9 和更高版本
-     Windows Phone 8.1 及更高版本

必须为每个设备平台创建单独的配置文件。 在创建配置文件时，将其与已创建的受信任的根证书配置文件关联。

### <a name="further-considerations"></a>更多注意事项

- 如果没有企业证书颁发机构，则必须创建一个。
- 如果你决定基于你的设备平台使用简化的证书注册协议 (SCEP) 配置文件，你还需要配置网络设备注册服务 (NDES) 服务器。
- 无论你计划使用 SCEP 配置文件还是 PKCS 配置文件，都必须下载并配置 Microsoft Intune 证书连接器。

## <a name="before-you-start"></a>开始之前


### <a name="if-you-want-to-use-scep-certificates"></a>如果想要使用 SCEP 证书

请完成 [SCEP 的证书基础结构](/intune-azure/configure-devices/configure-certificate-infrastructure-for-scep)中的必要先决条件。

### <a name="if-you-want-to-use-pkcs-certificates"></a>如果想要使用 PKCS 证书

请完成 [PKCS 的证书基础结构](/intune-azure/configure-devices/configure-certificate-infrastructure-for-pfx)中的必要先决条件。

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>任务 1：导出受信任的根 CA 证书
将受信任的根证书颁发机构 (CA) 证书从发证 CA 或从信任你的发证 CA 的任何设备中导出为“**.cer**”文件。 不要导出私钥。

设置受信任的证书配置文件时，将导入该证书。

## <a name="task-2-create-trusted-certificate-profiles"></a>任务 2：创建受信任的证书配置文件
必须创建受信任的证书配置文件，然后才能创建 SCEP 或 PKCS 证书配置文件。 对于每个设备平台，需要&1; 个受信任的证书配置文件和&1; 个 SCEP 或 PKCS 配置文件。

### <a name="to-create-a-trusted-certificate-profile"></a>创建受信任的证书配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“配置设备”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入受信任的证书配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，为此受信任证书选择设备平台。 目前，可以为设备限制设置选择以下平台之一：
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**
6. 从“配置文件”类型下拉列表中，选择“受信任的证书”。
7. 浏览到任务 1 中保存的证书，然后单击“确定”。
8. 从以下位置选择受信任证书的**目标存储区**（仅适用于 Windows 8.1 和 Windows 10 设备）：
    - **计算机证书存储区 - 根**
    - **计算机证书存储区 - 中间**
    - **用户证书存储区 - 中间**
8. 完成后，选择“确定”，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](how-to-assign-device-profiles.md)。


> [!Note]
> Android 设备将显示第三方已安装受信任的证书的通知。

## <a name="task-3-create-scep-or-pkcs-certificate-profiles"></a>任务 3：创建 SCEP 或 PKCS 证书配置文件
创建受信任的证书配置文件后，为要使用的各个平台创建 SCEP 或 PKCS 证书配置文件。 创建 SCEP 证书配置文件时，必须为相同平台指定受信任的证书配置文件。 尽管该平台链接了两个证书配置文件，但仍然必须单独分配各个配置文件。

### <a name="to-create-an-scep-certificate-profile"></a>创建 SCEP 证书配置文件

1. 在 Azure 门户中，选择“配置设备”工作负荷。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入 SCEP 证书配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，为此 SCEP 证书选择设备平台。 目前，可以为设备限制设置选择以下平台之一：
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**
6. 从“配置文件”类型下拉列表中，选择“SCEP 证书”。
7. 在“SCEP 证书”边栏选项卡上，配置下列设置：
    - **证书有效期** - 如果对发证 CA 运行允许自定义有效期的 **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** 命令，则可以指定证书过期之前剩余的时间量。<br>你可以指定比指定证书模板中的有效期小的值，但不能指定较大的值。 例如，证书模板中的证书有效期为&2; 年，则你可以指定值&1; 年，但不能指定值&5; 年。 该值还必须小于发证 CA 证书的剩余有效期。 
    - **密钥存储提供程序 (KSP)** (Windows Phone 8.1、Windows 8.1、Windows 10) - 指定将存储证书密钥的位置。 可以选择下列值之一：
        - **如果存在受信任的平台模块(TPM) KSP 则注册到它；否则注册到软件 KSP**
        - **注册到受信任的平台模块(TPM) KSP，否则失败**
        - **注册到 Passport，否则失败(Windows 10 及更高版本)**
        - **注册到软件 KSP**
    - “使用者名称格式” - 从列表中，选择 Intune 如何自动创建证书请求中的使用者名称。 如果证书用于用户，还可包含使用者名称中的用户电子邮件地址。 选择：
        - **不配置**
        - **公用名**
        - **包括电子邮件的公用名**
        - **公用名为电子邮件**
    - “使用者可选名称” - 指定 Intune 如何在证书请求中为使用者可选名称 (SAN) 自动创建值。 例如，你选择了用户证书类型，则可以在使用者可选名称中包括用户主体名称 (UPN)。 如果将使用客户端证书向网络策略服务器进行验证，则必须将使用者可选名称设置为 UPN。 
    - **密钥使用情况** - 指定证书的密钥使用情况选项。 可从以下选项中进行选择： 
        - **密钥加密：**仅在密钥加密时允许交换密钥。 
        - **数字签名：**仅在数字签名帮助保护密钥时允许交换密钥。 
    - **密钥大小（位数）** - 选择密钥中将包含的位数。 
    - **哈希算法** (Android、Windows Phone 8.1、Windows 8.1、Windows 10) - 选择要与此证书一起使用的可用哈希算法类型之一。 选择连接设备支持的最高级别安全性。 
    - **根证书** - 选择之前配置并分配到用户或设备的根 CA 证书配置文件。 此 CA 证书必须是将颁发在此证书配置文件中配置的证书的 CA 的根证书。 
    - **扩展的密钥使用情况** - 选择“添加”为证书的预期目的添加值。 大多数情况下，证书将需要“客户端身份验证”  以便用户或设备能够向服务器进行验证。 但，你可以根据需要添加任何其他密钥用法。 
    - **注册设置**
        - **续订阈值(%)** - 指定设备请求证书续订之前剩余的证书有效期限的百分比。
        - **SCEP 服务器 URL** - 为将通过 SCEP 颁发证书的 NDES 服务器指定&1; 个或多个 URL。 
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。

按照配置文件配置页上的说明配置 SCEP 证书配置文件设置。
>[!Note]
> 仅适用于 iOS 设备：在“使用者名称格式”中选择“自定义”，输入自定义使用者名称格式。
> 自定义格式当前支持的两个变量为**公用名 (CN)** 和**电子邮件 (E)**。 通过使用这些变量和静态字符串的组合，可以创建自定义主题名称格式，例如：**CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**。在此示例中，创建的主题名称格式除 CN 变量和 E 变量之外，对 Organizational Unit、Organization、Location、State 和 Country 的值使用字符串。 [本主题](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)介绍了 **CertStrToName** 函数及其支持的字符串。


### <a name="to-create-a-pkcs-certificate-profile"></a>创建 PKCS 证书配置文件

在 Azure 门户中，选择“配置设备”工作负荷。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在“配置文件”边栏选项卡上，单击“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入 PKCS 证书配置文件的“名称”和“说明”。
5. 从“平台”下拉列表的以下项中，为此 PKCS 证书选择设备平台：
    - **Android**
    - **iOS**
    - **Windows 10 及更高版本**
6. 从“配置文件”类型下拉列表中，选择“PKCS 证书”。
7. 在“PKCS 证书”边栏选项卡上，配置下列设置：
    - **续订阈值(%)** - 指定设备请求证书续订之前剩余的证书有效期限的百分比。
    - **证书有效期** - 如果对发证 CA 运行允许自定义有效期的 **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** 命令，则可以指定证书过期之前剩余的时间量。<br>你可以指定比指定证书模板中的有效期小的值，但不能指定较大的值。 例如，证书模板中的证书有效期为&2; 年，则你可以指定值&1; 年，但不能指定值&5; 年。 该值还必须小于发证 CA 证书的剩余有效期。
    - **密钥存储提供程序(KSP)** (Windows 10) -
    - **证书颁发机构** -
    - **证书颁发机构名称** -
    - **证书模板名称** - 输入网络设备注册服务配置为使用并且已添加到颁发 CA 的证书模板的名称。
    确保该名称与运行网络设备注册服务的服务器的注册表中所列证书模板名称之一完全匹配。 确保指定证书模板名称，而不是证书模板显示名称。 
    若要查找证书模板的名称，请浏览到以下项：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP。 你将看到作为 **EncryptionTemplate**、 **GeneralPurposeTemplate**和 **SignatureTemplate**的值而列出的证书模板。 默认情况下，所有三个证书模板的值为“IPSECIntermediateOffline”，映射为模板显示名称“IPSec (脱机请求)”。 
    - “使用者名称格式” - 从列表中，选择 Intune 如何自动创建证书请求中的使用者名称。 如果证书用于用户，还可包含使用者名称中的用户电子邮件地址。 选择：
        - **不配置**
        - **公用名**
        - **包括电子邮件的公用名**
        - **公用名为电子邮件**
    - “使用者可选名称” - 指定 Intune 如何在证书请求中为使用者可选名称 (SAN) 自动创建值。 例如，你选择了用户证书类型，则可以在使用者可选名称中包括用户主体名称 (UPN)。 如果将使用客户端证书向网络策略服务器进行验证，则必须将使用者可选名称设置为 UPN。
    - **扩展的密钥使用情况** (Android) - 选择“添加”为证书的预期目的添加值。 大多数情况下，证书将需要“客户端身份验证”  以便用户或设备能够向服务器进行验证。 但，你可以根据需要添加任何其他密钥用法。 
    - **根证书** (Android) - 选择之前配置并分配到用户或设备的根 CA 证书配置文件。 此 CA 证书必须是将颁发在此证书配置文件中配置的证书的 CA 的根证书。
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。

## <a name="task-4-assign-certificate-profiles"></a>任务 4：分配证书配置文件

将证书配置文件分配给组之前，考虑以下事项：

- 将证书配置文件分配给组时，将在设备上安装受信任的 CA 证书配置文件的证书文件。 设备使用 SCEP 或 PKCS 证书配置文件来创建设备需要的证书。
- 证书配置文件仅安装在运行你创建配置文件时使用的平台的设备上。
- 你可以对用户集或对设备集部署证书配置文件。
- 若要在设备注册后将证书快速发布到设备，请将证书配置文件部署到用户组（而不是部署到设备组）。 如果部署到设备组，则需要在设备接收策略前进行完整的设备注册。
- 尽管单独部署每个配置文件，但仍需部署受信任的根 CA 和 SCEP 或 PKCS 配置文件。 否则，SCEP 或 PKCS 证书策略将失败。

## <a name="next-steps"></a>后续步骤
有关如何分配设备配置文件的信息，请参阅[如何分配设备配置文件](how-to-assign-device-profiles.md)。

