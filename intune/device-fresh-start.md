---
title: "重置使用 Intune 的 Windows 10 设备"
titlesuffix: Azure portal
description: "了解如何使用“全新启动”重置运行 Intune 的 Windows 10 电脑。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff6198cb42d5c96ed4e4c4e0009a8bbd6f6a0dec
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2017
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>使用“全新启动”重置使用 Intune 的 Windows 10 设备


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“全新启动”设备操作可删除在运行创意者更新的 Windows 10 电脑上安装的所有应用，然后将电脑自动更新到 Windows 的最新版本。
这可用于删除新电脑通常附带的预先安装的 (OEM) 应用。 发出此设备操作时可以配置是否保留用户数据。 在这种情况下，应用和设置已删除，但会保留用户主页文件夹的内容。

## <a name="how-to-use-fresh-start"></a>如何使用全新启动

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理设备列表中，选择一项 Windows 10 桌面设备，然后选择“全新启动”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。

