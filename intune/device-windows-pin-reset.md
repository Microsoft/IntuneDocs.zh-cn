---
title: "使用 Intune 在 Windows 设备上重置密码"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 在与 Microsoft PIN 重置服务集成的 Windows 设备上重置密码。”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9cf2549852c5949ff1c95af12b40f59136d56e34
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2017
---
# <a name="reset-the-passcode-on-windows-devices-integrated-with-the-microsoft-pin-reset-service-using-intune"></a>使用 Intune 在与 Microsoft PIN 重置服务集成的 Windows 设备上重置密码

适用于 Windows 设备的重置密码功能与 Microsoft PIN 重置服务相集成，让用户能够为运行 Windows 10 移动版的设备生成新密码。 设备必须运行 Windows 10 创建者更新或更高版本。

## <a name="supported-platforms"></a>受支持的平台

- Windows - Windows 10 创意者更新及更高版本（已加入 Azure AD）支持
- Windows Phone - 不支持
- iOS - 不支持
- macOS - 不支持
- Android - 不支持


## <a name="before-you-start"></a>开始之前

必须先将 PIN 重置服务载入 Intune 租户并配置所管理的设备，才能以远程方式在可管理的 Windows 设备上重置密码。 请按照这些说明设置：

### <a name="connect-intune-with-the-pin-reset-service"></a>将 Intune 与 PIN 重置服务连接

1. 请访问 [Microsoft PIN 重置服务集成网站](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent)，并使用用于管理 Intune 租户的租户管理员帐户进行登录。
2. 登录后，单击“接受”以允许 PIN 重置服务访问自己的帐户。<br>
![PIN 重置服务权限页](./media/pin-reset-service-application.png)
3. 在 Azure 门户中，可验证 Intune 和 PIN 重置服务是从企业应用程序进行集成 - 所有应用程序边栏选项卡如下面的屏幕截图所示：<br>
![Azure 中的 PIN 重置服务应用程序](./media/pin-reset-service-home-screen.png)
4. 使用 Intune 租户管理员凭据登录到[此网站](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent)，然后再次选择“接受”以允许该服务访问自己的帐户。

### <a name="configure-windows-devices-to-use-pin-reset"></a>将 Windows 设备配置为使用 PIN 重置

若要在所管理的 Windows 设备上配置 PIN 重置，请使用 [Intune Windows 10 自定义设备策略](custom-settings-windows-10.md)来启用这项功能。 使用以下 Windows 策略配置服务提供程序 (CSP) 来配置策略：


- 对于设备 - **./Device/Vendor/MSFT/PassportForWork/租户 ID**/Policies/EnablePinRecovery

“租户 ID” 是指 Azure Active Directory 的 Directory ID，可从 Azure Active Directory 的“属性”页获取。

将此 CSP 的值设置为“True”。

## <a name="steps-to-reset-the-passcode"></a>重置密码的步骤

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备”边栏选项卡上，选择“管理” > “所有设备”。
5. 选择要重置密码的设备，然后在设备属性边栏选项卡上选择“新密码”。
6. 在出现的确认内容中，选择“是”。 密码已生成，并将在接下来的七天内显示在门户中。

## <a name="next-steps"></a>后续步骤

如果密码重置失败，可通过门户提供的链接获取详细信息。


