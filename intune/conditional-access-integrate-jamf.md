---
title: 将 Jamf Pro 与 Microsoft Intune 集成来满足符合性要求
titlesuffix: ''
description: 通过将 Microsoft Intune 符合性策略与 Azure Active Directory 条件访问相结合，可确保由 Jamf 管理的设备的安全。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e936ecd4ce6a9b0fa447ecfe8e45e04a78999a2b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185009"
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

可以通过以下方式将 Intune 与 Jamf Pro 连接：

1. 在 Azure 中创建新的应用程序
2. 启用 Intune 以与 Jamf Pro 集成
3. 在 Jamf Pro 中配置条件访问

## <a name="create-a-new-application-in-azure-active-directory"></a>在 Azure Active Directory 中创建新的应用程序

1. 打开“Azure Active Directory” > “应用注册”。
2. 单击“+新应用程序注册”。
3. 输入显示名称，如 Jamf 条件访问。
4. 选择“Web 应用/API”。
5. 使用 Jamf Pro 实例 URL 指定登录 URL。
6. 单击“创建应用程序”。
7. 保存新创建的“应用程序 ID”，然后打开“设置”并导航到”API 访问” > “密钥”以创建新的应用程序密钥。 输入描述、过期之前的时间，然后保存该应用程序密钥。

   > [!IMPORTANT]
   > 应用程序密钥在此过程中仅显示一次。 请务必将其保存在可以轻松检索到它的地方。

8. 打开“设置”，然后导航到“API 访问” > “所需权限”，删除所有权限。

   > [!NOTE]
   > 添加新的必要权限。 应用程序必须具有单个必需权限才能正常工作。

9. 选择“Microsoft Intune API”，然后单击“选择”。
10. 选择“将设备属性发送到 Microsoft Intune”，然后单击“选择”。
11. 保存应用程序的必需权限后，单击“授予权限”按钮。

    > [!NOTE]
    > 如果应用程序密钥过期，则必须在 Microsoft Azure 中创建一个新的应用程序密钥，然后更新 Jamf Pro 中的条件访问数据。 Azure 允许同时具有旧密钥和新密钥，以防止服务中断。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>启用 Intune 以与 Jamf Pro 集成

1. 在 Microsoft Azure 门户中，打开“Microsoft Intune” > “设备符合性” > “合作伙伴设备管理器”。
2. 通过将应用程序 ID 粘贴到 Jamf Azure Active Directory 应用程序 ID 字段来启用 Jamf 的符合性连接器。
3. 单击 **“保存”**。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>在 Jamf Pro 中配置 Microsoft Intune 集成

1. 在 Jamf Pro 中，导航到“全局管理” > “条件访问”。 单击“Microsoft Intune 集成”选项卡上的“编辑”按钮。
2. 选中“启用 Microsoft Intune 集成”复选框。
3. 提供之前步骤中保存的有关 Azure 租户的必要信息，包括“位置”、“域名”、“应用程序 ID”和“应用程序密钥”。
4. 单击 **“保存”**。 Jamf Pro 将测试设置并验证是否成功。

## <a name="set-up-compliance-policies-and-register-devices"></a>设置符合性策略并注册设备

完成 Intune 和 Jamf 之间的集成配置后，需要[将符合性策略应用到 Jamf 托管的设备](conditional-access-assign-jamf.md)。

## <a name="information-shared-from-jamf-pro-to-intune"></a>从 Jamf Pro 共享到 Intune 的信息

Jamf Pro 捕获有关托管的 macOS 设备的清单信息。 Jamf Pro 向 Intune 报告以下信息：

* 设备 Azure AD ID
* JAMF 清单状态（Jamf Pro 在过去 24 小时内签入的计算机的清单状态）
* 操作系统版本
* 用户 Azure AD ID
* 已加密（FileVault 2）
* 网关守卫状态
* 密码：最小字符集数
* 密码过期(天)
* 密码类型 - 简单、字母数字字符或未知
* 防止自动登录
* 所需的密码长度
* 密码：阻止重用的曾用密码数
* 系统完整性保护
* 上次签入时间
* 体系结构类型
* 可用的 RAM 槽
* 电池容量
* 启动 ROM
* 总线速度
* 缓存大小
* 设备名称
* 域加入
* Jamf ID
* MAC 地址
* 品牌
* 型号
* 模型标识符
* NIC 速度
* 内核数量
* 处理器数目
* 操作系统
* 平台
* 处理器速度
* 处理器类型
* 辅助 MAC 地址
* 序列号
* SMC 版本
* RAM 总量
* UDID
* 用户电子邮件

## <a name="next-steps"></a>后续步骤

- [将符合性策略应用到 Jamf 管理的设备](conditional-access-assign-jamf.md)
