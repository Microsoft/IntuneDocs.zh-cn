---
# required metadata

title: 查找 per-app VPN 的包系列名称 (PFN) |Microsoft Intune|
description:
keywords:
author: nbigman
manager: [ALIAS]
ms.date: 05/10/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: [ALIAS]
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 查找 per-app VPN 配置的产品系列名称 (PFN)

有两种方法来查找 PFN，以便你可以配置 per-app VPN。

## 查找安装在 Windows 10 计算机上的应用的 PFN 

如果你正在使用的应用已安装在 Windows 10 计算机上，则可以使用 [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell cmdlet 来获取 PFN。

Get-AppxPackage 的语法是：

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> 注意：你可能需要以管理员身份运行 PowerShell，以检索 PFN

例如，要获取安装在计算机上的所有通用应用的信息，请使用 `Get-AppxPackage`。

要获取你知道名称或部分名称的应用的信息，请使用 `Get-AppxPackage *<app_name>`。 请注意通配符的使用，特别是在你不确定应用的完整名称的情况下，这会很有帮助。 例如要获取 OneNote 的信息，请使用 `Get-AppxPackage *OneNote`。


下面是针对 OneNote 检索到的信息：

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## 计算机上未安装该应用时查找 PFN

1.  转到 https://www.microsoft.com/en-us/store/apps
2.  在搜索栏中输入应用的名称。 在本示例中，我们搜索 OneNote。
3.  单击应用的链接。 请注意，你访问的 URL 末尾有一系列字母。 在我们的示例中，URL 如下所示：
`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  在另一个选项卡上，粘贴下面的 URL，`https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`，并将 `<app id>` 替换为从 https://www.microsoft.com/en-us/store/apps 获取的应用 ID，即步骤 3 中 URL 末尾的一系列字母。 在本示例中，以 OneNote 为例，粘贴：`https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`。

你所需的信息会在边缘显示；在 Internet Explorer 中，单击**打开**来查看该信息。 PFN 值会在第一行给出。 本示例的结果如下所示：
 

`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`



<!--HONumber=May16_HO3-->


