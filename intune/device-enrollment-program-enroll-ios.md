---
title: "注册 iOS 设备 - 设备注册计划"
titleSuffix: Intune on Azure
description: "了解如何使用“设备注册计划”注册公司拥有的 iOS 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d88d191e3212e1999376fb2577a85c3dc957a787
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>通过 Apple 设备注册计划自动注册 iOS 设备

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题旨在帮助你为通过 Apple [设备注册计划 (DEP)](https://deploy.apple.com) 购买的设备启用 iOS 设备注册。 可在不触碰设备的情况下为大量设备启用 DEP 注册。 可将 iPhone 和 iPad 等设备直接运送到用户手中。 用户打开设备时，“设置助理”将运行预先配置的设置，设备将注册以便进行管理。

若要启用 DEP 注册，需同时使用 Intune 和 Apple DEP 门户。 需要序列号列表或购买订单编号，这样才能将设备分配到 Intune 进行管理。 创建 DEP 注册配置文件，这些配置文件包含注册过程中应用于设备的设置。

另外，DEP 注册不能与[设备注册管理器](device-enrollment-manager-enroll.md)一起使用。

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>先决条件
- 通过 [Apple 设备注册计划](http://deploy.apple.com)购买的设备
- [MDM 机构](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 用户关联需要 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [了解详细信息](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

> [!NOTE]
> 在为用户关联设置 DEP 注册期间，多重身份验证 (MFA) 不起作用。 注册后，MFA 将按预期在设备上运行。 设备无法提示用户在首次登录时需要更改密码。 此外，在注册过程中，密码已过期的用户不会获得重置密码的提示。 用户必须使用其他设备重置密码。

## <a name="get-the-apple-dep-token"></a>获取 Apple DEP 令牌

必须先从 Apple 获得 DEP 令牌 (.p7m) 文件，然后才能通过 DEP 注册 iOS 设备。 此令牌允许 Intune 同步有关公司所拥有的 DEP 设备的信息。 还允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

可使用 Apple DEP 门户创建 DEP 令牌。 还可以使用 DEP 门户将设备分配到 Intune 进行管理。

> [!NOTE]
> 如果在迁移到 Azure 前从 Intune 经典控制台删除了此令牌，则 Intune 可能会将已删除的 Apple DEP 令牌还原。 可在 Azure 门户中再次删除 DEP 令牌。 可在 Azure 门户中再次删除 DEP 令牌。

**步骤 1.下载创建 Apple DEP 令牌所需的 Intune 公钥证书。**<br>

1. 在 Azure 门户中的 Intune 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”。

  ![Apple 证书工作区中的“注册计划令牌”窗格的屏幕截图。](./media/enrollment-program-token-add.png)

2. 选择“下载公钥”，将加密密钥 (.pem) 文件下载到本地并保存。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。

  ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/enrollment-program-token-download.png)

**步骤 2：创建和下载 Apple DEP 令牌。**<br>
1. 选择“通过 Apple 设备注册计划创建令牌”，打开 Apple 部署计划门户，并使用公司 Apple ID 登录。 可使用此 Apple ID 续订 DEP 令牌。
2.  在 Apple [部署计划门户](https://deploy.apple.com)中，对“设备注册计划”选择“开始”。

3. 在“管理服务器”页上，选择“添加 MDM 服务器”。
4. 输入“MDM 服务器名称”，然后选择“下一步”。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

   ![为 DEP 添加 MDM 服务器名称并单击“下一步”的屏幕截图。](./media/enrollment-program-token-add-server.png)

5. “添加&lt;服务器名称&gt;”对话框随即打开，提示“上传公钥”。 选择“选择文件…” 以上传 .pem 文件，然后选择“下一步”。

6.  “添加 &lt;ServerName&gt;”对话框显示“你的服务器令牌”链接。 将服务器令牌 (.p7m) 文件下载到计算机，然后选择“完成”。

7. 转到“部署计划”&gt;“设备注册计划”&gt;“管理设备”。
8. 在“选择设备方式”下，指定如何标识设备：
    - **序列号**
    - **订单号**
    - **上传 CSV 文件**。

   ![指定按序列号选择设备、将“选择操作”设置为“分配到服务器”并选择服务器名称的屏幕截图。](./media/enrollment-program-token-specify-serial.png)

9. 对于“选择操作”，选择“分配到服务器”，选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后选择“确定”。 Apple 门户将指定的设备分配到 Intune 服务器以进行管理，然后显示“分配完成”。

   在 Apple 门户中，转到“部署计划”&gt;“设备注册计划”&gt;“查看分配历史记录”，以查看设备及其 MDM 服务器分配的列表。

**步骤 3：输入用于创建注册计划令牌的 Apple ID。**<br>在 Azure 门户中的 Intune 中，提供 Apple ID 供未来参考。 使用此 ID 在未来续订注册计划令牌，避免重新注册所有设备。

![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/enrollment-program-token-apple-id.png)

**步骤 4：浏览到要上传的注册计划令牌。**<br>
转到证书 (.pem) 文件，选择“打开”，然后选择“上传”。 使用 Push Certificate，Intune 可通过将策略推送到已注册的移动设备来注册和管理 iOS 设备。 Intune 会自动与 Apple 同步以查看你的注册计划帐户。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件

已经安装了令牌，现在可以为 DEP 设备创建注册配置文件。 设备注册配置文件定义注册时应用于设备组的设置。

1. 在 Azure 门户中的 Intune 中，选择“设备注册” > “Apple 注册”。
2. 在“Apple 注册计划”下，选择“注册计划配置文件” > “创建”。
3. 在“创建注册配置文件”上，输入配置文件的“名称”和“说明”进行管理。 用户看不到这些详细信息。 可以使用此“名称”字段在 Azure Active Directory 中创建动态组。 使用配置文件名称定义 enrollmentProfileName 参数，以向设备分配此注册配置文件。 详细了解 [Azure Active Directory 动态组](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)。

  对于“用户关联”，选择具有此配置文件的设备是否通过已分配的用户进行注册。

 - 通过用户关联进行注册 - 为属于用户且需要使用公司门户获取服务（如安装应用）的设备选择此选项。

 - 不通过用户关联进行注册 - 为不属于单个用户的设备选择此选项。 为无需访问本地用户数据即可执行任务的设备使用此选项。 公司门户等应用将无法运行。

4. 选择“设备管理设置”，配置以下配置文件设置：

  ![选择管理模式的屏幕截图。 设备包含以下设置：受到监管、注册锁定、允许配对设置为全部拒绝。 新注册计划配置文件的 Apple Configurator 证书将变灰。](./media/enrollment-program-profile-mode.png)
    - **受到监管** - 默认启用更多的管理选项并已禁用激活锁的管理模式。 如果将此复选框保留为空，则管理功能将受限。

    - **注册锁定** -（需要管理模式 = 受到监督）禁用可能允许删除管理配置文件的 iOS 设置。 如果将此复选框保留为空，它将允许从“设置”菜单中删除管理配置文件。 注册设备后，除非将设备恢复出厂设置，否则无法更改此设置。

    - **允许配对** - 指定 iOS 设备是否可以与计算机同步。 如果选择“通过证书允许 Apple Configurator”，则必须在“Apple Configurator 证书”下选择证书。

    - Apple Configurator 证书 - 如果在“允许配对”下选择“通过证书允许 Apple Configurator”，请选择要导入的 Apple Configurator 证书。

  选择“保存”。

5. 选择“设置助理设置”，配置以下配置文件设置：

  ![通过新注册计划配置文件的可用设置选择配置设置的屏幕截图。](./media/enrollment-program-profile-settings.png)
    - **部门名称** - 用户在激活过程中点击“关于配置”时显示。

    - **部门电话** - 用户在激活过程中单击“需要帮助”按钮时显示。
    - **设置助理选项** - 这些可选设置可以稍后在 iOS 的“设置”菜单中设置。
        - **密码**
        - **位置服务**
        - **还原**
        - **Apple ID**
        - **条款和条件**
        - **Touch ID**
        - **Apple Pay**
        - **缩放**
        - **Siri**
        - **诊断数据**

    选择“保存”。
9. 若要保存配置文件设置，请在“创建注册配置文件”边栏选项卡上选择“创建”。 注册配置文件显示在 Apple 注册计划注册配置文件列表中。

## <a name="sync-managed-devices"></a>同步托管设备
Intune 已拥有管理设备的权限，现在可以将 Intune 与 Apple 同步，以在 Azure 门户的 Intune 中查看托管设备。

1. 在 Azure 门户中的 Intune 中，选择“设备注册” >  “Apple 注册” > “注册计划设备”。
2. 在“注册计划设备”下，选择“同步”。

  ![选中“注册计划设备”节点和选中“同步”链接的屏幕截图。](./media/enrollment-program-device-sync.png)
3. 在“同步”边栏选项卡上，选择“请求同步”。 进度栏显示再次请求同步之前必须等待的时长。

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

1. 在 Azure 门户中的 Intune 中，选择“设备注册” > “Apple 注册”，然后选择“注册计划配置文件”。
2. 在“注册计划配置文件”列表中，选择要分配给设备的配置文件，然后选择“分配设备”。

 ![“设备分配”的屏幕截图，其中选中了“分配”。](./media/enrollment-program-device-assign.png)

3. 选择“分配”，然后选择要向其分配此配置文件的设备。 可以进行筛选来查看可用设备：
  - **未分配**
  - **所有**
  - &lt;配置文件名称&gt;
4. 选择要分配的设备。 列上方的复选框将选中最多 1000 个已列出设备，然后单击“分配”。 若要注册 1000 个以上的设备，请重复分配步骤，直至已向所有设备分配了注册配置文件。

  ![用于在 Intune 中分配注册计划配置文件的“分配”按钮的屏幕截图](media/dep-profile-assignment.png)

## <a name="distribute-devices"></a>分配设备
已经在 Apple 和 Intune 之间启用了管理和同步，并且分配了注册 DEP 设备所需的配置文件。 现在可以将设备分配给用户。 具有用户关联的设备需要每个用户都分配有 Intune 许可证。 没有用户关联的设备需要设备许可证。 已激活设备只有恢复出厂设置才能应用注册配置文件。

请参阅[通过设备注册计划在 Intune 中注册 iOS 设备](/intune-user-help/enroll-your-device-dep-ios)。
