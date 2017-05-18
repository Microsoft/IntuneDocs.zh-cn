---
title: "更新应用 | Microsoft Docs"
description: "使用本主题中的信息了解在需要新版本时如何更新应用。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: 824605544487c987c8726e0efe91d06a597fadb2


---

# <a name="update-apps-using-microsoft-intune"></a>使用 Microsoft Intune 更新应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可帮助你管理应用更新。 使用本主题中的信息了解在需要新版本时如何更新应用。

## <a name="how-to-update-apps"></a>如何更新应用
当已部署的应用发布新版本后，Intune 将让你更新和部署应用的更新版本。 你只能用同一应用（具有相同的标识符）的更新版本替换部署。 无法使用应用更新来更新具有不同应用包的部署。

### <a name="app-identifiers"></a>应用标识符
应用标识符是唯一标识应用的属性。 无法安装具有相同标识符的应用的多个副本。 以下是应用标识符的一些示例：

- **iOS** - 捆绑 ID（例如：com.microsoft.excel）
- **Android** - 程序包 ID（例如：com.microsoft.excel）
- **Windows Phone** -（xap 安装程序）使用产品 ID (GUID)
- **Windows** - (appx/appxbundle)，使用程序包全名



> [!IMPORTANT]
> 如果你部署应用时采用的部署操作是 **“所需的安装”** ，但随后又将部署操作更改为 **“可用安装”**，则应用的更新不会自动安装到在更改部署前已安装到设备的应用上。 若要修复此问题，你可以执行以下操作：
>
> -   让设备的用户转到公司门户，选择已安装的应用，然后选择“安装”。
> -   将部署操作更改为 **“卸载”**，并在卸载应用后，采用 **“可用安装”**的部署操作重新部署应用。

### <a name="to-update-an-app"></a>若要更新应用程序

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“应用”&gt;“应用”。

2.  从“应用”列表上，选择要更新的应用，然后选择“编辑”。

3.  在 **“编辑软件”** 向导中，提供应用包的所有新的详细信息。

4.  完成后，选择“更新”。

当设备接下来检查可用应用时，应用将自动更新到最新版本。
对于从应用包（业务线应用）安装的应用，该应用将对必需和可用的部署进行自动升级，只要该应用具有相同的标识符。

对于以链接形式部署到商店的应用，更新将由该应用所属的商店进行管理。



<!--HONumber=Dec16_HO5-->


