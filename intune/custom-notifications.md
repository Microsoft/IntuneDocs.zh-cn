---
title: 使用 Microsoft Intune 向用户发送自定义通知
titleSuffix: Microsoft Intune
description: 使用 Intune 创建自定义推送通知并将其发送给使用 iOS 和 Android 设备的用户
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bffbc96e945d522453c299717a6eb413354a4af4
ms.sourcegitcommit: 98f2597eec28c6096985d5a1acae72430c2afb1a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70878039"
---
# <a name="send-custom-notifications-in-intune"></a>使用 Intune 发送自定义通知  

使用 Microsoft Intune 向使用托管 iOS 设备和 Android 设备的用户发送自定义通知。 这些消息在用户设备上显示为来自公司门户应用和 Microsoft Intune 应用的标准推送通知，就像设备上显示的来自其他应用程序的通知一样。 Windows 设备不支持 Intune 自定义通知。   

自定义通知消息包括短标题和不超过 500 个字符的消息正文。 可以出于任何常规通信目的自定义这些消息。

## <a name="common-scenarios-for-sending-custom-notifications"></a>发送自定义通知的常见方案  

- 自定义通知用于提醒特定用户有关公司门户中可用的新应用。  
- 通知所有员工关于时间表中发生的更改，例如因恶劣天气导致的办公楼关闭。  

## <a name="considerations-for-using-custom-notifications"></a>使用自定义通知的注意事项  

**设备配置**：  
- 设备必须安装公司门户应用或 Microsoft Intune 应用，用户才可以接收自定义通知。 它们还必须配置权限，以允许公司门户应用或 Microsoft Intune 应用发送推送通知。 如有必要，公司门户应用和 Microsoft Intune 应用可能会提示用户允许通知。  
- 在 Android 上，Google Play Services 是必备依赖项。  
- 设备必须已注册 MDM。

**创建通知**：  
- 若要创建消息，请使用分配了包含“组织”的“更新”权限的 Intune 角色的帐户   。 若要向用户分配权限，请参阅[角色分配](role-based-access-control.md#role-assignments)  
- 自定义通知的标题最多允许 50 个字符，其消息最多允许 500 个字符。  
- Intune 不保存已发送的消息。 若要重新发送消息，必须重新创建该消息。  
- 每小时最多只能发送 25 条消息。 此限制仅针对租户级别。  
- 每个通知都可以直接面向最多 25 个组。 嵌套组不计入此总数。  
- 组可以包含用户或设备，但仅向用户发送消息且发送到用户已注册的每个 iOS 或 Android 设备。  

**发送**：  
- Intune 将消息发送到用户的公司门户应用或 Microsoft Intune 应用，然后创建推送通知。 用户无需登录应用，即可在设备上推送通知。  
- Intune 和公司门户应用及 Microsoft Intune 应用无法保证发送自定义通知。 自定义通知可能会在几个小时的延迟后显示（如果有的话），因此它们不应用于紧急消息。  
- 来自 Intune 的自定义通知消息在设备上显示为标准推送通知。 如果公司门户应用在收到通知后在 iOS 设备上处于打开状态，则通知将在应用中显示，而不在推送通知中显示。  
- 因设备设置而异，自定义通知可以在 iOS 和 Android 设备的锁屏界面上显示。  
- 在 Android 设备上，其他应用可能可以访问自定义通知中的数据。 请勿将其用于敏感通信。  
- 最近未注册设备的用户或从组中删除的用户可能仍会收到随后发送到该组的自定义通知。  同样，如果在向组发送自定义通知后将用户添加到组，则新添加的用户可能会收到之前发送的通知消息。  

## <a name="send-a-custom-notification"></a>发送自定义通知  

1. 使用可以创建和发送通知的帐户登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后转至“设备” > “发送自定义通知”   。  

2. 在“基本信息”选项卡上，指定以下各项，然后选择“下一步”以继续  。  
   - **标题** - 指定此通知的标题。 标题最多允许 50 个字符。  
   - **正文** - 指定消息。 消息最多允许 500 个字符

   ![创建自定义通知](./media/custom-notifications/custom-notifications.png)  

3. 在“分配”选项卡上，选择要向其发送此自定义通知的组，然后选择“下一步”以继续  。  

4. 在“查看 + 创建”选项卡上查看信息，并在准备好发送通知后，选择“创建”   。  

Intune 会立即处理你创建的消息。 消息已发送的唯一确认就是确认已发送自定义通知的 Intune 通知。  

![发送通知确认](./media/custom-notifications/notification-sent.png)  

Intune 不会跟踪你发送的自定义通知，并且设备不会在设备的通知中心之外记录回执。  

## <a name="receive-a-custom-notification"></a>接收自定义通知  

用户可以在设备上看到作为标准推送通知由 Intune 从公司门户应用或 Microsoft Intune 应用发送的自定义通知消息。 这些通知类似于用户从设备上的其他应用接收的推送通知。  

在 iOS 设备上，如果在收到通知时公司门户应用处于打开状态，则通知将在应用中显示，而不在推送通知中显示。  

通知将一直保留，除非用户将其关闭。  

## <a name="next-steps"></a>后续步骤  
[管理设备](device-management.md)
