---
title: "用户入门"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e711f32ebd77a83b17e6db468f8cb23a409c8d31
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="get-started-with-users"></a>用户入门

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Azure Active Directory 管理组织的对象（如设备和应）组以及用户组。 可将用户或设备归组，而无需单独管理每个设备。 通过这种方式可轻松向数量较大的用户和设备分配应用和设置。

## <a name="how-do-i-create-a-user"></a>如何创建用户？

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 使用“搜索资源”，搜索“用户和组”。
3. 打开“用户和组”边栏选项卡后，选择“所有用户”，然后选择“+ 新用户” 。
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
