---
title: "为 iOS 设备设置 Apple School Manager 计划注册"
titlesuffix: Azure portal
description: "了解如何使用 Intune 为公司拥有的 iOS 设备设置 Apple School Manager 计划注册"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: afb3aeff7a7c6cc481d24bac3a61de0816b4d34b
ms.sourcegitcommit: 001577b700f634da2fec0b44af2a378150d1f7ac
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>通过 Apple School Manager 进行 iOS 设备注册

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题旨在帮助你为通过 [Apple School Manager](https://school.apple.com/) 计划购买的设备启用 iOS 设备注册。 通过结合使用 Intune 与 Apple School Manager，可在不触碰设备的情况下注册大量 iOS 设备。 学生或教师打开设备时，“设置助理”使用预先配置的设置运行，并且会注册设备以便进行管理。

若要启用 Apple School Manager 注册，请使用 Intune 和 Apple School Manager 门户。 需要序列号列表或购买订单编号，这样才能将设备分配到 Intune 进行管理。 创建 DEP 注册配置文件，这些配置文件包含注册过程中应用于设备的设置。

另外，Apple School Manager 注册不能与 [Apple 的设备注册计划](device-enrollment-program-enroll-ios.md)或[设备注册管理器](device-enrollment-manager-enroll.md)一起使用。

**必备条件**
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- [MDM 机构](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 用户关联需要 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [了解详细信息](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。
- 从 [Apple School Management](http://school.apple.com) 计划购买的设备

>[!NOTE]
>在具有用户关联的 Apple School Manager 设备上注册期间，多重身份验证 (MFA) 不起作用。 注册之后，MFA 在这些设备上会正常运行。 注册后，MFA 将按预期在设备上运行。 设备无法提示用户在首次登录时需要更改密码。 此外，在注册过程中，密码已过期的用户不会获得重置密码的提示。 用户必须使用其他设备重置密码。

## <a name="get-the-apple-token-and-assign-devices"></a>获取 Apple 令牌并分配设备

必须先从 Apple 获取令牌 (.p7m) 文件，然后才能使用 Apple School Manager 注册公司拥有的 iOS 设备。 使用此令牌，Intune 可以同步有关已加入 Apple School Manager 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。 在 Apple 门户中时，还可分配设备序列号以进行管理。

**步骤 1.下载创建 Apple 令牌所需的 Intune 公钥证书。**<br>
1. 在 [Azure 门户的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册”，然后选择“注册计划令牌”。

  ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/enrollment-program-token-download.png)

2. 在“注册计划令牌”边栏选项卡中，选择“下载公钥”，下载加密密钥 (.pem) 文件，并将其保存在本地。 .pem 文件用于从 Apple School Manager 门户请求信任关系证书。

**步骤 2：下载令牌并分配设备。**<br>
1. 选择“通过 Apple School Manager 创建令牌”，然后使用公司 Apple ID 登录。 可使用此 Apple ID 续订 Apple School Manager 令牌。
2.  在 [Apple School Manager 门户](https://school.apple.com)中，转到“MDM 服务器”，然后选择“添加 MDM 服务器”（右上方）。
3.  输入“MDM 服务器名称”。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。
   ![Apple School Manager 门户的屏幕截图，选中了“序列号”选项](./media/asm-server-assignment.png)

4.  在 Apple 门户中选择“上传文件...”，浏览到 .pem 文件，然后选择“保存 MDM 服务器”（右下方）。
5.  选择“获取令牌”，然后将服务器令牌 (.p7m) 文件下载到计算机。
6. 转到“设备分配”，并通过手动输入“序列号”、“订单编号”来“选择设备”，或“上传 CSV 文件”。
     ![Apple School Manager 门户的屏幕截图，选中了“序列号”选项](./media/asm-device-assignment.png)
7.  选择“分配到服务器”操作，然后选择自己创建的“MDM 服务器”。
8. 指定“选择设备”的方式，然后提供设备信息和详细信息。
9. 选择“分配到服务器”，然后选择为 Microsoft Intune 指定的 &lt;ServerName&gt;，然后选择“确定”。

**步骤 3：输入用于创建 Apple School Manager 令牌的 Apple ID。**<br>该 ID 应用于续订 Apple School Manager 令牌，应保存以供未来参考。

![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/enrollment-program-token-apple-id.png)

**步骤 4：查找并上传你的令牌。**<br>
转到证书 (.p7m) 文件，选择“打开”，然后选择“上传”。 Intune 会自动从 Apple 同步 Apple School Manager 设备。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件
设备注册配置文件定义注册时应用于设备组的设置。

1. 在 Azure 门户的 Intune 中，选择“设备注册”，然后选择“Apple 注册”。
2. 在“注册计划”下，选择“注册计划配置文件”。
3. 在“注册计划配置文件”边栏选项卡上，选择“创建”。
4. 在“创建注册配置文件”边栏选项卡上，输入要在 Intune 中显示的配置文件“名称”和“说明”。
5. 对于“用户关联”，请选择具有此配置文件的设备是否通过用户关联进行注册。

 - 通过用户关联进行注册 - 设置期间将设备与用户关联。

  Apple School Manager 的“Shared iPad”模式要求用户不通过用户关联进行注册。

 - “不通过用户关联进行注册”- 为不属于单个用户的设备（例如共享设备）选择此选项。 为无需访问本地用户数据即可执行任务的设备使用此选项。 公司门户等应用将无法运行。

6. 选择“设备管理设置”。 这些项会在激活时进行设置，并且需要执行恢复出厂设置才能更改。 配置以下配置文件设置，然后选择“保存”：

  ![选择管理模式的屏幕截图。 设备包含以下设置：受到监督、注册锁定、允许配对设置为全部拒绝。 新注册计划配置文件的 Apple Configurator 证书将变灰。](./media/enrollment-program-profile-mode.png)

    - **受到监管** - 默认启用更多的管理选项并已禁用激活锁的管理模式。 如果将此复选框保留为空，则管理功能将受限。

     - 注册锁定 -（需要管理模式 = 受到监督）禁用可能允许删除管理配置文件的 iOS 设置。 如果将此复选框保留为空，它将允许从“设置”菜单中删除管理配置文件。
   - Shared iPad -（要求“不通过用户关联进行注册”和“受监督”模式。）允许多个用户使用托管 Apple ID 登录到已注册的 iPad。 在 Apple School Manager 门户中创建托管的 Apple ID。 了解有关[共享 iPad](education-settings-configure-ios-shared.md) 的详细信息。 还应查看 [Apple 的共享 iPad 要求](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56)。

   >[!NOTE]
   >如果“用户关联”设置为“使用用户关联”或者“受监督”模式设置为“关闭”，则注册配置文件将禁用“Shared iPad”模式。

        - **Maximum Cached Users** - (Requires **Shared iPad** = **Yes**) Creates a partition on the device for each user. The recommended value is the number of students likely to use the device over a period of time. For example, if six students use the device regularly during the week, set this number to six.  

    - **允许配对** - 指定 iOS 设备是否可以与计算机同步。 如果选择“通过证书允许 Apple Configurator”，则必须在“Apple Configurator 证书”下选择证书。

      - Apple Configurator 证书 - 如果在“允许配对”下选择“通过证书允许 Apple Configurator”，请选择要导入的 Apple Configurator 证书。

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
（可选）Apple School Manager 支持使用 Microsoft 学校数据同步 (SDS) 将学籍数据同步到 Azure Active Directory (AD)。 请完成以下步骤以使用 SDS 来同步学校数据。

1. 在“注册计划令牌”边栏选项卡上，选择蓝色的信息横幅或“连接 SDS”。
2. 选择“允许 Microsoft 学校数据同步使用此令牌”，并设置为“允许”。 此设置将允许 Intune 与 Office 365 中的 SDS 连接。
3. 若要允许 Apple School Manager 与 Azure AD 连接，请选择“设置 Microsoft 学校数据同步”。详细了解[如何设置学校数据同步](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1)。
4. 单击“确定”，以保存并继续。

## <a name="sync-managed-devices"></a>同步托管设备
至此，已将管理 Apple School Manager 设备的权限分配给 Intune，接下来可以通过 Apple 服务同步 Intune，以便在 Intune 中查看托管设备。

1. 在 Azure 门户的 Intune 中，选择“设备注册”，然后选择“Apple 注册”。
2. 在“注册计划设备”下，选择“同步”。进度栏显示再次请求同步之前必须等待的时长。
3. 在“同步”边栏选项卡上，选择“请求同步”。进度栏显示再次请求同步之前必须等待的时长。

  ![选中“请求同步”链接的“同步”边栏选项卡屏幕截图。](./media/enrollment-program-device-request-sync.png)

  为了遵从 Apple 有关可接受流量的条款，Intune 规定了以下限制：
   -    每七天只能运行一次完全同步。 无论之前是否同步了序列号，在完全同步时，Intune 都将刷新 Apple 分配给 Intune 的每个序列号。 如果在上一个完全同步的七天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
   -    任何同步请求都在 15 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。

>[!NOTE]
>也可以从“注册计划设备”边栏选项卡向配置文件分配 Apple School Manager 序列号。

## <a name="assign-a-profile-to-devices"></a>为设备分配配置文件
必须先向 Intune 管理的 Apple School Manager 设备分配注册配置文件，然后才能注册设备。

1. 在 Azure 门户中的 Intune 中，选择“设备注册” > “Apple 注册”，然后选择“注册计划配置文件”。
2. 在“注册计划配置文件”列表中，选择要分配给设备的配置文件，然后选择“设备分配”

 ![“设备分配”的屏幕截图，其中选中了“分配”。](./media/enrollment-program-device-assign.png)

3. 选择“分配”，然后选择要向其分配此配置文件的 Apple School Manager 设备。 可以进行筛选来查看可用设备：
  - **未分配**
  - **所有**
  - &lt;配置文件名称&gt;
4. 选择要分配的设备。 列上方的复选框最多可选择 1000 个已列出的设备。 单击“分配”。 若要注册 1000 个以上的设备，请重复分配步骤，直至已向所有设备分配了注册配置文件。

  ![用于在 Intune 中分配注册计划配置文件的“分配”按钮的屏幕截图](media/dep-profile-assignment.png)

## <a name="distribute-devices-to-users"></a>将设备分配给用户

现在可以将公司拥有的设备分发给用户。 打开 iOS Apple School Manager 设备时，它将注册以便由 Intune 管理。 如果设备已激活并处于使用状态，则在将设备恢复出厂设置后才能应用配置文件。
