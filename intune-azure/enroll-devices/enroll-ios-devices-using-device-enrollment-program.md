---
title: "注册 iOS 设备 - 设备注册计划"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何使用设备注册计划注册企业拥有的 iOS 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 3e1898441b7576c07793e8b70f3c3f09f1cac534
ms.openlocfilehash: ddeaeb2d532635802c615d09b4625dee0a824919
ms.lasthandoff: 02/23/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>使用设备注册计划注册 iOS 设备

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune 可以部署注册配置文件，该配置文件以“无线”方式注册通过设备注册计划 (DEP) 购买的 iOS 设备。 配置文件包含想要应用于设备的管理设置。 注册包包括设备的设置助理选项。 用户无法注销通过 DEP 注册的设备。

>[!NOTE]
>此注册方法不能与[设备注册管理器](enroll-devices-using-device-enrollment-manager.md)方法共同使用。

要使用 Apple 的设备注册计划 (DEP) 管理公司拥有的 iOS 设备，组织必须加入 Apple DEP 并通过该计划获取设备。 该过程的详细信息，可以通过以下网站获得：  [https://deploy.apple.com](https://deploy.apple.com)。 该计划的优点包括免手动设置设备，无需通过 USB 电缆将每个设备连接到计算机。

可以通过 DEP 注册公司拥有的 iOS 设备之前，需要从 Apple [获得 DEP 令牌](get-apple-dep-token.md)。 此令牌允许 Intune 同步有关公司所拥有的且加入了 DEP 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

[选择在 Intune 中注册 iOS 设备的方式](choose-ios-enrollment-method.md)中介绍了注册 iOS 设备的其他方法。

## <a name="prerequisites"></a>先决条件

在设置 iOS 设备注册前，完成以下先决条件：

- [配置域](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [设置 MDM 机构](set-mdm-authority.md)
- [创建组](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- 在 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)中分配用户许可证
- [获取 Apple MDM Push Certificate](get-an-apple-mdm-push-certificate.md)
- [获取 Apple DEP 令牌](get-apple-dep-token.md)

## <a name="create-an-apple-dep-profile-for-devices"></a>为设备创建 Apple DEP 配置文件

设备注册配置文件定义应用于设备组的设置。 以下步骤说明如何为使用 DEP 注册的 iOS 设备创建设备注册配置文件。

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在“Intune”边栏选项卡上，选择“注册设备”，然后选择“Apple 注册”。

3. 在“管理 Apple 设备注册计划 (DEP) 设置”下，选择“DEP 配置文件”。

4. 在“Apple DEP 配置文件”边栏选项卡上，选择“创建”。

5. 在“创建注册配置文件”边栏选项卡上，输入配置文件的名称和说明。

6. 对于“用户关联”，请选择具有此配置文件的设备是否通过用户关联进行注册。

 - **通过用户关联注册** - 必须在初始设置过程中将设备与某个用户相关联，然后才能允许此设备访问公司数据和电子邮件。 对属于用户且需要使用公司门户获取服务（如安装应用）的 DEP 托管设备，选择用户关联。 请注意：在具有用户关联的 DEP 设备上注册期间，多重身份验证 (MFA) 不起作用。 注册之后，MFA 在这些设备上会正常运行。 注册 DEP 设备时，需要更改密码的新用户在首次登录时不会获得提示。 此外，在 DEP 注册过程中，密码已过期的用户不会获得重置密码的提示，必须使用其他设备重置密码。

    >[!NOTE]
    >具有用户关联的 DEP 要求启用 WS-Trust 1.3 用户名/混合终结点以请求用户令牌。

 - **不通过用户关联注册** - 该设备不与用户关联。 将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）无法运行。

7. 选择“设备管理设置”，配置以下配置文件设置，然后选择“保存”：

    - **受到监管** - 默认启用更多的管理选项并已禁用激活锁的管理模式。 如果将此复选框保留为空，则管理功能将受限。

    - **注册锁定** -（需要管理模式 = 受到监督）禁用可能允许删除管理配置文件的 iOS 设置。 如果将此复选框保留为空，它将允许从“设置”菜单中删除管理配置文件。 此项在激活过程中设置，且只能通过恢复出厂设置更改。

    - **允许配对** - 指定 iOS 设备是否可以与计算机同步。 如果选择“通过证书允许 Apple Configurator”，则必须在“Apple Configurator 证书”下选择证书。

    - **Apple Configurator 证书** - 如果在“允许配对”下选择“通过证书允许 Apple Configurator”，请选择要导入的 Apple Configurator 证书。

8. 选择“设置助理设置”，配置以下配置文件设置，然后选择“保存”：

    - **部门名称** - 用户在激活过程中点击“关于配置”时显示。

    - **部门电话** - 用户在激活过程中单击“需要帮助”按钮时显示。
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
        - **诊断数据** - 如果启用，在激活过程中设置助手会提示此服务

9. 若要保存配置文件设置，请在“创建注册配置文件”边栏选项卡上选择“创建”。

## <a name="assign-apple-dep-serial-numbers-to-your-mdm-server"></a>将 Apple DEP 序列号分配给 MDM 服务器

1. 转到[设备注册计划门户](https://deploy.apple.com) (https://deploy.apple.com)，然后使用公司 Apple ID 登录。

2. 转到“部署计划”&gt;“设备注册计划”&gt;“管理设备”。

3. 指定**选择设备**的方式，然后提供设备信息并按设备**序列号**、**订单编号**指定详细信息，或**上传 CSV 文件**。

4. 选择“分配到服务器”，然后选择为 Microsoft Intune 指定的 &lt;ServerName&gt;，然后选择“确定”。

## <a name="synchronize-dep-managed-devices"></a>同步 DEP 管理的设备

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在Azure 门户的“Intune”边栏选项卡上，选择“注册设备”，然后选择“Apple 注册”。

3. 在“管理 Apple 设备注册计划(DEP)设置”下，选择“DEP 序列号”。

4. 在“Apple DEP 序列号”边栏选项卡上，选择“同步”。

5. 在“同步”边栏选项卡，选择“请求同步”。 进度栏显示再次请求同步之前必须等待的时长。

    为了遵从 Apple 的有关可接受的 DEP 流量的条款，Intune 规定了以下限制：
     -    每七天只运行一次完全的 DEP 同步。 无论之前是否同步了序列号，在完全同步时，Intune 都将刷新 Apple 分配给 Intune 的每个序列号。 如果在上一个完全同步的七天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
     -    任何同步请求都在 10 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。

>[!NOTE]
>还可以从“Apple DEP 序列号”边栏选项卡将 DEP 序列号分配给配置文件。

## <a name="distribute-devices-to-users"></a>将设备分配给用户

现在可以将公司拥有的设备分发给用户。 打开 iOS 设备时，它将注册为由 Intune 管理。


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>用户如何在其设备上安装和使用公司门户

配置了用户关联的设备可以安装和运行公司门户应用，以下载应用和管理设备。 用户收到设备后，必须完成如下所述的其他步骤，才能完成设置助理并安装公司门户应用。

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>用户如何注册具有用户关联的公司所有的 iOS 设备

1. 用户打开设备时，系统会提示其完成设置助理。 安装过程中，系统会提示用户输入其凭据。 用户必须使用与其在 Intune 中的订阅相关联的凭据（即唯一的个人名称或 UPN）。

2. 安装过程中，系统会提示用户输入 Apple ID。 必须提供 Apple ID 才能允许设备安装公司门户。 设置完成后，他们还可以提供 iOS 设置菜单中的 ID。

3. 完成设置后，用户必须从 App Store 安装公司门户应用。

4. 现在用户可以使用在设置设备时使用的 UPN 登录公司门户。

5. 登录后，系统会提示用户注册其设备。 第一步是识别其设备。 应用会提供一份已为公司注册并已被分配到用户的 Intune 帐户的 iOS 设备列表。 他们应选择匹配的设备。 如果该设备还不是公司注册的设备，他们应选择新设备以使用标准注册流程继续操作。

6. 在下一个屏幕上，用户需要确认新设备的序列号。 若要执行此操作，用户需选择出现的链接。 链接将启动“设置”应用，用户便可验证其序列号。 然后用户必须将序列号的最后&4; 个字符输入到公司门户应用中。

   此步骤验证该设备是否是在 Intune 中注册的企业设备。 如果设备上的序列号不匹配，则用户选择了错误的设备。 用户必须返回到上一屏幕并选择其他设备。

7. 验证序列号后，公司门户应用将重定向到公司门户网站以完成注册。 然后该网站会提示用户返回到应用。

注册现已完成，现在用户可以使用此设备的完整功能。

