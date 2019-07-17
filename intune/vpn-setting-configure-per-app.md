---
title: 在 Microsoft Intune 中设置适用于 iOS 设备的每个应用程序 VPN - Azure | Microsoft 文档
description: 查看先决条件，为虚拟专用网络 (VPN) 用户创建组，添加 SCEP 证书配置文件，配置每个应用程序 VPN 配置文件，以及将一些应用分配到 iOS 设备上 Microsoft Intune 中的 VPN 配置文件。 此外，还列出了在设备上验证 VPN 连接的步骤。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dc78f8126e0fa9c65fdbe70cfd909da70391e3e
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884523"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>在 Intune 中为 iOS 设备设置每应用虚拟专用网络 (VPN)

在 Microsoft Intune 中，可以创建和使用分配给应用的虚拟专用网络 (VPN)。 此功能称为“每应用 VPN”。 选择可以在 Intune 托管的设备上使用 VPN 的托管应用。 使用每应用 VPN 时，最终用户可以自动通过 VPN 连接，并有权访问组织资源（例如，文档）。

此功能适用于：

- iOS 9 及更高版本

请参阅 VPN 提供程序文档，查看你的 VPN 是否支持每应用 VPN。

本文介绍如何创建每应用 VPN 配置文件，并将此配置文件分配给应用。 使用这些步骤为最终用户创建无缝的每应用 VPN 体验。 对于支持每应用 VPN 的大多数 VPN，用户打开应用时，它会自动连接到 VPN。

某些 VPN 允许使用每应用 VPN 进行用户名和密码身份验证。 这意味着，用户需要输入用户名和密码才能连接到 VPN。

## <a name="per-app-vpn-with-zscaler"></a>使用 Zscaler 的每应用 VPN

Zscaler Private Access (ZPA) 与 Azure Active Directory (Azure AD) 集成以进行身份验证。 使用 ZPA 时，不需要（本文所述）的[受信任的证书](#create-a-trusted-certificate-profile)或 [SCEP 或 PKCS 证书](#create-a-scep-or-pkcs-certificate-profile)配置文件。 如果为 Zscaler 设置了每应用 VPN 配置文件，请打开其中某个不会自动连接到 ZPA 的关联应用。 相反，用户需要首先登录 Zscaler 应用。 然后，远程访问仅限于关联应用。

## <a name="prerequisites-for-per-app-vpn"></a>每个应用 VPN 的先决条件

> [!IMPORTANT]
> 你的 VPN 供应商可能对每应用 VPN 有其他要求，例如特定硬件或许可。 在 Intune 中设置每个应用 VPN 之前，请务必检查其文档并满足这些先决条件。

为了证明其身份，VPN 服务器提供了设备必须在提示的情况下必须接受的证书。 要确保自动批准证书，请创建包含由证书颁发机构 (CA) 颁发的 VPN 服务器根证书的受信任证书配置文件。 

#### <a name="export-the-certificate-and-add-the-ca"></a>导出证书并添加 CA

1. 在 VPN 服务器上打开管理控制台。
2. 确认 VPN 服务器使用基于证书的身份验证。 
3. 导出受信任的根证书文件。 其扩展名为 .cer，在创建受信任的证书配置文件时添加它。
4. 添加颁发用于对 VPN 服务器进行身份验证的证书的 CA 名称。

    如果该设备提供的 CA 与 VPN 服务器上受信任 CA 列表中的 CA 匹配，则 VPN 服务器可成功对该设备进行验证。

## <a name="create-a-group-for-your-vpn-users"></a>为 VPN 用户创建组

在 Azure Active Directory (Azure AD) 中为使用每应用 VPN 的用户或设备创建组或选择现有组。 要创建新组，请参阅[添加组以组织用户和设备](groups-add.md)。

## <a name="create-a-trusted-certificate-profile"></a>创建受信任的证书配置文件

将 CA 颁发的 VPN 服务器根证书导入到 Intune 中创建的配置文件中。 受信任的证书配置文件指示 iOS 设备自动信任 VPN 服务器提供的 CA。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置” > “配置文件” > “创建配置文件”    。
3. 输入以下属性：
    - **名称**
    - **描述**
    - **平台**：选择“iOS”  。
    - **配置文件类型**：选择“受信任的证书”  。
4. 选择文件夹图标，浏览到从 VPN 管理控制台导出的 VPN 证书（.cer 文件）。 
5. 选择“确定” > “创建”   。

    ![在 Microsoft Intune 中为 iOS 设备创建受信任的证书配置文件](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>创建 SCEP 或 PKCS 证书配置文件

受信任的根证书配置文件允许设备自动信任 VPN 服务器。 SCEP 或 PKCS 证书提供 iOS VPN 客户端到 VPN 服务器的凭据。 该证书允许设备在不提示用户名和密码的情况下以静默方式进行身份验证。 

要配置和分配客户端身份验证证书，请参阅以下某篇文章：

- [使用 Intune 配置和管理 SCEP 证书](certificates-scep-configure.md)
- [使用 Intune 配置和管理 PKCS 证书](certficates-pfx-configure.md)

请确保配置用于客户端身份验证的证书。 可以直接在 SCEP 证书配置文件中设置该证书（“扩展密钥用法”列表 >“客户端身份验证”）   。 对于 PKCS，请在证书颁发机构 (CA) 的证书模板中设置客户端身份验证。

![在 Microsoft Intune 中创建 SCEP 证书配置文件，包括主题名称格式、密钥用法、扩展密钥用法等](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>创建每个应用 VPN 配置文件

VPN 配置文件包含附带客户端凭据的 SCEP 或 PKCS 证书、VPN 的连接信息以及每应用 VPN 标志，用于启用供 iOS 应用程序使用的每应用 VPN 功能。

1. 在 Intune 中，选择“设备配置” > “配置文件” > “创建配置文件”     。 
2. 输入以下属性： 
    - **名称**
    - **描述**
    - **平台**：选择“iOS”  。
    - **配置文件类型**：选择“VPN”  。
3. 在“连接类型”中，选择你的 VPN 客户端应用  。
4. 选择“基础 VPN”  。 [iOS VPN 设置](vpn-settings-ios.md)列出并介绍了所有设置。 使用每应用 VPN 时，请确保设置列出的以下属性： 
    
    - **身份验证方法**：选择“证书”  。 
    - **身份验证证书**：选择现有 SCEP 或 PKCS 证书 >“确定”  。      
    - **拆分隧道**：选择“禁用”，强制所有流量在 VPN 连接处于活动状态时使用 VPN 隧道  。 

      ![在每应用 VPN 配置文件中，输入连接、IP 地址或 FQDN、身份验证方法以及 Microsoft Intune 中的拆分调优](./media/vpn-per-app-create-vpn-profile.png)

    有关其他设置的信息，请参阅 [iOS VPN 设置](vpn-settings-ios.md)。

5. 选择“自动 VPN” > “自动 VPN 类型” > “每应用 VPN”   

    ![在 Intune 中，将自动 VPN 设置为 iOS 设备上的每应用 VPN](./media/vpn-per-app-automatic.png)

6. 选择“确定” > “确定” > “创建”    。

## <a name="associate-an-app-with-the-vpn-profile"></a>将应用与 VPN 配置文件相关联

添加 VPN 配置文件后，将应用和 Azure AD 组与配置文件关联。

1. 在 **Intune** 中，选择“客户端应用” > “应用”   。
2. 从列表 >“分配” > “添加组”中选择应用   。
3. 在“分配类型”中，选择“需要”或“适用于已注册的设备”    。
4. 选择“包含组” > “选择要包括的组”> 选择（在本文中）[创建](#create-a-group-for-your-vpn-users)的组 >“选择”    。
5. 在“VPN”中，选择（在本文中）[创建](#create-a-per-app-vpn-profile)的每应用 VPN 配置文件  。

    ![在 Microsoft Intune 中将应用分配给每应用 VPN 配置文件](./media/vpn-per-app-app-to-vpn.png)

6. 选择“确定” > “保存”   。

当存在以下所有条件时，在下一个设备签入期间，会删除应用和配置文件之间的关联：

- 通过所需的安装意向来定向应用。
- 配置文件和应用都定向到同一组。
- 从应用分配中删除每个应用 VPN 配置。

当存在以下所有条件时，应用和配置文件之间的关联持续存在，直到用户请求从公司门户重新安装：

- 通过可用的安装意向来定向应用。
- 配置文件和应用都定向到同一组。
- 最终用户从公司门户请求安装应用，导致在设备上安装应用和配置文件。
- 从应用分配中删除或更改每个应用 VPN 配置。

## <a name="verify-the-connection-on-the-ios-device"></a>验证 iOS 设备上的连接

设置每应用 VPN 并将其与应用相关联后，从设备验证连接是否有效。

### <a name="before-you-attempt-to-connect"></a>尝试连接之前请确保满足以下各项

- 确保将上述所有策略部署到同一个组。 否则，每应用 VPN 体验将无法正常运行。
- 如果使用的是 Pulse Secure VPN 应用或自定义 VPN 客户端应用，可以选择使用应用层或数据包层隧道。 针对应用层隧道，将 ProviderType 值设置为 app-proxy，针对数据包层隧道，将其设置为 packet-tunnel    。 请查看 VPN 提供程序文档，确保使用的是正确的值。

### <a name="connect-using-the-per-app-vpn"></a>使用每应用 VPN 进行连接

无需选择 VPN 或键入凭据即可连接，感受“零接触”体验。 “零接触”体验意味着：

- 设备不要求你信任 VPN 服务器。 也就是说，用户看不到“动态信任”对话框  。
- 用户无需键入凭据。
- 用户打开其中某个关联应用时，用户的设备将连接到 VPN。

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>后续步骤

- 若要查看 iOS 设置，请参阅 [Microsoft Intune 中适用于 iOS 设备的 VPN 设置](vpn-settings-ios.md)。
- 要了解 VPN 设置和 Intune 的详细信息，请参阅[在 Microsoft Intune 中配置 VPN 设置](vpn-settings-configure.md)。
