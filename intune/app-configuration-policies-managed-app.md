---
title: "为受管理应用添加应用配置策略（无需设备注册）| Microsoft Docs"
titlesuffix: Azure portal
description: "了解如何为受管理应用添加应用配置策略（无需设备注册）。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 750ce7dbb0dccf08757e076826e2d3650b6e6ab5
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2017
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>为受管理应用添加应用配置策略（无需设备注册）

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可将应用配置策略用于受管理应用，这些应用甚至在未注册设备上也支持 Intune App SDK。 

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 选择“移动应用”工作负荷。
4. 在“管理”组中，单击“应用配置策略”，然后单击“添加”。
5. 设置以下详细信息：
    - **名称**  
      在 Azure 门户中显示的配置文件名称。
    - **描述**  
      在 Azure 门户中显示的配置文件说明。
    - **设备注册类型**  
      选择“管理应用”。
6. 选择“关联的应用”以选择要配置的应用。 从已同意并与 Intune 同步的应用列表中选择应用。
7. 对于该应用支持的每个配置设置，请键入“名称”和“值”，然后单击省略号 (…)。  
    要删除配置，请单击省略号 (…)，然后选择“删除”。  
    启用 Intune App SDK 的应用支持键值对形式的配置。 要详细了解支持哪些键值配置，请参阅相关文档了解每个应用。  
    此外，可使用将由应用程序生成的数据动态填充的令牌。

## <a name="configuration-values-using-tokens"></a>使用令牌配置值

可使用 Intune 生成一些令牌并将其发送到受管理的应用程序。 例如，如果应用配置可使用电子邮件设置，则可通过使用令牌添加动态电子邮件。 在“名称”字段键入应用所需名称，然后在“值”字段键入 `\{\{mail\}\}`。

Intune 支持在配置设置中使用以下令牌类型：

- \{\{userprincipalname\}\} -（示例：**John@contoso.com**）
- \{\{mail\}\} -（示例：**John@contoso.com**）
- \{\{partialupn\}\} -（示例：**John**）
- \{\{accountid\}\} -（示例：**fc0dc142-71d8-4b12-bbea-bae2a8514c81**）
- \{\{deviceid\}\} -（示例：**b9841cd9-9843-405f-be28-b2265c59ef97**）
- \{\{userid\}\} -（示例：**3ec2c00f-b125-4519-acf0-302ac3761822**）
- \{\{username\}\} -（示例：**John Doe**）
- \{\{PrimarySMTPAddress\}\} -（示例：testuser@ad.domain.com） 


> [!Note]  
> \{\{ 和 \}\} 字符仅供令牌类型使用，不得用于其他目的。

## <a name="next-steps"></a>后续步骤

照常继续[分配](apps-deploy.md)和[监视](apps-monitor.md)应用。