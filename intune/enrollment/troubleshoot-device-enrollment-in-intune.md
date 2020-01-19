---
title: 设备注册疑难解答
titleSuffix: Microsoft Intune
description: 有关如何排查 Microsoft Intune 中设备注册问题的建议。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328a578f4d2ada41bed17839f1f85b3b9add80fa
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885951"
---
# <a name="troubleshoot-device-enrollment-in-microsoft-intune"></a>Microsoft Intune 设备注册疑难解答

本文针对[设备注册](device-enrollment.md)问题排查提供了相关建议。 如果此信息未解决你的问题，请参阅[如何获取对 Microsoft Intune 的支持](../fundamentals/get-support.md)，了解更多获得帮助的方法。


## <a name="initial-troubleshooting-steps"></a>初始故障排除步骤

开始故障排除之前，请检查确保你已正确配置 Intune 以启用注册。 可以在此处了解这些配置要求：

- [为在 Microsoft Intune 中注册设备做好准备](../fundamentals/setup-steps.md)
- [设置 iOS 和 Mac 设备管理](../ios-enroll.md)
- [设置 Windows 设备管理](windows-enroll.md)
- [设置 Android 设备管理](android-enroll.md) - 无需其他步骤

还可以确保用户设备上的日期和时间设置正确无误：

1. 重启设备。
2. 确保设置的日期和时间接近最终用户时区的 GMT 标准日期和时间（± 12 小时）。
3. 卸载并重新安装 Intune 公司门户（若有）。

托管的设备用户可收集注册和诊断日志以供你查看。 以下提供了有关收集日志的用户说明：

- [将 Android 注册错误发送给 IT 管理员](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [将 iOS 错误发送给 IT 管理员](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>常规注册问题
所有设备平台上都可能发生这些问题。

### <a name="device-cap-reached"></a>已达到设备上限
**问题：** 用户在注册期间收到错误（如“公司门户暂时不可用”  ）。

**解决方法：**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>检查已注册的和允许的设备数量

通过下述步骤，检查确保向用户分配的设备数未超过上限：

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “注册限制” > “设备限制”    。 记下“设备限制”列中的值  。

2. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“用户”   > “所有用户”  > 选择用户 >“设备”  。 记下设备的数量。

3. 如果用户注册的设备数已达到其设备限制，则在执行下述操作前无法再注册设备：
    - [删除现有设备](../remote-actions/devices-wipe.md)，或者
    - 通过[设置设备限制](enrollment-restrictions-set.md)来提高设备上限。

为避免达到设备上限，请一定要删除陈旧的设备记录。

> [!NOTE]
> 
> 可通过使用设备注册管理器帐户避免达到设备注册上限，如[使用 Microsoft Intune 中的设备注册管理器注册企业自有设备](device-enrollment-manager-enroll.md)中所述。
> 
> 如果对添加到设备注册管理器帐户的用户帐户强制实施条件访问策略，该特定用户登录将无法完成注册。

### <a name="company-portal-temporarily-unavailable"></a>公司门户暂时不可用
**问题：** 用户在设备上看到错误消息“公司门户暂不可用”  。

**解决方法：**

1. 从设备中删除 Intune 公司门户应用。

2. 在设备上，打开浏览器，浏览到 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)，然后尝试用户登录。

3. 如果用户登录失败，应尝试其他网络。

4. 如果仍然失败，请确保用户的凭据已与 Azure Active Directory 正确同步。

5. 如果用户成功登录，iOS 设备将提示你安装 Intune 公司门户应用并注册。 在 Android 设备上，需要手动安装 Intune 公司门户应用，之后才能重试注册。

### <a name="mdm-authority-not-defined"></a>未定义 MDM 机构
**问题：** 用户看到错误消息“未定义 MDM 机构”  。

**解决方法：**

1. 验证确保已 MDM 机构[设置得当](../fundamentals/mdm-authority-set.md)。
    
2. 验证用户的凭据已与 Azure Active Directory 正确同步。 可在 Microsoft 365 管理中心验证用户的 UPN 是否与 Active Directory 信息相匹配。
    如果 UPN 与 Active Directory 信息不匹配：

    1. 关闭本地服务器上的目录同步。

    2. 从“Intune 帐户门户”  用户列表中删除不匹配的用户。

    3. 等待大约一小时，让 Azure 服务删除不正确的数据。

    4. 再次打开目录同步，并检查该用户现在是否已正确同步。

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>如果公司名称包含特殊字符，则无法创建策略或注册设备
**问题：** 无法创建策略或注册设备。

**解决方法：** 在 [Microsoft 365 管理中心](https://admin.microsoft.com/)内，删除公司名称中的特殊字符，再保存公司信息。

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>如果有多个经过验证的域，则无法登录或注册设备
**问题：** 将第二个已验证域添加到 ADFS 时，可能会遇到此问题。 具有第二个域的用户主体名称 (UPN) 后缀的用户可能无法登录门户或注册设备。


<strong>解决方法：</strong>在下列情况下，Microsoft Office 365 客户必须为每个后缀单独部署 AD FS 2.0 联合身份验证服务实例：
- 通过 AD FS 2.0 使用单一登录 (SSO) 且
- 在其组织内为用户的 UPN 后缀提供多个顶级域名（例如，@contoso.com 或 @fabrikam.com）。


[AD FS 2.0 汇总](https://support.microsoft.com/kb/2607496)与 SupportMultipleDomain 切换结合使用可启用 AD FS 服务器，以在无需其他 AD FS 2.0 服务器的情况下支持此方案。 有关详细信息，请参阅[此博客](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/)。


## <a name="android-issues"></a>Android 的问题

### <a name="android-enrollment-errors"></a>Android 注册错误

下表列出了在 Intune 中注册 Android 设备时最终用户可能会遇到的错误。

|错误消息|问题|解决方法|
|---|---|---|
|**需 IT 管理员分配许可证才能进行访问**<br>IT 管理员未授予你使用此应用的权限。 请向 IT 管理员寻求帮助或稍后再试。|无法注册设备，因为该用户的帐户没有必要的许可证。|必须先为用户分配必要的许可证，用户才能注册其设备。 此消息表明用户持有的移动设备管理机构许可证类型不正确。 例如，如果以下两项均为“true”，则用户将看到此错误：<ol><li>已将 Intune 设置为移动设备管理机构</li><li>他们使用的是 System Center 2012 R2 Configuration Manager 许可。</li></ol>有关详细信息，请参阅[将 Intune 许可证分配给用户帐户](/intune/licenses-assign)。|
|**IT 管理员需要设置 MDM 机构**<br>似乎 IT 管理员并未设置 MDM 机构。 请向 IT 管理员寻求帮助或稍后再试。|尚未定义移动设备管理机构。|尚未在 Intune 中设置移动设备管理机构。 请参阅有关如何[设置移动设备管理机构](/intune/mdm-authority-set)的信息。|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>设备无法使用 Intune 服务签入
，并在 Intune 管理控制台中显示为“不正常”
**问题：** 一些运行 Android 版本 4.4.x 和 5.x 的 Samsung 设备可能会停止使用 Intune 服务签入。 如果设备不签入：

- 它们将无法从 Intune 服务接收策略、应用和远程命令。
- 它们在管理控制台中显示的管理状态为“不正常”  。
- 受条件访问策略保护的用户可能失去对公司资源的访问权限。

Samsung Smart Manager 软件（预装在某些 Samsung 设备上）会停用 Intune 公司门户及其组件。 当公司门户处于停用状态时，它无法在后台运行且无法联系 Intune 服务。

**解决方法 #1：**

告知你的用户手动启动公司门户应用。 应用重启后，设备将使用 Intune 服务签入。

> [!IMPORTANT]
> 手动打开公司门户应用只是一种临时解决方案，因为 Samsung Smart Manager 可能会再次停用公司门户应用。

**解决方法 #2：**

告知你的用户尝试升级到 Android 6.0。 停用问题不会发生在 Android 6.0 设备上。 若要检查是否有可用的更新，请转到“设置” > “关于设备” > “手动下载更新”> 按照提示进行操作    。

**解决方法 #3：**

如果解决方案 #2 无效，请让你的用户按照以下步骤操作，使 Smart Manager 排除公司门户网站应用：

1. 在设备上启动 Smart Manager 应用。

   ![选择设备上的“Smart Manager”图标](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. 选择“电池”  磁贴。

   ![选择“电池”磁贴](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. 在“应用省电”  或“应用优化”  下，选择“详细信息”  。

   ![在“应用省电”或“应用优化”下选择“详细信息”](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. 从应用列表中选择“公司门户”  。

   ![从应用列表中选择“公司门户”](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. 选择“关闭”  。

   ![从“应用优化”对话框中选择“关闭”](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. 在“应用省电”  或“应用优化”  下，确认公司门户已关闭。

   ![验证公司门户已关闭](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>配置文件安装失败
**问题：** 用户在 Android 设备上看到错误消息“配置文件安装失败”  。

**解决方法：**

1. 确认针对你在使用的 Intune 服务版本，该用户分配有适当的许可证。

2. 确认该设备尚未注册其他 MDM 提供程序。

3. 确认该设备尚未安装管理配置文件。

4. 确认默认浏览器为适用于 Android 的 Chrome，并且已启用 Cookie。

### <a name="android-certificate-issues"></a>Android 证书问题

**问题**：用户在设备上看到以下错误消息：无法登录，因为设备缺少必需证书。 

**解决方法 1**：

用户可能可以按照[设备缺少必需证书](/intune-user-help/your-device-is-missing-a-required-certificate-android)中的说明操作，检索缺少的证书。 如果错误一直存在，请尝试解决方法 2。

**解决方法 2**：

输入公司凭据并重定向到联合登录后，用户可能仍会看到缺少证书的错误。 在这种情况下，该错误可能意味着 Active Directory 联合身份验证服务 (AD FS) 服务器中缺少中间证书

此证书错误之所以出现是因为，Android 设备要求必须在 [SSL 服务器 Hello](https://technet.microsoft.com/library/cc783349.aspx) 内添加中间证书。 目前，在 SSL 客户端 Hello 的 SSL 服务器 Hello 响应中，默认 AD FS 服务器或 WAP（即 AD FS 代理服务器安装）仅发送 AD FS 服务 SSL 证书。

若要解决此问题，请按以下步骤将证书导入 AD FS 服务器或代理上的计算机个人证书：

1. 在 ADFS 和代理服务器上，右键单击“开始” > “运行” > “certlm.msc”，启动本地计算机证书管理控制台    。
2. 展开“个人”  ，再选择“证书”  。
3. 查找用于 AD FS 服务通信的证书（公共签名证书），然后双击以查看其属性。
4. 选择“证书路径”  选项卡，查看证书的父证书。
5. 在每个父证书上，选择“查看证书”  。
6. 选择“详细信息” > “复制到文件...”   。
7. 按照向导提示操作，将父证书的公钥导出或保存到所选的文件位置。
8. 右键单击“证书”   > “所有任务”   > “导入”  。
9. 按照向导提示操作，将一个或多个父证书导入“Local Computer\Personal\Certificates”  。
10. 重启 AD FS 服务器。
11. 在所有 AD FS 和代理服务器上重复上述步骤。

若要验证证书安装是否正确，可以使用 [https://www.digicert.com/help/](https://www.digicert.com/help/) 上的诊断工具。 在“服务器地址”  框中，输入 ADFS 服务器的 FQDN（IE：sts.contso.com），再单击“检查服务器”  。

**若要验证是否正确安装证书**：

以下步骤只描述了用于验证是否正确安装证书的许多方法和工具中的一种。

1. 转到[免费的 Digicert 工具](ttps://www.digicert.com/help/)。
2. 输入 AD FS 服务器的完全限定域名（例如 sts.contoso.com），再选择“检查服务器”  。

如果已正确安装服务器证书，则会在结果中看见所有复选标记。 如果存在上述问题，则会在报告的“证书名称匹配”和“已正确安装 SSL 证书”部分看见红色的 X。


## <a name="ios-issues"></a>iOS 的问题

### <a name="ios-enrollment-errors"></a>iOS 注册错误
下表列出了在 Intune 中注册 iOS 设备时最终用户可能遇到的错误。

|错误消息|问题|解决方法|
|-------------|-----|----------|
|NoEnrollmentPolicy|找不到注册策略|检查是否已设置所有注册必备组件（如 Apple Push Notification 服务 (APNs) 证书），并确保已启用“iOS 平台”。 有关说明，请参阅[设置 iOS 和 Mac 设备管理](../ios-enroll.md)。|
|DeviceCapReached|已注册太多的移动设备。|用户必须从公司门户中删除当前已注册的某个移动设备，然后才可注册其他设备。 请参阅所使用设备类型的相关说明：[Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android)、[iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios)、[Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows)。|
|APNSCertificateNotValid|移动设备用于与公司网络通信的证书存在问题。<br /><br />|Apple Push Notification 服务 (APNs) 提供与注册的 iOS 设备联系的通道。 如果出现以下情况，注册将失败，并将显示此消息：<ul><li>获取 APN 证书的步骤尚未完成，或</li><li>APN 证书已过期。</li></ul>查看[同步 Active Directory 并将用户添加到 Intune](../fundamentals/users-add.md) 和[组织用户和设备](../fundamentals/groups-add.md)中有关如何设置用户的信息。|
|AccountNotOnboarded|移动设备用于与公司网络通信的证书存在问题。<br /><br />|Apple Push Notification 服务 (APNs) 提供与注册的 iOS 设备联系的通道。 如果出现以下情况，注册将失败，并将显示此消息：<ul><li>获取 APN 证书的步骤尚未完成，或</li><li>APN 证书已过期。</li></ul>有关详细信息，请查看[使用 Microsoft Intune 设置 iOS 和 Mac 管理](../ios-enroll.md)。|
|DeviceTypeNotSupported|用户可能已尝试使用非 iOS 设备进行注册。 不支持你正在尝试注册的移动设备类型。<br /><br />确认设备正在运行 iOS 版本 8.0 或更高版本。<br /><br />|请确保用户的设备正在运行 iOS 版本 8.0 或更高版本。|
|UserLicenseTypeInvalid|无法注册设备，因为用户帐户还不是所需用户组的成员。<br /><br />|用户必须是相应用户组的成员才能注册其设备。 此消息表明用户持有的移动设备管理机构许可证类型不正确。 例如，如果以下两项均为“true”，则用户将看到此错误：<ol><li>已将 Intune 设置为移动设备管理机构</li><li>他们使用的是 System Center 2012 R2 Configuration Manager 许可。</li></ol>有关详细信息，请查看下列文章：<br /><br />查看[使用 Microsoft Intune 设置 iOS 和 Mac 管理](../ios-enroll.md)，以及[同步 Active Directory 并将用户添加到 Intune](../fundamentals/users-add.md)、[组织用户和设备](../fundamentals/groups-add.md)中的有关如何设置用户的信息。|
|MdmAuthorityNotDefined|尚未定义移动设备管理机构。<br /><br />|尚未在 Intune 中设置移动设备管理机构。<br /><br />请查看[开始使用 Microsoft Intune 的 30 天试用版](../fundamentals/free-trial-sign-up.md)中“第 6 步：注册移动设备并安装应用”部分内的第 1 项。|

### <a name="devices-are-inactive-or-the-admin-console-cant-communicate-with-them"></a>设备处于非活动状态，或管理控制台不能与其通信
**问题：** iOS 设备未使用 Intune 服务签入。 设备必须定期使用该服务签入，以保持对受保护的公司资源的访问权限。 如果设备不签入：

- 它们将无法从 Intune 服务接收策略、应用和远程命令。
- 它们在管理控制台中显示的管理状态为“不正常”  。
- 受条件访问策略保护的用户可能失去对公司资源的访问权限。

**解决方法：** 与最终用户共享以下解决办法，帮助他们重新获得对公司资源的访问权限。

如果用户启动了 iOS 公司门户应用，则可确定他们的设备是否与 Intune 失去联系。 如果没有检测到任何联系，则会自动尝试与 Intune 同步以重新连接，用户将看到“正在尝试同步...”  消息）。

  ![尝试同步通知](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

如果同步成功，将在 iOS 公司门户应用中看到“同步成功”  内联通知，指示你的设备处于正常状态。

  ![同步成功通知](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

如果同步失败，用户将在 iOS 公司门户应用中看到“无法同步”  内联通知。

  ![无法同步通知](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

若要解决此问题，用户必须选择“设置”  按钮，该按钮位于“无法同步”  通知的右侧。 通过“设置”按钮，用户可转到“公司访问设置”流屏幕，在此处，用户可按提示注册设备。

  ![“公司访问设置”屏幕](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

注册后，设备将恢复到正常状态，并重新获得对公司资源的访问权限。

### <a name="verify-ws-trust-13-is-enabled"></a>确认已启用 WS-Trust 1.3
**问题**无法注册设备注册计划 (DEP) iOS 设备

注册具有用户关联的 DEP 设备要求启用 WS-Trust 1.3 用户名/混合终结点以请求用户令牌。 默认情况下，Active Directory 启用此终结点。 若要获取已启用的终结点列表，请使用 Get-AdfsEndpoint PowerShell cmdlet 查找 trust/13/UsernameMixed 终结点。 例如：

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

有关详细信息，请参阅 [Get-AdfsEndpoint 文档](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

有关详细信息，请参阅[保护 Active Directory 联合身份验证服务安全的最佳做法](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs)。 有关确定身份联合提供程序中是否启用了 WS-Trust 1.3 用户名/混合的帮助，请执行以下操作：
- 联系 Microsoft 支持部门（如果使用 ADFS）
- 联系第三方标识供应商。


### <a name="profile-installation-failed"></a>配置文件安装失败
**问题：** 用户在 iOS 设备上看到错误消息“配置文件安装失败”  。

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>失败配置文件安装的故障排除步骤

1. 确认针对你在使用的 Intune 服务版本，该用户分配有适当的许可证。

2. 确认该设备尚未注册其他 MDM 提供程序。

3. 确认该设备尚未安装管理配置文件。

4. 导航到 [https://portal.manage.microsoft.com https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)，当出现提示时，并尝试安装配置文件。

5. 确认默认浏览器为适用于 iOS 的 Safari，并且已启用 Cookie。

### <a name="users-ios-device-is-stuck-on-an-enrollment-screen-for-more-than-10-minutes"></a>用户的 iOS 设备在注册屏幕上受阻时间超过 10 分钟

**问题**：注册设备可能会卡滞在以下两个屏幕中：
- 等待来自“Microsoft”的最终配置
- 引导式访问应用不可用。 请与管理员联系。

如果发生以下情况，则可能出现此问题：
- Apple 服务暂时中断，或者
- iOS 注册设置为使用表中所示的 VPP 令牌，但 VPP 令牌存在问题。

| 注册设置 | 值 |
| ---- | ---- |
| 平台 | iOS |
| 用户关联 | 注册用户关联 |
|使用公司门户而不是 Apple 设置助理进行身份验证 | 是 |
| 使用 VPP 安装公司门户 | 使用令牌：令牌地址 |
| 在身份验证前以单应用模式运行公司门户 | 是 |

**解决方法**：若要解决此问题，必须执行以下操作：
1. 确定 VPP 令牌是否存在问题并进行修复。
2. 确定已阻止的设备。
3. 擦除受影响的设备。
4. 告知用户重启注册过程。

#### <a name="determine-if-theres-something-wrong-with-the-vpp-token"></a>确定 VPP 令牌是否存在问题
1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “iOS” > “iOS 注册” > “注册计划令牌”>“令牌名称”>“配置文件”>“配置文件名称”>“管理” > “属性”        。
2. 查看属性，了解是否出现与以下情况类似的错误：
    - 此令牌已过期。
    - 此令牌超出公司门户许可范围。
    - 另一个服务正在使用此令牌。
    - 另一个租户正在使用此令牌。
    - 此令牌已删除。
3. 修复此令牌的问题。

#### <a name="identify-which-devices-are-blocked-by-the-vpp-token"></a>确定 VPP 令牌阻止了哪些设备
1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “iOS”>“iOS 注册” > “注册计划令牌”>“令牌名称”>“设备”      。
2. 按照“已阻止”筛选“配置文件状态”列   。
3. 记下“已阻止”的所有设备的序列号  。

#### <a name="remotely-wipe-the-blocked-devices"></a>远程擦除已阻止设备
修复 VPP 令牌的问题后，必须擦除已阻止设备。
1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “所有设备” > “列” > “序列号” > “应用”      。 
2. 对于每个已阻止设备，请在“所有设备”列表中选择该设备，然后依次选择“擦除” > “确认”    。

#### <a name="tell-the-users-to-restart-the-enrollment-process"></a>告知用户重启注册过程
擦除已阻止设备后，可告知用户重启注册过程。

## <a name="macos-issues"></a>macOS 问题

### <a name="macos-enrollment-errors"></a>macOS 注册错误
**错误消息 1：** *你似乎使用的是虚拟机。请确保已完全配置了虚拟机，包括序列号和硬件型号。如果这不是虚拟机，请联系支持人员。*  

**错误消息 2：** *无法托管你的设备。如果使用虚拟机、具有受限制的序列号或者此设备已分配给其他人，则可能会导致此问题。了解如何解决这些问题，或联系公司支持人员。*

**问题：** 导致此消息出现的原因如下：  
- macOS 虚拟机 (VM) 未正确配置  
- 已启用设备限制，要求设备为公司拥有或在 Intune 中具有已注册的设备序列号  
- 设备已注册并仍分配给 Intune 中的其他人  

**解决方法：** 首先，请与用户联系，以确定其设备受到哪个问题的影响。 然后完成以下解决方案中最相关的解决方案：

- 如果用户注册用于测试的 VM，请确保已将其完全配置，以便 Intune 可以识别其序列号和硬件型号。 了解如何在 Intune 中[设置 VM](macos-enroll.md#enroll-virtual-macos-machines-for-testing) 的详细信息。
- 如果组织启用了阻止个人 macOS 设备的注册限制，则必须手动[添加个人设备的序列号](corporate-identifiers-add.md#manually-enter-corporate-identifiers)到 Intune。  
- 如果设备仍分配给 Intune 中的其他用户，则其前所有者未使用公司门户应用来删除或重置它。 从 Intune 清除陈旧的设备记录：  

    1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，使用管理凭据登录。
    2. 选择“设备” > “所有设备”   。  
    3. 查找存在注册问题的设备。 按设备名称或 MAC/HW 地址搜索以缩小结果范围。
    4. 选择“设备”>“删除”  。 删除与设备关联的所有其他条目。  

## <a name="pc-issues"></a>电脑问题

|错误消息|问题|解决方法|
|---|---|---|
|**需 IT 管理员分配许可证才能进行访问**<br>IT 管理员未授予你使用此应用的权限。 请向 IT 管理员寻求帮助或稍后再试。|无法注册设备，因为该用户的帐户没有必要的许可证。|必须先为用户分配必要的许可证，用户才能注册其设备。 此消息表明用户持有的移动设备管理机构许可证类型不正确。 例如，如果以下两项均为“true”，则用户将看到此错误： <ol><li>已将 Intune 设置为移动设备管理机构</li><li>他们使用的是 System Center 2012 R2 Configuration Manager 许可。</li></ol>请参阅有关如何[将 Intune 许可证分配给用户帐户](../fundamentals/licenses-assign.md)的信息。|

### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>该计算机已注册 - 错误 hr 0x8007064c

**问题：** 注册失败，并看到错误消息“计算机已注册”  。 注册日志显示错误 **hr 0x8007064c**。

此次失败出现的原因是计算机：

- 先前已注册，或
- 具有已注册计算机的克隆映像。
先前帐户的帐户证书仍在此计算机上。

**解决方法：**

1. 在“开始”  菜单中，键入“运行”   -> “MMC”  。
1. 选择“文件”   > “添加/删除管理单元”  。
1. 双击“证书”  ，选择“计算机帐户”   > “下一步”  ，然后选择“本地计算机”  。
1. 双击“证书(本地计算机)”  ，然后选择“个人/证书”  。
1. 查找 Sc_Online_Issuing 发布的 Intune 证书，并将其删除（若存在）。
1. 删除注册表项 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey  （若有）以及所有子项。
1. 尝试重新注册。
1. 如果 PC 仍无法注册，请查找并删除以下项（若有）：**KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**。
1. 尝试重新注册。

    > [!IMPORTANT]
    > 此部分、方法或任务包含教你如何修改注册表的步骤。 但是，如果注册表修改不正确，可能会发生严重问题。 因此，请确保认真遵循这些步骤。 为提高保护程度，请在修改之前备份注册表。 那么，如果发生问题，你也可以恢复注册表。
    > 有关如何备份和还原注册表的详细信息，请参阅 [如何在 Windows 中备份和还原注册表](https://support.microsoft.com/kb/322756)

## <a name="general-enrollment-error-codes"></a>常规注册错误代码

|错误代码|可能的问题|建议的解决方法|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |未将客户端计算机上的时钟设置为正确的时间。|确保将客户端计算机上的时钟和时区设置为正确的时间和时区。|
|0x80240438、0x80CF0438、0x80CF402C|无法连接到 Intune 服务。 检查客户端代理设置。|验证 Intune 是否支持客户端计算机上的代理配置。 验证客户端计算机是否可访问 Internet。|
|0x80240438，0x80CF0438|未配置 Internet Explorer 和本地系统中的代理设置。|无法连接到 Intune 服务。 检查客户端代理设置。验证 Intune 是否支持客户端计算机上的代理配置。 验证客户端计算机是否可访问 Internet。|
|0x80043001、0x80CF3001、0x80043004、0x80CF3004|注册程序包过期。|从“管理”工作区中下载并安装最新的客户端软件包。|
|0x80043002、0x80CF3002|帐户处于维护模式。|当帐户处于维护模式时，便无法注册新客户端计算机。 若要查看帐户设置，请登录到你的帐户。|
|0x80043003、0x80CF3003|帐户被删除。|验证你的帐户和 Intune 订阅是否仍处于活动状态。 若要查看帐户设置，请登录到你的帐户。|
|0x80043005、0x80CF3005|客户端计算机已停用。|等几个小时并从计算机中删除任何较旧版本的客户端软件，然后尝试重新安装客户端软件。|
|0x80043006、0x80CF3006|已达到允许此帐户拥有的最大座位数。|贵组织必须购买额外的席位，你才能在服务中注册更多客户端计算机。|
|0x80043007、0x80CF3007|在安装程序所在的文件夹中找不到证书文件。|在开始安装之前提取所有文件。 请不要重命名或移动任何提取的文件：所有文件必须位于同一文件夹中，否则安装将失败。|
|0x8024D015、0x00240005、0x80070BC2、0x80070BC9、0x80CFD015|无法安装软件，因为客户端计算机的重启处于挂起状态。|重启计算机，然后尝试重新安装客户端软件。|
|0x80070032|未在客户端计算机上找到安装客户端软件所需的一个或多个必备项。|确保所有必需的更新都已安装在客户端计算机上，然后尝试重新安装客户端软件。|
|0x80043008、0x80CF3008|未能启动 Microsoft Online Management 更新服务。|请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](../fundamentals/get-support.md)中所述。|
|0x80043009、0x80CF3009|已在服务中注册客户端计算机。|你必须先停用客户端计算机，然后才能在服务中重新注册该客户端计算机。|
|0x8004300B、0x80CF300B|无法运行客户端软件安装包，因为不支持客户端上运行的 Windows 的版本。|Intune 不支持客户端计算机上运行的 Windows 的版本。|
|0xAB2|Windows Installer 无法针对自定义操作访问 VBScript 运行时。|此错误是由基于动态链接库 (DLL) 的自定义操作引起的。 排查 DLL 问题时，可能需要使用 [Microsoft 支持 KB198038:针对打包和部署问题的有用工具中描述的工具](https://support.microsoft.com/kb/198038)。|
|0x80cf0440|到服务终结点的连接已终止。|试用或付费帐户处于挂起状态。 创建一个新的试用或付费帐户，并重新注册。|

## <a name="next-steps"></a>后续步骤

如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](../fundamentals/get-support.md)中所述。
