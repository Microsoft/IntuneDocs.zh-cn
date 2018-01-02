---
title: "在 Intune 中设置注册限制"
titlesuffix: Azure portal
description: "按平台限制注册，并在 Intune 中设置设备注册限制。 \""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdb89d3426bd2dd040b184c8f7c23397bbed576b
ms.sourcegitcommit: a99a5104400708b47ecee80075264d541b82874f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2017
---
# <a name="set-enrollment-restrictions"></a>设置注册限制

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

作为 Intune 管理员，可创建和管理注册限制，这些限制可以定义注册接受 Intune 的管理的设备数量和类型。 可创建多个限制并将其应用于不同用户组。 可为不同限制设置[优先级顺序](#change-enrollment-restriction-priority)。

>[!NOTE]
>注册限制不是安全功能。 遭到入侵的设备可能会误报字符。 这些限制是针对非恶意用户的最合适的障碍。

>[!NOTE]
>下面所述的组分配注册限制和优先级功能即将在 Intune 客户群间推出。 此次推出完成之前，你可能无权访问组和优先级功能。 

可创建的特定注册限制包括：

- 最大设备注册数
- 可注册的设备平台：
  - Android
  - Android for Work
  - iOS
  - macOS
  - Windows
- iOS、Android、Android for Work 和 Windows 的平台操作系统版本（仅 Windows 10 版本可供使用，如果要支持 Windows 8.1，请将此留空）
  - 最低版本
  - 最高版本
- 限制个人拥有的设备（仅 iOS、Android、Android for Work、macOS）

## <a name="default-restrictions"></a>默认限制

为设备类型和设备限制注册限制自动提供默认限制。 更改默认选项。 默认限制适用于所有用户和无用户注册。 可通过创建优先级更高的新限制来替代这些默认值。

## <a name="create-a-restriction"></a>创建限制

1. 登录到 Azure 门户中。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”。
3. 选择“设备注册” > “注册限制”。
4. 选择“创建限制”。
5. 为该限制提供名称和描述。
6. 选择“限制类型”，然后单击“创建”。
7. 针对设备限制，请单击“设备限制”，设置用户可注册的最大设备数。
8. 针对设备类型限制，请单击“平台”和“平台配置”以允许或阻止各种平台和版本。
9. 单击“分配” > “+ 选择组”。
10. 在“选择组”下，选择一个或多个组，然后单击“选择”。 限制仅适用于它分配到的组。 如果连一个组都没有分配限制，则不会产生任何影响。
11. 单击 **“保存”**。
12. 使用高于默认值的优先级创建新限制。 可[更改优先级](#change-enrollment-restriction-priority)。

## <a name="set-device-type-restrictions"></a>设置设备类型限制

通过执行以下步骤可更改设备类型限制的设置：

1. 登录到 Azure 门户中。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”。
3. 选择“设备注册” > “注册限制”。
4. 在“设备类型限制”下，选择想要设置的限制。
5. 在限制名称（默认限制为“所有用户”）下，选择“平台”。 为列出的每个平台选择“允许”或“阻止”。
6. 单击 **“保存”**。
7. 在限制名称（默认限制为“所有用户”）下，选择“平台配置”，并为列出的平台选择最小和最大“版本”。 支持的版本包括：
  - Android 和 Android for Work 支持 major.minor.rev.build。
  - iOS 支持 major.minor.rev。
  - Windows 仅对 Windows 10 支持 major.minor.rev.build。
  操作系统版本不会应用于使用设备注册计划、Apple School Manager 或 Apple Configurator 应用注册的 Apple 设备。 
8. 指定是否对每个列出的平台允许或阻止个人拥有的设备。

    ![设备限制工作区的屏幕截图，含默认设备平台配置，其中显示已配置“个人拥有的”设置。](media/device-restrictions-platform-configurations.png)
9. 单击 **“保存”**。

>[!NOTE]
>- 如果阻止私人拥有的 Android 设备进行注册，私人拥有的 Android for Work 设备仍可注册。
>- 默认情况下，Android for Work 设备的设置与 Android 设备的设置相同。 但是，更改 Android for Work 设置后则不再相同。
>- 如果阻止个人 Android for Work 注册，那么仅公司 Android 设备可注册为 Android for Work。

## <a name="set-device-limit-restrictions"></a>设置设备限制

通过执行以下步骤可更改设备限制的设置：

1. 登录到 Azure 门户中。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”。
3. 选择“设备注册” > “注册限制”。
4. 在“设备限制”下，选择想要设置的限制。
5. 选择“设备限制”，然后在下拉列表中选择用户可注册的最大设备数。
    ![含设备限制的设备限制边栏选项卡的屏幕截图。](./media/device-restrictions-limit.png)
6. 单击 **“保存”**。

## <a name="change-enrollment-restriction-priority"></a>更改注册限制优先级

当用户在分配有限制的多个组中时，则使用优先级。 用户仅遵循其所在组分配到的最高优先级的限制。 例如，Joe 位于优先级为 5 的限制的 A 组和优先级为 2 的限制的 B 组。 Joe 仅遵循优先级为 2 的限制。 

创建限制时，将其添加到默认值正上方的列表中。

设备注册同时包括设备类型和设备限制的默认限制。 这两个限制应用于所有用户，除非由更高优先级的限制替代。 

可更改任何非默认限制的优先级。 

**更改限制优先级**

1. 登录到 Azure 门户中。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”。
3. 选择“设备注册” > “注册限制”。
4. 将鼠标悬停在优先级列表中的限制上。
5. 使用三个垂直点，将优先级拖到列表中的所需位置。





