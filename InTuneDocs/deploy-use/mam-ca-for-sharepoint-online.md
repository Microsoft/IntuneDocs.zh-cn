---
title: "配置 SharePoint Online 的应用访问"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 992273f88e4bbe234f11f936d6416dbaf0d394e9
ms.lasthandoff: 04/19/2017


---

# <a name="create-a-sharepoint-online-conditional-access-policy-to-only-allow-apps-supported-by-mam"></a>创建 SharePoint Online 条件访问策略以便仅允许 MAM 支持的应用
本主题提供有关如何为 Exchange Online 设置条件访问以便仅允许支持 Intune 移动应用管理 (MAM) 策略的移动应用的分步说明。

## <a name="configure-a-sharepoint-online-policy"></a>配置 SharePoint Online 策略
**步骤 1：**登录包含应用访问功能的 [Azure 门户](https://portal.azure.com)。 如果是刚接触 Azure 门户体验，请阅读 [MAM 策略的 Azure 门户](azure-portal-for-microsoft-intune-mam-policies.md)主题。

**步骤 2：**转到“浏览 > Intune > Intune 移动应用程序管理边栏选项卡 > 设置”，然后在“条件访问”部分中，选择“SharePoint Online”。

![随即会打开显示条件访问部分的边栏选项卡和 SharePoint Online 边栏选项卡的设置屏幕快照](../media/mam-ca-settings-spo.png)

**步骤 3：**在“允许的应用”边栏选项卡上，选择“允许支持 Intune 应用策略的应用”选项以便仅允许 Intune MAM 策略支持的应用能够访问 SharePoint Online。 当选中仅允许由 Intune MAM 策略支持的应用的选项时，将显示受支持应用的列表。

![显示应用列表的允许应用边栏选项卡的屏幕快照](../media/mam-ca-spo-allowed-apps.png)

**步骤 4：**若要将此策略应用于用户，请打开“已限制的用户组”边栏选项卡，然后选择“添加用户组”。 选择应获取此策略的一个或多个用户组。

![突出显示添加用户组选项的已限制用户组边栏选项卡的屏幕截图](../media/mam-ca-spo-restricted-groups.png)


**步骤 5：**你可能希望在上一步中选择的用户组中的某些用户不受此策略影响。 在这种情况下，将用户组添加到被免除的用户组列表。 从“SharePoint Online”边栏选项卡，选择“被免除的用户组”。 选择“添加用户组”以打开用户组的列表。 选择要从此策略中免除的组。  

## <a name="modifying-an-existing-policy"></a>修改现有策略
### <a name="adding-or-deleting-user-groups"></a>添加或删除用户组
若要从“已限制的用户组”列表中**删除用户组**，请打开“已限制的用户组”边栏选项卡，突出显示要删除的用户组，然后单击 … 以查看删除选项。 选择“删除”以从列表中删除用户组。 可以按照相同过程从“被免除的用户组”列表中删除用户组。


## <a name="next-steps"></a>后续步骤
[为 Exchange Online 配置应用访问](mam-ca-for-exchange-online.md)

[阻止不具有新式验证的应用](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>另请参阅

[使用 MAM 策略保护应用数据](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

