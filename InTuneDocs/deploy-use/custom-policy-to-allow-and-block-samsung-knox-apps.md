---
title: "KNOX 允许和阻止的应用 | Microsoft Docs"
description: "自定义配置文件以创建 KNOX 允许和阻止的应用的列表。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: be3cfc0120caf6e702139b829fc6ee1fa9bf9a1e



---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>使用自定义策略允许和阻止适用于 Samsung KNOX 标准版设备的应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用此主题中的过程创建 Microsoft Intune 自定义策略，该策略创建以下内容之一：

- 阻止在设备上运行的应用的列表。 阻止运行此列表中的应用，即使应用此策略时已安装这些应用也是如此。
- 允许设备用户从 Google Play 商店中安装的应用的列表。 仅可安装你列出的应用。 其他应用不能从应用商店安装。

仅运行 Samsung KNOX 标准版的设备可以使用这些设置。

## <a name="to-create-an-allowed-or-blocked-app-list"></a>若要创建允许或阻止的应用列表

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择“策略”&gt;“配置策略”&gt;“添加”。
2. 在“创建新策略”对话框中，展开“Android”，选择“自定义配置”，然后选择“创建策略”。
3. 提供策略的名称和可选描述，然后在“OMA-URI 设置”部分，选择“添加”。
4. 在“添加或编辑 OMA-URI 设置”对话框中，指定以下内容：有关阻止在设备上运行的应用列表：
    
    - **设置名称。** 输入 **PreventStartPackages**。
    - **设置描述。** 输入可选描述，如“阻止运行的应用列表”。
    -   **数据类型。** 在下拉列表中，选择“字符串”。
    -   **OMA-URI。** 输入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **值。** 输入你要允许的应用包名称的列表。 你可使用 **; : ,** 或 **|** 作为分隔符。 （示例：package1;package2;）

    有关允许用户从 Google Play 商店中安装的应用（同时排除所有其他应用）的列表：

    - **设置名称。** 输入 **AllowInstallPackages**。
    - **设置描述。** 输入可选描述，如“用户可从 Google Play 安装的应用的列表”。
    - **数据类型。** 在下拉列表中，选择“字符串”。
    - **OMA-URI。** 输入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **值。** 输入你要允许的应用包名称的列表。 你可使用 **; : ,** 或 **|** 作为分隔符。 （示例：package1;package2;）

4. 单击“确定”，然后单击“保存策略”。 

>[!TIP]
> 可通过浏览 Google Play 商店上的应用找到应用的包 ID。 包 ID 包含在应用页面的 URL 中。 例如，Microsoft Word 应用的包 ID 是 **com.microsoft.office.word**。

每个目标设备下次签入时，将应用此应用设置。


## <a name="deploy-the-policy"></a>部署策略

1.  在“策略”  工作区中，选择想要部署的策略，然后单击“管理部署” 。

2.  在“管理部署”对话框中，选择要向其部署策略的一个或多个组，然后单击“添加” &gt;“确定”。

 
如果你选择的是已部署的策略，则可以在策略列表的下半部分查看有关部署的详细信息。

### <a name="see-also"></a>另请参阅
[Microsoft Intune 中 Android 和 Samsung KNOX 策略设置](android-policy-settings-in-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


