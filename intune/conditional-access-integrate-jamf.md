---
title: 将 Jamf Pro 与 Microsoft Intune 集成来满足符合性要求
titleSuffix: Microsoft Intune
description: 通过将 Microsoft Intune 符合性策略与 Azure Active Directory 条件访问相结合，可确保由 Jamf 管理的设备的安全。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cac92aeac895201459e692aae164f51dab10dfb0
ms.sourcegitcommit: ca0f48982e49e90bc14fac5575077445e027f728
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65712635"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>将 Jamf Pro 与 Intune 集成以实现合规

适用于：Azure 门户中的 Intune

如果你的组织使用 [Jamf Pro](https://www.jamf.com) 管理最终用户的 Mac，则可以将 Microsoft Intune 符合性策略用于 Azure Active Directory 条件访问，从而确保组织中的设备满足合规要求。

## <a name="prerequisites"></a>必备条件

需要满足以下要求才能通过 Jamf Pro 配置条件访问：

- Jamf Pro 10.1.0 或更高版本
- [适用于 macOS 的公司门户应用](https://aka.ms/macoscompanyportal)
- 带有 OS X 10.11 Yosemite 或更高版本的 macOS 设备

## <a name="connecting-intune-to-jamf-pro"></a>将 Intune 连接到 Jamf Pro

若要将 Intune 与 Jamf Pro 连接，可通过以下方式实现：

1. 在 Azure 中创建新的应用程序
2. 启用 Intune 以与 Jamf Pro 集成
3. 在 Jamf Pro 中配置条件访问

## <a name="create-an-application-in-azure-active-directory"></a>在 Azure Active Directory 中创建应用程序

1. 在 [Azure 门户](https://portal.azure.com)中转到“Azure Active Directory” > “应用注册”，然后选择“新建注册”。 

2. 在“注册应用程序”页上，指定以下详细信息：
   - 在“名称”部分中，输入一个有意义的应用程序名称，例如“Jamf 条件访问”。
   - 对于“支持的帐户类型”部分，选择“任何组织目录中的帐户”。 
   - 对于“重定向 URI”，保留 Web 的默认值，然后指定 Jamf Pro 实例的 URL。  

3. 选择“注册”以创建应用程序并打开新应用的“概述”页。  

4. 在应用的“概述”页上，复制“应用程序(客户端)ID”值并记录该值以供将来使用。 后续过程中将需要此值。  

5. 选择“管理”下的“证书和密码”。 选择“新建客户端密码”按钮。 输入“说明”中的值，选择“截止期限”的任何选项，然后选择“添加”。

   > [!IMPORTANT]  
   > 在离开此页面之前，复制客户端密码的值并记录该值以供将来使用。 后续过程中将需要此值。 此值不再可用，无需重新创建应用注册。  

6. 选择“管理”下的“API 权限”。  选择现有权限，然后选择“删除权限”以删除这些权限。 添加新权限时有必要删除所有现有权限，且应用程序仅在具有单个所需权限时正常运行。  

7. 若要分配新权限，请选择“添加权限”。 在“请求获取 API 权限”页上，选择“Intune”，然后选择“应用程序权限”。 仅选中 update_device_attributes 对应的复选框。  

   选择“添加权限”以保存此配置。  

8. 在“API 权限”页上，选择“为 Microsoft 授予管理员同意”，然后选择“是”。  

   将完成 Azure AD 中的应用注册过程。


    > [!NOTE]
    > 如果客户端密码过期，则必须在 Azure 中创建一个新的客户端密码，然后更新 Jamf Pro 中的条件访问数据。 Azure 允许同时具有旧密钥和新密钥，以防止服务中断。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>启用 Intune 以与 Jamf Pro 集成

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=20909)，然后转到“Microsoft Intune” > “设备符合性” > “合作伙伴设备管理”。

2. 通过将上一步骤期间保存的应用程序 ID 粘贴到“Jamf Azure Active Directory 应用 ID”字段来启用 Jamf 的符合性连接器。

3. 选择“保存”。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>在 Jamf Pro 中配置 Microsoft Intune 集成

1. 在 Jamf Pro 中，导航到“全局管理” > “条件访问”。 单击“Microsoft Intune 集成”选项卡上的“编辑”按钮。

2. 选中“启用 Microsoft Intune 集成”复选框。

3. 提供在 Azure AD 中创建应用时保存的有关 Azure 租户的必要信息，包括“位置”、“域名”、“应用程序 ID”和“客户端密码”的值。  

4. 选择“保存”。 Jamf Pro 将测试设置并验证是否成功。

## <a name="set-up-compliance-policies-and-register-devices"></a>设置符合性策略并注册设备

配置 Intune 和 Jamf 之间的集成后，需要[将符合性策略应用到 Jamf 托管的设备](conditional-access-assign-jamf.md)。



## <a name="next-steps"></a>后续步骤

- [将符合性策略应用到 Jamf 管理的设备](conditional-access-assign-jamf.md)
- [Jamf 向 Intune 发送的数据](data-jamf-sends-to-intune.md)
