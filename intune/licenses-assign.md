---
title: "分配 Intune 许可证"
description: "为你的 Intune 订阅用户分配许可证"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 06/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: f4f84acfa48c0de6e1478be3ee8624a7fd4841ad
ms.openlocfilehash: 6116ccd5614a1ff3eb528f8f0ac2eb87565534a2
ms.contentlocale: zh-cn
ms.lasthandoff: 06/16/2017


---

# <a name="assign-intune-licenses-to-your-user-accounts"></a>将 Intune 许可证分配给用户帐户

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

不管是手动添加用户还是从本地 Active Directory 同步，都必须首先为每个用户分配一个 Intune 许可证，然后用户才能在 Intune 中注册其设备。

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>在 Office 365 管理中心分配 Intune 许可证

可以使用 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)手动添加基于云的用户并将许可证分配给基于云的用户帐户和从本地 Active Directory 同步到 Azure AD 的帐户。

1.  使用你的租户管理员凭据登录到 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)，然后选择“用户” > “活动用户”。

2.  选择你想要为其分配 Intune 用户许可证的用户帐户，然后选择“产品许可证” > “编辑”。

3.  将 **Intune** 或**企业移动性 + 安全性**切换为“打开”，然后选择”保存”。

4. 现在，该用户帐户拥有所需的权限，可以使用该服务并在管理组件中注册设备。

> [!NOTE]
> 用户仅在注册设备后才会显示在管理控制台中。 此外，你还可以选择要立即编辑的一组用户，为所选的用户选择添加或替换许可证。

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>使用“学校数据同步”向 Intune for Education 中的用户分配许可证
如果你是教育组织，可以使用“学校数据同步 (SDS)”向同步用户分配 Intune for Education 许可证。 只需在设置 SDS 配置文件时，选中“Intune for Education”复选框。  

![SDS 配置文件设置图像](./media/i4e-sds-profile-setup-setting.png)

分配 Intune for Education 许可证时，请确保同时分配 Intune A Direct 许可证。

![产品许可证设置图像](./media/i4e-set-licenses.png)

请参阅此[学校数据同步概述](https://support.office.com/en-us/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91?ui=en-US&rs=en-US&ad=US)，了解有关 SDS 的详细信息。

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>用户和设备许可证如何影响对服务的访问
* 每个你向其分配用户软件许可证的**用户**，均可访问和使用联机服务和相关软件（包括 System Center 软件）来管理应用程序和多达 15 台的设备。
* 每台你向其分配设备软件许可证的**设备**，均可访问和使用供任意数量的用户使用的联机服务和相关软件（包括 System Center 软件）。
* 如果设备由多个用户使用，则每位用户均需要设备软件许可证，或所有用户都需要用户软件许可证。

## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>使用 PowerShell 来选择性地管理 EMS 用户许可证
使用 Microsoft 企业移动性 + 安全性（以前称为“企业移动性套件”）的组织中可能会有只需要 Azure Active Directory Premium 或 EMS 包中的 Intune 服务的用户。 你可以使用 [Azure Active Directory PowerShell cmdlet](https://msdn.microsoft.com/library/jj151815.aspx) 分配一个或一部分服务。

若要有选择性地为 EMS 服务分配用户许可证，请使用已安装的[用于 Windows PowerShell 的 Azure Active Directory 模块](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule)在计算机上以管理员身份打开 PowerShell。 你可以在本地计算机或 ADFS 服务器上安装 PowerShell。

必须创建仅应用于所需服务计划的新许可证 SKU 定义。 若要执行此操作，请禁用不想应用的计划。 例如，你可以创建一个不分配 Intune 许可证的许可证 SKU 定义。 若要查看从可用服务的列表，请键入：

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

你可以运行下面的命令来排除 Intune 服务计划。 你可以使用相同的方法来扩展整个安全组，或者使用更精细的筛选器。

**示例 1**<br>
在命令行上创建一个新用户，并在不启用许可证的 Intune 部分的情况下分配一个 EMS 许可证：

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


验证方式：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**示例 2**<br>
为已获得许可证的用户禁用 EMS 许可证的 Intune 部分：

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

验证方式：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

