---
title: 通过公司门户在 Intune 中注册 macOS 设备 | Microsoft Docs
description: 介绍如何通过公司门户应用在 Intune 中注册 macOS 设备
keywords: Mac OS X、macOS、OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 7d45ea6d2a33db2de1d640a554b6a07ad8825109
ms.sourcegitcommit: 8117444cfdddf6d9bdbc4ac715af8d88e72f411d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48260243"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>通过公司门户应用在 Intune 中注册 macOS 设备

通过 Intune 公司门户应用注册 macOS 设备，以便获取对组织的电子邮件、文件和应用的安全访问权限。

组织通常会要求先托管设备，然后才能从中访问专有数据。 托管设备后，组织可以通过移动设备管理提供程序向该设备推送策略和应用。 若要从设备持续访问工作或学校信息，必须配置设备以匹配策略设置。  

本文介绍适用于 macOS 的 Intune 公司门户应用如何帮助你注册、配置和维护设备，以满足组织需求。

## <a name="what-to-expect-from-the-company-portal-app"></a>公司门户应用的作用

初始设置期间，应用要求你向组织验证自己的身份。 然后，它将告知你必须进行的所有设备设置。 例如，组织通常会设置密码的最小或最大字符数要求，必须满足此要求。    

注册设备后，公司门户应用将继续确保设备受到保护。 例如，如果安装的应用来自于不受信任的源，应用将发出警报，且有时会撤销对公司数据的访问权限。 诸如此类的应用保护策略在组织中很常见，通常需要卸载不受信任的应用，然后才能重新获得访问权限。

如果注册后组织实施了新的安全要求（如多重身份验证），公司门户应用将对此进行通知。 可调整设置，以便可以继续通过该设备开展工作。  

若要了解有关注册的详细信息，请参阅[安装公司门户应用并注册设备后会发生什么情况？](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)。  

## <a name="get-your-device-managed"></a>托管设备  
使用以下步骤注册运行 OS X El Capitan 10.11 和更高版本的 macOS 设备。   


1. 若要访问公司门户网站，请在“Safari”中打开新窗口，并转到 https://portal.manage.microsoft.com 。  

2. 使用工作或学校帐户登录到公司门户网站。

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. 转到页面左上角，单击“菜单” > “设备”。  

4. “设备”页将显示托管设备列表或横幅。 显示的内容取决于是否已托管设备。 
    * 若要添加未列出的设备，请选择显示为“点击此处告诉我们你正在使用的设备或添加新设备”的横幅。
    * 如果没有任何设备，横幅上将显示：“没有任何托管设备。请点击此处添加设备。” 单击横幅添加设备。  

     ![“设备”页的屏幕截图，使用红色方框圈出横幅选项，以突出显示单击位置。](./media/CP-enroll-MACOS-1808.png)  
5.  完成以下步骤，该步骤与公司门户当前显示的消息匹配。  
    * 如果是第一次添加设备，系统将提示在设备上下载公司门户应用。 单击“下载”继续。  

         ![下载 macOS 公司门户应用提示屏幕的示例屏幕截图。 用户可以选择单击提示左下角的蓝色“下载”按钮，或单击右下角的灰色“取消”按钮。](./media/CP-enroll-download-macOS-1808.png)  

    * 如果已有托管的 macOS 设备，则将收到包含当前已托管 macOS 设备列表的提示。 选择“此处未列出我的设备” > “下载”，以便在添加的设备上下载公司门户应用。  

         ![下载 macOS 公司门户应用提示屏幕的示例屏幕截图。 用户可以选择“此处未列出我的设备”，或选择页面中间位置的特定设备。 提示的左下角将显示蓝色“下载”按钮，右下角将显示灰色“取消”按钮](./media/cp-mac-os-device-isnt-here-1808.png)  

6. 设备将进行检查，确认安装文件 CompanyPortal.pkg 可以安全打开。 完成后，打开安装程序并完成安装。  

7. 完成安装程序后，转到“启动板”并打开“公司门户”。  

8. macOS 设备将提示确认是否想要打开公司门户应用。 单击“打开”。  

   > [!TIP]
   > Intune 需要访问你的计算机，以确保设备足够安全以访问你组织的资源。 如果计算机拒绝打开“公司门户”应用，请[关闭 Gatekeeper](https://support.apple.com/HT202491)。 然后打开该应用。

9. 公司门户应用中显示的第一个屏幕将提示你登录。 使用用于登录到公司门户网站的同一工作或学校帐户。

10. 公司门户确认帐户信息后会显示“设备注册”和“设备符合性”状态。 黄色三角形突出显示保护学校或工作 macOS 设备需采取的操作。 单击“开始”可开始注册。 

11. 如果系统出现提示，请键入计算机的登录信息。  

在管理中注册设备可能需要几分钟时间。 在此期间，可在设备上执行其他操作。 完成公司访问设置后，将收到一条消息，通知操作已完成。  

## <a name="unverified-profiles"></a>未验证的配置文件
查看已安装的 macOS 设备移动设备管理 (MDM) 配置文件时，某些配置文件可能会显示为“未验证”状态。 只要“管理配置文件”显示为“已验证”状态，便无需担心。  

管理配置文件定义了 MDM 通道连接。 只要已验证管理配置文件，那么通过该通道传递给计算机的任何其他配置文件都会继承管理配置文件的安全特性。

此外，由于这些其他配置文件不需要单独验证，因此它们可以更快地生成并传递到设备。 

仍需帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)中查找他们的联系信息。  
