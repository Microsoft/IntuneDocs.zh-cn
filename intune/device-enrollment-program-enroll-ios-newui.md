---
title: "注册 iOS 设备 - 设备注册计划"
titlesuffix: Azure portal
description: "了解如何使用“设备注册计划（新 UI）”注册公司拥有的 iOS 设备。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 48b74b81c9f3f8b9c936ae22a343ccfb565b4ec1
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2018
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>通过 Apple 设备注册计划自动注册 iOS 设备

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>用户界面临时差异
> 本页所述功能的用户界面正在进行更新。 这些更新将于四月末在所有用户帐户中推出。
>
> 如果“设备注册”页如下图所示，则用户界面已更新，可以使用此帮助页面。
>
> ![新用户界面](./media/appleenroll-newui.png)
>
> 反之，如果“设备注册”页如下图所示，则帐户尚未更新到新的用户界面。 请转到[此帮助页面](device-enrollment-program-enroll-ios.md)。
>
> ![旧用户界面](./media/appleenroll-oldui.png)

本主题旨在帮助你为通过 Apple [设备注册计划 (DEP)](https://deploy.apple.com) 购买的设备启用 iOS 设备注册。 可在不触碰设备的情况下为大量设备启用 DEP 注册。 可将 iPhone 和 iPad 等设备直接运送到用户手中。 用户打开设备时，“设置助理”将运行预先配置的设置，设备将注册以便进行管理。

若要启用 DEP 注册，需同时使用 Intune 和 Apple DEP 门户。 需要序列号列表或购买订单编号，这样才能将设备分配到 Intune 进行管理。 创建 DEP 注册配置文件，这些配置文件包含注册过程中应用于设备的设置。

另外，DEP 注册不能与[设备注册管理器](device-enrollment-manager-enroll.md)一起使用。

## <a name="what-is-supervised-mode"></a>受监督模式简介
Apple 在 iOS 5 中引入了受监督模式。 处于受监督模式的 iOS 设备可通过更多控件进行管理。 因此，此模式尤其适用于企业拥有的设备。 在 Apple 设备注册计划 (DEP) 中，Intune 支持将设备配置为受监督模式。 

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>必备条件
- 通过 [Apple 设备注册计划](http://deploy.apple.com)购买的设备
- [MDM 机构](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>获取 Apple DEP 令牌

必须先从 Apple 获得 DEP 令牌 (.p7m) 文件，然后才能通过 DEP 注册 iOS 设备。 此令牌允许 Intune 同步有关公司所拥有的 DEP 设备的信息。 还允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

可使用 Apple DEP 门户创建 DEP 令牌。 还可以使用 DEP 门户将设备分配到 Intune 进行管理。

> [!NOTE]
> 如果在迁移到 Azure 前从 Intune 经典门户删除了令牌，Intune 可能会还原已删除的 Apple DEP 令牌。 可在 Azure 门户中再次删除 DEP 令牌。 可在 Azure 门户中再次删除 DEP 令牌。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>步骤 1。 下载创建令牌所需的 Intune 公钥证书。

1. 在 Azure 门户的 Intune 中，选择“设备注册” > “Apple 注册” > “注册计划令牌” > “添加”。

    ![获取注册计划令牌。](./media/device-enrollment-program-enroll-ios/image01.png)

2. 选择“下载公钥”，将加密密钥 (.pem) 文件下载到本地并保存。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。
  ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>步骤 2。 使用密钥从 Apple 下载令牌。

1. 选择“创建 Apple 设备注册计划令牌”，以打开 Apple 部署计划门户，并使用公司 Apple ID 登录。 可使用此 Apple ID 续订 DEP 令牌。
2.  在 Apple [部署计划门户](https://deploy.apple.com)中，对“设备注册计划”选择“开始”。

3. 在“管理服务器”页上，选择“添加 MDM 服务器”。
4. 输入“MDM 服务器名称”，然后选择“下一步”。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

5. “添加&lt;服务器名称&gt;”对话框随即打开，提示“上传公钥”。 选择“选择文件…” 以上传 .pem 文件，然后选择“下一步”。

6. 转到“部署计划”&gt;“设备注册计划”&gt;“管理设备”。
7. 在“选择设备方式”下，指定如何标识设备：
    - **序列号**
    - **订单号**
    - **上传 CSV 文件**。

   ![指定按序列号选择设备、将“选择操作”设置为“分配到服务器”并选择服务器名称的屏幕截图。](./media/enrollment-program-token-specify-serial.png)

8. 对于“选择操作”，选择“分配到服务器”，选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后选择“确定”。 Apple 门户将指定的设备分配到 Intune 服务器以进行管理，然后显示“分配完成”。

   在 Apple 门户中，转到“部署计划”&gt;“设备注册计划”&gt;“查看分配历史记录”，以查看设备及其 MDM 服务器分配的列表。

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>步骤 3. 保存用于创建此令牌的 Apple ID。

在 Azure 门户中的 Intune 中，提供 Apple ID 供未来参考。

![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>步骤 4. 上传令牌。
在“Apple 令牌”框中，浏览到证书 (.pem) 文件，选择“打开”，然后选择“创建”。 使用 Push Certificate，Intune 可通过将策略推送到已注册的移动设备来注册和管理 iOS 设备。 Intune 会自动与 Apple 同步以查看你的注册计划帐户。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件

已经安装了令牌，现在可以为 DEP 设备创建注册配置文件。 设备注册配置文件定义注册时应用于设备组的设置。

1. 在 Azure 门户中的 Intune 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”。
2. 选择令牌，选择“配置文件”，然后选择“创建配置文件”。
    ![创建配置文件屏幕截图。](./media/device-enrollment-program-enroll-ios/image04.png)
3. 在“创建配置文件”下，输入配置文件的“名称”和“描述”以便于管理。 用户看不到这些详细信息。 可以使用此“名称”字段在 Azure Active Directory 中创建动态组。 使用配置文件名称定义 enrollmentProfileName 参数，以向设备分配此注册配置文件。 详细了解 [Azure Active Directory 动态组](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)。
    ![配置文件名称和描述。](./media/device-enrollment-program-enroll-ios/image05.png)

4. 对于“用户关联”，选择具有此配置文件的设备是否必须通过已分配的用户进行注册。
    - 通过用户关联进行注册 - 为属于用户且想要使用公司门户获取服务（如安装应用）的设备选择此选项。 使用此选项时，用户还可使用公司门户对其设备进行身份验证。 用户关联需要 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [了解详细信息](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

    - 不通过用户关联进行注册 - 为不属于单个用户的设备选择此选项。 为无需访问本地用户数据即可执行任务的设备使用此选项。 公司门户等应用将无法运行。

5. 如果选择“通过用户关联进行注册”，则可选择让用户不使用 Apple 设置助理而使用公司门户进行身份验证。

    ![使用公司门户进行身份验证。](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 如果已将配置文件属性设置为“与用户关联结合注册”且未在使用公司门户，则在进行 DEP 注册时，多重身份验证 (MFA) 不起作用。 注册后，MFA 将按预期在设备上运行。 设备无法提示用户在首次登录时需要更改密码。 此外，在注册过程中，密码已过期的用户不会获得重置密码的提示。 用户必须使用其他设备重置密码。

6. 选择“设备管理设置”，然后选择是否要监督使用此配置文件的设备。
    “受监督”的设备会提供更多的管理选项，并且会默认禁用“激活锁”。 Microsoft 建议使用 DEP 作为启用受监督模式的机制，尤其适用于计划部署大量 iOS 设备的组织。

    将通过两种方式通知用户他们的设备受到监督：

    - 锁屏界面显示“此 iPhone 由 Contoso 托管”。
    - “设置” > “常规” > “关于”屏幕上显示“此 iPhone 受监督”。 Contoso 可以监视你的 Internet 流量并找到此设备。”

     > [!NOTE]
     > 不受监督的注册设备只能使用 Apple Configurator 重置为受监督。 以此方式重置设备需要使用 USB 线将 iOS 设备连接到 Mac。 有关详细信息，请参阅 [Apple Configurator 文档](http://help.apple.com/configurator/mac/2.3)。
     
7. 选择是否要为使用此配置文件的设备锁定注册。 “锁定注册”将禁用允许从“设置”菜单删除管理配置文件的 iOS 设置。 注册设备后，除非将设备恢复出厂设置，否则无法更改此设置。 此类设备必须将“受监督”管理模式设置为“是”。 

8. 选择是否要让使用此配置文件的设备能够“与计算机同步”。 如果选择“通过证书允许 Apple Configurator”，则必须在“Apple Configurator 证书”下选择证书。

9. 如果在上一步中选择了“通过证书允许 Apple Configurator”，则选择要导入的“Apple Configurator 证书”。

10. 选择“确定”。

11. 选择“设置助理设置”，以配置下列配置文件设置：![设置助理自定义](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)。

    | Setting | 描述 |
    | --- | --- |
    | **部门名称** | 用户在激活过程中轻点“关于配置”时显示。 |
    | **部门电话** | 用户在激活过程中单击“需要帮助”按钮时显示。 |
    | **设置助理选项** | 这些可选设置可以稍后在 iOS 的“设置”菜单中设置。 |
    | **密码** | 在激活过程中提示输入密码。 始终需要密码，除非设备受到保护，或以某种其他方式（即限制设备只可使用一个应用的展台模式）控制访问权限。 |
    | **位置服务** | 如果启用，在激活过程中设置助理会提示此服务。 |
    | **还原** | 如果启用，在激活过程中设置助理会提示进行 iCloud 备份。 |
    | **iCloud 和 Apple ID** | 如果启用，设置助理会提示用户登录 Apple ID，“应用和数据”屏幕将允许从 iCloud 备份还原设备。 |
    | **条款和条件** | 如果启用，在激活过程中设置助理会提示用户接受 Apple 的条款和条件。 |
    | **Touch ID** | 如果启用，在激活过程中设置助理会提示此服务。 |
    | **Apple Pay** | 如果启用，在激活过程中设置助理会提示此服务。 |
    | **缩放** | 如果启用，在激活过程中设置助理会提示此服务。 |
    | **Siri** | 如果启用，在激活过程中设置助理会提示此服务。 |
    | **诊断数据** | 如果启用，在激活过程中设置助理会提示此服务。 |

12. 选择“确定”。

13. 若要保存配置文件，则选择“创建”。

## <a name="sync-managed-devices"></a>同步托管设备
Intune 已拥有管理设备的权限，现在可以将 Intune 与 Apple 同步，以在 Azure 门户的 Intune 中查看托管设备。

1. 在 Azure 门户的 Intune 中，选择“设备注册”>“Apple 注册”>“注册计划令牌”> 在列表中选择令牌 >“设备”>“同步”。![选中“注册计划设备”节点和选中“同步”链接的屏幕截图。](./media/device-enrollment-program-enroll-ios/image06.png)
  
  为了遵从 Apple 的有关可接受的注册计划流量的条款，Intune 规定了以下限制：
  - 每七天只能运行一次完全同步。 在完全同步期间，Intune 将刷新分配给 Intune 的每一个 Apple 序列号。 如果在上一个完全同步的七天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
  - 任何同步请求都在 15 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。
  - Intune 每 24 小时与 Apple 同步一次新设备及已删除设备。

## <a name="assign-an-enrollment-profile-to-devices"></a>将注册配置文件分配到设备
必须先向设备分配注册计划配置文件才能注册他们。

>[!NOTE]
>还可以从“Apple 序列号”边栏选项卡将序列号分配给配置文件。

1. 在 Azure 门户的 Intune 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”> 在列表中选择令牌。
2. 选择“设备”> 在列表中选择设备 >“分配配置文件”。
3. 在“分配配置文件”下，为设备选择配置文件，然后选择“分配”。

### <a name="assign-a-default-profile"></a>分配默认配置文件

可以选择一个默认配置文件，以将其应用于所有使用特定令牌注册的设备。

1. 在 Azure 门户的 Intune 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”> 在列表中选择令牌。
2. 选择“设置默认配置文件”，在下拉列表中选择配置文件，然后选择“保存”。 此配置文件将应用于所有使用此令牌注册的设备。

## <a name="distribute-devices"></a>分配设备
已经在 Apple 和 Intune 之间启用了管理和同步，并且分配了注册 DEP 设备所需的配置文件。 现在可以将设备分配给用户。 具有用户关联的设备需要每个用户都分配有 Intune 许可证。 没有用户关联的设备需要设备许可证。 已激活设备只有恢复出厂设置才能应用注册配置文件。

请参阅[通过设备注册计划在 Intune 中注册 iOS 设备](/intune-user-help/enroll-your-device-dep-ios)。


