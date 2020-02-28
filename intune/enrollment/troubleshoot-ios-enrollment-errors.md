---
title: Microsoft Intune 中的 iOS/iPadOS 设备注册问题疑难解答
titleSuffix: Microsoft Intune
description: 对在 Intune 中注册 iOS/iPadOS 设备时解决一些最常见问题的建议。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: a29fab4be6e2046b2c6757505001a7ba3455b8d6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514313"
---
# <a name="troubleshoot-iosipados-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune 中的 iOS/iPadOS 设备注册问题疑难解答

本文可帮助 Intune 管理员在 Intune 中注册 iOS/iPadOS 设备时了解和解决问题。

## <a name="prerequisites"></a>必备条件

在开始故障排除之前，请务必收集一些基本信息。 此信息可帮助你更好地了解问题并缩短找到解决方法的时间。

收集有关问题的下列信息：

- 确切错误消息是什么？
- 在哪里看到错误消息？
- 何时开始出现问题？ 注册成功了吗？
- 哪个平台（Android、iOS/iPadOS、Windows）存在问题？
- 有多少用户受到影响？ 是所有用户都受影响还是仅仅一部分用户受影响？
- 有多少设备受到影响？ 是所有设备都受影响还是仅仅一部分设备受影响？
- 什么是 MDM 机构？
- 如何执行注册？ 是“自带设备”(BYOD) 还是带有注册配置文件的 Apple 设备注册计划 (DEP)？

## <a name="error-messages"></a>错误消息

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>配置文件安装失败。 发生了网络错误。

**原因：** 设备上的 iOS/iPadOS 存在未指定的问题。

#### <a name="resolution"></a>解决方法

1. 若要防止在以下步骤中丢失数据（还原 iOS/iPadOS 会删除设备上的所有数据），请确保备份数据。
2. 将设备置于恢复模式，然后将其还原。 请确保将其设置为新设备。 有关如何还原 iOS/iPadOS 设备的详细信息，请参阅 [https://support.apple.com/HT201263](https://support.apple.com/HT201263)。
3. 重新注册设备。

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>配置文件安装失败。 无法建立到服务器的连接。

**原因：** Intune 租户配置为仅允许公司拥有的设备。 

#### <a name="resolution"></a>解决方法
1. 登录到 Azure 门户。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”   。
3. 选择“设备注册” > “注册限制”   。
4. 在“设备类型限制”  下，选择要设置的限制，然后选择“属性”   > 选择平台  > 针对“iOS”选择“允许”   ，然后单击“确定”  。
5. 选择“配置平台”  ，针对个人拥有的 iOS/iPadOS 设备选择“允许”  ，然后单击“确定”  。
6. 重新注册设备。

**原因：** DNS 中不存在必需的 CNAME 记录。

#### <a name="resolution"></a>解决方法
为公司的域创建 CNAME DNS 资源记录。 例如，贵公司的域为 contoso.com，则在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollment-s.manage.microsoft.com 的 CNAME。

虽然可选择性创建 CNAME DNS 条目，但 CNAME 记录可简化用户的注册。 如果找不到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称 enrollment.manage.microsoft.com。

如果存在多个经过验证的域，则为每个域创建一个 CNAME 记录。 CNAME 资源记录必须包含以下信息：

|类型：|主机名|指向|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小时|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

如果公司对用户凭据使用多个域，请为每个域创建 CNAME 记录。

> [!NOTE]
> 对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

**原因：** 你注册了以前使用其他用户帐户注册的设备，并且以前的用户未相应地从 Intune 中删除。

#### <a name="resolution"></a>解决方法
1. 取消安装当前所有配置文件。
2. 在 Safari 中打开 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)。
3. 重新注册设备。

> [!NOTE]
> 如果注册仍失败，请在 Safari 中删除 cookie（不要阻止 cookie），然后重新注册设备。

**原因：** 该设备已经在另一个 MDM 提供程序中注册。

#### <a name="resolution"></a>解决方法
1. 在 iOS/iPadOS 设备上打开“设置”  ，转到“常规”>“设备管理”  。
2. 删除任何现有的管理配置文件。
3. 重新注册设备。

**原因：** 尝试注册该设备的用户没有 Microsoft Intune 许可证。

#### <a name="resolution"></a>解决方法
1. 转到 [Office 365 管理中心](https://portal.office.com/adminportal/home#/homepage)，然后选择“用户”>“活动用户”  。
2. 选择想要为其分配 Intune 用户许可证的用户帐户，然后选择“产品许可证”>“编辑”  。
3. 将需要分配给该用户的许可证切换到“打开”  位置，然后选择“保存”  。
4. 重新注册设备。

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>不支持此服务。 无注册策略。

**原因：** Intune 中未配置 Apple MDM Push Certificate，或者该证书无效。 

#### <a name="resolution"></a>解决方法

- 如果未配置 MDM Push Certificate，请按照[获取 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate) 中的步骤操作。
- 如果 MDM 推送证书无效，请按照[续订 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate) 中的步骤操作。

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>公司门户暂时不可用。 公司门户应用遇到问题。 如果问题仍然存在，请与系统管理员联系。

**原因：** 公司门户应用已过期或已损坏。

#### <a name="resolution"></a>解决方法
1. 从设备中删除公司门户应用。
2. 从 **App Store** 下载并安装 **Microsoft Intune 公司门户**应用。
3. 重新注册设备。
 > [!NOTE]
    > 如果用户尝试注册的设备数目超过配置允许的设备注册数，也会出现此错误。 如果这些步骤不能解决问题，请按照以下“已达到设备上限”的解决方法步骤操作  。

### <a name="device-cap-reached"></a>已达到设备上限

**原因：** 用户尝试注册的设备数超过设备注册限制。

#### <a name="resolution"></a>解决方法
1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “所有设备”  ，并检查用户已注册的设备数。
    > [!NOTE]
    > 还应让受影响的用户登录到 [Intune 用户门户](https://portal.manage.microsoft.com/)并检查这些用户已注册的设备。 [Intune 用户门户](https://portal.manage.microsoft.com/)中可能显示一些设备，但 [Intune 管理门户](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)中没有显示，此类设备也会计入设备注册限制。
2. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “注册限制”  ，然后查看设备注册限制。 默认情况下，将此限制设置为 15 个。 
3. 如果已注册的设备数已达到限制，请删除不必要的设备，或者增加设备注册限制。 由于每个已注册的设备都使用 Intune 许可证，因此建议首先删除不必要的设备。
4. 重新注册设备。

### <a name="workplace-join-failed"></a>Workplace Join 失败

**原因：** 公司门户应用已过期或已损坏。  

#### <a name="resolution"></a>解决方法
1. 从设备中删除公司门户应用。
2. 从 **App Store** 下载并安装 **Microsoft Intune 公司门户**应用。
3. 重新注册设备。

### <a name="user-license-type-invalid"></a>用户许可证类型无效

**原因：** 尝试注册该设备的用户没有有效的 Intune 许可证。

#### <a name="resolution"></a>解决方法
1. 转到 [Microsoft 365 管理中心](https://portal.office.com/adminportal/home#/homepage)，然后选择“用户”   > “活动用户”  。
2. 选择受影响的用户帐户 >“产品许可证”   > “编辑”  。
3. 验证是否为此用户分配了有效的 Intune 许可证。
4. 重新注册设备。

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>未识别用户名。 此用户帐户无权使用 Microsoft Intune。 如果你认为收到的消息不正确，请与系统管理员联系。

**原因：** 尝试注册该设备的用户没有有效的 Intune 许可证。

1. 转到 [Microsoft 365 管理中心](https://portal.office.com/adminportal/home#/homepage)，然后选择“用户”   > “活动用户”  。
2. 选择受影响的用户帐户，然后选择“产品许可证”   > “编辑”  。
3. 验证是否为此用户分配了有效的 Intune 许可证。
4. 重新注册设备。

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>配置文件安装失败。 新的 MDM 有效负载与旧负载不匹配。

**原因：** 设备上已安装管理配置文件。

#### <a name="resolution"></a>解决方法

1. 在 iOS/iPadOS 设备上打开“设置”  >“常规”   > “设备管理”  。
2. 点击现有的管理配置文件，然后点击“删除管理”  "。
3. 重新注册设备。

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**原因：** Apple Push Notification 服务 (APNs) 证书丢失、无效或已过期。

#### <a name="resolution"></a>解决方法
验证是否已将有效的 APNs 证书添加到 Intune。 有关详细信息，请参阅[设置 iOS/iPadOS 注册](ios-enroll.md)。

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**原因：** Intune 中配置的 Apple Push Notification 服务 (APNs) 证书存在问题。

#### <a name="resolution"></a>解决方法
续订 APNs 证书，然后重新注册设备。

> [!IMPORTANT]
> 请务必续订 APNs 证书。 请勿替换 APNs 证书。 如果替换证书，则必须在 Intune 中重新注册所有 iOS/iPadOS 设备。 

- 若要在 Intune 独立版中续订 APNs 证书，请参阅[续订 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)。
- 若要在 Office 365 中续订 APNs 证书，请参阅[为 iOS/iPadOS 设备创建 APNs 证书](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7)。

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR 连接无效

当你打开一台分配有注册配置文件的受 DEP 管理的设备时，注册将会失败，并且你会收到以下错误消息：

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**原因：** 设备与 Apple DEP 服务之间存在连接问题。

#### <a name="resolution"></a>解决方法
解决连接问题，或使用其他网络连接来注册设备。 如果问题仍然存在，可能还需要联系 Apple。


## <a name="other-issues"></a>其他问题

### <a name="dep-enrollment-doesnt-start"></a>DEP 注册不启动
当你打开分配了注册配置文件的受 DEP 管理的设备时，Intune 注册过程未启动。

**原因：** 在将 DEP 令牌上传到 Intune 之前创建了注册配置文件。

#### <a name="resolution"></a>解决方法

1. 编辑注册配置文件。 可以对配置文件进行任何更改。 目的是更新配置文件的修改时间。
2. 同步 DEP 管理的设备：在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “iOS” > “iOS 注册” > “注册计划令牌”>“选择令牌”>“立即同步”      。 会向 Apple 发送同步请求。

### <a name="dep-enrollment-stuck-at-user-login"></a>在用户登录时，DEP 注册停滞
打开分配有注册配置文件的受 DEP 管理的设备并输入凭据后，初始设置会停滞。

**原因：** 启用了多重身份验证 (MFA)。 在 DEP 设备上注册期间，当前 MFA 不起作用。

#### <a name="resolution"></a>解决方法
禁用 MFA，然后重新注册设备。


## <a name="next-steps"></a>后续步骤

- [Intune 中的设备注册问题疑难解答](../troubleshoot-device-enrollment-in-intune.md)
- [在 Intune 论坛中提问](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [查看 Microsoft Intune 支持团队博客](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [查看 Microsoft 企业移动性和安全性博客](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
