---
title: "设置电信费用管理服务 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：将 Saaswedo 电信费用管理服务配置为与 Intune 集成。"
keywords: Saaswedo
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 915d61344a3c1d388305dd51b1e2463bd2e32770
ms.openlocfilehash: 8d94fec099e1dc8918077062fb73b94a5973ea96

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>在 Intune Azure 预览版中设置电信费用管理服务
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 已集成第三方软件开发商 Saaswedo 的 Datalert 电信费用管理解决方案。 Datalert 是一款实时电信费用管理软件，可管理 Intune 托管设备的电信数据流量，避免昂贵和意外的数据和漫游过量。 Intune 与 Datalert 相集成，通过在限制超过定义的阈值时使用自动报警，来实现集中设置、监视和强制实施漫游和国内数据流量限制。 可以将服务配置为对最终用户的个人或群组应用不同的操作，包括在用户超出阈值时禁用漫游。 可在 Datalert 管理控制台中查看提供数据流量和监视信息的报告。

通过 Intune 使用 Datalert 之前，需要在 Datalert 控制台和 Intune 中配置设置。 请务必打开 Datalert 服务和 Intune 的连接。 如果 Datalert 端已启用连接，但 Intune 端未启用，那么 Intune 虽然能接收到通信，但会将其忽略。

>[!NOTE]
>若要在试用租户中启用此功能，请[联系 Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)以请求激活，并联系 Datalert 支持以获取所需的软件许可证。

## <a name="supported-platforms"></a>受支持的平台

- Samsung Knox
- iOS 8.0 及更高版本

## <a name="prerequisites"></a>先决条件

- Microsoft Intune 订阅
- Datalert 电信费用管理服务订阅

## <a name="list-of-telecom-expense-management-providers"></a>电信费用管理提供商列表

Intune 目前与下列电信费用管理提供商集成：

[Saaswedo Datalert 电信费用管理服务](http://www.datalert.biz/)

## <a name="configure-intune-to-work-with-the-datalert-service"></a>将 Intune 配置为支持 Datalert 服务

 

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“配置设备”。
2. 在“设备配置”边栏选项卡上，选择“设置” > “电信费用管理”。
2. 在“电信费用管理”下，选择“连接状态”。

3. 选择“TEM 服务提供商列表”，然后从显示的列表中选择你的提供商。 将打开特定于你的提供商的页面。 对于 Saaswedo，将打开 Datalert 页。 需要使用 Saaswedo Datalert 来购买订阅。

4. 在 **Datalert** 管理控制台中进行以下操作：

    a. 转到“设置”选项卡，然后转到“MDM 配置”部分。

    b。 选择“解锁”以在页面上输入设置。

    c. 对于“服务器 MDM”，选择“Microsoft Intune”。

    d. 对于“租户 ID”，输入 Intune 租户 ID，然后选择“连接”按钮。 选择“连接”将使 Datalert 服务登记到 Intune，以确保与 Intune 之间没有预先存在的 Datalert 连接。 几秒钟后将出现 Microsoft 登录页，随后是 Datalert Azure 身份验证。

    e. 在 Microsoft 身份验证页上，选择“接受”。 将重定向到 Datalert“谢谢”页，该页会在几秒钟后关闭。 Datalert 会验证连接，并在其验证的项列表旁显示绿色复选标记。 如果验证失败，将看到一条红色消息。 若发生这种情况，请联系 Datalert 支持以获取帮助。

5. 请等待几分钟，然后转到 Azure 门户，检查连接状态是否显示为“活动”。 

    >[!NOTE]
    >若要在试用租户中启用此功能，请[联系 Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

6. 返回到 Datalert 管理控制台，并配置数据行：

    a. 单击“设置”选项卡。

    b。 转到“设置”向导，然后按照向导中的步骤进行操作。



Datalert 服务目前处于活动状态，它开始监控数据流量，并在超过所配置流量限制的设备上禁用手机网络和漫游数据。

## <a name="turning-off-the-datalert-service"></a>关闭 Datalert 服务

如果在 Azure 门户中禁用 Datalert 服务：

- 因为之前违反流量限制而应用到设备的所有操作都将撤销。
- 将不再阻止用户进行数据访问和漫游。
- Intune 仍然会接收来自服务的信号，但将忽略它们。

**关闭服务**

1. 在 Azure 门户中的“电信费用管理”边栏选项卡上，选择“禁用”。

2. 选择“保存”。

## <a name="viewing-data-usage-and-roaming-reports"></a>查看数据流量和漫游报告

目前，仅在 Saaswedo 的 Datalert 管理控制台中提供数据流量报告。



<!--HONumber=Feb17_HO2-->


