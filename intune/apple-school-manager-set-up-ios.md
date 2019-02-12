---
title: iOS 设备的 Apple School Manager 计划注册
titleSuffix: Microsoft Intune
description: 了解如何使用 Intune 为公司拥有的 iOS 设备设置 Apple School Manager 计划注册。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1498e6bf9a4b2df7da9ef0a7ec6824e2a3e4f94
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851315"
---
# <a name="set-up-ios-device-enrollment-with-apple-school-manager"></a>通过 Apple School Manager 设置 iOS 设备注册

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

可以将 Intune 设置为，注册通过 [Apple School Manager](https://school.apple.com/) 计划购买的 iOS 设备。 通过结合使用 Intune 与 Apple School Manager，可在不触碰设备的情况下注册大量 iOS 设备。 学生或教师打开设备时，“设置助理”使用预先配置的设置运行，并且会注册设备以便进行管理。

若要启用 Apple School Manager 注册，请使用 Intune 和 Apple School Manager 门户。 需要序列号列表或购买订单编号，这样才能将设备分配到 Intune 进行管理。 创建 DEP 注册配置文件，这些配置文件包含注册过程中应用于设备的设置。

Apple School Manager 注册不能与 [Apple 的设备注册计划](device-enrollment-program-enroll-ios.md)或[设备注册管理器](device-enrollment-manager-enroll.md)一起使用。

**必备条件**
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- [MDM 机构](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 如果使用的是 ADFS，用户关联需要 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [了解详细信息](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。
- 从 [Apple School Management](http://school.apple.com) 计划购买的设备

## <a name="get-an-apple-token-and-assign-devices"></a>获取 Apple 令牌并分配设备

必须先从 Apple 获取令牌 (.p7m) 文件，然后才能使用 Apple School Manager 注册公司拥有的 iOS 设备。 使用此令牌，Intune 可以同步有关已加入 Apple School Manager 的设备的信息。 它也允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。 在 Apple 门户中时，还可分配设备序列号以进行管理。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>步骤 1。 下载创建 Apple 令牌所需的 Intune 公钥证书

1. 在 [Intune](https://aka.ms/intuneportal) 下选择“设备注册” > “Apple 注册” > “注册计划令牌” > “添加”。

   ![获取注册计划令牌。](./media/device-enrollment-program-enroll-ios/image01.png)

2. 在“注册计划令牌”边栏选项卡中，选择“下载公钥”，下载加密密钥 (.pem) 文件，并将其保存在本地。 .pem 文件用于从 Apple School Manager 门户请求信任关系证书。
     ![注册计划令牌”边栏选项卡](./media/device-enrollment-program-enroll-ios/image02.png)。

### <a name="step-2-download-a-token-and-assign-devices"></a>步骤 2。 下载令牌并分配设备
1. 选择“通过 Apple School Manager 创建令牌”，使用公司 Apple ID 登录到 Apple School。 可使用此 Apple ID 续订 Apple School Manager 令牌。
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

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>步骤 3. 保存用于创建此令牌的 Apple ID

在 Azure 门户中的 Intune 中，提供 Apple ID 供未来参考。

![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>步骤 4. 上传令牌
在“Apple 令牌”框中，浏览到证书 (.pem) 文件，选择“打开”，然后选择“创建”。 使用 Push Certificate，Intune 可通过将策略推送到已注册的移动设备来注册和管理 iOS 设备。 Intune 会自动从 Apple 同步 Apple School Manager 设备。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件
至此，你已安装令牌，接下来可以为 Apple School 设备创建注册配置文件了。 设备注册配置文件定义注册时应用于设备组的设置。

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”。
2. 选择令牌，选择“配置文件”，然后选择“创建配置文件”。

3. 在“创建配置文件”下，输入配置文件的“名称”和“描述”以便于管理。 用户看不到这些详细信息。 可以使用此“名称”字段在 Azure Active Directory 中创建动态组。 使用配置文件名称定义 enrollmentProfileName 参数，以向设备分配此注册配置文件。 详细了解 [Azure Active Directory 动态组](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)。

    ![配置文件名称和描述。](./media/device-enrollment-program-enroll-ios/image05.png)

4. 对于“用户关联”，选择具有此配置文件的设备是否必须通过已分配的用户进行注册。
    - 通过用户关联进行注册 - 为属于用户且想要使用公司门户获取服务（如安装应用）的设备选择此选项。 使用此选项时，用户还可使用公司门户对其设备进行身份验证。 如果使用的是 ADFS，用户关联需要 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [了解详细信息](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。   Apple School Manager 的“Shared iPad”模式要求用户不通过用户关联进行注册。

    - 不通过用户关联进行注册 - 为不属于单个用户的设备（例如共享设备）选择此选项。 对无需访问本地用户数据即可执行任务的设备使用此选项。 公司门户等应用将无法运行。

5. 如果选择“通过用户关联进行注册”，则可选择让用户不使用 Apple 设置助理而使用公司门户进行身份验证。

    ![使用公司门户进行身份验证。](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 如果想要执行以下任一操作，请将“不使用 Apple 设置助理而使用公司门户进行身份验证”设置为“是”。
    >    - 使用多重身份验证
    >    - 提示用户在首次登录时需要更改密码
    >    - 提示用户在注册期间重置过期的密码
    >
    > 使用 Apple 设置助理进行身份验证时不支持这些功能。

6. 选择“设备管理设置”，然后选择是否要监督使用此配置文件的设备。
    “受监督”的设备会提供更多的管理选项，并且会默认禁用“激活锁”。 Microsoft 建议使用 DEP 作为启用受监督模式的机制，尤其适用于计划部署大量 iOS 设备的组织。

    将通过两种方式通知用户他们的设备受到监督：

   - 锁定屏幕显示：“此 iPhone 由 Contoso 托管”。
   - “设置” > “常规” > “关于”屏幕显示：“此 iPhone 受到监督”。 Contoso 可以监视你的 Internet 流量并找到此设备。”

     > [!NOTE]
     > 不受监督的注册设备只能使用 Apple Configurator 重置为受监督。 以此方式重置设备需要使用 USB 线将 iOS 设备连接到 Mac。 有关详细信息，请参阅 [Apple Configurator 文档](http://help.apple.com/configurator/mac/2.3)。

7. 选择是否要为使用此配置文件的设备锁定注册。 “锁定注册”将禁用允许从“设置”菜单删除管理配置文件的 iOS 设置。 注册设备后，除非擦除设备，否则无法更改此设置。 此类设备必须将“受监督”管理模式设置为“是”。 

8. 若要让多个用户使用托管 Apple ID 登录已注册 iPad，请选择“共享 iPad”下的“是”（此选项要求必需将“无用户关联注册”和“已监督”模式设置为“是”）。在 Apple School Manager 门户中创建托管的 Apple ID。 详细了解[共享 iPad](education-settings-configure-ios-shared.md) 和 [Apple 的共享 iPad 要求](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56)。

9. 选择是否要让使用此配置文件的设备能够“与计算机同步”。 如果选择“通过证书允许 Apple Configurator”，则必须在“Apple Configurator 证书”下选择证书。

10. 如果在上一步中选择了“通过证书允许 Apple Configurator”，则选择要导入的“Apple Configurator 证书”。

11. 选择“确定”。

12. 选择“设置助理设置”，配置以下配置文件设置：![设置助理自定义项。](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    |                 Setting                  |                                                                                               描述                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>部门名称</strong>     |                                                             用户在激活过程中轻点“关于配置”时显示。                                                              |
    |    <strong>部门电话</strong>     |                                                          用户在激活过程中单击“需要帮助”按钮时显示。                                                          |
    | <strong>设置助理选项</strong> |                                                     这些可选设置可以稍后在 iOS 的“设置”菜单中设置。                                                      |
    |        <strong>密码</strong>         | 在激活过程中提示输入密码。 始终需要密码，除非设备受到保护，或以某种其他方式（即限制设备只可使用一个应用的展台模式）控制访问权限。 |
    |    <strong>位置服务</strong>    |                                                                 如果启用，在激活过程中设置助理会提示此服务。                                                                  |
    |         <strong>还原</strong>         |                                                                如果启用，在激活过程中设置助理会提示进行 iCloud 备份。                                                                 |
    |   <strong>iCloud 和 Apple ID</strong>   |                         如果启用，设置助理会提示用户登录 Apple ID，“应用和数据”屏幕将允许从 iCloud 备份还原设备。                         |
    |  <strong>条款和条件</strong>   |                                                   如果启用，在激活过程中设置助理会提示用户接受 Apple 的条款和条件。                                                   |
    |        <strong>Touch ID</strong>         |                                                                 如果启用，在激活过程中设置助理会提示此服务。                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 如果启用，在激活过程中设置助理会提示此服务。                                                                 |
    |          <strong>缩放</strong>           |                                                                 如果启用，在激活过程中设置助理会提示此服务。                                                                 |
    |          <strong>Siri</strong>           |                                                                 如果启用，在激活过程中设置助理会提示此服务。                                                                 |
    |     <strong>诊断数据</strong>     |                                                                 如果启用，在激活过程中设置助理会提示此服务。                                                                 |


13. 选择“确定”。

14. 若要保存配置文件，则选择“创建”。

## <a name="connect-school-data-sync"></a>连接学校数据同步
（可选）Apple School Manager 支持使用 Microsoft 学校数据同步 (SDS) 将学籍数据同步到 Azure Active Directory (AD)。 你只能同步一个包含 SDS 的令牌。 如果设置了其他包含学校数据同步的令牌，则会从之前包含 SDS 的令牌中将其删除。 新连接将替换当前的令牌。 请完成以下步骤以使用 SDS 来同步学校数据。

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”。
2. 选择 Apple School Manager 令牌，然后选择“学校数据同步”。
3. 在“学校数据同步”下，选择“允许”。 此设置将允许 Intune 与 Office 365 中的 SDS 连接。
4. 若要允许 Apple School Manager 与 Azure AD 连接，请选择“设置 Microsoft 学校数据同步”。详细了解[如何设置学校数据同步](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1)。
5. 单击“保存” > “确定”。

## <a name="sync-managed-devices"></a>同步托管设备

在 Intune 分配有管理 Apple School Manager 设备的权限后，将 Intune 与 Apple 服务同步，以便在 Intune 中查看托管设备。

在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”> 在列表中选择令牌 >“设备” > “同步”。![选中“注册计划设备”节点和选中“同步”链接的屏幕截图。](./media/device-enrollment-program-enroll-ios/image06.png)

  为了遵从 Apple 的有关可接受的注册计划流量的条款，Intune 规定了以下限制：
  - 每七天只能运行一次完全同步。 在完全同步期间，Intune 将刷新分配给 Intune 的每一个 Apple 序列号。 如果在上一个完全同步的七天内尝试完全同步，则 Intune 只刷新已经不在 Intune 中列出的序列号。
  - 任何同步请求都在 15 分钟内完成。 在此期间或在请求成功之前，“同步”按钮处于禁用状态。
  - Intune 每 24 小时与 Apple 同步一次新设备及已删除设备。

>[!NOTE]
>也可以从“注册计划设备”边栏选项卡向配置文件分配 Apple School Manager 序列号。

## <a name="assign-a-profile-to-devices"></a>为设备分配配置文件
必须先向 Intune 管理的 Apple School Manager 设备分配注册配置文件，然后才能注册设备。

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”> 在列表中选择令牌。
2. 选择“设备”> 在列表中选择设备 >“分配配置文件”。
3. 在“分配配置文件”下，选择设备的配置文件，再选择“分配”。

## <a name="distribute-devices-to-users"></a>将设备分配给用户

已经在 Apple 和 Intune 之间启用了管理和同步，并且分配了注册 Apple School 设备所需的配置文件。 现在可以将设备分配给用户。 打开 iOS Apple School Manager 设备时，它将注册以便由 Intune 管理。 如果设备已激活并处于使用状态，则在将设备擦除后才能应用配置文件。
