---
title: "如何使用适用于 iOS 的 Intune 应用配置策略"
titlesuffix: Azure portal
description: "了解如何使用应用配置策略，为运行中的 iOS 应用提供配置数据。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bc42f3cafa83b5f7ba053d03dbd066b725bb1fee
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>如何使用适用于 iOS 的 Microsoft Intune 应用配置策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 中的应用配置策略，可提供用户在运行 iOS 应用时使用的设置。 例如，应用可能要求用户指定：

-   自定义端口号。

-   语言设置。

-   安全设置。

-   公司徽标之类的品牌设置。

如果用户输入的这些设置不正确，可能会加重支持人员的负担并降低新应用的采用率。

通过让你在运行应用之前将策略中的这些设置分配给用户，应用配置策略可消除此类问题。 随后这些设置会自动提供，用户无需执行任何操作。 应用必须编写为支持使用应用配置。 有关详细信息，请咨询应用供应商。

无需直接向用户和设备分配这些策略。 而是将策略与应用关联，然后分配应用。 只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

> [!TIP]
> 此策略类型目前仅适用于运行 iOS 8.0 及更高版本的设备。 它支持下列应用安装类型：
>
> -   **来自应用商店的托管 iOS 应用程序**
> -   **iOS 应用包**
>
> 有关应用安装类型的详细信息，请参阅[如何将应用添加到 Microsoft Intune](apps-add.md)。

## <a name="create-an-app-configuration-policy"></a>创建应用配置策略
1.  登录到 Azure 门户中。
2.  选择“更多服务” > “监视 + 管理” > “Intune”。
3.  在“Intune”边栏选项卡上，选择“移动应用”。
4.  在“移动应用”工作负荷中，选择“管理” > “应用配置策略”。
5.  在“策略列表”边栏选项卡中，选择“添加”。
6.  在“添加配置策略”边栏选项卡上，为应用配置策略提供“名称”和可选“描述”。
7.  对于“设备注册类型”，选择以下选项之一：
    - 向 Intune 注册 - 适用于由 Intune 托管的应用。
    - 不向 Intune 注册 - 适用于不由 Intune 托管或由其他解决方案托管的应用。
8.  对于“平台”，选择 **iOS**（仅适用于已注册 Intune 的设备）
9.  选择“关联应用”，然后在“关联应用”边栏选项卡上，选择要对其应用配置的托管应用。
10. 在“添加配置策略”边栏选项卡上，选择“配置设置”
11. 在“配置设置”边栏选项卡上，从以下来源选择想要指定构成配置文件的 XML 值：
    - 输入 XML 数据（仅适用于已注册 Intune 的设备）- 输入或粘贴 XML 属性列表，此列表包含所需的应用配置设置。 根据你所配置的应用，XML 属性列表的格式可能有所不同。 若需了解要使用确切格式的详细信息，请联系应用供应商。
Intune 会检查所输入的 XML 的格式是否有效。 它不会检查 XML 属性列表是否会与其关联的应用共同发挥作用。
若要了解有关 XML 属性列表的详细信息，请参阅 iOS 开发人员库中的[了解 XML 属性列表](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)。
    - 使用配置设计器（无论设备是否已注册 Intune）- 允许直接在门户中指定 XML 键值对。
11. 完成后，返回“添加配置策略”边栏选项卡，然后点击“创建”。

将创建该策略并在“策略列表”边栏选项卡上显示。



>[!Note]
>无论设备是否已注册 Intune，均可以使用 [Intune App SDK](https://docs.microsoft.com/intune/app-sdk-ios) 为将业务线应用由 Intune 应用保护策略和应用配置策略托管做准备。 例如，可以使用应用配置策略来配置 [Intune Managed Browser](app-configuration-managed-browser.md) 允许的和阻止的 URL。 一旦应用与这些策略兼容，则可使用策略配置它们。


当分配的应用在设备上运行时，将使用你在应用配置策略中配置的设置运行。
请参阅适用于你所配置的应用的文档，了解有关一个或多个应用配置策略冲突后将发生情况的信息。

>[!Tip]
>此外，可以使用图形 API 完成这些任务。 有关详细信息，请参阅[针对 Graph API 参考 MAM 的配置](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)。


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

## <a name="example-format-for-an-app-configuration-xml-file"></a>应用配置 XML 文件的示例格式

在创建应用配置文件时，你可以指定下面的一个或多个使用此格式的值：

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

## <a name="next-steps"></a>后续步骤

照常继续[分配](apps-deploy.md)和[监视](apps-monitor.md)应用。