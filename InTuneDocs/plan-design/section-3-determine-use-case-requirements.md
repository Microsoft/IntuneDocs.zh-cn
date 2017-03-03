---
title: "确定 Intune 用例场景要求 | Microsoft Docs"
description: "本文有助于确定 Microsoft Intune 仅云实现的 Intune 用例以及子用例场景要求。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: 91b25fe35c6a1f8a554d543ca005cc3b482f22d7


---

# <a name="determine-intune-use-case-scenario-requirements"></a>确定 Intune 用例场景要求

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

此部分将确定对每个用例场景内每个组织组的要求。 完成此过程有助于更好地为其他 Intune 部署规划领域做准备，例如体系结构和设计、载入和推出。 还有助于确定与 Intune 部署项目相关的潜在缺陷和难题。

对于每个用例/子用例场景，以及其关联的组织组和移动设备平台，可能有几套不同的要求。 例如，与“自带设备办公”(BYOD) 用例场景（在此场景下要求的设置限制较低，例如 PIN 4 个字符，允许云备份）相比，你公司的用例场景要求可能需要设备通过一组限制较高的设备设置（例如 PIN 6 个字符，禁用云备份）注册到 Intune 中。

你可能还会有用于公司用例场景的组织组，这些组也有几套不同的要求（例如 PIN 设置、Wi-Fi 或 VPN 配置文件、已部署的应用）。 此外，要求还可以根据移动设备平台的功能（如指纹读取器、电子邮件配置文件）来确定。

下面是一个组织用例场景要求的几个示例，显示了针对每个用例/子用例场景、组织组以及移动设备平台的几套不同的要求。 此外，还可使用下表输入组织的用例要求：

| **用例** | **子用例** | **组** | **设备 OS 平台** | **惠?** |
|:---:|:---:|:---:|:---:|:---:|
| 企业 | 資訊工作者 | 人力资源、财务 | iOS | 安全电子邮件、设备设置、配置文件、应用 |                                                          
| 企业 | 高级管理人员 | 人力资源、财务 | iOS | 安全电子邮件、设备设置、配置文件、应用 |                                                         
| 企业 | Kiosk | 零售 | Android | 设备设置、配置文件、应用 |
| BYOD | 資訊工作者 | 营销、销售 | iOS | 安全电子邮件、设备设置、配置文件、应用 |                                                         
| BYOD | 高级管理人员 | 营销、销售 | iOS | 安全电子邮件、设备设置、配置文件、应用 |

## <a name="examples-of-requirements"></a>要求示例

下面是可在上表所引用的“要求”列使用的几个其他示例：

- **安全电子邮件**
    - Exchange Online/内部部署条件性访问
    - Outlook 应用保护策略
<br></br>
- **设备设置**
    - 具有 4 个、6 个字符的 PIN 设置
    - 限制云备份
<br></br>
- **配置文件**
    - Wi-Fi
    - VPN
    - 电子邮件（Windows 10 移动版）
<br></br>
- **应用**
    - 具有应用保护策略的 Office 365
    - 具有应用保护策略的业务线 (LOB)

## <a name="next-section"></a>下一节

下一节提供[如何开发 Intune 推出计划](section-4-develop-a-rollout-plan.md)的相关指南。



<!--HONumber=Dec16_HO5-->


