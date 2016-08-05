---
title: "设置 Windows 10 移动版和 Windows Phone 管理 | Microsoft Intune"
description: "使用 Microsoft Intune 为 Windows 10 移动版或 Windows Phone 设备启用移动设备管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: cc928e4facf592ca0f7398b374242a7a07ae193e


---


# 使用 Microsoft Intune 设置 Windows Phone 和 Windows 10 移动版管理
在可以使用 Microsoft Intune 管理 Windows 10 移动版或 Windows Phone 设备之前，设备必须能够与 Intune 通信。 若要简化此操作，可以创建 DNS 记录，这样用户无需输入服务器地址。 以下步骤介绍了如何简化用户注册。  

大多数情况下，用户可以从 Windows 应用商店安装公司门户应用。 如果你管理 Windows Phone 8.0 设备或需要将公司门户部署到 Windows Phone 设备，则必须下载公司门户应用并对其进行签名。 请参阅[设置 Windows Phone 8.0 管理](set-up-windows-phone-8.0-management-with-microsoft-intune.md)。

1.  **设置 Intune** 如果你尚未设置，请将[移动设备管理机构](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)设置为**Microsoft Intune**并设置 MDM，为管理移动设备做好准备。

2.  **为注册服务器地址设置 DNS 别名** （可选）

    创建 DNS 别名（CNAME 记录类型）使用户能更轻松地注册其设备。 虽然对于 Windows 设备注册 CNAME DNS 条目是可选的，但是建议根据需要创建一个或多个记录，以使 Windows 设备注册过程中的操作变得更简单。 如果找不到任何 CNAME 记录，则系统将提示用户手动输入 MDM 服务器名称。

  1.  为公司的域创建 **CNAME** DNS 资源记录。 例如，你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 manage.microsoft.com 的 CNAME。 如果有多个已验证的域，则为每个域创建 CNAME 记录。CNAME 资源记录必须包括以下信息：

      |类型：|主机名|指向|TTL|
      |--------|-------------|-------------|-------|
      |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
      |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

      DNS 记录更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

      **EnterpriseEnrollment-s.manage.microsoft.com** – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

      **EnterpriseRegistration.windows.net** – 支持将使用其工作或学校帐户向 Azure Active Directory 注册的 Windows 8.1 和 Windows 10 移动版设备

    2.  在 [Intune 管理控制台](http://manage.microsoft.com)中，单击**管理** &gt; **移动设备管理** &gt; **Windows Phone**。

      ![设置 Windows 的移动设备管理对话框](../media/windows-device-enrollment.png)

    3.  在**指定一个已验证的域名**框中键入公司网站结果验证的域的 URL，然后单击**测试自动检测**。



无需任何额外的工作，除非你要将公司门户部署到设备。  可以安全地忽略管理控制台中的步骤 2 和 3。



<!--HONumber=Jul16_HO4-->


