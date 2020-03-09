---
title: 设置 iOS 设备对公司资源的访问 | Microsoft Docs
description: 介绍如何获取 Intune 管理的 iOS 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 92d1ca850d8bb542f0b7fe027ab7af8c12089ef8
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181749"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>设置 iOS 设备对公司资源的访问  

通过 Intune 公司门户应用注册 iOS 设备，以便获取对组织的电子邮件、文件和应用的安全访问权限。

注册设备后，它将成为托管设备  。 组织可通过移动设备管理 (MDM) 提供程序（如 Intune）为该设备分配策略和应用。  

> [!NOTE]
> 我们不会出于任何原因向任何第三方出售我们服务收集的任何数据。  

若要持续拥有从设备访问工作或学校信息的权限，则需要配置设备以匹配组织的首选设置。 本文介绍如何使用公司门户注册设备并维护组织的设置要求。  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> 如果想要在邮件应用中访问公司电子邮件，但收到托管设备的提示，那么通过本文你将了解如何解决该问题。 按照下面的说明，获取对 iOS 设备上的电子邮件和其他公司资源的访问权限。  


## <a name="what-to-expect-from-the-company-portal-app"></a>公司门户应用的作用  

### <a name="security"></a>安全  
初始设置期间，应用要求你向组织验证自己的身份。 然后，它将告知你必须更新的所有设备设置。 例如，组织通常会设置密码的最小或最大字符数要求，必须满足此要求。

### <a name="protection"></a>保护  
注册设备后，公司门户应用将继续确保设备受到保护。 例如，如果安装的应用来自于不受信任的源，应用将发出警报，且有时会撤销对公司数据的访问权限。 此类策略在组织中很常见，通常需要卸载不受信任的应用，然后才能重新获得访问权限。  

### <a name="setting-notifications"></a>设置通知  
如果注册后组织强制使用新的安全要求（如多重身份验证），公司门户应用将对此作出通知。 可调整设置，以便可以继续通过该设备开展工作。  

要了解有关注册的详细信息，请参阅[安装公司门户应用并注册设备后会发生什么情况？](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)。  

## <a name="enroll-your-ios-device"></a>注册 iOS 设备  

转到 App Store 下载并在设备上安装 [Intune 公司门户应用](install-and-sign-in-to-the-intune-company-portal-app-ios.md)。 还需要维护 Wi-Fi 连接，并可以在注册期间访问 Safari。 

如果在注册期间暂停超过几分钟，可能会导致应用关闭或设置结束。 如果发生这种情况，请打开公司门户应用，然后重试。  

1. 打开公司门户并使用工作或学校帐户登录。  

2. 当系统提示接收公司门户通知时，请点击“允许”  。 例如，如果需要更新设备设置，公司门户会使用通知来提醒你。  

3. 在“设置访问权限”屏幕上，选择“开始”   。   

    ![公司门户的示例屏幕截图，“设置访问权限”屏幕。](./media/ios-enrollment-checklist-1909.PNG)  

4. 随即将显示“选择设备和注册类型”屏幕，并提示输入设备类型  。  
    * 如果收到了来自组织的设备，请点击“(组织)拥有此设备”  。 然后跳到本文中的[保护整个设备](#secure-entire-device)以完成设置。  
    * 如果你使用的是从家里带来的个人设备，请点击“我拥有此设备”  。 然后继续执行下一步。  

    如果看不到此屏幕，请跳到[保护整个设备](#secure-entire-device)以完成设置。  
    
    ![公司门户的示例屏幕截图，“选择设备和注册类型”屏幕，设备类型选项。](./media/ios-device-type-1909.PNG)  


5. 选择注册设备后如何保护设备上的数据。  
    * 点击“保护整个设备”  ，以保护设备上的所有应用和数据。 然后转到[保护整个设备](enroll-your-device-in-intune-ios.md#secure-entire-device)以完成设置。
    * 点击“仅保护与工作相关的应用和数据”  ，以仅保护使用工作帐户访问的应用和数据。 然后转到[保护与工作相关的应用和数据](enroll-your-device-in-intune-ios.md#secure-work-related-apps-and-data)。  

    ![公司门户的示例屏幕截图，“选择设备和注册类型”屏幕，注册类型选项。](./media/ios-enrollment-type-1909.PNG)  


### <a name="secure-entire-device"></a>保护整个设备  

1. 在“设备管理和隐私”屏幕上，仔细阅读组织可以查看和无法查看的设备信息列表  。 然后点击“继续”  。  


 > [!IMPORTANT]
> 这些后续步骤和屏幕将因 iOS 版本而异。 按照你的 iOS 版本的步骤进行操作。 

2. Safari 在设备上打开公司门户网站。 当系统提示下载配置文件时，请点击“允许”  。 如果你的设备运行的是：  
    * iOS 12.2 及更高版本：下载完成后，点击“完成”  。 然后继续执行步骤 3。  
    * iOS 12.1 及更低版本：下载完成后，你将被自动重定向到“设置”应用。 跳到步骤 4。  
 
    如果不小心点击“忽略”，请刷新页面  。 系统会提示打开公司门户应用。 完成后，点击“再次下载”  。

  > [!NOTE]
  > 必须在下载后的 8 分钟内按照后续步骤中的说明安装管理配置文件。 如果不这样做，配置文件将被删除，必须重新开始注册。  

3. 当系统提示打开公司门户时，请点击“打开”  。 仔细阅读“如何安装管理配置文件”屏幕上的信息  。  

4. 转到“设置”应用，然后点击“注册 <组织名称>”或“下载的配置文件”   。  

    ![“设置”应用的示例屏幕截图，“注册组织”选项。](./media/enroll-in-organization-ios-1909.PNG)  

   如果这两个选项均未出现，请转到“常规” > “配置文件和设备管理”> “管理配置文件”    。 如果仍没有看到管理配置文件，则可能需要再次下载。  

5. 点击“安装”  。  
    
6. 输入设备密码。 然后点击“安装”  。    

7. 下一个屏幕是有关设备管理的标准系统警告。 若要继续安装，请点击“安装”  。 如果系统提示信任远程管理，请点击“信任”  。  

8. 安装完成后，点击“完成”  。 若要验证配置文件是否已安装，请转到“配置文件和设备管理”设置  。 应该会在“移动设备管理”下看到此配置文件  。   

    ![Settings 应用的示例屏幕截图，“配置文件和设备管理”设置，其中显示管理配置文件。](./media/ios-12-cp-enroll-1904.PNG)  

9. 返回到 Company Portal 应用。 Company Portal 将开始同步和设置你的设备。 Company Portal 可能会提示更新其他设备设置。 如果是这样，请点击“继续”  。  

10. 当列表中的所有项都显示绿色复选标记时，表明设置已完成。 点击“完成”  。   

> [!Note]
> 如果组织监视语音和数据限制，或者为你提供公司拥有的设备，则可能还需要完成一些步骤。 如果系统提示安装 Datalert 应用，请参阅[在电信费用管理中注册设备](enroll-your-device-with-telecom-expense-management-ios.md)  。 如果组织参加了 Apple 的设备注册计划，请了解[如何注册公司拥有的设备](enroll-your-device-dep-ios.md)。  

### <a name="secure-work-related-apps-and-data"></a>保护与工作相关的应用和数据  
1. 随即将显示“下载 Microsoft Authenticator”屏幕（如果已安装有 Authenticator，则看不到此屏幕，请跳到步骤 2）  。  
    1. 点击“从 App Store 下载”  。
    2. App Store 打开后，安装该应用。 
    3. 返回到公司门户并点击“继续”  。    
    
   安装 Microsoft Authenticator 后，不需要对该应用执行任何其他操作。 只需确保设备上显示该应用即可。 

   ![公司门户的示例屏幕截图，“下载 Microsoft Authenticator”屏幕。](./media/download-ms-authenticator-1909.PNG)  

2. 在“设备管理和隐私”屏幕上，仔细阅读组织可以查看和无法查看的设备信息列表  。 然后点击“继续”  。  


 > [!IMPORTANT]
> 这些后续步骤和屏幕将因 iOS 版本而异。 按照你的 iOS 版本的步骤进行操作。 

3. Safari 在设备上打开公司门户网站。 当系统提示下载配置文件时，请点击“允许”  。 如果你的设备运行的是：  
    * iOS 12.2 及更高版本：下载完成后，点击“完成”  。 然后继续执行步骤 4。  
    * iOS 12.1 及更低版本：下载完成后，你将被自动重定向到“设置”应用。 跳到步骤 5。  
 
    如果不小心点击“忽略”，请刷新页面  。 系统会提示打开公司门户应用。 在应用中，可点击“再次下载”  。

  > [!NOTE]
  > 必须在下载后的 8 分钟内按照后续步骤中的说明安装管理配置文件。 如果不这样做，配置文件将被删除，必须重新开始注册。  

4. 当系统提示打开公司门户时，请点击“打开”  。 仔细阅读“如何安装管理配置文件”屏幕上的信息  。 

5. 转到“设置”应用，然后点击“注册 <组织名称>”或“下载的配置文件”   。  

    ![“设置”应用的示例屏幕截图，“注册组织”选项。](./media/enroll-in-organization-ios-1909.PNG)  

   如果这两个选项均未出现，请转到“常规” > “配置文件和设备管理”> “管理配置文件”    。 如果仍没有看到管理配置文件，则可能需要再次下载。   


6. 在“用户注册”屏幕上，点击“注册我的 iPhone”   。  

    ![“设置”应用的示例屏幕截图，“用户注册”屏幕，其中突出显示了注册按钮。](./media/user-enrollment-information-1909.PNG)  

7. 输入设备密码。 然后点击“安装”  。  

8. 在“登录”屏幕上，请输入托管 Apple ID 的密码  。 在大多数情况下，除非你的组织为你提供了一组不同的凭据，否则这些凭据将与用于登录工作帐户或学校帐户的凭据相同。 
9. 点击“登录”  。  
10. 安装配置文件后，屏幕上将短暂地显示一条成功消息。 若要验证配置文件是否已安装，请转到“配置文件和设备管理”设置 ****  。 应该会在“移动设备管理”下看到此配置文件 **** 。  

    ![Settings 应用的示例屏幕截图，“配置文件和设备管理”设置，其中显示管理配置文件。](./media/ios-12-cp-enroll-1904.PNG)  

11. 返回到 Company Portal 应用。 Company Portal 将开始同步和设置你的设备。 Company Portal 可能会提示更新其他设备设置。 如果是这样，请点击“继续”  。    

12. 当列表中的所有项都显示绿色复选标记时，表明设置已完成。 点击“完成” **** 。  

## <a name="it-administrator-support"></a>IT 管理员支持  
如果你是 IT 管理员且在注册设备时遇到问题，请参阅 [Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/en-us/help/4039809)（Microsoft Intune 中的 iOS 设备注册问题疑难解答）。 本文列出了常见错误、错误原因及其解决方法步骤。  

## <a name="next-steps"></a>后续步骤  
找到可在工作或学校方面对你有帮助的应用。 通过 Company Portal 了解[应用的提供方式](use-managed-apps-on-your-device-ios.md)。  

仍需帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)中查找他们的联系信息。  
