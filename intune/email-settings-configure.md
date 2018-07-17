---
title: 如何配置 Microsoft Intune 电子邮件设置
titleSuffix: ''
description: 了解如何配置 Microsoft Intune，以在所管理的设备上创建与公司电子邮件的连接。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 15710f6115bb23dfe9ba899dfa01b38f315d00f0
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905302"
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置电子邮件设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

如果设备通过连接到公司电子邮件和与其同步时所需的设置进行管理，则其可使用电子邮件配置文件进行配置。 这有助于确保设置在所有设备中是标准的，还有助于减少对不了解正确电子邮件设置的最终用户的支持呼叫。

大多数平台支持内置邮件客户端。 当前不支持大多数第三方电子邮件应用。

你可以使用电子邮件配置文件配置下列设备类型上的本机电子邮件客户端：

- Android Samsung Knox Standard 4.0 及更高版本
- Android 工作配置文件设备
- iOS 8.0 及更高版本
- Windows Phone 8.1 及更高版本
- Windows 10（桌面版）和 Windows 10 移动版

使用本文章中的信息了解有关配置电子邮件配置文件的基础知识，然后阅读针对每个平台的深入主题以了解设备规范。

## <a name="create-a-device-profile-containing-email-settings"></a>创建包含电子邮件设置的设备配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格上，选择“设备配置”。
2. 在“管理”部分的“设备配置”窗格上，选择“配置文件”。
3. 在“配置文件”窗格上，选择“创建配置文件”。
4. 在“创建配置文件”窗格上，输入电子邮件配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用电子邮件设置的设备平台。 目前，可以为电子邮件设备设置选择以下平台之一：
    - **Android**（仅 Samsung Android Knox Standard）
    - **Android 企业**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**
6. 在“配置文件”键入下拉列表中，选择“电子邮件”。
7. 根据所选择的平台，可配置的设置有所不同。 有关每个平台的详细设置，请转到以下主题之一：
    - [Android 工作配置文件和 Samsung Knox Standard 设置](email-settings-android.md)
    - [iOS 设置](email-settings-ios.md)
    - [Windows Phone 8.1 设置](email-settings-windows-phone-8-1.md)
    - [Windows 10 设置](email-settings-windows-10.md)
8. 完成后，返回“创建配置文件”窗格，然后点击“创建”。

随即会创建配置文件，并显示在“配置文件列表”窗格上。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。

## <a name="further-information"></a>更多信息

### <a name="remove-an-email-profile"></a>删除电子邮件配置文件

如果想要从设备中删除电子邮件配置文件，请编辑分配并删除包含该设备的任何组。 如果电子邮件配置文件是设备上唯一的电子邮件配置文件，则无法通过此方法将其删除。

### <a name="securing-email-access"></a>保护电子邮件访问权限

可以使用以下两种方法之一来帮助保护电子邮件配置文件：

1. **证书** - 创建电子邮件配置文件时，可以选择之前在 Intune 中创建的证书配置文件。 该配置文件又称为身份证书，用于根据受信任的证书配置文件（或根证书）进行身份验证，以确定用户的设备可以连接。 受信任的证书会分配到对电子邮件连接进行身份验证的计算机（通常是本机邮件服务器）。
有关如何在 Intune 中创建和使用证书配置文件的详细信息，请参阅[如何使用 Intune 配置证书](certificates-configure.md)。
2. **用户名和密码** - 用户通过提供其用户名和密码向本机邮件服务器进行身份验证。
密码不包含在电子邮件配置文件中，因此用户在连接到电子邮件时需要提供密码。


### <a name="how-intune-handles-existing-email-accounts"></a>Intune 如何处理现有电子邮件帐户

如果用户已配置电子邮件帐户，Intune 电子邮件配置文件分配结果将取决于设备平台：

- **iOS**：基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 重复的电子邮件配置文件会阻止分配 Intune 配置文件。 在这种情况下，公司门户将通知用户其不符合规定并提示用户手动删除已配置的配置文件。 若要帮助防止此问题，请告知用户在安装电子邮件配置文件前进行注册，这可允许 Intune 设置配置文件。
- **Windows**：基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 Intune 会覆盖由用户创建的现有电子邮件配置文件。
- **Android Samsung Knox Standard**：根据电子邮件地址检测到现有的重复电子邮件配置文件，并用 Intune 配置文件覆盖它。
由于 Android 不使用主机名来识别配置文件，因此我们建议不要创建多个电子邮件配置文件并在不同主机的同一邮件地址中使用，因为它们会相互覆盖。
- **Android 工作配置文件** Intune 提供两个 Android 工作配置文件电子邮件配置文件，分别用于 Gmail 和 Nine Work 电子邮件应用。 这些应用在 Google Play 商店中提供，且安装在设备工作配置文件中，因此它们不会导致出现重复的配置文件。 这两个应用支持到 Exchange 的连接。 若要启用电子邮件连接，请将其中一个电子邮件应用部署到用户的设备，然后创建并部署相应的电子邮件配置文件。 Nine Work 等电子邮件应用可能需付费使用。 若有任何问题，请查看应用的许可详细信息或与应用公司联系。

### <a name="update-an-email-profile"></a>更新电子邮件配置文件

如果更改以前分配的电子邮件配置文件，最终用户可能会看到一条消息，请求他们批准重新配置其电子邮件设置。
