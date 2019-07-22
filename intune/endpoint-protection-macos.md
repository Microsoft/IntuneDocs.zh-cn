---
title: 在 Microsoft Intune 中添加对 macOS 的终结点保护 - Azure | Microsoft Docs
description: 在 macOS 设备上，使用网关守卫来确定安装应用的位置，包括 Mac App Store。 此外，还可以使用 Microsoft Intune 启用或配置防火墙，以允许使用特定应用、阻止使用特定应用、使用隐藏模式，甚至阻止特定类型的传入连接。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d110013c10f0330c0edbbf230c508009fb47b2a6
ms.sourcegitcommit: 11a31cd39b727f2254e2705b07d18924e103bd2e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341315"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Intune 中的 MacOS 终结点保护设置  

本文介绍可为运行 macOS 的设备配置的终结点保护设置。 使用 Intune 中的[endpoint protection](endpoint-protection-configure.md)的 macOS 设备配置文件配置这些设置。  

## <a name="gatekeeper"></a>网关守卫  

- **允许从这些位置下载的应用**  
  限制设备可启动的应用, 具体取决于从何处下载应用。 其目的是保护设备免受恶意软件侵扰，仅允许使用来自信任来源的应用。  

  - 未配置   
  - **Mac App Store**  
  - **Mac App Store 和已识别的开发人员**  
  - **任何来源**  

  **默认值**：未配置  

- **用户可以替代网关守卫**  
  可以防止用户重写网关守卫设置，并能防止用户通过按住 Control 键并单击安装应用。 启用时，用户可以通过按住 Control 键并单击安装任何应用。  
 
  - **未配置**-用户可以通过单击来安装应用。  
  - **阻止**-阻止用户使用控件单击来安装应用。  

  **默认值**：未配置  

## <a name="firewall"></a>防火墙  

使用防火墙按每个应用程序（而不是按每个端口）控制连接。 按每个应用程序进行设置能更轻松地享受防火墙保护的优点。 它还有助于防止某些应用意外占用为合理应用打开的网络端口。  

**常规**
- **防火墙**  
  启用防火墙，配置环境对传入连接的处理方式。  
  - 未配置   
  - **启用**  

  **默认值**：未配置  

- **传入连接**  
  阻止所有传入连接，DHCP、Bonjour 和 IPSec 等基本 Internet 服务需要的连接除外。 此功能还会阻止所有共享服务，例如文件共享和屏幕共享。 如果需要使用共享服务，请让此设置保持“未配置”状态  。  
  - 未配置   
  - **阻止**  

  **默认值**：未配置  

**允许或阻止特定应用的传入连接。**  

  - **允许的应用**  
    选择显式允许接收传入连接的应用。  

  - **阻止的应用**  
    选择应阻止传入连接的应用。  

  - **隐藏模式**  
    若要防止计算机对探测请求做出响应，请启用隐藏模式。 设备会继续回应已授权应用的传入请求。 意外的请求将被忽略，如 ICMP (ping)。  
    - 未配置   
    - **启用**  

    **默认值**：未配置  

## <a name="filevault"></a>FileVault  
有关 Apple FileVault 设置的详细信息, 请参阅 Apple 开发人员内容中的[FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) 。 

- **FileVault**  
  可以在运行 macOS 10.13 和更高版本的设备上通过 FileVault 使用 XTS-AES 128*启用*完整磁盘加密。  
  - 未配置   
  - **启用**  

  **默认值**：未配置  

  - **恢复密钥类型**  
    为设备创建*个人密钥*恢复密钥。 为个人密钥配置以下设置。  

     - **个人恢复密钥的位置**-向用户指定一条简短消息, 说明他们如何检索其个人恢复密钥。 启用 FileVault 时, 此文本将插入用户看到的消息中。  
      
     - **个人恢复密钥轮换**-指定设备的个人恢复密钥将旋转的频率。 您可以选择 "**未配置**" 或 " **1**到**12**个月" 的默认值。  

  - **推迟 FileVault, 直到注销** 
    > [!NOTE]
    > 只有在7月发布完成了几天的推出后, 才支持 FileVault。 在推出完成之前, 如果配置了 FileVault, 则必须将*FileVault*设置为 "注销", 才能**启用**。   

    在用户注销之前, FileVault 将不会启用。在注销或下一次登录时, 系统将提示本地用户或移动帐户用户启用 FileVault。  
    - 未配置   
    - **启用**  
    
    **默认值**：未配置  



    - **注销时禁用提示**  
      禁止提示用户在注销时启用 FileVault。  
      - 未配置   
      - **启用**  

      **默认值**：未配置  

    - **允许绕过的次数**  
      设置用户在需要 FileVault 之前允许用户登录所需的提示的次数。  

      - **未配置**-在允许下次登录之前需要对设备进行加密。  
      -  **1**到**10** -允许用户在需要对设备进行加密之前忽略1到10次的提示。  
      - **无限制, 始终提示**-系统会提示用户启用 FileVault, 但绝不会要求加密。  
 
      **默认值**：未配置  


