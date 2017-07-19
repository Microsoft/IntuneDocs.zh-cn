---
title: "技术支持疑难解答门户"
titleSuffix: Intune on Azure
description: "技术支持人员使用疑难解答门户来解决用户的技术问题"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 7a61c3703cd1016ef63c8baa371c3a21dca127fc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>使用 Microsoft Intune 中的疑难解答门户帮助用户

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

通过使用故障排除门户，技术支持人员和 Intune 管理员可以查看用户信息，以解决用户求助的问题。 设有技术支持团队的组织可以为一组用户分配**技术支持人员**，之后技术支持人员可使用疑难解答边栏选项卡来帮助用户。

例如，当用户就 Intune 技术问题联系支持人员时，技术支持人员会输入该用户的名字。 Intune 会显示相关信息，可帮助解决许多第 1 层问题，例如用户状态、应用安装失败或符合性问题。 解决的问题可能包括：
- 设备未响应
-   设备不具有 VPN 或 Wi-fi 设置
-   应用安装失败


## <a name="add-help-desk-operators"></a>添加技术支持人员
Intune 管理员可以通过两种方式向技术支持人员分配用户权限：
- 分配内置的**技术支持人员**角色
- 创建和分配自定义角色

## <a name="assign-help-desk-operator-role"></a>分配技术支持人员角色
Intune 管理员可以将技术支持人员角色分配给一个用户组。 该组的成员可以使用管理门户。 每个技术支持人员必须具有用于访问 Intune 门户的 Intune 许可证。 了解如何[分配 Intune 许可证](licenses-assign.md)。

1. 以 Intune 管理员身份登录到 Intune 门户，并选择“Intune 角色”。
2. 在“Intune 角色”工作负荷中，选择“技术支持人员” > “分配”，然后选择“分配”。
  ![Intune 门户的屏幕截图，其中突出显示了 Intune 角色，同时显示了一系列内置角色，其中包括“技术支持人员”（其中突出显示了“分配”）和“分配”周围的红框](./media/help-desk-user-assign.png)
3. 键入“分配名称”（必需）、“分配说明”（可选），然后分配“成员（组）”和“作用域（组）”。
4. 技术支持人员角色的成员现在可以使用疑难解答门户。

有关 Intune 角色的详细信息，请参阅“Intune 角色 (RBAC)”[](role-based-access-control.md)。

## <a name="create-a-custom-role-for-troubleshooting"></a>创建自定义角色进行故障排除
Intune 管理员可以创建自定义角色，让用户能够通过符合组织需要的权限来使用故障排除门户。 有关 Intune 角色的详细信息，请参阅“Intune 角色 (RBAC)”[](role-based-access-control.md)。

![Intune 门户的屏幕截图，其中突出显示了 Intune 角色，同时显示了一系列内置角色，包括技术支持人员](./media/help-desk-user-add.png)

要使用 Intune 控制台获取技术支持视图，自定义技术支持角色应拥有以下权限：
- MobileApps：读取
- ManagedApps：读取
- ManagedDevices：读取
- 组织：读取

## <a name="access-the-troubleshooting-portal"></a>访问疑难解答门户

技术支持人员和 Intune 管理员可以使用两种方式访问疑难解答门户：
- 在 Web 浏览器中，打开 [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting)。
- 在 Intune 门户中，转到**帮助和支持** > **故障排除**。

![包含“选择用户”链接的 Intune“疑难解答”工作负载的屏幕截图](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>使用疑难解答门户

在疑难解答门户中，可以选择“选择用户”以查看用户的信息。 用户信息可以帮助你了解用户及其设备的当前状态。 疑难解答门户显示以下疑难解答详细信息：
- **租户状态**
- **用户状态**
- **设备**和设备操作
- **组成员身份**
- **应用保护状态**
