---
title: 将 Android Enterprise 系统应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Enterprise 系统应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11618d844fe7c4e190295ad06111ae0944deda95
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507278"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>将 Android Enterprise 系统应用添加到 Microsoft Intune

将应用分配给一个设备或一组用户之前，必须先将应用添加到 Microsoft Intune。 Android Enterprise 设备支持系统应用。 你可以为 [Android Enterprise 专用设备](../enrollment/android-kiosk-enroll.md)或[完全托管设备](../enrollment/android-fully-managed-enroll.md)启用系统应用。

## <a name="add-the-app"></a>添加应用

通过执行以下步骤，从 Azure 门户将 Android Enterprise 系统应用添加到 Intune：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在“Intune”窗格中，选择“客户端应用” > “应用” > “添加”     。
3. 在“添加应用”窗格中的“其他”类型下，选择“Android Enterprise 系统应用”    。
4. 若要配置应用信息，请选择“配置”，然后提供以下信息  ：
    - **应用名称**：输入应用的名称。
    - **发布者**：输入应用发布者的名称。  
    - **包名称**：输入包名称。 Intune 将验证包名称是否有效。
5. 选择“确定”  。
6. 选择“添加”  。

> [!NOTE]
> 需要与设备的 OEM 合作，查找要启用/禁用的应用的包名称。

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。 

Android Enterprise 系统应用将启用或禁用已成为平台一部分的应用。 若要启用应用，请将系统应用分配为“必需”  。 若要禁用应用，请将系统应用分配为“卸载”  。 无法将系统应用分配为可供用户使用。


## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)
