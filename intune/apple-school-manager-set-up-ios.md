---
title: "为 iOS 设备设置 Apple School Manager 计划注册"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 为公司拥有的 iOS 设备设置 Apple School Manager 计划注册"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73556209c88759ffe0747d9927cbcbb49600e0c0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>通过 Apple School Manager 进行 iOS 设备注册

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题旨在帮助 IT 管理员为通过 [Apple School Manager](https://school.apple.com/) (ASM) 计划购买的设备进行 iOS 设备注册。 Microsoft Intune 可以通过“无线方式”部署注册配置文件，该配置文件会注册 ASM 设备来对其进行管理。 管理员始终不需要接触每个受管理设备。 ASM 配置文件包含注册时应用于设备的管理设置，包括“设置助理”选项。

**ASM 注册步骤**
1. [获取 ASM 令牌并分配设备](#get-the-asm-token-and-assign-devices)
2. [创建注册配置文件](#create-an-apple-enrollment-profile)
3. [连接学校数据同步](#connect-school-data-sync)（可选）
4. [同步 ASM 受管理设备](#sync-asm-managed-devices)
5. [将 ASM 配置文件分配给设备](#assign-an-asm-profile-to-devices)
6. [将设备分配给用户](#distribute-devices-to-users)

>[!NOTE]
>ASM 注册不能与 Apple 的[设备注册计划 (DEP)](device-enrollment-program-enroll-ios.md) 或 Intune 的[设备注册管理器](device-enrollment-manager-enroll.md)帐户一起使用。

## <a name="get-the-apple-asm-token-and-assign-devices"></a>获取 Apple ASM 令牌并分配设备

使用 Apple School Manager (ASM) 注册公司拥有的 iOS 设备之前，需要从 Apple 获取 ASM 令牌 (.p7m) 文件。 使用此令牌，Intune 可以同步有关已加入 ASM 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。 在 Apple 门户中时，还可分配设备序列号以进行管理。

**必备条件**
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 已注册 [Apple School Management](http://school.apple.com)

**步骤 1.下载创建 Apple ASM 令牌所需的 Intune 公钥证书。**<br>
1. 在 Azure [Intune 门户](https://aka.ms/intuneportal)中，选择“设备注册”，然后选择“注册计划令牌”。
2. 在“注册计划令牌”边栏选项卡中，选择“下载公钥”，以本地下载和保存加密密钥 (.pem) 文件。 .pem 文件用于从 Apple School Manager 门户请求信任关系证书。

**步骤 2：下载 ASM 令牌并分配设备。**<br>
选择“通过 Apple School Manager 创建令牌”，然后通过公司 Apple ID 登录。 可使用此 Apple ID 续订 ASM 令牌。

   1.  在 [Apple School Manager 门户](https://school.apple.com)中，转到“MDM 服务器”，然后选择“添加 MDM 服务器”（右上方）。
   2.  输入“MDM 服务器名称”。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。
   3.  在 Apple 门户中选择“上传文件...”，浏览到 .pem 文件，然后选择“保存 MDM 服务器”（右下方）。
   4.  选择“获取令牌”，然后将服务器令牌 (.p7m) 文件下载到计算机。
   5. 转到“设备分配”，并通过手动输入“序列号”、“订单编号”来“选择设备”，或“上传 CSV 文件”。
   6.   选择“分配到服务器”操作，然后选择自己创建的“MDM 服务器”。
   7. 指定**选择设备**的方式，然后提供设备信息并按设备**序列号**、**订单编号**指定详细信息，或**上传 CSV 文件**。
   8. 选择“分配到服务器”，然后选择为 Microsoft Intune 指定的 &lt;ServerName&gt;，然后选择“确定”。

**步骤 3：输入用于创建 ASM 令牌的 Apple ID。**<br>该 ID 应用于续订 Apple ASM 令牌并应将其存储以供日后参考。

**步骤 4：查找并上传你的令牌。**<br>
转到证书 (.p7m) 文件，选择“打开”，然后选择“上传”。 Intune 会自动从 Apple 中同步你的 ASM 设备。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件
设备注册配置文件定义注册时应用于设备组的设置。

1. 在 Intune 门户中，选择“设备注册”，然后选择“Apple 注册”。
2. 在“注册计划”下，选择“注册计划配置文件”。
3. 在“注册计划配置文件”边栏选项卡上，选择“创建”。
4. 在“创建注册配置文件”边栏选项卡上，输入要在 Intune 门户中显示的配置文件“名称”和“说明”。
5. 对于“用户关联”，请选择具有此配置文件的设备是否通过用户关联进行注册。

 - **通过用户关联注册** - 必须在初始设置过程中将设备与某个用户相关联，然后才能允许此设备访问公司数据和电子邮件。 为用户使用其托管 Apple ID 登录的 ASM 受管理设备选择用户关联。

 >[!NOTE]
 >在具有用户关联的 ASM 设备上注册期间，多重身份验证 (MFA) 不起作用。 注册之后，MFA 在这些设备上会正常运行。

  Apple School Manager 的“Shared iPad”模式要求用户通过用户关联注册。

 >[!NOTE]
    >具有用户关联的 ASM 必须启用 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)，才可以请求用户令牌。 [详细了解 WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

 - **不通过用户关联注册** - 该设备不与用户关联。 将此隶属关系用于无需访问本地用户数据即可执行任务的设备。 需要用户关联的应用（包括用于安装业务线应用的公司门户应用）无法运行。

6. 选择“设备管理设置”。 这些项会在激活时进行设置，并且需要执行恢复出厂设置才能更改。 配置以下配置文件设置，然后选择“保存”：

    - **受到监管** - 默认启用更多的管理选项并已禁用激活锁的管理模式。 如果将此复选框保留为空，则管理功能将受限。

    - **注册锁定** -（需要管理模式 = 受到监督）禁用可能允许删除管理配置文件的 iOS 设置。 如果将此复选框保留为空，它将允许从“设置”菜单中删除管理配置文件。

  - **Shared iPad** - （要求“通过用户关联注册”和“受到监管”模式。）允许多个用户使用托管的 Apple ID 登录到已注册的 iPad。 在 Apple School Manager 门户中创建托管的 Apple ID。

  >[!NOTE]
  >如果配置文件中启用了“Shared iPad”模式，并且已将“用户关联”或“受到监管”模式设置为“关闭”，则注册配置文件将禁用“Shared iPad”模式。

  - **最大缓存用户数** - （要求“Shared iPad” = “是”）将在设备上为每个用户创建一个分区。 建议值是在某个时间段内可能使用此设备的学生人数。 例如，如果 6 个学生在一周内定期使用此设备，则将此数值设置为 6。  

    - **允许配对** - 指定 iOS 设备是否可以与计算机同步。 如果选择“通过证书允许 Apple Configurator”，则必须在“Apple Configurator 证书”下选择证书。

    - **Apple Configurator 证书** - 如果在“允许配对”下选择“通过证书允许 Apple Configurator”，请选择要导入的 Apple Configurator 证书。

7. 选择“设置助理设置”，配置以下配置文件设置，然后选择“保存”：

    - **部门名称** - 用户在激活过程中点击“关于配置”时显示。

    - **部门电话** - 用户在激活过程中单击“需要帮助”按钮时显示。
    - **设置助理选项** - 如果在“设置助理”选项中将这些设置排除在外，则可稍后在 iOS 的“设置”菜单中设置它们。
        - **密码** - 在激活过程中提示输入密码。 始终需要密码，除非设备受到保护，或以某种其他方式（即限制设备只可使用一个应用的展台模式）控制访问权限。
        - **定位服务** - 如果启用，在激活过程中设置助手会提示此服务
        - **还原** - 如果启用，在激活过程中设置助手会提示进行 iCloud 备份
        - **Apple ID** - 如果启用，Intune 在没有 ID 的情况下尝试安装应用时，iOS 将提示用户提供 Apple ID。 下载 iOS 应用商店应用（包括由 Intune 安装的应用）时需要 Apple ID。
        - **条款和条件** - 如果启用，在激活过程中设置助手会提示用户接受 Apple 的条款和条件
        - **Touch ID** - 如果启用，在激活过程中设置助手会提示此服务
        - **Apple Pay** - 如果启用，在激活过程中设置助手会提示此服务
        - **Zoom** - 如果启用，在激活过程中设置助手会提示此服务
        - **Siri** - 如果启用，在激活过程中设置助手会提示此服务
        - **诊断数据** - 如果启用，在激活过程中设置助手会提示此服务

8. 若要保存配置文件设置，请在“创建注册配置文件”边栏选项卡上选择“创建”。

## <a name="connect-school-data-sync"></a>连接学校数据同步
（可选）ASM 支持使用 Microsoft 学校数据同步 (SDS) 将学籍数据同步到 Azure Active Directory (AD)。 请完成以下步骤以使用 SDS 来同步学校数据。

1. 在“注册计划令牌”边栏选项卡上，选择蓝色的信息横幅或“连接 SDS”。
2. 选择“允许 Microsoft 学校数据同步使用此令牌”，并设置为“允许”。 此设置将允许 Intune 与 Office 365 中的 SDS 连接。
3. 若要允许 ASM 与 Azure AD 连接，请选择“设置 Microsoft 学校数据同步”。 详细了解[如何设置学校数据同步](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1)。
4. 单击“确定”，以保存并继续。

## <a name="sync-asm-managed-devices"></a>同步 ASM 受管理设备
至此，已将管理 ASM 设备的权限分配给 Intune，接下来可以通过 ASM 服务同步 Intune，以便在 Intune 门户中查看受管理设备。

1. 在 Intune 门户中，选择“设备注册”，然后选择“Apple 注册”。
2. 在“注册计划设备”下，选择“同步”。 进度栏显示再次请求同步之前必须等待的时长。

    为了遵从 Apple 有关可接受的 ASM 流量的条款，Intune 规定了以下限制：
     -  每七天只运行一次完全的 ASM 同步。 无论之前是否同步了序列号，在完全同步时，Intune 都将刷新 Apple 分配给 Intune 的每个序列号。 如果在上一个完全同步的七天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
     -  任何同步请求都在 15 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。

>[!NOTE]
>也可以从“注册计划设备”边栏选项卡向配置文件分配 ASM 序列号。

## <a name="assign-an-asm-profile-to-devices"></a>将 ASM 配置文件分配给设备
必须先向 Intune 托管的 ASM 设备分配 ASM 配置文件，然后再注册设备。

1. 在 Intune 门户中，选择“设备注册” > “Apple 注册”，然后选择“注册计划配置文件”。
2. 在“注册计划配置文件”列表中，选择要分配给设备的配置文件，然后选择“设备分配”
3. 选择“分配”，然后选择要向其分配此配置文件的 ASM 设备。 可以进行筛选来查看 ASM 可用设备：
  - **未分配**
  - **所有**
  - **&lt;ASM 配置文件名称&gt;**
4. 选择要分配的设备。 列上方的复选框最多可选择 1000 个已列出的设备。 单击“分配”。 若要注册 1000 个以上的设备，请重复分配步骤，直至已向所有设备分配了 ASM 配置文件。

## <a name="distribute-devices-to-users"></a>将设备分配给用户

现在可以将公司拥有的设备分发给用户。 打开 iOS ASM 设备时，它将注册为由 Intune 管理。 如果设备已激活并处于使用状态，则在将设备恢复出厂设置后才能应用配置文件。

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>用户如何在其设备上安装和使用公司门户

配置了用户关联的设备可以安装和运行公司门户应用，以下载应用和管理设备。 用户收到设备后，必须运行设置助理并安装公司门户应用。
