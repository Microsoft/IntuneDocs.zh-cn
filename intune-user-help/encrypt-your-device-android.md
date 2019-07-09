---
title: 适用于 Intune 加密 Android 设备 |Microsoft Docs
description: 打开 Android 设备加密时所需的 Intune 的步骤
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545257"
---
# <a name="encrypting-your-android-device"></a>加密 Android 设备

设备加密可保护文件和文件夹从未经授权的访问丢失或被盗设备。 启用设备加密后，只有个人与正确的密码或 pin 将能够登录到你的设备。 

在可以访问学校或工作资源之前，你的组织可能要求你加密你的 Android 设备。 默认情况下，某些较新的 Android 设备进行加密的框。  

## <a name="turn-on-encryption"></a>启用加密

如果公司门户或 Microsoft Intune 应用提示你加密你的设备，请完成以下步骤。 

> [!Note]
> 华为、 Vivo 和 oppo 生产从某些 Android 设备不能进行加密。 请单击[此处](your-device-appears-encrypted-but-cp-says-otherwise-android.md)，查看详细信息。  

1. 设置设备屏幕锁。  
    a. 转到“设置”   > “锁定屏幕和安全性”   > “屏幕锁定类型”  。  
    b. 选择任一**PIN**，**密码**，或**模式**。  
    c. 按照屏幕上的说明配置屏幕锁。  

2. 返回到**锁定屏幕和安全**，然后选择**安全启动**。
3. 选择**要求输入 pin 码时设备将启用** > **确定**。
4. 输入你的 PIN 以确认并加密你的设备。
5. 打开公司门户或 Microsoft Intune 应用。
    * 公司门户用户：选择设备，并点击“检查设备设置”  。 
    * Microsoft Intune 用户： 必须在页面更新之前要等待，但您的加密状态时，应更改为符合。  

运行 Android 4.4 及更早版本的设备可能没有**安全启动**选项。 在这种情况下，完成以下步骤来加密你的设备。

1. 转到**设置** > **安全** > **加密设备**。 在屏幕上的标签而异的 Android 设备。 如果没有看到**加密设备**选项，请签入：
    * **存储** > **存储加密**
    * **存储** > **锁定屏幕和安全** > **其他安全设置** 

2. 按照屏幕上的说明操作。 在加密期间，设备可以重启几次。
3. 打开公司门户或 Microsoft Intune 应用。
    * 公司门户用户：选择设备，并点击“检查设备设置”  。  
    * Microsoft Intune 用户： 必须在页面更新之前要等待，但您的加密状态时，应更改为符合。

## <a name="troubleshoot"></a>故障排除  
**问题**： 你的设备已加密和

- 已禁用加密按钮。
- 出现一条消息，指出仍需要加密。
- 尝试使用公司门户或 Microsoft Intune 应用时收到错误。

**要尝试的操作**

- 确保设备已充电并已插入。  
- 确保设备上已设置 PIN 或密码。  

仍需帮助？ 请联系公司支持人员（访问[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)获取联系信息），或写邮件给 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 团队</a>。  
