---
title: Windows 设备的 Intune 注册方法功能
titleSuffix: Microsoft Intune
description: Windows 设备的每种注册方法对应的功能。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd1dbb3280fbbb93423796b18f6dd85a50a41f11
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567538"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Windows 设备的 Intune 注册方法功能
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

在 Intune 中注册工作人员设备的方法有多种。 每种方法都有不同的最佳做法和功能，如下表所示。

## <a name="best-practices-by-enrollment-method"></a>不同注册方法对应的最佳做法
| **Best practices**（最佳做法） | **[已联接 Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[使用 Autopilot 联接 Azure AD（用户驱动模式）](enrollment-autopilot.md)** |**[使用 Autopilot 联接 Azure AD（自部署模式）](enrollment-autopilot.md)** |**[批量](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|常用于 EDU 中|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|设备可以用作共享设备|![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|个人设备必须访问公司资源|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|应用的自助服务|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>不同注册方法对应的功能

| **功能** | **[已联接 Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[使用 Autopilot 联接 Azure AD（用户驱动模式）](enrollment-autopilot.md)** |**[使用 Autopilot 联接 Azure AD（自部署模式）](enrollment-autopilot.md)** |**[批量](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|条件性访问                                      |![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|
|用户与设备关联                    |![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|
|需要 Azure AD Premium                               |![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|
|设备可以评估受 CA 保护的资源             |![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|
|用户不能是其设备上的管理员               |![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|配置设备设置体验的功能        |![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|无需用户交互即可注册设备的功能      |![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|
|运行 PowerShell 脚本的功能                       |![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|支持 AD 域加入后的自动注册      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|
|支持混合 Azure AD 域加入后的自动注册|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|
|支持 Azure AD 加入后的自动注册       |![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![选中标记](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>后续步骤

[设置 Windows 的注册](windows-enroll.md)

