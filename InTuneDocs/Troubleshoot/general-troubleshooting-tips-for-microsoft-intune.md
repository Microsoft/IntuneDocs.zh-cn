---
title: "常规疑难解答提示 | Microsoft Intune"
description: "帮助解决 Intune 问题的常规资源。"
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c1e215320168c659d5f838355f6350111d6979b0
ms.openlocfilehash: 3fe277417c82bc4d60f355ac5366f0f7d70039ab


---

# 有关 Microsoft Intune 的常规疑难解答提示
部署 Microsoft Intune 后，你可能会遇到有关配置或客户端的问题。 下面的资源可帮助你找出问题的原因，以便解决问题。

> [!NOTE]
> 若要创建支持请求或查看现有请求，请[访问 Office 365 管理中心](https://portal.office.com/admin/default.aspx)。 有关支持选项的详细信息，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)。
## 定义问题

-   行为是什么？

-   经历此行为的人员、平台和设备是什么？

-   设备之前是否正常工作？

-   你对 Intune 或设备配置进行了什么更改？

-   请考虑除对配置的更改外，对操作环境是否还进行了其他更改。

-   此问题发生的频率，是偶尔发生还是连续发生？

-   用户是否可能遇到身份验证问题？ 如果可能遇到此问题，请检查用户是否可以登录到使用 Azure Active Directory 的其他服务。 此外，请查看用户可以从另一个设备登录。

-   是否已检查服务状态？ 你可以在 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中监视 Intune 服务运行状况。 在左侧窗格中选择**服务运行状况**。

## 收集可用数据

-   设备日志。 在以下位置了解如何收集设备日志：
  - [使用 USB 电缆将 Android 诊断数据日志发送给 IT 管理员](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [使用电子邮件将 Android 诊断数据日志发送给 IT 管理员](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [将 Android 注册错误发送给 IT 管理员](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [将 iOS 注册错误发送给 IT 管理员](/intune/enduser/send-errors-to-your-it-admin-ios)

-   例如，管理控制台数据，对于策略实施问题，你应该检查目标策略及其状态，如[通过 Microsoft Intune 使用组来管理用户和设备](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)。

## 研究解决方案

-   在 Web 上搜索解决方案。 例如，如果你收到错误 0x80073CF0，你可以在 Web 上搜索 **technet intune 0x80073cf0**，找到文章 [Microsoft Intune 中的应用部署问题疑难解答](troubleshoot-app-deployment-problems-in-microsoft-intune.md)，它提供了解决此问题的建议。

-   你可以在 [Intune TechNet 论坛](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)搜索答案。  如果以前未解决过该问题，则你应该发布该问题以查看社区可能具有的建议。

-   你可以建立支持请求。 如果你已经定义问题并收集可用数据，Intune 支持将能够更好地帮助你解决问题。

    要创建支持请求，请[访问 Office 365 管理中心](https://portal.office.com/admin/default.aspx)。 有关支持选项的详细信息，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)。

## 社区资源
你可以在以下社区资源中查找其他有用信息：

-   [Microsoft Intune 生存指南](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx)中包含指向许多资源的链接，这些资源可帮助你配置、维护 Intune 以及进行疑难解答。

-   [Intune 博客](http://blogs.technet.com/b/windowsintune/)

-   [在 Twitter 上关注 Intune](https://twitter.com/MSIntune)

-   [Intune 论坛](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### 后续步骤
下面列出的主题包含针对特定问题的疑难解答帮助。 如果该信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。

[Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[排查 Microsoft Intune 中的公司资源访问权限问题](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Microsoft Intune 中的应用部署问题疑难解答](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[排查 Intune 中的设备注册问题](troubleshoot-device-enrollment-in-intune.md)

[排查 Microsoft Intune 中的策略问题](troubleshoot-policies-in-microsoft-intune.md)

[排查 Microsoft Intune 中的客户端安装问题](troubleshoot-client-setup-in-microsoft-intune.md)

[排查 Microsoft Intune 中的软件更新问题](troubleshoot-software-updates-in-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


