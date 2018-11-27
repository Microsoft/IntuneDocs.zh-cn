---
title: 用户管理入门
titlesuffix: Microsoft Intune
description: 向 Intune 添加用户并为其分配许可证，以便他们可以在移动设备上访问公司资源。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fc5d2a6f17bdac8711348c136ee390a400fc21bd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182493"
---
# <a name="get-started-managing-users"></a>用户管理入门

应考虑组织中的所有人员。 对于使用公司数据的每一位人员，都需通过 Intune 用户形式管理对公司数据的访问。

## <a name="how-do-i-create-a-user"></a>如何创建用户？

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 打开“Microsoft Intune”窗格后，选择“用户”。 在“所有用户”页上，选择“添加新用户”。
4. 输入用户详细信息，如名称和用户名。 用户名的域名部分必须为以下域之一：
    - 初始默认域名“contoso.onmicrosoft.com”，或
    - 有效的非联合域名，例如“contoso.com”。
5. 在“组”下，选择要添加用户的[组](get-started-groups.md)。
6. 保存自动生成的用户密码，以便用于登录测试设备。 必须向用户提供此密码，以便他们可将其更改为自己能够记住的常规密码。
7. 在“用户”窗格中，选择“创建”。

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
