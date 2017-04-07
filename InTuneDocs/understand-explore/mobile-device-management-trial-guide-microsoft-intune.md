---
title: "在 Microsoft Intune 中评估移动设备管理 | Microsoft Docs"
description: "在 Intune 免费试用版中评估 MDM。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 4133c64d283682f0be37cd6ac69164ef872a5026
ms.lasthandoff: 01/05/2017


---

# <a name="evaluate-mobile-device-management-in-microsoft-intune"></a>在 Microsoft Intune 中评估移动设备管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本评估指南演示移动设备管理在 Intune 中的工作原理。 用户将：
- 注册设备以使设备由 Intune 管理。
- 创建用于组织用户和设备的组。
- 创建一些设备管理策略并将它们部署到组。
- 发布应用，确保已注册设备的用户可在设备上安装应用。
<!--- - Monitor the device? View a report of compliant devices?--->
<!--- - Remove the device from management--->

## <a name="assumptions"></a>假设
本指南假设用户仅将试用版用于评估目的并希望在订阅时获得一个干净的环境。

为了方便开始使用试用版，专门设置了一个非常简单的环境，该环境仅使用 Intune 并假设它是移动设备管理机构。 但是，在整个指南中，如果希望进一步探索，将引导进入更深层次的技术内容。

试用版的功能与订阅版相同，唯一的区别是试用版限制 100 个用户帐户。

## <a name="whats-not-covered"></a>不包含的内容
|如果感兴趣 |阅读本文 |
|------------------------|----------|
|非测试环境中的 MDM | [入门](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune) |
|使用 Intune 和 System Center Configuration Manager 的 MDM | [混合移动设备管理](https://docs.microsoft.com/en-us/sccm/mdm/understand/hybrid-mobile-device-management) |

由于上述指南可帮助在生产环境中设置 Intune，因此相较评估指南而言，这些指南内容更多，提供工作所需的更多决策点。

若要熟悉快速 Intune，建议从评估指南开始，然后再转到其他指南。

## <a name="prerequisites-for-this-evaluation"></a>此评估的先决条件
- Internet Explorer 10 或更高版本
- 一台设备，将利用该设备来测试 Intune 用户如何使用公司门户注册和管理其设备。 本指南使用 iPad 和 Android 手机。
- 若要管理 iPad 或其他 iOS 设备，需要 [Apple Push Notification 服务证书](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。
- [Intune 试用订阅](sign-up-for-30-day-trial-microsoft-intune.md)

## <a name="set-your-mdm-authority"></a>设置 MDM 机构
使用 Intune 来管理移动设备需要执行的第一步是设置**移动设备管理 (MDM) 机构**。

如果使用 Intune 独立版本（由于此试用版假设正在或即将使用 Intune 作为企业移动性 + 安全性 (EMS) 订阅的一部分），需要将 Intune 设置为移动设备管理机构。 也就是说，指定 Intune 作为用于在组织内部管理移动设备的服务。

希望使用 Intune 和 System Center Configuration Manager 来管理移动设备的客户需要决定是否使用 Intune 或 Configuration Manager 作为其移动设备管理机构。 这是生产环境中需要制定的一项重要决策，因为一旦设置，当前将很难更改，这超出了本评估指南的范围。 要深入了解将 Intune 或 Configuration Manager 设置为 MDM 机构的意义，请参阅[在独立的 Intune 与混合移动设备管理之间进行选择](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)。

对于试用版，将 Intune 设置为 MDM 机构，这不会影响生产环境，除非决定在生产环境中使用试用版。

1. 在 [Intune 管理员控制台](https://manage.microsoft.com/)中，选择“管理员”&gt;“移动设备管理”。
2. 在“任务”列表中，选择“设置 MDM 机构”。 将打开“设置 MDM 机构”  对话框。 <!---screen shot--->
3. Intune 要求确认你希望使用 Intune 作为 MDM 机构。 勾选复选框，然后选择“是”，使用 Intune 来管理移动设备。

## <a name="enroll-your-test-devices-into-intune"></a>在 Intune 中注册测试设备

本指南将注册 Android 手机和 Apple iPad，但本部分末尾提供了[深入了解 Intune 中的设备注册](#Learn-more-about-device-enrollment)链接。
### <a name="android"></a>Android
安装 Microsoft Corporation 提供的 **Intune 公司门户**应用（该应用可从 [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) 获取），并使用注册免费试用版时创建的 Intune [用户凭据](sign-up-for-30-day-trial-microsoft-intune.md#add-users)登录。

### <a name="ios"></a>iOS
在用户注册其 iOS 设备之前，需要先设置 Intune 来管理设备。

1. **获取证书签名请求**<br/>
使用管理员帐户登录 Intune，转到“管理” > “移动设备管理” > “iOS 和 Mac OS X” > “上传 APNs 证书”，然后选择“下载 APNs 证书请求”。 本地保存证书签名请求 (.csr) 文件。 .Csr 文件用于从 Apple 推送证书门户请求信任关系证书。 <!--- screen shot--->
2.    **获取 Apple 推送通知服务证书**<BR/>
转到 [Apple Push Certificates 门户](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&rv=2)，并使用公司 Apple ID 登录以使用 .csr 文件创建 APNs 证书。 选择“在 Apple Push Certificates 门户中上传”后，将收到不能用于 APNs 的 .json 文件。 完成下载后，返回第三方服务器证书的 Apple Push Certificates 门户，然后选择“下载”。<br/>
下载 APNs (.pem) 证书并本地保存文件。 之后必须使用此 Apple ID 才能续订 APNs 证书。
3.    **将 APNs 证书添加到 Intune**<BR/>
在 Microsoft Intune 管理控制台中，转到“管理” > “移动设备管理” > “iOS 和 Mac OS X” > “上传 APNs 证书”，然后选择“上传 APNs 证书”。 转到证书 (.pem) 文件，选择“打开”，然后输入 Apple ID。 使用 APNs 证书， Intune 可通过将策略推送到已注册的移动设备注册并管理 iOS 设备。
4.    **告诉用户如何注册其设备以获取对公司资源的访问权限。**<br/>
有关最终用户注册说明，请参阅[在 Intune 中注册 iOS 设备](https://docs.microsoft.com/en-us/Intune/enduser/enroll-your-device-in-intune-ios)和[在 Intune 中注册 Mac OS X 设备](https://docs.microsoft.com/en-us/Intune/enduser/enroll-your-device-in-intune-mac-os-x)。 注册过程会告知用户将出现的情况，以及 IT 管理员在其设备上可以看到和不能看到的内容。


### <a name="learn-more-about-device-enrollment"></a>深入了解设备注册

Intune 支持以下设备平台：

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

启用设备管理的要求取决于希望管理的平台。
- **Android** 移动设备允许用户使用可从 Google Play 获取的[公司门户应用](/intune/deploy-use/set-up-android-management-with-microsoft-intune)注册。 Intune 中不需要附加配置。
- [**iOS 和 Mac OS X** 的设置要求](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [**Windows Phone** 的设置要求](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)。

<!--- ## Verify enrollment--->
<!--- START HERE

### iOS and Mac OS X
Install the **Microsoft Intune Company Portal** app from Microsoft Corporation available in the App Store and sign in with Intune user credentials added above. View **Enrolled devices** to add your device.



### Windows Phone 8.1
Users install the **Company Portal** app from Microsoft Corporation, available in the Windows Phone store, and sign in with the Intune user credentials added above.  View **Enrolled devices** to add your device.

## Install the previously deployed app
Open the Company Portal on the mobile device, choose **Apps**, and then install **Microsoft Skype**.--->



## <a name="next-steps"></a>后续步骤
[创建用于组织用户和设备的组](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)

