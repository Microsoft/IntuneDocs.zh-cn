---
title: "注册 iOS 设备 - 设备注册计划"
titleSuffix: Intune on Azure
description: "了解如何使用“设备注册计划”注册公司拥有的 iOS 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 654a19dd6f1e5f4fd2bda771b0df95b87944db75
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2017
---
# <a name="set-up-ios-device-enrollment-with-device-enrollment-program"></a>使用“设备注册计划”设置 iOS 设备注册

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题旨在帮助 IT 管理员为通过 Apple 的[设备注册计划 (DEP)](https://deploy.apple.com) 购买的设备启用 iOS 设备注册。 Microsoft Intune 可以将注册配置文件“无线”部署到通过 DEP 购买的设备。 管理员始终不需要接触每个受管理设备。 DEP 配置文件包含注册时应用于设备的管理设置，包括“设置助理”选项。

若要启用 DEP 注册，需同时使用 Intune 和 Apple DEP 门户。 另外，还需要 ID 列表或采购订单号，从而可以将其分配到 Intune 以在 Apple 门户中进行管理。

>[!NOTE]
>DEP 注册不能与[设备注册管理器](device-enrollment-manager-enroll.md)共同使用。

**从 Apple 启用注册计划的步骤**
1. [获取 Apple DEP 令牌并分配设备](#get-the-apple-dep-token)
2. [创建注册配置文件](#create-an-apple-enrollment-profile)
3. [同步 DEP 托管的设备](#sync-managed-device)
4. [将 DEP 配置文件分配给设备](#assign-an-enrollment-profile-to-devices)
5. [将设备分配给用户](#end-user-experience-with-managed-devices)

## <a name="get-the-apple-dep-token"></a>获取 Apple DEP 令牌

你需要先从 Apple 获取 DEP 令牌 (.p7m)，然后才可以使用 Apple 的设备注册计划 (DEP) 注册公司拥有的 iOS 设备。 此令牌允许 Intune 同步有关公司所拥有的且加入了 DEP 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

> [!NOTE]
> 如果在迁移到 Azure 前从 Intune 经典控制台删除了此令牌，则 Intune 可能会将已删除的 Apple DEP 令牌还原。 可在 Azure 门户中再次删除 DEP 令牌。 可在 Azure 门户中再次删除 DEP 令牌。

**必备条件**
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 注册 [Apple 的设备注册计划](http://deploy.apple.com)

**步骤 1.下载创建 Apple DEP 令牌所需的 Intune 公钥证书。**<br>
1. 在 Intune 门户中，依次选择“设备注册”、“Apple 注册”和“注册计划令牌”。

  ![Apple 证书工作区中的“注册计划令牌”窗格的屏幕截图。](./media/enrollment-program-token-add.png)

2. 选择“下载公钥”，本地下载和保存加密密钥 (.pem) 文件。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。

  ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/enrollment-program-token-download.png)

**步骤 2：创建和下载 Apple DEP 令牌。**<br>
1. 选择“通过 Apple 设备注册计划创建令牌”以打开 Apple 的部署计划门户，并使用公司 Apple ID 登录。 可使用此 Apple ID 续订 DEP 令牌。

  ![Apple 证书工作区中的“注册计划令牌”窗格的屏幕截图。](./media/enrollment-program-token-create.png)

  ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/enrollment-program-token-sign.png)
2.  在 Apple 的[部署计划门户](https://deploy.apple.com)中，对“设备注册计划”选择“开始使用”。

   ![对“设备注册计划”单击“开始使用”时“注册计划”的屏幕截图。](./media/enrollment-program-token-started.png)

3. 在“管理服务器”页上，选择“添加 MDM 服务器”。
4. 输入“MDM 服务器名称”，然后选择“下一步”。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

   ![为 DEP 添加 MDM 服务器名称并单击“下一步”的屏幕截图。](./media/enrollment-program-token-add-server.png)

5. “添加&lt;服务器名称&gt;”对话框随即打开，提示“上传公钥”。 选择“选择文件…” 以上传 .pem 文件，然后选择“下一步”。

   ![选择公钥文件按钮并单击“下一步”的屏幕截图。](./media/enrollment-program-token-choose-file.png)
6.  “添加 &lt;ServerName&gt;”对话框显示“你的服务器令牌”链接。 将服务器令牌 (.p7m) 文件下载到计算机，然后选择“完成”。
   ![选择公钥文件按钮并单击“下一步”的屏幕截图。](./media/enrollment-program-token-your-token.png)
7. 转到“部署计划”&gt;“设备注册计划”&gt;“管理设备”。
8. 在“选择设备方式”下，指定如何标识设备：
    - **序列号**
    - **订单号**
    - **上传 CSV 文件**。

   ![指定按序列号选择设备、将“选择操作”设置为“分配到服务器”并选择服务器名称的屏幕截图。](./media/enrollment-program-token-specify-serial.png)

9. 在“选择操作”中，选择“分配到服务器”，选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后选择“确认”。 Apple 门户将指定的设备分配到 Intune 服务器以进行管理，然后显示“分配完成”。

   在 Apple 门户中，转到“部署计划”&gt;“设备注册计划”&gt;“查看分配历史记录”，以查看设备及其 MDM 服务器分配的列表。

**步骤 3：输入用于创建注册计划令牌的 Apple ID。**<br>在 Intune 门户中，提供 Apple ID 供未来参考。 使用此 ID 续订注册计划令牌，以避免重新注册所有设备。

![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/enrollment-program-token-apple-id.png)

**步骤 4：浏览到要上传的注册计划令牌。**<br>
转到证书 (.pem) 文件，选择“打开”，然后选择“上传”。 使用 Push Certificate，Intune 可通过将策略推送到已注册的移动设备来注册和管理 iOS 设备。 Intune 会自动与 Apple 同步以查看你的注册计划帐户。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件

设备注册配置文件定义注册时应用于设备组的设置。

1. 在 Intune 门户中，选择“设备注册”，然后选择“Apple 注册”。
2. 在“Apple 的注册计划”下，选择“注册计划配置文件”，然后在“注册计划配置文件”边栏选项卡上选择“创建”。

  ![选择“创建”链接以创建新的注册计划配置文件的屏幕截图。](./media/enrollment-program-profile-create.png)

3. 在“创建注册配置文件”边栏选项卡上，输入配置文件的“名称”和“说明”以用作管理用途。 用户看不到这些详细信息。

  ![指定名称和说明并为新注册计划配置文件选择“通过用户关联注册”的屏幕截图。](./media/enrollment-program-profile-name.png)
对于“用户关联”，请选择具有此配置文件的设备是否通过用户关联进行注册。

 - “通过用户关联注册” - 用户在设置过程中将与设备相关联，然后可允许访问公司数据和电子邮件。 对属于用户且需要使用公司门户获取服务（如安装应用）的设备，选择“用户关联”。

 > [!NOTE]
 > 在具有用户关联的注册计划托管的设备上进行注册期间，多重身份验证 (MFA) 不起作用。 注册之后，MFA 在这些设备上会正常运行。 注册设备时，需要在首次登录时更改密码的新用户不会获得提示。 此外，在注册过程中，密码已过期的用户不会获得重置密码的提示，必须使用其他设备重置密码。

 >[!NOTE]
 >通过用户关联进行注册计划管理要求启用 [WS-Trust 1.3 Username/Mixed endpoint](https://technet.microsoft.com/library/adfs2-help-endpoints) 终结点以请求用户令牌。 [详细了解 WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

 - **不通过用户关联注册** - 该设备不与用户关联。 将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户隶属关系的应用（包括用于安装业务线应用的公司门户应用）无法运行。

4. 选择“设备管理设置”，以配置以下配置文件设置：

  ![选择管理模式的屏幕截图。 设备包含以下设置：受到监管、注册锁定、允许配对设置为全部拒绝。 新注册计划配置文件的 Apple Configurator 证书将变灰。](./media/enrollment-program-profile-mode.png)
    - **受到监管** - 默认启用更多的管理选项并已禁用激活锁的管理模式。 如果将此复选框保留为空，则管理功能将受限。

    - **注册锁定** -（需要管理模式 = 受到监督）禁用可能允许删除管理配置文件的 iOS 设置。 如果将此复选框保留为空，它将允许从“设置”菜单中删除管理配置文件。 注册设备后，除非将设备恢复出厂设置，否则无法更改此设置。

    - **允许配对** - 指定 iOS 设备是否可以与计算机同步。 如果选择“通过证书允许 Apple Configurator”，则必须在“Apple Configurator 证书”下选择证书。

    - **Apple Configurator 证书** - 如果在“允许配对”下选择“通过证书允许 Apple Configurator”，请选择要导入的 Apple Configurator 证书。

  选择“保存”。

5. 选择“设置助理设置”，配置以下配置文件设置：

  ![通过新注册计划配置文件的可用设置选择配置设置的屏幕截图。](./media/enrollment-program-profile-settings.png)
    - **部门名称** - 用户在激活过程中点击“关于配置”时显示。

    - **部门电话** - 用户在激活过程中单击“需要帮助”按钮时显示。
    - **设置助理选项** - 这些可选设置可以稍后在 iOS 的“设置”菜单中设置。
        - **密码** - 在激活过程中提示输入密码。 始终需要密码，除非设备受到保护，或以某种其他方式控制访问权限。 例如，展台模式限制设备只可使用一个应用。
        - **定位服务** - 如果启用，在激活过程中设置助手会提示此服务
        - **还原** - 如果启用，在激活过程中设置助手会提示进行 iCloud 备份
        - **Apple ID** - 如果启用，Intune 在没有 ID 的情况下尝试安装应用时，iOS 将提示用户提供 Apple ID。 下载 iOS App Store 应用（包括由 Intune 安装的应用）时需要 Apple ID。
        - **条款和条件** - 如果启用，在激活过程中设置助手会提示用户接受 Apple 的条款和条件
        - **Touch ID** - 如果启用，在激活过程中设置助手会提示此服务
        - **Apple Pay** - 如果启用，在激活过程中设置助手会提示此服务
        - **Zoom** - 如果启用，在激活过程中设置助手会提示此服务
        - **Siri** - 如果启用，在激活过程中设置助手会提示此服务
        - **诊断数据** - 如果启用，在激活过程中设置助手会提示此服务

    选择“保存”。
9. 若要保存配置文件设置，请在“创建注册配置文件”边栏选项卡上选择“创建”。 注册配置文件显示在 Apple 注册计划注册配置文件列表中。

## <a name="sync-managed-devices"></a>同步托管设备
现在 Intune 拥有管理设备的权限，你可以将 Intune 与 Apple 同步，以在 Intune 门户中查看托管的设备。

1. 在 Intune 门户中，选择“设备注册”&gt;“Apple 注册”&gt;“注册计划设备”。
2. 在“注册计划设备”下，选择“同步”。 将出现“同步”边栏选项卡。

  ![选中“注册计划设备”节点和选中“同步”链接的屏幕截图。](./media/enrollment-program-device-sync.png)
3. 在“同步”边栏选项卡，选择“请求同步”。 进度栏显示再次请求同步之前必须等待的时长。

  ![选中“请求同步”链接的“同步”边栏选项卡屏幕截图。](./media/enrollment-program-device-request-sync.png)

  为了遵从 Apple 的有关可接受的注册计划流量的条款，Intune 规定了以下限制：
     -  每七天只能运行一次完全同步。 在完全同步期间，Intune 将刷新分配给 Intune 的每一个 Apple 序列号。 如果在上一个完全同步的七天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
     -  任何同步请求都在 15 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。
     - Intune 每 24 小时与 Apple 同步一次新设备及已删除设备。
     
4. 在“注册计划设备”工作区中，选择“刷新”以查看设备。

## <a name="assign-an-enrollment-profile-to-devices"></a>将注册配置文件分配到设备
必须先向设备分配注册计划配置文件才能注册他们。

>[!NOTE]
>还可以从“Apple 序列号”边栏选项卡将序列号分配给配置文件。

1. 在 Intune 门户中，选择“设备注册” > “Apple 注册”，然后选择“注册计划配置文件”。
2. 在“注册计划配置文件”列表中，选择要分配给设备的配置文件，然后选择“分配设备”。

 ![选中“请求同步”链接的“同步”边栏选项卡屏幕截图。](./media/enrollment-program-device-assign.png)

3. 选择“分配”，然后选择要向其分配此配置文件的设备。 可以进行筛选来查看可用设备：
  - **未分配**
  - **所有**
  - &lt;配置文件名称&gt;
4. 选择要分配的设备。 列上方的复选框将选中最多 1000 个已列出设备，然后单击“分配”。 若要注册 1000 个以上的设备，请重复分配步骤，直至已向所有设备分配了注册配置文件。

  ![用于在 Intune 门户中分配注册计划配置文件的“分配”按钮屏幕截图](media/dep-profile-assignment.png)

## <a name="end-user-experience-with-managed-devices"></a>托管设备的最终用户体验

现在可以将设备分配给用户。 具有用户关联的设备需要每个用户都分配有 Intune 许可证。 已激活设备只有恢复出厂设置才能应用注册配置文件。 如果打开注册计划托管的 iOS 设备，用户将在设备上看到以下选项：  

1. 设置 iOS 设备 - 用户可从以下选项中选择：
  - 设置为新设备
  - 从 iCloud 备份中还原
  - 从 iTunes 备份中还原
2. 通知用户“&lt;你的组织&gt;将自动配置你的设备”。 还提供了以下其他配置详细信息：

  配置允许&lt;你的组织&gt;无线管理此设备。

  管理员可以帮助你设置电子邮件和网络帐户、安装和配置应用以及远程管理设置。

  管理员可能禁用功能、安装和删除应用、监视和限制你的 Internet 流量以及远程擦除此设备。

  配置由<br> &lt;你的组织 &gt;iOS 团队提供<br> &lt;地址&gt;

3. 提示用户输入其工作或学校用户名和密码。
4. 提示用户输入其 Apple ID。 安装 Intune 公司门户应用和其他应用时需要 Apple ID。 提供凭据后，设备将安装无法删除的管理配置文件。 Intune 管理配置文件显示在设备的“设置” > “通用” > “设备管理”中。

用户现在可以使用 Intune 公司门户或 Apple 设置助理完成设置其公司拥有的设备。
