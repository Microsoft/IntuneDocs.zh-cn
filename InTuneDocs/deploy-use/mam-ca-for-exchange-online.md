---
title: "为 Exchange Online 配置应用访问 | Microsoft Intune"
description: "本主题介绍如何为 MAM 应用配置条件访问策略。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f2cd1a1f-fd29-4081-8dfa-c40993a107d5
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dae04661289c79798c2f37272a0f941d30335ea5
ms.openlocfilehash: a0c0bac5082119b2cfa1518934dea8cdc3f75067


---

# <a name="create-an-exchange-online-conditional-access-to-only-allow-apps-supported-by-mam"></a>创建 Exchange Online 条件访问以便仅允许 MAM 支持的应用
本主题提供有关如何为 Exchange Online 设置条件访问以便仅允许支持 Intune 移动应用管理 (MAM) 策略的移动应用的分步说明。


## <a name="create-an-exchange-online-policy"></a>创建 Exchange Online 策略
1.  登录包含应用访问功能的 [Azure 门户](https://portal.azure.com)。 如果是刚接触 Azure 门户体验，请阅读 [MAM 策略的 Azure 门户](azure-portal-for-microsoft-intune-mam-policies.md)主题。

2.  选择“浏览”>“Intune”>“Intune 移动应用程序管理边栏选项卡”>“设置”，然后在“条件访问”部分中，选择“Exchange Online”。

  ![显示条件访问部分（其中突出显示 Exchange Online 选项）的设置边栏选项卡的屏幕截图](../media/mam-ca-settings-exo.png)

3.  在“允许的应用”边栏选项卡上，选择“允许支持 Intune 应用策略的应用”选项以便仅允许 Intune MAM 策略支持的应用能够访问 Exchange Online。 选择此选项时，会显示支持的应用的列表。

  >[!NOTE]
  >会阻止所有 Exchange Active Sync 邮件客户端（包括 iOS 和 Android 上连接到 Exchange Online 的内置邮件客户端）发送或接收电子邮件。 用户会改为收到一封电子邮件，告知他们需要使用 Outlook 邮件应用。 
4.   若要将此策略应用于用户，请打开“已限制的用户组”边栏选项卡，然后选择“添加用户组”。 选择应获取此策略的一个或多个用户组。

  ![突出显示添加用户组选项的已限制用户组边栏选项卡的屏幕截图](../media/mam-ca-add-user-group.png)

5.  你可能希望在上一步中选择的用户组中的某些用户不受此策略影响。 在这种情况下，将用户组添加到被免除的用户组列表。 从“Exchange Online”边栏选项卡，选择“被免除的用户组”。 选择“添加用户组”以打开用户组的列表。 选择要从此策略中免除的组。  

## <a name="modify-an-existing-policy"></a>修改现有策略
### <a name="add-or-delete-user-groups"></a>添加或删除用户组

若要从“已限制的用户组”列表中**删除用户组**，请打开“已限制的用户组”边栏选项卡，突出显示要删除的用户组，然后单击**省略号 (...)** 以查看“删除”选项。 选择“删除”以从列表中删除用户组。 可以按照相同过程从“被免除的用户组”列表中删除用户组。


## <a name="next-steps"></a>后续步骤
[阻止不具有新式验证的应用](block-apps-with-no-modern-authentication.md)
### <a name="see-also"></a>另请参阅
[使用 MAM 策略保护应用数据](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


