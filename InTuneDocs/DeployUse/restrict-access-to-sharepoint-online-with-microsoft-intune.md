---
# required metadata

title: 限制对 SharePoint Online 的访问 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 限制对 SharePoint Online 的访问
使用 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 条件性访问以控制对位于 SharePoint Online 上的文件的访问。
条件性访问有两个组件：
- 设备合规性策略，设备必须符合该策略才能被视为合规。
- 条件性访问策略，你可以从中指定设备必须满足该策略才能访问服务的条件。
若要了解有关条件性访问如何工作的详细信息，请阅读 [restrict access to email and O365 services](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)（限制对电子邮件和 O365 服务的访问）主题。

当用户尝试在其设备上使用受支持的应用（如 OneDrive）连接到文件时，会进行以下评估：

![图示显示了确定是允许访问还是阻止设备访问 SharePoint 的决策点 ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>具有使用新式验证的应用的 PC 和 Windows 10 移动设备的条件性访问当前不可用于所有的 Intune 客户。 如果你已在使用这些功能，则无需采取任何措施。 你可以继续使用它们。

>如果你尚未为具有使用新式验证的应用的 PC 或 Windows 10 移动设备创建条件性访问策略，并希望创建该策略，则必须提交请求。  你可以在 [Connect 网站](http://go.microsoft.com/fwlink/?LinkId=761472)中了解有关已知问题和如何访问此功能的详细信息

在配置 SharePoint Online 的条件性访问策略**之前**，必须：
- 具有 **SharePoint Online 订阅**，并且用户必须获得 SharePoint Online 许可。
- 已订阅了**企业移动性套件**或 **Azure Active Directory Premium**

  若要连接到所需文件，设备必须：
-   已向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] **注册** 或是已加入域的 PC。

-   已在 Azure Active Directory 中**注册设备**（向以下对象注册设备时会自动发生此情况）


-   符合任何已部署的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 符合性策略

基于指定的条件，设备状态存储在可授予或阻止对文件的访问权限的 Azure Active Directory 中。

如果不满足条件，则用户将在登录时看到以下消息的其中一条：

-   如果未向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 注册设备，或未在 Azure Active Directory 中注册，则会显示一条消息，其中包含有关如何安装公司门户应用和进行注册的说明。

-   如果设备不合规，则显示一条消息，将用户定向到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 公司门户网站，用户可从中找到有关问题及其修正方法的信息。

## 对移动设备的支持
- iOS 7.1 及更高版本
- Android 4.0 及更高版本、Samsung Knox 标准版 4.0 或更高版本
- Windows Phone 8.1 及更高版本

## 对 PC 的支持
- Windows 8.1 及更高版本（注册到 Intune 时）
- Windows 7.0 或 Windows 8.1（若已加入域）

  - 必须将已加入域的 PC 设置为[自动注册](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/)到 Azure Active Directory。
AAD DRS 将对 Intune 和 Office 365 客户自动激活。 已经部署了 ADFS 设备注册服务的用户将不会在他们本地的 Active Directory 上看到已注册的设备。

  - 如果策略设置为要求加入域，且 PC 未加入域，则会显示一条与 IT 管理员联系的消息。

  - 如果策略设置要求加入域或合规，且 PC 不符合任一要求，则会显示一条消息，其中包含有关如何安装公司门户应用和进行注册的说明。
-    [Office 365 新式验证必须已启用](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)，且具有所有最新的 Office 更新。

    新式验证将基于 Active Directory 身份验证库 (ADAL) 的登录引入到 Office 2013 Windows 客户端中，并实现诸如“多重身份验证”和“基于证书的身份验证”等更佳的安全性


## 配置 SharePoint Online 的条件性访问

### 步骤 1：配置 Active Directory 安全组
在开始之前，针对条件访问策略配置 Azure Active Directory 安全组。 你可以在 **“Office 365 管理中心”**，或 **“Intune 帐户门户”**中配置这些组。 这些组将用于以用户为目标或从策略中免除用户。 如果将某个用户设定为策略的目标，则其使用的每个设备必须合规才能访问资源。

你可以在 SharePoint Online 策略中指定两种组类型：

-   **目标组** – 包含将应用策略的用户组。

-   **免除组** – 包含从策略中免除的用户组。

如果用户位于两个组中，则会将其从策略中免除。

### 步骤 2：配置和部署合规性策略
如果你尚未创建和部署合规性策略，请先创建合规性策略并将其部署到 SharePoint Online 策略将以其为目标的用户。

> 将合规性策略部署到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 组，而条件性访问策略以 Azure Active Directory 安全组为目标。

有关如何配置合规性策略的详细信息，请参阅[创建合规性策略](create-a-device-compliance-policy-in-microsoft-intune.md)

> 如果尚未部署合规性策略，那么设备将被视为合规。

准备就绪后，继续**步骤 3**

### 步骤 3：配置 SharePoint Online 策略
接下来，配置策略以要求只有托管及合规设备才能访问 SharePoint Online。 此策略会存储在 Azure Active Directory 中。

#### <a name="bkmk_spopolicy"></a>

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，单击“策略” > “条件性访问” > “SharePoint Online 策略”
![SharePoint Online 策略页面的屏幕截图](../media/IntuneSASharePointOnlineCAPolicy.png)

2.  选择“启用 SharePoint Online 的条件性访问策略”

3.  在“应用程序访问”下，可以选择将条件性访问策略应用到：

    -   **所有平台**

        这将要求用于访问 **SharePoint Online** 的任何设备已在 Intune 中注册且符合相应的策略。  任何使用**新式验证**的客户端应用程序需遵守条件性访问策略。 如果目前 Intune 不支持该平台，则会阻止对 **SharePoint Online** 的访问。
        >[!TIP]
        >如果你尚未使用 PC 的条件性访问，则可能不会看到此选项。  请改用“特定平台”。 针对 PC 的条件性访问当前不可用于所有的 Intune 客户。   你可以在 [Microsoft Connect 网站](http://go.microsoft.com/fwlink/?LinkId=761472)中了解有关已知问题和如何访问此功能的详细信息

    -   **特定平台**

         条件性访问策略会应用到在你指定的平台上使用新式验证的任何客户端应用。

     对于 Windows PC，PC 必须已加入域，或是向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 注册并且必须是合规的。 可以设置以下要求：

     -   **设备必须已加入域或必须是合规的。** 如果你想让 PC 加入域或符合 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 中设置的策略，请选择此选项。 如果 PC 不满足任一要求，则系统会提示用户向以下对象注册设备

     -   **设备必须已加入域。** 选择此选项可要求 PC 必须已加入域才能访问 Exchange Online。 如果 PC 未加入域，则系统会阻止对电子邮件的访问，并且提示用户与 IT 管理员联系。

     -   **设备必须是合规的。** 选择此选项可要求 PC 必须在 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 中注册并且必须是合规的。 如果 PC 未注册，则会显示一条消息，其中包含有关如何注册的说明。

4.  在“目标组” 下，单击“修改”  以选择将应用策略的 Azure Active Directory 安全组。 你可以选择将此应用于所有用户或仅针对选择的用户组。

5.  在“免除组” 下，可以选择“修改”  以选择从此策略中免除的 Azure Active Directory 安全组。

6.  完成后，请单击“保存”

不需要部署条件访问策略，它将立即生效。

### 步骤 4：监视符合性和条件访问策略
在“组”工作区中，可以查看设备的状态。

选择任何移动设备组，然后在“设备”  选项卡上，选择以下“筛选器” 之一:

-   **未向 AAD 注册的设备** – 从 SharePoint Online 阻止这些设备。

-   **不兼容的设备** – 从 SharePoint Online 阻止这些设备。

-   **已向 AAD 注册的兼容设备** – 这些设备可以访问 SharePoint Online。

### 另请参阅
[使用 Microsoft Intune 限制对电子邮件和 O365 服务的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


