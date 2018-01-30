---
title: "iOS 的 Intune 共享设备配置设置"
titlesuffix: Azure portal
description: "了解在 iOS 设备锁定屏幕上显示信息可以使用的 Intune 设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c5473a280551ab74f781a2de682d7e5922491e98
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>用于在 iOS 设备锁定屏幕上显示消息的共享设备配置设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

共享设备配置设置使你能够指定在登录窗口和锁定屏幕上显示的可选文本。 例如，可输入“如果丢失，返回到”消息和资产标记信息。 

>[!IMPORTANT]
> 此功能支持运行 iOS 9.3 和更高版本的监督设备。

## <a name="create-shared-device-settings"></a>创建共享设备设置

1. 在“设备功能”边栏选项卡上，选择“共享设备配置（仅限监督设备）”。
2. 在“共享设备配置（仅限监督设备）”边栏选项卡上，配置以下设置：
    - **资产标记信息** - 输入有关设备的资产标记的信息。 例如：“由 Contoso 公司拥有”。所输入的信息会应用于分配此配置文件的所有设备。
    - **锁定屏幕脚注** - 输入一个可帮助在设备丢失或被盗时将其找回的注释。 例如：**如果找到，调用“数字”**。
3. 完成后，选择“确定”，直到返回到“创建配置文件”边栏选项卡，然后选择“创建”。 


## <a name="next-steps"></a>后续步骤

现在可将设备配置文件分配到所选择的组。 有关详细信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。
