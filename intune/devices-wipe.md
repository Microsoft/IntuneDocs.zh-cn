---
title: 使用 Microsoft Intune 删除设备上的公司数据 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 删除设备上的公司数据，或者在 Android、Android 工作配置文件、iOS、macOS 或 Windows 设备上恢复出厂设置。 并从 Azure Active Directory 中删除设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 41d8f70dd72e845663f39e151c393f5edc0ad394
ms.sourcegitcommit: 391755a4c8a38e3a22744516fd27d75e40438899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028739"
---
# <a name="remove-devices-by-using-factory-reset-removing-company-data-or-manually-unenrolling-the-device"></a>通过恢复出厂设置、删除公司数据或手动取消注册设备来删除设备

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用“删除公司数据”或“恢复出厂设置”操作，可从 Intune 中删除不再需要的、已重新调整用途的或丢失的设备。 用户还可从 Intune 公司门户中向在 Intune 中注册的个人所有设备发出远程命令。

> [!NOTE]
> 从 Azure Active Directory (Azure AD) 中删除用户前，对与该用户关联的所有设备使用“恢复出厂设置”或“删除公司数据”操作。 如果从 Azure AD 删除具有托管设备的用户，Intune 不再能够向这些设备发出恢复出厂设置或删除公司数据命令。

## <a name="factory-reset"></a>恢复出厂设置

“恢复出厂设置”操作将设备还原为其出厂默认设置。 如果选择“保留注册状态和用户帐户”复选框，则保留用户数据。 否则，驱动器将被安全擦除。

|恢复出厂设置操作|保留注册状态和用户帐户|从 Intune 管理中删除|描述|
|:-------------:|:------------:|:------------:|------------|
|恢复出厂设置| 未选中 | 是 | 擦除所有用户帐户、数据、MDM 策略和设置。 将操作系统重置为其默认状态和设置。|
|恢复出厂设置| 已选中 | 否 | 擦除所有 MDM 策略。 保留用户帐户和数据。 将用户设置重置回默认设置。 将操作系统重置为其默认状态和设置。|

“保留注册状态和用户帐户”选项仅适用于 Windows 10 版本 1709 或更高版本。

将在设备下次连接到 Intune 时重新应用 MDM 策略。

恢复出厂设置可用于在将设备提供给新用户前或在设备丢失或被盗时，对设备进行重置。 请谨慎选择“恢复出厂设置”。 无法恢复设备上的数据。

### <a name="factory-reset-a-device"></a>恢复设备的出厂设置

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备” > “所有设备”。
4. 选择要恢复出厂设置的设备名称。
5. 在显示设备名称的窗格中，选择“恢复出厂设置”。
6. 对于 Windows 10 版本 1709 或更高版本，还具有“保留注册状态和用户帐户”选项。 
    
    |在恢复出厂设置过程中保留|不保留|
    | -------------|------------|
    |与设备关联的用户帐户|用户文件|
    |计算机状态\(域加入、已加入 Azure AD）| 用户安装的应用\(存储和 Win32 应用）|
    |移动设备管理 (MDM) 注册|非默认设备设置|
    |OEM 安装的应用\(存储和 Win32 应用）||
    |用户配置文件||
    |用户配置文件以外的用户数据||
    |用户自动登录|| 
    
         
7. 若要确认恢复出厂设置，请选择“是”。

如果设备已打开并连接，“恢复出厂设置”操作会在 15 分钟内跨所有设备类型进行传播。

## <a name="remove-company-data"></a>删除公司数据

“删除公司数据”操作将删除使用 Intune 分配的托管应用数据（如果适用）、设置和电子邮件配置文件。 设备从 Intune 管理中删除。 这种情况发生在设备下次检入并收到远程“删除公司数据”操作时发生。

“删除公司数据”会将用户的个人数据保留在设备上。  

下表描述了将删除什么数据，以及在删除公司数据后“删除公司数据”操作对设备上保留的数据的影响。

### <a name="ios"></a>iOS

|数据类型|iOS|
|-------------|-------|
|Intune 安装的公司应用和关联数据|卸载应用。 删除公司应用数据。<br /><br />来自使用移动应用程序管理的 Microsoft 应用程序的应用程序数据被删除。 应用程序不会删除。|
|设置|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|
|证书配置文件设置|已删除并吊销证书。|
|管理代理|删除管理配置文件。|
|Email|删除通过 Intune 预配的电子邮件配置文件。 删除设备上缓存的电子邮件。|
|Outlook|删除适用于 iOS 的 Microsoft Outlook 应用接收到的电子邮件。 进行此操作之前，需先将 Outlook 移动应用部署为 iOS 用户的必需应用。|
|Azure AD 脱离|删除 Azure AD 记录。|
|联系人 |删除从应用直接同步到本机通讯簿的联系人。 无法删除从本机通讯簿同步到另一个外部源中的任何联系人。 <br /> <br />目前仅支持 Outlook 应用。

### <a name="android"></a>Android

|数据类型|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Web 链接|删除。|删除。|
|非托管的 Google Play 应用|保留已安装的应用和数据。|保留已安装的应用和数据。|
|非托管的业务线应用|保留已安装的应用和数据。|已卸载应用并删除了应用的本地数据。 未删除应用外的数据（例如 SD 卡上的数据）。|
|托管的 Google Play 应用|删除应用数据。 应用不会删除。 应用（例如 SD 卡）外由移动应用程序管理 (MAM) 加密保护的数据仍然进行加密处理且不可用，但不删除。|删除应用数据。 应用不会删除。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理，但不删除。|
|托管的业务线应用|删除应用数据。 应用不会删除。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理且不可用，但不删除。|删除应用数据。 应用不会删除。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理且不可用，但不删除。|
|设置|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|删除。|
|证书配置文件设置|已撤销证书，但未删除。|已删除并吊销证书。|
|管理代理|撤销设备管理员权限。|撤销设备管理员权限。|
|Email|N/A（Android 设备不支持电子邮件配置文件）|删除通过 Intune 预配的电子邮件配置文件。 删除设备上缓存的电子邮件。|
|Outlook|仅当 Outlook 由 MAM 策略保护时，才会删除 Android 版 Outlook 应用接收的电子邮件。 否则，取消注册设备时不会擦除 Outlook。|仅当 Outlook 由 MAM 策略保护时，才会删除 Android 版 Outlook 应用接收的电子邮件。 否则，取消注册设备时不会擦除 Outlook。|
|Azure AD 脱离|删除 Azure AD 记录。|删除 Azure AD 记录。|
|联系人 |删除从应用直接同步到本机通讯簿的联系人。 无法删除从本机通讯簿同步到另一个外部源中的任何联系人。 <br /> <br />目前仅支持 Outlook 应用。|删除从应用直接同步到本机通讯簿的联系人。 无法删除从本机通讯簿同步到另一个外部源中的任何联系人。 <br /> <br />目前仅支持 Outlook 应用。

### <a name="android-work-profile"></a>Android 工作配置文件

从 Android 工作配置文件设备上删除公司数据将删除该设备上工作配置文件中的所有数据、应用和设置。 设备将从 Intune 管理中停用。 Android 工作配置文件不支持恢复出厂设置。

### <a name="android-enterprise-kiosk-devices"></a>Android 企业展台设备

只能将 Android 展台设备恢复出厂设置。 不能从 Android 展台设备删除公司数据。


### <a name="macos"></a>macOS

|数据类型|macOS|
|-------------|-------|
|设置|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|
|证书配置文件设置|删除并吊销通过 MDM 部署的证书。|
|管理代理|删除管理配置文件。|
|Outlook|如果启用条件访问，设备不会收到新邮件。|
|Azure AD 脱离|删除 Azure AD 记录。|

### <a name="windows"></a>Windows

|数据类型|Windows 8.1 (MDM) 和 Windows RT 8.1|Windows RT|Windows Phone 8.1 和 Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Intune 安装的公司应用和关联数据|对于受 EFS 保护的文件，会撤销密钥。 用户无法打开文件。|未删除公司应用。|卸载最初通过公司门户安装的应用。 删除公司应用数据。|卸载应用。 删除旁加载密钥。<br>对于 Windows 10 版本 1703（创意者更新）及更高版本，不会删除 Office 365 专业增强版应用。|
|设置|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|删除。|不支持。|删除。|
|证书配置文件设置|已删除并吊销证书。|已删除并吊销证书。|不支持。|已删除并吊销证书。|
|Email|删除已启用 EFS 的电子邮件。 这包括适用于 Windows 的邮件应用中的电子邮件和附件。|不支持。|删除通过 Intune 预配的电子邮件配置文件。 删除设备上缓存的电子邮件。|删除已启用 EFS 的电子邮件。 这包括适用于 Windows 的邮件应用中的电子邮件和附件。 删除由 Intune 预配的邮件帐户。|
|Azure AD 脱离|不能。|不能。|删除 Azure AD 记录。|不适用。 在 Windows 10 中，无法删除已加入 Azure AD 设备的公司数据。|

### <a name="remove-company-data"></a>删除公司数据

1. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)。
2. 在“设备”窗格中，选择“所有设备”。
3. 选择想要从中删除公司数据的设备名称。
4. 在显示设备名称的窗格中，选择“删除公司数据”。 选择“是”以确认。

如果设备已打开并连接，“删除公司数据”操作会在 15 分钟内跨所有设备类型进行传播。

## <a name="delete-devices-from-the-intune-portal"></a>从 Intune 门户中删除设备

如果要从 Intune 门户中删除设备，可以从特定设备窗格中删除它们。 下次设备检入时，其上的任何公司数据都将被删除。

1. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)。
2. 选择“设备” > “所有设备”>“选择要删除的设备”>“删除”。

### <a name="automatically-delete-devices-with-cleanup-rules"></a>使用清理规则自动删除设备
可配置 Intune 以自动删除看似非活动、过时或无响应的设备。 这些清理规则会持续监控设备清单，以便设备记录保持最新。 以这种方式删除的设备将从 Intune 管理中删除。
1. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)。
2. 选择“设备” > “设备清理规则” > “是”。
3. 在“删除指定天数未签入的设备”框中，输入介于 90 和 270 的数字。
4. 选择 **“保存”**。



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>从 Azure Active Directory 门户删除设备

由于通信问题或设备丢失，可能需要从 Azure AD 删除设备。 可以使用“删除”操作从 Azure 门户中删除已知无法访问且不太可能再与 Azure 通信的设备记录。 “删除”操作不会从管理中删除设备。

1.  使用管理员凭据登录 [Azure 门户中的 Azure Active Directory](http://aka.ms/accessaad)。 还可以登录到 [Office 365 门户](https://portal.office.com)。 从菜单中，选择“管理中心” > “Azure AD”。
2.  创建 Azure 订阅（如果没有）。 如果有付费帐户，应该不需要提供信用卡或付款（选择“注册免费的 Azure Active Directory”订阅链接）。
3.  选择“Azure Active Directory”，然后选择组织。
4.  选择“用户”  选项卡。
5. 选择与想要删除的设备相关联的用户。
6.  选择“设备”。
7.  根据需要删除设备。 例如，可删除那些不再使用的设备或者定义不准确的设备。

## <a name="retire-an-apple-dep-device-from-intune"></a>从 Intune 停用 Apple DEP 设备

如果想要通过 Intune 从管理完全删除 Apple DEP 设备，请按以下步骤进行操作：

1. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)。
2. 选择“设备” > “所有设备”，再依次选择相关设备和“删除公司数据”。
![显示删除公司数据的屏幕截图](./media/devices-wipe/remove-company-data.png)
3. 选择“设备注册” > “Apple 注册” > “注册计划令牌”，再选择相关令牌和“设备”，然后选择相关设备的复选框，最后选择“删除” > “是”。
![显示删除设备的屏幕截图](./media/devices-wipe/delete-device.png)
4. 访问 [deploy.apple.com](http://deploy.apple.com)，并按序列号搜索设备。
5. 在“分配到”菜单中，选择“未分配”。

6. 选择“重新分配”。

    ![显示 Apple 重新分配的屏幕截图](./media/devices-wipe/apple-reassign.png)

## <a name="next-steps"></a>后续步骤

如果要重新注册已删除的设备，请参阅[注册选项](enrollment-options.md)。

