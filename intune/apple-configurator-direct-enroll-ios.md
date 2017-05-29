---
title: "使用 Apple Configurator 和直接注册来注册 iOS 设备"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何通过 Apple Configurator 使用直接注册来注册公司拥有的 iOS 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 5347e2023a9ce19f8e8ab960e2eebf8107530220
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-direct-enrollment"></a>使用 Apple Configurator 和直接注册来注册 iOS 设备 

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Intune 支持注册企业所有的 iOS 设备，方法是使用在 Mac 计算机上运行的 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)。 此过程不会将设备恢复至出厂设置，并将使用预定义策略注册设备。 此方法针对“无用户关联”的设备，并且要求通过 USB 将 iOS 设备连接到 Mac 计算机以设置企业注册。

>[!NOTE]
>此注册方法不能与[设备注册管理器](device-enrollment-manager-enroll.md)方法共同使用。

直接注册 iOS 设备时，可以在无需获取设备的序列号的情况下注册设备。 在注册过程中，你还可以在 Intune 捕获设备名称前对设备命名以进行标识。 直接注册的设备不支持公司门户应用。 本指南假定你在 Mac 计算机上使用 Apple Configurator 2.0。

[选择在 Intune 中注册 iOS 设备的方式](enrollment-method-choose-ios.md)中介绍了注册 iOS 设备的其他方法。


## <a name="prerequisites"></a>先决条件

在设置 iOS 设备注册前，完成以下先决条件：

- [配置域](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [设置 MDM 机构](mdm-authority-set.md)
- [创建组](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [配置公司门户](company-portal-app.md)
- 在 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)中分配用户许可证
- [获取 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 确保具有对 iOS 设备的物理访问权限
- 获取设备序列号（请参阅[如何获取 iOS 序列号](https://support.apple.com//HT204308)）
- 准备好 USB 连接电缆
- 确保 Mac 电脑已安装 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

## <a name="create-an-apple-configurator-profile-for-devices"></a>为设备创建 Apple Configurator 配置文件

设备注册配置文件定义应用于设备组的设置。 以下步骤说明如何使用 Apple Configurator 创建已注册 iOS 设备的设备注册配置文件。

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在“Intune”边栏选项卡上，选择“注册设备”，然后选择“Apple 注册”。

3. 在“管理 Apple Configurator 注册设置”下，选择“AC 配置文件”。

4. 在“Apple Configurator 注册配置文件”边栏选项卡上，选择“创建”。

5. 在“创建注册配置文件”边栏选项卡上，输入配置文件的名称和说明。

6. 对于“用户关联”，选择“无用户关联注册”，确保该设备不与用户相关联。 将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）无法运行。

7. 选择“创建”保存该配置文件。

## <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>将配置文件作为 .mobileconfig 导出到 iOS 设备

1. 在“导出配置文件”边栏选项卡上，将注册配置文件下载到 Apple Configurator[](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)，作为管理配置文件直接推送到已连接的 iOS 设备。 此方法不会将设备恢复至出厂设置。

2. 通过以下步骤使用 Apple Configurator 准备设备。

   a. 在 Mac 计算机上，打开 Apple Configurator 2.0。

   b。 使用 USB 线将 iOS 设备连接到 Mac 计算机。 关闭“照片”、iTunes 和其他在检测设备时为设备打开的应用。

   c. 在 Apple Configurator 中，选择已连接的 iOS 设备，然后选择“添加”按钮。 可以添加到设备的选项将显示在下拉列表中。 选择“配置文件”。

   d. 使用文件选取器选择从 Intune 导出的 .mobileconfig 文件，然后选择“添加”。 配置文件将添加到设备。 如果设备是“非监督”状态，安装将需要在设备上验收。

3. 使用以下步骤在 iOS 设备上安装配置文件。 设备必须已经完成设置助理且准备好使用。 如果注册需要应用部署，设备应设置一个 Apple ID，因为应用部署将需要你有一个 Apple ID 登录到应用商店。

   a. 解锁 iOS 设备。

   b。 在“管理配置文件”的“安装配置文件”对话框中，选择“安装”。

   c. 如果需要的话，提供“设备密码”或“Apple ID”。

   d. 接受“警告”，并选择“安装”。

   e. 接受“远程警告”，并选择“信任”。

   f. “已安装配置文件”框确认配置文件“已安装”后，选择“完成”。

4. 在 iOS 设备上，打开“设置”并转到“常规” > “设备管理”  > “管理配置文件”。 确认配置文件安装已列出，并检查 iOS 策略限制和已安装的应用。 策略限制和应用可能需要 10 分钟才会出现在设备上。

5. 分配设备。 iOS 设备现已向 Intune 注册并已托管。

