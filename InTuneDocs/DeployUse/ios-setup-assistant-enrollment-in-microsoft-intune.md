---
# required metadata

title: 使用 Microsoft Intune 对 iOS 设备设置助理注册 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用设置助理通过 Apple Configurator 注册 iOS 设备
Intune 支持注册企业所有的 iOS 设备，方法是使用在 Mac 计算机上运行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具。 此过程可恢复设备的出厂设置，并且在预安装了公司的策略的情况下将其准备好，以便由设备的新用户运行设置助理。


## 使用 Microsoft Intune 对 iOS 设备设置助理注册
可以使用 Apple Configurator 恢复 iOS 设备的出厂设置并做好准备，使新用户能够对设备进行设置。  此方法要求你通过 USB 将 iOS 设备连接到 Mac 计算机以设置企业注册，并且假定你使用的是 Apple Configurator 2.0。 大多数情况要求应用到 iOS 设备的策略包括“用户关联性”，以便启用 Intune 公司门户应用。

**先决条件**
* 具有对 iOS 设备的物理访问权限 - 设备必须在没有密码保护的情况下处于未配置状态（恢复出厂设置）
* 设备序列号 - [如何获取 iOS 序列号](https://support.apple.com/en-us/HT204308)
* USB 连接电缆
* 安装了 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 的 Mac 计算机


1.  **创建移动设备组** （可选） 如果你的业务要求借助移动设备组来管理设备，请创建这些组。

2.  通过 Microsoft Intune 使用组来管理用户和设备 创建设备的配置文件

    ###### 设备注册配置文件定义应用于设备组的设置。

    1.  如果尚无此配置文件，请使用 Apple Configurator 创建已注册的 iOS 设备的设备注册配置文件。

    ![创建配置文件](../media/pol-sa-corp-enroll.png)

    2.  在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“策略” &gt; “企业所有的设备”，然后单击“添加...”

        -   创建设备注册配置文件 输入设备配置文件的详细信息：

        -   **“名称”** – 设备注册配置文件的名称。 （对用户不可见）

        -   “说明”- 设备注册配置文件的说明。

            -   （对用户不可见） “注册详细信息”– 指定注册设备的方式。
            “用户关联提示”– 可在初始设置过程中将 iOS 设备与用户相关联，然后允许该用户将其用于访问公司数据和电子邮件。

                -   对于大多数设置助理方案，请使用“用户关联提示” 此模式支持多种方案：

                -   “企业拥有的个人设备”–“自带设备办公”(CYOD)与私人拥有的设备或个人设备相似，但管理员具有某些权限，包括擦除、重置、管理和注销设备的权限。 设备的用户可安装应用，并且拥有大多数其他设备用途的权限（如果不被管理策略阻止）。 **设备注册管理器帐户** – 使用特殊的 Intune 管理员帐户注册设备。

            -   可将其作为私人帐户管理，但只有知道注册管理器凭据的用户才可安装应用程序，擦除、重置、管理和注销设备。 有关注册多个用户通过共同帐户共享的设备的信息，请参阅[使用 Microsoft Intune 中的“设备注册管理器”注册企业自有设备](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) “没有用户关联性”– 该设备不可多个用户共享。

        -   将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户隶属关系的应用程序已禁用或无法运行。

          -  “设备组预分配”– 部署此配置文件的所有设备将最初属于此组。 在注册后，可以将设备重新分配。

    3.  **设备注册计划** - Apple 设备注册计划 (DEP) 不能与设置助理注册一起使用。

3.  确保将开关设置为“关闭” 单击 **“保存配置文件”** 以添加配置文件。

    ![通过设置助理添加 iOS 设备以进行注册](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“组” &gt; “所有设备” &gt; “所有企业所有的设备” &gt; “所有设备”，然后单击“添加设备…”

        |||
        |-|-|
        |&lt;可以通过两种方式添加设备：&gt;|&lt;添加设备对话框&gt;|
        |&lt;“上传包含序列号的 CSV 文件” - 创建不带标头的两列的逗号分隔值 (.csv) 列表，每个 csv 文件限 5000 台设备或 5 MB。&gt;|&lt;Serial #1&gt;|
        Device #1 Details

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   Serial#2

    > [!NOTE]
    > 设备 #2 详细信息  在文本编辑器中查看该 .csv 文件时，该文件显示为：

    “手动添加设备详细信息”- 输入最多五台设备的序列号和设备详细信息

4.  如果稍后必须从 Intune 管理中删除企业拥有的设备，则可能需要在“企业拥有的设备”组中从 Intune 删除设备序列号以禁用设备注册。 如果 Intune 在删除序列号时或大约在这一时间执行灾难恢复过程，你需要验证组里是否仅包含活动设备的序列号。 然后单击“下一步”

5.  选择要注册的设备 确认要注册的设备。

6.  无法导入已注册或通过其他方式注册的序列号。 单击 **“下一步”** 以继续。 分配配置文件 指定要从可用配置文件列表分配到已添加的设备的配置文件，查看 **“注册配置文件详细信息”**，然后单击 **“完成”**。 可以将手动添加的设备分配到任何注册配置文件。
    导出要部署到 iOS 设备的配置文件 在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中转到“策略” &gt; “公司设备注册”，然后选择要部署到移动设备的设备配置文件。
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    在任务栏中，单击

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   “导出…”。

    > [!NOTE]
    > 复制并保存 **“配置文件 URL”**。 稍后你将在 Apple Configurator 中将其上传，以定义 iOS 设备使用的 Intune 配置文件。

7.  要支持 Apple Configurator 2，必须编辑 2.0 配置文件 URL。

    1.  替换 与

         > [!WARNING]
         > 你可以按照以下过程使用 Apple Configurator 将此配置文件 URL 上载到 Apple DEP 服务，以定义 iOS 设备使用的 Intune 配置文件。 注册配置文件 URL 从导出时开始两周内有效。 两周过后，必须导出新的注册配置文件 URL 以使用设置助理注册 iOS 设备。

    2. 用 Apple Configurator 准备设备 iOS 设备连接到 Mac 计算机，并注册移动设备管理。

    3. 在 Mac 计算机上，打开“Apple Configurator 2”。 在菜单栏中，单击“Apple Configurator 2”，然后单击“首选项” 注册过程中，设备将重置为工厂配置。  

       最佳做法是重置设备并启动它。 作为最佳做法，当连接设备时，设备应处于 **Hello** 屏幕界面。 在首选项窗格中，选择“服务器”，然后在左窗格下方单击“+”符号以启动 MDM 服务器向导。

    4.  单击“下一步” 输入上面的第 6 步中 MDM 服务器的“名称”和“注册 URL”。 对于注册 URL，请输入从 Intune 中导出的注册配置文件 URL。

    5.  单击“下一步”

        > [!WARNING]
        > 如果你收到有关 Apple TV 的信任配置文件要求的警告，你可以单击灰色“X”放心地取消“信任配置文件”选项。 你还可以放心地忽略任何定位点证书警告。 若要继续，请单击“下一步”，直到完成该向导。

    6.  在“服务器”窗格中，单击新服务器的配置文件旁边的“编辑”。 确保注册 URL 与从 Intune 中导出的 URL 完全匹配。

    7. 如果不同，请重新输入原始 URL，并保存从 Intune 中导出的注册配置文件。

    8. 用 USB 适配器将 iOS 移动设备连接到 Apple 计算机。

    9. 注册过程中，设备将重置为工厂配置。

    10. 最佳做法是重置设备并启动它。 作为最佳做法，当启动设置助理时，设备应处于“Hello”屏幕界面。  

    11. 单击 **“准备”**。  

8.  在“准备 iOS 设备”窗格上，选择“手动”，然后单击“下一步” 在“在 MDM 服务器中注册”窗格上，选择你创建的服务器的名称，然后单击“下一步” 在“监督设备”窗格上，选择监督级别，然后单击“下一步”



### 在“创建组织”窗格上，选择“组织”或创建新的组织，然后单击“下一步”
[在“配置 iOS 设置助理”窗格上，选择提供给用户的步骤，然后单击“准备”。](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


