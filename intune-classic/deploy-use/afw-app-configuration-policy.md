---
title: "Android for Work 应用配置策略"
description: "Intune 中的移动应用配置策略可提供用户在运行 Android for Work 应用时可能需要的设置。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6ab8b2a53d67ada01ac95f380b9339cb0bb70396
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2017
---
# <a name="configure-android-for-work-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>在 Microsoft Intune 中使用移动应用配置策略配置 Android for Work 应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 中的移动应用配置策略可提供用户在运行应用时可能需要的设置。 例如，应用可能要求用户指定：

-   自定义端口号
-   语言设置
-   公司徽标之类的品牌设置

如果用户输入的设置不正确，可能会加重支持人员的负担并降低新应用的采用率。

移动应用配置策略可让你在用户运行应用前将这些设置部署到设备。 会自动提供这些设置，用户无需执行任何操作。

若要利用应用配置策略，应用开发人员必须在创建企业应用配置时公开了配置。 例如，Google Chrome 公开了使你可以设置默认书签、允许和拒绝的站点等内容的设置。 请与应用的开发人员联系，以了解是否支持这些设置以及如何在策略中指定它们。

对其部署应用配置策略的用户应与对其部署要配置的应用的用户相同。 运行应用时使用应用设置。

## <a name="configure-a-mobile-app-configuration-policy"></a>配置移动应用配置策略

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)，选择“策略”&gt;“概述”&gt;“添加策略”。

2.  在策略列表中，展开“Android for Work”，选择“移动应用配置策略(Android for Work)”，然后选择“创建策略”。

    > [!TIP]
    > 你只能配置此策略类型的自定义设置。 建议的设置不可用。

3.  在“创建策略”页的“常规”部分中，输入移动应用配置策略的名称和可选描述。

4. 在该页的“移动应用配置策略”部分中，指定以下信息：
    - **此配置适用的应用程序的包 ID** - 包 ID 可以在 Google Play 页上应用 URL 的“id=”中找到。 例如，Microsoft Excel 应用的包 ID 是 **com.microsoft.office.excel**。
    - 在文本框中，为要配置的应用设置输入数据。 可从应用的供应商处获取这些设置。 并非所有应用都支持这些设置。
5.  单击“验证”，以确保所输入的数据的属性列表格式有效。

    > [!IMPORTANT]
    > 单击“验证”后，Intune 会检查所输入的配置数据的格式是否有效。 它不会检查这些数据是否会与其关联的应用共同发挥作用。

6.  完成后，单击**“保存策略”**。

新策略显示在“配置策略”节点中。


## <a name="deploy-the-app-configuration-policy"></a>部署应用配置策略
创建移动应用配置策略之后，必须将其部署给向其部署这些设置所适用于的应用的相同用户。

有关有关如何部署策略的信息，请参阅[部署配置策略](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)

有关如何将应用部署到 Android for Work 设备的信息，请参阅[如何使用 Intune 部署 Android for Work 应用](android-for-work-apps.md)。

当部署的应用在设备上运行时，将使用你在移动应用配置策略中配置的设置运行。

> [!TIP]
> 对于每个应用，只能将一个应用配置策略部署给用户。
