---
title: Microsoft Intune 中的 Windows 设备注册问题疑难解答
titleSuffix: Microsoft Intune
description: 对在 Intune 中注册 Windows 设备时解决一些最常见问题的建议。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dae8e92209a8640ab3254e073d3043d390c3791b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514245"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune 中的 Windows 设备注册问题疑难解答

本文可帮助 Intune 管理员在 Intune 中注册 Windows 设备时了解和解决问题。

## <a name="prerequisites"></a>必备条件
在开始故障排除之前，请务必收集一些基本信息。 此信息可帮助你更好地了解问题并缩短找到解决方法的时间。

收集有关问题的下列信息：
- 是否向用户分配了有效的 Intune 许可证？ 必须先为用户分配必要的许可证，用户才能注册其设备。
- Windows 设备上是否安装了最新的更新？ Intune 中的某些功能仅适用于最新版本的 Windows。 Windows 更新提供了许多针对已知问题的修补程序。 应用所有最新的更新通常可以修复 Windows 设备注册问题。 
- 确切错误消息是什么？
- 在哪里看到错误消息？
- 何时开始出现问题？ 注册成功了吗？ 
- 哪个平台（Android、iOS/iPadOS、Windows）存在问题？
- 有多少用户受到影响？ 是所有用户都受影响还是仅仅一部分用户受影响？
- 有多少设备受到影响？ 是所有设备都受影响还是仅仅一部分设备受影响？
- 什么是 MDM 机构？
- 如何执行注册？ 是“自带设备”(BYOD) 还是带有注册配置文件的 Apple 设备注册计划 (DEP)？

## <a name="error-messages"></a>错误消息

### <a name="this-user-is-not-authorized-to-enroll"></a>此用户未经授权，无法注册。

错误 0x801c003：“此用户未经授权，无法注册。 你可以重试此操作，或与系统管理员联系并提供错误代码 (0x801c0003)。”
错误 80180003：“出现错误。 此用户未经授权，无法注册。 你可以重试此操作，或与系统管理员联系并提供错误代码 80180003。”

 原因：以下任何条件： 

- 用户在 Intune 中注册的设备数已超出允许的上限。    
- 设备由于设备类型限制而被阻止。    
- 该计算机运行的是 Windows 10 家庭版。 但是，只有 Windows 10 专业版和更高版本才支持在 Intune 中注册或加入 Azure AD。

#### <a name="resolution"></a>解决方法
该问题有以下几种可能的解决方法：

##### <a name="remove-devices-that-were-enrolled"></a>删除已注册的设备
1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。    
2. 转到“用户”   > “所有用户”  。    
3. 选择受影响的用户帐户，然后单击“设备”  。    
4. 选择任何未使用或不需要的设备，然后单击“删除”  。 

##### <a name="increase-the-device-enrollment-limit"></a>增加设备注册限制

> [!NOTE]
> 此方法会增加所有用户的设备注册限制，而不只是针对受影响的用户。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 转到“设备” > “注册限制” > “默认”（位于“设备限制”下）>“属性” > “编辑”（在“设备限制”旁边）> 增加“设备限制”（最多 15 台）>“审核 + 保存”          。    
 

##### <a name="check-device-type-restrictions"></a>查看设备类型限制
1. 使用全局管理员帐户登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 转到“设备”   > “注册限制”  ，然后在“设备类型限制”  下选择“默认”  限制。    
3. 选择“平台”  ，然后针对“Windows (MDM)”选择“允许”   。

    > [!IMPORTANT]
    > 如果当前设置已是“允许”  ，请将其更改为“阻止”  ，保存设置，然后将其更改回“允许”  并再次保存设置。 这样便会重置注册设置。

4. 等待大约 15 分钟，然后再次注册受影响的设备。    

##### <a name="upgrade-windows-10-home"></a>升级 Windows 10 家庭版
[将 Windows 10 家庭版升级到 Windows 10 专业版](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro)或更高版本。 



### <a name="this-user-is-not-allowed-to-enroll"></a>不允许此用户注册。

错误 0x801c0003：“不允许此用户注册。 可以重试操作，或与系统管理员联系并提供错误代码 801c0003。”

**原因：** “用户可以将设备加入 Azure AD”  设置已设置为“无”  。 这会阻止新用户将其设备加入到 Azure AD 中。 因此，Intune 注册失败。

#### <a name="resolution"></a>解决方法
1. 以管理员身份登录到 [Azure 门户](https://portal.azure.com/)。    
2. 转到“Azure Active Directory”   > “设备”   > “设备设置”  。    
3. 将“用户可以将设备加入 Azure AD”设置为“全部”   。    
4. 再次注册设备。   

### <a name="the-device-is-already-enrolled"></a>设备已注册。

错误 8018000a：“出现错误。 设备已注册。  你可以与你的系统管理员联系并提供错误代码 8018000a。”

 原因：符合下列条件之一：
- 另一个用户已经在 Intune 中注册了该设备，或已将该设备加入 Azure AD。 若要确定是否是这种情况，请转到“设置”   > “帐户”   > “工作访问”  。 查找类似于以下内容的消息：“系统上的另一个用户已连接到工作或学校。 请删除该工作或学校连接，然后重试。”    

#### <a name="resolution"></a>解决方法

使用以下某种方法解决该问题：

##### <a name="remove-the-other-work-or-school-account"></a>删除另一个工作或学校帐户
1. 注销 Windows，然后使用已注册或已加入设备的其他帐户登录。    
2. 转到“设置”   > “帐户”   > “工作访问”  ，然后删除工作或学校帐户。
3. 注销 Windows，并使用你的帐户登录。    
4. 在 Intune 中注册设备，或将设备加入 Azure AD。 



### <a name="this-account-is-not-allowed-on-this-phone"></a>此电话不允许使用此帐户。

错误：“此电话不允许使用此帐户。 请确保你提供的信息正确无误，然后重试或请求公司提供支持。”

**原因：** 尝试注册该设备的用户没有有效的 Intune 许可证。

#### <a name="resolution"></a>解决方法
为用户分配有效的 Intune 许可证，然后注册设备。


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>似乎未正确配置 MDM 使用条款终结点。

 原因：符合下列条件之一： 
 - 你对租户同时使用 Office 365 移动设备管理 (MDM) 和 Intune，并且尝试注册该设备的用户没有有效的 Intune 许可证或 Office 365 许可证。     
- Azure AD 中的 MDM 条款和条件为空白或不包含正确的 URL。    

#### <a name="resolution"></a>解决方法

若要解决此问题，请使用下列方法之一： 
 
##### <a name="assign-a-valid-license-to-the-user"></a>向用户分配有效的许可证
转到 [Microsoft 365 管理中心](https://portal.office.com/adminportal/home)，然后向用户分配 Intune 或 Office 365 许可证。

##### <a name="correct-the-mdm-terms-of-use-url"></a>更正 MDM 使用条款 URL
  1. 登录到 [Azure 门户](https://portal.azure.com/)，然后选择“Azure Active Directory”  。    
  2. 选择“移动性(MDM 和 MAM)”  ，然后单击“Microsoft Intune”  。    
  3. 选择“还原默认 MDM URL”  ，确认“MDM 使用条款 URL”  设置为“https://portal.manage.microsoft.com/TermsofUse.aspx”  。    
  4. 选择 **“保存”** 。    


### <a name="something-went-wrong"></a>出现错误。

错误 80180026：“出现错误。 请确认你使用的登录信息正确无误，并且你的组织正在使用此功能。 你可以尝试再次执行此操作，或与系统管理员联系并提供错误代码 80180026。”

**原因：** 当你尝试将 Windows 10 计算机加入 Azure AD 并且满足以下两个条件时，会发生此错误： 
- 在 Azure 中启用了 MDM 自动注册。    
- 在 Windows 10 计算机上已安装 Intune PC 客户端（Intune PC 代理）。

#### <a name="resolution"></a>解决方法
使用以下某种方法解决该问题：

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>在 Azure 中禁用 MDM 自动注册。
1. 登录到 [Azure 门户](https://portal.azure.com/)。    
2. 转到“Azure Active Directory” > “移动性(MDM 和 MAM)” > “Microsoft Intune”    。    
3. 将“MDM 用户范围”  设置为“无”  ，然后单击“保存”  。    
     
##### <a name="uninstall"></a>“卸载”
从计算机上卸载 Intune PC 客户端代理。    

### <a name="the-software-cannot-be-installed"></a>无法安装该软件。

错误：“无法安装该软件，0x80cf4017。”

**原因：** 客户端软件已过期。

#### <a name="resolution"></a>解决方法
1. 登录到 [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)。    
2. 转到“管理”   > “客户端软件下载”  ，然后单击“下载客户端软件”  。    
3. 保存安装包，然后安装客户端软件。 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>帐户证书无效并可能已过期。

错误：“帐户证书无效并可能已过期，0x80cf4017。”

**原因：** 客户端软件已过期。

#### <a name="resolution"></a>解决方法
1. 登录到 [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)。    
2. 转到“管理”   > “客户端软件下载”  ，然后单击“下载客户端软件”  。    
3. 保存安装包，然后安装客户端软件。    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>你的组织不支持此版本的 Windows。 

错误：“出现问题。 你的组织不支持此版本的 Windows。  (0x80180014)”

**原因：** 在 Intune 租户中禁用了 Windows MDM 注册。

#### <a name="resolution"></a>解决方法
若要在独立 Intune 环境中解决此问题，请执行以下步骤： 
 
1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “注册限制”  ，然后选择设备类型限制。    
2. 选择“属性”   > “编辑”  （在“平台设置”  旁边），针对“Windows (MDM)”选择“允许”   。    
3. 单击“查看 + 保存”  。    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>批量注册过程中发生了安装失败。

**原因：** 不允许相应预配包的帐户包 (Package_GUID) 中的 Azure AD 用户帐户将设备加入 Azure AD。 为 Windows 配置设计器 (WCD) 或设置学校电脑应用安装预配包时，会自动创建这些 Azure AD 帐户，然后使用这些帐户将设备加入 Azure AD。

#### <a name="resolution"></a>解决方法
1. 以管理员身份登录到 [Azure 门户](https://portal.azure.com/)。    
2. 转到“Azure Active Directory”>“设备”>“设备设置”  。    
3. 将“用户可以将设备加入 Azure AD”  设置为“全部”  或“已选择”  。

   如果选择“已选定” **，请单击“已选定”**  ，然后单击“添加成员”  添加可以将其设备加入 Azure AD 的所有用户。 确保已添加预配包的所有 Azure AD 帐户。
 
有关如何为 Windows 配置设计器创建预配包的详细信息，请参阅[创建适用于 Windows 10 的预配包](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)。

有关设置学校电脑应用的详细信息，请参阅[使用设置学校电脑应用](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app)。


### <a name="auto-mdm-enroll-failed"></a>自动注册 MDM：失败 

尝试使用组策略自动注册 Windows 10 设备时，遇到以下问题： 
- 在任务计划程序的“Microsoft”   > “Windows”   > “EnterpriseMgmt”  下，“由注册客户端创建的用于从 AAD 自动注册 MDM 的计划”  任务的上次运行结果如下所示：“事件 76 自动注册 MDM：失败（未知 Win32 错误代码：0x8018002b）”        
- 在事件查看器中，在“Applications and Services Logs/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/Admin”  下记录以下事件：   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
 原因：符合下列条件之一： 
- UPN 包含未经验证或不可路由的域，例如 .local（如 joe@contoso.local 中的情况）。    
- “MDM 用户范围”  设置为“无”  。 

#### <a name="resolution"></a>解决方法
如果 UPN 包含未经验证或不可路由的域，请执行以下步骤： 

1. 在运行 Active Directory 域服务 (AD DS) 的服务器上，通过在“运行”对话框中键入 dsa.msc   ，打开“Active Directory 用户和计算机”  ，然后单击“确定”  。    
2. 单击域下的“用户”  ，然后执行以下操作：  
    - 如果只有一个受影响的用户，请右键单击该用户，然后单击“属性”  。 在“帐户”  选项卡上，在“用户登录名”  下的“UPN 后缀”下拉列表中，选择一个有效的 UPN 后缀（如 contoso.com），然后单击“确定”  。    
    - 如果有多个受影响的用户，请在“操作”  菜单中选择用户，然后单击“属性”  。 在“帐户”  选项卡上，选中“UPN 后缀”  复选框，在下拉列表中选择一个有效的 UPN 后缀（如 contoso.com），然后单击“确定”  。
3. 等待下一次同步，或者通过在提升的 PowerShell 提示符下运行以下命令，强制从同步服务器执行增量同步：
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

如果将“MDM 用户范围”  设置为“无”  ，请执行以下步骤： 
 
1. 登录到 [Azure 门户](https://portal.azure.com/)，然后选择“Azure Active Directory”  。
2. 选择“移动性(MDM 和 MAM)”  ，然后选择“Microsoft Intune”  。    
3. 将“MDM 用户范围”  设置为“全部”  。 或者，将“MDM 用户范围”  设置为“部分”  ，并选择可以自动注册其 Windows 10 设备的组。    
4. 将“MAM 用户范围”  设置为“无”  。


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>创建 Autopilot 配置文件时出错。

**原因：** 设备名称模板的指定命名格式不符合要求。 例如，对 serial 宏使用小写形式，如 %serial%，而不是 %SERIAL%。

#### <a name="resolution"></a>解决方法

确保命名格式满足以下要求：

- 创建设备的唯一名称。 名称长度必须在 15 个字符或以下，可以包含字母（a-z、A-Z）、数字 (0-9) 和连字符 (‐)。
- 名称不能全为数字。
- 名称不能包含空格。
- 使用 %SERIAL% 宏添加特定于硬件的序列号。 或者，使用 %RAND:<数字的数目>% 宏来添加数字的随机字符串，字符串包含 <数字的数目> 位数。 例如，MYPC-%RAND:6% 的生成名称为 MYPC-123456。

### <a name="something-went-wrong-oobeidps"></a>出现错误。 OOBEIDPS。

**原因：** 如果存在阻止访问标识提供者 (IdP) 的代理、防火墙或其他网络设备，则会出现此问题。

#### <a name="resolution"></a>解决方法
请确保没有阻止对 Autopilot 所需的基于Internet 的服务的访问。 有关详细信息，请参阅 [Windows Autopilot 网络要求](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network)。


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>注册设备以进行移动管理（失败：3，0x801C03EA）。

**原因：** 该设备具有支持 2.0 版的 TPM 芯片，但尚未升级到版本 2.0。

#### <a name="resolution"></a>解决方法
将 TPM 芯片升级到 2.0 版。

如果此问题仍然存在，请检查同一设备是否在两个分配的组中，并且为每个组分配了不同的 Autopilot 配置文件。 如果在两个组中，请确定应将哪个 Autopilot 配置文件应用于哪台设备，然后删除另一个配置文件的分配。

若要详细了解如何使用 Autopilot 在展台模式下部署 Windows 设备，请参阅[使用 Windows Autopilot 部署展台](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)。


### <a name="securing-your-hardware-failed-0x800705b4"></a>保护硬件（失败：0x800705b4）。

错误 800705b4： 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**原因：** 目标 Windows 设备不符合以下任一要求：

- 设备必须具有物理 TPM 2.0 芯片。 具有虚拟 TPM（例如 Hyper-V VM）或 TPM 1.2 芯片的设备不能在自部署模式下使用。
- 设备必须运行以下 Windows 版本之一：
    - Windows 10 版本 1703 或更高版本。
    - 如果使用混合 Azure AD 联接，则为 Windows 10 内部版本 1809 或更高版本。


#### <a name="resolution"></a>解决方法
确保目标设备满足“原因”  部分中所述的两个要求。

若要详细了解如何使用 Autopilot 在展台模式下部署 Windows 设备，请参阅[使用 Windows Autopilot 部署展台](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)。


### <a name="something-went-wrong-error-code-80070774"></a>出现错误。 错误代码 80070774。

错误 0x80070774：出现了问题。 请确认你使用的登录信息正确无误，并且你的组织正在使用此功能。 你可以尝试再次执行此操作，或与系统管理员联系并提供错误代码 80070774。

当设备在“初始登录”屏幕中超时时，在混合 Azure AD Autopilot 方案中重启设备之前通常会发生此问题。 这意味着由于连接问题，无法找到或无法成功访问域控制器。 或者该设备进入了无法加入域的状态。

**原因：** 最常见的原因是正在使用混合 Azure AD 联接，并且在 Autopilot 配置文件中配置了“分配用户”功能。 使用“分配用户”功能可在初始登录屏幕期间在设备上执行 Azure AD 联接，从而使设备处于无法加入本地域的状态。 因此，只应在标准 Azure AD 联接 Autopilot 方案中使用“分配用户”功能。  不应在混合 Azure AD 联接方案中使用该功能。

#### <a name="resolution"></a>解决方法

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “Windows”   > “Windows 设备”  。
2. 选择遇到问题的设备，然后单击最右侧的省略号 (…)。
3. 选择“取消分配用户”  并等待该过程完成。
4. 重新尝试 OOBE 之前，请确保已分配混合 Azure AD Autopilot 配置文件。

#### <a name="second-resolution"></a>第二个解决方法
如果此问题仍然存在，请在托管脱机域加入 Intune 连接器的服务器上检查是否在 ODJ 连接器服务日志中记录了事件 ID 30312。 事件 30312 类似于以下内容：

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

此问题通常是由于错误地将权限委派给创建 Windows Autopilot 设备的组织单位引起的。 有关详细信息，请参阅[增加组织单位中的计算机帐户限制](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit)。

1. 打开“Active Directory 用户和计算机(DSA.msc)”  。
2. 右键单击将用于创建加入混合 Azure AD 的计算机的组织单位，然后选择“委派控制”  。
3. 在“委派控制”向导中，选择“下一步” > “添加” > “对象类型”     。
4. 在“对象类型”窗格中，选中“计算机”复选框，然后选择“确定”    。
5. 在“选择用户、计算机或组”窗格的“输入要选择的对象名称”框中，输入安装连接器的计算机的名称     。
6. 选择“检查名称”  以验证输入，然后单击“确定”   > “下一步”  。
7. 选择“创建要委派的自定义任务” > “下一步”   。
8. 选择“仅文件夹中的以下对象”复选框，然后选择“计算机对象”、“在本文件夹中创建选定对象”和“在本文件夹中删除选定对象”复选框     。
9. 选择“下一步”  。
10. 在“权限”下，选择“完全控制”复选框   。 此操作将选择所有其他选项。
11. 选择“下一步”   > “完成”  。

### <a name="the-enrollment-status-page-times-out-before-the-sign-in-screen"></a>“注册状态”页在登录屏幕之前超时

**原因：** 如果满足以下所有条件，则会出现此问题：
- 你正在使用“注册状态”页跟踪适用于企业的 Microsoft Store 应用。
- 你有一个 Azure AD 条件访问策略，该策略使用“需要将设备标记为符合要求”控件。
- 该策略应用于所有云应用和 Windows。

#### <a name="resolution"></a>解决方法：
尝试执行以下操作之一：
- 对设备执行你的 Intune 符合性策略。 确保在用户登录之前可以确定符合性。
- 对应用商店应用使用脱机许可。 这样，在确定设备符合性之前，Windows 客户端无需检查 Microsoft Store。



## <a name="next-steps"></a>后续步骤

- [Intune 中的设备注册问题疑难解答](../troubleshoot-device-enrollment-in-intune.md)
- [在 Intune 论坛中提问](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [查看 Microsoft Intune 支持团队博客](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [查看 Microsoft 企业移动性和安全性博客](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [获取对 Microsoft Intune 的支持](../fundamentals/get-support.md)
- [查找共同管理注册错误](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
