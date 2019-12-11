---
title: Jamf Pro 与 Microsoft Intune 的集成疑难解答
titleSuffix: Microsoft Intune
description: 在将 Jamf Pro for Mac 设备与 Microsoft Intune 集成时，解决一些最常见问题的建议。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44733eb369e520d2d5f0ff548d4f1921abcb8758
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503579"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>排查 Jamf Pro 与 Microsoft Intune 的集成问题

本文将帮助 Intune 管理员了解 Jamf Pro for macOS 与 Intune 的集成问题并解决这些问题。

> [!TIP]  
> 本文中的大部分信息最初都是在[将 Jamf 与 support.microsoft.com 上的 Microsoft Intune 进行集成时遇到的问题](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune)。

## <a name="prerequisites"></a>必备条件

在开始故障排除之前，请收集一些基本信息以阐明问题并缩短查找解决方法的时间。 例如，当遇到与 Jamf 集成相关的问题时，请始终验证是否满足了先决条件。 在开始故障排除之前，请查看以下注意事项：

- 查看将[Jamf Pro 与 Intune 集成](conditional-access-integrate-jamf.md#prerequisites)的先决条件。
- 所有用户都必须具有 Microsoft Intune 和 Microsoft AAD Premium P1 许可证 
- 您必须具有在 Jamf Pro 控制台中具有 Microsoft Intune 集成权限的用户帐户。
- 你必须拥有一个在 Azure 中具有全局管理员权限的用户帐户。


调查 Jamf Pro 与 Intune 的集成时，请考虑以下信息： 
- 确切错误消息是什么？
- 错误消息位于何处？
- 何时开始出现问题？  Intune 的 Jamf Pro 集成是否曾经工作？
- 有多少用户受到影响？ 所有用户是否受影响或只影响一些？
- 受影响的设备有多少？ 所有设备是否受影响或只影响一些？
 

## <a name="common-problems"></a>常见问题 

以下信息可帮助你确定和解决在设置 Intune 和 Jamf Pro 集成后设备的常见问题。  

| 问题   | 详细信息                  |
|-----------------|--------------------------|
| **设备在 Jamf Pro 中被标记为无响应**  | [设备无法与 Jamf Pro 或 with Azure AD 一起签入](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **打开应用时，Mac 设备提示进行密钥链登录无法注册**  | [系统会提示用户输入密码，以允许应用注册到 Azure AD](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)。 |
| **设备无法注册**  | 可能的原因如下： <br> **-** [***原因 1*** -Azure 中的 Jamf Pro 应用具有不正确的权限](#cause-1) <br> **-** [***原因 2*** -Azure AD 中的*Jamf 本机 macOS 连接器*存在问题](#cause-2) <br> **-** [***原因 3*** -用户没有有效的 Intune 或 Jamf 许可证](#cause-3) <br> **-** [***原因 4*** -用户未使用 Jamf 自助服务启动公司门户应用](#cause-4) <br> **-** [***原因 5*** -已关闭 Intune 集成](#cause-5) <br> **-** [***原因 6*** -设备之前已在 Intune 中注册，或用户多次尝试注册设备](#cause-6) <br> **-** [***引起 7*** -JamfAAD 请求访问用户密钥链的 "Microsoft Workplace Join 密钥"](#cause-7) |
|  **Mac 设备在 Intune 中显示符合，但在 Azure 中不相容** | [设备注册问题](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **使用 Jamf 注册的 Mac 设备的 Intune 控制台中显示重复项** | [用于同一设备的多个注册](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **合规性策略无法评估设备** | [策略目标设备组](#compliance-policy-fails-to-evaluate-the-device) |
| **无法检索 Microsoft Graph API 的访问令牌** | 可能的原因如下： <br> [Azure 中 Jamf Pro 应用](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure)的 -权限 <br> [Jamf 或 Intune - 过期的许可证](#a-license-required-for-jamf-intune-integration-has-expired) <br> **-** [端口未打开](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>设备在 Jamf Pro 中被标记为无响应  

**原因**：以下是 Jamf Pro 将设备标记为*无响应*的常见原因：

- 设备无法与 Jamf Pro 签入。  
  Jamf Pro 期望设备每15分钟检查一次。 如果设备在24小时内无法签入，Jamf 会将其标记为无响应。  

- 设备无法签入 Azure AD。  
  成功注册到 Azure AD 后，macOS 设备将收到 Azure 令牌：
  - 此令牌每12小时刷新一次。   
  - 当令牌刷新失败24小时或更长时间时，Jamf Pro 会将设备标记为无响应。  
  - 如果 Azure 令牌过期，则会提示用户登录到 Azure 以获取新令牌。 Azure 访问的刷新令牌每7天生成一次。

**解决方法**  
Jamf Pro 将设备标记为*无响应*后，设备的已注册用户必须登录才能更正无响应状态。 该用户必须是已加入该帐户的用户，因为他们在其登录密钥链中具有 Intune 中的标识。



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>打开应用时，Mac 设备提示进行密钥链登录  

配置 Intune 和 Jamf Pro 集成并部署条件访问策略后，在打开 Microsoft Office 365 应用程序（如团队、Outlook 和其他需要 Azure 的应用程序）时，使用 Jamf Pro 管理的设备的用户将收到密码提示AD 身份验证。 

例如，当打开 Microsoft 团队时，会出现一个提示，其中包含类似于以下示例的文本：

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**原因**：对于需要 Azure AD 注册的每个适用应用，Jamf Pro 会生成这些提示。 

**解决方法**   
在提示符下，用户必须提供其设备密码才能登录 Azure AD。 选项包括：
- **Deny** -不登录，不使用应用。
- **允许**-一次登录。 下次应用程序打开时，它会提示再次登录。
- **始终允许**-为应用程序缓存登录凭据。 下次应用程序打开时，它不会提示登录。  

选择 "*始终允许*单个应用" 只会批准该应用，以便以后登录。 其他应用会提示进行身份验证，直到它们也设置为 "*始终允许*"。 一个应用的缓存凭据不能被另一个应用使用。  

### <a name="devices-fail-to-register"></a>设备无法注册  

对于无法注册的 Mac 设备，有几个常见的原因。  

#### <a name="cause-1"></a>原因 1  

**Azure 中的 Jamf Pro 企业应用程序具有错误的权限或具有多个权限**  

  在 Azure 中创建应用时，必须删除所有默认 API 权限，然后向 Intune 分配*update_device_attributes*的单个权限。 

  **解决方法**  
  查看并根据需要更正在 Azure AD 中创建的 Jamf 应用程序的权限。 请参阅[在 Azure AD 中创建用于 Jamf 的应用程序](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory)的过程。 

#### <a name="cause-2"></a>原因 2  

**未在你的 Azure AD 租户中创建**Jamf 本机 MacOS 连接器**应用，或者同意使用没有全局管理员权限的帐户对连接器进行签名**  

  **解决方法**  
  请参阅 docs.jamf.com 上的[与 Microsoft Intune 集成](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html)中的*配置 macOS Intune 集成*部分。 

#### <a name="cause-3"></a>原因 3

**用户没有有效的 Intune 或 Jamf 许可证**  

  缺少有效的许可证可能会导致以下错误，这表明 Jamf 许可证已过期：  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **解决方法**
  - Jamf 许可证：若要获取 Jamf 的新许可，请联系 Jamf 获取帮助。  
  - Intune 许可证：向用户分配有效的许可证，或与 Microsoft 或合作伙伴联系，获取有关如何获取当前许可证的信息。

#### <a name="cause-4"></a>原因 4  

**用户未使用*Jamf 自助服务*启动公司门户的应用程序**

若要让设备通过 Jamf 成功注册并注册到 Intune，用户必须使用 Jamf 自助服务打开 Intune 公司门户。 如果用户手动打开公司门户，设备将注册并注册，而无需连接到 Jamf。  

若要确定设备用于注册和注册的服务，请查看设备上的公司门户应用。 通过 Jamf 注册后，你应该会收到通知，提示你打开自助服务应用以进行更改。

在公司门户应用程序中，用户可能会看到 **`Not registered`** ，但公司门户日志中可能会出现类似于以下示例的条目：  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**解决方法**  
若要将注册源从 Intune 更改为 Jamf：
1. [从 Intune 取消注册 macOS 设备](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos)。 若要避免从 Intune 完全删除的设备的更复杂，请参阅此原因列表中的[*原因 6*](#cause-6) 。  

2. 在设备上，使用 Jamf 自助服务打开公司门户应用，然后使用 Intune 注册设备。 此任务要求你[使用 Jamf 来部署用于 macOS 的公司门户应用](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)，并[在 Jamf Pro 中创建了一个向 Azure AD 注册用户设备的策略](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory)。  

3. 打开门户时，会看到提示你登录的第一个屏幕。 使用你的工作或学校帐户  

4. 公司门户确认帐户信息后会显示“设备注册”和“设备符合性”状态。 黄色三角形突出显示保护学校或工作 macOS 设备需采取的操作。 单击“开始”可开始注册。  

5. 如果系统出现提示，请键入计算机的登录信息。  
     
在管理中注册设备可能需要几分钟时间。 在此期间，可在设备上执行其他操作。 完成公司访问设置后，将收到一条消息，通知操作已完成。

#### <a name="cause-5"></a>原因 5  

**已关闭 Intune 集成**

如果已关闭 Intune 集成，则当用户尝试注册设备时，用户会在公司门户收到一个弹出窗口，并显示以下消息：  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

关闭集成后，Jamf Pro 服务器会将脉冲发送到 Intune 服务器，这会告诉 Intune 已禁用集成。 

**解决方法**  
在 Jamf Pro 中重新启用 Intune 集成。 请参阅[在 Jamf Pro 中配置 Microsoft Intune 集成](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro)。


#### <a name="cause-6"></a>原因 6  

**设备之前已在 Intune 中注册，或者用户已尝试多次注册设备**

如果设备从 Jamf 取消注册，但未从 Intune 中正确删除，或进行了多个注册尝试，则可能会在门户中看到同一设备的多个实例。 这会导致 Jamf 注册失败。

**解决方法**  
1. 在 Mac 上，启动**终端**。
2. 运行**SUDO JAMF removemdmprofile**。
3. 运行**SUDO JAMF removeFramework**。
4. 在 JAMF Pro 服务器上，删除计算机的清单记录。
5. 从 AzureAD 中删除设备。
6. 删除设备上的以下文件（如果存在）：
   - /Library/application support 支持/Companyportal.appx. usercontext
   - /Library/application support 支持/Companyportal.appx
   - /Library/application support 支持/jamfsoftware. selfservice
   - /Library/Saved 应用程序
   - Jamfsoftware. selfservice. savedState
   - /Library/Saved 应用程序状态/savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Users/<username>/Library/Cookies/com.microsoft.CompanyPortal.binarycookies
   - /Users/<username>/Library/Cookies/com.jamf.management.jamfAAD.binarycookies
   - Companyportal.appx
   - Companyportal.appx. HockeySDK
   - enterpriseregistration。windows。net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Microsoft 会话传输密钥（公钥和私钥）
   - Microsoft Workplace Join 密钥（公钥和私钥）
7. 从设备上的密钥链中删除引用*Microsoft*、 *Intune*或*公司门户*的任何内容，包括 DeviceLogin.microsoft.com 证书。 删除*JAMF*引用，除了 JAMF 公钥和私钥。 
   > [!IMPORTANT]  
   > 删除公钥和私钥将中断设备注册。

8. 删除你找到的以下任何条目：  
   - 类型：应用程序密码;帐户： workplacejoin。
   - 类型：应用程序密码;Account： workplacejoin. registeredUserPrincipalName
   - Kind： Certificate;颁发者： MS-组织访问
   - Kind：标识首选项;名称（如果存在，则为 ADFS STS URL）： https://adfs\<DNSName>.com/adfs/ls
   - Kind：标识首选项;名称： https://enterpriseregistration.windows.net
   - Kind：标识首选项;名称： https://enterpriseregistration.windows.net/  
9. 重新启动 Mac 设备。
10. 从设备中卸载公司门户。
11. 请访问 portal.manage.microsoft.com 并删除 Mac 设备的所有实例。 等待至少30分钟，然后再执行下一步。
12. 在 JAMF Pro 中重新注册设备。
13. 重新打开自助服务并启动注册策略。


#### <a name="cause-7"></a>原因 7  

**JamfAAD 请求从用户的密钥链访问 "Microsoft Workplace Join 密钥"**

注册期间，macOS 设备的用户将收到以下提示，以允许 JamfAAD 从其密钥链访问密钥： 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**解决方法**  
若要成功地将设备注册到 Azure AD，Jamf 要求用户提供其帐户密码，并选择 "**允许**"。

此请求类似于在本文前面的[打开应用时，对 Mac 设备的密钥链登录请求提示](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)。  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>Mac 设备在 Intune 中显示符合，但在 Azure 中不相容  

**原因**：以下情况可能导致设备在 Intune 中显示为合规，但在 Azure 中不符合要求：  
- 设备未正确注册。  
- 设备多次注册，但没有必要的清除操作。

**解决方法**  
若要解决此问题，请遵循本文前面的 "导致*设备无法注册*的[*原因 6*](#cause-6) " 的解决方法。 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>使用 Jamf 注册的 Mac 设备的 Intune 控制台中显示重复项  
 
**原因**：设备多次向 intune 注册，通常会在从 intune 中删除后重新注册。  

从 Intune 和 Jamf Pro 集成中删除设备后，某些数据可能会遗留，这可能会导致连续注册创建重复条目。  

**解决方法**  
若要解决此问题，请遵循本文前面的 "导致*设备无法注册*的[*原因 6*](#cause-6) " 的解决方法。 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>合规性策略无法评估设备  

**原因**：Jamf 与 Intune 的集成不支持针对设备组的符合性策略。 

**解决方法**  
修改要分配给用户组的 macOS 设备的符合性策略。 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>无法检索 Microsoft Graph API 的访问令牌

收到以下错误：

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

此错误的原因可能是以下原因之一： 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Azure 中的 Jamf Pro 应用程序存在权限问题

在 Azure 中注册 Jamf Pro 应用时，出现以下情况之一：  
- 应用收到了多个权限。
- 不选择 "**授予管理员 *\<公司 >***  " 选项。  

**解决方法**  
请参阅本文前面的 "导致[设备无法注册](#devices-fail-to-register)的原因 1" 的解决方法。

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Jamf-Intune 集成所需的许可证已过期

**解决方法**：请参阅原因3的解决方法：[设备注册失败](#devices-fail-to-register)。 

#### <a name="the-required-ports-arent-open-on-your-network"></a>网络上未打开所需的端口

**解决方法**：查看与 Intune 集成 Jamf Pro 的[先决条件](conditional-access-integrate-jamf.md#prerequisites)中的网络端口信息。


## <a name="next-steps"></a>后续步骤
了解有关将[Jamf Pro 与 Intune 集成的](conditional-access-integrate-jamf.md)详细信息