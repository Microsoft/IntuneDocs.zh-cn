---
title: 在 Microsoft Intune 中创建设备配置文件 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中添加或配置设备配置文件，包括选择平台类型以及在 Azure 门户内配置设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cb6e3f0a9f62348d55b5dc2284c1007ea7faf088
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203206"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>在 Microsoft Intune 中创建设备配置文件

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。

2. 选择“设备配置” > “配置文件” > “创建配置文件”。

3. 输入以下属性：

   - **名称**：输入新配置文件的描述性名称。
   - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
   - **平台**：选择平台类型：  

       - **Outlook Web Access (OWA)**
       - **Android 企业**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 及更高版本**
       - **Windows 10 及更高版本**

   - **配置文件类型**：选择要创建的类型。 列表取决于所选择的平台。
   - **设置**：以下文章介绍了每种配置文件类型的设置：

       -  [设备功能](device-features-configure.md)
       -  [设备限制](device-restrictions-configure.md)
       -  [Endpoint protection](endpoint-protection-configure.md)
       -  [标识保护](identity-protection-configure.md)  
       -  [展台](kiosk-settings.md)
       -  [Email](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  针对 [Windows 10](education-settings-configure.md) 和 [iOS](wi-fi-settings-ios.md) 的教育
       -  [Windows 10 版本升级](edition-upgrade-configure-windows-10.md)
       -  [iOS 更新策略](software-updates-ios.md)
       -  [证书](certificates-configure.md)
       -  [Windows 信息保护](windows-information-protection-configure.md)
       -  [自定义](custom-settings-configure.md)

     ![“创建配置文件”的屏幕截图](./media/create-device-profile.png)

4. 完成后，选择“创建”。

配置文件随即创建并显示在列表中。

## <a name="next-steps"></a>后续步骤
[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
