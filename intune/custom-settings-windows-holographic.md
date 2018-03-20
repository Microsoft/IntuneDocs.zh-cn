---
title: "Windows Holographic for Business 设备的 Microsoft Intune 自定义设置"
titlesuffix: 
description: "了解可以在 Windows Holographic for Business 自定义配置文件中使用的设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 3/6/2018
ms.article: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b95d891d1dfaecbce182fde4a2221255a7e1eb06
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-holographic-for-business"></a>运行 Windows Holographic for Business 的设备的 Microsoft Intune 自定义设备设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 使用 Windows Holographic for Business 的 Microsoft Intune 自定义配置文件部署可用于控制设备功能的 OMA-URI（开放移动联盟统一资源标识符）设置。 通过 Windows Holographic for Business 可以进行很多配置服务提供程序 (CSP) 设置。 有关 CSP 的概述，请参阅[面向 IT 专业人员的配置服务提供程序 (CSP) 简介](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。 如需了解 Windows Holographic 支持的具体 CSP，请参阅 [Windows Holographic 中支持的 CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)。

如果正在寻找特定设置，请牢记 [Windows Holographic for Business 设备限制配置文件](device-restrictions-windows-holographic.md)包含许多内置设置，无需指定自定义值。

1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](custom-settings-configure.md)中的说明进行操作。
2. 在“创建配置文件”上，选择“设置”添加一个或多个 OMA-URI 设置。
3. 在“自定义 OMA-URI 设置”上，单击“添加”可添加新值。 还可以单击“导出”创建逗号分隔值 (.csv) 文件中配置的所有值的列表。
4. 对于要添加的每个 OMA URI 设置，请输入以下信息：
    - **设置名称** - 输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
    - **设置描述** -（可选）输入设置的描述。
    - **数据类型** -从以下各项选择：
        - **字符串**
        - **字符串 (XML)**
        - **日期和时间**
        - **整数**
        - **浮点**
        - **布尔值**
    - **OMA-URI（区分大小写）** - 指定想要为其提供设置的 OMA-URI。
    - **值** - 指定要与输入的 OMA-URI 关联的值。
1. 完成后，返回“创建配置文件”，然后单击“创建”。
配置文件随即创建并显示在配置文件列表中。

## <a name="recommended-custom-settings"></a>推荐的自定义设置

以下设置也可用于运行 Windows Holographic for Business 的设备：


|设置名|OMA-URI|数据类型  |
|---------|---------|---------|
|[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)|./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Integer<br>0 - 不允许<br>1 - 允许（默认值）|
|[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)|./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Integer<br>0 - 不允许<br>1 - 允许（默认值）|
|[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)|./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Integer<br>0 – 不允许更新服务 <br>1 – 允许更新服务（默认值）。|
|[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)|./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|字符串<br>URL - 设备从指定的 URL 上的 WSUS 服务器检查更新。<br>未配置 - 设备从 Microsoft 更新检查更新。|
|[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)|./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Integer<br>0 – 未配置。 设备安装所有适用的更新。<br>1 – 设备仅安装既适用又在已批准更新列表中的更新。 如果 IT 想控制设备上的更新部署（例如部署前需要测试），请将此策略设置为 1。|
|[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)|./Vendor/MSFT/Update/ApprovedUpdates<br><br>**重要说明**<br>必须代表最终用户阅读和接受更新 EULA。 如果不这样做，将被视为违反法律或合同义务。|更新批准的节点和代表最终用户的 EULA 接受。|
[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)|./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br><br>**重要说明**<br>AppLocker CSP 一文使用转义 XML 示例。 若要使用 Intune 自定义配置文件配置设置，必须使用纯 XML。|字符串<br>有关详细信息，请参阅文章 [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)。 

## <a name="how-to-find-the-policies-you-can-configure"></a>如何查找可以配置的策略

在 [Windows Holographic 中支持的 CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) 中，可以找到 Windows Holographic 支持的所有配置服务提供程序 (CSP) 的完整列表。 并非所有设置都与所有 Windows Holographic 版本兼容。 Windows 文章中的表将说明各个 CSP 支持的版本。

此外，Intune 并不支持文章中列出的所有设置。 若要查明 Intune 是否支持所需的设置，请打开针对该设置的文章。 每个设置页面将显示其支持的操作。 若要使用 Intune，设置必须支持“添加”或“替换”操作。
