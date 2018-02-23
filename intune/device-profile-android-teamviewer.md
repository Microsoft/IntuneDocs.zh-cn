---
title: "如何使用 TeamViewer 远程管理设备"
titlesuffix: Azure portal
description: "了解如何使用 TeamViewer 远程管理设备。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 2/14/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0219993e0322be06dbf9b26707789332039001f1
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2018
---
# <a name="provide-remote-assistance-for-intune-managed-devices"></a>为 Intune 托管设备提供远程协助

Intune 可使用 [TeamViewer](https://www.teamviewer.com) 软件（另行购买）向你所管理的设备的用户提供远程协助。 请使用本主题介绍的信息开始使用。

## <a name="before-you-start"></a>开始之前

### <a name="supported-devices"></a>支持的设备

Intune 托管的 Android 和 Windows 设备支持远程管理。

>[!NOTE]
>TeamViewer 软件不支持 Windows Holographic (HoloLens)、Windows 团队 (Surface Hub) 和 Windows 10 S。



### <a name="required-permissions"></a>所需权限

确保 Azure 门户的用户具有以下作为 [Intune 角色](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control)分配给他们的权限：
- 若要允许管理员修改 TeamViewer 连接器设置，请授予“更新远程协助”权限。
- 若要允许管理员启动新的远程协助请求，请授予“请求远程协助”权限。 具有“请求远程协助”权限的用户可为任何用户请求发起会话。 他们不受任何 Intune 角色分配范围的限制。 Intune 角色分配范围不会限制可以启动远程协助请求的设备或用户。

>[!NOTE]
>通过启用 TeamViewer，你可以让 Intune 连接器的 TeamViewer 创建 TeamViewer 会话，读取 Active Directory 数据并保存 TeamViewer 帐户访问令牌。

### <a name="configure-the-intune-teamviewer-connector"></a>配置 Intune TeamViewer 连接器

必须先按照以下步骤配置 Intune TeamViewer 连接器，然后才可向设备提供远程协助：


1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“设备和组”边栏选项卡上，选择“设置” > “TeamViewer 连接器”。
5. 在“TeamViewer 连接器”边栏选项卡上，单击“启用”，然后查看和接受 TeamViewer 服务许可证协议。
6. 选择“登录到 TeamViewer 并授权”。
7. 随即一个 Web 页面将打开 TeamViewer 网站。 输入你的 TeamViewer 许可证凭据，然后单击“登录”。


## <a name="how-to-remotely-administer-a-device"></a>如何远程管理设备

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“设备”边栏选项卡上，选择“管理” > “所有设备”。
5. 选择你想要远程管理的设备，然后在“设备属性”边栏选项卡上，选择“更多” > “新建远程协助会话”。
6. 将 Intune 连接到 TeamViewer 服务后，将看到设备的一些相关信息。 选择“连接”以开始远程会话。

![Android TeamViewer 示例](./media/android-teamviewer.png)

在 TeamViewer 窗口中，可以在设备上执行一系列的远程操作，包括设备的远程控制。 有关可执行操作的完整详细信息，请参阅 [TeamViewer 文档](https://www.teamviewer.com/support/documents/)。

完成后，关闭 TeamViewer 窗口。

## <a name="next-steps"></a>后续步骤

最终用户会在其设备上的公司门户应用图标上看到一个通知标志，在打开应用时也会看到一条通知。 然后，他们就可以接受远程协助请求了。
