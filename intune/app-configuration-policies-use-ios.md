---
title: "为受管理 iOS 设备添加应用配置策略"
titlesuffix: Microsoft Intune
description: "了解如何使用应用配置策略，为运行中的 iOS 应用提供配置数据。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee17ceae0af131f683341f2346f92ad5ef03ed16
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>为受管理 iOS 设备添加应用配置策略

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 中的应用配置策略可提供用户在运行 iOS 应用时的设置。 无需直接向用户和设备分配这些策略。 而是将策略与应用关联，然后分配应用。 只要应用检测到策略设置（通常在其首次运行时），即会使用它们。

可通过将包括和排除分配相结合来向一组用户和设备分配应用程序配置策略。 添加应用配置策略后，即可设置应用分配策略的配置。 设置策略分配时，可选择包括和排除应用该策略的用户组。 选择包括一个或多个组时，可以选择要包括的特定组或选择内置组。 内置组包括“所有用户”、“所有设备”和“所有用户 + 所有设备”。 

>[!NOTE]
>为方便起见，Intune 在具有内置优化的控制台中提供了预先创建的“所有用户”和“所有设备”组。 强烈建议针对所有用户和所有设备使用这些组，而不要使用你自己创建的任何“所有用户”或“所有设备”组。

为应用程序配置策略选择了包括的组之后，也可以选择要排除的特定组。

> [!TIP]
> 此策略类型目前仅适用于运行 iOS 8.0 及更高版本的设备。 它支持下列应用安装类型：
>
> -   **来自应用商店的托管 iOS 应用程序**
> -   **iOS 应用包**
>
> 有关应用安装类型的详细信息，请参阅[如何将应用添加到 Microsoft Intune](apps-add.md)。

## <a name="create-an-app-configuration-policy"></a>创建应用配置策略

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 选择“移动应用”工作负荷。
4. 在“管理”组中，选择“应用配置策略”，然后选择“添加”。
5. 设置以下详细信息：
    - **名称**<br>
      在 Azure 门户中显示的配置文件名。
    - **描述**<br>
      在 Azure 门户中显示的配置文件说明。
    - **设备注册类型**<br>
      选择“受管理设备”。
6. 对“平台”选择“iOS”。
7.  选择“关联应用”。 然后在“关联应用”窗格中，选择要对其应用配置的托管应用，并选择“确定”。
8.  在“添加配置策略”窗格中，选择“配置设置”。
9. 选择“配置设置格式”。 选择以下选项之一：
    - **[使用配置设计器](#use-configuration-designer)**
    - **[输入 XML 数据](#enter-xml-data)**
10. 添加完 XML 信息后，选择“确定”，然后选择“添加”以添加配置策略。 随即显示配置策略的概述窗格。
11. 选择“分配”，显示包括和排除选项。 

    ![策略分配“包括”选项卡的屏幕截屏](./media/app-config-policy01.png)
12. 在“包括”边栏选项卡上选择“所有用户”。

    ![策略分配“所有用户”下拉列表选项的屏幕截图](./media/app-config-policy02.png)
13. 选择“排除”选项卡。 
14. 单击“选择要排除的组”以显示相关窗格。

    ![策略分配“选择要排除的组”边栏选项卡的屏幕截图](./media/app-config-policy03.png)
15. 选择想要排除的组，然后单击“选择”。

    >[!NOTE]
    >添加组时，如果给定的分配类型中已包括任何其他组，则在其他包括分配类型中，会预先选定该组且无法更改。 因此，已被使用的组无法用作排除组。
16. 单击 **“保存”**。

## <a name="use-configuration-designer"></a>使用配置设计器

可对已注册或未注册 Intune 的设备上的应用使用配置设计器。 使用设计器可配置特定配置键和值。 还须指定每个值的数据类型。 在安装应用时，将自动向应用提供设置。

### <a name="add-a-setting"></a>添加设置

1. 对于配置中的每个项和值，请设置以下内容：
   - **配置项**<br>
     对特定设置配置进行唯一标识的键。
   - **值类型**<br>
     配置值的数据类型。 类型包括整数、实数、字符串或布尔值。
   - **配置值**<br>
     配置的值。
2. 选择“确定”以设置配置设置。

### <a name="delete-a-setting"></a>删除设置

1. 选择设置旁边的省略号 (...)。
2. 选择“删除”。

\{\{ 和 \}\} 字符仅供令牌类型使用，不得用于其他目的。

## <a name="enter-xml-data"></a>输入 XML 数据

可键入或粘贴 XML 属性列表，此列表包含将设备注册到 Intune 所需的应用配置设置。 根据你所配置的应用，XML 属性列表的格式可能有所不同。 若需了解要使用的确切格式的详细信息，请联系应用供应商。

Intune 会验证 XML 格式。 但是，Intune 不会检查 XML 属性列表 (PList) 是否适用于目标应用。

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
- \{\{userprincipalname\}\} - 例如 John@contoso.com
- \{\{mail\}\} - 例如 John@contoso.com
- \{\{partialupn\}\} - 例如 John
- \{\{accountid\}\} - 例如 fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{deviceid\}\} - 例如 b9841cd9-9843-405f-be28-b2265c59ef97
- \{\{userid\}\} - 例如 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\} - 例如 John Doe
- \{\{serialnumber\}\} - 例如 F4KN99ZUG5V2（用于 iOS 设备）
- \{\{serialnumberlast4digits\}\} - 例如 G5V2（用于 iOS 设备）

## <a name="next-steps"></a>后续步骤

照常继续[分配](apps-deploy.md)和[监视](apps-monitor.md)应用。