---
title: 适用于 GCC 高级版和 DoD 环境的应用
titleSuffix: Microsoft Intune
description: 使用 Microsoft Intune 了解涉及 GCC 高级版和 DoD 环境的应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a6c430ab15c40166e8c3afbccd6fcc7c2c5976d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72507267"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>使用 Intune 在 GCC 高级版和 DoD 环境中部署应用 

租户管理员可使用 Microsoft Intune 将应用分发给他们的工作人员。 工作人员是公司员工，是应用的用户。 可以通过 Intune 在 GCC 高级版或 DoD 环境中部署多种类型的应用。 如果管理员需要上传和分发某个面向 GCC 高级版或 DoD 受众的 Windows 应用，且该应用是由第三方供应商按自定义配置创建的，或是从[适用于企业的 Microsoft Store](https://businessstore.microsoft.com/store) 中下载的脱机应用，管理员可以选择将其分发为[业务线应用](apps-add.md#app-types-in-microsoft-intune)。  

> [!NOTE]
> 对于商业环境，租户管理员可以将适用于企业的 Microsoft Store 与 Intune 进行同步，但此服务对 GCC 高级版和 DoD 环境不适用。 在这种情况下，管理员必须通过直接上传到 Intune 来部署应用。  

## <a name="add-line-of-business-apps-using-intune"></a>使用 Intune 添加业务线应用 

若要使用 Intune 添加适用于 GCC 高级版或 DoD 环境的业务线应用，可以按照 [Windows LOB 应用](lob-apps-windows.md)说明进行操作。 可以选择先通过适用于企业的 Microsoft Store 来部署公司门户。 如果选择使用公司门户，可以手动安装和部署公司门户。 有关详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>使用 Intune 从适用于企业的 Microsoft Store 分发脱机应用  

如果需要从适用于企业的 Microsoft Store 中[下载脱机许可应用](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app)，请按照以下步骤下载应用程序： 

1. 登录到[适用于企业的 Microsoft Store](https://businessstore.microsoft.com/)。
2. 选择“管理” > “设置”   。
3. 在“购物体验”下，将“显示脱机应用”设置为“开”    。

购买应用时，如果有脱机版本，可以选择将许可类型更改为脱机。 获取应用后，可以通过选择[适用于企业的 Microsoft Store](https://businessstore.microsoft.com/) 中的“管理” > “产品和服务”来管理该应用   。 此外，可以下载应用及其依赖项。 然后，可以使用 Intune 向用户部署此下载的应用（及其依赖项）。  

## <a name="syncing-intune-to-the-store-for-business"></a>将 Intune 同步到适用于企业的 Microsoft Store 

在商业（非政府）环境中，管理员可以将 Intune 同步到适用于企业的 Microsoft Store。 这是在政府环境中不可用的功能。 有关商业环境中的 Intune 和政府环境中的 Intune 的差异的详细信息，请参阅[针对美国政府的企业移动性 + 安全性服务描述](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description)。  

要将 Intune 同步到适用于企业的 Microsoft Store 帐户，请参阅[如何使用 Microsoft Intune 管理从适用于企业的 Microsoft Store 中购买的应用](windows-store-for-business.md)。  

## <a name="compliance"></a>合规性 

在评估这些服务的使用是否合适时，请查看应用的隐私与合规性声明，并将其与组织的合规性、安全性和隐私要求进行比较。   

## <a name="next-steps"></a>后续步骤

要了解有关如何部署和分配应用的详细信息，请参阅[使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

 
