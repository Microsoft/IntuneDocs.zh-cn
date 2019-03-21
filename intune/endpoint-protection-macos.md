---
title: 在 Microsoft Intune 中添加对 macOS 的终结点保护 - Azure | Microsoft Docs
description: 在 macOS 设备上，使用网关守卫来确定安装应用的位置，包括 Mac App Store。 此外，还可以使用 Microsoft Intune 启用或配置防火墙，以允许使用特定应用、阻止使用特定应用、使用隐藏模式，甚至阻止特定类型的传入连接。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2c3a33b996a68263550fc05d3af853c263c930a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565924"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Intune 中的 macOS 终结点保护设置

本文介绍可为运行 macOS 的设备配置的终结点保护设置。 包括对这些设备进行网关守卫和防火墙设置，并且可以在 Microsoft Intune 中使用设备配置文件进行配置。

## <a name="gatekeeper"></a>网关守卫

- **允许使用从以下位置下载的应用**：根据应用的下载来源对应用进行限制。 其目的是保护设备免受恶意软件侵扰，仅允许使用来自信任来源的应用。 可用选项： 
  - **Mac App Store**
  - **Mac App Store 和已识别的开发人员**
  - **任何来源**

- **用户可以重写网关守卫**：可以防止用户重写网关守卫设置，并能防止用户通过按住 Control 键并单击安装应用。 启用时，用户可以通过按住 Control 键并单击安装任何应用。

## <a name="firewall"></a>防火墙

使用防火墙按每个应用程序（而不是按每个端口）控制连接。 按每个应用程序进行设置能更轻松地享受防火墙保护的优点。 它还有助于防止某些应用意外占用为合理应用打开的网络端口。

- **使用防火墙控制每个应用的连接，避免未经授权的网络访问设备。**
  - **防火墙**：启用防火墙，配置环境对传入连接的处理方式。
  - **传入连接**：阻止所有传入连接，DHCP、Bonjour 和 IPSec 等基本 Internet 服务需要的连接除外。 此功能还会阻止所有共享服务，例如文件共享和屏幕共享。 如果需要使用共享服务，请让此设置保持“未配置”状态。

- **允许或阻止特定应用的传入连接**
  - **允许的应用**：选择显式允许接收传入连接的应用。
  - **阻止的应用**：选择应阻止传入连接的应用。
  - **隐藏模式**：若要防止计算机对探测请求做出响应，请启用隐藏模式。 设备会继续回应已授权应用的传入请求。 意外的请求将被忽略，如 ICMP (ping)。
