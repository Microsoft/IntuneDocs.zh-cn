---
title: Microsoft Intune 中的 Windows 信息保护设置
titleSuffix: ''
description: 了解可用于管理 Windows 信息保护的 Microsoft Intune 设置。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 1/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1ec649134d4c3d28c99863aa3f04d2a89d4e029f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置 Windows 信息保护

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

随着企业中员工拥有的设备的增加，通过应用和服务（如电子邮件、社交媒体和公共云）发生的意外数据泄露的风险也在增加，这是不受企业控制的。 例如，某位员工从个人电子邮件帐户发送最新的工程图片、将产品信息复制并粘贴到推文，或将正在进行的销售报表保存到公有云存储。

“Windows 信息保护”有助于防范这种潜在的数据泄露，而不会干扰员工体验。 它还有助于防范企业应用和数据在企业自有设备和员工带到工作中的个人设备上的意外数据泄露，而无需对你的环境或其他应用进行更改。

此 Intune 策略管理由 Windows 信息保护功能保护的应用、企业网络位置、保护级别和加密设置的列表。

>[!NOTE]
> 若要将 Windows 10 公司门户应用与 Windows 信息保护结合使用，必须在“免除”的 Windows 信息保护模式下添加公司门户应用。 

### <a name="next-steps"></a>后续步骤
有关更多信息，请参阅：
-  [使用 Windows 信息保护来保护企业数据](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。
- [使用 Microsoft Intune 经典控制台创建 Windows 信息保护 (WIP) 策略](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune)
- [使用 Microsoft Intune Azure 门户创建具有 MDM 的 Windows 信息保护 (WIP) 策略](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure)
- [使用 Microsoft Intune Azure 门户创建具有 MAM 的 Windows 信息保护 (WIP) 策略](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)
