---
title: "为受管理 iOS 设备添加应用配置策略 | Microsoft Docs"
titlesuffix: Azure portal
description: "了解如何使用应用配置策略，为运行中的 iOS 应用提供配置数据。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d293ff6001ef937c7da0055e6642aa5a1226bd2e
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2017
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>为受管理 iOS 设备添加应用配置策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 中的应用配置策略可提供用户在运行 iOS 应用时的设置。 无需直接向用户和设备分配这些策略。 而是将策略与应用关联，然后分配应用。 只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

> [!TIP]
> 此策略类型目前仅适用于运行 iOS 8.0 及更高版本的设备。 它支持下列应用安装类型：
>
> -   **来自应用商店的托管 iOS 应用程序**
> -   **iOS 应用包**
>
> 有关应用安装类型的详细信息，请参阅[如何将应用添加到 Microsoft Intune](apps-add.md)。

## <a name="create-an-app-configuration-policy"></a>创建应用配置策略

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 选择“移动应用”工作负荷。
4. 在“管理”组中，单击“应用配置策略”，然后单击“添加”。
5. 设置以下详细信息：
    - **名称**  
      在 Azure 门户中显示的配置文件名称。
    - **描述**  
      在 Azure 门户中显示的配置文件说明。
    - **设备注册类型**  
      选择“受管理设备”。
6. 对“平台”选择“iOS”。
7.  选择“关联应用”，然后在“关联应用”边栏选项卡上，选择要对其应用配置的托管应用。
8.  在“添加配置策略”边栏选项卡上，选择“配置设置”
9. 选择“配置设置格式”。 选择下列选项之一：
    - **[使用配置设计器](#Use-the-configuration-designer)**
    - **[输入 XML 数据](#enter-xml-data)**
10. 单击“确定”，然后单击“添加”。

## <a name="use-configuration-designer"></a>使用配置设计器

可对已注册或未注册 Intune 的设备上的应用使用配置设计器。 使用设计器可配置特定配置项和值。 还须指定每个值的数据类型。 在安装应用时，自动向应用提供设置。

### <a name="add-a-setting"></a>添加设置

1. 对于配置中的每个项和值，请设置以下内容： <ul><li>**配置项**<br>用于对特定设置配置进行唯一标识。</li><li>**值类型**<br>配置值的数据类型。 类型包括整数、实数、字符串或布尔值。</li><li>**配置值**<br>配置的值。</li></ul>
2. 单击“确定”以设置配置设置。

### <a name="delete-a-setting"></a>删除设置

1. 单击设置旁的省略号 (...)。
2. 选择“删除”。

\{\{ 和 \}\} 字符仅供令牌类型使用，不得用于其他目的。

## <a name="enter-xml-data"></a>输入 XML 数据

可键入或粘贴 XML 属性列表，此列表包含将设备注册到 Intune 所需的应用配置设置。 根据你所配置的应用，XML 属性列表的格式可能有所不同。 若需了解要使用确切格式的详细信息，请联系应用供应商。

Intune 会验证 XML 格式。 但是，Intune 不会检查 XML 属性列表是否会与目标应用共同发挥作用。
要详细了解 XML 属性列表，请参阅 [了解 XML 属性列表]

了解有关 XML 属性列表的详细信息：

  -  请参阅[使用 Microsoft Intune 中的移动应用配置策略配置 iOS 应用](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。
  -  请参阅 iOS 开发人员库中的[了解 XML 属性列表](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)。

### <a name="example-format-for-an-app-configuration-xml-file"></a>应用配置 XML 文件的示例格式

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
### <a name="supported-xml-plist-data-types"></a>支持的 XML 属性列表数据类型

Intune 在属性列表中支持以下数据类型：

- &lt;整数&gt;
- &lt;实数&gt;
- &lt;字符串&gt;
- &lt;数组&gt;
- &lt;dict&gt;
- &lt;true /&gt; 或 &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>属性列表中使用的令牌

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

## <a name="next-steps"></a>后续步骤

照常继续[分配](apps-deploy.md)和[监视](apps-monitor.md)应用。