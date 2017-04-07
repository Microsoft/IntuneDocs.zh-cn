---
title: "移动设备注册的先决条件 | Microsoft Docs"
description: "设置移动设备管理 (MDM) 先决条件并准备好注册不同的操作系统。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7beff3bf4579d9fb79f0c3f2fb8fbf9bb1ea160
ms.openlocfilehash: fc97e1266c2e859104b21f3bf4ff24f33123f66a
ms.lasthandoff: 02/22/2017


---

# <a name="prerequisites-for-mobile-device-management-in-intune"></a>Intune 中移动设备管理的先决条件

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

要使员工能在 Intune 中注册移动设备，需要执行以下步骤。 管理公司拥有的设备需要同样的步骤。

|步骤|详细信息|  
|-----------|-------------|  
|**步骤 1：**[启用连接](#step-1-enable-connections)|确保配置自定义域名并将网络通信准备就绪|  
|**步骤 2：**[设置 MDM 机构](#step-2-set-mdm-authority)|移动设备管理机构定义分配给设备的服务|
|**步骤 3：**[创建组](#step-3-create-groups)|配置公司门户应用中面向用户的设置|  
|**步骤 4：**[配置公司门户](#step-4-configure-company-portal)|配置公司门户应用中面向用户的设置|  
|**步骤 5**：[分配用户许可证](#step-5-assign-user-licenses)|将 Intune 许可证分配给用户，以便他们能够注册设备|
|**步骤 6**：[启用注册](#step-6-enable-enrollment)|为 iOS 和 Windows 管理启用特定平台的设置。 Android 设备不需要其他配置。|
|**步骤 7：**[后续步骤](#step-7-next-steps)|为 iOS 和 Windows 管理启用特定平台的设置。 Android 设备不需要其他配置。|

想要使用 Configuration Manager 查找 Intune？
> [!div class="button"]
[查看 SCCM 文档 >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## <a name="step-1-enable-connections"></a>步骤 1：启用连接

启用移动设备注册前，请确保已完成以下步骤：
- [查看所需网络 URL 和端口](../get-started/network-infrastructure-requirements-for-microsoft-intune.md)
- [添加并验证域名](../get-started/domain-names-for-microsoft-intune.md)

## <a name="step-2-set-mdm-authority"></a>步骤 2：设置 MDM 机构
MDM 机构定义有权管理一组设备的管理服务。 适用于 MDM 机构的选项包括 Intune 本身以及带 Intune 的 Configuration Manager。 如果将 Configuration Manager 设置为管理机构，则没有其他服务可以用于移动设备管理。

>[!IMPORTANT]
> 请仔细考虑是希望仅使用 Intune（联机服务），还是使用带 Intune 的 System Center Configuration Manager（与联机服务相结合的本地软件解决方案）来管理移动设备。 设置移动设备管理机构后，如果没有 Microsoft 支持部门的帮助，将无法对其进行更改。 有关说明，请参阅[如果选择了错误的 MDM 机构设置怎么办](#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)。


1.  在“[Microsoft Intune 管理控制台](http://manage.microsoft.com)”中，选择“**管理员**”&gt;“**移动设备管理**”。

2.  在“任务”  列表中，单击“设置移动设备管理机构” 。 将打开“设置 MDM 机构”  对话框。

    ![“设置 MDM 机构”对话框](../media/intune-mdm-authority.png)

3.  Intune 要求确认你希望使用 Intune 作为 MDM 机构。 勾选复选框，然后选择“**是**”以使用 Microsoft Intune 管理移动设备。

## <a name="step-3-create-groups"></a>步骤 3：创建组

可通过创建用户和设备组，简化管理和提高已部署应用、策略和公司资源的目标。 [了解如何创建组](use-groups-to-manage-users-and-devices-with-microsoft-intune.md#create-groups)。

## <a name="step-4-configure-company-portal"></a>步骤 4：配置公司门户

在 Intune 公司门户中，用户可以访问公司数据和执行常见任务，比如注册设备、安装应用，以及查找信息以从 IT 部门获得帮助。

> [!TIP]
> 当你自定义公司门户时，配置会同时应用于公司门户网站和公司门户应用。

自定义公司门户有助于为最终用户提供熟悉且有帮助的体验。 为此，只需以租户或服务管理员身份登录到“[Microsoft Intune 管理员控制台](https://manage.microsoft.com)”，选择“**管理员**”&gt;“**公司门户**”，然后配置公司门户设置。

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### <a name="company-contact-information-and-privacy-statement"></a>公司联系人信息和隐私声明

公司名称显示为公司门户的标题。 联系人信息和详细信息将在公司门户的“联系 IT 部门”屏幕中向用户显示。 当用户单击隐私链接时，将显示隐私声明。

|字段名称|最大长度|更多信息|
    |----------|------------------------|----------------|
    |公司名称|40|此名称显示为公司门户的标题。 **注意**：仅支持字母数字字符。 此字段不支持特殊字符。|
    |IT 部门联系人姓名|40|此名称显示在“联系 IT”页上。|
    |IT 部门的电话号码|20|此联系人号码显示在“联系 IT”页上。|
    |IT 部门的电子邮件地址|40|此联系人地址显示在“联系 IT”页上。 必须以 **alias@domainname.com** 格式输入有效的电子邮件地址。|
    |其他信息|120|此信息显示在“**联系 IT**”页上。|
    |公司隐私声明 URL|79|你可以指定自己的公司隐私声明，当用户从公司门户中单击隐私链接时，该隐私声明将出现。 必须以 https://www.contoso.com 格式输入有效的 URL。|

### <a name="support-contacts"></a>支持联系人
在公司门户向用户显示支持网站，以使他们能够访问在线支持。

|字段名称|最大长度|更多信息|
    |----------|------------------------|----------------|
    |支持网站 URL|150|如果你拥有希望用户可以使用的支持网站，请在此处指定 URL。 该 URL 必须采用 https://www.contoso.com 格式。 如果不指定 URL，则公司门户中的“联系 IT”页上将不会显示支持网站的任何内容。|
    |网站名称|40|此名称是为支持网站的 URL 显示的友好名称。 如果指定支持网站 URL 而不指定友好名称，则公司门户中的“联系 IT”页上将显示“转到 IT 网站”。|


### <a name="company-branding-customization"></a>公司品牌自定义

你可以使用公司徽标、公司名称、主题颜色和背景来自定义公司门户。

|字段名称|更多信息|
    |----------|----------------|
    |主题颜色|选择要应用于公司门户的主题颜色。|
    |包括公司徽标|如果启用此选项，你可以上传公司徽标以显示在公司门户中。 你可以上传两个徽标：一个在公司门户背景为白色时显示的徽标，以及一个在公司门户背景使用所选主题颜色时使用的徽标。 每个徽标必须是 .png 或 .jpg 文件，最大分辨率为 400 x 100 像素，大小等于或小于 750 KB。|
    |为公司门户应用选择背景|此设置只影响公司门户应用的背景。|


保存更改之后，你可以使用管理控制台的“**公司门户**”页面底部提供的链接来查看公司门户网站。 无法更改这些链接。 当用户登录时，这些链接将在公司门户中显示你的订阅。

## <a name="step-5-assign-user-licenses"></a>步骤 5：分配用户许可证

使用 **Office 365 管理门户**手动添加基于云的用户并将许可证分配给基于云的用户帐户和从本地 Active Directory 同步到 Azure Active Directory (Azure AD) 的帐户。 可[将本地用户同步到 Azure AD](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md#how-to-sync-on-premises-users-with-azure-ad)。

1.  使用你的租户管理员凭据登录到 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)。

2.  选择你想要为其分配 Intune 用户许可证的用户帐户，然后在用户帐户属性上勾选“**Microsoft Intune**”复选框。

3.  用户帐户即会添加到 Microsoft Intune 用户组，该用户组授予用户使用该服务和将设备注册到管理中的权限。

### <a name="to-synchronize-on-premises-users-with-azure-ad"></a>将本地用户与 Azure AD 同步

1. 在本地 Active Directory 中，为你的自定义域[添加 UPN 后缀](https://technet.microsoft.com/en-us/library/cc772007.aspx)。
2. 为计划导入的本地用户设置新的 UPN 后缀。
3. 运行 [Azure AD Connect 同步](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/)，以将本地用户与 Azure AD 集成。
4. 成功同步用户帐户信息后，你可以使用 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)分配 Microsoft Intune 许可证。

## <a name="step-6-enable-enrollment"></a>步骤 6：启用注册
设置 MDM 机构之后，需要为组织要支持的操作系统设置设备管理。 设置设备管理所需的步骤因操作系统而异。 例如，Android OS 不需要你在 Intune 管理控制台中执行任何操作。 另一方面，Windows 和 iOS 需要设备与 Intune 之间存在信任关系才能允许进行管理。

为下列平台设置管理：
- [iOS 和 Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Android](set-up-android-management-with-microsoft-intune.md)
- [Android for Work](set-up-android-for-work.md)
- [Windows 电脑和笔记本电脑](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows 10 移动版和 Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

还可以启用[公司拥有设备的注册](manage-corporate-owned-devices.md)。

## <a name="step-7-next-steps"></a>步骤 7：后续步骤

现已启用注册，应设置管理以满足业务需要。 以下是一些管理选项：

- [部署管理设备上的设置和功能的策略](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
- [启用对公司资源（如电子邮件、Wi-Fi 和 VPN）的访问](enable-access-to-company-resources-with-microsoft-intune.md)
- [添加应用](add-apps.md)和[部署应用](deploy-apps.md)到托管设备
- [创建设备合规性策略](introduction-to-device-compliance-policies-in-microsoft-intune.md)和[基于合规性限制访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)

## <a name="what-to-do-if-you-choose-the-wrong-mdm-authority-setting"></a>如果选择了错误的 MDM 机构设置怎么办

如果确定选择了错误的 MDM 机构设置并需要对其进行更改，则必须与 Microsoft 支持部门联系。 无法自行更改该设置。 联系 Microsoft 支持部门之前，请查看以下信息（Microsoft 支持部门需要获得这些信息才能进行更改）。

有三种方法可以重置 MDM 机构。 在支持请求中，需要选择适用于你的情况的方式。 如果请求的方案未列出，请进而与 Microsoft 支持部门联系。

Microsoft 支持部门将让你确认下列信息：

- 租户 ID：用于登录到服务的域（例如 intune.onmicrosoft.com）
- 想要更改为该机构的 MDM 机构
- 确认已完成的必需步骤，如下所示

如果正在使用共存，则需要验证 Intune 和 Office 365 清单。

### <a name="reset-mdm-authority-from-intune-to-configuration-manager"></a>将 MDM 机构从 Intune 重置为 Configuration Manager

请在联系 Microsoft 支持部门之前完成这些步骤以重置 MDM 机构。

- 从 Intune 管理员控制台停用所有设备。 请勿尝试从设备停用设备。 
- 删除 Service To Service Connector（“管理” > “移动设备管理” > “Microsoft Exchange”下），或禁用 Exchange Connector（如果已设置）。 
- 在“管理员” > “设备注册管理器”中删除设备注册管理器角色。
- 在“管理员” > “移动设备管理” > “设备组映射”中关闭设备组映射。
- 从“管理员” > “移动设备管理” > “Windows” > “旁加载密钥”删除旁加载密钥。
- 在“管理员” > “移动设备管理” > “iOS”页中，删除 iOS APN 证书。
- 在“管理员” > “移动设备管理” > “iOS”页中，删除 iOS DEP 令牌。
- 在“策略” > “配置策略”下，删除适用于 MDM 设备的所有策略。
- 在“应用” > “托管软件”中，删除适用于 MDM 设备的所有已发布应用程序。

### <a name="reset-mdm-authority-from-configuration-manager-to-intune"></a>将 MDM 机构从 Configuration Manager 重置为 Intune

请在联系 Microsoft 支持部门之前完成这些步骤以重置 MDM 机构。

- 从 Configuration Manager 控制台停用所有设备（作为移动设备管理的设备）。 请勿尝试从设备停用设备。 
- 删除 Intune 用户组中的所有用户。 将 Intune 订阅指向空用户集合，或删除目标集合中的所有用户。  在 CloudUserSync.log 中确认用户已删除。 
- 取消选中 iOS 平台以清除 APN 证书。
- 删除适用于 MDM 设备的所有已发布应用程序。
- 删除适用于 MDM 设备的所有策略。 
- 从 Configuration Manager 控制台（仅适用于 R2 SP1 或更低版本）删除 Windows Intune 连接器。
通过右键单击订阅并选择“删除”，可删除 Intune 订阅。
- 重启 SMS Executive 服务。
- 请提供一些示例用户，以便完成该过程后，我们可以验证 Configuration Manager 许可证已删除。

### <a name="reset-mdm-authority-from-office-365-to-configuration-manager"></a>将 MDM 机构从 Office 365 重置为 Configuration Manager

1. 导航到 [https://protection.office.com](https://protection.office.com)。
2. 选择“安全策略”选项卡，然后选择“设备管理”。 
3. 通过选择“选择性擦除”停用所有设备。 请勿尝试从设备停用设备。 如果已禁用“选择性擦除”，则不需要进一步操作。
4. 选择“安全策略”选项卡，然后选择“安全策略”。 
5. 对所有现有策略选择“删除”。 如果策略都处于挂起状态，则不需要进一步操作。

>[!NOTE]
>无法删除 IOS APN 证书，该证书仍附加到帐户。 

### <a name="next-steps-for-mdm-authority-resets"></a>MDM 机构重置的后续步骤

Microsoft 支持部门验证适用清单上的项后，重置 MDM 机构最多需要&3; 个工作日，但通常在一天之内完成。 

>[!IMPORTANT]
>在 Microsoft 支持部门确认已成功完成重置之前，请勿尝试配置订阅！ 过早配置可能会导致损坏并/或影响 Intune 服务的使用。 

