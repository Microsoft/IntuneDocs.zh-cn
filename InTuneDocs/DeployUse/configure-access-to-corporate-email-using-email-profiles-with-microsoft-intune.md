---
title: "使用电子邮件配置文件访问公司电子邮件 | Microsoft Intune"
description: "电子邮件配置文件设置可用于配置移动设备上特定电子邮件客户端的电子邮件访问设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f0c5920f7cc46e40bf4d1795a68ba1d67840fcfa
ms.openlocfilehash: 6ac7034ba0713c7b6bdd28c7b53b99c247d3aeb3


---

# <a name="configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune"></a>使用 Microsoft Intune 的电子邮件配置文件配置对公司电子邮件的访问

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

许多移动平台包含一个作为操作系统一部分附带的本机电子邮件客户端。 可使用本主题中所述的电子邮件配置文件对这些客户端中的某一些进行设置。

电子邮件配置文件设置可用于设置移动设备上特定电子邮件客户端的电子邮件访问设置。 在受支持的平台上，可以使用 Microsoft Intune 设置本机电子邮件客户端，以使用户能够在不进行任何其他设置的情况下在个人设备上访问公司电子邮件。

如果需要采取额外的措施进行数据丢失防护，请使用[条件性访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)，它可以控制对任何电子邮件客户端（包括本机电子邮件客户端）的用户邮箱的访问。

IT 管理员或用户还可以选择安装备用电子邮件客户端（例如，Microsoft Outlook for Android 或 iOS）。 这些电子邮件客户端可能不支持电子邮件配置文件，并且不能使用 Intune 电子邮件配置文件进行设置。  

你可以使用电子邮件配置文件配置下列设备类型上的本机电子邮件客户端：
-   Windows Phone 8.1 及更高版本
-   Windows 10 桌面版、Windows 10 移动版及更高版本
-   iOS 8.0 及更高版本
-   Samsung KNOX 标准版（4.0 及更高版本）
-   Android for Work

>[!NOTE]
>Intune 提供两个 Android for Work 电子邮件配置文件，分别用于 Gmail 和 Nine Work 电子邮件应用。 这些应用在 Google Play 商店中提供，支持与 Exchange 的连接。 若要启用电子邮件连接，请将其中一个电子邮件应用部署到用户的设备，然后创建并部署相应的配置文件。

除了在设备上设置电子邮件帐户外，还可以设置要同步的电子邮件数量，并且根据设备类型设置要同步的内容类型。

>[!NOTE]
>
>如果用户在通过 Intune 设置配置文件前已安装了电子邮件配置文件，则 Intune 电子邮件配置文件部署的结果将取决于设备平台：

>**iOS**：基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 用户创建的重复电子邮件配置文件会阻止由 Intune 管理员创建的配置文件的部署。 这是一个常见问题，因为 iOS 用户通常会创建电子邮件配置文件，然后注册。 公司门户将通知用户由于他们的电子邮件配置文件是手动配置的，因此他们不合规，并提示用户删除该配置文件。 用户应删除其电子邮件配置文件，以便设置 Intune 配置文件。 为防止此问题，请告知用户在安装电子邮件配置文件前进行注册，并允许 Intune 设置配置文件。

>**Windows**：基于主机名和电子邮件地址检测到现有的重复电子邮件配置文件。 Intune 会覆盖由用户创建的现有电子邮件配置文件。

>**Samsung KNOX**：基于电子邮件地址检测到现有的重复电子邮件帐户，并使用 Intune 配置文件将其覆盖。 如果用户设置该帐户，则 Intune 配置文件将再次覆盖该帐户。 请注意，这可能会使用户感到迷惑。

>由于 Samsung KNOX 不使用主机名来识别配置文件，因此我们建议不要创建多个电子邮件配置文件并在不同主机的同一邮件地址中使用，因为它们会相互覆盖。

>**Android for Work**：Intune 配置文件只应用于设备的工作配置文件中的特定电子邮件应用，不会影响设备用户配置文件上的电子邮件配置。


## <a name="secure-email-profiles"></a>保护电子邮件配置文件
可以使用证书或密码保护电子邮件配置文件。

### <a name="certificates"></a>证书
当你创建电子邮件配置文件时，你可以选择之前在 Intune 中创建的证书配置文件。 该配置文件又称为身份证书，用于根据受信任的证书配置文件（或根证书）进行身份验证，以确定用户的设备可以连接。 受信任的证书会部署到对电子邮件连接进行身份验证的计算机（通常是本机邮件服务器）。

有关如何在 Intune 中创建和使用证书配置文件的详细信息，请参阅[使用证书配置文件的安全资源访问](secure-resource-access-with-certificate-profiles.md)。

### <a name="user-name-and-password"></a>用户名和密码
用户通过提供其用户名和密码向本机邮件服务器进行身份验证。

密码不包含在电子邮件配置文件中，因此用户在连接到电子邮件时需要提供密码。

### <a name="create-an-email-profile"></a>创建一个电子邮件配置文件

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“策略”&gt;“添加策略”。

2.  设置以下策略类型之一：

    -   **Samsung KNOX 标准（4.0 及更高版本）的电子邮件配置文件**

    -   **电子邮件配置文件（iOS 8.0 及更高版本）**

    -   **电子邮件配置文件（Windows Phone 8.1 及更高版本）**

    -   **电子邮件配置文件（Windows 10 桌面版和移动版及更高版本）**

    -   **电子邮件配置文件 (Android for Work - Gmail)**

    -   **电子邮件配置文件 (Android for Work - Nine Work)**

    你只能创建和部署自定义电子邮件配置文件策略。 建议的设置不可用。

3.  使用下表来帮助设置电子邮件配置文件设置：

|设置名 | 更多信息|
| ----------- | --------------- |
    |**Name**|电子邮件配置文件的唯一名称。|
    |**描述**|可帮助你识别此配置文件的说明。|
    |**主机**|托管本机电子邮件服务的公司服务器的主机名。|
    |**帐户名**|电子邮件帐户的显示名称，因为它将在用户的设备上显示。|
    |**用户名**|这是 Active Directory (AD) 或 Azure AD 中的属性，将用于生成此电子邮件配置文件的用户名。 选择主 SMTP 地址，例如 *user1@contoso.com* 或用户主体名称（如 *user1* 或 *user1@contoso.com*）。|
    |**电子邮件地址**|每个设备上用户电子邮件地址的生成方式。 选择“主 SMTP 地址”以使用主 SMTP 地址登录到 Exchange，或使用“用户主体名称”以使用完整主体名称作为电子邮件地址。|
    |**身份验证方法**（Android for Work、Samsung KNOX 和 iOS）|选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。|
    |**为客户端身份验证选择客户端证书(身份证书)**（Android for Work、Samsung KNOX 和 iOS）|请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 证书。 有关如何在 Intune 中使用证书配置文件的详细信息，请参阅[使用证书配置文件的安全资源访问](secure-resource-access-with-certificate-profiles.md)。 仅当身份验证方法为“证书”时才会显示此选项。|
    |**使用 S/MIME**（Samsung KNOX 和 iOS）|发送使用 S/MIME 加密的传出电子邮件。|
    |**签名证书**（Samsung KNOX 和 iOS）|选择将用于签署发送电子邮件的签名证书。 仅当你选择**使用 S/MIME**时才会显示此选项。|
    |**要同步的电子邮件的天数**|你想要同步的电子邮件的天数，或选择“无限制”以同步所有可用的电子邮件。|
    |**同步计划**（Android for Work、Samsung KNOX、Windows Phone 8 及更高版本、Windows 10）|选择设备同步 Exchange Server 的数据所依据的计划。 你还可以选择“在邮件到达时”（在邮件到达时同步数据），或选择“手动”（设备用户必须启动同步）。|
    |**使用 SSL**|发送电子邮件、接收电子邮件以及与 Exchange Server 通信时，请使用安全套接字层 (SSL) 通信。 对于运行 Samsung KNOX 4.0 或更高版本的设备，必须导出 Exchange Server 的 SSL 证书并将其部署为 Intune 中的 Android 可信证书配置文件。 如果此证书通过其他方式安装在 Exchange Server 上，则 Intune 不支持对其进行访问。|
    |**要同步的内容类型**（所有平台，Android for Work Gmail 除外）|请选择想要同步到设备的内容类型。|
    |**允许从第三方应用程序发送电子邮件**（仅针对 iOS）|允许用户选择此配置文件作为用于发送电子邮件的默认帐户，并允许第三方应用程序在本机电子邮件应用中打开电子邮件，例如，将文件附加到电子邮件。|

> [!IMPORTANT]
>
> 如果你部署了一个电子邮件配置文件，之后想要更改“主机”或“电子邮件地址”的值，则必须删除现有的电子邮件配置文件并创建一个具有所需值的新配置文件。

4.  完成后，请单击“保存策略” **Save Policy**。

新的策略将在“策略”  工作区的“配置策略”  节点处显示。

## <a name="deploy-the-policy"></a>部署策略

1.  在“策略”工作区中，选择想要部署的策略，然后选择“管理部署”。

2.  在“管理部署”  对话框中：

    -   **部署策略**选择想要向其部署策略的一个或多个组，然后选择“添加”&gt;“确定”。

    -   **关闭对话框而不部署** — 选择**取消**。

“策略”  工作区“概述”  页的状态摘要和警报可识别需要关注的策略问题。 此外，状态摘要会显示在“仪表板”工作区中。

> [!NOTE]
> - 对于 Android for Work，请确保除了部署相应的电子邮件配置文件外，还部署了 Gmail 或 Nine Work 应用。
> - 如果想要从设备中删除电子邮件配置文件，则请编辑部署并删除包含该设备的任何组。



<!--HONumber=Nov16_HO3-->


