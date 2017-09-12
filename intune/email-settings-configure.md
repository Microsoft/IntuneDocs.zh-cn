---
title: "如何配置 Intune 电子邮件设置"
titleSuffix: Azure portal
description: "了解如何配置 Intune，以在所管设备上创建与公司电子邮件的连接。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 484bd9b0-fbf1-4f4f-940c-6b12fa07e228
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9de8eed31a93fc1360eb1a62b1d9328b42853d74
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置电子邮件设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

如果设备通过连接到公司电子邮件和与其同步时所需的设置进行管理，则其可使用电子邮件配置文件进行配置。 这有助于确保设置在所有设备中是标准的，还有助于减少对不了解正确电子邮件设置的最终用户的支持呼叫。

大多数平台支持内置邮件客户端。 当前不支持大多数第三方电子邮件应用。

你可以使用电子邮件配置文件配置下列设备类型上的本机电子邮件客户端：

- Android Samsung KNOX 标准版 4.0 和更高版本
- Android for Work
- iOS 8.0 及更高版本
- Windows Phone 8.1 及更高版本
- Windows 10（桌面版）和 Windows 10 移动版

使用本主题中的信息了解有关配置电子邮件配置文件的基础知识，然后阅读有关每个平台的深入主题以了解设备规范。

## <a name="create-a-device-profile-containing-email-settings"></a>创建包含电子邮件设置的设备配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入电子邮件配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用电子邮件设置的设备平台。 目前，可以为电子邮件设备设置选择以下平台之一：
    - **Android**（仅 Samsung Android KNOX 标准版）
    - **Android for Work**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 及更高版本**
6. 在“配置文件”键入下拉列表中，选择“电子邮件”。
7. 根据所选择的平台，可配置的设置将有所不同。 有关每个平台的详细设置，请转到以下主题之一：
    - [ 和 Samsung KNOX 标准版设置](email-settings-android.md)
    - [iOS 设置](email-settings-ios.md)
    - [Windows Phone 8.1 设置](email-settings-windows-phone-8-1.md)
    - [Windows 10 设置](email-settings-windows-10.md)
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。

## <a name="further-information"></a>更多信息

### <a name="remove-an-email-profile"></a>删除电子邮件配置文件

如果想要从设备中删除电子邮件配置文件，请编辑分配并删除包含该设备的任何组。 请注意，如果电子邮件配置文件是设备上唯一的电子邮件配置文件，则无法通过此方法将其删除。

### <a name="securing-email-access"></a>保护电子邮件访问权限

可以使用以下两种方法之一来帮助保护电子邮件配置文件：

1. **证书** - 创建电子邮件配置文件时，可以选择之前在 Intune 中创建的证书配置文件。 该配置文件又称为身份证书，用于根据受信任的证书配置文件（或根证书）进行身份验证，以确定用户的设备可以连接。 受信任的证书会分配到对电子邮件连接进行身份验证的计算机（通常是本机邮件服务器）。
有关如何在 Intune 中创建和使用证书配置文件的详细信息，请参阅[如何使用 Intune 配置证书](certificates-configure.md)。
2. **用户名和密码** - 用户通过提供其用户名和密码向本机邮件服务器进行身份验证。
密码不包含在电子邮件配置文件中，因此用户在连接到电子邮件时需要提供密码。


### <a name="how-intune-handles-existing-email-accounts"></a>Intune 如何处理现有电子邮件帐户

如果用户已配置电子邮件帐户，Intune 电子邮件配置文件分配结果将取决于设备平台：

- **iOS**：基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 重复的电子邮件配置文件将阻止分配 Intune 配置文件。 在这种情况下，公司门户将通知用户其不符合规定并提示用户手动删除已配置的配置文件。 若要帮助防止此问题，请告知用户在安装电子邮件配置文件前进行注册，这可允许 Intune 设置配置文件。
- **Windows**：基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 Intune 会覆盖由用户创建的现有电子邮件配置文件。
- **Android Samsung KNOX 标准版**：基于电子邮件地址检测到现有的重复电子邮件帐户，并使用 Intune 配置文件将其覆盖。
由于 Android 不使用主机名来识别配置文件，因此我们建议不要创建多个电子邮件配置文件并在不同主机的同一邮件地址中使用，因为它们会相互覆盖。
- **Android for Work** Intune 提供两个 Android for Work 电子邮件配置文件，分别用于 Gmail 和 Nine Work 电子邮件应用。 这些应用在 Google Play 商店中提供，且安装在设备工作配置文件中，因此它们不会导致出现重复的配置文件。 这两个应用支持到 Exchange 的连接。 若要启用电子邮件连接，请将其中一个电子邮件应用部署到用户的设备，然后创建并部署相应的电子邮件配置文件。 Nine Work 等电子邮件应用可能需付费使用。 若有任何问题，请查看应用的许可详细信息或与应用公司联系。

### <a name="update-an-email-profile"></a>更新电子邮件配置文件

如果更改以前分配的电子邮件配置文件，最终用户可能会看到一条消息，请求他们批准重新配置其电子邮件设置。
