---
# required metadata

title: 创建策略并发布应用程序 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 创建策略并发布应用程序
Intune 策略提供的设置有助于控制移动设备上的安全设置、维护计算机的 Windows 防火墙和 Endpoint Protection 设置以及部署应用程序。 你可以在[使用 Microsoft Intune 策略管理设备上的设置和功能](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)和[使用适用于 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)中了解更多信息

可以使用 Intune 执行两种类型的应用安装。 第一种是 **必需安装**，它会自动将该应用部署到托管的计算机。 另一个是 **可用安装**，它将应用或应用的链接部署到 Intune 公司门户，以便用户可以选择将其安装到计算机上或移动设备上。

<!-- this section really isn't necessary and confuses a lot of people because most mobile device apps aren't licensed this way (and our licensing/reporting features aren't super helpful). I think it's best to avoid this during a quick start guide.

Before using Intune to deploy apps, make sure that you have the appropriate licenses to publish, distribute, and use the app. The Licenses workspace lets you add and manage license agreement information for apps or software purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.
-->

下列步骤将帮助你设置移动设备配置策略和 Windows 电脑防火墙策略，并在移动设备注册后，将 Skype 配置为这些移动设备的可用安装。

> [!TIP]
> 添加并部署新策略后，向其部署策略的组中的所有用户或设备都将继承该设置，使其作为它们的基准策略。 之后，你始终可以从“策略”工作区查看和编辑这些策略的详细信息。


## 创建和部署移动设备配置策略

1.  打开 [Intune 管理控制台](https://manage.microsoft.com/)

2.  在左窗格中，选择“策略”图标。

    ![admin-console-policy-workspace](./media/policy.png)

3.  在“策略概述”页上的“任务”列表中，选择“添加策略”。

4.  在策略列表中，展开想要为其创建策略的平台，然后选择“常规配置” > “使用建议的设置创建和部署策略” > “创建策略”

5.  当系统提示“选择你想要将此策略部署到的组”时，从可用的组列表中选择“Intune 用户”（上一步中创建的组），然后选择“添加” > “确定”

你的策略将出现在配置策略的列表中，并已部署到“Intune 用户”组。 双击策略查看其设置。

## 发布移动设备的 Skype 应用

1.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，选择“应用”图标，然后选择“应用” > “添加应用”。 如果出现提示，输入你的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 凭据。

    ![admin-console-apps-workspace](./media/apps.png)

    > 首次启动 **Intune 软件发行者** 时，安装应用程序时会出现短暂延迟。

2.  查看安全警告并选择“运行”。

3.  在“开始之前”页上，选择“下一步”

4.  在“软件安装程序”页上的“选择如何将此软件提供给设备”中，选择“外部链接”

5.  在“指定 URL”中输入软件的外部链接，然后选择“下一步”。 请确保 URL 以 **http://** 开头。 对于 Skype 应用，请使用下面的链接，这些链接与你使用的移动设备平台相匹配：

    -   **iOS：**   [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android：**  [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 或 Windows Phone 8.1：**  [http://www.windowsphone.com/zh-cn/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  在“软件描述”页上，提供你希望用户在软件的公司门户中看到的信息，然后选择“下一步”。 以下设置可用（此示例指 Skype）：

    -   **发布者：** 输入发布者的名称，“Microsoft”

    -   **名称：** 输入 **Skype**

    -   **描述:** 输入对软件的描述，如 **Skype 通信应用**

    -   **类别：** 选择最适合此软件的类别，如 **协作**

    -   **将此应用显示为特色应用并在公司门户中突出显示：** 选择此选项以在移动设备上的公司门户中突出显示应用。

    -   **图柄：**选择是否要将图标与软件关联。 可选图标的最大大小为 250 x 250 像素，建议的大小为 32 x 32 像素。

7.  在“摘要”页上，验证软件信息，然后选择“上传”。 选择“关闭”以退出向导。

8.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，选择“应用” > “应用” > “Skype” > “管理部署”

9. 在“选择组”页上，选择“Intune用户”以将软件部署到该用户组，然后选择“添加” > “下一步”

10. 在 **“部署操作”** 页上，从组的 **“批准”** 列选择 **“可用安装”** 。

11. 选择“完成”

Skype 应用现已可从公司门户中在移动设备上安装，但首先你需要在计算机和移动设备上安装 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 软件。


### 后续步骤
祝贺你！ 你刚刚完成了 *Intune 快速入门指南*的步骤 6

>[!div class="step-by-step"]

>[&larr; **组织用户和设备**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**自定义公司门户** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  


<!--HONumber=May16_HO2-->


