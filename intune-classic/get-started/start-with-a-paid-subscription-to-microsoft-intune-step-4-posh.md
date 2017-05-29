---
title: "使用 PowerShell 管理 Intune 许可证 | Microsoft Docs"
description: "使用 PowerShell 管理 Intune 许可证"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 211b1aba54924204a7e2d33301824f9d7eb9c030
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="manage-intune-licenses-using-powershell"></a>使用 PowerShell 管理 Intune 许可证

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题指导管理员如何使用 PowerShell 管理 Intune 用户许可证。

在登录以使用 Intune 服务或将设备注册到管理组件之前，你必须首先为每个用户分配一个 Intune 订阅的许可证，如[管理 Intune 许可证](start-with-a-paid-subscription-to-microsoft-intune-step-4.md)中所述。 但是，使用 Microsoft 企业移动性 + 安全性的组织可能会有只需要 Azure Active Directory Premium 或 EMS 包中的 Intune 服务的用户。 你可以使用 [Azure Active Directory PowerShell cmdlet](https://msdn.microsoft.com/library/jj151815.aspx) 分配一个或一部分服务。

若要有选择性地为 EMS 服务分配用户许可证，请使用已安装的[用于 Windows PowerShell 的 Azure Active Directory 模块](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule)在计算机上以管理员身份打开 PowerShell。 你可以在本地计算机或 ADFS 服务器上安装 PowerShell。

必须创建仅应用于所需服务计划的新许可证 SKU 定义。 若要执行此操作，请禁用不想应用的计划。 例如，你可以创建一个不分配 Intune 许可证的许可证 SKU 定义。 若要查看从可用服务的列表，请键入：

    (Get-MsolAccountSku | Where {$\_.SkuPartNumber -eq "EMS"}).ServiceStatus

你可以运行下面的命令来排除 Intune 服务计划。 你可以使用相同的方法来扩展整个安全组，或者使用更精细的筛选器。

**示例 1** 在命令行上创建一个新用户，并在不启用许可证的 Intune 部分的情况下分配一个 EMS 许可证：

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


验证方式：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**示例 2** 为已获得许可证的用户禁用 EMS 许可证的 Intune 部分：

    Connect-MsolService

    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS

验证方式：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

### <a name="next-steps"></a>后续步骤
祝贺你！ 你刚刚完成了 *Intune 快速入门指南*的步骤 4。
>[!div class="step-by-step"]

>[&larr; **将用户同步到 Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**组织用户和设备** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  

