---
title: 在 Microsoft Intune 中创建证书配置文件 - Azure | Microsoft Docs
description: 针对所用设备，通过配置 SCEP 或 PKCS 证书环境来添加或创建证书配置文件、导出公共证书、在 Azure 门户中创建配置文件，然后在 Azure 门户中向 Microsoft Intune 证书配置文件 分配 SCEP 或 PKCS
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40d8b3d14411827642661b01929d17e83a5198ad
ms.sourcegitcommit: 4980c094faaca452f8ec8ddded04f47b3229ff38
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65765359"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>在 Microsoft Intune 中为设备配置证书配置文件

可以通过 VPN、Wi-Fi 或电子邮件配置文件为用户提供对公司资源的访问权限。 可以使用证书验证这些连接。 使用证书时，最终用户无需输入用户名和密码即可进行身份验证。

可以使用 Intune 将这些证书分配到你管理的设备。 Intune 支持分配和管理以下证书类型：

- 简单证书注册协议 (SCEP)
- PKCS#12（或 PFX）

每个证书类型均具有其自己的先决条件和基础结构要求。


## <a name="overview"></a>概述

1. 确保设置正确的证书基础结构。 可以使用 [SCEP 证书](certificates-scep-configure.md)和 [PKCS 证书](certficates-pfx-configure.md)。

2. 在每台设备上安装根证书或中间证书颁发机构 (CA) 证书，以便该设备识别 CA 的合法性。 要安装证书，请为每台设备创建并分配受信任的证书配置文件。 分配此配置文件时，Intune 托管的设备会请求并接收根证书。 必须为每个平台创建单独的配置文件。 受信任的证书配置文件可用于以下平台：

    - iOS 8.0 及更高版本
    - macOS 10.11 和更高版本
    - Android 4.0 及更高版本
    - Android Enterprise  
    - Windows 8.1 及更高版本
    - Windows Phone 8.1 及更高版本
    - Windows 10 及更高版本

    > [!NOTE]  
    > 运行专用设备适用的 Android Enterprise 的设备不支持证书配置文件。

3. 创建证书配置文件以便设备请求 1 个将用于对 VPN、Wi-Fi 和电子邮件访问进行身份验证的证书。 下列配置文件类型可用于不同的平台：  

   | 平台     |PKCS 证书|SCEP 证书| PKCS 导入的证书 | 
   |--------------|----------------|----------------|-------------------|
   | Android                | 是    | 是    | 是    |
   | Android Enterprise     | 是    | 是    | 是    |
   | iOS                    | 是    | 是    | 是    |
   | macOS                  |        | 是    | 是    |
   | Windows Phone 8.1      |        | 是    | 是    |
   | Windows 8.1 及更高版本  |        | 是    |        |
   | Windows 10 及更高版本   | 是    | 是    | 是    |

   务必为每个设备平台创建单独的配置文件。 在创建配置文件时，将其与已创建的受信任的根证书配置文件关联。

### <a name="further-considerations"></a>更多注意事项

- 如果没有企业证书颁发机构，则必须创建一个
- 如果使用 SCEP 配置文件，还需配置网络设备注册服务 (NDES) 服务器
- 无论是计划使用 SCEP 配置文件还是 PKCS 配置文件，都需下载并配置 Microsoft Intune 证书连接器


## <a name="step-1-configure-your-certificate-infrastructure"></a>步骤 1：配置证书基础结构

请查看下列主题，在为各类型的证书配置文件配置基础结构方面获取帮助：

- [使用 Intune 配置和管理 SCEP 证书](certificates-scep-configure.md)
- [使用 Intune 配置和管理 PKCS 证书](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>步骤 2：导出受信任的根 CA 证书

将受信任的根证书颁发机构 (CA) 证书从发证 CA 或从信任发证 CA 的任何设备中导出为公共证书 (.cer) 文件。 不要导出私钥 (.pfx)。

设置受信任的证书配置文件时，导入该证书。

## <a name="step-3-create-trusted-certificate-profiles"></a>步骤 3：创建受信任的证书配置文件
必须先创建受信任的证书配置文件，才可创建 SCEP 或 PKCS 证书配置文件。 对于每个设备平台，需要一个受信任的证书配置文件和一个 SCEP 或 PKCS 配置文件。 为每个设备平台创建受信任的证书的步骤是相似的。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “管理” > “配置文件” > “创建配置文件”。
4. 为受信任的证书配置文件输入“名称”和“说明”。
5. 从“平台”下拉列表中，为此受信任证书选择设备平台。 选项包括：

    - **Outlook Web Access (OWA)**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**

6. 从“配置文件类型”下拉列表中，选择“受信任的证书”。
7. 浏览到[步骤 2：导出受信任的根 CA 证书](#step-2-export-your-trusted-root-ca-certificate)中保存的证书，然后选择“确定”。
8. 从以下位置选择受信任证书的**目标存储区**（仅适用于 Windows 8.1 和 Windows 10 设备）：

    - **计算机证书存储区 - 根**
    - **计算机证书存储区 - 中间**
    - **用户证书存储区 - 中间**

9. 完成后，选择“确定”，返回“创建配置文件”窗格，然后选择“创建”。

系统随即创建配置文件，并在列表中显示。 要向组分配此配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。

   >[!NOTE]
   > Android 设备可能会显示第三方已安装受信任的证书的消息。

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>步骤 4：创建 SCEP 或 PKCS 证书配置文件

请查看下列文章，在配置和分配各类型的证书配置文件方面获取帮助：

- [使用 Intune 配置和管理 SCEP 证书](certificates-scep-configure.md)
- [使用 Intune 配置和管理 PKCS 证书](certficates-pfx-configure.md)

创建受信任的证书配置文件后，为要使用的各个平台创建 SCEP 或 PKCS 证书配置文件。 创建 SCEP 证书配置文件时，必须为同一平台输入受信任的证书配置文件。 尽管该步骤链接了两个证书配置文件，但仍须单独分配各个配置文件。

## <a name="next-steps"></a>后续步骤
[分配设备配置文件](device-profile-assign.md)  
[使用 S/MIME 对电子邮件进行签名和加密](certificates-s-mime-encryption-sign.md)  
[使用第三方证书颁发机构](certificate-authority-add-scep-overview.md)

## <a name="see-also"></a>另请参阅

[对与 Microsoft Intune 证书配置文件一起使用的 NDES 配置进行故障排除](https://support.microsoft.com/help/4459540)

[在 Microsoft Intune 中对 SCEP 证书配置文件部署进行故障排除](https://support.microsoft.com/help/4457481)
