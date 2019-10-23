---
title: 在 Microsoft Intune 中使用 Windows 更新的更新符合性报告
titleSuffix: Microsoft Intune
description: 使用 OMS 更新符合性查看向 Intune 部署的 Windows 更新的报告数据。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55fa1109fde57e3104c8bb15e1f45761d661c735
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508729"
---
# <a name="intune-compliance-reports-for-updates"></a>Intune 的更新符合性报告
使用 Intune 将 Windows 更新部署到 Windows 10 设备时，请使用 Intune 或名为“更新符合性”的免费解决方案查看有关更新符合性的详细信息，其中该方案是 Microsoft Operations Management Suite (OMS) 的一部分  。

## <a name="use-intune"></a>使用 Intune
查看已配置的 Windows 10 更新通道的部署状态策略报告： 
1. 登录到 [Azure 门户](https://portal.azure.com/)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”    。
3. 选择“软件更新” > “概述”   。 可查看有关已分配的任意更新通道状态的一般信息。
4. 打开以下报告之一：  

   **对于所有部署通道**：
   1. 在“软件更新” > “Windows 10 更新通道”上  
   2. 在“监视”部分，选择“每个更新通道的部署状态”   。  

   **对于特定部署通道**：  

   1. 在“软件更新” > “Windows 10 更新通道”中，选择要查看的部署通道   。  
   2. 在“监视”部分，从下列报表中进行选择以查看有关更新通道的更详细信息：   
      - **设备状态**  
      - **用户状态**  

## <a name="use-update-compliance"></a>使用更新符合性
可使用[更新符合性](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)这一 Windows Analytics 解决方案来监视 Windows 10 更新的推出情况。 更新符合性通过 Azure 门户提供，满足其[先决条件](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites)的设备可免费使用。  

使用此解决方案时，可将商业 ID 部署到要报告其更新符合性且由 Intune 托管的任意 Windows 10 设备上。  

在 Intune 控制台中，可使用自定义策略的 OMA-URI 设置来配置商业 ID。 有关详细信息，请参阅 [Microsoft Intune 中适用于 Windows 10 设备的 Intune 策略设置](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)。  

用于配置商业 ID 的 OMA-URI（区分大小写）路径为：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID   

例如，你可以在“**添加或编辑 OMA-URI 设置**”中使用以下值：
- **设置名称**：Windows Analytics 商业 ID
- **设置说明**：为 Windows Analytics 解决方案配置商业 ID
- OMA-URI（区分大小写）：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID  
- **数据类型**：字符串
- **值**：\<使用 OMS 工作区中 Windows 遥测选项卡上显示的 GUID>
 
> [!NOTE]  
> 有关 MS DM 服务器的详细信息，请参阅 [DMClient 配置服务提供程序 (CSP)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp)。

## <a name="next-steps"></a>后续步骤
[管理 Intune 中的软件更新](windows-update-for-business-configure.md)

