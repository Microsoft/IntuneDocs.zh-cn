---
title: "用户管理入门"
titlesuffix: Microsoft Intune
description: "向 Intune 添加用户并为其分配许可证，以便他们可以在移动设备上访问公司资源。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e06b335c03caee0bd997748f9c48ed78d7d379b
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-managing-users"></a>用户管理入门

应考虑组织中的所有人员。 对于使用公司数据的每一位人员，都需通过 Intune 用户形式管理对公司数据的访问。

## <a name="how-do-i-create-a-user"></a>如何创建用户？

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 使用“搜索资源”，搜索 Intune。
3. 打开“Microsoft Intune”边栏选项卡后，选择“用户”。 在“所有用户”页上，选择“添加新用户”。
4. 输入用户详细信息，如名称和用户名。 用户名称的域名部分必须为初始默认域名“contoso.onmicrosoft.com”或一个已验证的非联合域名，例如“contoso.com”。
5. 在“组”下，选择要添加用户的测试组。
6. 保存自动生成的用户密码，以便用于登录测试设备。 必须向用户提供此密码，以便他们可将其更改为自己能够记住的常规密码。
7. 在“用户”边栏选项卡中，选择“创建”。

## <a name="assigning-licenses-to-users"></a>向用户分配许可证

创建用户之后，需要使用 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)为其分配 Intune 许可证。 若没有为其分配许可证，用户将不能为自己的设备注册管理。

1. 使用登录 Intune 的凭据登录 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 选择“用户” > “Active 用户”，然后选择之前创建的用户。
3. 可能需要等待一段时间，系统才能加载完所有用户信息。 加载完之后，针对用户的“产品许可证”选择“编辑”。
4. 向用户分配一个位置，然后将 Intune 切换为“开”。

 > [!NOTE]
 > 此操作会为此用户使用一个许可证。 如果使用的是实时环境，可在之后停用此许可证，以将其重新分配给一个真正的用户。

5. 选择“保存”。

## <a name="next-steps"></a>后续步骤

[组入门](get-started-groups.md) - 将用户归组，以便更轻松地管理其可访问的策略和应用。
