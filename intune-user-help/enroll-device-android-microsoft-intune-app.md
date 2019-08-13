---
title: 使用 Microsoft Intune 应用注册公司设备 | Microsoft Docs
description: 介绍如何在 Intune 中注册公司 Android 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/07/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ef7ec650c65206eeab69d8f666dc4fb39052bbdb
ms.sourcegitcommit: 549352bdea93cc2809e3e0010bfcc10bd44dc728
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68862203"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>使用 Microsoft Intune 应用注册公司设备

注册公司拥有的 Android 设备，以安全访问组织提供的公司电子邮件、应用和其他数据。 Microsoft Intune 应用支持运行 Android 6.0 及更高版本的公司拥有的设备。 该应用将在注册期间自动在新设备和恢复出厂设置设备上进行安装。 

有四种方法可以进行注册。 组织应告诉你要使用的选项。
 
* 近场通信 (NFC)  
* Token  
* QR 码   
* Google Zero Touch  

## <a name="enroll-device"></a>注册设备 
完成这些步骤即可设置和注册设备。  

> [!NOTE]
> Android 版本或设备制造商可能会要求你完成此过程中未涵盖的其他步骤。 屏幕截图中显示的颜色和文字因设备而异。  

1. 打开新的或恢复出厂设置设备。  
2. 在“欢迎使用”屏幕上，选择语言  。   如果系统指示使用 QR 码或 NFC 注册，请按照与该方法匹配的以下步骤操作。  
     * NFC：针对程序员设备点击 NFC 支持的设备，以连接到组织的网络。 按照屏幕上的提示操作。 访问 Chrome 的服务条款屏幕时，请继续执行步骤 5。  

     * QR 码：完成 [QR 码注册](#qr-code-enrollment)中的步骤。  

     如果系统指示使用其他方法，请继续执行步骤 3。    

3. 连接 Wi-Fi，然后点击“下一步”  。 按照与注册方法匹配的步骤操作。 

    * 令牌：转到 Google 登录屏幕后，完成[令牌注册](#token-enrollment)中的步骤。  
    * Google Zero Touch：连接到 Wi-Fi 后，组织会识别你的设备。 继续执行步骤 4 并按照屏幕上的提示进行操作，直到设置完成。    
 
       ![Google 条款屏幕的示例图像，如果使用的是 Google Zero Touch，其中会突出显示“接受并继续”按钮。](./media/google-zero-touch-intune-app-01.png)   
   
4. 查看 Google 的条款。 然后点击“接受并继续”  。  

      ![Google 条款屏幕的示例图像，其中突出显示“接受并继续”按钮。](./media/fully-managed-intune-app-04.png)   

6. 查看 Chrome 的服务条款。 然后点击“接受并继续”  。  

   ![Chrome 服务条款屏幕的示例图像，其中突出显示“接受并继续”按钮。](./media/fully-managed-intune-app-06.png)   

7. 在登录屏幕上，请使用工作或学校帐户登录。   

    a. 输入电子邮件，然后点击“下一步”  。      
    b. 输入密码，然后点击“登录”  。  

8. 根据组织的要求，系统可能会提示更新设置（如锁屏或加密）。 如果看到这些提示，请点击“设置”并按照屏幕上的说明进行操作  。  

   ![“设置工作电话”屏幕的示例图像，其中突出显示“设置”按钮。](./media/fully-managed-intune-app-10.png)   

9. 若要在设备上安装工作应用，请点击“安装”  。 安装完成后，点击“下一步”  。  

   ![“设置工作电话”屏幕的示例图像，其中突出显示“安装”按钮。](./media/fully-managed-intune-app-11.png)   

10. 点击 **"** 开始" 打开 Microsoft Intune 应用并注册设备。 

    ![“设置工作电话”屏幕的示例图像，其中突出显示了“开始”按钮。](./media/fully-managed-intune-app-17.png)   

11. 点击 **"登录** ", 然后**点击** "下一步" 开始注册。 当你看到注册已完成的消息时, 点击 **"** 完成"。  

    ![示例图像: 设置访问权限, 注册设备屏幕, 突出显示 "完成" 按钮。](./media/fully-managed-intune-app-19.png)   

10. 收到设备准备就绪的消息后，点击“完成”  。  

    ![“设置工作电话”屏幕的示例图像，其中突出显示了“完成”按钮。](./media/fully-managed-intune-app-18.png)   

如果在访问组织的资源时遇到问题, 可能需要更新设备上的其他设置。 登录到 Microsoft Intune 应用以检查所需的更新。   


## <a name="qr-code-enrollment"></a>QR 码设备注册  
在本节中，将扫描公司提供的 QR 码。  完成后，你将重定向回设备注册步骤。     
  
1. 在“欢迎”屏幕上，点击屏幕五次，才能启动 QR 码安装  。  

   ![设备安装“欢迎”屏幕的示例图像，其中突出显示点击屏幕的说明。](./media/qr-code-intune-app-01.png)  

2. 按照屏幕上的任何说明连接到 Wi-Fi。  
3. 如果设备没有安装 QR 码扫描仪，安装屏幕将显示安装扫描仪时的进程。 等待安装完成。  
4. 系统出现提示时，扫描组织提供的注册配置文件 QR 码。  
5. 返回步骤 4 [注册设备](#enroll-device)，继续执行安装。  

## <a name="token-enrollment"></a>令牌注册  
在本节中，输入公司提供的令牌。 完成后，你将重定向回设备注册步骤。  

1. 在 Google 登录屏幕上，在“电子邮件或电话”框中，键入“afw#setup”   。 点击“下一步”  。 

   ![“Google 登录”屏幕的示例图像，其中显示键入到字段中的“afw#setup”。](./media/token-intune-app-01.png)   

2. 为“Android 设备策略”应用选择“安装”   。 继续完成安装。 可能需要查看并接受其他条款，具体取决于你的设备。    

3. 在“注册此设备”屏幕上，选择“下一步”   。  

4. 选择“输入条形码”  。  

5. 在“扫描或输入条形码”屏幕上，键入组织提供的条形码  。  然后单击 **“下一步”** 。  

   ![“扫描或输入条形码”屏幕的示例图像，其中突出显示“下一步”按钮。](./media/token-intune-app-04.png)  

6. 返回步骤 4 [注册设备](#enroll-device)，继续执行安装。  



## <a name="next-steps"></a>后续步骤   
仍需帮助？ 请联系公司支持人员（访问[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)获取联系信息），或写邮件给 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 团队</a>。  
