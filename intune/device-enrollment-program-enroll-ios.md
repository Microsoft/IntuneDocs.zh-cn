---
title: "注册 iOS 设备 - 设备注册计划"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何使用设备注册计划注册企业拥有的 iOS 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 5144b9e7c17a3323667b9ca68cb47829d69866c3
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>使用设备注册计划注册 iOS 设备

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

本主题帮助 IT 管理员注册通过 [Apple 设备注册计划 (DEP)](https://deploy.apple.com) 购买的公司所属的 iOS 设备。 Microsoft Intune 可以无线部署注册 DEP 的注册配置文件，因此管理员不必接触每个托管设备。 DEP 配置文件包含你想要在注册期间应用于设备的管理设置。 注册包包括设备的设置助理选项。

>[!NOTE]
>DEP 注册不能与[设备注册管理器](device-enrollment-manager-enroll.md)共同使用。
>此外，如果用户使用公司门户应用注册其 iOS 设备，然后导入这些设备的序列号并为这些序列号分配了 DEP 配置文件，设备将从 Intune 取消注册。

**DEP 注册步骤**
1. [获取 Apple DEP 令牌](#get-the-apple-dep-certificate)
2. [创建 DEP 配置文件](#create-an-apple-dep-profile)
3. [将 Apple DEP 序列号分配给 Intune 服务器](#assign-apple-dep-serial-numbers-to-your-mdm-server)
4. [同步 DEP 托管的设备](#synchronize-dep-managed-devices)
5. [将 DEP 配置文件分配给设备](#assign-a-dep-profile-to-devices)
6. [将设备分配给用户](#distribute-devices-to-users)

## <a name="get-the-apple-dep-certificate"></a>获取 Apple DEP 证书
使用 Apple 的设备注册计划 (DEP) 注册公司拥有的 iOS 设备之前，需要从 Apple 获取 DEP 证书 (.p7m) 文件。 此令牌允许 Intune 同步有关公司所拥有的且加入了 DEP 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

要使用 DEP 管理公司拥有的 iOS 设备，组织必须加入 Apple DEP 并通过该计划获取设备。 该过程的详细信息，可以通过以下网站获得：https://deploy.apple.com。 该计划的优点包括免手动设置设备，无需通过 USB 电缆将每个设备连接到计算机。

> [!NOTE]
> 如果你的 Intune 租户从 Intune 经典控制台迁移到 Azure 门户，并且在迁移期间从 Intune 管理控制台中删除了 Apple DEP 令牌，则 DEP 令牌可能已被还原到你的 Intune 帐户。 可在 Azure 门户中再次删除 DEP 令牌。

**步骤 1.下载创建 Apple DEP 令牌所需的 Intune 公钥证书。**<br>
1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。 在 Intune 边栏选项卡上，选择“设备注册” > “Apple DEP令牌”。
2. 选择“下载公钥”，本地下载和保存加密密钥 (.pem) 文件。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。

**步骤 2：从相应的 Apple 网站下载 Apple DEP 令牌。**<br>
选择[“通过 Apple 部署计划创建 DEP 令牌”](https://deploy.apple.com) (https://deploy.apple.com) ，并使用公司的 Apple ID 登录。 可使用此 Apple ID 续订 DEP 令牌。

   1.  在 Apple 的[设备注册计划门户](https://deploy.apple.com)中，转到“设备注册计划”&gt;“管理服务器”，然后选择“添加 MDM 服务器”。
   2.  输入“MDM 服务器名称”，然后选择“下一步”。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。
   3.  此时将打开“添加 &lt;服务器名称&gt;”对话框。 选择“选择文件…” 以上传 .pem 文件，然后选择“下一步”。
   4.  “添加 &lt;ServerName&gt;”对话框显示“你的服务器令牌”链接。 将服务器令牌 (.p7m) 文件下载到计算机，然后选择“完成”。

**步骤 3：输入用于创建 Apple DEP 令牌的 Apple ID。此 ID 可以用于续订 Apple DEP 令牌。**

**步骤 4：浏览到要上传的 Apple DEP 令牌。Intune 会自动与 DEP 帐户同步。**<br>
转到证书 (.pem) 文件，选择“打开”，然后选择“上传”。 使用 Push Certificate，Intune 可通过将策略推送到已注册的移动设备来注册和管理 iOS 设备。

## <a name="create-an-apple-dep-profile"></a>创建 Apple DEP 配置文件

设备注册配置文件定义应用于设备组的设置。 以下步骤说明如何为使用 DEP 注册的 iOS 设备创建设备注册配置文件。

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。
2. 在“Intune”边栏选项卡上，选择“设备注册”，然后选择“Apple 注册”。
3. 在“管理 Apple 设备注册计划 (DEP) 设置”下，选择“DEP 配置文件”。
4. 在“Apple DEP 配置文件”边栏选项卡上，选择“创建”。
5. 在“创建注册配置文件”边栏选项卡上，输入配置文件的名称和说明。
6. 对于“用户关联”，请选择具有此配置文件的设备是否通过用户关联进行注册。

 - **通过用户关联注册** - 必须在初始设置过程中将设备与某个用户相关联，然后才能允许此设备访问公司数据和电子邮件。 对属于用户且需要使用公司门户获取服务（如安装应用）的 DEP 托管设备，选择用户关联。 请注意：在具有用户关联的 DEP 设备上注册期间，多重身份验证 (MFA) 不起作用。 注册之后，MFA 在这些设备上会正常运行。 注册 DEP 设备时，需要在首次登录时更改密码的新用户不会获得提示。 此外，在 DEP 注册过程中，密码已过期的用户不会获得重置密码的提示，必须使用其他设备重置密码。

    >[!NOTE]
    >具有用户关联的 DEP 要求启用 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/en-us/library/adfs2-help-endpoints)以请求用户令牌。 [详细了解 WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

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
必须在 Apple DEP Web 门户中向你的 Intune MDM 服务器分配设备序列号才能允许 Intune 管理这些设备。

1. 转到[设备注册计划门户](https://deploy.apple.com) (https://deploy.apple.com) ，然后使用公司 Apple ID 登录。

2. 转到“部署计划”&gt;“设备注册计划”&gt;“管理设备”。

3. 指定**选择设备**的方式，然后提供设备信息并按设备**序列号**、**订单编号**指定详细信息，或**上传 CSV 文件**。

4. 选择“分配到服务器”，然后选择为 Microsoft Intune 指定的 &lt;ServerName&gt;，然后选择“确定”。

## <a name="synchronize-dep-managed-devices"></a>同步 DEP 托管的设备
现已将管理 DEP 设备的权限分配给 Intune，可以通过 DEP 服务同步 Intune，以便在 Intune 门户中查看托管的设备。

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在 Azure 门户的 Intune 边栏选项卡上，选择“设备注册”，然后选择“Apple 注册”。

3. 在“管理 Apple 设备注册计划(DEP)设置”下，选择“DEP 序列号”。

4. 在“Apple DEP 序列号”边栏选项卡上，选择“同步”。

5. 在“同步”边栏选项卡，选择“请求同步”。 进度栏显示再次请求同步之前必须等待的时长。

    为了遵从 Apple 的有关可接受的 DEP 流量的条款，Intune 规定了以下限制：
     -    每七天只运行一次完全的 DEP 同步。 无论之前是否同步了序列号，在完全同步时，Intune 都将刷新 Apple 分配给 Intune 的每个序列号。 如果在上一个完全同步的七天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
     -    任何同步请求都在 10 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。

>[!NOTE]
>还可以从“Apple DEP 序列号”边栏选项卡将 DEP 序列号分配给配置文件。

## <a name="assign-a-dep-profile-to-devices"></a>将 DEP 配置文件分配给设备
必须先向 Intune 托管的 DEP 设备分配 DEP 配置文件，然后再注册设备。

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在Azure 门户的“Intune”边栏选项卡上，选择“设备注册” > “Apple 注册”，然后选择“DEP 配置文件”。

3. 在“Apple DEP 注册配置文件”列表中，选择要分配给设备的配置文件，然后选择“设备分配”

4. 选择“分配”，然后选择要向其分配此配置文件的 DEP 设备。 可以进行筛选来查看 DEP 可用设备：
  - **未分配**
  - **所有**
  - **&lt;DEP 配置文件名称&gt;**

  ![用于在 Intune 门户中分配 DEP 配置文件的“分配”按钮屏幕截图](media/dep-profile-assignment.png)

5. 选择要分配的设备。 列上方的复选框将选中最多 1000 个已列出设备，然后单击“分配”。 若要注册 1000 个以上的设备，请重复分配步骤，直至已向所有设备分配 DEP 配置文件。

## <a name="distribute-devices-to-users"></a>将设备分配给用户

现在可以将公司拥有的设备分发给用户。 打开 iOS DEP 设备时，它将注册为由 Intune 管理。 如果设备已激活并处于使用状态，则在将设备恢复出厂设置后才能应用配置文件。

查看[如何使最终用户了解 Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)。 也可以将最终用户转到[通过 Intune 使用 iOS 或 macOS 设备](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune) 

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>用户如何在其设备上安装和使用公司门户

配置了用户关联的设备可以安装和运行公司门户应用，以下载应用和管理设备。 用户收到设备后，必须完成如下所述的其他步骤，才能完成设置助理并安装公司门户应用。

