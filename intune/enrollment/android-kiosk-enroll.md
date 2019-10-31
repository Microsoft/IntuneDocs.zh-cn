---
title: 设置适用于 Android Enterprise 专用设备的 Intune 注册
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中注册 Android Enterprise 专用设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: edc884850b70ff7621224c5b01a68d016f27504e
ms.sourcegitcommit: 5932da3ed8f52c7b0f0d71c1801f81c85952cf0c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72923378"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>设置 Android Enterprise 专用设备的 Intune 注册

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Android Enterprise 通过其专用设备解决方案集支持企业所有的单一用途的展台式设备。 这些设备用于单一用途，例如数字签名、票据打印或库存管理等。 管理员会将设备的用途限制为有限的一组应用和 Web 链接。 它还可以防止用户在设备上添加其他应用或执行其他操作。

Intune可帮助将应用和设置部署到 Android Enterprise 专用设备。 有关 Android Enterprise 的特定详细信息，请参阅 [Android Enterprise 要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

通过此方式管理的设备在没有用户帐户的情况下注册到 Intune，且不与任何最终用户关联。 它们不适用于个人使用的应用程序或非常需要 Outlook 或 Gmail 等特定于用户的帐户数据的应用。

## <a name="device-requirements"></a>设备要求

设备必须满足以下要求才能作为 Android Enterprise 专用设备进行托管：

- Android OS 版本 5.1 及以上版本。
- 设备必须运行具有 Google Mobile Services (GMS) 连接性的 Android 发行版。 设备必须有可用的 GMS，并且必须能连接到 GMS。

## <a name="set-up-android-enterprise-dedicated-device-management"></a>设置 Android Enterprise 专用设备管理

要设置 Android Enterprise 专用设备管理，请执行以下步骤：

1. 若准备管理移动设备，必须[将移动设备管理 (MDM) 机构设置为“Microsoft Intune”](../fundamentals/mdm-authority-set.md)以获取说明  。 第一次设置 Intune 以进行移动设备管理时，只需设置一次此项。
2. [将 Intune 租户帐户连接到托管的 Google Play 帐户](connect-intune-android-enterprise.md)。
3. [创建注册配置文件](#create-an-enrollment-profile)
4. [创建设备组](#create-a-device-group)。
5. [注册专用设备](#enroll-the-dedicated-devices)。

### <a name="create-an-enrollment-profile"></a>创建注册配置文件

> [!NOTE]
> 如果令牌已过期，则与其关联的配置文件将不会显示在“设备注册”   > “Android 注册”   > “公司拥有的专用设备”  中。 若要查看与活动令牌和非活动令牌关联的所有配置文件，请单击“筛选”  ，然后选中“活动”和“非活动”策略状态对应的框。 

必须创建注册配置文件，以便注册专用设备。 创建配置文件时，它会提供注册令牌（随机字符串）和 QR 码。 可使用令牌或 QR 码[注册专用设备](#enroll-the-dedicated-devices)，具体取决于 Android OS 和设备版本。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，选择“设备注册” > “Android 注册” > “公司拥有的专用设备”    。
2. 选择“创建”并填写必填字段  。
    - **名称**：键入在将配置文件分配给动态设备组时使用的名称。
    - **令牌到期日期**：令牌到期日期。 Google 规定最长为 90 天。
3. 选择“创建”  保存该配置文件。

### <a name="create-a-device-group"></a>创建设备组

可将应用和策略定位到已分配或动态设备组。 可按照以下步骤配置动态 AAD 设备组，以自动填充使用特定注册配置文件进行注册的设备：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，选择“组” > “所有组” > “新建组”    。
2. 在“组”边栏选项卡中，填写必填字段，如下所示  ：
    - **组类型**：安全
    - **组名称**：键入直观名称（如“出厂 1 设备”）
    - **成员身份类型**：动态设备
3. 选择“添加动态查询”  。
4. 在“动态成员身份规则”边栏选项卡中，填写如下字段  ：
    - **添加动态成员身份规则**：简单规则
    - **添加设备位置**enrollmentProfileName
    - 在中间的框中，选择“等于”  。
    - 在最后一个字段中，输入之前创建的注册配置文件名称。
    有关动态成员身份规则的详细信息，请参阅 [AAD 中的组动态成员身份规则](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)。 
5. 选择“添加查询” > “创建”   。

### <a name="replace-or-remove-tokens"></a>替换或删除令牌

- **替换令牌**：使用“替换令牌”，可以令牌快要到期时生成新的令牌/QR 码。
- **撤销令牌**：可以立即让令牌/QR 码到期。 从此时起，令牌/QR 码不再可用。 在以下情况下可使用此选项：
  - 意外地与未经授权的一方共享令牌/QR 码
  - 完成所有注册，不再需要令牌/QR 码

替换或撤销令牌/QR 码不会对已注册的设备产生任何影响。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，选择“设备注册” > “Android 注册” > “公司拥有的专用设备”    。
2. 选择要使用的配置文件。
3. 选择“令牌”  。
4. 若要替换令牌，请选择“替换令牌”  。
5. 若要撤销令牌，请选择“撤销令牌”  。

## <a name="enroll-the-dedicated-devices"></a>注册专用设备

现在可以[注册专用设备](android-dedicated-devices-fully-managed-enroll.md)。

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>在 Android Enterprise 专用设备上管理应用

Android Enterprise 专用设备上只能安装分配类型[设置为必需](../apps/apps-deploy.md#assign-an-app)的应用。 从托管的 Google Play 商店安装应用与从 Android Enterprise 工作配置文件设备安装应用的方式相同。

当应用开发人员向 Google Play 发布更新时，托管设备上的应用会自动更新。

要从 Android Enterprise 专业设备中删除应用，可执行以下任一操作：
- 删除所需的应用部署。
- 创建应用的卸载部署。

## <a name="next-steps"></a>后续步骤
- [部署 Android 应用](../apps/apps-deploy.md)
- [添加 Android 配置策略](../configuration/device-profiles.md)
