---
title: "适用于 iOS 设备的 Apple DEP 管理 | Microsoft Docs"
description: "部署注册配置文件，该配置文件以“无线”方式注册通过 iOS 设备注册计划 (DEP) 购买的 iOS 设备以管理 Apple 设备。"
keywords: 
author: staciebarker
ms.author: stabar
manager: arob98
ms.date: 12/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8063b933a767740a7951fa69a918a8677b664d02
ms.openlocfilehash: e8a21ace32b5668f8158b9a383b882b7c2f524df


---

# <a name="enroll-corporate-owned-device-enrollment-program-ios-devices"></a>使用设备注册计划注册企业所有的 iOS 设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可以部署注册配置文件，该配置文件以“无线”方式注册通过设备注册计划 (DEP) 购买的 iOS 设备。 注册包包括设备的设置助理选项。 用户无法注销通过 DEP 注册的设备。

## <a name="apple-dep-management-for-ios-devices-with-microsoft-intune"></a>使用 Microsoft Intune 对 iOS 设备进行 Apple DEP 管理
要使用 Apple 的设备注册计划 (DEP) 管理公司拥有的 iOS 设备，组织必须加入 Apple DEP 并通过该计划获取设备。 该过程的详细信息，可以通过以下网站获得：  [https://deploy.apple.com](https://deploy.apple.com)。 该计划的优点包括免手动设置设备，无需通过 USB 电缆将每个设备连接到计算机。

可以通过 DEP 注册公司拥有的 iOS 设备之前，需要从 Apple 获得 DEP 令牌。 此令牌允许 Intune 同步有关公司所拥有的且加入了 DEP 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

1.  **开始使用 Microsoft Intune 管理 iOS 设备**</br>
    能够注册 iOS 设备注册计划 (DEP) 之前，必须完成对 Intune 启用 iOS 管理。

2.  **获取加密密钥**</br>
    以管理用户身份打开 [Microsoft Intune 管理控制台](http://manage.microsoft.com)，转到“管理”&gt;“移动设备管理”&gt;“iOS”&gt;“设备注册计划”，然后选择“下载加密密钥”。 在本地保存加密密钥(.pem)文件。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。

      ![更新设备注册计划令牌](../media/dev-sa-ios-dep.png)

3.  **获取设备注册计划令牌**</br>
    转到[设备注册计划门户](https://deploy.apple.com) (https://deploy.apple.com)，然后使用公司 Apple ID 登录。 之后必须使用此 Apple ID 才能续订 DEP 令牌。

    1.  在[设备注册计划门户](https://deploy.apple.com)中，转到“设备注册计划”&gt;“管理服务器”，然后选择“添加 MDM 服务器”。

    2.  输入“MDM 服务器名称”，然后选择“下一步”。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

    3.  此时将打开“添加 &lt;服务器名称&gt;”对话框。 选择“选择文件…” 以上传 .pem 文件，然后选择“下一步”。

    4.  “添加 &lt;ServerName&gt;”对话框显示“你的服务器令牌”链接。 将服务器令牌 (.p7m) 文件下载到计算机，然后选择“完成”。

    此证书(.p7m)文件用于在 Intune 和 Apple 的设备注册计划服务器之间建立信任关系。

4.  **将 DEP 令牌添加到 Intune**</br>
    在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)，转到“管理”&gt;“移动设备管理”&gt;“iOS”&gt;“设备注册计划”，然后选择“上传 DEP 令牌”。 **浏览**到证书 (.p7m) 文件，输入你的 **Apple ID**，然后选择“上传”。

5.  **添加企业设备注册策略**</br>
    在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“策略”&gt;“企业设备注册”，然后选择“添加”。

    提供**常规**详细信息，包括**名称**和**说明**，然后指定分配到配置文件的设备是否拥有用户关联或是否属于某个组。
      - **用户关联提示**：必须在初始设置过程中将设备与某个用户相关联，然后才能以该用户的身份允许此设备访问公司数据和电子邮件。 应该对属于用户且需要使用公司门户（即需要安装应用）的 DEP 托管设备设置**用户关联**。 在具有用户关联的 DEP 设备上注册期间，多重身份验证 (MFA) 不起作用。 注册之后，MFA 在这些设备上会正常运行。 

      > [!NOTE]
      > 具有用户关联的 DEP 要求启用 WS-Trust 1.3 用户名/混合终结点以请求用户令牌。

      - **没有用户关联**：该设备不与用户关联。 将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）无法运行。

    你还可以**将设备分配到以下组**。 选择“选择...”来选择组。

    [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    然后，启用**为该策略配置设备注册程序设置**以支持 DEP。

      ![设置助理窗格](../media/pol-sa-corp-enroll.png)

     为 DEP 托管的设备提供了下列设置：

     - **部门** - 用户在激活过程中点击“关于配置”时显示
     - **支持电话号码** - 用户在激活过程中单击“需要帮助”按钮时显示
     - **准备模式** - 在激活过程中设置，且只能通过恢复设备出厂设置更改：
        - **无人监督** - 有限的管理功能
        - **受到监督** - 启用更多的管理选项，并默认禁用激活锁定
     - **将注册配置文件锁定到设备** - 在激活过程中设置，且只能通过恢复出厂设置更改
        - **禁用** - 允许从**设置**菜单中删除管理配置文件
        - **启用** -（需要**准备模式** = **受到监督**）禁用可能允许删除管理配置文件的 iOS 设置
     - **设置助理选项** - 这些可选设置可以稍后在 iOS 的“设置”菜单中设置。
        - **密码** - 在激活过程中提示输入密码。 始终需要密码，除非设备将受到保护，或以某种其他方式（即限制设备只可使用一个应用的展台模式）控制访问权限。
        - **定位服务** - 如果启用，在激活过程中设置助手会提示此服务
        - **还原** - 如果启用，在激活过程中设置助手会提示进行 iCloud 备份
        - **Apple ID**如果启用，Intune 在没有 ID 的情况下尝试安装应用时，iOS 将提示用户提供 Apple ID。 下载 iOS 应用商店应用（包括由 Intune 安装的应用）时需要 Apple ID。
        - **条款和条件** - 如果启用，在激活过程中设置助手会提示用户接受 Apple 的条款和条件
        - **Touch ID** - 如果启用，在激活过程中设置助手会提示此服务
        - **Apple Pay** - 如果启用，在激活过程中设置助手会提示此服务
        - **Zoom** - 如果启用，在激活过程中设置助手会提示此服务
        - **Siri** - 如果启用，在激活过程中设置助手会提示此服务
        - **向 Apple 发送诊断数据** - 如果启用，在激活过程中设置助手会提示此服务
     -  **启用附加 Apple Configurator 管理** - 设置为**禁止**可阻止通过 Apple Configurator 与 iTunes 或管理同步文件。 建议选择“禁止”，从 Apple 配置器中导出任何进一步的配置，然后通过 Intune 部署为自定义 iOS 配置文件，而不使用此设置允许带或不带证书的手动部署。
        - **禁止** - 阻止设备通过 USB （禁止配对）进行通信
        - **允许** - 允许设备通过任何电脑或 Mac 的 USB 连接进行通信
        - **需要证书** - 允许与具有导入到注册配置文件的证书的 Mac 配对

6.  **分配 DEP 设备以进行管理**转到[设备注册计划门户](https://deploy.apple.com) (https://deploy.apple.com) 然后使用公司 Apple ID 登录。 转到“部署计划”&gt;“设备注册计划”&gt;“管理设备”。 指定 **“选择设备”**的方式，提供设备信息并按设备 **“序列号”**、 **“订单编号”**指定详细信息，或 **“上载 CSV 文件”**。 接下来，选择“分配到服务器”，然后选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后选择“确定”。

7.  **同步 DEP 托管的设备** 以管理用户身份，打开 [Microsoft Intune 管理控制台](http://manage.microsoft.com)，转到“管理”&gt;“移动设备管理”&gt;“iOS”&gt;“设备注册计划”，然后选择“立即同步”。 会向 Apple 发送同步请求。 若要在同步后查看 DEP 托管的设备，在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“组”&gt;“所有设备”&gt;“企业预注册设备”&gt;“按 iOS 序列号”。 在“按 iOS 序列号”工作区中，在打开设备并运行设置助理以注册设备之前，托管设备的“状态”将一直显示为“未连接”。

    为了遵从 Apple 的有关可接受的 DEP 流量的条款，Intune 规定了以下限制：
     -  每七天只运行一次完全的 DEP 同步。 无论之前是否同步了序列号，在完全同步时，Intune 都将刷新 Apple 分配给 Intune 的每个序列号。 如果在上一个完全同步的七天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
     -  任何同步请求都在 10 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。

8.  **将设备分配给用户**你的企业拥有的设备现在可以分配给用户。 打开 iOS 设备时，它将注册为由 Intune 管理。

## <a name="changes-to-intune-group-assignments"></a>Intune 组分配的更改

从 2016 年 12 月开始，设备组管理将移到 Azure Active Directory。 过渡到 Azure Active Directory 组后，组分配将不会出现在“企业注册配置文件”选项中。 由于此更改将历时数月，因此你可能不会立即看到更改。 移到新的门户后，可以根据企业注册配置文件名称定义动态设备组分配。 此过程可确保分配到设备组的设备会自动注册到部署了策略和应用的组中。 [详细了解 Azure Active Directory 组](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)

### <a name="see-also"></a>另请参阅
[注册设备的先决条件](prerequisites-for-enrollment.md)



<!--HONumber=Jan17_HO1-->


