---
title: "创建 Intune 设备配置描述文件 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何创建 Intune 设备配置描述文件。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89afae81076d563f4ebba289f8fa82eaea6ab234
ms.openlocfilehash: 6c6ac8112a6b6413df635607a24d0d06466c0b88


---

# <a name="how-to-create-device-configuration-profiles"></a>如何创建设备配置描述文件 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“配置设备”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
2. 在显示配置文件列表的边栏选项卡上，选择“创建配置文件”。
3. 在“创建配置文件”边栏选项卡上，指定下列信息：
    - **名称** - 输入新配置文件的描述性名称。
    - **说明** - 输入配置文件的可选说明。
    - **平台** - 选择要创建的配置文件的平台类型。
    - **配置文件类型** - 选择要创建的配置文件的类型。 可用类型的列表根据你选择的平台而有所不同。
    - **设置** - 有关每种配置文件类型的设置的信息，请参阅以下主题：
        -  [设备限制设置](/intune-azure/configure-devices/how-to-configure-device-restrictions)
        -  [电子邮件设置](/intune-azure/configure-devices/how-to-configure-email-settings)
        -  [VPN 设置](/intune-azure/configure-devices/how-to-configure-vpn-settings)
        -  [Wi-Fi 设置](/intune-azure/configure-devices/how-to-configure-wi-fi-settings)
        -  [Windows 10 版本升级设置](/intune-azure/configure-devices/how-to-configure-windows-10-edition-upgrade)
        -  [证书设置](/intune-azure/configure-devices/how-to-configure-certificates)
        -  [Windows 信息保护设置](/intune-azure/configure-devices/how-to-configure-windows-information-protection)
        -  [教育设置](/intune-azure/configure-devices/education-settings-for-ios.md)
        -  [自定义设置](/intune-azure/configure-devices/how-to-configure-custom-settings)

    ![创建设备配置文件](./media/create-device-profile.png)
4. 完成配置设置后，在“创建配置文件”边栏选项卡上，选择“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](how-to-assign-device-profiles.md)。


### <a name="next-steps"></a>后续步骤
有关如何分配设备配置文件的信息，请参阅[如何使用 Microsoft Intune 分配设备配置文件](/intune-azure/configure-devices/how-to-assign-device-profiles)。



<!--HONumber=Feb17_HO1-->


