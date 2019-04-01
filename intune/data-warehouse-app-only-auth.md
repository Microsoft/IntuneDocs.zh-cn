---
title: Intune 数据仓库仅应用程序身份验证
titleSuffix: Microsoft Intune
description: 本主题介绍了 Microsoft Intune 数据仓库仅应用程序身份验证。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3511644b9de87cb3f2d36ad3f3c738663085c02
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57564782"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Intune 数据仓库仅应用程序身份验证

你可以使用 Azure Active Directory (Azure AD) 设置应用程序并通过 Intune 数据仓库进行身份验证。 此过程适用于应用程序不应在其中具有用户凭据访问权限的网站、应用和后台进程。 通过以下步骤，可以使用 OAuth 2.0 借助 Azure AD 向应用程序授权。

## <a name="authorization"></a>授权

Azure Active Directory (Azure AD) 使用 OAuth 2.0 使你能够在你的  Azure  AD  租户中授予对  Web  应用程序和  Web  API  的访问权限。 本指南介绍了如何使用 C# 对应用程序进行身份验证。 OAuth 2.0 规范的第 4.1 节介绍了 OAuth 2.0 授权代码流。 有关详细信息，请参阅[授权使用 OAuth 2.0 和 Azure Active Directory 访问 Web 应用程序](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)。


## <a name="azure-keyvault"></a>Azure Key Vault

以下过程通过专用方法处理和转换应用密钥。 此专用方法已命名为 SecureString。 或者，可以使用 Azure Key Vault 来存储应用密钥。 有关详细信息，请参阅 [Key Vault](https://azure.microsoft.com/services/key-vault/)。

## <a name="create-a-web-app"></a>创建 Web 应用

在本部分中，将详细介绍有关在 Intune 中要指向的 Web 应用。 Web 应用是客户端-服务器应用程序。 服务器提供 Web 应用，其中包括 UI、内容和功能。 此应用类型是在 Web 上单独进行维护的。 你可以使用 Intune 授予 Web 应用对 Intune 的访问权限。 数据流由 Web 应用启动。 

1.  登录到 [Azure 门户](https://portal.azure.com)。
2.  使用 Azure 门户顶部附近的“搜索资源、服务和文档”字段搜索“Azure Active Directory”。
3.  在下拉菜单中，选择“服务”下的“Azure Active Directory”。
4.  选择“应用注册”。
5.  单击“新应用程序注册”，以显示“创建”边栏选项卡。
6.  在“创建”边栏选项卡中，添加以下应用详细信息：

    - 应用名称，例如“Intune 仅应用身份验证”。
    - “应用程序类型”。 选择“Web 应用/API”，以添加一个表示 Web 应用程序和/或 Web API 的应用程序。
    - 应用程序的“登录 URL”。 进行身份验证期间用户将自动导航到这个位置。 用户需要证明自己所说的身份。 有关详细信息，请参阅[什么是 Azure Active Directory 的应用程序访问与单一登录？](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

7.  单击“创建”边栏选项卡底部的“创建”。

    >[!NOTE] 
    > 复制“已注册的应用”边栏选项卡中的“应用程序 ID”，以供以后使用。

## <a name="create-a-key"></a>创建密钥

在本部分中，Azure AD 将生成应用的密钥值。

1.  在“应用注册”边栏选项卡上，选择新创建的应用，以显示应用边栏选项卡。
2.  选择边栏选项卡顶部附近的“设置”，以显示“设置”边栏选项卡。
3.  在“设置”边栏选项卡上，选择“密钥”。
4.  添加密钥“说明”，即“过期”时间以及密钥的“值”。
5.  单击“保存”，以保存和更新应用程序的密钥。
6.  你必须将所生成的密钥值（base64 编码）复制下来。

    >[!NOTE] 
    > 因为离开“密钥”边栏选项卡后，将不再显示此密钥值， 以后将无法从此边栏选项卡检索此密钥。 请复制此密钥，以供以后使用。

## <a name="grant-application-permissions"></a>授予应用程序权限

在本部分中，将授予应用程序权限。

1.  在“设置”边栏选项卡上，选择“必需权限”。
2.  单击“添加” 。
3.  选择“添加 API”，以显示“选择 API”边栏选项卡。
4.  从“选择 API”边栏选项卡选择“Microsoft Intune API (MicrosoftIntuneAPI)”，然后单击“选择”。 已选择“选择权限”步骤，并已显示“启用访问权限”边栏选项卡。
5.  从“应用程序权限”部分选择“从 Microsoft Intune 获取数据仓库信息”选项。
6.  从“启用访问权限”边栏选项卡单击“选择”。
7.  从“添加 API 访问权限”边栏选项卡单击“完成”。
8.  从“必需权限”边栏选项卡单击“授予权限”，当提示更新此应用程序的任何已有权限时，单击“是”。

## <a name="generate-token"></a>生成令牌

使用 Visual Studio 创建支持 .NET Framework 并使用 C# 作为编码语言的控制台应用 (.NET Framework) 项目。

1.  选择“文件” > “新建” > “项目”，以显示“新建项目”对话框。
2.  在左侧选择“Visual C#”，以显示所有的 .NET Framework 项目。
3.  选择“控制台应用(.NET Framework)”，添加应用名称，然后单击“确定”，以创建应用。
4.  在“解决方案资源管理器”中，选择“Program.cs”，以显示代码。
5.  在弹出菜单中，选择“添加” > “新建项”。 随即将显示“添加新项”对话框。
6.  在左侧的“Visual C#”下，选择“代码”。
7.  选择“类”，将类的名称更改为“IntuneDataWarehouseClass.cs”，然后单击“添加”。
8.  将下列代码添加到 <code>Main</code> 方法中：

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

9. 在代码文件的顶部添加以下代码，以添加其他命名空间：

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

10. 在 <code>Main</code> 方法的后面添加以下专用方法，用于处理和转换应用密钥：

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

11. 在“解决方案资源管理器”中，右键单击“引用”，然后选择“管理 NuGet 程序包”。
12. 搜索“Microsoft.IdentityModel.Clients.ActiveDirectory”，然后安装相关的 Microsoft NuGet 程序包。
13. 在“解决方案资源管理器”中，选择并打开“App.config”文件。
14. 添加 <code>appSettings</code> 部分，使 xml 如下所示：

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

15. 更新 <code>appId</code>、<code>appKey</code> 和 <code>tenantDomain</code> 值，以与唯一的应用相关值匹配。
16. 生成应用。

    >[!NOTE] 
    > 若要查看其他实现代码，请参阅 [Intune 数据仓库代码示例](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp )。

## <a name="next-steps"></a>后续步骤
有关 Azure Key Vault 的详细信息，请查看[什么是 Azure Key Vault？](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)

