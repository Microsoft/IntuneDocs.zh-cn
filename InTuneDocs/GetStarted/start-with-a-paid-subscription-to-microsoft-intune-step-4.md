---
# required metadata

title: 管理 Intune 许可证 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 管理 Intune 许可证
用户必须有你的 Intune 订阅的许可证，然后才能登录使用服务或将其设备注册到管理中。 如果用户有许可证，他们就是 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 用户组的成员。 此组包括拥有使用订阅的许可证的所有用户。 每个用户许可证支持注册最多 5 台设备

## 如何分配 Intune 许可证
当从本地上 Active Directory 同步用户帐户或通过帐户门户将用户帐户手动添加到云服务订阅时，将不会为用户帐户自动分配 Intune 许可证。 相反，Intune 租户管理员必须稍后编辑用户帐户才能从帐户门户中向用户分配许可证。

如果你的订阅与订阅的其他关联云服务共享 Azure AD，则你可以访问已添加到那些服务的用户。 在你为每个用户分配许可证之前，这些用户将没有 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的许可证。

> [!TIP]
> 如果禁用了用于分配或吊销 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 许可证的选项，则你的订阅可能包括批量许可选项，例如在使用[企业移动性套件](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx)时可用的选项。 有关如何分配或吊销许可证的信息，请参阅你的许可选项的文档。

## 分配 Intune 用户许可证

使用 **[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]** 手动添加基于云的用户并将许可证分配给基于云的用户帐户和从本地 Active Directory 同步到 Azure AD 的帐户。

1.  使用你的租户管理员凭据登录到 Intune 帐户门户。

2.  选择你想要为其分配 Intune 用户许可证的用户帐户并在用户帐户属性上启用 **Microsoft Intune** 复选框。

3.  用户帐户现在将添加到 Microsoft Intune 用户组，该用户组授予用户使用该服务和将设备注册到管理中的权限。

### 使用 PowerShell 来选择性地管理 EMS 用户许可证
使用 Microsoft 的企业移动性套件 (EMS) 的组织可能会有只需要 Azure Active Directory Premium 或 EMS 包中的 Intune 服务的用户。 你可以使用 [Azure Active Directory PowerShell cmdlet](https://msdn.microsoft.com/library/jj151815.aspx) 分配一个或一部分服务 

若要有选择性地为 EMS 服务分配用户许可证，请使用已安装的[用于 Windows PowerShell 的 Azure Active Directory 模块](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule)在计算机上以管理员身份打开 PowerShell。 你可以在本地计算机或 ADFS 服务器上安装 PowerShell。

必须创建仅应用于所需服务计划的新许可证 SKU 定义。 若要执行此操作，请禁用不想应用的计划。 例如，你可以创建一个不分配 Intune 许可证的许可证 SKU 定义。 若要查看从可用服务的列表，请键入：
 
    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus 

你可以运行下面的命令来排除 Intune 服务计划。 你可以使用相同的方法来扩展整个安全组，或者使用更精细的筛选器。 

示例 1

    Connect-MsolService 
        
    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS 
    

在命令行上创建一个新用户，并在不启用许可证的 Intune 部分的情况下分配一个 EMS 许可证：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

验证方式：

    Connect-MsolService 
    
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS
 
示例 2
 
    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![为已获得许可证的用户禁用 EMS 许可证的 Intune 部分：](./media/posh-addlic-verify.png)

### 验证方式：
PoSH-AddLic-Verify 后续步骤
>祝贺你！

>你刚刚完成了 *Intune 快速入门指南*的步骤 4  


<!--HONumber=May16_HO2-->


