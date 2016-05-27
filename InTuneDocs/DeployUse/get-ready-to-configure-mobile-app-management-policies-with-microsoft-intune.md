---
# required metadata

title: 准备好配置移动应用管理策略 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 准备好使用 Microsoft Intune 配置移动应用管理策略
本主题介绍可以在 Azure 门户中创建移动应用管理策略 (MAM) 之前需要执行的操作。
如果你当前使用 **Intune 管理控制台**管理设备，则可以创建一个 MAM 策略，来支持在 Intune 中使用 [Intune 管理控制台](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)注册的设备的应用
>[!IMPORTANT]
> 你可能无法在 Intune 管理控制台中看到全部 MAM 策略设置。 Azure 门户是用于创建 MAM 策略的新管理控制台。

##  受支持的平台
- iOS 8.1 或更高版本

- Android 4 或更高版本

##  受支持的应用
若要查看支持的应用的完整列表，请转到 Microsoft Intune 应用程序合作伙伴页上的 [Microsoft Intune 移动应用程序库](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)。
单击应用可查看支持的方案、平台以及应用是否支持多身份。

可以配置 MAM 策略“之前”，需要以下准备事项：

-   **Microsoft Intune 订阅**。    最终用户需要 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 许可证以获取具有 MAM 策略的应用。

-   必须将“移动设备管理机构”设置为“Intune”或“Configuration Manager”，具体取决于你使用的只是 Intune 还是与 Intune 集成的 Configuration Manager 来管理设备。 如果你正在使用 O365 内置移动设备管理，则必须购买 Intune 订阅并[将移动设备管理机构设置为 Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)
-   以下事项需要 **Office 365 (O365)** 订阅：
  - 将 MAM 策略应用于具有多身份支持的应用。
  - 创建 SharePoint Online 和 Exchange Online 工作帐户。 不支持 Exchange 内部部署和 SharePoint 内部部署。


- “Azure Active Directory (Azure AD)”，用于创建用户。 当最终用户启动应用，并输入他们的工作凭据时，Azure AD 会对用户进行身份验证。

    > 如果你使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 控制台设置用户，请注意 MAM 策略配置将迁移到以后的 Azure 门户，要使用此门户，需要使用 Office 365 门户设置 Azure AD 用户组。


## 创建用户并分配 Microsoft Intune 许可证

1. 需要 Intune 订阅：如果当前使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 来管理设备，那么你已经具有 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 订阅。  如果你已购买 EMS 许可证，那么你还具有 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 订阅。 如果你尝试 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 来试用 MAM 功能，你可以在[此处](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)获取试用帐户

    要检查你是否具有 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 订阅，请在 Office 门户中转到“帐单”页面。  你应该可以看到在订阅下方 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 显示为“活动”状态。

2.  使用管理员凭据登录   [Office 门户](http://portal.office.com) 。

3.  导航到“活动用户”页，添加用户并分配 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 许可证。

    ![Office 门户添加用户页](../media/AppManagement/OfficePortal_AddUsers.png)

4.  要赋予用户访问 Office 门户、Azure AD 门户和 Azure 门户的权限，请将“全局管理员角色”分配给此用户。

    ![显示活动用户页的 Office 门户屏幕截图 ](../media/AppManagement/OfficePortal_AddRoletoUser.png)

5.  MAM 策略已部署到 Azure Active Directory 中的用户组。 要创建想要用于 MAM 策略的用户组，请导航到“Office 门户”上的“组”页，然后单击 **+** 图标，以创建新的安全组。  键入名称和描述，然后单击“创建” 。 创建组后，你可以向该组添加用户，方法是单击新创建的安全组的“编辑成员”  。 即在 Azure Active Directory 中创建了安全组。

    ![显示编辑用户角色页上的全局管理员角色选择的页面屏幕截图](../media/AppManagement/OfficePortal_CreateGroups.png)

下表列出了可以分配给管理员用户的权限和角色。

|||
|--|----|
|**角色**|**权限**|
|全局管理员（O365 门户）|对 O365 门户和 Azure AD 门户的访问<br /><br />对 Azure 门户的访问（可以执行角色管理和移动应用管理任务）。|
|所有者角色（Azure 门户）|对 Azure 门户的访问（可以执行角色管理和移动应用管理任务）。|
|参与者角色（Azure 门户）|对 Azure 门户的访问（只可以执行移动应用管理任务）。|

## 将参与者角色分配给用户

**全局管理员** 具有访问 Azure 门户的权限。  如果你希望其他管理员用户能够配置策略和执行其他移动应用管理任务，你可以将 **参与者角色** 分配给用户，如下所述:


1.  在“设置”边栏选项卡中，单击“资源管理”部分的“用户”

    ![Azure 门户上的“用户”边栏选项卡的屏幕截图](../media/AppManagement/AzurePortal_MAM_AddUsers.png)

2.  单击“添加”  以打开“添加访问”  边栏选项卡。

3.  单击“选择一个角色”，然后选择“参与者角色”

    ![Azure 门户上的“选择一个角色”边栏选项卡的屏幕截图](../media/AppManagement/AzurePortal_MAM_AddRole.png)

4.  选择该角色之后，单击“添加用户” ，然后按用户名或电子邮件地址搜索用户。 你在此列表中看到的用户是以前在 Azure AD 中使用 Office 门户创建的前 1000 个用户。 单击“添加访问”  边栏选项卡上的“确定”  以保存角色，并将角色分配给用户。

    ![Azure 门户上的“添加用户”边栏选项卡的屏幕截图](../media/AppManagement/AzurePortal_MAM_AddusertoRole.png)

    > 如果选择未向其分配 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 许可证的用户，则用户将无法访问门户。

## 后续步骤
[使用 Microsoft Intune 创建和部署移动应用管理策略](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


