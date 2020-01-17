---
title: 在移动设备上安装 Mobile Threat Defense
description: 了解如何在移动设备上安装 Mobile Threat Defense。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 6b75712cf05626999c09e8d74fd28252666313c4
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857868"
---
# <a name="install-mobile-threat-defense"></a>安装 Mobile Threat Defense   

作为组织安全要求的一部分，你可能需要安装移动威胁防御（MTD）供应商应用。 此类应用可检测并提醒你设备上的威胁，例如可疑应用、网络或操作系统漏洞。  

如果没有所需的 MTD 应用，会阻止你使用工作或学校帐户登录到受保护的应用。 在本文中，你将了解[如何安装 MTD 应用程序](set-up-mobile-threat-defense.md#install-app)以取消阻止。  

有多种可供安装的 MTD 供应商应用;你的组织将通知你使用哪一个。 


## <a name="information-your-organization-can-see"></a>你的组织可查看的信息   

你的组织在个人应用中看不到任何数据，如文本、电子邮件和图片。 MTD 应用会将有关你的应用的信息（如名称和版本）报告给你的组织。 报告的实际信息取决于公司使用的 MTD 供应商。 你的组织可能会看到：   

* 应用名称  
* 应用 ID：在 Google Play 中标识应用的唯一名称。  
* 应用版本和短版本号：应用的特定发行版号。  
* 应用程序包和动态大小：应用在设备中使用的空间大小。 


## <a name="install-app"></a>安装应用    
当你登录到受保护的应用时，系统会自动提示你安装 MTD 应用。 按照屏幕上的步骤完成安装。 使用本部分中的步骤获取更多帮助。  
 
系统可能还会提示你注册设备。 注册需要确认身份，并将你的学校或工作帐户连接到你的设备。 如果未注册，则在安装 MTD 应用之前，会自动指导您完成该设置。 转到 "**获取访问权限**" 屏幕时，可以启动安装步骤。  

有关设备注册的详细信息，请参阅[在组织的网络上注册您的个人设备](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)。  

### <a name="ios-setup"></a>iOS 安装程序  

1. 在 "**获取访问权限**" 屏幕上，按照说明安装组织所需的 MTD 应用。   
2. 返回到 "**获取访问权限**" 屏幕并选择 "**打开**"。  
3. MTD 应用要求打开 Microsoft Authenticator 的权限。 选择“打开”  。 
4. 选择工作帐户进行登录。 
5. 等待 MTD 应用扫描设备的安全威胁。 
6. 返回到你最初尝试访问的学校或工作应用。 此时，你的组织可能会提示你配置其他应用安全要求，例如创建 PIN。   
7. 现在应可以访问应用。 如果仍被阻止：  
    * 在 "**获取访问权限**" 屏幕上，选择 "重新**检查**"。  
    * 中转到 MTD 应用并检查现有的威胁。 完成解决威胁并重新获得访问权限的建议步骤。    

### <a name="android-setup"></a>Android 安装程序 

1. 在 "**获取访问权限**" 屏幕上，按照说明安装组织所需的 MTD 应用。  
2. 返回到 "**获取访问权限**" 屏幕并选择 "**打开**"。  
3. MTD 应用要求你有权访问设备的特定区域（如果需要）。 为了使此应用程序正常工作，您必须**允许**访问联系人。 请求的权限将因 MTD 供应商而异。  
4. 选择工作帐户进行登录。  
5. 等待 MTD 应用扫描设备的安全威胁。  
6. 返回到你最初尝试访问的学校或工作应用。 此时，你的组织可能会提示你配置其他应用安全要求，例如创建 PIN。  
7. 现在应可以访问应用。 如果仍被阻止：  
    * 在 "**获取访问权限**" 屏幕上，选择 "重新**检查**"。  
    * 中转到 MTD 应用并检查现有的威胁。 完成解决威胁并重新获得访问权限的建议步骤。  

### <a name="installation-failed"></a>安装失败  

如果安装失败，请与 IT 支持人员联系。 请转到[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)，查找组织的联系人信息。  

你还可以将应用程序日志发送给你的 IT 支持人员，为他们提供有关安装的更多上下文。  
* Android 用户：从公司门户[上传和发送日志](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。   

* iOS 设备用户：从适用于 iOS 的 Microsoft Edge[检索并发送日志](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs)。  

## <a name="resolve-a-threat"></a>解决威胁  
如果威胁超出组织定义的威胁级别，你的组织可以：  
   
* 阻止访问：阻止你在登录到你的工作或学校帐户时使用组织的受保护应用。  
* 擦除数据：从组织的一个或多个受保护的应用中删除工作或学校数据。  

若要解决威胁并重新获得访问权限，请在设备上打开 MTD 应用。 通读提供的信息，了解威胁可能会如何影响设备以及如何解决问题。 在按照这些步骤进行操作以解决威胁后，返回到 MTD 应用并启动新扫描。 重新获得对你的组织的访问权限可能需要几分钟的时间。  

## <a name="next-steps"></a>后续步骤  

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。

