---
title: 设置 Wandera 移动威胁防御与 Intune 的集成
titleSuffix: Intune on Azure
description: 如何设置 Wandera 移动威胁防御解决方案与 Microsoft Intune 的集成，从而控制移动设备对公司资源的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bf8fd189e50a704e96fc24d0804c5c5d6f91bb4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728216"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>将 Wandera 移动威胁防御与 Intune 集成  

完成以下步骤，以便将 Wandera 移动威胁防御解决方案与 Intune 相集成。  

## <a name="before-you-begin"></a>在开始之前  

在开始将 Wandera 与 Intune 集成的过程之前，请确保已具备以下先决条件：
- Microsoft Intune 订阅  
- 用于授予下列权限的 Azure Active Directory 管理员凭据：  
  - 登录和读取用户配置文件  
  - 使用已登录用户的身份访问目录  
  - 读取目录数据  
  - 向 Intune 发送设备信息  

- Wandera 订阅：
  - 已获得 EMM Connect 许可的一个或多个 Wandera 帐户  
  - 在 Wandera 中具有超级管理员权限的帐户  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Wandera 移动威胁防御应用授权  

Wandera 移动威胁防御应用授权流程：  
- 允许 Wandera 移动威胁防御服务将与设备运行状况状态相关的信息反馈给 Intune。  
- 同步 Wandera 与 Azure AD 注册组成员身份，以填充其设备的数据库。  
- 允许 Wandera RADAR 管理门户使用 Azure AD 单一登录 (SSO)。  
- 允许 Wandera 移动威胁防御应用使用 Azure AD SSO 登录。  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>设置 Wandera 移动威胁防御集成  
为 Wandera 设置 EMM Connect  需要在 Intune 和 Wandera 控制台中同时完成一次性配置流程。 此配置过程需要大约 15 分钟的时间。 无需与 Wandera 技术客户经理或支持代表协调即可完成配置。  

### <a name="enable-support-for-wandera-in-intune"></a>在 Intune 中启用对 Wandera 的支持
1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，转到“设备符合性” > “移动威胁防御”，然后选择“添加”    。

2. 在“添加连接器”页上，使用下拉列表以选择“Wandera”   。 然后选择“创建”  。  

3. 在“移动威胁防御”窗格中，从连接器列表中选择“Wandera”  MTD 连接器，以打开“编辑连接器”  窗格。 选择“打开 Wandera 管理控制台”  以打开 Wandera 管理控制台 [RADAR](https://radar.wandera.com/login) 并登录。 

4. 在 Wandera 控制台中，转到“设置” > “EMM 集成”   ，然后选择“EMM Connect”  选项卡。使用“EMM 供应商”  下拉列表，并选择“Microsoft Intune”  。

   ![选择“Intune”](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. 选择“授予权限”  ，以打开与 Intune 门户的连接。 使用 Intune 管理员凭据登录，选中相应的复选框，然后选择“接受”  权限请求。  

   ![接受权限](./media/wandera-mtd-connector-integration/permissions.png) 

6. Wandera 完成连接，并返回到 RADAR 管理控制台。 根据需要重复此过程以“授予”  对其他配置的访问权限。  

   ![集成和权限](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. 在 RADAR 控制台中，复制显示在“EMM 标签”下的“SyncOnly”组的名称   。 此名称将用于在 Intune 中配置组与 Wandera 的同步。

   ![集成和权限](./media/wandera-mtd-connector-integration/sync-group-name.png) 

8. 返回到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 控制台，并编辑 Wandera MTD Connector。 将可用的开关设置为“开”  ，然后“保存”  配置。  

   ![启用 Wandera](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune 和 Wandera 现已连接。  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>配置 Wandera 应用程序和同步组  
若要部署 Wandera，将适用于你使用的平台（iOS 和 Android）的 Wandera 移动应用添加到 Intune，并将其分配到特定组（SyncOnly  组）进行同步。 

下面的各部分和过程将指导你完成此过程。

有关从 Wandera 完成此过程的详细信息，请登录到 Wandera [RADAR](https://radar.wandera.com/login)。 转到“设置” > “EMM 集成”，选择“应用推送”选项卡，然后选择“Microsoft Intune”     。 “应用推送”选项卡将使用特定于 Intune 的说明进行更新。  

### <a name="add-the-wandera-apps"></a>添加 Wandera 应用  
在 Intune 中创建客户端应用以将 Wandera 应用部署到 Android 和 iOS 设备。 有关特定于 Wandera 应用的过程和自定义详细信息，请参阅[添加 MTD 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)。  

创建应用后，返回此处以创建同步组并分配应用。  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>创建同步组并分配应用

1. 在 Wandera RADAR 控制台中，获取显示在“EMM 标签”下的“SyncOnly”组的名称   。 在步骤 7 中执行[在 Intune 中启用对 Wandera 的支持](#enable-support-for-wandera-in-intune)操作时，可能已经保存了此名称。 在 Intune 中使用此名称作为组名以用于 Wandera 同步。  

2. 在 Intune 控制台中，转到“组”，然后选择“新建组”   。 指定下列各项以配置供 Wandera 使用的同步组：
   - **组类型**：**安全**
   - **组名称**：指定从 Wandera RADAR 管理控制台中检索到的 SyncOnly 名称  。

   ![配置同步组](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. 选择“成员”  并分配要包括你希望用于 Wandera 的 Android 和 iOS 设备的组。

4. 选择“创建”  以保存该组。

有关详细信息，请参阅[部署应用](../apps/apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>将 Wandera 应用分配到同步组  
对于为 iOS 和 Android 创建的 Wandera 应用，重复以下过程。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并转到“客户端应用” > “应用”，选择 Wandera 应用   。  

2. 选择“分配”，然后选择“添加组”   。  

3. 在“添加组”窗格中，对于“分配类型”，选择“必需”    。

4. 依次选择“包括的组”和“选择要包括的组”   。 指定为 Wandera 同步所创建的组，然后单击“选择” > “确定” > “确定”    。 选择“保存”以完成组分配  。  
 

## <a name="next-steps"></a>后续步骤  
现已配置集成，可以开始配置策略、设置高级条件访问以及在 Wandera 管理控制台中查看报表。 若要详细了解如何管理和配置 Wandera，请参阅 Wandera 文档中的[支持中心入门指南](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started)。  
 