---
title: "利用 Intune 在电信费用管理中注册 iOS 设备"
description: "了解如何在电信费用管理中注册 iOS 设备。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope: User help
ROBOTS: 
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 13f284c62e1232a560ec9e5186de4055d616ef3a
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2017
---
# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>在电信费用管理中注册 iOS 设备

组织可能使用电信费用管理软件确保其数据和语音计划在可接受的限制内使用。 设备注册完成后，系统随即将提示选择适合该设备的最佳类别。

  ![iOS 设备上“选择设备的最佳类别”屏幕的屏幕截图。 它显示了企业注册或个人注册选项。](./media/ios-enroll-10-tem-select-best-category.png)

选择适当的选项，然后将收到从应用商店安装 [__Datalert__](https://itunes.apple.com/app/datalert/id771029268?mt=8) 应用的通知。 组织可使用 Datalert 应用测量数据的使用情况。 如果贵组织已配置 Microsoft 工作或学校注册选项，则要求使用工作或学校帐户进行登录。 如果尚未启用此选项，则需要提供电话号码等信息，并使用验证码来验证设备以便从应用注册 Datalert 服务。

  ![Datalert 应用欢迎屏幕的屏幕截图，屏幕上简要介绍如何使用 Datalert 充分利用数据计划，然后提示进入下一屏幕。](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>使用 Microsoft 工作或学校帐户注册 Datalert

> [!NOTE]
> 需要在你的手机上安装并激活 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) 应用，才能按此方法注册。

1. 选择“使用 Microsoft 帐户注册”。

  ![Datalert 应用的设置屏幕的图像，在屏幕的上半部分显示提供注册设备的电话号码字段，在底部显示“使用 Microsoft 帐户注册”，只要你拥有 Microsoft Office 365 帐户和 Intune 订阅。](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. 将收到 __"Datalert" 想要打开 "Authenticator"__ 的通知。 选择“打开”。

  ![提示用户应 Datalert 应用的要求打开 Authenticator 应用的弹出窗口的图像。](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. 使用你的 __Microsoft 学校或工作帐户__登录。 Datalert 安装程序将工作一段时间，然后就应该会完成。 完成后，请点击“完成”。

## <a name="enroll-into-datalert-using-your-phone-number"></a>使用电话号码注册 Datalert

1. 提供设备的电话号码。

  ![显示 Datalert 应用请求电话号码的屏幕截图。](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. 随后会收到一条内含验证码的短信。 提供代码并点击“确定”。

  ![显示 Datalert 应用请求短信验证码的屏幕截图。](./media/ios-enroll-13-tem-datalert-sms.png)

3. 提供验证码后，Datalert 安装将随即完成。 点击“完成”，随后便能从 Datalert 应用中监视数据。

  ![显示 Datalert 应用监视今日数据使用情况的屏幕截图。](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

注册后，即可开始在 Datalert 应用中看到数据的使用情况。

仍需要帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
