---
title: 在 Microsoft Intune 中远程管理设备 - Azure | Microsoft Docs
description: 查看使用 TeamViewer 所需的角色、如何安装 TeamViewer 连接器，以及在 Azure 门户中使用 Microsoft Intune 远程管理设备的分步指南
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/05/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd2d9f0a0caf87eb75ba3a9cdc123e69425ceb8b
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509717"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>使用 TeamViewer 远程管理 Intune 设备

可使用 [TeamViewer](https://www.teamviewer.com) 远程管理 Intune 托管的设备。 TeamViewer 是需另行购买的第三方程序。 本主题介绍如何在 Intune 中配置 TeamViewer，以及如何远程管理设备。 

## <a name="prerequisites"></a>必备条件

- 使用支持的设备。 Intune 托管的 Android、Windows、iOS 和 macOS 设备支持远程管理。 TeamViewer 可能不支持 Windows Holographic (HoloLens)、Windows Team (Surface Hub) 或 Windows 10 S。有关可支持性的信息，请参阅 [TeamViewer](https://www.teamviewer.com)，了解所有更新。

- Azure 门户中的 Intune 管理员必须具有以下 [Intune 角色](role-based-access-control.md)：  

    - **更新远程协助**：允许管理员修改 TeamViewer 连接器设置
    - **请求远程协助**:允许管理员为任何用户发起新的远程协助会话。 具有此角色的用户不受作用域内任何 Intune 角色的限制。 此外，获得了作用域内某一 Intune 角色的用户或设备组也可以请求远程协助。 

- 具有登录凭据的 [TeamViewer](https://www.teamviewer.com) 帐户。 只有一些 TeamViewer 许可证可能支持与 Intune 集成。 有关 TeamViewer 特定的需求，请参阅 [TeamViewer 集成合作伙伴：Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/)。

通过 TeamViewer，可以让 Intune TeamViewer 连接器创建 TeamViewer 会话，读取 Active Directory 数据并保存 TeamViewer 帐户访问令牌。

## <a name="configure-the-teamviewer-connector"></a>配置 TeamViewer 连接器

要向设备提供远程协助，请按照以下步骤配置 Intune TeamViewer 连接器：

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，然后搜索“Microsoft Intune”。
2. 在 Microsoft Intune 中，依次选择“设备”、“TeamViewer 连接器”。
3. 选择“连接”，然后接受许可协议。
4. 选择“登录到 TeamViewer 并授权”。
5. 随即一个 Web 页面将打开 TeamViewer 网站。 输入 TeamViewer 许可证凭据，然后单击“登录”。

## <a name="remotely-administer-a-device"></a>远程管理设备

配置连接器后，即可远程管理设备。 请使用以下步骤： 

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，然后搜索“Microsoft Intune”。
2. 在 Microsoft Intune 中，依次选择“设备”、“所有设备”。
3. 从列表中，选择想要远程管理的设备。 在设备属性中，选择“新远程协助会话”。
4. 将 Intune 连接到 TeamViewer 服务后，将看到设备的一些相关信息。 选择“连接”可开始远程会话。

![使用 TeamViewer 远程管理 Android 设备 - 示例](./media/android-teamviewer.png)

启动远程会话时，用户会在设备的公司门户应用图标上看到通知标志。 打开应用时也会显示通知。 然后，用户即可接受远程协助请求。

> [!NOTE]
> 使用“无用户”方法注册的 Windows 设备（如 DEM 和 WCD）不会在公司门户应用中显示 TeamViewer 通知。 在这些情况下，建议使用 TeamViewer 门户生成会话。

在 TeamViewer 中，可对设备完成一系列操作，包括控制该设备。 有关可执行操作的详细信息，请参阅 [TeamViewer 指南](https://www.teamviewer.com/support/documents/)。

完成后，关闭 TeamViewer 窗口。
