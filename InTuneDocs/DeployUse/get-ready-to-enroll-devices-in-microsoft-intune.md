---
# required metadata

title: 为在 Microsoft Intune 中注册设备做好准备 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 为在 Microsoft Intune 中注册设备做好准备
若要使员工可以向 Intune 注册移动设备（包括 Android、iOS 和 Windows Phone 与 Windows 电脑），必须启用设备注册。 若要允许注册，必须设置移动设备管理机构、配置 Intune 公司门户、分配许可证并为设备平台启用注册。

## <a name="BKMK_Set_MDM_Authority"></a>设置移动设备管理机构
MDM 机构定义有权管理一组设备的管理服务。 适用于 MDM 机构的选项包括 Intune 本身以及带 Intune 的 Configuration Manager。 如果将 Configuration Manager 设置为管理机构，则没有其他服务可以用于移动设备管理。

>[!IMPORTANT]
> 请仔细考虑是希望仅使用 Intune（联机服务），还是使用带 Intune 的 System Center Configuration Manager（与联机服务相结合的本地软件解决方案）来管理移动设备。 设置移动设备管理机构之后，无法更改它。



1.  在 [Microsoft Intune 管理员控制台](http://manage.microsoft.com)中，单击“管理” &gt; “移动设备管理”。

2.  在“任务”  列表中，单击“设置移动设备管理机构” 。 将打开“设置 MDM 机构”  对话框。

    ![“设置 MDM 机构”对话框](../media/intune-mdm-authority.png)

3.  Intune 要求确认你希望使用 Intune 作为 MDM 机构。 勾选复选框，然后单击“是”  ，使用 Microsoft Intune 管理移动设备。

## 配置 Intune 公司门户并分配许可证
Intune 公司门户可帮助用户访问公司资源（如应用）、查找技术支持信息以及注册和注销设备。 注册设备之前，应[配置公司门户](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-7)。 还必须[分配用户许可证](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-4)以允许访问 Intune。

## 设置设备管理
设置 MDM 机构之后，需要为组织要支持的操作系统设置设备管理。 设置设备管理所需的步骤因操作系统而异。 例如，Android OS 不需要你在 Intune 管理控制台中执行任何操作。 另一方面，Windows 和 iOS 需要设备与 Intune 之间存在信任关系才能允许进行管理。

> [!div class="op_single_selector"]
- [使用 Microsoft Intune 设置 Android 管理](set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [使用 Microsoft Intune 设置 Windows Phone 管理](set-up-windows-phone-management-with-microsoft-intune.md)
- [使用 Microsoft Intune 设置 Windows 设备管理](set-up-windows-device-management-with-microsoft-intune.md)

你还可以：
 - 使用[设备注册管理器帐户](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)注册多个设备
 - [使用 IMEI 号码指定公司拥有的设备](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)以帮助注册设备和目标策略


<!--HONumber=May16_HO2-->


