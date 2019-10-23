---
title: 使用 Microsoft Intune 在 Windows 设备上重置密码 - Azure | Microsoft Docs
description: 要在 Windows 设备上重置密码，请安装 Microsoft Pin 重置服务和 Microsoft Pin 重置客户端，使用 Azure Active Directory Directory ID 创建设备策略，然后在 Azure 门户中使用 Microsoft Intune 重置密码。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 445737a1b0a72e380844af6225cdb735cd3ec02c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509351"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>使用 Intune 在 Windows 设备上重置密码

可重置 Windows 设备的密码。 重置密码功能使用 Microsoft Pin 重置服务，为运行 Windows 10 移动版的设备生成新密码。 

## <a name="supported-platforms"></a>受支持的平台

- Windows 10 移动版运行创意者更新及更高版本（已加入 Azure AD）。

不支持以下平台  ：
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>授权 PIN 重置服务

要在 Windows 设备上重置密码，请将 PIN 重置服务载入到 Intune 租户。

1. 转到 [Microsoft PIN 重置服务生产](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent)，并使用租户管理员帐户登录。
2. 接受允许 PIN 重置服务访问帐户的许可  ：![接受 PIN 重置服务器的权限请求](./media/device-windows-pin-reset/pin-reset-service-home-screen.png)
3. 转到 [Microsoft PIN 重置客户端生产](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent)，并使用租户管理员帐户登录。  接受允许 PIN 重置客户端访问帐户的许可。
4. 在 [Azure 门户](https://portal.azure.com)，确认企业应用程序（所有应用程序）中列出了 PIN 重置服务：![PIN 重置服务权限页](./media/device-windows-pin-reset/pin-reset-service-application.png)

> [!NOTE]
> 接受 PIN 重置请求后，可能会收到 `Page not found` 消息，也可能看起来无任何变化。 此行为是正常的。 请务必确认列出了租户的两个 PIN 重置应用程序。

## <a name="configure-windows-devices-to-use-pin-reset"></a>将 Windows 设备配置为使用 PIN 重置

若要在所管理的 Windows 设备上配置 PIN 重置，请使用 [Intune Windows 10 自定义设备策略](../configuration/custom-settings-windows-10.md)。 使用以下 Windows 策略配置服务提供程序 (CSP) 来配置策略：

**使用设备策略** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

使用 Azure AD Directory ID 替换租户 ID，前者列在 [Azure 门户](https://portal.azure.com)中 Azure Active Directory 的“属性”中   。

将此 CSP 的值设置为“True”  。

> [!TIP]
> 创建策略后，可将其分配（或部署）到一个组。 可将策略分配到用户组或设备组。 如果将其分配到用户组，则组可包含拥有 IOS 等其他设备的用户。 从技术上讲，不会应用该策略，但这些设备仍包含在状态详细信息中。

## <a name="reset-the-passcode"></a>重置密码

1. 登录到 [Azure 门户](https://portal.azure.com)。 
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”    。
3. 依次选择“设备”和“所有设备”   。
4. 选择要重置密码的设备。 在设备属性中，选择“新建密码”  。
5. 单击“是”  以确认。 密码已生成，并将在接下来的七天内显示在门户中。

## <a name="next-step"></a>下一步

如果密码重置失败，门户中会提供显示详细信息的链接。
