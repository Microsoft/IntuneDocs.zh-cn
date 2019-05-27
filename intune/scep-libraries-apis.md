---
title: 用于载入第三方证书颁发机构的 API
titleSuffix: Microsoft Intune
description: 为第三方证书颁发机构 (CA) 添加或集成 SCEP GitHub 解决方案，以向 Microsoft Intune 中的设备颁发 SCEP 证书。 此解决方案包括 Java 和 C# API，它们用于验证、向 Intune 发送成功和失败通知，以及在与 Intune 通信时使用 SSL 套接字工厂。 另请查看测试 SCEP CA 配置的步骤概述。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc2b324c8c6e1687b8ce5563aa85c155e21fc197
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040720"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>使用 API 将 SCEP 的第三方 CA 添加到 Intune

在 Microsoft Intune 中，可以添加第三方证书颁发机构 (CA)，然后让这些 CA 使用简单证书注册协议 (SCEP) 颁发和验证证书。 [添加第三方证书颁发机构](certificate-authority-add-scep-overview.md)概述了此功能并描述了 Intune 中的管理员任务。

还有一些开发人员任务使用 Microsoft 在 GitHub.com 上发布的开源代码库。 该库包含的 API 会执行以下操作：

- 验证 Intune 动态生成的 SCEP 密码
- 通知 Intune 在提交 SCEP 请求的设备上创建的证书

使用此 API，你的第三方 SCEP 服务器可与适用于 MDM 设备的 Intune SCEP 管理解决方案集成。 该库会从其用户中提取诸如身份验证、服务位置和 ODATA Intune 服务 API 等方面的信息。

## <a name="scep-management-solution"></a>SCEP 管理解决方案

![第三方认证机构 SCEP 与 Microsoft Intune 集成的方式](./media/scep-certificate-vendor-integration.png)

使用 Intune，管理员可以创建 SCEP 配置文件，然后将这些配置文件分配给 MDM 设备。 SCEP 配置文件包括参数，例如：

- SCEP 服务器的 URL
- 证书颁发机构的受信任的根证书
- 证书属性等

使用 Intune 签入的设备分配有 SCEP 配置文件，并配置了这些参数。 Intune 创建动态生成的 SCEP 质询密码，然后将其分配给设备。

此质询包含：

- 动态生成的质询密码
- 有关设备向 SCEP 服务器发出的证书签名请求 (CSR) 中预期参数的详细信息
- 质询到期时间

Intune 会加密此信息，对加密的 blob 进行签名，然后将这些详细信息打包到 SCEP 质询密码中。

设备联系 SCEP 服务器以请求证书，然后提供此 SCEP 质询密码。 SCEP 服务器将 CSR 和加密的 SCEP 质询密码发送到 Intune 以进行验证。  只有在质询密码和 CSR 通过验证后，SCEP 服务器才能向设备颁发证书。 进行 SCEP 质询验证时，会进行以下检查：


- 验证加密 blob 的签名
- 验证质询是否未过期
- 验证配置文件是否仍然针对设备
- 验证 CSR 中设备请求的证书属性是否与预期值匹配

SCEP 管理解决方案还包括报告。 管理员可以获取有关 SCEP 配置文件的部署状态以及颁发给设备的证书的信息。

## <a name="integrate-with-intune"></a>与 Intune 集成

在 [Microsoft/Intune-Resource-Access GitHub 存储库](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)中可以下载与 Intune SCEP 集成的库代码。

将库集成到产品中包括以下步骤。 这些步骤需要有关使用 GitHub 存储库以及在 Visual Studio 中创建解决方案和项目的知识。

1. 注册以接收来自存储库的通知
2. 克隆或下载存储库
3. 转到 `\src\CsrValidation` 文件夹下所需的库实现 (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
4. 使用 README 文件中的说明构建库
5. 在构建 SCEP 服务器的项目中包含库
6. 在 SCEP 服务器上完成以下任务：

    - 允许管理员配置库进行身份验证所使用的 [Azure 应用程序标识符、Azure 应用程序密钥和租户 ID](#onboard-scep-server-in-azure)（在本文中）。 应允许管理员更新 Azure 应用程序密钥。
    - 识别包含 Intune 生成的 SCEP 密码的 SCEP 请求
    - 使用“验证请求 API”库验证 Intune 生成的 SCEP 密码
    - 使用库通知 API 通知 Intune 已针对具有 Intune 生成的 SCEP 密码的 SCEP 请求发出的证书。 还要通知 Intune 在处理这些 SCEP 请求时可能会发生的错误。
    - 确认服务器记录了足够的信息以帮助管理员排查问题

7. 完成[集成测试](#integration-testing)（在本文中），并解决任何问题
8. 向客户提供书面指南，说明：

    - SCEP 服务器需要如何载入 Azure 门户
    - 如何获取配置库所需的 Azure 应用程序标识符和 Azure 应用程序密钥

### <a name="onboard-scep-server-in-azure"></a>在 Azure 中载入 SCEP 服务器

要对 Intune 进行身份验证，SCEP 服务器需要 Azure 应用程序 ID、Azure 应用程序密钥和租户 ID。 SCEP 服务器还需要有权访问 Intune API。

要获取此数据，SCEP 服务器管理员需登录到 Azure 门户，注册应用程序，为应用程序授予 Microsoft Intune API\SCEP 质询验证权限，为应用程序创建密钥，然后下载应用程序 ID、其密钥和租户 ID。

有关注册应用程序以及获取 ID 和密钥的指导，请参阅[使用门户创建 AAD 应用程序和服务主体以访问资源](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)。

### <a name="java-library-api"></a>Java 库 API

Java 库是作为 Maven 项目实现的，该项目在构建时会拉入其依赖项。 API 在 `com.microsoft.intune.scepvalidation` 命名空间下由 `IntuneScepServiceClient` 类实现。

#### <a name="intunescepserviceclient-class"></a>IntuneScepServiceClient 类

`IntuneScepServiceClient` 类包括 SCEP 服务用来验证 SCEP 密码、通知 Intune 已创建的证书以及列出任何错误的方法。

##### <a name="intunescepserviceclient-constructor"></a>IntuneScepServiceClient 构造函数

签名：

```java
IntuneScepServiceClient(
    Properties configProperties)
```

描述:

实例化和配置 `IntuneScepServiceClient` 对象。

参数：

    - configProperties    包含客户端配置信息的属性对象

配置必须包含以下属性：

    - AAD_APP_ID=“在载入过程中获得的 Azure 应用程序 ID”
    - AAD_APP_KEY=“在载入过程中获得的 Azure 应用程序密钥”
    - TENANT=“在载入过程中获得的租户 ID”
    - PROVIDER_NAME_AND_VERSION=“用于标识产品及其版本的信息”
    
如果解决方案需要具有身份验证或无身份验证的代理，则可以添加以下属性：

    - PROXY_HOST =“托管代理的主机。”
    - PROXY_PORT =“代理侦听的端口。”
    - PROXY_USER =“代理使用基本身份验证时所用的用户名。”
    - PROXY_PASS =“代理使用基本身份验证时所用的密码。”

引发：

    - IllegalArgumentException    在没有适当的属性对象的情况下执行构造函数时引发。

> [!IMPORTANT]
> 最好实例化此类的实例，并使用它来处理多个 SCEP 请求。 这样做可以减少开销，因为它可以缓存身份验证令牌和服务位置信息。

**安全说明**  
SCEP 服务器实施者必须保护永久保存到存储空间的配置属性中输入的数据，防止篡改和泄露。 建议使用适当的 ACL 和加密来保护信息。

##### <a name="validaterequest-method"></a>ValidateRequest 方法

签名：

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

描述:

验证 SCEP 证书请求。

参数：

    - transactionId         SCEP 事务 ID
    - certificateRequest    采用 DER 编码的 PKCS #10 证书请求，该请求通过 Base64 编码成为字符串

引发：

    - IllegalArgumentException      使用无效的参数进行调用时引发
    - IntuneScepServiceException    发现证书请求无效时引发
    - Exception                     遇到意外错误时引发

> [!IMPORTANT]
> 服务器应记录此方法引发的异常。 请注意，`IntuneScepServiceException` 属性具有证书请求验证失败的原因的详细信息。

**安全说明**  

  - 如果此方法引发异常，则 SCEP 服务器不得向客户端颁发证书。
  - SCEP 证书请求验证失败可能表示 Intune 基础结构中存在问题。 或者，他们可以表示攻击者正在尝试获取证书。

##### <a name="sendsuccessnotification-method"></a>SendSuccessNotification 方法

签名：

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

描述:

通知 Intune 在处理 SCEP 请求时创建了一个证书。

参数：

    - transactionId         SCEP 事务 ID
    - certificateRequest      采用 DER 编码的 PKCS #10 证书请求，该请求通过 Base64 编码成为字符串
    - certThumprint           预配证书的指纹
    - certSerialNumber        预配证书的序列号
    - certExpirationDate      预配证书的到期日期。 日期时间字符串应采取的格式为 Web UTC 时间 (YYYY-MM-DDThh:mm:ss.sssTZD) ISO 8601。
    - certIssuingAuthority    颁发证书的机构名称

引发：

    - IllegalArgumentException      使用无效的参数进行调用时引发
    - IntuneScepServiceException    发现证书请求无效时引发
    - Exception                     遇到意外错误时引发

> [!IMPORTANT]
> 服务器应记录此方法引发的异常。 请注意，`IntuneScepServiceException` 属性具有证书请求验证失败的原因的详细信息。

**安全说明**

  - 如果此方法引发异常，则 SCEP 服务器不得向客户端颁发证书。
  - SCEP 证书请求验证失败可能表示 Intune 基础结构中存在问题。 或者，他们可以表示攻击者正在尝试获取证书。

##### <a name="sendfailurenotification-method"></a>SendFailureNotification 方法

签名：

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

描述:

通知 Intune 在处理 SCEP 请求时出现错误。 不应对此类的方法引发的异常调用此方法。

参数：

    - transactionId         SCEP 事务 ID
    - certificateRequest    采用 DER 编码的 PKCS #10 证书请求，该请求通过 Base64 编码成为字符串
    - hResult               最能说明遇到的错误的 Win32 错误代码。 请参阅 [Win32 错误代码](https://msdn.microsoft.com/library/cc231199.aspx)
    - errorDescription      遇到的错误的描述

引发：

    - IllegalArgumentException      使用无效的参数进行调用时引发
    - IntuneScepServiceException    发现证书请求无效时引发
    - Exception                     遇到意外错误时引发

> [!IMPORTANT]
> 服务器应记录此方法引发的异常。 请注意，`IntuneScepServiceException` 属性具有证书请求验证失败的原因的详细信息。

**安全说明**

  - 如果此方法引发异常，则 SCEP 服务器不得向客户端颁发证书。
  - SCEP 证书请求验证失败可能表示 Intune 基础结构中存在问题。 或者，他们可以表示攻击者正在尝试获取证书。

##### <a name="setsslsocketfactory-method"></a>SetSslSocketFactory 方法

签名：

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

描述:

使用此方法通知客户端，在与 Intune 通信时必须使用指定的（而非默认的）SSL 套接字工厂。

参数：

    - factory    客户端应该用于 HTTPS 请求的 SSL 套接字工厂

引发：

    - IllegalArgumentException    使用无效的参数进行调用时引发

> [!NOTE]
> 在执行此类的其他方法之前，必须设置 SSL 套接字工厂（如果需要）。

## <a name="integration-testing"></a>集成测试

必须验证并测试解决方案是否与 Intune 正确集成。 以下列出了步骤概述：

1. 设置 [Intune 试用帐户](account-sign-up.md)。
2. [将 SCEP 服务器载入 Azure 门户](#onboard-scep-server-in-azure)（在本文中）。
3. 使用在载入 SCEP 服务器时创建的 ID 和密钥[配置 SCEP 服务器](certificates-scep-configure.md)。
4. [注册设备](device-enrollment.md)以测试[方案测试矩阵](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv)中的方案。
5. 为测试证书颁发机构[创建受信任的根证书配置文件](certificates-scep-configure.md)。
6. 创建 SCEP 配置文件以测试[方案测试矩阵](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv)中列出的方案。
7. 向已注册其设备的用户[分配配置文件](device-profile-assign.md)。
8. 等待设备与 Intune 同步。 或者，手动[同步设备](device-sync.md)。
9. 确认将受信任的根证书和 SCEP [配置文件部署到设备](device-profile-monitor.md)。
10. 确认所有设备上都安装了受信任的根证书。
11. 确认所有设备上都已安装分配的配置文件的 SCEP 证书。
12. 确认已安装证书的属性与 SCEP 配置文件中设置的属性相匹配。
13. 确认在 Intune 控制台中正确列出了已颁发的证书

## <a name="see-also"></a>另请参阅

- [添加第三方 CA 概述](certificate-authority-add-scep-overview.md)
- [安装 Intune](setup-steps.md)
- [设备注册](device-enrollment.md)
- [配置 SCEP 证书配置文件](certificates-scep-configure.md#create-a-scep-certificate-profile)（此方案不使用 Microsoft NDES Server\Connector 安装程序）
