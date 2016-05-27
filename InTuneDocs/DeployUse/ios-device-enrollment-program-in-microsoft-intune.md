---
# required metadata

title: 使用 Microsoft Intune 对 iOS 设备进行 Apple DEP 管理 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用设备注册计划注册企业所有的 iOS 设备
Microsoft Intune 可以部署注册配置文件，该配置文件以“无线”方式注册通过设备注册计划 (DEP) 购买的 iOS 设备。 注册包包括设备的设置助理选项。 用户无法注销通过 DEP 注册的设备。

## 使用 Microsoft Intune 对 iOS 设备进行 Apple DEP 管理
要使用 Apple 的设备注册程序 (DEP) 管理企业所有的 iOS 设备，则你的组织必须加入 Apple DEP 并通过该程序获取设备。 该过程的详细信息，可以通过以下网站获得：  [https://deploy.apple.com](https://deploy.apple.com)。 该程序的优点包括免手动设置设备，无需通过 USB 将每个设备连接到计算机。

在你可以通过 DEP 注册企业所拥有的 iOS 设备之前，你需要从 Apple 获得 DEP 令牌。 此令牌允许 Intune 同步有关你的企业所拥有的且加入了 DEP 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

1.  **开始使用 Microsoft Intune 管理 iOS 设备**
    在能够注册 iOS 设备注册计划 (DEP) 之前，必须对 Intune 完成启用 iOS 管理的步骤。

2.  **获取加密密匙**
    以管理用户身份打开 [Microsoft Intune 管理控制台](http://manage.microsoft.com)，转至“管理” &gt; “移动设备管理” &gt; “iOS” &gt; “设备注册计划”，然后单击“下载加密密钥”。 在本地保存加密密钥(.pem)文件。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。

      ![更新设备注册计划令牌](../media/dev-sa-ios-dep.png)

3.  **获取设备注册计划令牌**
    转到[设备注册计划门户](https://deploy.apple.com) (https://deploy.apple.com)，然后使用公司 Apple ID 登录。 若要续订 DEP 令牌，必须在将来使用此 Apple ID。

    1.  在[设备注册计划门户](https://deploy.apple.com)中，转到“设备注册计划” &gt; “管理服务器”，然后单击“添加 MDM 服务器”。.

    2.  输入 **“MDM 服务器名称”** ，然后单击 **“下一步”**。 服务器名称供参考，用于识别 MDM 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

    3.  此时将打开“添加 &lt;服务器名称&gt;”对话框。 单击“选择文件…” 以上传 .pem 文件，然后单击“下一步”。.

    4.  “添加 &lt;服务器名称&gt;”对话框将显示“你的服务器令牌”链接。 将服务器令牌 (.p7m) 文件下载到计算机，然后单击“完成”。.

    此证书(.p7m)文件用于在 Intune 和 Apple 的设备注册计划服务器之间建立信任关系。

4.  **将 DEP 令牌添加到 Intune**
    在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“管理” &gt; “移动设备管理” &gt; “iOS” &gt; “设备注册计划”，然后单击“上载 DEP 令牌”。浏览到证书 (.p7m) 文件，输入你的“Apple ID”，然后单击“上载”。. .

5.  **添加企业设备注册策略**
    在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“策略” &gt; “企业设备注册”，然后单击“添加”。 提供 **“常规”** 详细信息，包括 **“名称”** 和 **“说明”**，指定分配到配置文件的设备是否拥有用户相关性或是否属于某个组，然后启用 **“配置此策略的设备注册计划设置”** 以支持 DEP。  **“设置助理”窗格** 定义安装过程中配置的 iOS 设备设置。

      ![设置助理窗格](../media/pol-sa-corp-enroll.png)

6.  **分配 DEP 设备以进行管理**
    转到[设备注册计划门户](https://deploy.apple.com) (https://deploy.apple.com)，然后使用公司 Apple ID 登录。 转到“部署计划” &gt; “设备注册计划” &gt; “管理设备”。 指定 **“选择设备”**的方式，提供设备信息并按设备 **“序列号”**、 **“订单编号”**指定详细信息，或 **“上载 CSV 文件”**。 接下来，选择“分配到服务器”，然后选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后单击“确定”。.

7.  **同步 DEP 托管的设备**
    以管理用户身份打开 [Microsoft Intune 管理控制台](http://manage.microsoft.com)，转至“管理” &gt; “移动设备管理” &gt; “iOS” &gt; “设备注册计划”，然后单击“立即同步”。 会向 Apple 发送同步请求。 若要在同步后查看 DEP 托管的设备，在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“组” &gt; “所有企业所有的设备”。 在“企业拥有的设备”工作区中，在打开设备并运行设置助理以注册设备之前，托管设备的“状态”将一直显示为“未连接”。

    为了遵从 Apple 的有关可接受的 DEP 流量的条款，Intune 规定了以下限制：
     -  每 7 天只运行一次完全的 DEP 同步。 无论之前是否同步了序列号，在完全同步时，Intune 都将刷新 Apple 分配给 Intune 的每个序列号。 如果在上一个完全同步的 7 天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
     -  任何同步请求都在 10 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。

8.  **将设备分配给用户**
    你的企业拥有的设备现在可以分配给用户。 打开 iOS 设备时，它将注册为由 Intune 管理。



### 另请参阅
[为注册设备做好准备](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


