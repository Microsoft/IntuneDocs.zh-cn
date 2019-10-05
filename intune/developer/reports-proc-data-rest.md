---
title: 使用 REST 客户端从数据仓库 API 获取数据
titleSuffix: Microsoft Intune
description: 本主题介绍如何使用 RESTful API 从 Microsoft Intune 数据仓库检索数据。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 301e453baa15ce71e411ebc143d9201f4cb67aee
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733434"
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>使用 REST 客户端从 Intune 数据仓库 API 获取数据

可以通过 RESTful 终结点访问 Intune 数据仓库数据模型。 客户端必须使用 OAuth 2.0 获得 Microsoft Azure Active Directory (Azure AD) 授权后才能访问数据。 若要实现访问，首先需在 Azure 中设置本机应用，并授予 Microsoft Intune API 的访问权限。 本地客户端获取授权后，即可通过本机应用与数据仓库终结点进行通信。

若要将客户端设置为从数据仓库 API 获取数据，需执行以下步骤：

1. 在 Azure 中创建一个客户端应用作为本机应用
3. 授予该客户端应用访问 Microsoft Intune API 的权限
3. 创建一个本地 REST 客户端以获取数据

通过以下步骤了解如何使用 REST 客户端授权和访问 API。 首先，将了解使用 Postman 的通用 REST 客户端的使用方法。 Postman 是对 REST 客户端进行故障排除和开发使用 API 的 REST 客户端的常用工具。 有关 Postman 的详细信息，请参阅 [Postman](https://www.getpostman.com) 站点。 然后将介绍一个 C# 代码示例。 示例展示了如何向客户端授权并从 API 获取数据。

## <a name="create-a-client-app-as-a-native-app-in-azure"></a>在 Azure 中创建一个客户端应用作为本机应用

在 Azure 中创建本机应用。 此本机应用即客户端应用。 本地客户端请求凭据时，在本地计算机上运行的客户端将引用 Intune 数据仓库 API。

1. 登录到租户的 Azure 门户。 选择“Azure Active Directory” > “应用注册”，打开“应用注册”窗格    。
2. 选择“新建应用注册”  。
3. 键入应用详细信息。
    1. 在“名称”中键入易于理解的名称，例如 Intune 数据仓库客户端  。
    2. 对于“应用程序类型”，选择“本机”   。
    3. 在“登录 URL”中键入一个 URL  。 登录 URL 因具体方案不同而有所不同，但是如果计划使用 Postman，请键入 `https://www.getpostman.com/oauth2/callback`。 向 Azure AD 进行身份验证时，将针对客户端身份验证步骤使用回调。
4. 选择“创建”  。

     ![Intune 数据仓库客户端应用](./media/reports-proc-data-rest/reports-get_rest_data_client_overview.png)

5. 将此应用的“应用程序 ID”记下来  。 下一部分中将用到此 ID。

## <a name="grant-the-client-app-access-to-the-microsoft-intune-api"></a>授予该客户端应用访问 Microsoft Intune API 的权限

现在便有了一个在 Azure 中定义的应用。 授予从本机应用访问 Microsoft Intune API 的权限。

1. 选择本机应用。 使用类似于 Intune 数据仓库客户端的名称命名该应用  。
2. 从“设置”窗格中选择“所需权限”  
3. 在“所需权限”窗格中选择“添加”   。
4. 选择“选择 API”  。
5. 搜索 Web 应用名称。 其名称为“Microsoft Intune API”  。
6. 在列表中选择该应用。
7. 选择“选择”  。
8. 勾选“委派的权限”框，以添加“从 Microsoft Intune 获取数据仓库信息”   。

    ![启用访问 - Microsot Intune API](./media/reports-proc-data-rest/reports-get_rest_data_client_access.png)

9. 选择“选择”  。
10. 选择“完成”  。
11. 在“所需权限”窗格中，根据情况选择“授予权限”  。 此操作将授予对当前目录中的所有帐户的访问权限。 将不再为租户中的每位用户显示同意对话框。 有关详细信息，请参阅[将应用程序与 Azure Active Directory 集成](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)。
12. 选择“是”  。

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>使用 Postman 从 Microsoft Intune API 获取数据

可以通过 Postman 等常规 REST 客户端使用 Intune 数据仓库 API。 借助 Postman，可深入了解 API（基础 OData 数据模型）的各项功能，并且能够解决 API 资源连接问题。 本部分介绍为本地客户端生成 Auth2.0 令牌的相关信息。 客户端需使用令牌向 Azure AD 进行身份验证和访问 API 资源。

### <a name="information-you-will-need-to-make-the-call"></a>调用时所需信息

使用 Postman 进行 REST 调用时需要以下信息：

| 属性        | 描述                                                                                                                                                                          | 示例                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| 回调 URL     | 在应用设置页中将其设置为回调 URL。                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| 令牌名称       | 用于将凭据传递给 Azure 应用的字符串。 该过程会生成令牌，用于调用数据仓库 API。                          | 持有者                                                                                        |
| 身份验证 URL         | 这是用于进行身份验证的 URL。 | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/ |
| 访问令牌 URL | 这是用于授予令牌的 URL。                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| 客户端 ID        | 这是在 Azure 中创建本机应用时创建并记下来的 ID。                                                                                               | 4184c61a-e324-4f51-83d7-022b6a81b991                                                          |
| 作用域（可选） | 空                                                                                                                                                                               | 可以将该字段留空。                                                                     |
| 授权类型       | 令牌是一个授权代码。                                                                                                                                                  | 授权代码                                                                            |

### <a name="odata-endpoint"></a>OData 终结点

你还需要终结点。 要获取数据仓库终结点，将需要自定义源 URL。 可从“数据仓库”窗格中获取 OData 终结点。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 选择“Microsoft Intune - 概述”  边栏选项卡右侧“其他任务”  下的数据仓库链接，打开“Intune 数据仓库”  窗格。
4. 从“使用第三方报表服务”中复制自定义源 URL  。 它看上去应类似于：`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0`

终结点的格式如下所示：`https://fef.{yourtenant}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity}?api-version={verson-number}`

例如，日期实体看上去应类似于：`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0` 

有关详细信息，请参阅 [Intune 数据仓库 API 终结点](../reports-api-url.md)。

### <a name="make-the-rest-call"></a>进行 REST 调用

若要获取 Postman 的新访问令牌，必须添加 Azure AD 授权 URL，添加客户端 ID 和客户端密码。 Postman 将加载授权页面，需要在该页面中键入凭据。

#### <a name="add-the-information-used-to-request-the-token"></a>添加请求令牌时所需的信息

1. 如果尚未安装 Postman，请下载该工具。 若要下载 Postman，请参阅 [www.getpostman](https://www.getpostman.com)。
2. 打开 Postman。 选择 HTTP 操作“GET”  。
3. 将终结点 URL 粘贴到地址中。 如下所示：  

    `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. 选择“授权”选项卡，然后从“类型”列表中选择“OAuth 2.0”    。
5. 选择“获取新的访问令牌”  。
6. 验证确认已在 Azure 中将回调 URL 添加至应用。 回调 URL 为 `https://www.getpostman.com/oauth2/callback`。
7. 为“令牌名称”键入持有者  。
8. 添加“身份验证 URL”  。 它看上去应类似于：  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/`
9. 添加“访问令牌 URL”  。 它看上去应类似于：  

     `https://login.microsoftonline.com/common/oauth2/token`

10. 添加在 Azure 中创建并命名为 `Intune Data Warehouse Client` 的本机应用的“客户端 ID”  。 它看上去应类似于：  

     `88C8527B-59CB-4679-A9C8-324941748BB4`

11. 选择“授权代码”，并在本地请求访问令牌  。

12. 选择“请求令牌”  。

    ![访问令牌信息](./media/reports-proc-data-rest/reports-postman_getnewtoken.png)

13. 在 Active AD 授权页面中键入凭据。 Postman 中的令牌列表现包含名为 `Bearer` 的令牌。
14. 选择“使用令牌”  。 标头列表包含授权的新密钥值和值 `Bearer <your-authorization-token>`。

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>使用 Postman 发送终结点调用

1. 选择“发送”  。
2. 返回的数据显示在 Postman 响应正文中。

    ![Postman 客户端状态为 200 正常](./media/reports-proc-data-rest/reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>创建 REST 客户端 (C#) 以从 Intune 数据仓库获取数据

下面的示例包含一个简单的 REST 客户端。 该代码使用 .Net 库中的 httpClient .Net 类  。 客户端获得 Azure AD 凭据后，会构造一个 GET REST 调用，以检索数据仓库 API 中的日期实体。

> [!Note]  
> 可在 [GitHub](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs) 上访问以下代码示例。 请访问 GitHub 存储库，了解有关该示例的最新更改和更新。

1. 打开“Microsoft Visual Studio”  。
2. 选择“文件” > “新建项目”   。 展开“Visual C#”，然后选择“控制台应用 (.Net Framework)”   。
3. 将项目命名为 `IntuneDataWarehouseSamples`，浏览到要保存该项目的位置，然后选择“确定”  。
4. 在解决方案资源管理器中右键单击该解决方案的名称，然后选择“管理用于解决方案的 NuGet 包...”  。 选择“浏览”，然后在搜索框中键入 `Microsoft.IdentityModel.Clients.ActiveDirectory`  。
5. 选择该包，选择“管理用于解决方案的包”下的“IntuneDataWarehouseSamples”项目，然后选择“安装”   。
6. 选择“我接受”以接受 NuGet 包的许可  。
7. 从解决方案资源管理器打开 `Program.cs`。

    ![Visual Studio 中的 Progam.cs 和解决方案资源管理器](./media/reports-proc-data-rest/reports-get_rest_data_in.png)

8. 将 Program.cs 中的代码替换为以下代码  ：  

   ```csharp
   namespace IntuneDataWarehouseSamples
   {
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;
   using Microsoft.IdentityModel.Clients.ActiveDirectory;

   class Program
   {
    static void Main(string[] args)
   {
   /**
   * TODO: Replace the below values with your own.
   * emailAddress - The email address of the user that you will authenticate as.
   *
   * password  - The password for the above email address.
   *    This is inline only for simplicity in this sample. We do not
   *    recommend storing passwords in plaintext.
   *
   * applicationId - The application ID of the native app that was created in AAD.
   *
   * warehouseUrl   - The data warehouse URL for your tenant. This can be found in
   *      the Azure portal.
   *
   * collectionName - The name of the warehouse entity collection you would like to
   *      access.
   */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
   resource: "https://api.manage.microsoft.com/",
   clientId: applicationId,
   userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
   }
   }
   ```

9. 更新代码示例中的 `TODO`。
10. 按“Ctrl + F5”生成 Intune.DataWarehouseAPIClient 客户端并在调试模式下执行该客户端  。

    ![检索到的 JSON 格式的数据实体。](./media/reports-proc-data-rest/reports-get_rest_data_output.png)

11. 查看控制台输出。 该输出包含从 Intune 租户中的“日期”实体中拉取的 JSON 格式的数据  。

## <a name="next-steps"></a>后续步骤

有关授权、API URL 结构和 OData 终结点的详细信息，请参阅[使用 Intune 数据仓库 API](../reports-api-url.md)。

也可以参考 Intune 数据仓库数据模型，查找 API 中包含的数据实体。 有关详细信息，请参阅[Intune 数据仓库 API 数据模型](reports-ref-data-model.md)
