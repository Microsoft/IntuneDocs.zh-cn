---
title: 适用于 iOS 的 Microsoft Intune 共享设备配置设置
titlesuffix: ''
description: 了解在 iOS 设备锁定屏幕上显示信息可以使用的 Microsoft Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7c735486ad93bd76350435861482505a1ab0d30a
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>用于在 iOS 设备锁定屏幕上显示消息的共享设备配置设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍了可用于在 iOS 设备锁定屏幕上显示信息的 Microsoft Intune 设置。

共享设备配置设置使你能够指定在登录窗口和锁定屏幕上显示的可选文本。 例如，可输入“如果丢失，返回到”消息和资产标记信息。 

>[!IMPORTANT]
> 此功能支持运行 iOS 9.3 和更高版本的监督设备。

## <a name="create-shared-device-settings"></a>创建共享设备设置

1. 从 [Azure 门户中的 Intune](https://portal.azure.com)，导航到[设备配置区域中的“设备功能”](device-features-configure.md)。 
1. 在“设备功能”窗格上，选择“共享设备配置（仅限监督设备）”。
2. 在“共享设备配置（仅限监督设备）”窗格上，配置以下设置：
    - **资产标记信息** - 输入有关设备的资产标记的信息。 例如：“由 Contoso 公司拥有”。所输入的信息会应用于分配此配置文件的所有设备。
    - **锁定屏幕脚注** - 输入一个可帮助在设备丢失或被盗时将其找回的注释。 例如：**如果找到，调用“数字”**。
3. 完成后，选择“确定”，直到返回到“创建配置文件”窗格，然后选择“创建”。 


## <a name="next-steps"></a>后续步骤

现在可将设备配置文件分配到所选择的组。 有关详细信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。
