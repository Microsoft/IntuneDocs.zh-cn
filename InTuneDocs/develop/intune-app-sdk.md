---
title: "Intune App SDK 的优点 |Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 952cfa4f23f8ba080ce53f6785baceb8a0a367c6
ms.openlocfilehash: ce8fa172c68fed7a1398cd5b1263ac970b87559b


---

# Intune App SDK 概述
Intune 应用 SDK 适用于 iOS 和 Android 平台，并允许通过 Microsoft Intune 使用移动应用管理功能。 此外，我们还尽量减少开发人员需要进行的代码更改次数。 你会发现你可以在不改变应用行为的情况下启用大部分 SDK 功能。 为了增强最终用户和 IT 管理员体验，你可以利用我们的 API，针对需要应用参与的功能来自定义应用行为。 你启用应用后，IT 管理员即可将策略部署到 Intune 托管应用，并利用这些功能保护其公司数据。

## 常规功能

### 控制用户移动公司文档的能力
IT 管理员可以控制 Intune 托管应用中公司文档的文件迁移。 例如，他们可以部署策略，禁止文件备份应用将公司数据备份到云。

### 配置剪贴板限制
IT 管理员可以配置 Intune 托管应用中的剪贴板行为。 例如，他们可以部署策略，让最终用户无法使用剪贴板从 Intune 托管应用进行剪切/复制并粘贴到非托管应用。

### 配置屏幕捕获限制
IT 管理员可以阻止用户在显示 Intune 托管应用时捕获屏幕。 应用此限制将阻止捕获和发布公司机密内容。 此功能仅适用于 Android 设备。

### 对已保存数据强制执行加密
IT 管理员可以强制执行策略，确保对应用保存到设备的数据进行加密。

### 远程擦除公司数据
当从 Microsoft Intune 取消注册设备时，IT 管理员可远程擦除 Intune 托管应用上的公司数据。 此功能基于标识，将仅删除与公司标识相关的最终用户文件。 若要执行此操作，此功能要求应用的参与。 应用可指定基于用户设置应进行擦除的标识。 在应用没有指定这些用户设置的情况下，默认行为是擦除应用程序目录，并通知最终用户已删除公司资源访问权限。

### 强制使用托管浏览器
从 Intune 托管应用内打开链接时，IT 管理员可以强制使用托管浏览器。 使用 Microsoft Intune 托管浏览器有助于确保电子邮件（位于 Intune 托管的邮件客户端中）中显示的链接保持在 Intune 托管应用的域中。

### 强制执行 PIN 策略
启动 Intune 托管应用时，IT 管理员可以强制执行 PIN 策略。 此策略有助于确保将其设备注册到 Microsoft Intune 的最终用户与应用启动者是同一个人。 最终用户配置其 PIN 时，Intune App SDK 使用 Azure Active Directory 验证最终用户的凭据是否为设备注册凭据

### 要求用户先输入凭据才能启动应用
IT 管理员可以要求用户输入其凭据才能启动 Intune 托管应用。 Intune 应用 SDK 使用 Azure Active Directory 提供单一登录体验，其中一旦输入凭据就将在后续登录中重用该凭据。 我们还支持通过[与 Azure Active Directory 联合](https://msdn.microsoft.com/library/azure/jj679342.aspx)的标识管理解决方案进行身份验证。

### 检查设备运行状况和合规性
在最终用户访问 Intune 托管应用之前，IT 管理员可以检查设备的运行状况及其是否符合公司策略。 在 iOS 平台上，此策略将检查设备是否已越狱。 在 Android 平台上，此策略将检查设备是否已获得 root 权限。

## 预览功能
Microsoft Intune App SDK 包括多项处于“预览”状态的功能。 你可以开始与预览 API 集成，但仅用于测试目的。 请注意，这些预览功能将添加到现有方案，而不是替换现有方案。

### Microsoft Intune App SDK 多身份支持
多身份支持功能允许策略托管（企业）帐户和非托管（个人）帐户在单个应用中共存。

### 多身份方案示例
许多用户在 iOS 和 Android 的 Outlook 应用中同时配置公司和个人电子邮件帐户。 当用户访问其公司帐户中的数据时，IT 管理员必须确信将应用 MAM 策略管理。 但是，当用户访问个人电子邮件帐户时，该数据应在 IT 管理员的控制之外。 Microsoft Intune 在应用程序中仅针对公司帐户实行该管理策略，从而实现此目的。 多身份功能有助于解决同时支持个人和工作帐户的设备和应用带给组织的数据保护问题。

### 如何支持多身份
预览 API 允许你指定特定数据操作（如剪贴板操作和文件操作）的用户主体名称 (UPN)。 Microsoft Intune App SDK 使用该 UPN 来匹配对用于将设备注册到 Microsoft Intune 服务的 UPN 所进行的调用。 如果 UPN 匹配，则将该调用视为“公司数据”调用并保护数据；如果 UPN 不匹配，则将该调用视为“个人数据”调用且不保护数据。

### 无需设备注册的应用管理
许多用户使用个人设备，他们希望在不为其个人设备注册移动设备管理 (MDM) 产品的情况下查看和使用公司数据。 由于 MDM 注册要求对设备的全局控制权，而用户对于将其个人设备的全局控制权交给公司有所顾虑。

无需设备注册的应用管理允许 Microsoft Intune 服务将 MAM 策略直接部署到应用，而不依赖于 MDM 通道来部署策略。 由于不需要 MDM 通道，所以无需 MDM 注册。




<!--HONumber=Sep16_HO2-->


