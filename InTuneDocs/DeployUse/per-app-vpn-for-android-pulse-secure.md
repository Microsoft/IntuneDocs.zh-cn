---
title: "使用 Pulse Secure 的 Per-app VPN（针对 Android）| Microsoft Intune"
description: "可为 Intune 托管的 Android 设备创建 per-app VPN 配置文件。"
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52d9d2ad912de7bc775cde2c40c8de27a09ba2af
ms.openlocfilehash: d37630d2aaf4a260acf98a57aa2d38c95711f12b


---

# 使用自定义策略创建适用于 Android 设备的 per-app VPN 配置文件

可为 Intune 托管的 Android 设备创建 per-app VPN 配置文件。 首先，创建使用 Pulse Secure 连接类型的 VPN 配置文件，然后使用特定应用创建与此配置文件相关联的配置策略。 将这些策略部署到 Android 设备或用户组之后，在这些设备上打开某个指定应用将打开此应用的 VPN 连接。

> [备注]
> 
> 此配置文件仅支持 Pulse Secure 连接类型。


### 步骤 1：创建 VPN 配置文件

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，单击**策略**  >  **添加策略**。
2. 通过展开**Android**为新策略选择模板，然后选择**VPN 配置文件(Android 4 及更高版本)**。

3. 在模板中，选择用于**连接类型**的 **Pulse Secure**。
4. 完成并保存 VPN 配置文件。 有关 VPN 配置文件的更多详细信息，请参阅 [VPN 连接](vpn-connections-in-microsoft-intune.md)。

> [!NOTE]
记下 VPN 配置文件名称，以便在下一步中使用。 例如**MyAppVpnProfile**。

### 步骤 2：创建自定义配置策略

   1. 在 Intune 管理控制台中，单击**策略**  ->  **添加策略**  ->  **Android**  ->  **自定义配置**  -> **创建策略**。
   2. 提供策略的名称。
   3. 在**OMA-URI 设置**下，单击**添加**。
   4. 提供设置名称。
   5. 为**数据类型**指定**字符串**。
   6. 为**OMA-URI**指定以下字符串：**./Vendor/MSFT/VPN/Profile/*Name*/PackageList**，其中*Name*是步骤 1 中记下的 VPN 配置文件名称。 本示例中，字符串为 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**。
   7.   在**值**中提供应与配置文件相关联的包列表，其中此列表以分号进行分隔。  例如，如果你希望 Excel 和 Google Chrome 浏览器使用 VPN 连接，则需输入**com.microsoft.office.excel;com.android.chrome**。


   ![Android per-app VPN 自定义策略示例](..\media\android_per_app_vpn_oma_uri.png)
#### 将应用列表设置为黑名单或白名单（可选）
通过使用**黑名单**值，可指定列表中的应用将*不*允许使用 VPN 连接。  所有其他应用将通过 VPN 连接。

或者通过使用**白名单**值，指定*仅*指定的应用可使用 VPN 连接。


1.  在 OMA URI 设置下，单击**添加**。
2.  提供设置名称。
3.  为**数据类型**指定**字符串**。
4.  为**OMA-URI**指定以下字符串：**./Vendor/MSFT/VPN/Profile/*Name*/Mode**，其中 *Name* 是步骤 1 中记下的 VPN 配置文件名称。 本示例中，字符串为**./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**。
5.  在**值**中，输入**黑名单**或**白名单**。



### 步骤 3：部署两个策略

必须向*相同*Intune 组部署*这两个*策略。

   1.  在“策略”  工作区中，选择想要部署的策略，然后单击“管理部署” 。

2.  在“管理部署”  对话框中：

    -   **部署策略** - 选择要向其部署策略的一个或多个组，然后单击**添加**&gt;**确定**。

    -   **要关闭对话框而不部署** - 单击“取消”。

“策略”  工作区“概述”  页的状态摘要和警报可识别需要关注的策略问题。 此外，状态摘要会显示在“仪表板”工作区中。



<!--HONumber=Aug16_HO1-->


