---
title: 向 Intune 公司门户注册 Mac |Microsoft Docs
description: 了解如何通过公司门户应用在 Intune 中注册你的 Mac。
keywords: Mac OS X、macOS、OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: e04950a67938d883b0762c03efa371fcb74d0731
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855470"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>使用公司门户应用注册 macOS 设备  

通过 Intune 公司门户应用注册 macOS 设备，以便获取对工作或学校电子邮件、文件和应用的安全访问权限。

组织通常要求先注册设备，然后才能访问专用数据。 注册设备后，它将成为托管设备  。 组织可通过移动设备管理 (MDM) 提供程序（如 Intune）为该设备分配策略和应用。 若要在设备上持续访问工作或学校信息，必须配置设备以匹配组织的策略设置。  

本文介绍如何使用 macOS 的公司门户应用来注册、配置和维护设备，以满足组织需求。  


## <a name="what-to-expect-from-the-company-portal-app"></a>公司门户应用的作用

初始设置期间，公司门户应用需要你登录并向你的组织进行身份验证。 然后公司门户会通知你需要配置的任何设备设置，以满足组织的要求。 例如，组织通常会设置密码的最小或最大字符数要求，必须满足此要求。    

注册设备后，公司门户将始终确保你的设备符合组织的要求。 例如，如果从不受信任的源安装应用程序，公司门户会提醒你，并可能会限制对组织资源的访问权限。 此类应用保护策略非常常见。 若要重新获得访问权限，可能需要卸载不受信任的应用。 

如果注册后组织实施了新的安全要求（如多重身份验证），公司门户将对此进行通知。 可调整设置，以便可以继续通过该设备开展工作。  

要了解有关注册的详细信息，请参阅[安装公司门户应用并注册设备后会发生什么情况？](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)。  

## <a name="get-your-macos-device-managed"></a>管理 macOS 设备  
使用以下步骤将 macOS 设备注册到组织。 设备必须运行 macOS 10.12 或更高版本。   

> [!NOTE]
> 在此过程中，系统可能会提示你允许公司门户使用存储在密钥链中的机密信息。 这些提示是 Apple security 的组成部分。 收到提示时，键入登录密钥链密码，并选择 "**始终允许**"。 如果按**enter**键或在键盘上**返回**，则提示将改为选中 "**允许**"，这可能会导致其他提示。  

### <a name="install-company-portal-app"></a>安装公司门户应用  
1. 请参阅["注册我的 Mac"](https://go.microsoft.com/fwlink/?linkid=853070)。  
2. 将下载公司门户 .pkg 文件。 打开安装程序，并继续执行这些步骤。 
3. 同意软件许可协议。 
4. 输入设备密码或已注册的指纹以安装软件。  
5. 打开公司门户。 

> [!IMPORTANT]
> Microsoft 自动更新可能会打开以更新你的 Microsoft 软件。 安装所有更新之后，打开公司门户应用。 若要获得最佳安装体验，请安装最新版本的 Microsoft 自动更新和公司门户。  


### <a name="enroll-your-mac"></a>注册 Mac  


1. 用你的工作单位或学校帐户登录到公司门户。  
2. 当应用程序打开时，请选择 "**开始**"。  
3. 查看你的组织可以在你的已注册设备上看不到的内容。 然后，选择“继续”  。
4.  如果系统提示，请在 "**安装管理配置文件**" 屏幕上输入设备密码。

    ![公司门户，安装管理配置文件屏幕，突出显示密码提示的示例屏幕截图。](./media/install-management-profile-macos-1912.PNG)   
5. 在 "**确认设备管理**" 屏幕上，选择 "**打开系统首选项**"。  

    ![确认设备管理屏幕的示例屏幕截图，突出显示 "打开系统首选项" 按钮。](./media/confirm-device-management-macos-1912.PNG)  
6. 设备的系统首选项将打开。 从 "设备配置文件" 列表中选择 "**管理配置文件**"，然后选择 "**批准** > **批准**"。  
    ![系统首选项、管理配置文件屏幕的示例屏幕截图，突出显示 "批准" 按钮。](./media/management-profile-approve-macos-1912.PNG)   
1. 返回公司门户，然后选择 "**继续**"。    
2. 你的组织可能要求你更新设备设置。 完成更新设置后，选择 "**检查设置**"。  

    ![公司门户，更新设备设置屏幕的示例屏幕截图，突出显示 "检查设置" 按钮。](./media/update-settings-mac-1911.PNG)  
9. 安装完成后，选择 "**完成**"。  


 ## <a name="troubleshooting-and-feedback"></a>故障排除和反馈   

如果在注册过程中遇到问题，请参阅**帮助** > **发送诊断报告**，将问题报告给 Microsoft 应用开发人员。 此信息用于帮助改善应用。 如果 IT 支持人员对其进行帮助，他们还将使用此信息来帮助解决问题。  

向 Microsoft 报告问题之后，你可以将你的体验的详细信息发送给你的 IT 支持人员。 选择 "**电子邮件详细信息**"。 在电子邮件正文中键入经验。 若要查找支持人员的电子邮件地址，请访问公司门户应用 > "**联系**"。 或查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。  
 

此外，Microsoft Intune 公司门户团队需要倾听你的反馈意见。 请参阅 "**帮助**" > **发送反馈**，分享你的想法和观点。  

## <a name="unverified-profiles"></a>未验证的配置文件  
在“系统首选项”   > “配置文件”  中查看已安装的移动设备管理 (MDM) 配置文件时，某些配置文件可能会显示为“未验证”状态。 只要“管理配置文件”显示为“已验证”状态，便无需担心。  

管理配置文件定义了 MDM 通道连接。 只要已验证管理配置文件，那么通过该通道传递给计算机的任何其他配置文件都会继承管理配置文件的安全特性。  

## <a name="updating-the-company-portal-app"></a>更新公司门户应用

与更新任何其他 Office 应用相同，更新公司门户应用也通过 Microsoft AutoUpdate for macOS 完成。 了解有关[更新适用于 macOS 的 Microsoft 应用](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1)的详细信息。  

## <a name="next-steps"></a>后续步骤  
仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。  


