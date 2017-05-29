---
title: "常规疑难解答提示 | Microsoft Docs"
description: "帮助解决 Intune 问题的常规资源。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 63bb7ca097390582d85f3ea7daced42d2a97fbb4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>有关 Microsoft Intune 的常规疑难解答提示

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

部署 Microsoft Intune 后，可能会遇到有关配置或客户端设备的问题。 使用以下资源可帮助你发现问题的原因，以便解决问题。

> [!NOTE]
> 若要创建支持请求或查看现有请求，请[访问 Office 365 管理中心](https://portal.office.com/admin/default.aspx)。 有关支持选项的详细信息，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)。

## <a name="define-the-problem"></a>定义问题

-   行为是什么？

-   经历此行为的人员、平台和设备是什么？

-   设备之前是否正常工作？

-   你对 Intune 或设备配置进行了什么更改？

-   除对配置的更改外，对操作环境是否还进行了其他更改？

-   此问题发生的频率，是偶尔发生还是连续发生？

-   用户是否可能遇到身份验证问题？ 如果可能遇到此问题，请检查用户是否可以登录到使用 Azure Active Directory 的其他服务。 此外，请查看用户是否可以从另一个设备登录。

-   是否已检查服务状态？ 你可以在 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中监视 Intune 服务运行状况。 在左侧窗格中选择**服务运行状况**。

## <a name="collect-available-data"></a>收集可用数据

-   以下资源可帮助你了解如何收集设备日志：
  - [使用 USB 电缆将 Android 诊断数据日志发送给 IT 管理员](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [使用电子邮件将 Android 诊断数据日志发送给 IT 管理员](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [将 Android 注册错误发送给 IT 管理员](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)
  - [将 iOS 注册错误发送给 IT 管理员](/intune-user-help/send-errors-to-your-it-admin-ios)

-   利用管理控制台数据（例如，策略实现问题），检查目标策略和该策略的状态，如通过 Microsoft Intune 使用组来管理用户和设备 /intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune) 中所述。

## <a name="research-the-solution"></a>研究解决方案

-   在 Web 上搜索解决方案。 例如，如果收到错误 0x80073CF0，可以在 Web 上搜索 **technet intune 0x80073cf0**，找到文章[解决 Microsoft Intune 中的应用部署问题](troubleshoot-app-deployment-problems-in-microsoft-intune.md)。 此文章提供了有关解决此错误的建议。

-   在 [Intune TechNet 论坛](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)中搜索答案。  如果以前未解决过该问题，则发布该问题以查看社区可能的建议。

-   打开支持请求。 如果已经定义问题并收集了可用数据，Intune 支持将能够更好地帮助你解决问题。

    要创建支持请求，请[访问 Office 365 管理中心](https://portal.office.com/admin/default.aspx)。 有关支持选项的详细信息，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)。

## <a name="find-community-resources"></a>查找社区资源
你可以在以下社区资源中查找其他有用信息：

-   [Microsoft Intune 生存指南](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx)中包含指向许多资源的链接，这些资源可帮助你配置、维护 Intune 以及进行疑难解答。

-   [Intune 博客](http://blogs.technet.com/b/windowsintune/)

-   [在 Twitter 上关注 Intune](https://twitter.com/MSIntune)

-   [Intune 论坛](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>后续步骤
下面列出的主题包含针对特定问题的疑难解答。 如果该信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。

[Microsoft Intune 中的 Endpoint Protection 疑难解答](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Microsoft Intune 中的公司资源访问权限问题疑难解答](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Microsoft Intune 中的应用部署问题疑难解答](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Intune 中的设备注册问题疑难解答](troubleshoot-device-enrollment-in-intune.md)

[Microsoft Intune 中的策略问题疑难解答](troubleshoot-policies-in-microsoft-intune.md)

[Microsoft Intune 中的客户端安装问题疑难解答](troubleshoot-client-setup-in-microsoft-intune.md)

[Microsoft Intune 中的软件更新问题疑难解答](troubleshoot-software-updates-in-microsoft-intune.md)

