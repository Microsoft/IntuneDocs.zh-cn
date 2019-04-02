---
title: 设置 iOS 设备对公司资源的访问 | Microsoft Docs
description: 介绍如何获取 Intune 管理的 iOS 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: ee0f438d929abd6b5b90acbaeeddc41e3ce11f98
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490636"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>设置 iOS 设备对公司资源的访问  

通过 Intune 公司门户应用注册 iOS 设备，以便获取对组织的电子邮件、文件和应用的安全访问权限。

必须先托管企业或个人设备，随后才能从该设备访问专有数据。 设备进入托管状态后，组织将通过移动设备管理 (MDM) 提供程序（如 Intune）为该设备分配策略和应用。 

若要持续拥有从设备访问工作或学校信息的权限，必须配置设备以匹配组织的首选设置。 本文介绍如何使用公司门户注册设备和维护组织的设置要求。 

> [!NOTE]
> 如果想要在邮件应用中访问公司电子邮件，但收到托管设备的提示，那么通过本文你将了解如何解决该问题。 按照下面的说明，获取对 iOS 设备上的电子邮件和其他公司资源的访问权限。  

## <a name="what-to-expect-from-the-company-portal-app"></a>公司门户应用的作用  

### <a name="security"></a>安全  
初始设置期间，应用要求你向组织验证自己的身份。 然后，它将告知你必须更新的所有设备设置。 例如，组织通常会设置密码的最小或最大字符数要求，必须满足此要求。     

### <a name="protection"></a>保护  
注册设备后，公司门户应用将继续确保设备受到保护。 例如，如果安装的应用来自于不受信任的源，应用将发出警报，且有时会撤销对公司数据的访问权限。 此类策略通常在组织中，并通常要求你先卸载不受信任的应用，然后可以重新获得访问权限。  

### <a name="setting-notifications"></a>设置通知  
如果注册后组织强制使用新的安全要求（如多重身份验证），公司门户应用将对此作出通知。 可调整设置，以便可以继续通过该设备开展工作。  

要了解有关注册的详细信息，请参阅[安装公司门户应用并注册设备后会发生什么情况？](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)。  

## <a name="enroll-your-ios-device"></a>注册 iOS 设备   

> [!IMPORTANT]
> 在本部分中屏幕截图显示正在运行 iOS 版本 12.1 及更早版本的设备的体验。 如果适用，我们提供了特定于 iOS 版本 12.2 及更高版本的说明。 如果您注意到你的体验，与不同的屏幕截图所示，请参阅 12.2 说明。      

转到应用商店，下载并安装[Intune 公司门户应用](install-and-sign-in-to-the-intune-company-portal-app-ios.md)向你的设备。 注册期间，您还需要一个 Wi-fi 连接并能访问到 Safari。 

如果暂停超过几分钟后，在注册过程中，应用程序可能会关闭或结束安装程序。 如果发生这种情况，请打开公司门户应用，然后重试。  

1. 打开公司门户并使用工作或学校帐户登录。 

    ![公司门户应用，登录的示例屏幕截图。](./media/ios-01-cp-enroll-1903.PNG)  

2. 当提示你接收公司门户通知，点击**允许。** 公司门户使用通知来向您发出警报，例如，需要更新你的设备设置。 

    ![公司门户主页上，"通知"提示符的示例屏幕截图。](./media/ios-04-cp-enroll-1903.PNG)  

3. 上**设置的访问权限**屏幕上，选择**开始。**  

     ![示例的公司门户中，"设置访问权限"屏幕的屏幕截图。](./media/ios-05-cp-enroll-1903.PNG)  

4. 读完你的组织可以看到和不能看到的设备信息的列表。 [本主题的更多详情](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md)可以通过找到**了解详细信息**链接。 完成后，点击**继续**。  

    ![示例屏幕截图中的公司门户应用"可以看到哪些内容我的组织"，使用继续按钮。](./media/ios-06-cp-enroll-1903.PNG)  
 
5. **什么是下一步？** 屏幕总结了的剩余步骤。 这些步骤可能不同，具体取决于你的 iOS 版本。 
    * **12.2 及更高版本的 iOS**： 你的体验可能会改为要求您为：  

        a. **允许管理配置文件的下载**： 你的浏览器将打开公司门户网站，并提示您允许下载。 将设置应用程序中保存下载。  

        b. **打开设置应用并将配置文件安装**： 你将需要转到设置应用并安装管理配置文件。  

        c. **返回到公司门户应用**： 你将需要返回到公司门户应用以完成安装。  

    如果你已准备好下载管理配置文件，请点击**继续**。  

6. Safari 打开公司门户网站。 当提示你下载的配置文件，点击**允许**。  
    * **12.2 及更高版本的 iOS**： 等待配置文件来完成下载 Safari 然后点击**完成**。 然后在设备上打开“设置”应用。  

    > [!IMPORTANT]
    > 你必须转到**设置**应用并将其下载 8 分钟内安装此配置文件。 如果不这样做，将删除的配置文件，并且您将需要重新启动注册。 

7. 在中**设置**应用，点击**安装下载配置文件** > **安装**。 如果**安装下载配置文件**不会显示为一个选项，请转到**常规** > **配置文件**。 如果仍看不到配置文件，您可能需要再次下载。  

    ![示例屏幕截图中的设置应用中，安装下载配置文件设置下，该值指示最近下载的配置文件旁边的红色标记。](./media/ios-10-cp-enroll-1903.PNG)  
    
8. 如果系统提示，请输入你的设备密码。 然后点击**安装**。      

9. 下一个屏幕是设备管理的标准系统警告。 若要了解有关你的组织可以和不能在设备上看到的内容的详细信息，请参阅相关[Intune docs 文章](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md)。 若要继续安装，请点击**安装**。 如果系统提示信任远程管理，请点击**信任**。  

    ![示例的设置应用程序，用于根证书和移动设备管理的标准系统警告屏幕的屏幕截图。](./media/ios-15-cp-enroll-1903.PNG)  

10. 安装完成后，点击**完成**。 若要验证是否已安装的配置文件，请转到**配置文件和设备管理**设置。 应会看到下列出的配置文件**移动设备管理**。   

    ![示例屏幕截图中的配置文件和设备管理设置应用程序设置，从而显示管理配置文件。](./media/ios-00-cp-enroll-1903.PNG)  


11. 返回到“公司门户”应用。 公司门户将开始同步，并设置你的设备。 公司门户可能会提示你更新其他设备设置。 如果存在，请点击**继续**。

    ![公司门户"设置访问权限"屏幕，要求设置旁边的黄色三角形中的示例屏幕截图。](./media/ios-12-cp-enroll-1903.PNG)  

12. 你将了解在列表中的所有项都显示一个绿色圆圈时完成该安装程序。 点击“完成”。  
    
    ![示例屏幕截图中的公司门户，"准备好了 ！" 屏幕，其中显示所有的绿色圆圈。](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> 如果你的组织监视语音和数据限制，或者你提供公司拥有的设备，可能有几个步骤才能完成。 如果系统会提示你安装**Datalert**应用，请参阅[注册你的设备在电信费用管理中](enroll-your-device-with-telecom-expense-management-ios.md)。 如果你的组织是 Apple 的设备注册计划的一部分，找出[如何注册公司自有设备](enroll-your-device-dep-ios.md)。  

## <a name="next-steps"></a>后续步骤  
查找帮助您在工作或学校的应用。 了解[如何应用都可用](use-managed-apps-on-your-device-ios.md)给你通过公司门户。  

仍需帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)中查找他们的联系信息。  
