---
title: "移动应用程序管理故障排除 | Microsoft Docs"
description: "本主题介绍条件性访问部署的一些故障排除提示。"
keywords: 
author: oydang
ms.author: oydang
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: a2e43444bff3b189c1516c6ca7131771035313ea
ms.openlocfilehash: 6258917de60bdbf8efde4720c17ec6fc643154bd


---

# <a name="troubleshoot-mobile-application-management"></a>移动应用程序管理故障排除

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若有关于 Intune 移动应用程序管理的问题，请从此处开始阅读。 本主题包含一些用户可能会遇到的常见问题，并提供解决方案和答案。

如果此信息未解决你的问题，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)，了解更多获得帮助的方法。


## <a name="common-it-administrator-issues"></a>IT 管理员常见问题

这些是 IT 管理员使用 Intune 应用保护策略可能会遇到的常见问题。

| 问题 | 说明 | 解决方法 |
| -- | -- | -- |
| 策略不适用于 Skype for Business | Azure 门户中制定的无需设备注册的应用保护策略不适用于 iOS 和 Android 设备上的 Skype for Business 应用。 | 必须将 Skype for Business 设置为进行新式验证。  请按照[为租户启用新式验证](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)中的指示为 Skype 设置新式验证。 |
| Office 应用策略不适用 | 应用保护策略不适用于任何用户的任何[支持的 Office 应用](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)。 | 确认用户已获得 Intune 许可，且 Office 应用是某个已部署的应用保护策略的目标对象。 可能需要最多 8 小时来使新部署的应用保护策略生效。 |
| 管理员无法在 Azure 门户中配置应用保护策略 | IT 管理员用户无法在 Azure 门户中配置应用保护策略。 | 下列用户角色可访问 Azure 门户： <ul><li>全局管理员，可在 [Office 门户](http://portal.office.com/)中设置</li><li>所有者，可在 [Azure 门户](https://portal.azure.com/)设置中。</li><li>参与者，可在 [Azure 门户](https://portal.azure.com/)设置中。</li></ul>  请参阅[准备好使用 Microsoft Intune 配置移动应用管理策略](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)，获取设置这些角色的帮助。|
|应用保护策略报表中缺少用户帐户 | 管理控制台报表不显示最近部署了应用保护策略的用户帐户。 | 若用户是应用保护策略的新目标用户，则可能要 24 小时后，该用户才会在报表中显示为目标用户。 |
| 策略更改无效 | 对应用保护策略的更改和更新可能需要 8 小时才能应用。 | 如果适用，最终用户可注销该应用，然后重新登录，强行与服务同步。 |
| DEP 中无法使用应用保护策略 | 应用保护策略不适用于 Apple DEP 设备。 | 请确保通过 Apple 设备注册计划 (DEP) 使用用户关联。 对需要在 DEP 下进行用户身份验证的应用而言，用户关联是必须的。 <br><br>请参阅 [Enroll corporate-owned Device Enrollment Program iOS devices（将通过“设备注册计划”购买的 iOS 设备注册为企业所有）](../deploy-use/ios-device-enrollment-program-in-microsoft-intune.md)，了解有关 iOS DEP 注册的详细信息。|
| iOS 中无法使用数据传输策略 | **允许应用向其他应用传输数据**和**允许应用从其他应用接收数据**策略未成功管理 iOS 中的数据传输。 | 请参阅[使用 Microsoft Intune 管理 iOS 应用之间的数据传输](/deploy-use/manage-data-transfer-between-ios-apps-with-microsoft-intune.md). |






## <a name="common-end-user-issues"></a>常见最终用户问题

常见最终用户问题细分为以下类别：

* **正常使用场景**：最终用户可能会在具有 Intune 应用保护策略的应用上遇到这些情况。 这些不是实际问题，但可能会被视为 bug 或错误。

* **正常使用对话**：它们是最终用户可能会在具有 Intune 应用保护策略的应用中看到的使用对话。 这些消息和对话**不**指示错误或 bug。

* **错误消息和对话**：它们是最终用户可能会在具有 Intune 应用保护策略的应用中看到的错误消息和对话。 通常会指示由 IT 管理员造成的错误或 Intune 应用保护的 bug。



### <a name="normal-usage-scenarios"></a>正常使用场景

平台 | 方案 | 说明 |
---| --- | --- |
iOS | 即使将数据传输策略设置为“仅托管应用”或“无应用”，最终用户也可使用 iOS 共享扩展在非托管应用中打开工作或学校数据。 这样不会泄漏数据吗？ | 在不管理设备的情况下，Intune 应用保护策略不能控制 iOS 共享扩展。 因此，**Intune 会在应用外共享“企业”数据前先加密数据**。 可通过尝试在托管应用外打开“企业”文件进行验证。 该文件应进行加密，且无法在托管应用外打开。
Android | 为什么即使使用不需设备注册的 MAM 应用保护，最终用户也**需要安装公司门户应用**？  | 在 Android 上，应用保护的许多功能都内置于公司门户应用中。 **虽然始终需要公司门户应用，但无需设备注册**。 对于不需注册的应用保护，最终用户只需在设备上安装公司门户应用即可。

### <a name="normal-usage-dialogs"></a>正常使用对话

平台 | 消息或对话 | 说明 |
--- | --- | --- |
iOS、Android | **登录**：为保护其数据，组织需要管理此应用。 要完成此操作，请使用工作或学校帐户登录。 | 最终用户必须使用其工作或学校帐户登录才能使用此应用，这就需要应用保护策略。 为使策略适用，用户必须对 Azure Active Directory 进行身份验证。
iOS、Android |**需要重启**：组织当前正在此应用中保护其数据。 需重启应用才能继续。 | 应用刚收到 Intune 应用保护策略，必须重启才能应用该策略。
iOS、Android |**操作未允许**：组织仅允许在此应用中打开工作或学校数据。 | IT 管理员已将“允许应用从其他应用接收数据”设置为“仅托管应用”。 因此，最终用户只可将数据从其他具有应用保护策略的应用传输到此应用。
iOS、Android |**操作未允许**：组织仅允许将其数据传输到其他托管应用。 | IT 管理员已将“允许应用将数据传输到其他应用”设置为“仅托管应用”。 因此，最终用户只可将此应用的数据传输到其他具有应用保护策略的应用。
iOS、Android |**擦除警报**：组织已删除与此应用关联的组织数据。 若要继续，请重启应用。 | IT 管理员已使用 Intune 应用保护启动了应用擦除。
Android | **需要公司门户**：若要将工作或学校帐户用于此应用，必须安装 Intune 公司门户应用。 点击“转至商店”继续操作。 | 在 Android 上，应用保护的许多功能都内置于公司门户应用中。 **虽然始终需要公司门户应用，但无需设备注册**。 对于不需注册的应用保护，最终用户只需在设备上安装公司门户应用即可。


### <a name="error-messages-and-dialogs-on-ios"></a>iOS 上的错误消息和对话


错误消息和对话 | 原因 | 补救 |
-- | --- | --- |
**应用未设置**：此应用未设置，尚无法使用。 请联系你的 IT 管理员获取帮助。 | 未能检测到应用所需的应用保护策略。 |确保将 iOS 应用保护策略部署到用户的安全组，并以此应用为目标。
**欢迎使用 Intune Managed Browser**：当由 Microsoft Intune 管理时，此应用运行效果最佳。 可始终使用此应用浏览 Web，并且当它由 Microsoft Intune 管理时，可访问附加的数据保护功能。 | 未能检测到 Intune Managed Browser 应用所需的应用保护策略。 <br><br>用户仍可使用该应用浏览 Web，但该应用不由 Intune 托管。 | 确保将 iOS 应用保护策略部署到用户的安全组，并以 Intune Managed Browser 应用为目标。
**登录失败**：目前无法登录。 请稍后重试。 | 未能在用户尝试使用其工作或学校帐户登录后，向 MAM 服务注册该用户。 | 确保将 iOS 应用保护策略部署到用户的安全组，并以此应用为目标。
**帐户未设置**：组织未设置你的帐户来访问工作或学校数据。 请联系 IT 管理员寻求帮助。 | 用户帐户没有 Intune A Direct 许可证。 | 确保用户的帐户在 [Office 门户](http://portal.office.com)中分配有 Intune 许可证。
**设备不合规**：无法使用此应用，因为正在使用越狱的设备。 请联系你的 IT 管理员获取帮助。 | Intune 检测到用户正在使用越狱的设备。 | 将设备重置为默认出厂设置。 按照 Apple 支持站点中的[这些说明](https://support.apple.com/en-us/HT201274)操作。
**需要 Internet 连接**：必须连接到 Internet 才可验证是否可使用此应用。 | 设备未连接到 Internet。 | 将设备连接到 WiFi 或数据网络。
**未知故障**：尝试重启此应用。 如果问题仍然存在，请与 IT 管理员联系以寻求帮助。 | 发生未知故障。 | 请稍后重试。 如果错误仍然存在，请通过 Intune 在[此处](how-to-get-support-for-microsoft-intune.md)创建支持票证。
**访问组织数据**：指定的工作或学校帐户无权访问此应用。 可能必须使用其他帐户登录。 请联系你的 IT 管理员获取帮助。 | Intune 检测到用户尝试使用另一个工作或学校帐户（不同于已注册 MAM 的设备帐户）登录。 对于每个设备，MAM 一次只能管理一个工作或学校帐户。 | 让用户使用具有通过登录屏幕预填充的用户名的相应帐户登录。 <br> <br> 或让用户使用新的工作或学校帐户登录，并删除已注册 MAM 的现有帐户。
**连接问题**：出现意外的连接问题。 检查连接，然后重试。  |  意外故障。 | 请稍后重试。 如果错误仍然存在，请通过 Intune 在[此处](how-to-get-support-for-microsoft-intune.md)创建支持票证。
**警报**：此应用无法再进行使用。 有关详细信息，请与 IT 管理员联系。 | 验证应用证书失败。 | 确保应用版本为最新。 <br><br> 重新安装应用。
**错误**：此应用遇到问题，必须关闭。 如果此错误仍然存在，请与 IT 管理员联系。 | 未能从 Apple iOS Keychain 读取 MAM 应用 PIN。 | 重启设备。 确保应用版本为最新。 <br><br> 重新安装应用。


### <a name="error-messages-and-dialogs-on-android"></a>Android 上的错误消息和对话

对话框/错误消息 | 原因 | 补救 |
-- | --- | --- |
**应用未设置**：此应用未设置，尚无法使用。 请联系你的 IT 管理员获取帮助。 | 未能检测到应用所需的应用保护策略。 |确保将 Android 应用保护策略部署到用户的安全组，并以此应用为目标。
**应用启动失败**：启动应用时出现问题。 请尝试更新该应用或 Intune 公司门户应用。 如果需要帮助，请与你的 IT 管理员联系。 | Intune 检测到应用适用的有效应用保护策略，但应用在 MAM 初始化过程中崩溃。 | 确保应用版本为最新。 <br><br> 确保 Intune 公司门户应用已安装且在设备上为最新。 <br><br> 如果错误仍然存在，使用公司门户应用将日志发送到 Intune 或在[此处](how-to-get-support-for-microsoft-intune.md)创建支持票证。
**未找到应用**：组织不允许使用此设备上的任何应用来打开此内容。 请联系你的 IT 管理员获取帮助。 | 用户尝试使用另一个应用打开工作或学校数据，但 Intune 找不到任何其他有权打开该数据的托管应用。 | 确保将 Android 应用保护策略部署到用户的安全组，并至少再以另一个启用了 MAM 且可打开相关数据的应用为目标。
**登录失败**：重试登录。 如果此问题仍然存在，请与 IT 管理员联系以寻求帮助。 | 未能验证用户登录时尝试使用的帐户。 | 确保用户使用已注册 Intune MAM 服务的工作或学校帐户（第一个成功登录到此应用的工作或学校帐户）登录。 <br><br> 清除应用数据。 <br><br> 确保应用版本为最新。 <br><br> 确保公司门户版本为最新版。
**需要 Internet 连接**：必须连接到 Internet 才可验证是否可使用此应用。 | 设备未连接到 Internet。 | 将设备连接到 WiFi 或数据网络。
**设备不合规**：无法使用此应用，因为你正在使用已取得 root 权限的设备。 请联系你的 IT 管理员获取帮助。 | Intune 检测到用户正在使用已取得 root 权限的设备。 | 将设备重置为默认出厂设置。
**帐户未设置**：此应用必须由 Microsoft Intune 托管，但帐户尚未设置。 请联系你的 IT 管理员获取帮助。 | 用户帐户没有 Intune A Direct 许可证。 | 确保用户的帐户在 [Office 门户](http://portal.office.com)中分配有 Intune 许可证。
**无法注册应用**：此应用必须由 Microsoft Intune 托管，但目前无法注册此应用。 请联系你的 IT 管理员获取帮助。 | 需要应用保护策略时，未能自动向 MAM 服务注册该应用。 | 清除应用数据。 <br><br> 通过公司门户应用将日志发送给 Intune，或在[此处](how-to-get-support-for-microsoft-intune.md)提供支持票证。




### <a name="see-also"></a>另请参阅
- [验证移动应用管理设置](../deploy-use/validate-mobile-application-management.md)
- [准备好使用 Microsoft Intune 配置移动应用管理策略](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)



<!--HONumber=Dec16_HO5-->


