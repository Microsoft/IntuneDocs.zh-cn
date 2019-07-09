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
ms.openlocfilehash: 2c0d3484311d044842daf6718b306d45fc93edf2
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545926"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>注册设备的工作或学校资源的访问权限
若要注册设备并获取对电子邮件和应用程序的访问权限，你将需要安装 Intune 公司门户应用或 Microsoft Intune 应用。 注册时，你的组织已配置，如密码、 PIN 和加密，基本的管理策略应用到你的设备。 一旦你的设备设置符合所有组织的要求，可以从几乎任何位置安全访问你的工作信息。  

公司门户和 Microsoft Intune 应用保护你注册的设备通过确保你的设备设置的与组织的策略匹配。 

此外，公司门户应用还能：  
* 将你的个人和工作信息分开。  
* 轻松查找和安装相关工作和学校的应用。   

## <a name="get-the-apps"></a>获取应用
若要获取公司门户，请执行以下操作：

- 从特定于平台的应用商店安装公司门户应用。 在某些情况下，你的组织将为你安装公司门户应用。  
- 转到[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)从浏览器访问该应用。  

如果您需要使用 Microsoft Intune 应用，你的组织将安装它为您。  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>当我注册时，我的公司可以看到什么信息？
已注册设备后，你组织的支持人员只能看到与工作相关的信息。 无法查看你的个人信息。 如果要注册个人设备以便工作时，使用[了解究竟是什么可以和不能看到](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>应用与网站有何区别？
公司门户应用已可用于 Windows 10、 iOS、 macOS 和 Android 设备。 无缝集成你的设备的各自的平台。 网站版本可以从任意设备访问，无论你使用何种设备，都会为你提供相同的通用体验。 

Microsoft Intune 应用是公司拥有的 Android 设备。  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>使用公司门户可以注册的设备类型？
- 使用 iOS（例如 iPhone 和 iPad）和 macOS（例如 MacBook 和 iMac）的 Apple 设备
- Android 设备
- Windows 设备
    - Windows 10 移动版
    - Windows 10 桌面版
    - Windows Phone 8.1
    - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>您可以使用 Microsoft Intune 应用注册何种设备？  
你可以注册公司拥有的 Android 设备，你的组织已设置为使用与该应用程序。 应用程序支持 Android 6.0 及更高版本。 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>是否可从公司门户中删除计算机或设备？
可以从公司门户中删除或重置计算机或设备。 **删除**和**重置**有所不同。

如果从公司门户中删除计算机或设备，也会从 Intune 取消注册设备。 一旦取消注册，你将无法再从该设备访问公司门户，并且可能会从设备中删除某些公司数据。 若要了解如何从公司门户删除设备，请参阅以下链接：  

- [取消注册 Android 设备](unenroll-your-device-from-intune-android.md)
- [取消注册 iOS 设备](unenroll-your-device-from-intune-ios.md)
- [取消注册 macOS 设备](unenroll-your-device-from-intune-macos.md)
- [取消注册 Windows 设备](unenroll-your-device-from-intune-windows.md)

如果你重置计算机或设备，公司门户会尝试将计算机或设备重置回制造商默认设置。 重置设备会从设备中删除所有公司数据和个人数据。 如果设备丢失，还可以在公司门户网站中远程重置。  

若要了解如何重置你的设备，请参阅[将设备从公司门户网站重置](reset-erase-your-device-cpwebsite.md)。  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>可以删除计算机或设备从 Microsoft Intune 应用？
否，没有任何方法，以便从 Microsoft Intune 应用中删除企业拥有的设备。  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>如果看不到我的公司门户或 Microsoft Intune 应用中的设备？
若要能够看到设备，必须先将它添加到公司门户。 转到管理员建议的公司门户，并遵循设备的相关步骤。 你也无法查看你公司所拥有和管理的设备。

如果您使用 Microsoft Intune 应用程序，则只能看到当前正在使用的设备。 其他已注册的设备不会对你的应用中可见。  

## <a name="where-else-can-i-go-for-help"></a>可以从其他哪些地方获取帮助？  
若要解决常见的问题和疑问，请查看这些特定于平台的文档：  

- [解决 Android 设备的常见问题](check-compliance-on-your-device-android.md)  
- [解决 iOS 设备的常见问题](troubleshoot-your-device-ios.md)
- [解决 macOS 设备的常见问题](troubleshoot-your-device-macos.md)
- [解决 Windows 设备的常见问题](troubleshoot-your-device-windows.md)

您可以还联系支持人员。 公司门户和 Microsoft Intune 应用程序提供帮助和支持列出的联系人信息以及如何报告问题的页面。 联系信息，还可以在你的组织[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。  

## <a name="next-steps"></a>后续步骤  

获取开始注册到你的设备的平台特定的帮助：  

- [使用 Android 设备](using-your-android-device-with-intune.md)
- [使用 iOS 设备](using-your-ios-device-with-intune.md)
- [使用 macOS 设备](using-your-macos-device-with-intune.md)
- [使用 Windows 设备](using-your-windows-device-with-intune.md)
- [使用公司门户网站](using-the-intune-company-portal-website.md)


