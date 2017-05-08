---
title: "创建策略并向用户发布应用 | Microsoft Docs"
description: "当你注册 Intune 的免费 30 天评估时，如何创建策略并发布应用"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 12/12/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 21d1e624069117d905dc7aced33b70abeb0e1109
ms.contentlocale: zh-cn
ms.lasthandoff: 04/14/2017


---


# <a name="create-policies-and-publish-an-app-to-evaluation-users"></a>创建策略并向评估用户发布应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 策略提供的设置有助于控制移动设备上的安全设置、维护计算机的 Windows 防火墙和 Endpoint Protection 设置以及部署应用程序。 如果你打算在评估之后对你配置用于生产用的设备使用 Intune，请遵循[使用 Microsoft Intune 策略管理设备上的设置和功能](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)和[使用适用于 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)中的说明，这绝对必要。

可以使用 Intune 执行两种类型的应用安装。 第一种是“必需安装”，它会自动将该应用部署到托管的设备。 另一个是“可用安装”，它将应用或应用的链接部署到 Intune 公司门户，以便用户可以选择将其安装到计算机上或移动设备上。

使用 Intune 部署应用之前，请确保你有合适的许可证，以发布、分发和使用应用。 利用“许可证”工作区，可以为通过 Microsoft 批量许可协议购买的应用或软件以及通过其他方法购买的 Microsoft 或非 Microsoft 应用或软件添加和管理许可协议信息。 然后可以创建许可证报表，此报表将显示整个公司内的托管许可证使用情况信息，以随时了解许可证使用情况活动。

在这些步骤中，将设置移动设备配置策略和 Windows 计算机防火墙策略，并在移动设备注册后，将 Skype 配置为这些移动设备的可用安装。 添加并部署新策略后，向其部署策略的组中的所有用户或设备都将继承该设置，使其作为它们的基准策略。 之后，你始终可以从管理控制台中的“策略”  工作区查看和编辑这些策略的详细信息。

## <a name="create-and-deploy-a-mobile-device-configuration-policy"></a>创建和部署移动设备配置策略

1.  打开 [Intune 管理控制台](https://manage.microsoft.com/)。

2.  在左窗格中，选择“策略”图标。

3.  在**策略概述**页上的**任务**列表中，选择**添加策略**。

4.  在策略列表中，展开想要为其创建策略的平台，选择“常规配置”，选择“创建和部署自定义策略”，然后选择“创建策略”。

5.  当提示“选择想要对其部署该策略的组”时，从列表选择“我的试用用户”，然后选择“添加”&gt;“确定”。

你的策略将出现在配置策略的列表中，并已部署到 **“我的试用用户”** 组。 双击策略查看其设置。

## <a name="publish-the-skype-app-for-mobile-devices"></a>发布移动设备的 Skype 应用

1.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，选择“应用”图标，然后选择“应用”&gt;“添加应用”。 如果出现提示，输入你的 Intune 凭据。

    > [!NOTE]
    > 首次启动 **Intune 软件发行者** 时，安装应用程序时会出现短暂延迟。

2.  查看安全警告并选择“运行”。

3.  在**开始之前**页上，选择**下一步**。

4.  在“软件安装程序”  页上的“选择如何将此软件提供给设备” 中，选择“外部链接” 。

5.  在“指定 URL”中输入软件的外部链接，然后选择“下一步”。 请确保 URL 以 **https://** 开头。 对于 Skype 应用，请使用下面的链接，这些链接与你使用的移动设备平台相匹配：

    -   **iOS：**[https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android：**[https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8.1:** [http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  在“软件描述”页上，提供你希望用户在软件的公司门户中看到的信息，然后选择“下一步”。 以下设置可用（此示例指 Skype）：

    -   **发布者：**输入发布者的名称，“Microsoft”

    -   **名称：** 输入 **Skype**

    -   **描述:** 输入对软件的描述，如 **Skype 通信应用**

    -   **类别：** 选择最适合此软件的类别，如 **协作**

    -   **将此应用显示为特色应用并在公司门户中突出显示：**选择此选项以在移动设备上的公司门户中突出显示应用。

    -   **图标：**  （可选）选择是否要将图标与软件关联。 图标的最大大小是 250 x 250 像素，但建议的图标大小为 32 x 32 像素。

7.  在“摘要”页上，验证软件信息，然后选择“上传”。 选择“关闭”以退出向导。

8.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，依次选择“应用”&gt;“应用”&gt;“Skype”&gt;“管理部署”。

9. 在**“选择组”**页上，选择“我的试用用户”以将软件部署到该用户组，然后选择“添加”&gt;“下一步”。

10. 在 **“部署操作”** 页上，从组的 **“批准”** 列选择 **“可用安装”** 。

11. 选择**完成**。

## <a name="install-the-skype-app"></a>安装 Skype 应用
在移动设备上打开公司门户，选择“应用”，然后安装 Microsoft Skype。

这样就完成了 Intune 移动设备管理指南，但可以跟随“后续步骤”部分的链接深入了解 Intune。
## <a name="next-steps"></a>后续步骤
深入了解其他 [Intune 功能](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)

了解 [Intune 的常见使用方式](common-ways-to-use-intune.md)

转换为[付费订阅](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)

