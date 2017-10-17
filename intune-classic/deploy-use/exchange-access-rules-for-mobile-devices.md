---
title: "移动设备的 Exchange 访问规则"
description: "Exchange ActiveSync 访问规则以允许或阻止设备与 EAS 的连接"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 097d6ee8a7ad6752d48f554ee0bc9b3729311fe2
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="exchange-access-rules-for-mobile-devices"></a>移动设备的 Exchange 访问规则

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

移动设备的 Exchange 访问规则决定这些设备对 Exchange ActiveSync 拥有的访问级别。 这些设置会影响所有移动设备，包括未在 Microsoft Intune 中注册的设备。 可以先定义“**默认规则**”，该规则应用于未应用自定义规则的任何移动设备。

下表包含 Exchange ActiveSync 管理的访问级别：

|访问级别|描述|
|----------------|---------------|
|**允许设备访问 Exchange**|在“*允许访问*”状态下，移动设备可以通过 Exchange ActiveSync 进行同步，并连接到 Exchange 服务器以检索电子邮件和管理日历、联系人、任务和批注。 只要设备符合你在 Exchange 中配置的 Exchange ActiveSync 邮箱策略，就可继续执行此操作，除非 Exchange 管理员阻止了用户或特定移动设备。|
|**阻止设备访问 Exchange**|在“*阻止访问*”状态下，移动设备会受阻，不允许连接到 Exchange 服务器。 设备会收到 HTTP 403 禁止错误。 用户会收到来自 Exchange 服务器的电子邮件，告知他们已阻止移动设备访问其邮箱。 此邮件不能处于阻止的移动设备上。 可以使用“**设置用户通知**”任务为此邮件添加自定义的文本，来为其设备被阻止的用户提供说明。 |
|**隔离这些设备，以便以后可允许或阻止其访问**|某移动设备被隔离时，允许该移动设备连接到 Exchange 服务器。 但是，只授予它对数据的有限访问权限。 用户可以向其自己的日历、联系人、任务和批注文件夹中添加内容，但是服务器不允许设备检索任何来自用户邮箱的内容。 用户会收到一封单独的电子邮件，指示移动设备被隔离。 此邮件发送至设备以及用户的邮箱。 可以使用“**设置用户通知**”任务为此邮件添加自定义的文本，来为其设备被隔离的用户提供说明。|

访问策略是**默认规则**与适用于连接到 Exchange 的所有移动设备的**平台例外**的组合。 下表列出了一些示例的访问策略。

|访问策略|说明|
|-------------------|---------------|
|允许列表|可以使用“*允许列表*”授予对已知设备列表的访问权限，并限制其他设备的访问权限。 若要执行此操作，必须创建自定义规则，以便允许的设备平台能访问用户的邮箱。 一旦你创建了此类规则，你就必须设置默认访问规则以阻止或隔离所有其他的设备。 若要将新设备添加到允许列表，请创建新的自定义规则。|
|阻止列表|你可以使用“阻止列表”在默认情况下对所有设备授予访问权限，但对于你不想让其访问你的组织的设备集，则可阻止其进行访问。 通过创建自定义规则来创建一个阻止列表，以阻止你不想让其与组织的邮箱进行同步的设备平台。 我们建议将默认规则设置为允许访问现有规则未明确阻止的所有设备。 若要将新设备或设备集添加到阻止列表，请创建新的自定义规则。|
|允许和阻止相混合|除了创建允许和阻止列表外，你还可以在新的移动设备引入到组织中而你需要对其进行评估时将其隔离。 例如，如果你有组织中所不允许的移动设备的阻止列表，以及组织中所允许的移动设备的允许列表，则你可以将默认规则设置为隔离。 所有其他设备会自动隔离。 这使你可以在新设备引入到组织中时发现它们，并决定是否要将它们添加到允许或阻止列表。|
下面的过程描述如何创建自定义规则。

## <a name="create-a-default-access-rule"></a>创建默认访问规则

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“**策略**”&gt;“**Exchange ActiveSync**”。

2.  在“**默认规则**”列表中，选择要应用于规则或个人例外未涵盖的所有移动设备的访问规则。 选择“保存”。

下面的过程描述如何创建自定义规则：

## <a name="create-a-custom-access-rule"></a>创建自定义访问规则

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“**策略**”&gt;“**Exchange ActiveSync**”。

2.  在“**平台例外**”列表中，选择“**添加规则**”，然后创建自定义规则。 选择“保存”。
