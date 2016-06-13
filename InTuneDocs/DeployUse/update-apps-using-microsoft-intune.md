---
# required metadata

title: 更新应用 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 更新应用
Microsoft Intune 可帮助你管理应用更新。 使用本主题中的信息了解在需要新版本时可如何更新应用。

## 如何更新应用
当已部署的应用发布新版本后，Intune 将让你更新和部署应用的更新版本。 你只能用同一应用程序（使用相同的标识符）的更新版本替换部署。 无法使用应用更新来更新具有不同应用包的部署。

> [!IMPORTANT]
> 如果你部署应用时采用的部署操作是 **“所需的安装”** ，但随后又将部署操作更改为 **“可用安装”**，则应用的更新不会自动安装到在更改部署前已安装到设备的应用上。 若要修复此问题，你可以执行以下操作：
> 
> -   让设备的用户前往公司门户，选择已安装的应用，然后对它们单击 **“安装”**。
> -   将部署操作更改为 **“卸载”**，并在卸载应用后，采用 **“可用安装”**的部署操作重新部署应用。

### 若要更新应用程序

1.  在 [Microsoft Intune 管理员控制台](https://manage.microsoft.com)中，单击**应用**&gt;**应用**。

2.  从 **“应用”** 列表，选择要更新的应用，然后单击 **“编辑”**。

3.  在 **“编辑软件”** 向导中，提供应用包的所有新的详细信息。

4.  完成后，请单击“更新” 。

当设备接下来检查可用应用时，应用将自动更新到最新版本。





<!--HONumber=May16_HO2-->


