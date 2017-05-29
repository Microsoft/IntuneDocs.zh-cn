---
title: "注册 iOS 设备- Apple Configurator-设置助理"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何通过 Apple Configurator 使用设置助理来注册公司拥有的 iOS 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e6b0bc51515a2b72c7574a7ca7e29c094f3bdbdb
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-setup-assistant"></a>使用 Apple Configurator 和设置助理注册 iOS 设备

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Intune 支持注册企业所有的 iOS 设备，方法是使用在 Mac 计算机上运行的 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)。 此过程可恢复设备的出厂设置，并将其准备好以运行设置助理，从而为设备的新用户安装公司策略。

>[!NOTE]
>此注册方法不能与[设备注册管理器](device-enrollment-manager-enroll.md)方法共同使用。

可使用 Apple Configurator 将 iOS 设备恢复到出厂设置并将其准备好，方便设备的新用户进行设置。 此方法要求通过 USB 将 iOS 设备连接到 Mac 计算机以设置企业注册，并且假定使用的是 Apple Configurator 2.0。 多数方案均要求应用到 iOS 设备的策略包括用户关联性，以便启用 Intune 公司门户应用。

[选择在 Intune 中注册 iOS 设备的方式](enrollment-method-choose-ios.md)中介绍了注册 iOS 设备的其他方法。

## <a name="prerequisites"></a>先决条件

在设置 iOS 设备注册前，完成以下先决条件：

- [获取 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 确保具有对 iOS 设备的物理访问权限
- 获取设备序列号（请参阅[如何获取 iOS 序列号](https://support.apple.com//HT204308)）
- 准备好 USB 连接电缆
- 确保 Mac 电脑已安装 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)
- [添加 Apple Configurator 序列号](apple-configurator-serial-numbers-add.md)


## <a name="create-an-apple-configurator-profile-for-devices"></a>为设备创建 Apple Configurator 配置文件

设备注册配置文件定义应用于设备组的设置。 以下步骤说明如何使用 Apple Configurator 创建已注册 iOS 设备的设备注册配置文件。

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在“Intune”边栏选项卡上，选择“注册设备”，然后选择“Apple 注册”。

3. 在“管理 Apple Configurator 注册设置”下，选择“AC 配置文件”。

4. 在“Apple Configurator 注册配置文件”边栏选项卡上，选择“创建”。

5. 在“创建注册配置文件”边栏选项卡上，输入配置文件的名称和说明。

6. 对于“用户关联”，请选择包含此配置文件的设备通过或不通过用户关联进行注册。

   - **通过用户关联注册** - 必须在初始设置过程中将设备与某个用户相关联，然后才能允许此设备访问公司数据和电子邮件。 应对属于用户且需要使用公司门户获取服务（如安装应用）的托管设备设置用户关联。

   - **不通过用户关联注册** - 该设备不与用户关联。 将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）无法运行。

7. 选择“创建”保存该配置文件。

## <a name="assign-serial-numbers-to-an-apple-configurator-profile"></a>将序列号分配给 Apple Configurator 配置文件

创建 Apple Configurator 配置文件后，可以将设备序列号分配给配置文件。 必须先按照[添加 Apple Configurator 序列号](apple-configurator-serial-numbers-add.md)中的步骤将其添加到 Intune，才能分配序列号。

### <a name="assign-serial-numbers-to-apple-configurator-profiles"></a>将序列号分配给 Apple Configurator 配置文件

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在“Apple Configurator 注册配置文件”边栏选项卡中，选择要为其分配序列号的配置文件。

3. 在为配置文件命名的的边栏选项卡中，选择“序列号” > “分配”。

4. 选择要分配给配置文件的序列号，然后选择“分配”按钮。

## <a name="export-the-profile-to-ios-devices"></a>将配置文件导出到 iOS 设备

创建配置文件并分配序列号后，必须从 Intune 中将该配置文件导出为如下所述格式的 URL 或文件。 然后手动将其导入到 Mac 上的 Apple Configurator 程序，随后 Apple Configurator 程序将其部署到设备。

### <a name="export-a-profile-using-setup-assistant-enrollment"></a>使用设置助理注册导出配置文件

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在“Apple Configurator 注册配置文件”边栏选项卡中，选择要导出的配置文件。

3. 在配置文件的边栏选项卡中，选择“导出配置文件”。

4. 将配置文件 URL 复制到附加了 iOS 设备的 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)。 稍后你将在 Apple Configurator 中将其上传，以定义 iOS 设备使用的 Intune 配置文件。

  你可以按照以下过程使用 Apple Configurator 将此配置文件 URL 上载到 Apple 服务，以定义 iOS 设备使用的 Intune 配置文件。

5. 使用 Apple Configurator 将此配置文件 URL 上传到 Apple 服务，以定义 iOS 设备使用的 Intune 配置文件。
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

    查看[如何使最终用户了解 Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)。 也可以将最终用户转到[通过 Intune 使用 iOS 或 macOS 设备](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)

## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>用户如何在其设备上安装和使用公司门户

配置了用户关联的设备可以安装和运行公司门户应用，以下载应用和管理设备。 用户收到设备后，必须完成如下所述的其他步骤，才能完成设置助理并安装公司门户应用。

