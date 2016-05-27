---
# required metadata

title: 在 Microsoft Intune 中注册设备 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 在 Intune 中注册设备以进行管理
Microsoft Intune 移动设备管理 (MDM) 使用注册将设备纳入管理以及允许访问资源。 注册设备的方式取决于设备类型、所有权和所需管理级别。 “自带设备办公”(BYOD) 和公司拥有的设备 (COD) 方案需要注册过程。 使用 Exchange ActiveSync（在本地或在云中承载）的组织可以实现无需注册的更轻型管理。 还可以使用 Intune 客户端软件管理 Windows 电脑。

## 启用设备注册  
 注册使用户可以在其个人设备上访问公司资源，并使管理员可以确保这些设备符合保护公司资源的策略。 这是使用 Intune 实现“自带设备办公”方案的最佳方式。 管理员必须在 Intune 控制台中启用注册，这可能需要创建与设备的信任关系以及向用户分配许可证。 设备随后进行注册（通常由用户输入其工作或学校凭据）。 设备随后从 Intune 接收策略并获取对资源的访问权限。

[准备好在 Intune 中注册设备](get-ready-to-enroll-devices-in-microsoft-intune.md)

## 注册公司拥有的设备。
可以使用 Intune 控制台管理公司拥有的设备 (COD)。 可以直接通过 Apple 提供的工具注册 iOS 设备。 管理员或经理可以使用设备注册管理器注册所有设备类型。 具有 IMEI 号码的设备也可以标识并标记为公司拥有，以实现 COD 方案。

[注册公司拥有的设备。](manage-corporate-owned-devices.md)

## 使用 Exchange ActiveSync 和 Intune 管理移动设备
可以使用 EAS MDM 策略，通过 Intune 管理未注册、但连接到 Exchange ActiveSync (EAS) 的移动设备。 Intune 使用 Exchange Connector 与 EAS（在本地或是云承载）通信。



[使用 Exchange ActiveSync 和 Intune 管理移动设备](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## 使用 Intune 管理 Windows PC  
还可以使用 Microsoft Intune 管理使用 Intune Windows 电脑客户端软件的 Windows 电脑。 使用 Intune 客户端管理的电脑可以：

 - 报告软件和硬件清单
 - 安装桌面应用程序（例如 .exe 和 .msi 文件）
 - 防火墙设置

使用 Intune 客户端软件管理的计算机不能有选择地擦除或停用，并且不能利用许多 Intune 管理功能（如条件性访问、VPN 和 Wi-Fi 设置或证书和电子邮件配置的部署）。

[使用 Intune 管理 Windows PC](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


