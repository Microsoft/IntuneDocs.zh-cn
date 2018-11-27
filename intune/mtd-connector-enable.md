---
title: 在 Microsoft Intune 中启用移动威胁防御连接器
titleSuffix: ''
description: 在移动威胁防御 (MTD) 合作伙伴和 Microsoft Intune 之间启用连接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2937814ae5ceb6c7d8b3def4e954c8eec9337126
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180470"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>在 Intune 中启用移动威胁防御连接器

> [!NOTE] 
> 本主题适用于所有移动威胁防御合作伙伴。

在移动威胁防御 (MTD) 安装过程中，已配置了用于在 MTD 合作伙伴控制台中对威胁进行分类的策略，并且已在 Intune 中创建了设备符合性策略。 如果已在 MTD 合作伙伴控制台中配置了 Intune 连接器，则现在可在 Intune 中启用 MTD 连接。

## <a name="to-enable-the-mtd-connector"></a>启用 MTD 连接器

1. 转到 [Azure 门户](https://portal.azure.com)，然后使用 Intune 凭据登录。 成功登录后，会看到“Azure 仪表板”。

2. 在“Azure 仪表板”中，从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune。

3. 选择“Intune”，随即打开“Intune 仪表板”。

4. 在“Intune 仪表板”中，选择“设备符合性”，然后选择“设置”部分下的“移动威胁防御”。

5. 在“移动威胁防御”窗格上，选择“添加”。

6. 从下拉列表中选择 MTD 解决方案作为“要设置的移动威胁防御连接器”。

    ![Intune Azure 门户中的 MTD 设置](./media/enable-mtd-connector-1.png)

7. 根据你组织的要求启用切换选项。 可见的切换选项因 MTD 合作伙伴而异。

## <a name="mtd-toggle-options"></a>MTD 切换选项

可以根据组织要求决定需要启用哪些 MTD 切换选项。 下面是更多详细信息：

- **将 Android 4.1+ 设备连接到 [MTD 合作伙伴名称] for Work MTD**：如果启用此选项，可以让 Android 4.1 + 设备将安全风险报回 Intune。
    - **如果未收到任何数据则标记为不符合：** 如果 Intune 未从 MTD 合作伙伴收到有关此平台上的设备的数据，则将设备视为不符合。
<br></br>
- 将 iOS 8.0+ 设备连接到 [MTD 合作伙伴名称] for Work MTD：如果启用此选项，可以让 iOS 8.0+ 设备将安全风险报回 Intune。
    - **如果未收到任何数据则标记为不符合：** 如果 Intune 未从 MTD 合作伙伴收到有关此平台上的设备的数据，则将设备视为不符合。
<br></br>
- 启用 iOS 设备的应用同步：允许此 Mobile Threat Defense 合作伙伴请求 Intune 中的 iOS 应用程序的元数据，以用于威胁分析。

- **阻止不受支持的操作系统版本**：如果设备运行的操作系统版本低于支持的最低版本，则阻止该版本。

- 合作伙伴无响应之前的天数：在 Intune 由于连接断开将合作伙伴视为无响应之前的天数。 Intune 将忽略无响应 MTD 合作伙伴的符合性状态。

> [!IMPORTANT] 
> 在创建设备符合性和条件性访问策略规则之前，必须先添加和分配 MTD 应用。 这样可以确保最终用户能够安装 MTD 应用，以便访问电子邮件或其他公司资源。

> [!TIP]
> 可以从“移动威胁防御”窗格中查看 Intune 和 MTD 合作伙伴之间的“连接状态”和“上次同步”时间。
