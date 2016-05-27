---
# required metadata

title: 在 Microsoft Intune 中注册企业所有的 iOS 设备 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 在 Microsoft Intune 中注册企业所有的 iOS 设备
Microsoft Intune 支持注册企业所拥有的 iOS 设备，方法是使用 Apple 的设备注册计划 (DEP)，或在 Mac 计算机上运行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具。

可通过以下三种方式注册企业拥有的 iOS 设备：

-   **“设置助理注册”** – 恢复设备的出厂设置，使其准备好由设备的新用户设置。 此方法要求管理员通过 USB 将 iOS 设备连接到运行 Apple Configurator 的 Mac 计算机以预配置注册。 随后设备会交付给其用户，他们会运行设置助理过程，使用其工作或学校凭据配置设备并完成注册过程。 [使用 Apple Configurator 和设置助理注册 iOS 设备](ios-setup-assistant-enrollment-in-microsoft-intune.md)

-   **直接注册** – 在设备准备过程中创建 Apple Configurator 兼容文件以供使用。 已注册的设备没有进行出厂重置，但没有用户隶属关系。 此方法要求管理员通过 USB 将 iOS 设备连接到运行 Apple Configurator 的 Mac 计算机以注册设备。 [使用 Apple Configurator 直接注册来注册 iOS 设备](ios-direct-enrollment-in-microsoft-intune.md)

-   **设备注册计划 (DEP)** – 以“无线”方式将注册配置文件部署到通过 Apple 的设备注册计划购买的设备。 用户在设备上运行设置助理时，设备会在 Intune 中进行注册。  用户无法注销通过 DEP 注册的设备。 [注册设备注册计划 iOS 设备](ios-device-enrollment-program-in-microsoft-intune.md)




### 另请参阅
[为在 Microsoft Intune 中注册设备做好准备](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


