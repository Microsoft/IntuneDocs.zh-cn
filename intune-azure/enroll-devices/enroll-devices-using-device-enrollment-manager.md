---
title: "注册设备 - 设备注册管理员"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：使用设备注册管理器帐户在 Intune 中注册设备。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: b4629d98f935ab2fac95144940e2a58a1b1e7c5c
ms.lasthandoff: 02/18/2017

---

# <a name="enroll-devices-using-device-enrollment-manager"></a>使用设备注册管理器注册设备

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

组织可以使用 Intune 来管理大量带有单一用户帐户的移动设备。 设备注册管理器 (DEM) 帐户是可注册最多 1,000 台设备的特殊用户帐户。 将现有用户添加到 DEM 帐户以向他们提供特殊 DEM 功能。 每台已注册设备均使用单一许可证。 我们建议将通过此帐户注册的设备用作共享设备，而不是个人 ("BYOD") 设备。  

用户必须在 Azure 门户中存在才能添加为设备注册管理器。 为获得最佳安全性，DEM 用户也不应是 Intune 管理员。

>[!NOTE]
>DEM 注册方法不能与以下其他注册方法一起使用：[Apple Configurator 与设置助手](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)、[Apple Configurator 与直接注册](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)或[设备注册计划](enroll-ios-devices-using-device-enrollment-program.md)。 

## <a name="example-of-a-device-enrollment-manager-scenario"></a>设备注册管理器方案示例

一家餐厅想为服务员提供 50 台销售点平板电脑，为厨房员工提供订单监视器。 员工无需访问公司数据或以用户身份登录。 Intune 管理员将创建一个设备注册管理器帐户并向该 DEM 帐户添加餐厅主管，使主管拥有 DEM 功能。 现在主管便可使用 DEM 凭据注册这 50 台平板电脑。

只有 Intune 控制台中的用户可以是设备注册管理员。 设备注册管理器用户不能充当 Intune 管理员。

DEM 用户可以：

-   在 Intune 中最多注册 1000 台设备。
-   登录到公司门户以获得公司应用。
-   通过向平板电脑部署特定于角色的应用来配置对公司数据的访问权限。

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>使用 DEM 帐户注册的设备限制

使用设备注册管理器帐户注册的设备具有以下限制：

  - 没有具体的设备“用户”。 因此，也没有电子邮件或公司数据访问。 但是 VPN 等仍可用于向设备应用提供数据访问权限。

  - 无条件性访问，因为这些设备按每个用户进行注册。

  - DEM 用户无法在设备本身上使用公司门户注销 DEM 注册的设备。 Intune 管理员具有此功能，但 DEM 用户没有。

  - 公司门户应用或网站中仅显示本地设备。
 
  - 用户无法使用 Apple 批量购买计划 (VPP) 应用，因为每个用户都需具有 Apple ID 才可管理应用。
 
  - （仅限 iOS）如果使用 DEM 注册 iOS 设备，则无法使用 Apple Configurator 或 Apple Device Enrollment Program (DEP) 注册设备。


> [!NOTE]
> 若要将公司应用部署到设备注册管理器托管的设备，请将公司门户应用作为“**必需的安装**”部署到此设备注册管理器用户帐户。
> 为提高性能，在 DEM 设备上查看公司门户应用将仅显示本地设备。 仅可通过 Intune 管理控制台执行其他 DEM 设备的远程管理。


## <a name="add-a-device-enrollment-manager"></a>添加一个设备注册管理器

1.  在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2.  在 Intune 边栏选项卡上，选择“注册设备”，然后选择“设备注册管理器”。

3.  选择“添加”。

4.  在“添加用户”边栏选项卡上，输入 DEM 用户的用户主体名称，并选择“添加”。 DEM 用户将添加到 DEM 用户列表。

## <a name="remove-a-device-enrollment-manager"></a>删除设备注册管理器

删除设备注册管理器不会影响已注册的设备。 删除设备注册管理器后：

-   从 DEM 用户列表中删除用户不会影响已注册的设备，已注册的设备仍然完全受托管。

-   已删除的设备注册管理器帐户凭据仍然有效。

-   已删除的设备注册管理器仍无法擦除或停用设备。

-   已删除的设备注册管理器无法注册其他设备，除非尚未达到 Intune 管理员配置的每设备限制。

**删除设备注册管理器**

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在 Intune 边栏选项卡上，选择“注册设备”，然后选择“设备注册管理器”。

3. 在“设备注册管理器”边栏选项卡上，右键单击 DEM 用户，然后选择“删除”。

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>查看设备注册管理器的属性

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在 Intune 边栏选项卡上，选择“注册设备”，然后选择“设备注册管理器”。

3. 在“设备注册管理器”边栏选项卡上，右键单击 DEM 用户，然后选择“属性”。

