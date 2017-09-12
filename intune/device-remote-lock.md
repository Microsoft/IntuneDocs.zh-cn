---
title: "使用 Intune 远程锁定受管理设备"
titlesuffix: Azure portal
description: "了解如何使用 Intune 远程锁定你管理的设备。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6c5d282efbd3b0fe90c93ec813f2f513c1932a6e
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="remotely-lock-managed-devices-with-intune"></a>使用 Intune 远程锁定受管理设备


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**远程锁定**设备将锁定所选的设备。 设备所有者必须使用其密码才能解锁设备。 只能远程锁定设置了 PIN 或密码的设备。

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - Windows Phone 8.1 及更高版本支持
- iOS - 支持
- macOS - 不支持
- Android - 支持

## <a name="how-to-remote-lock-a-device"></a>如何远程锁定设备

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从你管理的设备列表中，选择设备，然后选择“远程锁定”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
