---
title: 使用托管设备完成工作 | Microsoft Docs
description: 了解将设备注册到 Intune 管理的意义。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883873"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>注册设备以便访问工作或学校资源
若要注册设备并获取电子邮件和应用的访问权限, 需要安装 Intune 公司门户应用或 Microsoft Intune 应用。 注册时, 你的组织配置的基本管理策略 (如密码、PIN 和加密) 将应用于你的设备。 一旦你的设备设置满足组织的所有要求, 你就可以从几乎任何位置安全地访问你的工作信息。  

公司门户和 Microsoft Intune 应用通过确保你的设备设置符合组织的策略来确保你的已注册设备的安全。 

此外，公司门户应用还能：  
* 将个人信息和工作信息分开。  
* 可以轻松地查找和安装相关的工作和学校应用。   

## <a name="get-the-apps"></a>获取应用
若要获取公司门户，请执行以下操作：

- 从特定于平台的应用商店安装公司门户应用。 在某些情况下, 你的组织将为你安装公司门户应用。  
- 请访问[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980), 通过浏览器访问应用程序。  

如果需要使用 Microsoft Intune 应用程序, 你的组织将为你安装它。  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>当我注册时，我的公司可以看到什么信息？
注册设备后, 组织的支持人员只能看到与工作相关的信息。 无法查看你的个人信息。 如果你要注册一台个人设备以在工作中使用, 请[确切了解可以和不能看到的内容](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>应用与网站有何区别？
公司门户应用适用于 Windows 10、iOS、macOS 和 Android 设备。 它与设备的相应平台无缝集成。 网站版本可以从任意设备访问，无论你使用何种设备，都会为你提供相同的通用体验。 

Microsoft Intune 应用适用于公司拥有的 Android 设备。  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>公司门户可以注册哪种类型的设备？
- 使用 iOS（例如 iPhone 和 iPad）和 macOS（例如 MacBook 和 iMac）的 Apple 设备
- Android 设备
- Windows 设备
  - Windows 10 移动版
  - Windows 10 桌面版
  - Windows Phone 8.1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Microsoft Intune 应用可以注册哪种类型的设备？  
你可以注册组织已设置为用于应用的企业拥有的 Android 设备。 应用支持 Android 6.0 及更高版本。 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>是否可从公司门户中删除计算机或设备？
可以从公司门户中删除或重置计算机或设备。 **删除**和**重置**有所不同。

如果从公司门户中删除计算机或设备，也会从 Intune 取消注册设备。 一旦取消注册，你将无法再从该设备访问公司门户，并且可能会从设备中删除某些公司数据。 若要了解如何从公司门户删除设备, 请参阅以下链接:  

- [取消注册 Android 设备](unenroll-your-device-from-intune-android.md)
- [取消注册 iOS 设备](unenroll-your-device-from-intune-ios.md)
- [取消注册 macOS 设备](unenroll-your-device-from-intune-macos.md)
- [取消注册 Windows 设备](unenroll-your-device-from-intune-windows.md)

如果你重置计算机或设备，公司门户会尝试将计算机或设备重置回制造商默认设置。 重置设备会从设备中删除所有公司数据和个人数据。 如果设备丢失，还可以在公司门户网站中远程重置。  

若要了解如何重置设备, 请参阅[从公司门户网站重置设备](reset-erase-your-device-cpwebsite.md)。  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>是否可以从 Microsoft Intune 应用中删除计算机或设备？
不能, 无法从 Microsoft Intune 应用中删除企业拥有的设备。  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>如果在公司门户或 Microsoft Intune 应用程序中看不到我的设备该怎么办？
若要能够看到设备，必须先将它添加到公司门户。 转到管理员建议的公司门户，并遵循设备的相关步骤。 你也无法查看你公司所拥有和管理的设备。

如果使用的是 Microsoft Intune 应用程序, 则只能看到当前正在使用的设备。 在应用中, 其他已注册的设备将不会显示。  

## <a name="where-else-can-i-go-for-help"></a>可以从其他哪些地方获取帮助？  
若要排查常见问题和问题, 请查看以下特定于平台的文档:  

- [解决 Android 设备的常见问题](check-compliance-on-your-device-android.md)  
- [解决 iOS 设备的常见问题](troubleshoot-your-device-ios.md)
- [解决 macOS 设备的常见问题](troubleshoot-your-device-macos.md)
- [解决 Windows 设备的常见问题](troubleshoot-your-device-windows.md)

你还可以联系支持人员。 公司门户和 Microsoft Intune 应用提供了帮助和支持页面, 其中列出了联系信息和报告问题的方式。 你的组织的[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)上也提供联系信息。  

## <a name="next-steps"></a>后续步骤  

从注册 (特定于设备的平台) 获取帮助:  

- [使用 Android 设备](using-your-android-device-with-intune.md)
- [使用 iOS 设备](using-your-ios-device-with-intune.md)
- [使用 macOS 设备](using-your-macos-device-with-intune.md)
- [使用 Windows 设备](using-your-windows-device-with-intune.md)
- [使用公司门户网站](using-the-intune-company-portal-website.md)


