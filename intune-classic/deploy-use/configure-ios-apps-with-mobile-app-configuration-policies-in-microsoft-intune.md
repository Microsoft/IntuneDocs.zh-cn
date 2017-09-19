---
title: "使用 iOS 移动应用配置策略"
description: "Intune 中的移动应用配置策略可提供用户在运行 iOS 应用时可能需要的设置。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7dd73ecbba6c10cbbec92bdf4e856bf15434aea9
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2017
---
# <a name="configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>使用 Microsoft Intune 中的移动应用配置策略配置 iOS 应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 中的移动应用配置策略可提供用户在运行应用时可能需要的设置。 例如，应用可能要求用户指定：

-   自定义端口号。

-   语言设置。

-   安全设置。

-   公司徽标之类的品牌设置。

如果用户输入的这些设置不正确，可能会加重支持人员的负担并降低新应用的采用率。

通过让你在运行应用之前将策略中的这些设置部署给用户，移动应用配置策略可消除此类问题。 随后这些设置会自动提供，用户无需执行任何操作。

无需直接向用户和设备部署这些策略， 而是将策略与应用关联，然后部署应用。 只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

> [!TIP]
> 此策略类型目前仅适用于运行 iOS 8.0 及更高版本的设备。 它支持下列应用安装类型：
>
> -   **来自应用商店的托管 iOS 应用程序**
> -   **iOS 应用包**
>
> 有关应用安装类型的详细信息，请参阅[使用 Microsoft Intune 部署应用](deploy-apps.md)。

## <a name="configure-a-mobile-app-configuration-policy"></a>配置移动应用配置策略

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)，选择“策略”&gt;“概述”&gt;“添加策略”。

2.  在策略列表中，展开“**iOS**”，选择“**移动应用配置**”，然后选择“**创建策略**”。

    > [!TIP]
    > 你只能配置此策略类型的自定义设置。 建议的设置不可用。

3.  在“**创建策略**”页的“**常规**”部分中，输入移动应用配置策略的名称和可选描述。

4.  在该页面的“**移动应用配置策略**”部分，在框中输入或粘贴包含你期望的应用配置设置的 XML 属性列表。 根据你所配置的应用，XML 属性列表的格式可能有所不同。 若需了解要使用确切格式的详细信息，请联系应用供应商。

    > [!TIP]
    > 若要了解有关 XML 属性列表的详细信息，请参阅 iOS 开发人员库中的[了解 XML 属性列表](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)。

5.  单击“**验证**”，确保所输入的 XML 的属性列表格式有效。

    > [!IMPORTANT]
    > 单击“验证”后，Intune 会检查所输入的 XML 的格式是否有效。 它不会检查 XML 属性列表是否会与其关联的应用共同发挥作用。

6.  完成后，单击 **“保存策略”**。

新策略显示在“配置策略”  节点中。

## <a name="information-about-the-xml-file-format"></a>有关 XML 文件格式的信息

Intune 在属性列表中支持以下数据类型：
    
- &lt;整数&gt;
- &lt;实数&gt;
- &lt;字符串&gt;
- &lt;数组&gt;
- &lt;dict&gt;
- &lt;true /&gt; 或 &lt;false /&gt;
     
有关数据类型的详细信息，请参阅 iOS 开发人员库中的 [关于属性列表](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) 。

此外，Intune 还支持属性列表中的以下令牌类型：
- \{\{userprincipalname\}\} -（示例：**John@contoso.com**）
- \{\{mail\}\} -（示例：**John@contoso.com**）
- \{\{partialupn\}\} -（示例：**John**）
- \{\{accountid\}\} -（示例：**fc0dc142-71d8-4b12-bbea-bae2a8514c81**）
- \{\{deviceid\}\} -（示例：**b9841cd9-9843-405f-be28-b2265c59ef97**）
- \{\{userid\}\} -（示例：**3ec2c00f-b125-4519-acf0-302ac3761822**）
- \{\{username\}\} -（示例：**John Doe**）
- iOS 设备的 \{\{serialnumber\}\} -（示例：**F4KN99ZUG5V2**
- iOS 设备的 \{\{serialnumberlast4digits\}\} -（示例：**G5V2**）
    
\{\{ 和 \}\} 字符仅供令牌类型使用，不得用于其他目的。

## <a name="associate-a-mobile-app-configuration-policy-with-an-app"></a>将移动应用配置策略与应用关联
创建移动应用配置策略后，必须将其与 iOS 应用（希望将配置策略设置应用到的应用）关联。

为此，请按照[在 Microsoft Intune 中为移动设备添加应用](add-apps-for-mobile-devices-in-microsoft-intune.md)和[使用 Microsoft Intune 部署应用](deploy-apps-in-microsoft-intune.md)中创建应用部署的步骤操作。 到达向导的“移动应用配置”页时，请从“应用配置策略”下拉列表选择要与应用关联的策略。

然后，如往常一样继续部署和监视应用部署。

当部署的应用在设备上运行时，将使用你在移动应用配置策略中配置的设置运行。

> [!TIP]
> 如果一个或多个移动应用配置策略发生冲突，则不会强制实施任一策略。 在 Intune 管理控制台“仪表板”中将报告冲突。

## <a name="example-format-for-a-mobile-app-configuration-xml-file"></a>移动应用配置 XML 文件的示例格式

在创建移动应用配置文件时，你可以指定下面的一个或多个使用此格式的值：

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```
