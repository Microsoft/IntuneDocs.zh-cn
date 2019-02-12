---
title: 如果安装适用于 Android 的公司门户应用会发生什么情况
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d8af8b01de3b9782f487e29a9f993ceaf32aac6
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838149"
---
# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-android-device-in-intune"></a>安装公司门户应用并在 Intune 中注册 Android 设备后会发生什么情况？

如果组织要求在 Android 设备上安装 Intune 公司门户应用，你也许想了解原因。 本文介绍了应用的用途和功能 &mdash; 以及该应用如何保护在设备上访问和存储的工作和学校数据。

## <a name="gets-your-device-managed"></a>帮助托管设备
公司门户应用有助于在组织的设备管理系统中托管（也称为“注册”）设备。 连接到组织的网络前，学校或工作区需要确保你拥有安全可信任的设备。 若要访问工作或学校资源，设备需要遵循组织的设备策略。 

公司支持人员或 IT 管理员在其公司范围内的设备管理系统中配置这些策略。 注册设备后，便可收到这些策略。 

组织可能需要的某些策略示例包括：
* 设置密码或 PIN
* 超过设定登录尝试的次数后限制访问
* 确保未使用越狱或取得 root 权限的设备
* 安装工作所需的应用

公司门户应用将逐步引导你完成注册，并将配置设备设置以满足组织的要求。 在某些情况下，应用将询问或通知你进行更改。

## <a name="gives-you-access-to-work-and-school-apps-work-files-and-email"></a>提供工作和学校应用、工作文件和电子邮件的访问权限
在注册期间，公司门户应用需要连接到工作或学校帐户。 通过身份验证后，便可以访问工作电子邮件以及组织的网络、文件和应用。 

组织有时会要求安装工作或安全应用，例如 Microsoft Office 或 Mobile Threat Defense。 如果这些应用是必需的或可供使用，则可在公司门户应用中进行查找。

## <a name="lets-you-remotely-reset-a-lost-or-stolen-device-if-device-supports-it"></a>可远程重置丢失或被盗的设备（如果设备支持）
如果设备丢失或被盗，则可以在任何其他设备上登录公司门户应用或公司门户网站，并将手机重置为出厂设置。 如果丢失的设备包含不希望任何其他人访问的专有工作数据，则此功能很有用。 由于设备已在管理中注册，因此公司支持人员或 IT 管理员也可帮助对其进行重置。  

## <a name="notifies-you-of-policy-updates-and-requirements"></a>通知策略更新和要求
公司门户应用将每 8 小时与组织的移动设备管理提供商进行签入或同步。 如果希望更频繁地签入，你或公司支持人员可启动手动同步。在签入期间，应用将执行以下操作：  
* 下载公司支持人员提供的任何策略或应用更新。  
* 发送硬件清单更新。 这些更新不包含个人信息。  
* 发送公司应用清单更新。 这些更新不包含个人信息。  

如果设备与组织的要求不同步，公司门户应用会进行通知。 该应用会告知你问题以及解决问题所需的步骤。 对工作和学校相关资源的访问权限可能因此取消，直到设备再次满足要求。 在公司门户应用中，此状态称为“不符合”。 

## <a name="permits-company-support-access-to-your-device"></a>允许公司支持访问设备
在公司门户应用中注册设备时，出于有限且有意义的目的，公司支持人员或 IT 管理员可以访问该设备。 最终用户可：  

* 将设备重置回制造商的默认设置。 如上所述，还可以重置设备。 但是，如果无法立即访问公司门户应用，公司可代为重置设备。  

* 删除公司相关的所有数据。 如果你离开公司或者设备变成未托管，则组织可能会从设备中删除与公司相关的数据。 个人数据和设置不会删除，并将保留在设备上。  

* 对设备设置要求，例如要求拥有设备密码或 PIN。 在这种情况下，将收到设备不符合要求的应用通知。 公司支持人员还可能会限制在设备上输入错误密码的次数。 密码尝试失败次数过多可能导致设备被锁定。  

* 要求你接受条款和条件。  

* 禁用摄像头。 此策略的目的是防止拍摄专有信息，并消除学校环境中的干扰。 学校可能会禁用教室设备上的摄像头，这样学生就不能共享测试材料。  

* 要求设备上所有数据都加密。 如果丢失或被盗，此策略有助于保护设备上的数据。 该策略还可以保护设备或应用之间共享的数据。  

需要帮助吗? 请联系公司支持人员（访问[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)获取联系信息），或写邮件给 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble installing the Company Portal app on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 团队</a>。
