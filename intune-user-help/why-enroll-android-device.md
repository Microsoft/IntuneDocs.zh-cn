---
title: 为何注册 Android 设备
description: 了解在 Intune 中注册设备很重要的原因
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: db9ff1b6f707a6d978d8499f3e82af2d1a04f355
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857496"
---
# <a name="why-enroll-your-android-device"></a>为何注册 Android 设备  

学校和雇主希望确保使用安全、受信任的设备来访问内部资源。 在访问这些资源时，公司门户和 Microsoft Intune 应用将保护 Android 设备和数据的安全。 无论你在何处或使用哪种设备，它们都确保你能够安全地访问资源。 

如果你的组织要求你使用其中一个应用进行安装和注册，则需要执行此操作，然后才能从你的设备访问公司资源。 本文介绍将设备注册到这些应用的目的和优点。  

## <a name="gets-your-device-managed"></a>帮助托管设备  
 公司门户和 Microsoft Intune 应用在 Intune 中注册设备。  Intune 是一种移动设备管理提供程序，可帮助你的组织通过安全和设备策略来管理移动设备和应用。 

这些应用会引导你完成每个注册步骤，并配置设备设置以匹配组织的策略。 它们还会提醒你需要解决的问题或设置，才能获得企业访问权限。  

组织可能需要的策略示例包括：  
* 设置密码或 PIN
* 超过设定登录尝试的次数后限制访问
* 确保未使用越狱或取得 root 权限的设备
* 安装工作所需的应用  

## <a name="gives-you-access-to-work-and-school-apps-work-files-and-email"></a>提供工作和学校应用、工作文件和电子邮件的访问权限  
在注册期间，公司门户和 Microsoft Intune 应用要求你连接到你的工作或学校帐户。  进行身份验证后，在将设备设置配置为符合组织的策略后，你将获得对你的组织的电子邮件帐户、网络、文件和应用的访问权限。  

组织有时会要求安装工作或安全应用，例如 Microsoft Office 或 Mobile Threat Defense。 如果这些应用程序是必需的或可供您使用，则可以在公司门户或 Microsoft Intune 应用程序中找到它们。

## <a name="lets-you-remotely-reset-a-lost-or-stolen-device-if-device-supports-it"></a>可远程重置丢失或被盗的设备（如果设备支持）
如果设备丢失或被盗，则可以在任何其他设备上登录公司门户应用或公司门户网站，并将手机重置为出厂设置。 如果丢失的设备包含不希望任何其他人访问的专有工作数据，则此功能很有用。 由于设备已在管理中注册，因此公司支持人员或 IT 管理员也可帮助对其进行重置。  

"重置" 功能在 Microsoft Intune 应用中不可用。  

## <a name="notifies-you-of-policy-updates-and-requirements"></a>通知策略更新和要求
公司门户或 Microsoft Intune 应用将每隔8小时自动签入或同步 Intune。 如果你正在使用公司门户并且想要更频繁地签入，你或你的公司支持人员可以启动手动同步。在签入期间，应用将执行以下操作：  

* 下载公司支持人员提供的任何策略或应用更新。  
* 发送硬件清单更新。 这些更新不包含个人信息。  
* 发送公司应用清单更新。 这些更新不包含个人信息。  

如果设备不同步或不再满足要求，则其状态将显示为 "*不符合*"。 对工作和学校相关资源的访问权限可能因此取消，直到设备再次满足要求。 公司门户应用会通知你这些问题以及解决这些问题所需采取的步骤。  


## <a name="permits-company-support-access-to-your-device"></a>允许公司支持访问设备
注册设备时，出于有限且有意义的目的，公司支持人员或 IT 管理员可以访问该设备。 最终用户可：  

* 将设备重置回制造商的默认设置。 如上所述，还可以重置设备。 但是，如果无法立即访问公司门户应用，公司可代为重置设备。  

* 删除公司相关的所有数据。 如果你离开公司或者设备变成未托管，则组织可能会从设备中删除与公司相关的数据。 个人数据和设置不会删除，并将保留在设备上。  

* 对设备设置要求，例如要求拥有设备密码或 PIN。 在这种情况下，将收到设备不符合要求的应用通知。 公司支持人员还可能会限制在设备上输入错误密码的次数。 密码尝试失败次数过多可能导致设备被锁定。  

* 要求你接受条款和条件。  

* 禁用摄像头。 此策略的目的是防止拍摄专有信息，并消除学校环境中的干扰。 学校可能会禁用教室设备上的摄像头，这样学生就不能共享测试材料。  

* 要求设备上所有数据都加密。 如果丢失或被盗，此策略有助于保护设备上的数据。 该策略还可以保护设备或应用之间共享的数据。 

## <a name="next-steps"></a>后续步骤  

需要帮助吗? 请联系公司支持人员（访问[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)获取联系信息），或写邮件给 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble installing the Company Portal app on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 团队</a>。
