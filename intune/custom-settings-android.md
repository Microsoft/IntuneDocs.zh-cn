---
title: 在 Microsoft Intune 中添加适用于 Android 设备的自定义设置 - Azure | Microsoft Docs
description: 添加或创建适用于 Android 设备的自定义配置文件，进而创建具有预共享密钥的 WiFi 配置文件、按每个应用创建 VPN 配置文件，或在 Microsoft Intune 中允许/阻止适用于 Samsung Knox 标准设备的应用
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0195e138b59fae019fa2bc02aadf211257a65cac
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022044"
---
# <a name="custom-settings-for-android-devices---intune"></a>适用于 Android 设备的自定义设置 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

自定义配置文件使用开放移动联盟统一资源标识符 (OMA-URI) 设置配置 Android 设备上的不同功能。 移动设备制造商通常使用这些设置来控制设备上的功能。

通过自定义配置文件，可配置和分配以下 Android 设置。 Intune 策略未内置有这些设置：

- [创建具有预共享密钥的 Wi-Fi 配置文件](/intune/wi-fi-profile-shared-key)
- [创建每应用 VPN 配置文件](/intune/android-pulse-secure-per-app-vpn)
- [允许和阻止适用于 Samsung Knox 标准版设备的应用](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> 此配置文件类型仅可配置上述设置。 Android 设备不公开可配置的 OMA-URI 设置的完整列表。 如需查看更多设置，请在 [Intune Uservoice 网站](https://microsoftintune.uservoice.com/forums/291681-ideas)投票支持其他设置。

## <a name="custom-profile-settings-for-android-devices"></a>适用于 Android 设备的自定义配置文件设置

1. 登录到 [Azure 门户](https://portal.azure.com)。 
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 使用 Android 平台创建自定义配置文件。 相关步骤，请参见[在 Microsoft Intune 中配置自定义设备设置](custom-settings-configure.md)。
4. 在“自定义 OMA-URI 设置”中选择“添加”，然后选择“添加行”。
5. 输入以下属性：

   - **名称** - 输入 OMA-URI 设置的唯一名称，便于轻松查找。
   - **说明** - 输入设置的简要说明以及其他重要详细信息。
   - **数据类型** - 输入用于此 OMA-URI 设置的数据类型。 从“字符串”、“字符串 (XML)”、“日期和时间”、“整数”、“浮点”或者“布尔值”中进行选择。
   - **OMA-URI** - 输入所需的 OMA-URI。
   - **值** - 输入要与已输入的 OMA-URI 关联的值。

6. 选择“确定”，保存所做更改。 根据需要继续添加更多设置。

## <a name="next-steps"></a>后续步骤

完成设置后，就会配置文件并显示在列表中。 要向组分配此配置文件，请参阅[如何分配设备配置文件](device-profile-assign.md)。
