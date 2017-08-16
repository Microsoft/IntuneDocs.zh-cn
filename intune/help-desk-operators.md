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
ms.openlocfilehash: 066f8668ea37e928455792f512e4e337a1f19c20
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2017
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>使用疑难解答门户帮助用户

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

通过故障排除门户，技术支持人员和 Intune 管理员可查看用户信息，处理用户求助请求。 设有技术支持团队的组织可以为一组用户分配**技术支持人员**，之后技术支持人员可使用疑难解答边栏选项卡来帮助用户。

例如，当用户就 Intune 技术问题联系支持人员时，技术支持人员会输入该用户的名字。 Intune 可显示有助于解决许多第 1 层问题的有用数据，包括：
- 用户状态
- 分配
- 应用安装失败
- 合规性问题
- 设备未响应
-   设备不具有 VPN 或 Wi-fi 设置
-   应用安装失败

## <a name="add-help-desk-operators"></a>添加技术支持人员
Intune 管理员可以将技术支持人员角色分配给一个用户组。 该组成员可以使用管理门户来解决用户的问题。 每个技术支持人员必须具有用于访问 Intune 门户的 Intune 许可证。 了解如何[分配 Intune 许可证](licenses-assign.md)。

添加技术支持用户：
1. [将用户添加到 Intune](users-add.md)（如有必要）。
2. [创建技术支持组](groups-add.md)并将用户添加到该组。
3. [分配 RBAC 技术支持人员角色](role-based-access-control.md#built-in-roles)

  ![Intune 门户的屏幕截图，其中突出显示了 Intune 角色，同时显示了一系列内置角色，包括技术支持人员](./media/help-desk-user-add.png) 还可[创建自定义角色](role-based-access-control.md#custom-roles)，可进一步对其进行修改，为技术支持人员提供访问权限。  技术支持人员需要具有以下权限才可帮助解决用户问题：
    - MobileApps：读取
    - ManagedApps：读取
    - ManagedDevices：读取
    - 组织：读取
    - DeviceCompliancePolices：读取
    - DeviceConfigurations：读取

4. 若要为技术支持人员授予查看服务运行状况和打开 Intune 支持票证的权限，请通过将用户设置为“服务管理员”来为其[授予用户管理员权限](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)。 不要授予“Intune 服务管理员”权限，因为此目录角色具有技术支持人员无需使用的权利。

## <a name="access-the-troubleshooting-portal"></a>访问疑难解答门户

技术支持人员和 Intune 管理员可以使用两种方式访问疑难解答门户：
- 在 Web 浏览器中打开 [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting)，直接查看疑难解答门户。
  ![疑难解答控制台的屏幕截图](./media/help-desk-console.png)
- 登录到 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”，然后转到“帮助和支持” > “疑难解答”。

单击“选择用户”查看用户和该用户的详细信息。

![包含“选择用户”链接的 Intune“疑难解答”工作负载的屏幕截图](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>使用疑难解答门户

在疑难解答门户中，可以选择“选择用户”以查看用户的信息。 用户信息可以帮助你了解用户及其设备的当前状态。 疑难解答门户显示以下疑难解答详细信息：
- **帐户状态**
- **用户状态**
- **设备**与设备操作
- **组成员身份**
- **应用保护状态**
