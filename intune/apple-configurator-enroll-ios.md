---
title: iOS 设备注册 - Apple Configurator 设置助理
titleSuffix: Microsoft Intune
description: 了解如何通过 Apple Configurator 使用设置助理来注册公司拥有的 iOS 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d91e92b561bbf7b574e0d8271374c0d8c6bd4a64
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230391"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>通过 Apple Configurator 设置 iOS 设备注册

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 支持注册 iOS 设备，方法是使用在 Mac 计算机上运行的 [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344)。 使用 Apple Configurator 进行注册时，需要通过 USB 将每个 iOS 设备连接到 Mac 计算机来设置公司注册过程。 你可采用两种方式使用 Apple Configurator 将设备注册到 Intune：
- **设置助理注册** – 擦除设备，使其准备好在设置助理期间进行注册。
- **直接注册** - 不擦除设备，并通过 iOS 设置注册设备。 此方法适仅支持“无用户关联”的设备。

Apple Configurator 注册方法不能与[设备注册管理器](device-enrollment-manager-enroll.md)同时使用。

## <a name="prerequisites"></a>必备条件

- 具有 iOS 设备的物理访问权限
- [设置 MDM 机构](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 设备序列号（仅设置助理注册）
- USB 连接电缆
- 运行 [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344) 的 macOS 计算机

## <a name="create-an-apple-configurator-profile-for-devices"></a>为设备创建 Apple Configurator 配置文件

设备注册配置文件定义在注册期间应用的设置。 这些设置只应用一次。 按照以下步骤创建注册配置文件，使用 Apple Configurator 注册 iOS 设备。

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “Apple Configurator” > “配置文件” > “创建”。

    ![创建 Apple Configurator 配置文件](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. 在“创建注册配置文件”下，输入配置文件的“名称”和“描述”，以便于管理。 用户看不到这些详细信息。 可使用此“名称”字段在 Azure Active Directory 中创建动态组。 使用配置文件名称定义 enrollmentProfileName 参数，以向设备分配此注册配置文件。 详细了解 Azure Active Directory 动态组。

    ![创建配置文件屏幕的屏幕截图，选中了“通过用户关联注册”](./media/apple-configurator-profile-create.png)

3. 对于“用户关联”，选择具有此配置文件的设备是否必须通过已分配的用户进行注册。

    - 通过用户关联进行注册 - 为属于用户且想要使用公司门户获取服务（如安装应用）的设备选择此选项。 设备必须通过设置助理与某个用户关联，然后才可访问公司数据和电子邮件。 仅设置助理注册支持。 用户关联需要 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [了解详细信息](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

    - 不通过用户关联进行注册 - 为不属于单个用户的设备选择此选项。 为无需访问本地用户数据即可执行任务的设备使用此选项。 需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）无法运行。 直接注册需要此设置此选项。

4. 如果选择“通过用户关联进行注册”，则可选择让用户不使用 Apple 设置助理而使用公司门户进行身份验证。

    > [!NOTE]
    > 如果想要执行以下任一操作，请将“不使用 Apple 设置助理而使用公司门户进行身份验证”设置为“是”。
    >    - 使用多重身份验证
    >    - 提示用户在首次登录时需要更改密码
    >    - 提示用户在注册期间重置过期的密码
    >
    > 使用 Apple 设置助理进行身份验证时不支持这些功能。


6. 选择“创建”保存该配置文件。

## <a name="setup-assistant-enrollment"></a>设置助理注册

### <a name="add-apple-configurator-serial-numbers"></a>添加 Apple Configurator 序列号

1. 创建没有标题的两列逗号分隔值 (.csv) 列表。 在左列添加序列号，在右列添加详细信息。 目前，该列表的最大长度为 5,000 行。 在文本编辑器中，该 .csv 列表如下所示：

    F7TLWCLBX196,设备详细信息</br>
    DLXQPCWVGHMJ，设备详细信息

   [了解如何查找 iOS 设备序列号](https://support.apple.com/HT204073)。
2. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “Apple Configurator” > “设备” > “添加”。

5. 选择一个注册配置文件，将其应用于导入的序列号。 如果想要让新的序列号详细信息覆盖现有的所有详细信息，请选择“覆盖现有标识符的详细信息”。
6. 在“导入设备”下，浏览到序列号的 .csv 文件，然后选择“添加”。

### <a name="reassign-a-profile-to-device-serial-numbers"></a>将配置文件重新分配给设备序列号

为 Apple Configurator 注册导入 iOS 序列号时，可分配注册配置文件。 此外，还可从 Azure 门户中的以下两个位置分配配置文件：
- Apple Configurator 设备
- AC 配置文件

#### <a name="assign-from-apple-configurator-devices"></a>从 Apple Configurator 设备分配
1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “Apple Configurator” > “设备”> 选择序列号 >“分配配置文件”。
2. 在“分配配置文件”下，选择要分配的新配置文件，然后选择“分配”。

#### <a name="assign-from-profiles"></a>从配置文件分配
1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “Apple Configurator” > “配置文件”> 选择配置文件。
2. 在配置文件中，选择“已分配设备”，然后选择“分配”。
3. 通过筛选找到要分配给配置文件的设备序列号，选择设备，然后选择“分配”。

### <a name="export-the-profile"></a>导出配置文件
创建配置文件并分配序列号后，必须从 Intune 中以 URL 的形式导出配置文件。 然后将其导入 Mac 上的 Apple Configurator 用于部署到设备。

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “Apple Configurator” > “配置文件”> 选择要导出的配置文件。
2. 在配置文件上，选择“导出配置文件”。
3. 复制“配置文件 URL”。 然后可在 Apple Configurator 中添加它，以定义 iOS 设备使用的 Intune 配置文件。

   接下列按照以下过程将此配置文件导入 Apple Configurator，定义 iOS 设备使用的 Intune 配置文件。

### <a name="enroll-devices-with-setup-assistant"></a>使用设置助理注册设备

1. 在 Mac 计算机上，打开“Apple Configurator 2”。 在菜单栏中，选择“Apple Configurator 2”，然后选择“首选项”。
    > [!WARNING]
    > 注册过程中，设备会重置为工厂配置。 最佳做法是重置设备，然后再启动。 连接设备时，设备应处于 **Hello** 屏幕界面。

2. 在“首选项”窗格中，选择“服务器”，然后选择加号 (+) 启动 MDM 服务器向导。 选择“下一步”。
3. 在使用 Microsoft Intune 对 iOS 设备注册设置助理的情况下，为 MDM 服务器输入主机名称或 URL以及注册 URL。 对于注册 URL，请输入从 Intune 中导出的注册配置文件 URL。 选择“下一步”。  
    可安全忽略警告“未验证服务器 URL”。 若要继续，请选择“下一步”，直到完成该向导。
4.  用 USB 适配器将 iOS 移动设备连接到 Mac 计算机。
5.  选择要管理的 iOS 设备，然后选择“准备”。 在“准备 iOS 设备”窗格上，选择“手动”，然后选择“下一步”。
6. 在“在 MDM 服务器中注册”窗格上，选择你创建的服务器名称，然后选择“下一步”。
7. 在“监督设备”窗格上，选择监督级别，然后选择“下一步”。
8. 在“创建组织”窗格上，选择“组织”或创建新的组织，然后选择“下一步”。
9. 在“配置 iOS 设置助理”上，选择要提供给用户的步骤，然后选择“准备”。 如果出现系统提示，请进行身份验证以更新信任设置。  
10. iOS 设备完成准备后，断开 USB 电缆的连接。  

### <a name="distribute-devices"></a>分配设备
设备现已准备好进行企业注册。 关闭设备，并将它们分发给用户。 用户打开其设备时，设置助理启动。

用户收到设备后，必须完成设置助理。 配置了用户关联的设备可以安装和运行公司门户应用，以下载应用和管理设备。

## <a name="direct-enrollment"></a>直接注册
直接使用 Apple Configurator 注册 iOS 设备时，无需获取设备序列号即可注册设备。 在注册过程中，你还可以在 Intune 捕获设备名称前对设备命名以进行标识。 直接注册的设备不支持公司门户应用。 此方法不擦除设备。

无法安装需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）。

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>将配置文件作为 .mobileconfig 导出到 iOS 设备

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “Apple Configurator” > “配置文件”> 选择要导出的配置文件 >“导出配置文件”。
2. 在“直接许可登记表”下，选择“下载配置文件”并保存此文件。 注册配置文件的有效期仅为两周，必须在此时间重新创建。
3. 将文件传输到运行 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 的 Mac 计算机，作为管理配置文件直接推送到 iOS 设备。
4. 通过以下步骤使用 Apple Configurator 准备设备：
    1. 在 Mac 计算机上，打开 Apple Configurator 2.0。
    2. 使用 USB 线将 iOS 设备连接到 Mac 计算机。 关闭“照片”、iTunes 和其他在检测设备时为设备打开的应用。
    3. 在 Apple Configurator 中，选择已连接的 iOS 设备，然后选择“添加”按钮。 可以添加到设备的选项将显示在下拉列表中。 选择“配置文件”。

        ![采集设置助理注册的导出配置文件的屏幕快照，在其中突出显示配置文件 URL](./media/ios-apple-configurator-add-profile.png)

    4. 使用文件选取器选择从 Intune 导出的 .mobileconfig 文件，然后选择“添加”。 配置文件将添加到设备。 如果设备是“非监督”状态，安装将需要在设备上验收。
5. 使用以下步骤在 iOS 设备上安装配置文件。 设备必须已经完成设置助理且准备好使用。 如果注册需要应用部署，设备应设置一个 Apple ID，因为应用部署需要有一个 Apple ID 登录到应用商店。
    1. 解锁 iOS 设备。
    2. 在“管理配置文件”的“安装配置文件”对话框中，选择“安装”。
    3. 如有必要，提供“设备密码”或“Apple ID”。
    4. 接受“警告”，并选择“安装”。
    5. 接受“远程警告”，并选择“信任”。
    6. “已安装配置文件”框确认配置文件“已安装”后，选择“完成”。

6. 在 iOS 设备上，打开“设置”并转到“常规” > “设备管理”  > “管理配置文件”。 确认配置文件安装已列出，并检查 iOS 策略限制和已安装的应用。 策略限制和应用可能需要 10 分钟才会出现在设备上。

7. 分配设备。 iOS 设备现已在 Intune 中注册并已托管。





