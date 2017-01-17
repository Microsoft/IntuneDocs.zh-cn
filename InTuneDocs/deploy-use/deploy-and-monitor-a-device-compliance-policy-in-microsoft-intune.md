---
title: "部署和监视合规性策略 | Microsoft Docs"
description: "使用本主题中的分步说明来部署和监视设备合规性策略。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 59c107b9431d4e2925b13d09ab3e01a25c8351fa


---

# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>在 Microsoft Intune 中部署和监视设备法规遵从性策略

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>部署合规性策略
将你[创建](create-a-device-compliance-policy-in-microsoft-intune.md)的合规性策略部署到组织中的一个或多个用户组。 将合规性策略部署到用户后，会对用户设备检查合规性。

1.  在“策略”工作区中，选择想要部署的策略，然后选择“管理部署”。
![合规性策略页面的屏幕截图，显示顶部的“管理部署”菜单选项](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  在“管理部署”对话框中，选择要对其部署策略的一个或多个组，然后选择“添加” > “确定”。
![“管理部署”对话框的屏幕截图](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png)使用刚才创建的 Active Directory 组并同步到 Intune，或在 Intune 控制台中手动创建这些组。 若要了解有关如何部署策略的详细信息，请参阅[部署配置策略](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

使用“策略”工作区“概述”页的状态摘要和警报来识别需要关注的策略问题。 此外，状态摘要会显示在“仪表板”  工作区中。

> [!IMPORTANT]
> 如果尚未部署合规性策略，但是启用了 Exchange 条件访问策略，则所有目标设备都将获得访问权限。

## <a name="monitor-the-compliance-policy"></a>监视合规性策略

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>要查看不符合法规遵从性策略的设备

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“组” > “所有设备”。

2.  双击设备列表中设备的名称。

3.  选择“策略”选项卡以查看该设备的策略列表。

4.  从“筛选器”下拉列表中，选择“不符合合规性策略”。
![显示筛选器列表中的选项列表的屏幕截图](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>查看运行状况证明报告

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“报告”。

2.  在“运行状况证明报告 - 创建新的报告”页面，可以查看 Intune 收集的包含所有 Windows 10 运行状况证明数据的报告。 也可以使用筛选器创建包含数据子集的报告。 筛选器可基于设备类型、操作系统或数据点子集。

## <a name="how-intune-resolves-policy-conflicts"></a>Intune 如何解决策略冲突
多个 Intune 策略应用到设备时可能会发生策略冲突。 如果策略设置重叠，Intune 将使用以下规则解决所有冲突：

-   如果冲突的设置来自 Intune 配置策略和合规性策略，那么合规性策略中的设置优先于配置策略中的设置。 即使配置策略中的设置更安全，也会发生这种情况。

-   如果部署了多个合规性策略，Intune 将使用其中最安全的策略。

## <a name="next-steps"></a>后续步骤
若要了解如何将合规性策略与条件访问策略配合使用，以控制对组织中服务的访问，请参阅[限制对电子邮件和 O365 服务的访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。


### <a name="see-also"></a>另请参阅
[Intune 中的设备合规性策略简介](introduction-to-device-compliance-policies-in-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


