---
# required metadata

title: 使用 Microsoft Intune 对 iOS 设备进行直接注册 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Apple Configurator 直接注册 iOS 设备
Intune 支持注册企业所有的 iOS 设备，方法是使用在 Mac 计算机上运行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具。 此过程不会恢复设备的出厂设置，并使用预定义策略注册设备。 此方法针对“无用户关联”的设备，并且要求你通过 USB 将 iOS 设备连接到 Mac 计算机以设置企业注册。 直接注册的设备不支持公司门户应用。 本指南假定你在 Mac 计算机上使用 Apple Configurator 2.0。

1.  创建设备的配置文件 设备注册配置文件定义应用于设备的设置。

    #### 如果尚无此配置文件，请使用 Apple Configurator 创建已注册的 iOS 设备的设备注册配置文件。

    1.  创建配置文件

        ![在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“策略” &gt; “企业设备注册”，然后单击“添加...”。](../media/pol-sa-corp-enroll.png)

    2.  创建设备注册配置文件页面

        -   输入设备配置文件的详细信息： **“名称”** – 设备注册配置文件的名称。

        -   对用户不可见。 “说明”- 设备注册配置文件的说明。

        -   对用户不可见。 **“用户隶属关系”** – 指定注册设备的方式。

        -   对于直接注册，请选择“无用户关联”。 “设备组预分配”– 部署此配置文件的所有设备将最初属于此组。

    3.  在注册后，可以将设备重新分配。

2.  单击 **“保存配置文件”** 以添加配置文件。

    ![通过 Apple Configurator 添加 iOS 设备以进行注册](../media/pol-SA-enroll-iOS-SetupAssistant.png)

      在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“组” &gt; “所有设备” &gt; “企业预注册的设备” &gt; “按 iOS 序列号”，然后单击“添加设备…”。

    -   iOS 设置助理

        |||
        |-|-|
        |&lt;可以通过两种方式添加设备：&gt;|&lt;“上传包含序列号的 CSV 文件” - 创建不带标头的两列的逗号分隔值 (.csv) 列表，每个 csv 文件限 5000 台设备或 5 MB。&gt;|
        |&lt;Serial #1&gt;|&lt;Device #1 Details&gt;|
        Serial#2

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   设备 #2 详细信息

    > [!NOTE]
    > 在文本编辑器中查看该 .csv 文件时，该文件显示为：  **手动添加设备详细信息** - 输入最多五台设备的序列号和设备详细信息，然后单击“下一步”。

3.  如果稍后必须从 Intune 管理中删除企业拥有的设备，则必须在“企业拥有的设备”组中从 Intune 删除设备序列号以禁用设备注册。 如果 Intune 在删除序列号时或大约在这一时间执行灾难恢复过程，你需要验证组里是否仅包含活动设备的序列号。 选择要注册的设备

4.  确认要注册的设备。 无法导入已注册或通过其他方式注册的序列号。

5.  单击 **“下一步”** 以继续。 分配配置文件 指定要从可用配置文件列表分配到已添加的设备的配置文件，查看 **“注册配置文件详细信息”**，然后单击 **“完成”**。 可以将手动添加的设备分配到任何注册配置文件。 选择要部署到 iOS 设备的配置文件

6.  在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中转到“策略” &gt; “公司设备注册”，然后选择要部署到移动设备的设备配置文件。
    > [!NOTE]
    > 此配置文件应为在前一步中分配用于部署的同一配置文件。 在任务栏中，单击
7.  “导出…”。

    1.  单击“下载配置文件”并保存下载的 .mobileconfig 文件。

    2.  传输文件 复制已下载的 .mobileconfig 文件到 Mac 计算机。

    3.  注册配置文件 URL 从导出时开始两周内有效。 两周过后，必须导出新的注册配置文件 URL 以使用设置助理注册 iOS 设备。 用 Apple Configurator 准备设备

    4.  iOS 设备连接到 Mac 计算机，并注册移动设备管理。 在 Mac 计算机上，启动 **Apple Configurator 2.0**。  使用 USB 线将 iOS 设备连接到 Mac 计算机。

8.  关闭“照片”、**iTunes** 和其他在检测设备时为设备打开的应用。 在 Apple Configurator 中，单击已连接的 iOS 设备，然后单击“添加”按钮。  可以添加到设备的选项将显示在下拉列表中。

    ###### 单击“配置文件”。

    1.  使用文件选取器选择从 Intune 导出的 .mobileconfig 文件，然后单击“添加”。

    2.  配置文件将添加到设备。

    3.  如果设备是“非监督”状态，安装将在设备需要验收。

    4.  安装配置文件

    5.  已准备好在 iOS 设备上安装配置文件。

    6.  设备必须已经完成设置助理且准备好使用。

9. 如果注册需要应用部署，设备应设置一个 Apple ID，因为应用部署将需要你有一个 Apple ID 登录到应用商店。 完成非监督的 iOS 设备的配置文件验收

10. 解锁 iOS 设备。


### 在“管理配置文件”的“安装配置文件”对话框中，点击“安装”。
[如果需要的话，提供“设备密码”或“Apple ID”。](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


