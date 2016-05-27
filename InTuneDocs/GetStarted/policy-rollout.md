---
# required metadata

title: 策略推出 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 390d5adf-86d2-4e23-ba93-1e61e6b1028b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 策略推出
本主题针对在 Microsoft Intune 中策略的分阶段推出提供了具体的建议。 此方法适用于你在新的 Intune 部署中应用的第一个策略，或者你添加到现有部署的策略。

有关推出阶段的一般信息，请参阅 [Microsoft Intune 部署的推出阶段](rollout-phases-for-microsoft-intune-deployment.md)

### 策略推出的阶段
策略推出的阶段是：

-   项目审视

-   概念证明

-   试点

-   企业推出

-   操作和维护

## 项目审视
定义你的 Intune 策略部署的范围：

-   对于新的实施，将需要定义所有你想用你的策略集创建的所需设备行为和安全要求。

-   确定你要用这些策略影响哪些用户和设备。

-   设计用户和设备组以让你能够适当地应用新策略。

-   确定是否有限制或要求与将影响你的策略意图的每个操作系统相关。

-   考虑策略设计细节，如要使用的策略类型和模板。

-   不论你是要发布第一个策略集还是要将新策略添加到现有策略集，都请考虑各种不同策略之间如何交互和设备行为可能是什么。 可以在试点阶段发现策略交互和冲突的问题，但在早期规划中捕获冲突则可以简化试点的执行。

## 概念证明
在概念证明阶段，在实验室环境中对已严格配置为用于测试目的的设备和用户进行策略部署测试。

-   让支持人员参与此阶段，以了解试点和生产部署期间可能出现的问题。 [排查 Microsoft Intune 中的策略问题](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)中提供了故障排除信息

-   此时应当为试点和生产用户制定沟通计划。 该计划至少应包括以下内容：将改变的设备行为是什么以及何时改变、改变的业务目的为何，以及如果用户或 IT 人员遇到问题时要采取的措施（包括自助服务信息和如何与支持人员联系）。

## 试点
在试点期间，你将为一小组测试用户和设备部署策略。 在 Intune 中进行策略试点有以下特定注意事项：

-   测试组对策略在产品推出时将应用到的组应具有代表性。

-   对支持人员进行有关策略更改的培训，并确保他们已准备好帮助测试组中的用户。

-   激活你的试点用户沟通计划。

-   试点可以先在独立模式下进行，设备在其中不会受制于可能导致冲突和意外行为的其他策略。

-   最终测试必须考虑将应用于同一个设备的新策略和所有现有策略。

## 企业推出

-   根据试点的结果，调整你已规划的策略以纠正策略冲突和意外行为。

-   向支持人员通知企业推出计划。 建立相关机制，以响应帮助请求以及根据需要调整推出。

-   准备好在出现问题时进行策略故障排除。

-   激活你的生产用户沟通计划。

-   将策略以增量方式应用到其他组，从而监视受影响设备的策略状态和跟踪可能与新策略相关的支持人员请求。

## 操作和维护
**操作：**监视 Intune 控制台中的警报以及用户或设备问题，并检查策略是否按照你的设计执行。

**支持人员：**确保支持人员了解将影响用户体验的策略的任何更改，因为这些可能会引发支持请求。


### 另请参阅
[准备好使用 Microsoft Intune 配置移动应用管理策略](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[排查 Microsoft Intune 中的策略问题](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)


<!--HONumber=May16_HO2-->


