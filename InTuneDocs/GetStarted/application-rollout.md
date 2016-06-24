---
# required metadata

title: 应用程序推出 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0fc32ed3-bcf4-472a-80e7-eb20986f78fa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 应用程序推出
本主题针对在 Microsoft Intune 中分阶段推出应用提供了具体的建议。 有关推出阶段的一般信息，请参阅 [Microsoft Intune 部署的推出阶段](rollout-phases-for-microsoft-intune-deployment.md)

### 应用的推出阶段
应用的推出阶段分为：

-   项目审视

-   概念证明

-   试点

-   企业推出

-   操作和维护

## 项目审视
请考虑下列各项：

-   应用旨在启用的用户任务。

-   应用对你的用户及其设备（可能会使用的所有操作系统）的适用性。

-   确认你选择的应用安装程序受 Intune 应用分发的支持，如[使用 Microsoft Intune 添加应用](/intune/deploy-use/add-apps)中所述

-   确保安装了应用分发必备组件。 <!---, as described in [Plan for app deployment in Microsoft Intune](plan-for-app-deployment-in-microsoft-intune.md--->确定应用类型受 Intune 支持。

-   确认你有足够的云存储空间可用于上载应用。

-   [使用 Microsoft Intune 添加应用](/intune/deploy-use/add-apps)中提供了有关购买附加存储的说明 概念证明

## 在概念证明阶段，在实验室环境中对已严格配置为用于测试的设备和用户进行应用部署测试。
让支持人员参与此阶段，以了解试点和生产部署期间可能出现的问题。

-   [Microsoft Intune 中的应用部署问题疑难解答](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)中提供了疑难解答信息 此时应当为试点和生产用户制定沟通计划。

-   该计划至少应包括以下内容：要部署的应用，用户如何以及何时获得该应用，部署的业务目的，以及他们遇到问题时要采取的措施（包括自助服务信息及如何与支持人员联系）。 试点

## 在试点期间，你将为一小组测试用户和设备部署应用。
请考虑下列各项： 确保测试组可代表将在生产推出后使用该应用的用户和设备。

-   对支持人员进行应用部署培训，并确保他们已准备好帮助测试组中的用户。

-   选择将典型地使用应用并且确实会向试点管理员报告问题的测试用户。

-   激活你的试点用户沟通计划。

-   企业推出

## 使用试点结果来调整你的企业推出。

-   向支持人员通知应用推出计划。

-   建立相关机制，以响应帮助请求以及根据需要调整推出。 准备好在出现问题时进行部署故障排除。

-   激活你的生产用户沟通计划。

-   采用分阶段方法部署应用，并以增量方式添加组以确保能够顺利推出。

-   操作和维护

## **操作：**监视 Intune 控制台中的警报以及用户或设备问题，并确保应用程序分发按设计正常运行。
**支持人员：**确保支持人员得知任何应用可用性更改，这类更改可能会导致支持请求。

另请参阅

### 部署应用
[Microsoft Intune 中的应用部署问题疑难解答](/intune/deploy-use/deploy-apps)

[Troubleshoot app deployment problems in Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)


<!--HONumber=May16_HO2-->


