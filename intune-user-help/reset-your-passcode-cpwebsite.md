---
title: 如何从公司门户网站重置密码 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 8ce71a14f9bb7e877fb31e78afdf64d5e492f4a8
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43146683"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>如何从公司门户网站重置设备密码

如果丢失了设备 PIN 或密码，可使用[公司门户网站](https://portal.manage.microsoft.com)进行重置。  

如果使用的是公司注册设备，则可能看不到重置设备密码的选项。 请联系公司支持人员为你重置密码。

   > [!NOTE]
   > 不能为 Android 7.0 或更高版本的设备重置密码。 如果忘记密码，则必须将设备重置为出厂设置。 

## <a name="reset-your-passcode"></a>重置密码

1.  打开[公司门户网站](https://portal.manage.microsoft.com)，然后选择“菜单”按钮 >“设备”。  

2. 选择需要重置密码的设备。  

    ![“设备”页面的屏幕截图，其中 2 个磁贴用于显示无法识别的、以一般方式命名的设备。 灰色横幅位于设备的正下方，提示用户识别他们正在使用的设备或添加新的设备。](./media/rename-reset-device-step2-1808.png) 

3. 选择“重置密码”。 如果页面顶部未显示密码选项，请选择“更多(…)” > “重置密码”。   

   ![公司门户网站上已选设备的设备详细信息页，其顶部具有显示“重命名”、“删除”、“重置设备”、“重置密码”和“远程锁定”的链接列表。 ](./media/rename-reset-device-1808.png)   

    ![“更多”图标的放大视图，用红色箭头突出显示。](./media/rename-reset-device-step3-more-1808.png)  

4. 出现提示时，单击“注销”。再次出现提示时，重新登录。 必须在五分钟内重新登录公司门户网站，否则公司门户网站将不会重置设备密码。  

   > [!NOTE]
   > 必须重新登录以确认身份。 这是为了防止恶意尝试重置设备密码。

   ![显示注销公司门户提示的示例屏幕截图。 用户输入的按钮为“注销”和“取消”。](./media/iwp-reset-passcode-popup-1808.png)

5. 将显示一条消息，警告即将删除现有设备密码。 单击“重置密码”以确认。  
    > [!WARNING]
    > 重置密码后，对设备具有物理访问权限的任何用户都可以访问其中大多数个人和公司信息。 如果该设备当前非你所有，请勿重置密码。  

   ![显示第二条重置密码消息的示例屏幕截图。 其中包括详细介绍设置新密码的文档链接，以及分别用于重置密码和取消的按钮。](./media/iwp-reset-passcode-popup2-1808.png) 

6. 如果要重置 iOS 设备的密码，则将删除其现有密码。 对于 Windows 或 Android 设备，系统将发出临时密码，用于解锁设备和设置新密码。 

   > [!NOTE]
   > 可在公司门户中的设备详细信息页找到 Windows 和 Android 设备的临时密码。 有关特定于操作系统的更多密码介绍，请参阅[设置新密码](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode)部分。  
   
7. 在设备上，转到“设置”并更改临时密码。 

8. 公司门户网站右上角将出现一个标志。 单击可读取通知和确认已成功重置密码。  

## <a name="set-up-a-new-passcode"></a>设置新密码  

本部分介绍每个设备平台的密码重置和临时密码行为。  

**Android**：删除现有密码，然后创建由字母和数字组成的临时密码。

**iOS**：删除现有密码且不创建临时密码。 如果使用 Touch ID 指纹扫描仪打开设备或进行购物，则必须重新进行设置。  

**Windows 10 移动版**：删除现有密码，然后创建由字母和数字组成的临时密码。 Windows Hello 面部识别将仍在设备上有效（如果已设置）。
    
**Windows Phone 8.1**：删除现有密码，然后创建由数字组成的临时密码。  

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。  
