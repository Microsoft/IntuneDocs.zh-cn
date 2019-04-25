---
title: 将 Jamf Pro 与 Microsoft Intune 集成来满足符合性要求
titleSuffix: Microsoft Intune
description: 通过将 Microsoft Intune 符合性策略与 Azure Active Directory 条件访问相结合，可确保由 Jamf 管理的设备的安全。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
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
ms.openlocfilehash: 57527d0b1825d0e8d3fefb63d1b960ab3fb5c676
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508117"
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

1. 在 [Azure 门户](https://portal.azure.com)中转到“Azure Active Directory” > “应用注册”。
2. 选择“+新应用程序注册”。
3. 输入显示名称，如 Jamf 条件访问。
4. 选择“Web 应用/API”。
5. 使用 Jamf Pro 实例 URL 指定登录 URL。
6. 选择“创建”。 应用程序已创建，且门户提供应用程序详细信息。
7. 保存新应用程序的应用程序 ID 的副本。 在后续步骤中指定此 ID。 接下来，选择“设置”，并转到“API 访问” > “密钥”。
8. 在“密钥”窗格中，指定“说明”，到期前需要等待的时间，然后选择“保存”以生成应用程序密钥（值）。

   > [!IMPORTANT]
   > 应用程序密钥在此过程中仅显示一次。 请务必将其保存在可以轻松检索到它的地方。

8. 在应用的“设置”窗格上，导航到“API 访问” > “所需权限”。 选择任何现有权限，然后单击“删除”并删除所有权限。 添加新权限时有必要删除现有权限，且应用程序仅在具有单个所需权限时正常运行。  
9. 若要分配新权限，请选择“+添加” > “选择 API” > “Microsoft Intune API”，然后单击“选择”。
10. 在“启用访问权限”窗格，选择“向 Microsoft Intune 发送设备属性”，然后单击“选择”并选择“完成”。
11. 在“所需权限”窗格，选择“授予权限”，然后单击“是”，以向应用程序应用所需权限。

    > [!NOTE]
    > 如果应用程序密钥过期，则必须在 Microsoft Azure 中创建一个新的应用程序密钥，然后更新 Jamf Pro 中的条件访问数据。 Azure 允许同时具有旧密钥和新密钥，以防止服务中断。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>启用 Intune 以与 Jamf Pro 集成

1. 在 [Azure 门户](https://portal.azure.com)中，转到“Microsoft Intune” > “设备符合性” > “合作伙伴设备管理器”。
2. 通过将上一步骤期间保存的应用程序 ID 粘贴到“Jamf Azure Active Directory 应用 ID”字段来启用 Jamf 的符合性连接器。
3. 选择“保存”。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>在 Jamf Pro 中配置 Microsoft Intune 集成

1. 在 Jamf Pro 中，导航到“全局管理” > “条件访问”。 单击“Microsoft Intune 集成”选项卡上的“编辑”按钮。
2. 选中“启用 Microsoft Intune 集成”复选框。
3. 提供之前步骤中保存的有关 Azure 租户的必要信息，包括“位置”、“域名”、“应用程序 ID”和“应用程序密钥”。
4. 选择“保存”。 Jamf Pro 将测试设置并验证是否成功。

## <a name="set-up-compliance-policies-and-register-devices"></a>设置符合性策略并注册设备

配置 Intune 和 Jamf 之间的集成后，需要[将符合性策略应用到 Jamf 托管的设备](conditional-access-assign-jamf.md)。



## <a name="next-steps"></a>后续步骤

- [将符合性策略应用到 Jamf 管理的设备](conditional-access-assign-jamf.md)
- [Jamf 向 Intune 发送的数据](data-jamf-sends-to-intune.md)
