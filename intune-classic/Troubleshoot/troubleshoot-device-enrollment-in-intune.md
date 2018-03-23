---
title: 设备注册疑难解答
description: 有关设备注册问题故障排除的建议。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/15/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0293614e2654c16b6fd5fd43d40331453b332e3c
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2018
---
# <a name="troubleshoot-device-enrollment-in-intune"></a>排查 Intune 中的设备注册问题

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题提供有关设备注册问题故障排除的建议。 如果此信息未解决你的问题，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)，了解更多获得帮助的方法。


## <a name="initial-troubleshooting-steps"></a>初始故障排除步骤

开始故障排除之前，请检查确保你已正确配置 Intune 以启用注册。 可以在此处了解这些配置要求：

-   [为在 Microsoft Intune 中注册设备做好准备](/intune-classic/deploy-use/prerequisites-for-enrollment)
-   [设置 iOS 和 Mac 设备管理](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
-   [设置 Windows 设备管理](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
-   [设置 Android 设备管理](/intune-classic/deploy-use/set-up-android-management-with-microsoft-intune) - 无需其他步骤
-   [设置 Android for Work 设备管理](/intune-classic/deploy-use/set-up-android-for-work)

还可以确保用户设备上的日期和时间设置正确无误：

1. 重启设备。
2. 确保设置的日期和时间接近相对于最终用户时区的 GMT 标准日期和时间（± 12 小时）。
3. 卸载并重新安装 Intune 公司门户（若有）。

托管的设备用户可收集注册和诊断日志以供你查看。 以下提供了有关收集日志的用户说明：

- [将 Android 注册错误发送给 IT 管理员](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [将 iOS 错误发送给 IT 管理员](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>常规注册问题
所有设备平台上都可能发生这些问题。

### <a name="device-cap-reached"></a>已达到设备上限
**问题：**注册期间，用户在设备上收到一个错误，例如 iOS 设备上的“公司门户暂时不可用”错误，并且 Configuration Manager 上的 DMPdownloader.log 包含错误“DeviceCapReached”。

**解决方法：**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>检查已注册的和允许的设备数量

1.  在 Intune 管理门户中，确保用户分配的设备不超过允许的最大数量 15 台。

2.  在 Intune 管理控制台中的“管理” > “移动设备管理” > “注册规则”下，确保设备注册限制设置为 15。

<!--- Mobile device users can delete devices at the following URL: [https://byodtestservice.azurewebsites.net/](https://byodtestservice.azurewebsites.net/). --->

管理员可以在 Azure Active Directory 门户中删除设备。

#### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>在 Azure Active Directory 门户中删除设备

1.  浏览到 [http://aka.ms/accessaad](http://aka.ms/accessaad)，或从 [https://portal.office.com](https://portal.office.com) 选择“管理员”&gt;“Azure AD”。

2.  单击页面左侧的链接，使用组织 ID 登录。

3.  如果还没有 Azure 订阅，请选择“注册免费 Azure Active Directory”订阅链接创建一个。 如果已有付费帐户，则无需使用信用卡或进行付款。

4.  选择“Active Directory”  ，然后选择你的组织。

5.  选择“用户”  选项卡。

6.  选择要删除其设备的用户。

7.  选择**设备**。

8.  根据需要删除设备，例如那些不再使用的设备或者定义不准确的设备。

> [!NOTE]

> 可通过使用设备注册管理器帐户避免达到设备注册上限，如[使用 Microsoft Intune 中的设备注册管理器注册企业自有设备](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)中所述。
>
> 如果对添加到设备注册管理器帐户的用户帐户强制实施条件访问策略，该特定用户登录将无法完成注册。

### <a name="company-portal-temporarily-unavailable"></a>公司门户暂时不可用
**问题：**用户的设备上收到“公司门户暂时不可用”错误。

**解决方法：**

1.  从设备中删除 Intune 公司门户应用。

2.  在设备上，打开浏览器，浏览到 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)，然后尝试用户登录。

3.  如果用户无法登录，请让她尝试另一个网络。

4.  如果仍然失败，请确保用户的凭据已与 Azure Active Directory 正确同步。

5.  如果用户成功登录，iOS 设备将提示你安装 Intune 公司门户应用并注册。 在 Android 设备上，需要手动安装 Intune 公司门户应用，之后才能重试注册。

### <a name="mdm-authority-not-defined"></a>未定义 MDM 机构
**问题：**用户收到“未定义 MDM 机构”错误。

**解决方法：**

1.  验证是否已针对使用的 Intune 服务类型（即 Intune、Office 365 或 System Center Configuration Manager with Intune）正确设置 MDM 机构。 对于 Intune，请在“管理员”&gt;“移动设备管理”中设置 MDM 机构。 对于 Configuration Manager with Intune，请在配置 Intune 连接器时对其进行设置，在 Office 365 中则对“移动设备”进行设置。

    > [!NOTE]    
    > 在 Configuration Manager 版本 1610 或更高版本和 Microsoft Intune 版本 1705 中，你将可以更改 MDM 颁发机构，而无需联系 Microsoft 支持部门，并且无需取消注册并重新注册现有的受管理设备。 有关详细信息，请参阅[如果选择了错误的 MDM 颁发机构设置怎么办](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)。

2.  通过检查用户的 UPN 是否与 Office 365 门户中的 Active Directory 信息匹配，验证该用户的凭据是否已与 Azure Active Directory 正确同步。
    如果 UPN 与 Active Directory 信息不匹配：

    1.  关闭本地服务器上的目录同步。

    2.  从“Intune 帐户门户”  用户列表中删除不匹配的用户。

    3.  等待大约一小时，让 Azure 服务删除不正确的数据。

    4.  再次打开目录同步，并检查该用户现在是否已正确同步。

3.  如果使用的是 System Center Configuration Manager with Intune，请确保该用户具有有效的云用户 ID：

    1.  打开 SQL Management Studio。

    2.  连接到相应的数据库。

    3.  打开数据库文件夹，找到并打开 **CM_DBName** 文件夹，其中 DBName 是客户数据库的名称。

    4.  在顶部选择**新建查询**并执行以下查询：

        -   查看所有用户：`select * from [CM_ DBName].[dbo].[User_DISC]`

        -   若要查看特定用户，请使用下面的查询，其中 %testuser1% 表示要查找的用户的 username@domain.com：`select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        编写查询后，选择**!执行**。
        返回结果后，即可查找云用户 ID。  如果找不到任何 ID，则表示未授权该用户使用 Intune。

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>如果公司名称包含特殊字符，则无法创建策略或注册设备
**问题：**无法创建策略或注册设备。

**解决方法：**在 [Office 365 管理中心](https://portal.office.com/)，删除公司名称中的特殊字符并保存公司信息。

### <a name="unable-to-log-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>如果有多个已验证的域，则无法登录或注册设备
**问题：**向 ADFS 添加第二个已验证的域时，具有第二个域的用户主体名称 (UPN) 后缀的用户可能无法登录门户或注册设备。


**解决方法：**对于通过 AD FS 2.0 使用单一登录 (SSO) 且其组织中拥有用户 UPN 后缀的多个顶级域（如 @contoso.com 或 @fabrikam.com）的 Microsoft Office 365 客户，他们需要为每个后缀部署 AD FS 2.0 联合身份验证服务的一个单独实例。 现在有了 [AD FS 2.0 汇总](http://support.microsoft.com/kb/2607496)，其与**SupportMultipleDomain** 切换结合使用可启用 AD FS 服务器，以在无需其他 AD FS 2.0 服务器的情况下支持此方案。 有关详细信息，请参阅[此博客](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/)。


## <a name="android-issues"></a>Android 的问题

### <a name="android-enrollment-errors"></a>Android 注册错误

下表列出了在 Intune 中注册 Android 设备时最终用户可能会遇到的错误。

|错误消息|问题|解决方法|
|---|---|---|
|**IT 管理员需要分配许可证才能进行访问**<br>IT 管理员未授予你使用此应用的权限。 请向 IT 管理员寻求帮助或稍后重试。|无法注册设备，因为该用户的帐户没有必要的许可证。|必须先为用户分配必要的许可证，用户才能注册其设备。 此消息表明用户持有的指定移动设备管理机构许可证类型不正确。 例如，如果已将 Intune 指定为移动设备管理机构，并且用户正在使用 System Center 2012 R2 Configuration Manager 许可证，则将收到此错误消息。<br><br>请参阅有关如何[将 Intune 许可证分配给用户帐户](/intune/licenses-assign)的信息。
|**IT 管理员需要设置 MDM 机构**<br>看起来 IT 管理员并未设置 MDM 机构。 请向 IT 管理员寻求帮助或稍后重试。|尚未定义移动设备管理机构。|尚未在 Intune 中指定移动设备管理机构。 请参阅有关如何[设置移动设备管理机构](/intune/mdm-authority-set)的信息。|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>设备无法签入 Intune 服务，并在 Intune 管理控制台中显示为“不正常”
**问题：**运行 Android 版本 4.4.x 和 5.x 的某些 Samsung 设备可能会停止签入 Intune 服务。 如果设备不签入：

- 它们将无法从 Intune 服务接收策略、应用和远程命令。
- 它们在管理控制台中显示的管理状态为“不正常”。
- 受条件访问策略保护的用户可能失去对公司资源的访问权限。

Samsung 已经确认 Samsung Smart Manager 软件（预装在某些 Samsung 设备上）会停用 Intune 公司门户及其组件。 当公司门户处于停用状态时，它无法在后台运行，因此无法联系 Intune 服务。

**解决方法 #1：**

告知你的用户手动启动公司门户应用。 应用重启后，设备将签入 Intune 服务。

> [!IMPORTANT]
> 手动打开公司门户应用只是一种临时解决方案，因为 Samsung Smart Manager 可能会再次停用公司门户应用。

**解决方法 #2：**

告知你的用户尝试升级到 Android 6.0。 停用问题不会发生在 Android 6.0 设备上。 若要检查是否有可用的更新，用户可以转到“设置” > “关于设备” > “手动下载更新”，然后按照设备上的提示进行操作。

**解决方法 #3：**

如果解决方案 #2 无效，请让你的用户按照以下步骤操作，使 Smart Manager 排除公司门户网站应用：

1. 在设备上启动 Smart Manager 应用。

  ![选择设备上的“Smart Manager”图标](./media/smart-manager-app-icon.png)

2. 选择“电池”磁贴。

  ![选择“电池”磁贴](./media/smart-manager-battery-tile.png)

3. 在“应用省电”或“应用优化”下，选择“详细信息”。

  ![在“应用省电”或“应用优化”下选择“详细信息”](./media/smart-manager-app-power-saving-detail.png)

4. 从应用列表中选择“公司门户”。

  ![从应用列表中选择“公司门户”](./media/smart-manager-company-portal.png)

5. 选择“关闭”。

  ![从“应用优化”对话框中选择“关闭”](./media/smart-manager-app-optimization-turned-off.png)

6. 在“应用省电”或“应用优化”下，确认公司门户已关闭。

  ![验证公司门户已关闭](./media/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>配置文件安装失败
**问题：**用户在 Android 设备上收到**配置文件安装失败**错误。

**解决方法：**

1.  确认针对你在使用的 Intune 服务版本，该用户分配有适当的许可证。

2.  确认尚未向另一个 MDM 提供程序注册该设备，或者该设备尚未安装管理配置文件。

3.  确认默认浏览器为适用于 Android 的 Chrome，并且已启用 Cookie。

### <a name="android-certificate-issues"></a>Android 证书问题

**问题**：用户在其设备上收到以下消息：*无法登录，因为设备缺少必需的证书。*

**解决方法 1**：

用户可能可以按照[设备缺少必需证书](/intune-user-help/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)中的说明操作，检索缺少的证书。 如果错误一直存在，请尝试解决方法 2。

**解决方法 2**：

如果用户在输入公司凭据并在联合登录中重定向后仍看到缺少证书的错误，那么 Active Directory 联合身份验证服务 (AD FS) 服务器可能缺少中间证书。

此证书错误之所以出现是因为，Android 设备要求必须在 [SSL 服务器 Hello](https://technet.microsoft.com/library/cc783349.aspx) 内添加中间证书。 目前，在 SSL 客户端 Hello 的 SSL 服务器 Hello 响应中，默认 AD FS 服务器或 WAP（即 AD FS 代理服务器安装）仅发送 AD FS 服务 SSL 证书。

若要解决此问题，请按以下步骤将证书导入 AD FS 服务器或代理上的计算机个人证书：

1.  在 ADFS 和代理服务器上，右键单击“开始” > “运行” > “certlm.msc”。 这会启动本地计算机证书管理控制台。
2.  展开“个人”，再选择“证书”。
3.  查找用于 AD FS 服务通信的证书（公共签名证书），然后双击以查看其属性。
4.  选择“证书路径”选项卡，查看证书的父证书。
5.  在每个父证书上，选择“查看证书”。
6.  依次选择“详细信息”选项卡和“复制到文件...”。
7.  按照向导提示操作，将父证书的公钥导出或保存到相应的文件位置。
8.  右键单击“证书” > “所有任务” > “导入”。
9.  按照向导提示操作，将一个或多个父证书导入“Local Computer\Personal\Certificates”。
10. 重启 AD FS 服务器。
11. 在所有 AD FS 和代理服务器上重复上述步骤。

若要验证证书安装是否正确，可以使用 [https://www.digicert.com/help/](https://www.digicert.com/help/) 上的诊断工具。 在“服务器地址”框中，输入 ADFS 服务器的 FQDN（IE：sts.contso.com），再单击“检查服务器”。

**若要验证是否正确安装证书**：

以下步骤只描述了用于验证是否正确安装证书的许多方法和工具中的一种。

1. 转到[免费的 Digicert 工具](ttps://www.digicert.com/help/)。
2. 输入 AD FS 服务器的完全限定域名（例如，sts.contoso.com），并选择“检查服务器”。

如果已正确安装服务器证书，则会在结果中看见所有复选标记。 如果存在上述问题，则会在报告的“证书名称匹配”和“已正确安装 SSL 证书”部分看见红色的 X。


## <a name="ios-issues"></a>iOS 的问题

### <a name="ios-enrollment-errors"></a>iOS 注册错误
下表列出了在 Intune 中注册 iOS 设备时最终用户可能遇到的错误。

|错误消息|问题|解决方法|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|找不到注册策略|检查是否已设置所有注册必备组件（如 Apple Push Notification 服务 (APNs) 证书），并确保已启用“iOS 平台”。 有关说明，请参阅[设置 iOS 和 Mac 设备管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceCapReached|已注册太多的移动设备。|注册其他移动设备前，用户必须从公司门户中删除当前已注册的移动设备之一。 请参阅你使用的设备类型的说明：[Android ](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android)、[iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios) 和 [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows)。|
|APNSCertificateNotValid|移动设备用于与公司网络通信的证书存在问题。<br /><br />|Apple Push Notification 服务 (APNs) 提供与已注册 iOS 设备通信的通道。 如果未执行获取 APNs 证书的步骤，或者 APNs 证书已过期，则注册尝试将失败并将显示此消息。<br /><br />查看[同步 Active Directory 并将用户添加到 Intune](/intune/users-permissions-add) 和[组织用户和设备](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)中有关如何设置用户的信息。|
|AccountNotOnboarded|移动设备用于与公司网络通信的证书存在问题。<br /><br />|Apple Push Notification 服务 (APNs) 提供与已注册 iOS 设备通信的通道。 如果未执行获取 APNs 证书的步骤，或者 APNs 证书已过期，则注册尝试将失败并将显示此消息。<br /><br />有关详细信息，请查看[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceTypeNotSupported|用于可能已尝试使用非 iOS 设备进行注册。 不支持你正在尝试注册的移动设备类型。<br /><br />确认设备正在运行 iOS 版本 8.0 或更高版本。<br /><br />|请确保用户的设备正在运行 iOS 版本 8.0 或更高版本。|
|UserLicenseTypeInvalid|无法注册设备，因为用户帐户还不是所需用户组的成员。<br /><br />|用户必须是相应用户组的成员才能注册其设备。 此消息表明用户持有的指定移动设备管理机构许可证类型不正确。 例如，如果已将 Intune 指定为移动设备管理机构，并且用户正在使用 System Center 2012 R2 Configuration Manager 许可证，则将收到此错误消息。<br /><br />有关详细信息，请查看以下内容：<br /><br />查看[同步 Active Directory 并将用户添加到 Intune](/intune/users-permissions-add) 和[组织用户和设备](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)中的[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)以及有关如何设置用户的信息。|
|MdmAuthorityNotDefined|尚未定义移动设备管理机构。<br /><br />|尚未在 Intune 中指定移动设备管理机构。<br /><br />查看[开始使用 Microsoft Intune 的 30 天试用版](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中的“步骤 6：注册移动设备并安装应用”部分的第 1 项。|

### <a name="devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>设备处于非活动状态，或管理控制台不能与其通信
**问题：**iOS 设备未使用 Intune 服务签入。 设备必须定期使用该服务签入，以保持对受保护的公司资源的访问权限。 如果设备不签入：

- 它们将无法从 Intune 服务接收策略、应用和远程命令。
- 它们在管理控制台中显示的管理状态为“不正常”。
- 受条件访问策略保护的用户可能失去对公司资源的访问权限。

**解决方法：**与最终用户共享以下解决方法，帮助他们重新获得公司资源的访问权限。

如果用户启动了 iOS 公司门户应用，则可确定他们的设备是否与 Intune 失去联系。 如果没有检测到任何联系，则会自动尝试与 Intune 同步以重新连接，用户将看到“正在尝试同步...” 内联通知。

  ![尝试同步通知](./media/ios_cp_app_trying_to_sync_notification.png)

如果同步成功，将在 iOS 公司门户应用中看到“同步成功”内联通知，指示你的设备处于正常状态。

  ![同步成功通知](./media/ios_cp_app_sync_successful_notification.png)

如果同步失败，用户将在 iOS 公司门户应用中看到“无法同步”内联通知。

  ![无法同步通知](./media/ios_cp_app_unable_to_sync_notification.png)

若要解决此问题，用户必须选择“设置”按钮，该按钮位于“无法同步”通知的右侧。 通过“设置”按钮，用户可转到“公司访问设置”流屏幕，在此处，用户可按提示注册设备。

  ![“公司访问设置”屏幕](./media/ios_cp_app_company_access_setup.png)

注册后，设备将恢复到正常状态，并重新获得对公司资源的访问权限。

### <a name="verify-ws-trust-13-is-enabled"></a>确认已启用 WS-Trust 1.3
**问题**无法注册设备注册计划 (DEP) iOS 设备

注册具有用户相关性的设备注册计划设备要求启用 WS-Trust 1.3 Username/Mixed 终结点以请求用户令牌。 默认情况下，Active Directory 启用此终结点。 通过使用 Get-AdfsEndpoint PowerShell cmdlet 和查找 trust/13/UsernameMixed 终结点可获取已启用的终结点列表。 例如：

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

有关详细信息，请参阅 [Get-AdfsEndpoint 文档](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

有关详细信息，请参阅[保护 Active Directory 联合身份验证服务安全的最佳做法](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs)。 如果你需要更多的帮助来确定联合身份验证提供程序中是否启用了 WS-Trust 1.3 Username/Mixed，并且你使用的是 ADFS，请联系 Microsoft 支持部门或第三方身份标识供应商。


### <a name="profile-installation-failed"></a>配置文件安装失败
**问题：**用户的 iOS 设备上收到**配置文件安装失败**错误。

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>失败配置文件安装的故障排除步骤

1.  确认针对你在使用的 Intune 服务版本，该用户分配有适当的许可证。

2.  确认尚未向另一个 MDM 提供程序注册该设备，或者该设备尚未安装管理配置文件。

3.  出现提示时，导航到 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)，并尝试安装配置文件。

4.  确认默认浏览器为适用于 iOS 的 Safari，并且已启用 Cookie。

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>通过 Intune 使用 System Center Configuration Manager 时，注册的 iOS 设备不会在控制台中显示
**问题：**用户注册了 iOS 设备，但它未出现在 Configuration Manager 管理控制台中。 该设备未指示已注册。 可能的原因：

- Configuration Manager 站点中的 Microsoft Intune 连接器当前未与 Intune 服务进行通信。
- 数据发现管理器 (ddm) 组件或状态管理器 (statmgr) 组件当前未处理来自 Intune 服务的消息。
- 你可能已从某个帐户下载了 MDM 证书，而在其他帐户上使用了它。


**解决方法：**查看以下日志文件是否存在错误：

- dmpdownloader.log
- ddm.log
- statmgr.log

即将增添有关在这些日志文件中查找哪些内容的示例。


## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>使用 System Center Configuration Manager with Intune 时的问题
### <a name="mobile-devices-disappear"></a>移动设备消失
**问题：** 在向 Configuration Manager 成功注册移动设备后，它从移动设备集合中消失，但该设备仍然具有管理配置文件，并且列示在 CSS 网关中。

**解决方法：**这可能是因为你有一个自定义进程用于删除未加入域的设备，或者是因为该用户已从订阅停用该设备。 若要验证并检查从 Configuration Manager 控制台中删除了该设备的是哪个进程或用户帐户，请执行以下步骤。

#### <a name="check-how-device-was-removed"></a>检查设备的删除途径

1.  在 Configuration Manager 管理控制台中，选择**监视** &gt; **系统状态** &gt; **状态消息查询**。

2.  右键单击“已手动删除的集合成员资源”，并选择“显示消息”。

3.  选取适当的时间/日期或过去 12 小时。

4.  找到有问题的设备，并查看该设备的删除途径。 下面的示例显示帐户 SCCMInstall 是通过某个未知应用程序删除设备的。

    ![设备删除诊断的屏幕快照](./media/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  确保 Configuration Manager 没有计划的任务、脚本或其他可能自动清除非域设备、移动设备或相关设备的进程。




### <a name="other-ios-enrollment-errors"></a>其他 iOS 注册错误
文档 [Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune)（Microsoft Intune 中的 iOS 设备注册问题疑难解答）中提供了 iOS 注册错误列表。

## <a name="pc-issues"></a>电脑问题


|错误消息|问题|解决方法|
|---|---|---|
|**IT 管理员需要分配许可证才能进行访问**<br>IT 管理员未授予你使用此应用的权限。 请向 IT 管理员寻求帮助或稍后重试。|无法注册设备，因为该用户的帐户没有必要的许可证。|必须先为用户分配必要的许可证，用户才能注册其设备。 此消息表明用户持有的指定移动设备管理机构许可证类型不正确。 例如，如果已将 Intune 指定为移动设备管理机构，并且用户正在使用 System Center 2012 R2 Configuration Manager 许可证，则将收到此错误消息。<br>请参阅有关如何[将 Intune 许可证分配给用户帐户](https://docs.microsoft.com/intune/licenses-assign)的信息。|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>该计算机已注册 - 错误 hr 0x8007064c
**问题：**注册失败，出现“该计算机已注册”错误。 注册日志显示错误 **hr 0x8007064c**。

可能的原因是计算机先前已注册，或具有某台已注册的计算机的克隆映像。 先前帐户的帐户证书仍在此计算机上。



**解决方法：**

1. 在“开始”菜单中，键入“运行” -> “MMC”。
1. 选择“文件” > “添加/删除管理单元”。
1. 双击“证书”，选择“计算机帐户” > “下一步”，然后选择“本地计算机”。
1. 双击“证书(本地计算机)”，然后选择“个人/证书”。
1. 查找 Sc_Online_Issuing 发布的 Intune 证书，并将其删除（若存在）。
1. 如果以下注册表项存在，请将其删除：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** 及所有子项。
1. 尝试重新注册。
1. 如果仍无法注册电脑，请查找并删除此项（若存在）：**KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**。
1. 尝试重新注册。

    > [!IMPORTANT]
    > 此部分、方法或任务包含教你如何修改注册表的步骤。 但是，如果注册表修改不正确，可能会发生严重问题。 因此，请确保认真遵循这些步骤。 为提高保护程度，请在修改之前备份注册表。 那么，如果发生问题，你也可以恢复注册表。
    > 有关如何备份和还原注册表的详细信息，请参阅 [如何在 Windows 中备份和还原注册表](https://support.microsoft.com/kb/322756)

## <a name="general-enrollment-error-codes"></a>常规注册错误代码

|错误代码|可能的问题|建议的解决方法|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |未将客户端计算机上的时钟设置为正确的时间。|确保将客户端计算机上的时钟和时区设置为正确的时间和时区。|
|0x80240438、0x80CF0438、0x80CF402C|无法连接到 Intune 服务。 检查客户端代理设置。|验证 Intune 是否支持客户端计算机上的代理配置，以及客户端计算机是否能够访问 Internet。|
|0x80240438，0x80CF0438|未配置 Internet Explorer 和本地系统中的代理设置。|无法连接到 Intune 服务。 检查客户端代理设置，确认客户端计算机的代理配置受 Intune 支持，且客户端计算机拥有 Internet 访问。|
|0x80043001、0x80CF3001、0x80043004、0x80CF3004|注册程序包过期。|从“管理”工作区中下载并安装最新的客户端软件包。|
|0x80043002、0x80CF3002|帐户处于维护模式。|当帐户处于维护模式时，你无法注册新客户端计算机。 若要查看帐户设置，请登录到你的帐户。|
|0x80043003、0x80CF3003|帐户被删除。|验证你的帐户和 Intune 订阅是否仍处于活动状态。 若要查看帐户设置，请登录到你的帐户。|
|0x80043005、0x80CF3005|客户端计算机已停用。|等几个小时并从计算机中删除任何较旧版本的客户端软件，然后重试客户端软件安装。|
|0x80043006、0x80CF3006|已达到允许此帐户拥有的最大座位数。|贵组织必须购买附加的座位，你才能在服务中注册更多客户端计算机。|
|0x80043007、0x80CF3007|在安装程序所在的文件夹中找不到证书文件。|在开始安装之前提取所有文件。 请不要重命名或重新定位任何提取的文件：所有文件必须位于同一文件夹中，否则安装将失败。|
|0x8024D015、0x00240005、0x80070BC2、0x80070BC9、0x80CFD015|无法安装软件，因为客户端计算机的重启处于挂起状态。|重启计算机，然后重试客户端软件安装。|
|0x80070032|在客户端计算机上未找到用于安装客户端软件的一个或多个先决条件。|确保所有必需的更新都已安装在客户端计算机上，然后重试客户端软件安装。|
|0x80043008、0x80CF3008|未能启动 Microsoft Online Management 更新服务。|请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。|
|0x80043009、0x80CF3009|已在服务中注册客户端计算机。|你必须先停用客户端计算机，然后才能在服务中重新注册该客户端计算机。|
|0x8004300B、0x80CF300B|无法运行客户端软件安装包，因为不支持客户端上运行的 Windows 的版本。|Intune 不支持客户端计算机上运行的 Windows 的版本。|
|0xAB2|Windows Installer 无法针对自定义操作访问 VBScript 运行时。|此错误是由基于动态链接库 (DLL) 的自定义操作引起的。 对 DLL 进行疑难解答时，可能必须使用 [Microsoft 支持 KB198038：用于打包和部署问题的有用工具](https://support.microsoft.com/kb/198038)中描述的工具。|
|0x80cf0440|到服务终结点的连接已终止。|试用或付费帐户处于挂起状态。 创建一个新的试用或付费帐户，并重新注册。|




### <a name="next-steps"></a>后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。
