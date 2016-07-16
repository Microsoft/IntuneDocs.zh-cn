---
title: "与 Microsoft 云服务和产品的 Intune 集成 | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 49675811-08a3-408f-810b-89552ff404bd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: e58b295bf89e200c7c986902c9b4408d23e67c64


---

# 与 Microsoft 云服务和产品的 Intune 集成

设置 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 之前，请查看本主题以及 [Microsoft Intune 启动前须知](what-to-know-before-you-start-microsoft-intune.md)中列出的其他要求。
##与其他 Microsoft 云服务的集成


[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 与其他 Microsoft 云服务共享一个公用基础。 当你使用同一帐户订阅多个云服务时，那些服务将使用相同 Microsoft Azure AD 基础结构，并且它们是 Azure AD 的租户。 Azure AD 提供 Microsoft 云服务的核心目录和身份管理功能。

详细了解 TechNet 库中的[管理 Azure AD ](http://technet.microsoft.com/library/hh967611.aspx)。

## 与其他 Microsoft 产品的集成
你可以将 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 作为独立的云服务或与其他产品集成的云服务使用。 目前，只有 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 可与 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 直接集成。

将 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 与 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 集成的决定是一个永久选择，要求你从 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 控制台中（而不是从 [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]内）设置移动设备管理机构。 设置了移动设备管理机构后，将无法更改或反转此配置。

当你使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 与 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 时，不要使用 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 来管理 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]，而是改为使用 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 控制台。 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 仍会在 Azure 中使用其云存储以托管你部署到使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 管理的设备的软件。

有关详细信息，请参阅 [!INCLUDE[cm5short](../includes/cm5short_md.md)] SP1 文档中的[使用 Configuration Manager 和 Microsoft Intune 管理移动设备](http://msdn.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10)。

### 另请参阅
[启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=Jun16_HO4-->


