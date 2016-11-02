---
title: "移动设备注册的先决条件 | Microsoft Intune"
description: "设置移动设备管理 (MDM) 先决条件并准备好注册不同的操作系统。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 92e40930c0ccbeb3d98bef43b115fd92f24beaef
ms.openlocfilehash: 93a29266ad9d18f444f0cc0c5aadf9b414eedfa2


---

# Intune 中移动设备管理的先决条件
要使员工能在 Intune 中注册移动设备，需要执行以下步骤。 管理公司拥有的设备需要同样的步骤。

|步骤|详细信息|  
|-----------|-------------|  
|**步骤 1：**[启用连接](#step-1-enable-connections)|确保配置自定义域名并将网络通信准备就绪|  
|**步骤 2：**[设置 MDM 机构](#step-2-set-mdm-authority)|移动设备管理机构定义分配给设备的服务|
|**步骤 3：**[配置公司门户](#step-3-configure-company-portal)|配置公司门户应用中面向用户的设置|  
|**步骤 4：**[分配用户许可证](#step-4-assign-user-licenses)|将 Intune 许可证分配给用户，以便他们能够注册设备|
|**步骤 5：**[启用注册](#step-5-enable-enrollment)|为 iOS 和 Windows 管理启用特定平台的设置。 Android 设备不需要其他配置。|

想要使用 Configuration Manager 查找 Intune？
> [!div class="button"]
[查看 SCCM 文档 >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## 步骤 1：启用连接

启用移动设备注册前，请确保已完成以下步骤：
- [查看所需网络 URL 和端口](../get-started/network-infrastructure-requirements-for-microsoft-intune)
- [添加并验证域名](../get-started/domain-names-for-microsoft-intune)

## 步骤 2：设置 MDM 机构
MDM 机构定义有权管理一组设备的管理服务。 适用于 MDM 机构的选项包括 Intune 本身以及带 Intune 的 Configuration Manager。 如果将 Configuration Manager 设置为管理机构，则没有其他服务可以用于移动设备管理。

>[!IMPORTANT]
> 请仔细考虑是希望仅使用 Intune（联机服务），还是使用带 Intune 的 System Center Configuration Manager（与联机服务相结合的本地软件解决方案）来管理移动设备。 设置移动设备管理机构之后，无法进行更改。



1.  在“[Microsoft Intune 管理控制台](http://manage.microsoft.com)”中，选择“**管理员**”&gt;“**移动设备管理**”。

2.  在“任务”  列表中，单击“设置移动设备管理机构” 。 将打开“设置 MDM 机构”  对话框。

    ![“设置 MDM 机构”对话框](../media/intune-mdm-authority.png)

3.  Intune 要求确认你希望使用 Intune 作为 MDM 机构。 勾选复选框，然后选择“**是**”以使用 Microsoft Intune 管理移动设备。

## 步骤 3：配置公司门户

在 Intune 公司门户中，用户可以访问公司数据和执行常见任务，比如注册设备、安装应用，以及查找信息以从 IT 部门获得帮助。

> [!TIP]
> 当你自定义公司门户时，配置会同时应用于公司门户网站和公司门户应用。

自定义公司门户有助于为最终用户提供熟悉且有帮助的体验。 为此，只需以租户或服务管理员身份登录到“[Microsoft Intune 管理员控制台](https://manage.microsoft.com)”，选择“**管理员**”&gt;“**公司门户**”，然后配置公司门户设置。

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### 公司联系人信息和隐私声明

公司名称显示为公司门户的标题。 联系人信息和详细信息将在公司门户的“联系 IT 部门”屏幕中向用户显示。 当用户单击隐私链接时，将显示隐私声明。

|字段名称|最大长度|更多信息|
    |----------|------------------------|----------------|
    |公司名称|40|此名称显示为公司门户的标题。 **注意**：仅支持字母数字字符。 此字段不支持特殊字符。|
    |IT 部门联系人姓名|40|此名称显示在“联系 IT”页上。|
    |IT 部门的电话号码|20|此联系人号码显示在“联系 IT”页上。|
    |IT 部门的电子邮件地址|40|此联系人地址显示在“联系 IT”页上。 必须输入格式为 **alias@domainname.com** 的有效电子邮件地址。|
    |其他信息|120|此信息显示在“**联系 IT**”页上。|
    |公司隐私声明 URL|79|你可以指定自己的公司隐私声明，当用户从公司门户中单击隐私链接时，该隐私声明将出现。 必须以 https://www.contoso.com 格式输入有效的 URL。|

### 支持联系人
在公司门户向用户显示支持网站，以使他们能够访问在线支持。

|字段名称|最大长度|更多信息|
    |----------|------------------------|----------------|
    |支持网站 URL|150|如果你拥有希望用户可以使用的支持网站，请在此处指定 URL。 该 URL 必须采用 https://www.contoso.com 格式。 如果不指定 URL，则公司门户中的“联系 IT”页上将不会显示支持网站的任何内容。|
    |网站名称|40|此名称是为支持网站的 URL 显示的友好名称。 如果指定支持网站 URL 而不指定友好名称，则公司门户中的“联系 IT”页上将显示“转到 IT 网站”。|


### 公司品牌自定义

你可以使用公司徽标、公司名称、主题颜色和背景来自定义公司门户。

|字段名称|更多信息|
    |----------|----------------|
    |主题颜色|选择要应用于公司门户的主题颜色。|
    |包括公司徽标|如果启用此选项，你可以上传公司徽标以显示在公司门户中。 你可以上传两个徽标：一个在公司门户背景为白色时显示的徽标，以及一个在公司门户背景使用所选主题颜色时使用的徽标。 每个徽标必须是 .png 或 .jpg 文件，最大分辨率为 400 x 100 像素，大小等于或小于 750 KB。|
    |为公司门户应用选择背景|此设置只影响公司门户应用的背景。|


保存更改之后，你可以使用管理控制台的“**公司门户**”页面底部提供的链接来查看公司门户网站。 无法更改这些链接。 当用户登录时，这些链接将在公司门户中显示你的订阅。

## 步骤 4：分配用户许可证

使用 **Office 365 管理门户**手动添加基于云的用户并将许可证分配给基于云的用户帐户和从本地 Active Directory 同步到 Azure Active Directory (Azure AD) 的帐户。 可[将本地用户同步到 Azure AD](../get-started/domain-names-for-microsoft-intune#to-synchronize-on-premises-users-with-azure-ad.md)。

1.  使用你的租户管理员凭据登录到 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)。

2.  选择你想要为其分配 Intune 用户许可证的用户帐户，然后在用户帐户属性上勾选“**Microsoft Intune**”复选框。

3.  用户帐户即会添加到 Microsoft Intune 用户组，该用户组授予用户使用该服务和将设备注册到管理中的权限。

### 将本地用户与 Azure AD 同步

1. 在本地 Active Directory 中，为你的自定义域[添加 UPN 后缀](https://technet.microsoft.com/en-us/library/cc772007.aspx)。
2. 为计划导入的本地用户设置新的 UPN 后缀。
3. 运行 [Azure AD Connect 同步](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/)，以将本地用户与 Azure AD 集成。
4. 成功同步用户帐户信息后，你可以使用 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)分配 Microsoft Intune 许可证。

## 步骤 5：启用注册
设置 MDM 机构之后，需要为组织要支持的操作系统设置设备管理。 设置设备管理所需的步骤因操作系统而异。 例如，Android OS 不需要你在 Intune 管理控制台中执行任何操作。 另一方面，Windows 和 iOS 需要设备与 Intune 之间存在信任关系才能允许进行管理。

为下列平台设置管理：
- [Android](set-up-android-management-with-microsoft-intune.md)
- [iOS 和 Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Windows 电脑和笔记本电脑](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows 10 移动版和 Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

你还可以：
 - 使用 [设备注册管理器帐户](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) 注册多个设备。
 - [使用 IMEI 号码指定公司自有设备](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) 以帮助注册设备和目标策略。



<!--HONumber=Oct16_HO3-->


