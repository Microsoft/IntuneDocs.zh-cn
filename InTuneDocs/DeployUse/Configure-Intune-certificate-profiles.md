---
title: "配置证书配置文件 | Microsoft Intune"
description: "了解如何创建 Intune 证书配置文件。"
keywords: 
author: nbigman
manager: Arob98
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 72288296d966b9b9fae4fd721b4460528213f626
ms.openlocfilehash: 40ae2ce3ea4393d24770c010bf5292ca1829a7f1


---

# 配置 Itune 证书配置文件
按照[为 SCEP 配置证书基础结构](configure-certificate-infrastructure-for-scep.md)或[为 PFX 配置基础结构](configure-certificate-infrastructure-for-pfx.md)所述配置基础结构和证书后，可以配置证书配置文件：

**任务 1** - 导出受信任根 CA 证书 **任务 2** - 创建可信 CA 证书配置文件 **任务 3** - 以下两项之一：

创建 SCEP 证书配置文件

创建 .PFX 证书配置文件

### 任务 1 — 导出受信任的根证书
将受信任的根 CA 证书从发证 CA 或信任你的发证 CA 的任何设备中导出为 **“.cer”** 文件。 不导出私钥。

配置受信任的证书配置文件时，你将导出该证书。

### 任务 2 — 创建受信任的证书配置文件
你必须创建**受信任的证书配置文件**，然后才能创建 SCEP 或 .PFX 证书配置文件。 对于每个移动设备平台，你需要一个受信任的证书配置文件和一个 SCEP 或 .PFS 配置文件。

##### 要创建“可信证书”配置文件

1.  打开 [Intune 管理控制台](https://manage.microsoft.com)，然后单击“策略”&gt;“添加策略”。

2.  配置以下策略类型之一：

    **Android &gt; 受信任的证书配置文件（Android 4 及更高版本）**

    **iOS &gt; 受信任的证书配置文件（iOS 7.1 及更高版本）**

    **Mac OS X &gt; 受信任的证书配置文（Mac OS X 10.9 及更高版本）**

    **Windows &gt; 受信任的证书配置文件（Windows 8.1 及更高版本）**

    **Windows &gt; 受信任的证书配置文件（Windows Phone 8.1 及更高版本）**

    了解详细信息：[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  提供所需信息以配置 Android、iOS、Mac OS X、Windows 8.1 或 Windows Phone 8.1 的受信任证书配置文件设置。 在“证书文件”设置中，导入你从发证 CA 导出的受信任的根 CA 证书 (**.cer**)。 “目标存储”设置仅适用于运行 Windows 8.1 及更高版本的设备并且该设备必须具有多个证书存储。


4.  完成后，请单击“保存策略” **Save Policy**。

新策略显示在 **“策略”** 工作区中，现在可以部署。

### 任务 3 – 创建 SCEP 或 .PFX 证书配置文件
创建可信 CA 证书配置文件后，为你要使用的各个平台创建 SCEP 或 .PFX 证书配置文件。 创建 SCEP 证书配置文件时，你必须为相同平台指定受信任的证书配置文件。 尽管这链接了两个证书配置文件，但是你依然必须单独部署各个配置文件。

##### 创建 SCEP 证书配置文件

1.  打开 [Intune 管理控制台](https://manage.microsoft.com)，单击“策略”&gt;“添加策略”。

2.  配置以下策略类型之一：

    **Android &gt; SCEP 证书配置文件(Android 4 及更高版本)**

    **iOS &gt; SCEP 证书配置文件(iOS 7.1 及更高版本)**

    **Mac OS X &gt; SCEP 证书配置文件(Mac OS X 10.9 及更高版本)**

    **Windows &gt; SCEP 证书配置文件(Windows 8.1 及更高版本)**

    **Windows &gt; SCEP 证书配置文件(Windows Phone 8.1 及更高版本)**

    了解详细信息：[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  按照配置文件配置页上的说明配置 SCEP 证书配置文件设置。

4.  完成后，请单击“保存策略” **Save Policy**。

新策略显示在 **“策略”** 工作区中，现在可以部署。

##### 创建 .PFX 证书配置文件

1.  打开 [Intune 管理控制台](https://manage.microsoft.com)，单击“策略”&gt;“添加策略”。

2.  配置以下策略类型之一：



-   **Android &gt; .PFX 证书配置文件(Android 4 及更高版本)**

    -   **Windows &gt; PKCS #12 (.PFX)证书配置文件(Windows 10 及更高版本)**

    -   **Windows &gt; PKCS #12 (.PFX)证书配置文件(Windows Phone 10 及更高版本)**

    -    **iOS > PKCS #12 (.PFX)证书配置文件(iOS 7.1 及更高版本)**    

    了解详细信息：[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  提供策略窗体上请求的信息。

4.  完成后，请单击“保存策略” **Save Policy**。

新策略显示在 **“策略”** 工作区中，现在可以部署。

## 部署证书配置文件
部署证书配置文件时，可信 CA 证书配置文件的证书文件已经安装在设备上，并且设备使用该 SCEP 或 .PFX 证书配置文件创建设备的证书请求。

根据创建配置文件时使用的平台，证书配置文件仅安装在合适的设备上。

-   你可以对用户集或设备集部署证书配置文件。

    > [!TIP]
    > 若要允许证书在设备注册后快速发布到设备，请将证书配置文件部署至用户组（不是设备组）。 如果部署到设备组，则必须在设备接收策略前进行完整的设备注册。

-   尽管各个配置文件都是单独部署，但是受信任的根和 SCEP/.PFX 配置文件必须部署，否则 SCEP/.PFX 证书策略将无效。

部署证书配置文件的方法与部署其他 Intune 策略的方法相同：

1.  在“策略”  工作区中，选择想要部署的策略，然后单击“管理部署” 。

2.  在“管理部署”  对话框中：

    -   **部署策略** - 选择要向其部署策略的一个或多个组，然后单击**添加**&gt;**确定**。

    -   **要关闭对话框而不部署** - 单击“取消”。

如果你选择的是已部署的策略，则可以在策略列表的下半部分查看有关部署的详细信息。
###  后续步骤

你现在可以使用证书来帮助保护电子邮件、Wi-Fi 和 VPN 配置文件：

-  [使用电子邮件配置文件配置对公司电子邮件的访问](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Microsoft Intune 中的 Wi-Fi 连接](wi-fi-connections-in-microsoft-intune.md)
-  [Microsoft Intune 中的 VPN 连接](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


