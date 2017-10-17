---
title: "配置证书配置文件"
description: "了解如何创建 Intune 证书配置文件。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1cda44d3200d0e0bf09ab4c565fa3475854017f4
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="configure-intune-certificate-profiles"></a>配置 Itune 证书配置文件

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

按照[为 SCEP 配置证书基础结构](configure-certificate-infrastructure-for-scep.md)或[为 PFX 配置基础结构](configure-certificate-infrastructure-for-pfx.md)中所述配置基础结构和证书后，可以创建证书配置文件。 过程如下：

- **任务 1**：导出受信任的根 CA 证书
- **任务 2**创建受信任的证书配置文件
- **任务 3**：创建两种证书配置文件类型中的一种：
  - SCEP 证书配置文件
  - .PFX 证书配置文件

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>**任务 1**：导出受信任的根 CA 证书
将受信任的根证书颁发机构 (CA) 证书从发证 CA 或从信任你的发证 CA 的任何设备中导出为“**.cer**”文件。 不要导出私钥。

设置受信任的证书配置文件时，将导入该证书。

## <a name="task-2-create-trusted-certificate-profiles"></a>**任务 2**创建受信任的证书配置文件
必须在创建受信任的证书配置文件后，才能创建简单证书注册协议 (SCEP) 或 PKCS #12 (.PFX) 证书配置文件。 对于每个移动设备平台，你需要一个受信任的证书配置文件和一个 SCEP 或 .PFX 配置文件。

### <a name="to-create-a-trusted-certificate-profile"></a>创建受信任的证书配置文件

1.  在 [Intune 管理控制台](https://manage.microsoft.com)中，选择“策略”&gt;“添加策略”，然后选择设备平台。 可以为这些设备创建受信任的证书配置文件：

-  Android 4 及更高版本

-  Android for Work

-  iOS 7.1 及更高版本

-  Mac OS X 10.9 及更高版本

-  Windows 8.1 及更高版本

-  Windows Phone 8.1 及更高版本

2.  添加**受信任的证书配置文件**策略。

    了解详细信息：[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  输入所需信息以配置 Android、iOS、Mac OS X、Windows 8.1 或 Windows Phone 8.1 的受信任证书配置文件设置。
4.  在“**证书文件**”设置中，导入你从发证 CA 导出的受信任的根 CA 证书 (.cer file)。 “目标存储”设置仅适用于运行 Windows 8.1 及更高版本的设备并且该设备必须具有多个证书存储。

4.  选择“**保存策略**”。

新的策略将显示在“**策略**”工作区中。 现在你可以进行部署。

> [!NOTE]
>
> Android 和 Android for Work 设备将显示第三方已安装受信任的证书的通知。


## <a name="task-3-create-scep-or-pfx-certificate-profiles"></a>**任务 3**：创建 SCEP 或 .PFX 证书配置文件
创建受信任的 CA 证书配置文件后，为你要使用的各个平台创建 SCEP 或 .PFX 证书配置文件。 创建 SCEP 证书配置文件时，必须为相同平台指定受信任的证书配置文件。 这链接了两个证书配置文件，但仍然必须单独部署各个配置文件。

### <a name="to-create-an-scep-certificate-profile"></a>创建 SCEP 证书配置文件

1.  在 [Intune 管理控制台](https://manage.microsoft.com)中，选择“策略”&gt;“添加策略”，然后选择设备平台。  可以为这些设备创建 SCEP 证书配置文件：

-  Android 4 及更高版本

-  Android for Work

-  iOS 7.1 及更高版本

-  Mac OS X 10.9 及更高版本

-  Windows 8.1 及更高版本

-  Windows Phone 8.1 及更高版本

2.  添加 **SCEP 证书配置文件**策略

    了解详细信息：[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  按照配置文件配置页上的说明配置 SCEP 证书配置文件设置。
    > [!NOTE]
    >
    > 在“使用者名称格式”中选择“自定义”，输入自定义使用者名称格式（仅限 iOS 配置文件）。
    >
    > 自定义格式当前支持的两个变量为 `Common Name (CN)` 和 `Email (E)`。 通过使用这些变量和静态字符串的组合，你可以创建自定义使用者名称格式，如下所示：

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > 在本示例中，管理员创建了使用者名称格式，其中除了使用 `CN` 和 `E` 变量外，还使用了组织单元、组织、位置、省/直辖市/自治区和国家/地区值的字符串。 [CertStrToName 函数](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)列出了受支持的字符串。

4.  选择“**保存策略**”。

新的策略将显示在“**策略**”工作区中。 现在你可以进行部署。

### <a name="to-create-a-pfx-certificate-profile"></a>创建 .PFX 证书配置文件

1.  在 [Intune 管理控制台](https://manage.microsoft.com)中，选择“策略”&gt;“添加策略”，然后选择设备平台。 对于以下各项支持 .PFX 证书：
  - Android 4 及更高版本
  - Android for Work
  - Windows 10 及更高版本
  - Windows Phone 10 及更高版本
  - iOS 8.0 及更高版本）    


2.  添加 **.PFX 证书配置文件**策略。
      了解详细信息：[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。
3.  在策略窗体上输入请求的信息。
4.  选择“**保存策略**”。

新的策略将显示在“**策略**”工作区中。 现在你可以进行部署。

## <a name="deploy-certificate-profiles"></a>部署证书配置文件
部署证书配置文件时，将在设备上安装受信任的 CA 证书配置文件的证书文件。 设备使用 SCEP 或 .PFX 证书配置文件来创建设备需要的证书。

证书配置文件仅安装在运行你创建配置文件时使用的平台的设备上。

-   你可以对用户集或对设备集部署证书配置文件。

    > [!TIP]
    > 若要在设备注册后将证书快速发布到设备，请将证书配置文件部署到用户组（而不是部署到设备组）。 如果部署到设备组，则需要在设备接收策略前进行完整的设备注册。

-   尽管单独部署每个配置文件，但仍需部署受信任的根 CA 和 SCEP 或 .PFX 配置文件。 否则，SCEP 或 .PFX 证书策略将失败。

部署证书配置文件的方法与部署其他 Intune 策略的方法相同：

1.  在“策略”工作区中，选择想要部署的策略，然后选择“管理部署”。
2.  在“管理部署”  对话框中：
    -   **若要部署策略**，选择要部署策略的一个组或多个组，然后选择“**添加**”&gt;“**确定**”。
    -   **若要关闭对话框而不对其部署**，选择“**取消**”。

如果你选择的是已部署的策略，则可以在策略列表的下半部分看到有关部署的详细信息。

### <a name="next-steps"></a>后续步骤

接下来，了解如何使用证书来帮助保护电子邮件、Wi-Fi 和 VPN 配置文件。

-  [使用电子邮件配置文件配置对公司电子邮件的访问](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Microsoft Intune 中的 Wi-Fi 连接](wi-fi-connections-in-microsoft-intune.md)
-  [Microsoft Intune 中的 VPN 连接](vpn-connections-in-microsoft-intune.md)
