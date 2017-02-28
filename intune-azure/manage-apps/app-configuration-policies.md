---
title: "如何使用 Intune 应用配置策略 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何使用应用配置策略，为运行中的 iOS 应用提供配置数据。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 1e1f03a81d28d73476b64cef7af3b93e4d003697
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-use-microsoft-intune-app-configuration-policies"></a>如何使用 Microsoft Intune 应用配置策略

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune 中的应用配置策略可提供用户在运行应用时可能需要的设置。 例如，应用可能要求用户指定：

-   自定义端口号。

-   语言设置。

-   安全设置。

-   公司徽标之类的品牌设置。

如果用户输入的这些设置不正确，可能会加重支持人员的负担并降低新应用的采用率。

通过让你在运行应用之前将策略中的这些设置分配给用户，应用配置策略可消除此类问题。 随后这些设置会自动提供，用户无需执行任何操作。

无需直接向用户和设备分配这些策略。 而是将策略与应用关联，然后部署应用。 只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

> [!TIP]
> 此策略类型目前仅适用于运行 iOS 8.0 及更高版本的设备。 它支持下列应用安装类型：
>
> -   **来自应用商店的托管 iOS 应用程序**
> -   **iOS 应用包**
>
> 有关应用安装类型的详细信息，请参阅[如何将应用添加到 Microsoft Intune](/intune-azure/manage-apps/add-apps)。

## <a name="create-an-app-configuration-policy"></a>创建应用配置策略

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
1.  在“管理应用”工作负荷中，选择“管理” > “应用配置策略”。

2.  在“策略列表”边栏选项卡中，选择“添加”。

3.  在“添加配置策略”边栏选项卡上，为应用配置策略提供名称和可选描述。
4.  选择“关联应用”，然后在“关联应用”边栏选项卡上，选择要对其应用配置的托管应用。
5.  在“添加配置策略”边栏选项卡上，选择“配置设置”，然后在“配置设置”边栏选项卡上，从以下来源选择想要指定构成配置描述文件的 XML 值：
    - **输入 XML 数据** - 输入或粘贴 XML 属性列表，此列表包含所需的应用配置设置。 根据你所配置的应用，XML 属性列表的格式可能有所不同。 若需了解要使用确切格式的详细信息，请联系应用供应商。
    Intune 会检查所输入的 XML 的格式是否有效。 它不会检查 XML 属性列表是否会与其关联的应用共同发挥作用。
    若要了解有关 XML 属性列表的详细信息，请参阅 iOS 开发人员库中的[了解 XML 属性列表](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)。
    - **使用配置设计器** - 允许直接在门户中指定 XML 键值对。
8. 完成后，返回“添加配置策略”边栏选项卡，然后点击“创建”。

将创建该策略并在“策略列表”边栏选项卡上显示。

然后，照常继续[分配](deploy-apps.md)和[监视](monitor-apps.md)应用。

当分配的应用在设备上运行时，将使用你在应用配置策略中配置的设置运行。

> [!TIP]
> 如果一个或多个应用配置策略发生冲突，则不会强制实施任一策略。

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

