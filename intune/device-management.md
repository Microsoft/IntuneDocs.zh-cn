---
title: "利用 Intune 来管理设备"
titleSuffix: Intune on Azure
description: "了解如何查看使用 Intune 管理的设备，并在设备上执行各种操作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f066e62e323fffb7c6954d83b2b55ee63f4be46
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>什么是 Microsoft Intune 设备管理？


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**设备**工作负荷可以让你了解所管理的设备，并能在这些设备上执行远程任务。 若要访问工作负荷，请执行以下操作：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。

现在，可以执行下列操作：

- [查看设备清单](device-inventory.md)
- 执行远程设备操作：
    - [删除公司数据](device-company-data-remove.md) 
    - [恢复出厂设置](device-factory-reset.md)
    - [远程锁定](device-remote-lock.md)
    - [重置密码](device-passcode-reset.md)
    - [绕过激活锁](device-activation-lock-bypass.md)
    - [重新开始](device-fresh-start.md)
    - [丢失模式](device-lost-mode.md)
    - [查找设备](device-locate.md)
    - [重新启动](device-restart.md)
    - [Windows 10 PIN 重置](device-windows-pin-reset.md)
    - [适用于 Android 的远程控制](device-profile-android-teamviewer.md)


## <a name="support-for-each-device-action"></a>对每个设备操作的支持

通过下表了解每个操作支持的设备平台。

|||||||
|-|-|-|-|-|-|
|设备操作|Windows|Windows Phone|iOS|macOS|Android|
|**删除公司数据**|是|是|是|是|是|
|**恢复出厂设置**|Windows 8.1 及更高版本（非 EAS 托管设备）|是|是|否|不支持 Android for Work|
|**删除**|是|是|是|是|是|
|**远程锁定**|否|Windows Phone 8.1 及更高版本|是|否|是|
|**重置密码**|否|Windows Phone 8.1 到 Windows 10 创意者更新（未加入 Azure AD），Windows 10 创意者更新及更高版本 - 全部|是|否|Android 7 之前的版本不支持 Android for Work|
|**新密码**（适用于 Windows 10 设备）|否|Windows 10 创意者更新及更高版本（加入 Azure AD）|否|否|不支持 Android for Work|
|**绕过激活锁**|否|否|仅企业拥有的设备|否|否|
|**丢失模式**|否|否|iOS 9.3 及更高版本，公司拥有的受监视的设备|否|否|
|**查找设备**|否|否|丢失模式 iOS 9.3 及更高版本，公司拥有的受监视的设备|否|否|
|**注销当前用户**|否|否|iOS 9.3 及更高版本（仅共享 iPad 设备）|否|否|
|**重新启动**|Windows 8.1 及更高版本|Windows Phone 8.1 及更高版本|否|否|否|
|**重新开始**|Windows 10 创意者更新及更高版本|否|否|否|否|
|**新远程协助会话**|否|否|否|否|是|
|**删除用户**|否|否|iOS 9.3 及更高版本（仅共享 iPad 设备）|否|否|

## <a name="next-steps"></a>后续步骤

- 选择“设备操作”以查看对所管理设备执行的操作的状态。 
![监视设备操作](./media/monitor-device-actions.png)