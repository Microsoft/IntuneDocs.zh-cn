---
title: "使用 Intune 从设备中删除公司数据"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 从设备中仅删除公司数据。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8074d6e7cc0a061a6708f8c8bfae1a4dfcb6daa3
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>从 Intune-托管设备中删除公司数据


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“删除公司数据”设备操作只会从 Intune 管理的设备中删除公司数据。 此操作不会删除设备中的个人数据。 删除之后，设备不再由 Intune 管理，且不能再访问公司资源。

## <a name="supported-platforms"></a>受支持的平台

- Windows - 支持（加入 Azure Active Directory 的 Windows 设备不支持）
- Windows Phone - 支持
- iOS - 支持
- macOS - 支持
- Android - 支持

## <a name="how-to-remove-company-data"></a>如何删除公司数据

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理的设备列表中选择一台设备，然后选择“删除公司数据”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
