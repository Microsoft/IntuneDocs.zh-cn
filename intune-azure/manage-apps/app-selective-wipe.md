---
title: "如何仅擦除应用中的企业数据 |Intune Azure 预览版 |Microsoft Docs"
description: "Intune Azure 预览版：了解如何使用 Microsoft Intune 选择性地擦除应用。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 44aefa68761236b946f5ab1db678ecc4aa81e92b
ms.openlocfilehash: ab2f9d065a1c4b0e0a016ff6195742cd09965191

---

# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>如何仅擦除 Intune 托管应用中的企业数据

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

当设备丢失或被盗，或如果员工离开公司，你想要确保从设备中删除了公司应用数据。 但是，你可能不想删除设备上的个人数据，尤其是如果该设备为员工所有。

若要选择性地删除公司应用数据，请按照本主题中的步骤创建擦除请求。 请求完成之后，应用下次在设备上运行时，会从应用中删除公司数据。

>[!IMPORTANT]
> 将删除从应用直接同步到本机通讯簿的联系人。 无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 目前仅适用于 Microsoft Outlook 应用。

## <a name="create-a-wipe-request"></a>创建擦除请求

1.  登录到 [Azure 门户](https://portal.azure.com)。

2.  选择“更多服务”，在筛选器文本框中键入“Intune”，然后选择“Intune”。 Intune 预览版边栏选项卡将打开，选择“管理应用”边栏选项卡。

    ![新建擦除请求边栏选项卡的屏幕截图](../media/intune-azure-preview-blade.png)

3.  在“移动应用”边栏选项卡上，选择“新建擦除请求”。 “新建擦除请求”边栏选项卡打开。

4.  选择“新建擦除请求”。 “新建擦除请求”边栏选项卡打开。

    ![新建擦除请求边栏选项卡的屏幕截图](../media/AzurePortal_MAM_NewWipeRequest.png)

5.  选择“用户”以打开“用户”边栏选项卡，然后选择要擦除其应用数据的用户。

6.  选择“设备”。 此操作将打开“设备”边栏选项卡，其中列出了与所选用户关联的所有设备，还提供了两个列：“设备名称”（用户定义的友好名称）和“设备类型”（其设备平台）。 选择要擦除的设备。

7.  你现在已返回“新建擦除请求”边栏选项卡。 选择“确定”以进行擦除请求。 

服务会为设备上的每个受保护应用以及与擦除请求相关联的用户创建并跟踪单独的擦除请求。

## <a name="monitor-your-wipe-requests"></a>监视擦除请求

你将获得一个汇总报表，其中介绍了擦除请求的总体状态，并包括挂起请求数和失败次数。 若要获取更多详细信息，请按以下步骤操作：

1.  在“移动应用 - 应用选择性擦除” 边栏选项卡中，可以查看按用户分组的请求列表。 由于系统会为设备上运行的每个受保护应用都创建一个擦除请求，因此对于某个用户，你可能会看到多个请求。 状态指示擦除请求是“挂起” 、“失败”还是“成功”。

    ![新建擦除请求边栏选项卡的屏幕截图](../media/wipe-request-status-1.png)

此外，还可以查看设备名称及其设备类型，这在阅读报表时非常有用。

>[!IMPORTANT]
> 用户必须打开应用才能进行擦除，进行请求后可能需要最多 30 分钟才能完成擦除。

## <a name="delete-a-wipe-request"></a>删除擦除请求

手动删除之前将显示具有挂起状态的擦除。  手动删除擦除请求：

1.  在“擦除请求”边栏选项卡上，选择“擦除请求”磁贴，打开“擦除请求”边栏选项卡。

2.  右键单击要删除的擦除请求，然后选择“删除擦除请求”。

    ![新建擦除请求边栏选项卡的屏幕截图](../media/delete-wipe-request.png)

3.  系统将提示你确认删除，请选择“是”或“否”，然后单击“确定”。

### <a name="see-also"></a>另请参阅
[什么是应用保护策略](what-is-app-protection-policy.md)

[什么是应用管理](what-is-app-management.md)


<!--HONumber=Feb17_HO2-->


