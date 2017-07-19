---
title: "注册 iOS 设备- Apple Configurator-设置助理"
titleSuffix: Intune on Azure
description: "了解如何通过 Apple Configurator 使用“设置助理”来注册公司拥有的 iOS 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1d74fbcebfe89bbafc545d11dd6316cb602db8ee
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>使用 Apple Configurator 注册 iOS 设备

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 支持注册企业所有的 iOS 设备，方法是使用在 Mac 计算机上运行的 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)。 使用 Apple Configurator 进行注册时，需要通过 USB 将每个 iOS 设备连接到 Mac 计算机来设置公司注册过程。 你可采用两种方式使用 Apple Configurator 将设备注册到 Intune：
- **设置助理注册** - 将设备恢复出厂设置，准备好运行“设置助理”，从而为设备的新用户安装公司策略。 多数方案均要求应用到 iOS 设备的策略包括用户关联性，以便启用 Intune 公司门户应用。
- **直接注册** - 不将设备恢复出厂设置，而使用预定义策略注册设备。 此方法适用于“无用户关联”的设备。

>[!NOTE]
>此注册方法不能与[设备注册管理器](device-enrollment-manager-enroll.md)方法共同使用。

[选择在 Intune 中注册 iOS 设备的方式](enrollment-method-choose-ios.md)中介绍了注册 iOS 设备的其他方法。

## <a name="prerequisites"></a>先决条件

在设置 iOS 设备注册前，完成以下先决条件：

- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 具有 iOS 设备的物理访问权限
- 设备序列号（请参阅[如何获取 iOS 序列号](https://support.apple.com//HT204308)）
- USB 连接电缆
- 安装了 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 的 Mac PC
- [添加 Apple Configurator 序列号](apple-configurator-serial-numbers-add.md)

## <a name="setup-assistant-enrollment"></a>设置助理注册

### <a name="create-an-apple-configurator-profile-for-devices"></a>为设备创建 Apple Configurator 配置文件

设备注册配置文件定义应用于设备组的设置。 以下步骤说明如何使用 Apple Configurator 创建已注册 iOS 设备的设备注册配置文件。

1. 在 Intune 门户中，选择“设备注册”，然后选择“Apple 注册”。
2. 在“管理 Apple Configurator 注册设置”下，选择“AC 配置文件”。
3. 在“Apple Configurator 注册配置文件”边栏选项卡上，选择“创建”。
4. 在“创建注册配置文件”边栏选项卡上，输入配置文件的名称和说明。
5. 对于“用户关联”，请选择包含此配置文件的设备通过或不通过用户关联进行注册。

   - **通过用户关联注册** - 必须在初始设置过程中将设备与某个用户相关联，然后才能允许此设备访问公司数据和电子邮件。 应对属于用户且需要使用公司门户获取服务（如安装应用）的受管理设备设置用户关联。
   - **不通过用户关联注册** - 该设备不与用户关联。 将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）无法运行。

6. 选择“创建”保存该配置文件。

### <a name="add-apple-configurator-serial-numbers"></a>添加 Apple Configurator 序列号

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

若要[使用 Apple Configurator 和设置助理注册公司拥有的 iOS 设备](apple-configurator-setup-assistant-enroll-ios.md)，请使用以下步骤将序列号添加到 Intune。 可以一次添加一个序列号，也可以上传序列号的逗号分隔值 (CSV) 文件。 添加序列号后，即可向其分配配置文件。 配置文件包含要应用于设备的特定管理设置。

[选择在 Intune 中注册 iOS 设备的方式](enrollment-method-choose-ios.md)中介绍了注册 iOS 设备的其他方法。

**将 Apple Configurator 序列号添加到 Intune**

1. 创建没有标题的两列逗号分隔值 (.csv) 列表。 在左列添加 IMEI 标识符，在右列添加详细信息。 目前，该列表的最大长度为 500 行。 在文本编辑器中，该 .csv 列表可能如下所示：

    F7TLWCLBX196,设备详细信息</br>
    DLXQPCWVGHMJ，设备详细信息

2. 在 Azure 门户中，选择“注册设备”，然后选择“Apple 注册”。
3. 在“管理 Apple Configurator 注册设置”下，选择“Apple Configurator 序列号”。
4. 在“Apple Configurator 序列号”边栏选项卡上，选择“添加”。
5. 在“添加序列号”边栏选项卡上，选择要应用于导入的序列号的配置文件。 若要导入包含新详细信息（将覆盖现有信息）的文件，请选择“覆盖现有标识符详细信息”以将现有详细信息替换为新的详细信息。
6. 导航到序列号的 .csv 文件，然后选择“添加”。

### <a name="assign-a-profile-to-specific-serial-numbers"></a>将配置文件分配给特定序列号

通过 Intune 可以从 Azure 门户中两个不同位置分配配置文件。 可以通过 Apple Configurator 配置文件进行分配或者可以通过设备进行分配。

#### <a name="assign-by-devices"></a>通过设备进行分配
1. 在 Intune 门户中，选择“设备注册”，然后选择“Apple 注册”。
3. 在“Apple Configurator 设备”边栏选项卡上，选择要向其分配配置文件的序列号，然后选择“分配配置文件”。
4. 在“分配配置文件”边栏选项卡上，选择要分配的配置文件，然后选择“分配”。

#### <a name="assign-by-profiles"></a>通过配置文件进行分配
1. 在 Intune 门户中，选择“设备注册”，然后选择“Apple 注册”。
2. 选择“AC 配置文件”，然后选择要向其分配序列号的配置文件。
3. 在为配置文件命名的的边栏选项卡中，选择“序列号” > “分配”。
4. 选择要分配给配置文件的序列号，然后选择“分配”按钮。

### <a name="export-the-profile-to-ios-devices"></a>将配置文件导出到 iOS 设备
创建配置文件并分配序列号后，必须从 Intune 中将该配置文件导出为如下所述格式的 URL 或文件。 然后手动将其导入到 Mac 上的 Apple Configurator 程序，随后 Apple Configurator 程序将其部署到设备。

1. 在 Intune 门户中，选择“Apple Configurator 注册配置文件”边栏选项卡，选择要导出的配置文件。
2. 在配置文件的边栏选项卡中，选择“导出配置文件”。
3. 将配置文件 URL 复制到附加了 iOS 设备的 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)。 稍后你将在 Apple Configurator 中将其上传，以定义 iOS 设备使用的 Intune 配置文件。

  你可以按照以下过程使用 Apple Configurator 将此配置文件 URL 上载到 Apple 服务，以定义 iOS 设备使用的 Intune 配置文件。
4. 使用 Apple Configurator 将此配置文件 URL 上传到 Apple 服务，以定义 iOS 设备使用的 Intune 配置文件。
 1.  在 Mac 计算机上，打开“Apple Configurator 2”。 在菜单栏中，选择“Apple Configurator 2”，然后选择“首选项”。
  > [!WARNING]
  > 注册过程中，设备将重置为工厂配置。 最佳做法是重置设备，然后再启动。 连接设备时，设备应处于 **Hello** 屏幕界面。
  2. 在“首选项”窗格中，选择“服务器”，然后选择加号 (+) 启动 MDM 服务器向导。 选择“下一步”。
  3. 在使用 Microsoft Intune 对 iOS 设备注册设置助理的情况下，为 MDM 服务器输入主机名称或 URL以及注册 URL。 对于注册 URL，请输入从 Intune 中导出的注册配置文件 URL。 选择**下一步**。  

    可安全忽略警告“未验证服务器 URL”。 若要继续，请选择“下一步”，直到完成该向导。
  4.  用 USB 适配器将 iOS 移动设备连接到 Mac 计算机。
  > [!WARNING]
  > 注册过程中，设备将重置为工厂配置。 最佳做法是重置设备，然后再启动。 启动设置助理时，设备应处于 **Hello** 屏幕界面。
  5.  选择“准备”。 在“准备 iOS 设备”窗格上，选择“手动”，然后选择“下一步”。
  6. 在“在 MDM 服务器中注册”窗格上，选择你创建的服务器名称，然后选择“下一步”。
  7. 在“监督设备”窗格上，选择监督级别，然后选择“下一步”。
  8. 在“创建组织”窗格上，选择“组织”或创建新的组织，然后选择“下一步”。
  9. 在“配置 iOS 设置助理”上，选择要提供给用户的步骤，然后选择“准备”。 如果出现系统提示，请进行身份验证以更新信任设置。  
  10. iOS 设备完成准备后，断开 USB 电缆的连接。  
6.  **分配设备**。
    设备现已准备好进行企业注册。 关闭设备，并将它们分发给用户。 用户打开其设备时，将启动设置助理。

## <a name="direct-enrollment"></a>直接注册
直接使用 Apple Configurator 注册 iOS 设备时，无需获取设备序列号即可注册设备。 在注册过程中，你还可以在 Intune 捕获设备名称前对设备命名以进行标识。 直接注册的设备不支持公司门户应用。 本指南假定你在 Mac 计算机上使用 Apple Configurator 2.0。

1. 在 Intune 门户中，选择“设备注册”、“Apple 注册”，然后选择“AC 配置文件”。
2. 在“Apple Configurator 注册配置文件”边栏选项卡上，选择“创建”。
3. 在“创建注册配置文件”边栏选项卡上，输入配置文件的名称和说明。
4. 对于“用户关联”，选择“无用户关联注册”，确保该设备不与用户相关联。 将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）无法运行。
5. 选择“创建”保存该配置文件。

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>将配置文件作为 .mobileconfig 导出到 iOS 设备

1. 在“导出配置文件”边栏选项卡上，将注册配置文件下载到 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)，作为管理配置文件直接推送到已连接的 iOS 设备。 此方法不会将设备恢复至出厂设置。
2. 通过以下步骤使用 Apple Configurator 准备设备。
  1. 在 Mac 计算机上，打开 Apple Configurator 2.0。
  2. 使用 USB 线将 iOS 设备连接到 Mac 计算机。 关闭“照片”、iTunes 和其他在检测设备时为设备打开的应用。
  3. 在 Apple Configurator 中，选择已连接的 iOS 设备，然后选择“添加”按钮。 可以添加到设备的选项将显示在下拉列表中。 选择“配置文件”。
  4. 使用文件选取器选择从 Intune 导出的 .mobileconfig 文件，然后选择“添加”。 配置文件将添加到设备。 如果设备是“非监督”状态，安装将需要在设备上验收。
3. 使用以下步骤在 iOS 设备上安装配置文件。 设备必须已经完成设置助理且准备好使用。 如果注册需要应用部署，设备应设置一个 Apple ID，因为应用部署将需要你有一个 Apple ID 登录到应用商店。
   1. 解锁 iOS 设备。
   2. 在“管理配置文件”的“安装配置文件”对话框中，选择“安装”。
   3. 如果需要的话，提供“设备密码”或“Apple ID”。
   4. 接受“警告”，并选择“安装”。
   5. 接受“远程警告”，并选择“信任”。
   6. “已安装配置文件”框确认配置文件“已安装”后，选择“完成”。

    4. 在 iOS 设备上，打开“设置”并转到“常规” > “设备管理”  > “管理配置文件”。 确认配置文件安装已列出，并检查 iOS 策略限制和已安装的应用。 策略限制和应用可能需要 10 分钟才会出现在设备上。

    5. 分配设备。 iOS 设备现已向 Intune 注册并已托管。


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>用户如何在其设备上安装和使用公司门户

配置了用户关联的设备可以安装和运行公司门户应用，以下载应用和管理设备。 用户收到设备后，必须完成如下所述的其他步骤，才能完成设置助理并安装公司门户应用。
