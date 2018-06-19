---
title: 电源优化阻止电子邮件访问 | Microsoft Docs
description: 了解如何关闭 Android 的电源优化，确保能收到电子邮件。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 663da92e11befeae1f65467e887870a52640cbeb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020565"
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Android 的电池优化开启时，Outlook 不会同步托管的电子邮件

> [!IMPORTANT]
> 我们已经收到越来越多关于此问题的客户报告，这也是本文对此进行说明的原因所在。 如果在执行下列步骤后仍然遇到此问题，请联系[公司支持人员](https://portal.manage.microsoft.com#HelpDeskDialog)，获取更多帮助。

在 Intune 中注册设备可以访问公司资源。 最常见的资源之一是电子邮件访问。 一个已知问题是由于开启了电池优化，无法通过 Android 设备上的 Outlook 访问电子邮件。 出于尽量延长设备开机时间的原因，电池优化可能会自动开启。 电池优化在某种程度上确实能帮助延长开机时间，因为它会尝试关闭自动电子邮件下载。

Microsoft Intune 团队正积极开发针对此问题的解决方案。 防止设备进入低能耗模式的一种方法是，保证电池电量高于 30%。 进入低能耗模式后，若要避免发生此问题，则必须从受电池优化和省电设置影响的应用列表中删除公司门户和 Outlook。

Android 设备种类繁多，其制造商也各有不同。 我们无法说明每个设备需采取的具体步骤。 可能只需在系统设置中执行操作，也可能还需在某些制造商特定的设置中执行操作。 我们提供了一些常见示例，说明如何在 Android 设备上解决此问题。

## <a name="unmodified-android-devices"></a>未经修改的 Android 设备

许多制造商都对 Android 设备添加了修改。 这可能改变你与设备交互的具体方式，例如主题和通知。 Google 一般不会对旗下手机进行这类修改。 例如，在 Android 7.0 或更高版本的 Google Pixel 设备上，可以按下列步骤从电池优化中删除这些应用：

1. 打开“设置” 。
2. 点击“电池” > “更多” > “电池优化”。
3. 点击向下键，然后点击“不优化”。
4. 选择公司门户和 Outlook 应用，然后关闭电池优化。

## <a name="samsung-devices"></a>Samsung 设备

对于其他类型的 Android 设备，例如 Android 7.0 或更高版本的 Samsung 设备，必须采取其他步骤才能从电池优化中删除 Outlook 和公司门户应用。

1. 打开“设置” 。
2. 依次点击“菜单(…)” > “特殊访问” > “优化电池用量”。
3. 从下拉列表中选择“所有应用”。
4. 将公司门户和 Outlook 应用旁边的切换键设为“关闭”，关闭电池优化。

此外，如果使用 Android 版本较低的 Samsung 设备，还需按下列步骤从省电模式中删除这些应用。

1. 打开“设置” 。
2. 依次点击“设备维护” > “电池” > “未监视的应用”。
3. 点击“添加应用”。
4. 选择公司门户和 Outlook 应用，然后点击“完成”。

## <a name="oneplus-devices"></a>OnePlus 设备

通过其他方法找到这些设置的另一个示例是，在系统设置中进行搜索。 例如，在 Android 7.1.1 的 OnePlus 3 上，请执行下列步骤： 

1. 打开“系统设置”。 
2. 点击“搜索”按钮。 即屏幕右上角形似放大镜的按钮。 
3. 在搜索中键入“电池优化”，然后在显示的“设置”屏幕上选择“电池优化”选项。 
4. 点击“电池” > “电池优化”。
5. 选择公司门户和 Outlook 应用，然后选择“不优化”。 点击“完成”。

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

仍需帮助？ 请与公司支持人员联系。 有关他们的联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
