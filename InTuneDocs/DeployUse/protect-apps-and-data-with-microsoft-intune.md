---
# required metadata

title: 保护应用和数据 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 保护应用和数据


Intune 通过多个技术层保护公司数据。  在标识层上，条件性访问通过仅允许从托管及合规设备进行访问来保护对服务的访问。  在客户端应用程序层上，移动应用管理 (MAM) 通过防止将数据移动到未受保护的应用或存储位置以及在设备丢失或被盗时擦除数据来防止数据丢失。  应结合使用这两个保护层，以在保持移动办公人员效率的同时保护数据。

保护公司数据的重要第一步就是通过确保用于访问该数据的设备使用的是强密码、加密等安全性保护且未越狱，从而实现条件性访问。 Microsoft Intune 使你能在允许设备访问公司电子邮件和数据之前，设置其必须遵守的条件。

[条件性访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)由可在 Intune 中设置的两种类型的策略决定：
- [合规性策略](introduction-to-device-compliance-policies-in-microsoft-intune.md)确定设备的合规性。 它们评估以下设置和条件：
  - PIN 和密码：可以创建以下规则：必须提供密码才可解锁设备、设定密码的复杂性和其他密码设置。
  - 加密：你可以限制对加密设备的访问。
  - 设备未越狱或取得 root 权限：Intune 可以检测注册的设备是否已越狱，而你可以设置策略来阻止此类设备上的访问。
- [条件性访问策略](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)专为 Exchange Online 或 SharePoint Online 等特定服务配置。 对于每个服务，你可以定义这些策略应该应用到哪些用户组。 例如，你可以确保财务部门的每个人只能从注册的合规设备访问公司电子邮件。

保护对公司资源的访问只是保护公司数据的第一步。 一旦它已在设备上访问该数据，你仍需要具备保护数据的能力。 现在可以将数据复制、移动、保存到其他位置，或进行共享。 Intune 通过创建以下规则组来向你提供限制数据移动的能力，从而解决此问题：
- 阻止复制和粘贴，或防止工作环境外的数据传输。
- 防止将数据备份到个人云存储空间，阻止另存为功能。
- 要求 PIN/密码或企业凭据，保障应用访问安全。
- 在 Intune 托管浏览器中打开所有 Web 链接。

这些规则组被称为[移动应用管理 (MAM) 策略](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。  可以将 MAM 策略应用到在不一定由你托管的设备上运行的应用。  可以针对已在 Intune 中注册的设备、由其他第三方 MDM 注册或托管的设备，或者可能不由你托管的设备（例如员工拥有的设备）使用 MAM 策略来保护公司数据。

若要将应用与 MAM 策略相关联，该应用必须包含 Microsoft Intune 应用软件开发工具包 (SDK)，或使用应用包装工具。

与 Microsoft Office 应用类似的应用内置了 App SDK。 可在 Microsoft Intune 应用程序合作伙伴页上的 [Microsoft Intune 移动应用程序库](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)中找到支持的应用完整列表。 选择应用可查看支持的方案、平台以及应用是否支持多身份。

还可以[启用自定义构建的业务线应用](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)以与 MAM 策略配合使用。

如果设备丢失或被盗，或者用户不再与你公司合作，除了限制数据移动之外，还可以[选择性擦除公司数据](wipe-managed-company-app-data-with-microsoft-intune.md)，仅保留个人数据。


<!--HONumber=Jun16_HO2-->


