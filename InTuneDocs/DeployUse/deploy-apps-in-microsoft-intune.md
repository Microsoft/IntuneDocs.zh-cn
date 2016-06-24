---
# required metadata

title: 部署应用 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:
---
# 在 Microsoft Intune 中部署应用

使用本主题中的信息可帮助部署 Microsoft Intune 应用。


## 部署应用
在此过程中，你将对所选设备或用户部署应用。

### 部署应用

1. 在 [Microsoft Intune 管理员控制台](https://manage.microsoft.com)中，单击**应用**&gt;**应用**以查看管理的应用列表。

2.  选择要部署的应用，然后单击“管理部署”。

3.  首先在“选择组”页上的“&lt;应用名称&gt;”对话框中，选择要对其部署应用的用户或设备组。

4.  在“部署操作”页上，配置下列设置：

    - **批准** - 选择部署是否为：
        - **必需**（强制安装）
        - **可用**（用户按需从公司门户安装）
        - **不适用**（未安装应用或公司门户未显示该应用）
        - **卸载**（将从目标设备卸载应用）。
    - **截止时间** - 对于“必需”安装，选择将在多长时间之后部署应用。 可以选择预定义的值，也可以选择“自定义”来配置你自己的截止时间。

5. 如果可以通过移动应用程序管理策略来配置要部署的应用，则会显示“移动应用程序管理”页。 在此页上，选择想要与此应用关联的移动应用程序管理策略。

    [查看与移动应用程序管理策略兼容的 Microsoft 应用。](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. 如果要部署的应用与 Intune VPN 配置文件兼容，则会显示“VPN 配置文件”页。 在此页上，你可以选择将 iOS 应用与已部署的 VPN 配置文件关联。 在应用启动时，将自动打开 VPN 连接。 若要使 VPN 配置文件可用，则必须启用“Per-app VPN”配置文件设置。
 若要了解如何配置 VPN 配置文件（包括支持将配置文件与应用相关联），请参阅[通过 Microsoft Intune 使用 VPN 配置文件帮助用户连接到其工作](vpn-connections-in-microsoft-intune.md)。

## 示例

在此示例中，将应用程序作为“可用”部署到 iOS 设备。
用户设备上的公司门户中将显示该应用，用户可从中安装该应用。 例如，在此屏幕截图中，iOS 版必应应用是使用“外部链接”安装类型（采用自定义图标）部署的，并且选中了选项“将此应用显示为特色应用并在公司门户中突出显示”。
    ![iOS 可用应用](./media/available-install-on-iOS.png)

如果将此应用作为“必需”到 iOS 设备，则用户将接收到通知，指示应用已准备就绪，可供安装。 例如，在此屏幕截图中，iOS 版工作文件夹应用是使用“来自应用商店的托管 iOS 应用”安装类型部署的。
    ![iOS 必需应用](./media/iOS-Required-install.PNG)

## 后续步骤

部署应用之后，需要监视其进度。 有关详细信息，请参阅[在 Microsoft Intune 中监视应用](monitor-apps-in-microsoft-intune.md)。


<!--HONumber=Jun16_HO2-->


