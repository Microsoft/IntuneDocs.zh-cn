---
title: "使用设备注册管理器进行注册 | Microsoft Intune"
description: "设备注册管理器 (DEM) 帐户可以管理大量带有单一用户帐户的企业自有的共享移动设备。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 656c93771776fd317f2b8d91bc59125fba1eb0b9
ms.openlocfilehash: 83b89d06793f6f3934537408fb600b3b89afd35b


---


# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>使用 Microsoft Intune 中的设备注册管理器注册企业自有设备
组织可以使用 Intune 来管理大量带有单一用户帐户的移动设备。 *设备注册管理器* (DEM) 帐户是可注册最多 1000 台设备的特殊 Intune 帐户。 每台已注册设备均使用单一许可证。 我们建议将通过此帐户注册的设备用作共享设备，而不是个人 ("BYOD") 设备。 例如，用户不能使用“本机”电子邮件应用。 DEM 许可是基于每个设备的，不是基于每个用户的。

例如，你可以将设备注册管理器用户帐户指定给存储管理员或主管，允许他们执行下列操作：

-   在 Intune 中注册设备。

-   登录到公司门户以获得公司应用。

-   安装和卸载软件。

-   配置对公司数据的访问权限。


**设备注册管理器方案：**一家餐厅想为服务员配备销售点平板电脑，为厨房员工配备订单监视器。 员工无需访问公司数据或以用户身份登录。 Intune 管理员创建设备注册管理器帐户并使用该帐户注册公司自有设备。 或者，管理员也可以将设备注册管理器凭据交给餐厅经理，允许经理注册和管理设备。

管理员或经理可以将特定于角色的应用部署到餐厅设备。 管理员还可以在 Intune 控制台中选择设备，并使用管理控制台从移动设备管理中将其停用。

使用设备注册管理器帐户注册的设备具有以下限制：
  - 没有特定的设备“用户” - 因此，也没有电子邮件或公司数据访问。 但是 VPN 等仍能向设备应用提供数据访问权限。
  - 无条件性访问，因为这些设备按每个用户进行注册。
  - 不可从公司门户重置设备。
  - 公司门户应用或网站中仅显示本地设备。
  - 无法使用 Apple 批量购买计划 (VPP) 应用，因为每个用户需具有 Apple ID 才可管理应用。
  - (iOS) 也不能使用 Apple Configurator 或 Apple 设备注册计划 (DEP) 进行注册，但可在无用户关联的情况下注册由 DEP 或 Apple Configurator 托管的设备。

> [!NOTE]
> 若要将公司应用部署到设备注册管理器托管的设备，请将公司门户应用作为“**必需的安装**”部署到此设备注册管理器用户帐户。
> 为提高性能，在 DEM 设备上查看公司门户应用将仅显示本地设备。 仅可通过 Intune 管理控制台执行其他 DEM 设备的远程管理。

## <a name="create-device-enrollment-manager-accounts"></a>创建设备注册管理器帐户
设备注册管理员帐户是有权限注册大量企业自有设备的用户帐户。 只有 Intune 控制台中的用户可以是设备注册管理员。

#### <a name="add-a-device-enrollment-manager-to-intune"></a>将设备注册管理员添加到 Intune

1.  转到 [Microsoft Intune 帐户门户](http://go.microsoft.com/fwlink/?LinkId=698854)并登录管理员帐户。

2.  选择“添加用户”。

3.  确认已列出将成为设备注册管理员的用户帐户。 否则，请通过选择“**新建**”和完成“**添加用户**”过程来添加用户。 访问该服务的每位用户都需要订购许可证。 设备注册管理器不能充当 Intune 管理员。 确定是否需要在使用此功能之前添加更多许可证。

4.  使用管理员凭据登录到 [Microsoft Intune 管理控制台](http://manage.microsoft.com)。

5.  在导航窗格中，选择“**管理员**”，转到“**管理员管理**”，然后选择“**设备注册管理器**”。 此时将打开**设备注册管理器**页。

6.  选择“添加…”。 打开“添加设备注册管理员”  对话框。

7.  输入 Intune 帐户的“**用户 ID**”，然后选择“**确定**”。 设备注册管理器用户不能充当 Intune 管理员。

8.  设备注册管理器现在可以使用相同的过程注册移动设备，与最终用户在公司门户中针对 BYOD 方案采用的过程相同。 管理器最终用户可以使用 DEM 凭据在多达 1000 台设备上安装公司门户应用并注册设备。

## <a name="delete-a-device-enrollment-manager-from-intune"></a>从 Intune 删除设备注册管理员

1.  使用管理员凭据登录到 [Microsoft Intune 管理门户](http://manage.microsoft.com)。

2.  在导航窗格中，选择“**管理员**”，转到“**管理员管理**”，然后选择“**设备注册管理器**”。 此时将打开**设备注册管理器**页。

3.  选择要删除的设备注册管理员“用户”，然后选择“删除”。 不会从 Intune 中删除此用户，并且此用户管理的设备仍将在 Intune 中处于注册状态。 删除设备注册管理员可防止该用户在 Intune 中注册更多设备。

4.  选择“**是**”，确认删除此设备注册管理器。

删除设备注册管理器不会影响注册的设备。 删除设备注册管理器时：

-   已注册设备均不会受到影响。

-   仍能继续完全管理已注册设备。

-   已删除的设备注册管理器帐户凭据仍有效，能够登录到公司门户来访问应用。

-   已删除的设备注册管理器帐户凭据仍无法擦除或停用设备。

-   已删除的设备注册管理器帐户与已注册设备的关系仍存在，但不可以注册任何其他设备。



<!--HONumber=Nov16_HO3-->


