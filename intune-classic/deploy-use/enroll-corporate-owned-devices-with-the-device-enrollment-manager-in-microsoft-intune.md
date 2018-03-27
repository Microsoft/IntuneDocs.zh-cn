---
title: 使用设备注册管理器进行注册
description: 设备注册管理器 (DEM) 帐户可以管理大量带有单一用户帐户的企业自有的共享移动设备。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0f9ecb8cf16d8c344ea595c53ab91c9b1f00c90e
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>使用 Microsoft Intune 中的设备注册管理器注册企业自有设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

组织可以使用 Intune 来管理大量带有单一用户帐户的移动设备。 *设备注册管理器* (DEM) 帐户是专用的用户帐户，可注册最多 1,000 台设备。 将现有用户添加到要为其提供专用 DEM 功能的 DEM 帐户。 每台已注册设备均使用单一许可证。 建议将通过此帐户注册的设备用作共享设备（即没有用户关联），而不是个人 ("BYOD") 设备。  

用户必须在 Azure 门户中存在才能添加为设备注册管理器。 为获得最佳安全性，DEM 用户也不应是 Intune 管理员。

>[!NOTE]
>DEM 注册方法不能与 [Apple Configurator 设置助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)、[直接许可登记表](ios-direct-enrollment-in-microsoft-intune.md)、macOS 或 [DEP 注册方法](ios-device-enrollment-program-in-microsoft-intune.md)结合使用。

## <a name="example-of-a-device-enrollment-manager-scenario"></a>设备注册管理器方案示例

一家餐厅想为服务员提供 50 台销售点平板电脑，为厨房员工提供订单监视器。 员工无需访问公司数据或以用户身份登录。 Intune 管理员将创建一个设备注册管理器帐户并向该 DEM 帐户添加餐厅主管，使主管拥有 DEM 功能。 现在主管便可使用 DEM 凭据注册这 50 台平板电脑。

只有 Intune 控制台中的用户可以是设备注册管理员。 设备注册管理器用户不能充当 Intune 管理员。

DEM 用户可以：

-   在 Intune 中最多注册 1000 台设备
-   使用公司门户应用以获得公司应用
-   通过向平板电脑部署特定于角色的应用来配置对公司数据的访问权限

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>使用 DEM 帐户注册的设备限制

使用设备注册管理器帐户注册的设备具有以下限制：

  - 没有具体的设备“用户”。 因此，也没有电子邮件或公司数据访问。 但是 VPN 等仍可用于向设备应用提供数据访问权限。

  - 无条件性访问，因为这些设备按每个用户进行注册。

  - DEM 用户无法在设备本身上使用公司门户注销 DEM 注册的设备。 Intune 管理员具有此功能，但 DEM 用户没有。

  - 公司门户应用或网站中仅显示本地设备。

  - 用户无法使用 Apple 批量购买计划 (VPP) 应用，因为每个用户都需具有 Apple ID 才可管理应用。

  - （仅限 iOS）如果使用 DEM 注册 iOS 设备，则无法使用 Apple Configurator 或 Apple Device Enrollment Program (DEP) 注册设备。

> [!NOTE]
> 若要将公司应用部署到设备注册管理器托管的设备，请将公司门户应用作为“必需的安装”部署到此设备注册管理器用户帐户。
> 为提高性能，在 DEM 设备上查看公司门户应用将仅显示本地设备。 仅可通过 Intune 管理控制台执行其他 DEM 设备的远程管理。


## <a name="add-a-device-enrollment-manager"></a>添加一个设备注册管理器

1.  确保想要向 DEM 帐户添加的用户已存在。 如果需要添加用户，请登录到 [Office 365 门户](https://go.microsoft.com/fwlink/p/?LinkId=698854)，然后按照[向 Office 365 门户逐一或批量添加用户](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)中的步骤进行操作。

2.  使用管理员凭据登录到 [Microsoft Intune 管理控制台](https://manage.microsoft.com)。

3.  在导航窗格中，选择“**管理员**”，转到“**管理员管理**”，然后选择“**设备注册管理器**”。 此时将打开**设备注册管理器**页。

4.  选择“添加…”。 打开“添加设备注册管理员”对话框。

5.  输入 Intune 帐户的“用户 ID”，然后选择“确定”。

    DEM 用户现在可以使用相同的过程注册移动设备，与最终用户在公司门户中针对 BYOD 方案采用的过程相同。 管理器最终用户可以使用 DEM 凭据在多达 1000 台设备上安装公司门户应用并注册设备。 若要深入了解用于每个平台的最终用户注册步骤，请参阅：

  - [在 Intune 中注册 iOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)
  - [在 Intune 中注册 macOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)
  - [在 Intune 中注册 Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)
  - [在 Intune 中注册 Windows 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)

## <a name="delete-a-device-enrollment-manager-from-intune"></a>从 Intune 删除设备注册管理员

1.  使用管理员凭据登录到 [Microsoft Intune 管理门户](https://manage.microsoft.com)。

2.  在导航窗格中，选择“**管理员**”，转到“**管理员管理**”，然后选择“**设备注册管理器**”。 此时将打开**设备注册管理器**页。

3.  选择要删除的设备注册管理员“用户”，然后选择“删除”。 不会从 Intune 中删除此用户，并且此用户管理的设备仍将在 Intune 中处于注册状态。 删除设备注册管理员可防止该用户在 Intune 中注册更多设备。

4.  选择“是”，确认删除此设备注册管理器。

删除设备注册管理器不会影响注册的设备。 删除设备注册管理器时：

-   已注册设备均不会受到影响。

-   仍能继续完全管理已注册设备。

-   已删除的设备注册管理器帐户凭据仍有效，能够登录到公司门户来访问应用。

-   已删除的设备注册管理器帐户凭据仍无法擦除或停用设备。

-   已删除的设备注册管理器帐户与已注册设备的关系仍存在，但不可以注册任何其他设备。
