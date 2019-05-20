---
title: 使用 Intune 设置 Sophos Mobile 集成
titleSuffix: Intune on Azure
description: 如何使用 Microsoft Intune 设置 Sophos Mobile 解决方案以控制移动设备对公司资源的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 67f3f329cb66716a2126f47eb2984ca26854b6de
ms.sourcegitcommit: b1ad73f5c9fd0ad8026c572aef8d15e258951c8f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64880751"
---
# <a name="integrate-sophos-mobile-with-intune"></a>将 Sophos Mobile 与 Intune 相集成  

完成以下步骤以将 Sophos Mobile Threat Defense 解决方案与 Intune 相集成。  

## <a name="before-you-begin"></a>在开始之前  

在开始将 Sophos Mobile 与 Intune 相集成之前，请确保具有以下各项：  
- Microsoft Intune 订阅  
- 用于授予下列权限的 Azure Active Directory 管理员凭据：  
  - 登录和读取用户配置文件  
  - 使用已登录用户的身份访问目录  
  - 读取目录数据  
  - 向 Intune 发送设备信息  
- 用于访问 Sophos Mobile 管理控制台的管理员凭据。  


### <a name="sophos-mobile-app-authorization"></a>Sophos Mobile 应用授权  
  
Sophos Mobile 应用授权流程如下：  
- 允许 Sophos Mobile 服务将与设备运行状况状态相关的信息反馈给 Intune。  
- Sophos Mobile 将与 Azure AD 注册组成员身份同步以填充其设备的数据库。  
- 允许 Sophos Mobile 管理控制台使用 Azure AD 单一登录 (SSO)。  
- 允许 Sophos Mobile 应用使用 Azure AD SSO 登录。  


## <a name="to-set-up-sophos-mobile-integration"></a>设置 Sophos Mobile 集成  

1. 登录 [Azure 门户]( https://portal.azure.com/)，转到“Intune” > “设备符合性” > “Mobile Threat Defense”> 选择“添加”。  
2. 在“添加连接器”页面上，使用下拉列表以选择“Sophos”。 然后选择“创建”。  
3. 选择“打开 Sophos 管理控制台”链接。  
4. 使用 Sophos 凭据登录 [Sophos 管理控制台](https://central.sophos.com/)。  
5. 转到“Mobile” > “设置” > “设置” > “Sophos 设置”。  
6. 在“Sophos 设置”页面上，选择“Intune MTD”选项卡。  
   ![Sophos 设置](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. 选择“绑定”，然后选择“是”。 Sophos 将连接到 Intune 并要求你登录你的 Intune 订阅。 
8. 在 Microsoft Intune 身份验证窗口中，输入你的 Intune 凭据并选择“接受”以接受“Sophos Mobile Thread Defense”的权限请求。  
   ![Intune 身份验证](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. 在“Sophos 设置”页面上，选择“保存”以完成 Intune 的配置：  
   ![保存 Sophos 设置](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. 出现“成功集成”消息即表示集成已完成。  
1. 在 Intune 控制台中，Sophos 现已可用。  


## <a name="next-steps"></a>后续步骤  
[配置 Sophos 客户端应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
