---
title: 如何仅擦除应用中的公司数据
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 选择性地仅擦除 Intune 托管应用中的公司数据。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1f6992aa93e1ca5a095b1e92a16a07bd0eb1c2f5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513626"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>如何仅擦除 Intune 托管应用中的企业数据

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

当设备丢失或被盗，或如果员工离开公司，你想要确保从设备中删除了公司应用数据。 但是，你可能不想删除设备上的个人数据，尤其是如果该设备为员工所有。

>[!NOTE]
> iOS/iPadOS、Android 和 Windows 10 平台是当前支持从 Intune 托管应用中擦除公司数据的三个平台。 Intune 托管应用是包含 Intune 应用 SDK 的应用程序，并且拥有贵组织的许可用户帐户。 不需要部署应用程序保护策略来启用应用选择性擦除。

若要选择性地删除公司应用数据，请按照本主题中的步骤创建擦除请求。 请求完成之后，应用下次在设备上运行时，会从应用中删除公司数据。 除了创建擦除请求外，还可在不满足应用程序保护策略 (APP) 访问设置的条件时，将组织数据的选择性擦除配置为新操作。 此功能可帮助你根据预先配置的标准自动保护和删除应用程序中的敏感组织数据。

>[!IMPORTANT]
> 将删除从应用直接同步到本机通讯簿的联系人。 无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 目前仅适用于 Microsoft Outlook 应用。

## <a name="deployed-wip-policies-without-user-enrollment"></a>已部署 WIP 策略（无需用户注册）
无需要求 MDM 用户注册 Windows 10 设备，即可部署 Windows 信息保护 (WIP) 策略。 此配置允许公司基于 WIP 配置保护其企业文档，同时允许用户管理自己的 Windows 设备。 使用 WIP 策略保护文档后，Intune 管理员可以选择性擦除受保护的数据。 通过选择用户和设备，并发送擦除请求，所有通过 WIP 策略保护的数据都将不可用。 在 Azure 门户中的“Intune”内，依次选择“客户端应用”   > “应用选择性擦除”  。 有关详细信息，请参阅[通过 Intune 创建和部署 Windows 信息保护 (WIP) 应用保护策略](windows-information-protection-policy-create.md)。

## <a name="create-a-wipe-request"></a>创建擦除请求

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用” > “应用选择性擦除” > “创建擦除请求”    。<br>
   将显示“创建擦除请求”  窗格。
3. 单击“选择用户”  ，选择要擦除其应用数据的用户，然后单击“选择用户”  窗格底部的“选择”  。

    ![“选择用户”窗格的屏幕截图](./media/apps-selective-wipe/apps-selective-wipe-01.png)

4. 单击“选择设备”，选择设备，然后单击“选择设备”窗格底部的“选择”    。

    ![选择设备的“创建擦除请求”窗格的屏幕截图](./media/apps-selective-wipe/apps-selective-wipe-02.png)

5. 选择“创建”以提出擦除请求  。

服务会为设备上的每个受保护应用以及与擦除请求相关联的用户创建并跟踪单独的擦除请求。

   ![“客户端应用 - 应用选择性擦除”窗格的屏幕截图](./media/apps-selective-wipe/apps-selective-wipe-03.png)

## <a name="monitor-your-wipe-requests"></a>监视擦除请求

你将获得一个汇总报表，其中介绍了擦除请求的总体状态，并包括挂起请求数和失败次数。 若要获取更多详细信息，请按以下步骤操作：

1. 在“应用”   > “应用选择性擦除”  窗格中，可以查看按用户分组的请求列表。 由于系统会为设备上运行的每个受保护应用都创建一个擦除请求，因此对于某个用户，你可能会看到多个请求。 状态指示擦除请求是“挂起”  、“失败”  还是“成功”  。

    ![“应用选择性擦除”窗格中擦除请求状态的屏幕截图](./media/apps-selective-wipe/wipe-request-status-1.png)

此外，还可以查看设备名称及其设备类型，这在阅读报表时非常有用。

>[!IMPORTANT]
> 用户必须打开应用才能进行擦除，进行请求后可能需要最多 30 分钟才能完成擦除。

## <a name="delete-a-wipe-request"></a>删除擦除请求

手动删除之前将显示具有挂起状态的擦除。 手动删除擦除请求：

1. 在“客户端应用 - 应用选择性擦除”窗格上  。

2. 从列表中，右键单击要删除的擦除请求，然后选择“删除擦除请求”  。

    ![“应用选择性擦除”窗格中擦除请求列表的屏幕截图](./media/apps-selective-wipe/delete-wipe-request.png)

3. 系统将提示你确认删除，请选择“是”  或“否”  ，然后单击“确定”  。

## <a name="see-also"></a>另请参阅
[什么是应用保护策略](app-protection-policy.md)

[什么是应用管理](app-management.md)
