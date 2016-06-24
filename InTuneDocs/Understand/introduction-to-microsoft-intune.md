---
# required metadata

title: Microsoft Intune 简介 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Intune 简介
Microsoft Intune 是 Microsoft 企业移动性套件 (EMS) 的“管理部分”。 企业移动性就是使员工可以在其所有设备上高效工作，同时保护组织的信息。  

EMS 是针对企业移动性的完整集成套件，包括工作效率、标识、访问控制、管理和数据保护。 它为你提供了在组织中部署和运行移动性解决方案的最佳可能方式。  

![企业移动性愿景图](..\media\em-vision.png)

Intune 使你能够管理移动设备和移动应用。 它与 Azure Active Directory (AD) 紧密集成以实现标识和访问控制，并与 Azure 权限管理 (RMS) 集成以实现数据保护。  

Intune 可帮助解决的一些常见业务问题包括：

* 保护本地电子邮件和协作基础结构，以便可以由移动设备和应用通过 Internet 进行访问
* 保护 Office 365 基础结构，以便可以由移动设备和应用通过 Internet 进行安全访问
* 使组织可以向其员工颁发移动电话
* 使组织可以为任务工作人员提供使用受限的“共享设备”
* 使组织可以实现安全的“自带设备办公 (BYOD)”或个人设备策略
* 使组织可以支持员工从不受控制的设备和应用（如贸易展览大厅中的展台）访问 Office 365

Intune 提供的一些主要工具包括：
* **移动设备管理 (MDM)**：能够将设备注册到 Intune 中，以便你可以对这些设备进行设置、配置、监视和执行操作（如擦除它们）。
* **移动应用程序管理 (MAM)**：为用户发布、推送、配置、保护、监视和更新移动应用的能力。
* **移动应用程序安全性**：作为管理移动应用的一部分，Intune 通过从公司数据隔离个人数据，并允许选择性擦除公司数据来提供帮助保护移动数据的能力

在不同组合中使用这些工具以启用上述常见方案。 例如，共享设备方案大量使用 MDM。 BYOD 方案通常依赖于 MAM。 而企业电话方案两者都依赖。 几乎所有方案都要用到移动应用安全性。

在本文档中，我们将介绍如何使用 Intune 提供的工具支持你的业务方案。  我们将介绍如何将 Office 365、Azure AD、Azure RMS 和 Microsoft 移动性套件的其他部分与这些工具配合使用。 这将有助于为你提供该技术的常规使用方法纵览，以及它在你的环境以及实施它们的步骤中如何才能有所帮助。 技术本身非常灵活，并且可适用于各种类型的方案，不仅仅局限于我们在此处介绍的。

### 后续步骤
* 了解一些 [Intune 的常见使用方式](common-ways-to-use-intune.md)
* 通过 [Intune 的 30 天试用版](get-started-with-a-30-day-trial-of-microsoft-intune.md)熟悉该产品
* 深入了解 Intune 的[技术要求和功能](/intune/get-started/what-to-know-before-you-start-microsoft-intune)


<!--HONumber=May16_HO2-->


