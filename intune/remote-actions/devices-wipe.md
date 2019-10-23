---
title: 使用 Microsoft Intune 停用或擦除设备 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 在 Android、Android 工作配置文件、iOS、macOS 或 Windows 设备上停用或擦除设备。 并从 Azure Active Directory 中删除设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbcc50d275a3d3e6a613640e96b363ce7608da81
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508563"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>使用“擦除”或“停用”操作删除设备，或手动取消注册设备

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用“停用”  或“擦除”  操作，可从 Intune 中删除不再需要的、已重新调整用途的或丢失的设备。 用户还可从 Intune 公司门户向注册到 Intune 的设备发出远程命令。

> [!NOTE]
> 从 Azure Active Directory (Azure AD) 中删除用户前，对与该用户关联的所有设备使用“擦除”或“停用”操作   。 如果从 Azure AD 删除具有托管设备的用户，Intune 将不再能够擦除或停用这些设备。

## <a name="wipe"></a>擦除

“擦除”操作将设备还原为出厂默认设置  。 如果选择“保留注册状态和用户帐户”  复选框，则保留用户数据。 否则，将删除所有数据、应用和设置。

|擦除操作|保留注册状态和用户帐户 |从 Intune 管理中删除|描述|
|:-------------:|:------------:|:------------:|------------|
|**擦除**| 未选中 | 是 | 擦除所有用户帐户、数据、MDM 策略和设置。 将操作系统重置为其默认状态和设置。|
|**擦除**| 已选中 | 否 | 擦除所有 MDM 策略。 保留用户帐户和数据。 将用户设置重置回默认设置。 将操作系统重置为其默认状态和设置。|


> [!NOTE]
> 擦除操作不适用于通过用户注册进行注册的 iOS 设备。

“保留注册状态和用户帐户”  选项仅适用于 Windows 10 版本 1709 或更高版本。

将在设备下次连接到 Intune 时重新应用 MDM 策略。

擦除可用于在将设备提供给新用户前或在设备丢失或被盗时，对设备进行重置。 请谨慎选择“擦除”  。 无法恢复设备上的数据。

### <a name="wiping-a-device"></a>擦除设备

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 选择“设备” > “所有设备”   。
4. 选择要擦除的设备的名称。
5. 在显示设备名称的窗格中，选择“擦除”  。
6. 对于 Windows 10 版本 1709 或更高版本，还具有“保留注册状态和用户帐户”选项  。 
    
    |在擦除过程中保留 |不保留|
    | -------------|------------|
    |与设备关联的用户帐户|用户文件|
    |计算机状态\(域加入、已加入 Azure AD）| 用户安装的应用\(存储和 Win32 应用）|
    |移动设备管理 (MDM) 注册|非默认设备设置|
    |OEM 安装的应用\(存储和 Win32 应用）||
    |用户配置文件||
    |用户配置文件以外的用户数据||
    |用户自动登录|| 
    
         
7. 若要确认擦除，请选择“是”  。

如果设备已打开并连接，“擦除”操作会在 15 分钟内跨所有设备类型进行传播  。

## <a name="retire"></a>停用

“停用”操作将删除使用 Intune 分配的托管应用数据（如果适用）、设置和电子邮件配置文件  。 设备从 Intune 管理中删除。 这种情况在设备下次检入并收到远程  “停用”操作时发生。 设备仍会显示在 Intune 中，直到设备签入。 如果要立即删除过时设备，请改用[删除操作](devices-wipe.md#delete-devices-from-the-intune-portal)。

“停用”  会将用户个人数据保留在设备上。  

下表描述了将删除什么数据，以及在删除公司数据后“停用”操作对设备上保留的数据的影响  。

### <a name="ios"></a>iOS

|数据类型|iOS|
|-------------|-------|
|Intune 安装的公司应用和关联数据|**使用公司门户安装的应用：** 对于固定到管理配置文件的应用，将删除所有应用数据和应用。 这些应用包括最初从应用商店安装且后来作为公司应用管理的应用。 <br /><br /> **使用移动应用管理并从应用商店安装的 Microsoft 应用：** 对于非公司门户托管的应用，将删除受应用本地存储中的移动应用程序管理 (MAM) 加密保护的公司应用数据。 受应用外部的 MAM 加密保护的数据仍然是加密且不可用的，但不会删除。 不会删除个人应用数据和应用。|
|设置|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|
|证书配置文件设置|已删除并吊销证书。|
|管理代理|删除管理配置文件。|
|Email|删除通过 Intune 预配的电子邮件配置文件。 删除设备上缓存的电子邮件。|
|Azure AD 脱离|删除 Azure AD 记录。|

### <a name="android"></a>Android

|数据类型|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Web 链接|删除。|删除。|
|非托管的 Google Play 应用|保留已安装的应用和数据。 <br /> <br />删除受应用本地存储中的移动应用管理 (MAM) 加密保护的公司应用数据。 受应用外部的 MAM 加密保护的数据仍然是加密且不可用的，但不会删除。 |保留已安装的应用和数据。 <br /> <br />删除受应用本地存储中的移动应用管理 (MAM) 加密保护的公司应用数据。 受应用外部的 MAM 加密保护的数据仍然是加密且不可用的，但不会删除。|
|非托管的业务线应用|保留已安装的应用和数据。|已卸载应用并删除了应用的本地数据。 未删除应用外的数据（例如 SD 卡上的数据）。|
|托管的 Google Play 应用|删除应用数据。 应用不会删除。 应用（例如 SD 卡）外由移动应用程序管理 (MAM) 加密保护的数据仍然进行加密处理且不可用，但不删除。|删除应用数据。 应用不会删除。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理，但不删除。|
|托管的业务线应用|删除应用数据。 应用不会删除。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理且不可用，但不删除。|删除应用数据。 应用不会删除。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理且不可用，但不删除。|
|设置|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|删除。|
|证书配置文件设置|已撤销证书，但未删除。|已删除并吊销证书。|
|管理代理|撤销设备管理员权限。|撤销设备管理员权限。|
|Email|N/A（Android 设备不支持电子邮件配置文件）|删除通过 Intune 预配的电子邮件配置文件。 删除设备上缓存的电子邮件。|
|Azure AD 脱离|删除 Azure AD 记录。|删除 Azure AD 记录。|

### <a name="android-work-profile"></a>Android 工作配置文件

从 Android 工作配置文件设备上删除公司数据将删除该设备上工作配置文件中的所有数据、应用和设置。 设备将从 Intune 管理中停用。 Android 工作配置文件不支持擦除。

### <a name="android-enterprise-kiosk-devices"></a>Android 企业展台设备

只能擦除展台设备。 不能停用 Android 展台设备。


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
|Intune 安装的公司应用和关联数据|对于受 EFS 保护的文件，会撤销密钥。 用户无法打开文件。|未删除公司应用。|卸载最初通过公司门户安装的应用。 删除公司应用数据。|卸载应用。 删除旁加载密钥。<br>对于 Windows 10 版本 1703（创意者更新）及更高版本，不会删除 Office 365 专业增强版应用。 在未注册设备上不会卸载已安装 Intune 管理扩展的 Win32 应用。 管理员可利用分配排除避免向 BYOD 设备提供 Win32 应用。|
|设置|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置。 用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|删除。|不支持。|删除。|
|证书配置文件设置|已删除并吊销证书。|已删除并吊销证书。|不支持。|已删除并吊销证书。|
|Email|删除已启用 EFS 的电子邮件。 这包括适用于 Windows 的邮件应用中的电子邮件和附件。|不支持。|删除通过 Intune 预配的电子邮件配置文件。 删除设备上缓存的电子邮件。|删除已启用 EFS 的电子邮件。 这包括适用于 Windows 的邮件应用中的电子邮件和附件。 删除由 Intune 预配的邮件帐户。|
|Azure AD 脱离|不能。|不能。|删除 Azure AD 记录。|删除 Azure AD 记录。|

> [!NOTE]
> 对于在初始安装过程 (OOBE) 中加入 Azure AD 的 Windows 10 设备，停用命令将从设备中删除所有 Azure AD 帐户。 按照[在安全模式下启动电脑](https://support.microsoft.com/en-us/help/12376/windows-10-start-your-pc-in-safe-mode)中的步骤，以本地管理员身份登录，重新获得对用户本地数据的访问权限。 

### <a name="retire"></a>停用

1. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)。
2. 在“设备”窗格中，选择“所有设备”   。
3. 选择要停用的设备的名称。
4. 在显示设备名称的窗格中，选择“停用”  。 选择“是”以确认  。

如果设备已打开并连接，“停用”操作会在 15 分钟内跨所有设备类型进行传播  。

## <a name="delete-devices-from-the-intune-portal"></a>从 Intune 门户中删除设备

如果要从 Intune 门户中删除设备，可以从特定设备窗格中删除它们。 下次设备检入时，其上的任何公司数据都将被删除。

1. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)。
2. 选择  “设备” >   “所有设备”>“选择要删除的设备”>“删除”  。

### <a name="automatically-delete-devices-with-cleanup-rules"></a>使用清理规则自动删除设备
可配置 Intune 以自动删除看似非活动、过时或无响应的设备。 这些清理规则会持续监控设备清单，以便设备记录保持最新。 以这种方式删除的设备将从 Intune 管理中删除。
1. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)。
2. 选择“设备”   > “设备清理规则”   > “是”  。
3. 在“删除这么多天尚未签入的设备”  框中，输入介于 30 和 270 的数字。
4. 选择 **“保存”** 。



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>从 Azure Active Directory 门户删除设备

由于通信问题或设备丢失，可能需要从 Azure AD 删除设备。 可以使用“删除”操作从 Azure 门户中删除已知无法访问且不太可能再与 Azure 通信的设备记录  。 “删除”操作不会从管理中删除设备  。

1. 使用管理员凭据登录 [Azure 门户中的 Azure Active Directory](https://aka.ms/accessaad)。 还可以登录到 [Microsoft 365 管理中心](https://admin.microsoft.com)。 从菜单中，选择“管理中心” > “Azure AD”   。
2. 创建 Azure 订阅（如果没有）。 如果有付费帐户，应该不需要提供信用卡或付款（选择“注册免费的 Azure Active Directory”订阅链接）  。
3. 选择“Azure Active Directory”，然后选择组织  。
4. 选择“用户”  选项卡。
5. 选择与想要删除的设备相关联的用户。
6. 选择“设备”  。
7. 根据需要删除设备。 例如，可删除那些不再使用的设备或者定义不准确的设备。

## <a name="retire-an-apple-dep-device-from-intune"></a>从 Intune 停用 Apple DEP 设备

如果想要通过 Intune 从管理完全删除 Apple DEP 设备，请按以下步骤进行操作：

1. 登录到 [Azure 门户中的 Intune](https://aka.ms/intuneportal)。
2. 选择“设备” > “所有设备”，再依次选择相关设备和“停用”    。
![停用的屏幕截图](./media/devices-wipe/retire.png)
3. 访问 [deploy.apple.com](http://deploy.apple.com)，并按序列号搜索设备。
4. 在“分配到”菜单中，选择“未分配”   。

5. 选择“重新分配”  。

    ![显示 Apple 重新分配的屏幕截图](./media/devices-wipe/apple-reassign.png)

## <a name="fresh-start"></a>全新启动

适用于 Windows 10 设备。 了解有关[全新启动](device-fresh-start.md)的详细信息。

## <a name="next-steps"></a>后续步骤

如果要重新注册已删除的设备，请参阅[注册选项](../enrollment/enrollment-options.md)。

