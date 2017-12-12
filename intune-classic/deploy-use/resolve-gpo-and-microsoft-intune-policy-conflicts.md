---
title: "解决 GPO 与 Intune 之间的策略冲突"
description: "了解如何解决组策略和 Intune 配置策略之间的冲突。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9764a1fec44ff5aae7ebcf63b3ebde252bb687f9
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2017
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>解决组策略对象 (GPO) 与 Microsoft Intune 之间的策略冲突

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 使用策略来帮助你管理 Windows 电脑上的设置。 例如，你可以使用策略来控制电脑上 Windows 防火墙的设置。 Intune 的许多设置都类似于你可使用 Windows 组策略配置的设置。 但是，有时可能会有两种方法互相冲突。

发生冲突时，除非电脑无法登录到域，否则域级组策略优先于 Intune 策略。 在这种情况下，Intune 策略将应用于客户端电脑。

## <a name="what-to-do-if-you-are-using-group-policy"></a>在使用组策略的情况下要执行的操作
确保你应用的策略不受组策略管理。 为了帮助防止冲突，你可以采用下列一种或多种方法：

-   在安装 Intune 客户端之前，将电脑移到未应用组策略设置的 Active Directory 组织单位 (OU)。 还可以在包含已在 Intune 中注册并且不希望应用组策略设置的电脑的 OU 上阻止组策略继承。

-   使用安全组筛选器将 GPO 仅限制到未由 Intune 托管的电脑。

-   禁用或删除与 Intune 策略冲突的组策略对象。

有关 Active Directory 和 Windows 组策略的详细信息，请参阅 Windows Server 文档。

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>如何筛选现有 GPO 以避免与 Intune 策略冲突
如果确定了其设置与 Intune 策略冲突的 GPO，则可以使用安全组筛选器将这些 GPO 仅限制到未由 Intune 托管的电脑。

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


你可以将 GPO 仅应用于在所选 GPO 的组策略管理控制台的“安全筛选”区域中指定的那些安全组。 默认情况下，GPO 应用于“Authenticated Users”。

-   在“Active Directory 用户和计算机”管理单元中，创建包含不希望使用 Intune 管理的计算机和用户帐户的新安全组。 例如，可以将组命名为 *Not In Microsoft Intune*。

-   在组策略管理控制台中所选 GPO 的“委派”选项卡上，右键单击新的安全组以将相应的“读取”和“应用组策略”权限委派给该安全组中的用户和计算机。 （“应用组策略” 权限可在“高级”  对话框上找到。）

-   然后，将新的安全组筛选器应用于所选 GPO，并删除“Authenticated Users”默认筛选器。

在 Intune 服务中的注册发生更改时，必须对新安全组进行维护。

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 管理 Windows 电脑](manage-windows-pcs-with-microsoft-intune.md)
