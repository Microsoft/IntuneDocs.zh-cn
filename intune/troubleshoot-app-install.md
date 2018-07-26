---
title: 排查应用安装问题
titlesuffix: Microsoft Intune
description: Microsoft Intune 疑难解答窗格有助于排查应用安装问题。
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: c1c2a37103f8fedc09a70b4387aae3f472dfb636
ms.sourcegitcommit: dc8b6f802cca7895a19ec38bec283d4b3150d213
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2018
ms.locfileid: "39138673"
---
# <a name="troubleshoot-app-installation-issues"></a>排查应用安装问题

在 Microsoft Intune MDM 托管的设备上，有时应用安装可能会失败。 当这些应用安装失败时，可能难以了解失败原因或解决此问题。 Microsoft Intune 提供应用安装失败详细信息，以便支持人员和 Intune 管理员能够查看应用信息，从而根据请求为用户提供帮助。 Intune 疑难解答窗格提供失败详细信息，包括用户设备上托管应用的详细信息。 在“托管应用”窗格中，可以在各个设备下详细了解应用的端到端生命周期。 可查看安装问题，如应用的创建时间、修改时间、定目标时间以及传递给设备的时间。 

## <a name="to-review-app-troubleshooting-details"></a>查看应用疑难解答详细信息的具体步骤

Intune 根据特定用户设备上安装的应用，提供应用疑难解答详细信息。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“疑难解答”。
4. 单击“选择用户”，选择要对其排查问题的用户。 此时，“选择用户”窗格显示。
5. 通过键入名称或电子邮件地址选择用户。 单击窗格底部的“选择”。 此用户的疑难解答信息显示在“疑难解答”窗格中。 
6. 在“设备”列表中，选择要对其排查问题的设备。
    ![Intune 疑难解答窗格。](media/troubleshoot-app-install-01.png)
7. 在选定设备窗格中，选择“托管应用”。 此时，托管应用列表显示。
    ![Intune 托管的特定设备的详细信息。](media/troubleshoot-app-install-02.png)
8. 在列表中，选择“安装状态”为“失败”的应用。
    ![显示安装失败详细信息的选定应用。](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > 可以将同一应用分配到多个组，但应用的预期操作（意向）应不同。 例如，如果在应用分配期间对用户排除了应用，那么应用的解析意向显示为“已排除”。 有关详细信息，请参阅[如何解决不同应用意向之间的冲突](apps-deploy.md#how-conflicts-between-app-intents-are-resolved)。<br><br>
    > Intune 暂不根据 OS 平台筛选掉应用。

应用安装错误详细信息指出问题所在。 根据这些详细信息，可以确定解决问题的最佳措施。 若要详细了解如何排查应用安装问题，请参阅[用于排查应用安装问题的错误代码](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues)。

> [!Note]  
> 还可通过浏览器前往 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) 来访问“疑难解答”窗格。

## <a name="next-steps"></a>后续步骤

- 有关其他 Intune 疑难解答信息，请参阅[使用疑难解答门户为公司用户提供帮助](help-desk-operators.md)。 
- 了解 Microsoft Intune 中的任何已知问题。 有关详细信息，请参阅 [Microsoft Intune 中的已知问题](known-issues.md)。
- 需要更多帮助？ 请参阅[如何获取对 Microsoft Intune 的支持](get-support.md)。
