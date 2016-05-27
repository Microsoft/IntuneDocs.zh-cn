---
# required metadata

title: 迁移到 Intune |Microsoft Intune
description:
keywords:
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 迁移到 Intune


从现有的企业移动性管理解决方案迁移到 Intune 可以按照以下大致的流程进行：

![Intune 的迁移步骤](./media/migrate-intune-steps.png)

## 通知用户

当你确信 Intune 试验性部署满足你的需求时，通知你的用户即将把他们的设备迁移到 Intune。 电子邮件消息、[说明](http://www.microsoft.com/en-us/download/details.aspx?id=46398)和[公告](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT)有助于设定期望目标和提供用户需要采取的注册步骤的详细信息，以便保持与公司资源和应用程序的不间断连接。 请确保你的支持团队已准备好帮助用户完成迁移过程。

## 修改现有的企业移动性管理解决方案

根据你要处理现有的企业移动性管理解决方案和 Intune 之间的条件性访问策略的方式，你可能需要禁用现有的条件性访问策略。 你将禁用现有的条件性访问策略，或者对现有的条件性访问策略设定范围，以便不包括即将迁移到 Intune 的用户/设备。  请勿使 Intune 和现有的企业移动性管理解决方案将条件性访问策略应用到相同的用户/设备。

## 启用 Intune 的条件性访问策略（可选）

如果你决定要立即实施条件性访问策略，而不想因设备迁移而留出宽限期，那么在此步骤中启用 Intune 的条件性访问策略。  请确保以将此决定与你的用户和技术支持人员进行良好的沟通。  如果设备未在 Intune 中注册或者不符合 Intune 策略，那么用户将无法访问公司资源。

## 从现有的企业移动性管理解决方案中注销设备

在 Intune 中注册设备之前必须从现有企业移动性管理解决方案中注销设备。 我们的建议是允许用户亲自注销其设备以获取最佳用户体验。  请务必遵循解决方案提供商的注销设备指南，以确保正确从平台删除用户和设备，并将与最终用户的连接中断的可能性降到最低。

## 在 Intune 中注册设备

计划执行迁移的用户应立即在 Intune 中注册，以便重新获得或防止丢失公司资源、电子邮件和应用程序的访问权限。 如果你已配置条件性访问，并且用户未在 Intune 中注册，那么当用户尝试连接到电子邮件时，他们的访问将被阻止，并且他们将收到注册电子邮件。 此电子邮件将引导他们在 Intune 中注册其设备。  或者，用户可以通过 Intune 公司门户应用注册 Intune，或者通过 Windows 8.1 和 Windows 10 Mobile 的操作系统在本机上注册。 有关每个平台的注册步骤的更多指南，请参阅 [What to tell your end users about using Microsoft Intune（最终用户需要了解的有关 Microsoft Intune 使用的内容）](what-to-tell-your-end-users-about-using-microsoft-intune.md)。

## 配置 Intune 的条件性访问（可选）

如果你已允许为条件性访问实施留出宽限期，那么当你与最终用户沟通的宽限期结束时，请在 Intune 中启用条件性访问策略以实施该策略。 这将立即要求所有设备都满足 Intune 条件性访问策略的要求。

## 注册剩余的设备和用户

现在你已启用条件性访问，所有用户都需要在 Intune 中注册并满足组织的合规性策略，以获取对公司资源的访问权限。 如果你在分阶段注册（不是一次性注册）中迁移了用户，那么请重复上述步骤，直到所有设备和用户都已注册且由 Intune 进行管理。

## 停用之前的企业移动性管理解决方案

将你的所有用户和设备迁移到 Intune 后，并且已验证到 Intune 的迁移是成功的，你可以停用以前的企业移动性管理解决方案和/或取消订阅该服务。 请务必遵循解决方案提供商的指南，以确保正确删除任何不需要的基础结构需求和取消任何订阅/许可证。

## 其他迁移资源

是否需要与迁移到 Intune 相关的更多帮助？ 我们可以提供专家帮助以确保迁移不会有任何问题：

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Microsoft 咨询服务](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Intune 技术和非技术支持](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Microsoft Intune TechNet 论坛](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## 获取该指南的可下载副本

若要获取此完整指南的可下载副本，请访问 [TechNet 库](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387)。


<!--HONumber=May16_HO2-->


