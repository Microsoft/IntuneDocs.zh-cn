---
title: 为 Autopilot 预配的设备添加和分配 Windows 10 公司门户应用
titleSuffix: Microsoft Intune
description: 为 Autopilot 预配的设备添加 Windows 10 公司门户应用并将其分配给 Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2020
ms.locfileid: "77577280"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>为 Autopilot 预配的设备添加和分配 Windows 10 公司门户应用

若要管理设备和安装应用，你的用户可以使用公司门户应用。 可以直接从 Intune 分配 Windows 10 公司门户应用。 

## <a name="prerequisites"></a>必备条件

对于 Windows 10 Autopilot 预配的设备，建议将适用于企业的 Microsoft Store 帐户与 Intune 进行关联。 有关详细信息，请参阅[如何使用 Microsoft Intune 管理从适用于企业的 Microsoft Store 批量采购的应用](~/apps/windows-store-for-business.md)。

使用以下步骤选择要安装的公司门户（脱机）。 如果将公司门户应用分配给 Autopilot 组并在用户登录之前将其安装在设备上，则将在设备上下文中安装该应用。 

## <a name="configure-settings-to-show-offline-apps"></a>配置设置以显示脱机应用
1. 使用管理员帐户登录到[适用于企业的 Microsoft Store](https://www.microsoft.com/business-store)。
2. 选择窗口顶部附近的“管理”选项卡  。
3. 在左窗格中，选择“设置”  。
4. 在“购物体验”下，将“显示脱机应用”设置为“开”    。  
    将显示脱机许可的应用。

## <a name="get-the-offline-company-portal-app"></a>获取脱机公司门户应用
1. 搜索并选择“公司门户”应用  。
2. 将“许可证类型”设置为“脱机”   。
3. 选择“获取应用”以获取脱机公司门户应用，并将其添加到清单中  。

## <a name="assign-the-company-portal-app"></a>分配公司门户应用
1.  使用管理员帐户登录到  [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 
2. 在右窗格中选择“应用” 选项卡 **** 。 
3. 在“按平台”下，选择“Windows” ****  。 
4. 选择“公司门户(脱机)” **** 。   
5. 必须等待同步计划完成，或者从 Microsoft 终结点管理器管理中心执行手动同步。
6. 将公司门户应用作为所需应用分配到你所选的 Autopilot 设备组。

## <a name="next-steps"></a>后续步骤

- 如需了解有关分配应用的详细信息，请参阅[将应用分配给组](apps-deploy.md)。

