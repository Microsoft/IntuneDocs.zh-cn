---
title: "使用 Microsoft Intune 设置 Windows 设备管理 | Microsoft Intune"
description: "使用 Microsoft Intune 为 Windows 电脑（包括 Windows 10 设备）启用移动设备管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: 79377078bf5b4c6dad0a3dc4a07a2e84aa2563f8


---

# 设置 Windows 设备管理
利用 Intune，可以为 Windows 电脑设备注册启用 BYOD（“自带设备办公”），以允许访问公司电子邮件和应用。 与 Azure Active Directory 一起使用，还可以以快速、无触控的方式将新的 Windows 10 设备纳入管理并获取访问公司资源的权限，而无需重置计算机的映像。 注册后，用户可以进行登录并使用 Intune 管理控制台向其设备应用策略、应用和设置。 你可能还需要通过 Intune 客户端[使用 Microsoft Intune 设置 Windows Phone 管理](set-up-windows-phone-management-with-microsoft-intune.md)或[使用 Intune 客户端软件管理计算机](manage-windows-pcs-with-microsoft-intune.md)。

创建 DNS CNAME 可帮助用户进行连接 Intune 并在其中进行注册，而无需输入服务器名称。

### 设置 Windows 设备管理

  1.  为公司的域创建 **CNAME** DNS 资源记录。 例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollment-s.manage.microsoft.com 的 CNAME。 虽然对于 Windows 设备注册 CNAME DNS 条目是可选的，但是建议根据需要创建一个或多个记录，以使 Windows 设备注册过程中的操作变得更简单。 如果找不到任何 CNAME 记录，则系统将提示用户手动输入 MDM 服务器名称。

  如果存在多个经过验证的域，则为每个域创建一个 CNAME 记录。 CNAME 资源记录必须包含以下信息：

  |类型：|主机名|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

  DNS 记录更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

  **EnterpriseEnrollment-s.manage.microsoft.com** – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

  **EnterpriseRegistration.windows.net** – 支持将使用其工作或学校帐户向 Azure Active Directory 注册的 Windows 8.1 和 Windows 10 移动版设备

  2.  在 [Intune 管理控制台](http://manage.microsoft.com)中，单击“管理”&gt;“移动设备管理”&gt;“Windows”。
  ![Windows 设备管理对话框](../media/enroll-intune-winenr.png)
  3.  在**指定一个已验证的域名**框中键入公司网站结果验证的域的 URL，然后单击**测试自动检测**。

### 另请参阅
[为在 Microsoft Intune 中注册设备做好准备](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


