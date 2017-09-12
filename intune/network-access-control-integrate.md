---
title: "网络访问控制与 Intune 集成"
titlesuffix: Azure portal
description: "网络访问控制 (NAC) 与 Intune 集成"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6d75d996f4166fb2a760d1ccb518ca7a228c1a0d
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="network-access-control-nac-integration-with-intune"></a>网络访问控制 (NAC) 与 Intune 集成

Intune 与网络访问控制合作伙伴集成，帮助组织在设备尝试访问本地资源时保护公司数据。

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Intune 和 NAC 解决方案如何帮助保护组织的资源？

NAC 解决方案负责通过 Intune 检查设备注册和符合性状态，以便作出访问控制决策。 如果设备未注册，或已注册但不符合 Intune 设备符合性策略，则设备应重定向到 Intune 进行注册和/或进行设备符合性检查。

### <a name="example"></a>示例

如果设备已注册且符合 Intune，则 NAC 解决方案会允许设备访问公司资源。 例如，当用户尝试访问公司 Wi-Fi 或 VPN 资源时，可以允许或拒绝其访问。

## <a name="nac-and-conditional-access"></a>NAC 和条件性访问

NAC 与条件性访问一起使用可提供访问控制决策。

- 有关更多详细信息，请参阅[通过 Intune 使用条件性访问的常见方式](conditional-access-intune-common-ways-use.md)。

## <a name="how-the-nac-integration-works"></a>NAC 集成的工作原理

下面概述了当与 Intune 集成时 NAC 集成的工作原理，前三个步骤介绍了载入过程。 NAC 解决方案与 Intune 集成后，步骤 4-9 描述正在进行的操作。

![NAC 如何与 Intune 协作](./media/ca-intune-common-ways-2.png)

1.  向 Azure Active Directory (AAD) 注册 NAC 伙伴解决方案，并为 Intune NAC API 授予委派权限。

2.  通过包括 Intune 发现 URL 在内的适当设置来配置 NAC 伙伴解决方案。

3.  配置 NAC 伙伴解决方案以进行证书身份验证。

4.  用户连接到公司 Wi-Fi 访问点，或者提出 VPN 连接请求。

5.  NAC 伙伴解决方案将设备信息转发给 Intune，并询问 Intune 设备注册和符合性状态。

6.  如果设备不符合或未注册，NAC 伙伴解决方案将指示用户注册或修复设备符合性。

7.  设备尝试重新验证其符合性和/或注册状态。

8.  设备已注册且符合后，NAC 伙伴解决方案将从 Intune 获取状态。

9.  成功建立的连接将允许设备访问公司资源。

## <a name="next-steps"></a>后续步骤

-   [将 Cisco ISE 与 Intune 集成](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)

-   [将 Citrix NetScaler 与 Intune 集成](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)

-   [将 HP Aruba Clear Pass 与 Intune 集成](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757)
