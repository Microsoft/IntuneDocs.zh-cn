---
title: "部署应用"
description: "本主题说明在开始使用 Intune 部署应用之前需要了解的概念。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 13c4046ed431dc25bda9a2facc59dbcb6d3e5ab5
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="deploy-apps-with-microsoft-intune"></a>使用 Microsoft Intune 部署应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题说明一些在开始使用 Microsoft Intune 部署应用之前需要了解的概念。


## <a name="app-deployment-actions"></a>应用部署操作
在部署应用时，你可以从以下部署操作中进行选择:

-   **所需的安装** – 应用安装在设备上，无需用户干预。

    > [!TIP]
    > 对于未处于监督模式的 iOS 设备，以及对于所有 Android 设备，用户在安装应用之前必须接受应用付费。
    >
    >  如果用户卸载部署为必需安装的应用，则 Intune 将在下一清单周期之后自动重新安装该应用，该周期通常为 7 天。

-   **可用安装** – 应用显示在公司门户中，最终用户可根据需要安装。

-   **“卸载”** – 应用从设备上卸载。

-   **不适用** – 应用不在公司门户中显示，并且未安装到任何设备。

#### <a name="understand-which-deployment-actions-are-available-for-each-installer-type"></a>了解可用于每种安装程序类型的部署操作

|安装程序类型|“必需安装”|“可用安装”|卸载|“不适用”|
|------------------|--------------------|---------------------|-------------|------------------|
|Windows 应用包（已部署到用户组）|是|是|是|是|
|Windows 应用包（部署到设备组）|是|否|是|是|
|移动设备的应用包（已部署到用户组）|是|是|是|是|
|移动设备的应用包（已部署到设备组）|是|否|是|是|
|Windows 安装程序（已部署到用户组）|否|是|否|是|
|Windows 安装程序（已部署到设备组）|是|否|是|是|
|外部链接（已部署到用户组）|否|是|否|是|
|外部链接（已部署到设备组）|否|否|否|否|
|来自应用商店的托管 iOS 应用程序（已部署到用户组）|是|是|是|是|
|来自应用商店的托管 iOS 应用程序（已部署到设备组）|是|否|是|是|
> [!TIP]
> 部署应用时，如果你同时选择用户和设备组，你只能将应用作为**可用安装**进行部署。

## <a name="deployment-conflicts"></a>部署冲突
如果某一设备收到具有相同部署操作的两个部署，则适用以下规则：

-   对设备组的部署优先于对用户组的部署。 但是，如果使用“**可用**”部署操作将应用部署到用户组，并且使用“**不适用**”部署操作将同一应用部署到设备组，则在公司门户中向用户提供此应用以供安装。

-   所有安装操作优先于卸载操作。

-   如果一台设备同时收到所需安装和可用安装，则合并两个操作。 换言之，用户可以在所需安装开始之前从公司门户安装可用的应用。


## <a name="next-steps"></a>后续步骤

了解如何[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)。

