---
# required metadata

title: 解决 GPO 与 Intune 之间的策略冲突 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 解决组策略对象 (GPO) 与 Microsoft Intune 之间的策略冲突
Intune 使用策略来帮助管理你所管理的计算机上的设置。 例如，你可以使用策略来控制计算机上 Windows 防火墙的设置。 Intune 的许多设置都类似于你可使用 Windows 组策略配置的设置。 但是，有时可能会有两种方法互相冲突。

发生冲突时，除非计算机无法登录到域，否则域级组策略优先于 Intune 策略。 在这种情况下，Intune 策略将应用于客户端计算机。

## 在使用组策略的情况下要执行的操作
检查你应用的任何策略是否未通过组策略进行管理。 为了帮助防止冲突，你可以采用下列一种或多种方法：

-   在安装 Intune 客户端之前，将计算机移到未应用组策略设置的 Active Directory 组织单位 (OU)。 还可以在包含已在 Intune 中注册并且不希望应用组策略设置的计算机的 OU 上阻止组策略继承。

-   使用 WMI 筛选器或安全筛选器将 GPO 仅限制到未由 Intune 托管的计算机。 要详细了解操作方法及其示例，请查看下面的[如何筛选现有组策略对象以避免与 Microsoft Intune 策略冲突](resolve-gpo-and-microsoft-intune-policy-conflicts.md#BKMK_Filter)一节。

-   禁用或删除与 Intune 策略冲突的组策略对象。

有关 Active Directory 和 Windows 组策略的详细信息，请参阅 Windows Server 文档。

## 如何筛选现有 GPO 以避免与 Intune 策略冲突
如果确定了其设置与 Intune 策略冲突的 GPO，则可以使用下列筛选方法将这些 GPO 仅限制到未由使用 Intune 托管的计算机。

### 使用 WMI 筛选器
WMI 筛选器会有选择地将 GPO 应用于满足查询条件的计算机。 若要应用 WMI 筛选器，在 Intune 服务中注册任何计算机之前，请将 WMI 类实例部署到企业中的所有计算机。

#### 将 WMI 筛选器应用于 GPO

1.  通过将以下内容复制并粘贴到文本文件中，然后将该文件作为 **WIT.mof** 保存到一个方便的位置，从而创建管理对象文件。 该文件包含部署到你希望在 Intune 服务中注册的计算机的 WMI 类实例。

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

2.  使用启动脚本或组策略来部署该文件。 下面是启动脚本的部署命令。 在 Intune 服务中注册客户端计算机之前，必须部署 WMI 类实例。

    **C:/Windows/System32/Wbem/MOFCOMP &lt;MOF 文件的路径&gt;\wit.mof**

3.  运行以下任一命令以创建 WMI 筛选器，具体情况取决于你希望筛选的 GPO 是应用于使用 Intune 管理的电脑，还是应用于未使用 Intune 管理的计算机。

    -   对于应用于未使用 Intune 管理的计算机的 GPO，请使用以下命令：

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   对于应用于由 Intune 管理的计算机的 GPO，请使用以下命令：

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  在组策略管理控制台中编辑 GPO 以应用上一步中创建的 WMI 筛选器。

    -   对于应该仅应用于要使用 Intune 管理的计算机的 GPO，请应用筛选器 **WindowsIntunePolicyEnabled=1**

    -   对于应该仅应用于不希望使用 Intune 管理的计算机的 GPO，请应用筛选器 **WindowsIntunePolicyEnabled=0**

有关如何在组策略中应用 WMI 筛选器的详细信息，请参阅博客文章 [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883)（组策略首选项中的安全筛选、WMI 筛选和项级目标设定）

### 使用安全组筛选器
利用组策略，你可以将 GPO 仅应用于在所选 GPO 的组策略管理控制台的“安全筛选”  区域中指定的那些安全组。 默认情况下，GPO 应用于“Authenticated Users”（经过身份验证的用户）

-   在“Active Directory 用户和计算机”管理单元中，创建包含不希望使用 Intune 管理的计算机和用户帐户的新安全组。 例如，可以将组命名为 **Not In Microsoft Intune**

-   在组策略管理控制台中所选 GPO 的“委派”选项卡上，右键单击新的安全组以将相应的“读取”和“应用组策略”权限委派给该安全组中的用户和计算机。 （“应用组策略” 权限可在“高级”  对话框上找到。）

-   然后，将新的安全组筛选器应用于所选 GPO，并删除“Authenticated Users”  默认筛选器。

在 Intune 服务中的注册发生更改时，必须对新安全组进行维护。

### 另请参阅
[使用 Microsoft Intune 管理 Windows PC](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


