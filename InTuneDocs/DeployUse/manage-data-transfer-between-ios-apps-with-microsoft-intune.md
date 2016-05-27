---
# required metadata

title: 管理 iOS 应用之间的数据传输 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 管理 iOS 应用之间的数据传输
## 管理 iOS 应用
保护公司数据包括确保文件传输仅限于在你所管理的应用中进行。  可以通过以下方式管理 iOS 应用：

-   通过为应用配置 MAM 策略来防止公司数据丢失，这种应用我们称为“策略托管”应用。

-   你还可以通过“MDM 通道”部署和管理应用。  这需要设备注册 MDM 解决方案。 可以是“策略托管”应用，也可以是其他托管应用。

适用于 iOS 设备的“打开方式管理”功能可以将文件传输限制为仅在使用“MDM 通道”部署的应用之间进行。 “打开方式管理”限制在配置设置中设置，并使用 MDM 解决方案进行部署。  当用户安装了部署的应用时，会应用你设置的限制。
##  将 MAM 用于 iOS 应用
移动应用管理 (MAM) 策略可与 iOS 的“打开方式管理”功能结合使用来通过以下方式保护公司数据：

-   **不由任何 MDM 解决方案管理的员工所有的设备：**可以将 MAM 策略设置设置为“仅允许应用将数据传输到托管应用”。 当最终用户在非策略托管应用中打开受保护的文件时，文件不可读。

-   **由 Intune 管理的设备：**对于在 Intune 中注册的设备，在已通过 Intune 部署 MAM 策略和其他托管的 iOS 应用的情况下自动允许在应用之间进行数据传输。 要允许具有 MAM 策略的应用之间的数据传输，请启用“仅允许应用将数据传输到托管应用”设置。 可使用“打开方式管理”功能控制在通过 Intune 部署的应用之间进行的数据传输。   

-   **第三方 MDM 解决方案管理的设备：**你可以使用“打开方式管理”功能将数据传输限制为仅在托管应用之间进行。
若要确保你使用第三方 MDM 解决方案部署的应用也与你在 Intune 中配置的 MAM 策略相关联，你必须按照[配置用户 UPN 设置](#configure-user-upn-setting)演练中所述配置用户 UPN 设置。  如果已使用用户 UPN 设置部署应用，则将在最终用户使用其工作帐户登录时将 MAM 策略应用到该应用。

> [!IMPORTANT]
> 只有部署到由第三方 MDM 管理的设备的应用才需使用用户 UPN 设置。  Intune 托管设备不需要使用此设置。

## 配置用户 UPN 设置
由第三方 MDM 解决方案管理的设备必须使用此配置。 下述过程是实现 UPN 设置的一般流程以及该过程所产生的最终用户体验：


1.  为 iOS 平台配置移动应用管理策略。 根据公司要求配置策略设置，并选择应使用此策略的应用。

2.  使用步骤 3 和 4 中所述的设置部署你想要通过第三方 MDM 解决方案管理的应用和电子邮件配置文件。

3.  使用以下应用配置设置来部署应用：键 =IntuneMAMUPN，值 =<username@company.com> [示例：“IntuneMAMUPN”、“jondoe@microsoft.com”]

4.  将打开位置策略部署到已注册设备。

### 最终用户体验示例

1.  最终用户在设备上安装 Microsoft Word 应用。

2.  最终用户启动托管的本机电子邮件应用以访问其电子邮件。

3.  最终用户尝试在 Microsoft Word 中打开本机邮件中的文档。

4.  Word 应用启动时，将提示最终用户使用其工作帐户进行登录。  最终用户在出现提示时输入的工作帐户应与你在 Microsoft Word 应用的应用配置设置中指定的帐户匹配。

    > 在个人环境中使用 Word 应用时，最终用户可以将其他个人帐户添加到 Word 来完成其个人工作，并且该帐户不受 MAM 策略的影响。

5.  登录成功后，会将应用策略设置应用到 Word 应用。

6.  现在数据传输成功，并且已在应用中将该文档标记为企业标识。 此外，在工作环境中处理数据并相应地应用策略设置。

### 另请参阅
[通过 Microsoft Intune 使用移动应用管理策略保护应用数据](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


