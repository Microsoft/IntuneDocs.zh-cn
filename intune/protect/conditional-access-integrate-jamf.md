---
title: 将 Jamf Pro 与 Microsoft Intune 集成来满足符合性要求
titleSuffix: Microsoft Intune
description: 通过将 Microsoft Intune 符合性策略与 Azure Active Directory 条件访问相结合，可帮助集成由 Jamf 管理的设备并确保安全。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09566e314f801c0de3f371384126cf672403b6a3
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306656"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>将 Jamf Pro 与 Intune 集成以实现合规

适用于：Azure 门户中的 Intune

你的组织使用 [Jamf Pro](https://www.jamf.com) 管理 macOS 设备时，可以将 Microsoft Intune 符合性策略用于 Azure Active Directory (Azure AD) 条件访问，从而确保组织中的设备满足符合性要求，然后才能访问公司资源。 本文将帮助你配置 Jamf 与 Intune 的集成。

将 Jamf Pro 与 Intune 集成时，可以通过 Azure AD 将 macOS 设备中的清单数据与 Intune 同步。 Intune 的符合性引擎随后会分析清单数据以生成报表。 Intune 的分析与有关设备用户的 Azure AD 标识的智能结合使用，以通过条件访问来驱动强制执行。 符合条件访问策略的设备可以访问受保护的公司资源。

配置集成后，将在使用 Jamf 管理的设备上[配置 Jamf 和 Intune 以使用条件访问强制实现符合性](conditional-access-assign-jamf.md)。  


## <a name="prerequisites"></a>必备条件

### <a name="products-and-services"></a>产品和服务
需要满足以下要求才能通过 Jamf Pro 配置条件访问：

- Jamf Pro 10.1.0 或更高版本
- [适用于 macOS 的公司门户应用](https://aka.ms/macoscompanyportal)
- 带有 OS X 10.11 Yosemite 或更高版本的 macOS 设备

### <a name="network-ports"></a>网络端口
<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
要使 Jamf 和 Intune 正确集成，应可访问以下端口： 
- **Intune**：端口 443
- **Apple**：端口 2195、2196 和 5223（向 Intune 推送通知）
- **Jamf**：端口 80 和 5223

若要允许 APNS 在网络上正常运行，还必须启用与以下位置的传出连接，以及来自以下位置的重定向：
- 通过所有客户端网络中的 TCP 端口 5223 和 443 的 Apple 17.0.0.0/8 块。   
- Jamf Pro 服务器中的端口 2195 和 2196。  

有关这些端口的详细信息，请参阅以下文章：  
- [Intune 网络配置要求和带宽](../fundamentals/network-bandwidth-use.md)。
- jamf.com 上的 [Jamf Pro 使用的网络端口](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro)。
- support.apple.com 上的 [Apple 软件产品使用的 TCP 和 UDP 端口](https://support.apple.com/HT202944)


## <a name="connect-intune-to-jamf-pro"></a>将 Intune 连接到 Jamf Pro

若要将 Intune 与 Jamf Pro 连接：

1. 在 Azure 中创建新的应用程序。
2. 启用 Intune 以与 Jamf Pro 集成。
3. 在 Jamf Pro 中配置条件访问。

## <a name="create-an-application-in-azure-active-directory"></a>在 Azure Active Directory 中创建应用程序

1. 在 [Azure 门户](https://portal.azure.com)中转到“Azure Active Directory” > “应用注册”，然后选择“新建注册”    。 

2. 在“注册应用程序”  页上，指定以下详细信息：
   - 在“名称”  部分中，输入一个有意义的应用程序名称，例如“Jamf 条件访问”  。
   - 对于“支持的帐户类型”  部分，选择“任何组织目录中的帐户”  。 
   - 对于“重定向 URI”  ，保留 Web 的默认值，然后指定 Jamf Pro 实例的 URL。  

3. 选择“注册”  创建应用程序并打开新应用的“概述”页  。  

4. 在应用的“概述”  页上，复制“应用程序(客户端)ID”  值并记录该值以供将来使用。 后续过程中将需要此值。  

5. 选择“管理”下的“证书和密码”   。 选择“新建客户端密码”  按钮。 输入“说明”中的值，选择“截止期限”的任何选项，然后选择“添加”    。

   > [!IMPORTANT]  
   > 在离开此页面之前，复制客户端密码的值并记录该值以供将来使用。 后续过程中将需要此值。 此值不再可用，无需重新创建应用注册。  

6. 选择“管理”下的“API 权限”   。 选择现有权限，然后选择“删除权限”  以删除这些权限。 添加新权限时有必要删除所有现有权限，且应用程序仅在具有单个所需权限时正常运行。  

7. 若要分配新权限，请选择“添加权限”  。 在“请求获取 API 权限”  页上，选择“Intune”  ，然后选择“应用程序权限”  。 仅选中 update_device_attributes  对应的复选框。  

   选择“添加权限”  以保存此配置。  

8. 在“API 权限”  页上，选择“为 \<你的租户> 授予管理员许可”，然后选择“是”  。  成功注册应用后，API 权限应显示如下：![成功的权限](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   将完成 Azure AD 中的应用注册过程。


    > [!NOTE]
    > 如果客户端密码过期，则必须在 Azure 中创建一个新的客户端密码，然后更新 Jamf Pro 中的条件访问数据。 Azure 允许同时具有旧密钥和新密钥，以防止服务中断。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>启用 Intune 以与 Jamf Pro 集成

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后转到“Microsoft Intune” > “设备符合性” > “合作伙伴设备管理”    。

2. 通过将上一步骤期间保存的应用程序 ID 粘贴到“Jamf Azure Active Directory 应用 ID”字段来启用 Jamf 的符合性连接器  。

3. 选择“保存”  。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>在 Jamf Pro 中配置 Microsoft Intune 集成

1. 在 Jamf Pro 中，导航到“全局管理”   > “条件访问”  。 单击“macOS Intune 集成”选项卡上的“编辑”按钮   。

2. 选中“启用适用于 macOS 的 Intune 集成”复选框  。

3. 提供在 Azure AD 中创建应用时保存的有关 Azure 租户的必要信息，包括“位置”、  “域名”、  “应用程序 ID”  和“客户端密码”的值  。  

4. 选择“保存”  。 Jamf Pro 将测试设置并验证是否成功。

## <a name="set-up-compliance-policies-and-register-devices"></a>设置符合性策略并注册设备

配置 Intune 和 Jamf 之间的集成后，需要[将符合性策略应用到 Jamf 托管的设备](conditional-access-assign-jamf.md)。


## <a name="disconnect-jamf-pro-and-intune"></a>断开 Jamf Pro 和 Intune 的连接 

如果不再使用 Jamf Pro 管理组织中的 Mac 并希望用户由 Intune 管理，则必须删除 Jamf Pro 和 Intune 之间的连接。 使用 Jamf Pro 控制台删除连接。 

1. 在 Jamf Pro 中，转到“全局管理”   > “条件访问”  。 在“macOS Intune 集成”  选项卡上，选择“编辑”  。
2. 清除“启用适用于 macOS 的 Intune 集成”  复选框。
3. 选择“保存”  。 Jamf Pro 将配置发送到 Intune，并且将终止集成。
4. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。 转到“Microsoft Intune”   > “设备合规性”   > “合作伙伴设备管理”  以验证现在状态是否“已终止”  。 

   > [!NOTE]
   > 组织的 Mac 设备将在控制台中显示的日期（3 个月）删除。 

## <a name="next-steps"></a>后续步骤

- [将符合性策略应用到 Jamf 管理的设备](conditional-access-assign-jamf.md)
- [Jamf 向 Intune 发送的数据](data-jamf-sends-to-intune.md)
