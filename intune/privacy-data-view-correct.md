---
title: 视图和正确的个人数据
description: 了解如何查看和更正个人数据。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1ba77bc7-505e-4eca-a49e-dcdaa75d0043
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d0567d605afeb37812d495cc6192100ab76444f
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57399075"
---
# <a name="view-and-correct-personal-data"></a>视图和正确的个人数据

Intune 管理员可基于其访问权限查看某些个人数据，但只有最终用户才可更改其设备的个人数据。

[!INCLUDE [GDPR-related guidance](./includes/gdpr-dsr-and-stp-note.md)]


## <a name="view-personal-data"></a>查看个人数据

管理员可在 Intune 用户界面的不同边栏选项卡中查看最终用户个人信息。 以下文章说明信息管理员有权和无权访问的信息：
- [在 Intune 中查看设备详细信息](device-inventory.md)介绍了如何查看某个最终用户的设备的相关详细信息。
- [监视应用信息和分配](apps-monitor.md)介绍了如何查看最终用户设备上安装的应用的相关详细信息。
- [在我注册自己的设备时，我的公司可以看到哪些信息？](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)一文向最终用户提供其公司可以看到和不能看到的数据列表。 最好明确告知用户你要收集的数据类型以及收集的原因。 可参阅本文来开启确保透明度的第一步。

### <a name="who-can-view-the-data"></a>谁可以查看数据？

Microsoft 使用严格的控制来管理对客户数据的访问权限，以授予完成关键任务所需的最低级别的访问权限，并在不再需要时撤销访问权限。 

可使用基于角色的管理控制 (RBAC) 来保护和控制对最终用户个人数据的访问权限。 有关详细信息，请参阅 [RBAC 与 Microsoft Intune](role-based-access-control.md)。

有关 Microsoft 数据实践的详细信息，请参阅 Online Services 条款和 [Microsoft Online Services 隐私声明](http://go.microsoft.com/fwlink/p/?linkid=131004&clcid=0x409)。 

## <a name="correct-end-user-personal-data"></a>更正最终用户的个人数据

管理员不能更新设备或应用特定的信息。 如果最终用户要更正任何个人数据（如设备名），必须直接在其设备上执行该操作。 此类更改在下次连接到 Intune 时同步。


## <a name="next-steps"></a>后续步骤

了解如何在 Intune 中[审核、导出或删除](privacy-data-audit-export-delete.md)个人数据。
