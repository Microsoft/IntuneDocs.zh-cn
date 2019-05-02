---
title: 设置 iOS 设备对公司资源的访问 | Microsoft Docs
description: 介绍如何获取 Intune 管理的 iOS 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0c7ac239a67a51ba7165771206883f3c46f5f55
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292418"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>设置 iOS 设备对公司资源的访问  

通过 Intune 公司门户应用注册 iOS 设备，以便获取对组织的电子邮件、文件和应用的安全访问权限。

已注册设备后，它将成为*托管*。 你的组织可以通过移动设备管理 (MDM) 提供程序，例如 Intune 向设备分配策略和应用。  

若要持续拥有从设备访问工作或学校信息的权限，必须配置设备以匹配组织的首选设置。 本文介绍如何使用公司门户注册设备和维护组织的设置要求。 

> [!NOTE]
> 如果想要在邮件应用中访问公司电子邮件，但收到托管设备的提示，那么通过本文你将了解如何解决该问题。 按照下面的说明，获取对 iOS 设备上的电子邮件和其他公司资源的访问权限。  

## <a name="what-to-expect-from-the-company-portal-app"></a>公司门户应用的作用  

### <a name="security"></a>安全  
初始设置期间，应用要求你向组织验证自己的身份。 然后，它将告知你必须更新的所有设备设置。 例如，组织通常会设置密码的最小或最大字符数要求，必须满足此要求。     

### <a name="protection"></a>保护  
注册设备后，公司门户应用将继续确保设备受到保护。 例如，如果安装的应用来自于不受信任的源，应用将发出警报，且有时会撤销对公司数据的访问权限。 这种策略在组织中很常见，通常要求你先卸载不受信任的应用，然后可以重新获得访问权限。  

### <a name="setting-notifications"></a>设置通知  
如果注册后组织强制使用新的安全要求（如多重身份验证），公司门户应用将对此作出通知。 可调整设置，以便可以继续通过该设备开展工作。  

要了解有关注册的详细信息，请参阅[安装公司门户应用并注册设备后会发生什么情况？](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)。  

## <a name="enroll-your-ios-device"></a>注册 iOS 设备  

转到应用商店，下载并安装[Intune 公司门户应用](install-and-sign-in-to-the-intune-company-portal-app-ios.md)在设备上。 此外需要维护的 Wi-fi 连接，并在注册过程有权访问 Safari。 

暂停超过几分钟后，在注册过程中可能会导致应用程序关闭或结束安装程序。 如果发生这种情况，请打开公司门户应用，然后重试。  

1. 打开公司门户并使用工作或学校帐户登录。 

    ![公司门户应用，登录的示例屏幕截图。](./media/ios-01-cp-enroll-1903.PNG)  

2. 当提示你接收公司门户通知，点击**允许。** 公司门户使用通知来向您发出警报，例如，需要更新你的设备设置。 

    ![公司门户主页上，"通知"提示符的示例屏幕截图。](./media/ios-04-cp-enroll-1903.PNG)  

3. 上**设置的访问权限**屏幕上，选择**开始。**  

     ![示例的公司门户中，"设置访问权限"屏幕的屏幕截图。](./media/ios-05-cp-enroll-1903.PNG)  

4. 读完你的组织可以看到和不能看到的设备信息的列表。 然后点击**继续**。  

5. 通过说明上读取**什么是下一步？** 屏幕。 当已准备好下载并安装管理配置文件，请点击**继续**。  

 > [!IMPORTANT]
> 这些下一步的步骤和屏幕将根据你的 iOS 版本不同。 按照你的 iOS 版本的步骤。 

6. Safari 打开你的设备上的公司门户网站。 当提示你下载的配置文件，点击**允许**。 如果您运行的设备上：  
    * iOS 12.2 及更高版本： 在下载完成后，点击**完成。** 继续执行本文中的步骤 7。
    * 12.1 及更早版本的 iOS： 你将自动定向到设置应用。 请跳到步骤 8 中这篇文章。  
 
    如果意外地点击**忽略**，刷新页面。 系统会提示打开公司门户应用。 从应用程序中，你可以点击**再次下载**。

  > [!NOTE]
  > 必须安装管理配置文件中所述的下一步骤中下载它的 8 分钟。 如果不这样做，将删除的配置文件，并且您将需要重新启动注册。  

7. 12.2 及更高版本的 iOS： 当系统提示你打开公司门户，请点击**打开**。 **安装管理配置文件**屏幕列出了安装配置文件的步骤。

    ![示例的公司门户中，安装管理配置文件屏幕的屏幕截图。](./media/ios-1904-settings-icon.PNG)  

8. 转到设置应用并点击**配置文件下载**。  

    如果**下载配置文件**不会显示为一个选项，请转到**常规** > **配置文件**。 如果仍看不到配置文件，您可能需要再次下载。  

    ![示例屏幕截图中的设置应用，设置下载配置文件。](./media/ios-1904-settings-badge.PNG)  

9. 点击“安装”。  
    
10. 更改设备密码 然后点击**安装**。    

    ![设置应用程序安装配置文件屏幕上，使用的游标的示例屏幕截图 * * 安装 * * 按钮。](./media/ios-1904-password-install.PNG)  


11. 下一个屏幕是设备管理的标准系统警告。 若要继续安装，请点击**安装**。 如果系统提示信任远程管理，请点击**信任**。  

    ![示例的设置应用程序，用于根证书和移动设备管理的标准系统警告屏幕的屏幕截图。](./media/ios-15-cp-enroll-1903.PNG)  

12. 安装完成后，点击**完成**。 若要验证是否已安装的配置文件，请转到**配置文件和设备管理**设置。 应会看到下列出的配置文件**移动设备管理**。   

    ![示例屏幕截图中的配置文件和设备管理设置应用程序设置，从而显示管理配置文件。](./media/ios-00-cp-enroll-1903.PNG)  

13. 返回到“公司门户”应用。 公司门户将开始同步，并设置你的设备。 公司门户可能会提示你更新其他设备设置。 如果存在，请点击**继续**。  

    ![公司门户"设置访问权限"屏幕，要求设置旁边的黄色三角形中的示例屏幕截图。](./media/ios-12-cp-enroll-1903.PNG)  

14. 你将了解在列表中的所有项都显示一个绿色圆圈时完成该安装程序。 点击“完成”。   
    
    ![示例屏幕截图中的公司门户，"准备好了 ！" 屏幕，其中显示所有的绿色圆圈。](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> 如果你的组织监视语音和数据限制，或者你提供公司拥有的设备，可能有几个步骤才能完成。 如果系统会提示你安装**Datalert**应用，请参阅[注册你的设备在电信费用管理中](enroll-your-device-with-telecom-expense-management-ios.md)。 如果你的组织是 Apple 的设备注册计划的一部分，找出[如何注册公司自有设备](enroll-your-device-dep-ios.md)。  

## <a name="next-steps"></a>后续步骤  
查找帮助您在工作或学校的应用。 了解[如何应用都可用](use-managed-apps-on-your-device-ios.md)给你通过公司门户。  

仍需帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)中查找他们的联系信息。  
