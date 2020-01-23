---
title: 在管理中注册组织提供的 iOS 设备 | Microsoft Docs
description: 了解如何在 Intune 中注册由组织购买和提供的 iOS 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 6c1b6417489d1443596113a18476b9cbc8f3832e
ms.sourcegitcommit: 8cc3eca2bce847b0c2b40d8531698e21df848878
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75951459"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>在管理中注册组织提供的 iOS 设备

了解如何在 Intune 中管理新的 iOS 设备。  

工作单位或学校提供的 iOS 设备通常会在分配前进行预配置。 首次打开并登录设备后，组织会将预配置的设置发送到设备。 设备完成设置后，将获得工作单位或学校资源的访问权限。  

要开始设置，请打开设备电源并使用工作单位或学校凭据登录。 本文的其余部分介绍使用“设置助理”过程中将看到的步骤和屏幕。

## <a name="what-is-apple-dep"></a>什么是 Apple DEP？

组织可以通过“Apple 设备注册计划”(DEP) 购买设备  。 组织可通过 Apple DEP 购买大量的 iOS 或 macOS 设备。 然后，组织可以在其首选的移动设备管理提供程序（例如 Intune）中配置和管理这些设备。 如果你是管理员并想了解有关 Apple DEP 的详细信息，请参阅[使用 Apple 设备注册计划自动注册 iOS 设备](/intune/enrollment/device-enrollment-program-enroll-ios)。

## <a name="set-up-your-ios-device"></a>设置 iOS 设备

如果使用的是自己的 iOS 设备，而不是组织提供的设备，请按照[个人设备和自带设备](enroll-your-device-in-intune-ios.md)步骤进行操作。  

1. 打开 iOS 设备。
2. 选择“语言”后，请将设备连接 Wi-Fi  。
3. 在“设置 iOS 设备”屏幕上，选择“设置为新设备”   。  
4. 连接 Wi-Fi 后，随即显示“配置”屏幕  。 它会显示“[你的公司] 将自动配置你的设备”  。

   **配置允许 [你的公司] 无线管理此设备。管理员可以帮助你设置电子邮件和网络帐户、安装和配置应用以及远程管理设置。管理员可能禁用功能、安装和删除应用、监视和限制 Internet 流量以及远程擦除此设备。**

   配置提供者：[贵公司的] iOS 团队 [地址] 

5. 使用 Apple ID 登录。 登录后，可安装公司门户应用，并能够安装管理配置文件，让公司允许你访问其资源，如电子邮件和应用。
6. 同意“条款和条件”，并决定是否将诊断信息发送给 Apple  。
7. 完成注册后，设备可能会提示你需要执行更多操作。 其中某些步骤可能是输入用于电子邮件访问的密码或设置一个密码。

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
