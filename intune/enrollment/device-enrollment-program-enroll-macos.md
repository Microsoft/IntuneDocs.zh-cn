---
title: 注册 macOS 设备 - Apple Business Manager 或 Apple School Manager
titleSuffix: ''
description: 了解如何注册企业拥有的 macOS 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ef08ea65a4976bcf77154108e415634dbae8e05
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514330"
---
# <a name="automatically-enroll-macos-devices-with-the-apple-business-manager-or-apple-school-manager"></a>使用 Apple Business Manager 或 Apple School Manager 自动注册 macOS 设备

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

可以为通过 Apple 的 [Apple Business Manager](https://business.apple.com/) 或 [Apple School Manager](https://school.apple.com/) 购买的 macOS 设备设置 Intune 注册。 可在不触碰设备的情况下为大量设备使用这些注册。 可以将 macOS 设备直接交付给用户。 用户打开设备时，“设置助理”将运行预先配置的设置，且设备将注册到 Intune 管理。

若要设置注册，需同时使用 Intune 和 Apple 门户。 创建注册配置文件，这些配置文件包含注册过程中应用于设备的设置。

Apple Business Manager 注册和 Apple School Manager 均不适用于[设备注册管理器](device-enrollment-manager-enroll.md)。

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>必备条件

- 在 [Apple School Manager](https://school.apple.com/) 或 [Apple 的设备注册计划](http://deploy.apple.com)中购买的设备
- 序列号列表或采购订单编号。
- [MDM 机构](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push Certificate](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>获取 Apple DEP 令牌

必须先从 Apple 获得 DEP 令牌 (.p7m) 文件，然后才能通过 DEP 或 Apple School Manager 注册 macOS 设备。 此令牌允许 Intune 同步有关组织所拥有的设备的信息。 它还允许 Intune 将注册配置文件上传到 Apple 并将这些配置文件上传到设备。

可以使用 Apple 门户创建令牌。 还可以使用 Apple 门户将设备分配到 Intune 进行管理。

> [!NOTE]
> 如果在迁移到 Azure 前从 Intune 经典门户删除了令牌，Intune 可能会还原已删除的 Apple 令牌。 可以从 Azure 门户再次删除令牌。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>步骤 1。 下载创建令牌所需的 Intune 公钥证书

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “macOS” > “macOS 注册” > “注册计划令牌” > “添加”      。

    ![获取注册计划令牌。](./media/device-enrollment-program-enroll-macos/image01.png)

2. 选择“我同意”，为 Microsoft 授予向 Apple 发送用户和设备信息的权限  。

   ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/device-enrollment-program-enroll-macos/add-enrollment-program-token-pane.png)

3. 选择“下载公钥”，将加密密钥 (.pem) 文件下载到本地并保存  。 .pem 文件用于从 Apple 门户请求信任关系证书。

### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>步骤 2。 使用密钥从 Apple 下载令牌

1. 选择“创建 Apple 设备注册计划令牌”  或“通过 Apple School Manager 创建令牌”  ，以打开相应的 Apple 门户，并使用公司 Apple ID 登录。 可使用此 Apple ID 续订令牌。
2. 对于 DEP，请在 Apple 门户中，选择“设备注册计划”   > “管理服务器”   > “添加 MDM 服务器”  ，然后选择“开始使用”  。
3. 对于 Apple School Manager，请在 Apple 门户中，依次选择“MDM 服务器”   > “添加 MDM 服务器”  。
4. 输入“MDM 服务器名称”  ，然后选择“下一步”  。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 并不是 Microsoft Intune 服务器的名称或 URL。

5. “添加&lt;服务器名称&gt;”  对话框随即打开，提示“上传公钥”  。 选择“选择文件…”  以上传 .pem 文件，然后选择“下一步”  。

6. 转到“部署计划”>“设备注册计划”>“管理设备”。  &gt;  &gt; 
7. 在“选择设备方式”  下，指定如何标识设备：
    - **序列号**
    - **订单号**
    - **上传 CSV 文件**。

   ![指定按序列号选择设备、将“选择操作”设置为“分配到服务器”并选择服务器名称的屏幕截图。](./media/device-enrollment-program-enroll-macos/enrollment-program-token-specify-serial.png)

8. 对于“选择操作”，选择“分配到服务器”，选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后选择“确定”    。 Apple 门户将指定的设备分配到 Intune 服务器以进行管理，然后显示“分配完成”  。

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>步骤 3. 保存用于创建此令牌的 Apple ID

在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，提供 Apple ID 供将来参考。

![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/device-enrollment-program-enroll-macos/image03.png)

### <a name="step-4-upload-your-token"></a>步骤 4. 上传令牌
在“Apple 令牌”框中，浏览到证书 (.pem) 文件，选择“打开”，然后选择“创建”    。 使用 Push Certificate，Intune 可通过将策略推送到已注册的设备来注册和管理 macOS 设备。 Intune 会自动与 Apple 同步以查看你的注册计划帐户。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件

现在，已经安装了令牌，可以为设备创建注册配置文件。 设备注册配置文件定义注册时应用于设备组的设置。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “macOS” > “macOS 注册” > “注册计划令牌”     。
2. 选择令牌，选择“配置文件”，然后选择“创建配置文件”   。

    ![“创建配置文件”的屏幕截图。](./media/device-enrollment-program-enroll-macos/image04.png)

3. 在“创建配置文件”下，输入配置文件的“名称”和“描述”以便于管理    。 用户看不到这些详细信息。 可以使用此“名称”字段在 Azure Active Directory 中创建动态组  。 使用配置文件名称定义 enrollmentProfileName 参数，以向设备分配此注册配置文件。 详细了解 [Azure Active Directory 动态组](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)。

    ![配置文件名称和描述。](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. 对于“平台”  ，选择“macOS”  。

5. 对于“用户关联”  ，选择具有此配置文件的设备是否必须通过已分配的用户进行注册。
    - 通过用户关联进行注册  - 为属于用户且想要使用公司门户应用获取服务（如安装应用）的设备选择此选项。 如果使用的是 ADFS，用户关联需要 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [了解详细信息](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)多重身份验证不支持使用用户关联的 macOS DEP 设备。

    - 不通过用户关联进行注册 - 为不属于单个用户的设备选择此选项  。 为无需访问本地用户数据即可执行任务的设备使用此选项。 公司门户等应用将无法运行。

6. 选择“设备管理设置”  ，然后选择是否锁定使用此配置文件的设备的注册。 “锁定注册”  将禁用 macOS 设置，该设置允许从“系统偏好设置”  菜单或通过“终端”  删除管理配置文件。 注册设备后，除非擦除设备，否则无法更改此设置。

    ![“设备管理设置”屏幕截图。](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)

7. 选择“确定”  。

8. 选择“设置助理设置”，配置以下配置文件设置  ：![设置助理的自定义项](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)。

    | 部门设置 | 说明 |
    |---|---|
    | <strong>部门名称</strong> | 用户在激活过程中轻点“关于配置”时显示。 |
    | <strong>部门电话</strong> | 用户在激活过程中单击“需要帮助”按钮时显示。 |

    用户设置设备时，可以选择在设备上显示或隐藏各种设置助理屏幕。
    - 如果选择“隐藏”，设置期间将不会显示该屏幕  。 设置设备之后，用户仍可以进入“设置”菜单来设置此功能  。
    - 如果选择“显示”，设置期间将显示该屏幕  。 用户有时可以跳过该屏幕，无需采取任何操作。 但是，他们可以稍后进入设备的“设置”菜单来设置此功能  。 

    | 设置助理屏幕设置 | 如果选择“显示”，设置期间设备将...  |
    |------------------------------------------|------------------------------------------|
    | <strong>密码</strong> | 提示用户输入密码。 始终需要密码，除非设备受到保护，或以某种其他方式（即限制设备只可使用一个应用的展台模式）控制访问权限。 |
    | <strong>位置服务</strong> | 提示用户输入位置。 |
    | <strong>还原</strong> | 显示“应用和数据”屏幕。 设置设备时，此屏幕为用户提供从 iCloud 备份还原或传输数据的选项。 |
    | <strong>iCloud 和 Apple ID</strong> | 为用户提供使用 Apple ID 登录并使用 iCloud 的选项   。                         |
    | <strong>条款和条件</strong> | 要求用户接受 Apple 的条款和条件。 |
    | <strong>Touch ID</strong> | 为用户提供设置设备的指纹识别的选项。 |
    | <strong>Apple Pay</strong> | 为用户提供在设备上设置 Apple Pay 的选项。 |
    | <strong>缩放</strong> | 设置设备时，为用户提供缩放显示内容的选项。 |
    | <strong>Siri</strong> | 为用户提供设置 Siri 的选项。 |
    | <strong>诊断数据</strong> | 向用户显示“诊断”屏幕。 此屏幕为用户提供将诊断数据发送到 Apple 的选项。 |
    | <strong>FileVault</strong> | 为用户提供设置 FileVault 加密的选项。 |
    | <strong>iCloud 诊断</strong> | 为用户提供将 iCloud 诊断数据发送到 Apple 的选项。 |
    | <strong>iCloud 存储</strong> | 为用户提供使用 iCloud 存储的选项。 |    
    | <strong>显示色调</strong> | 为用户提供打开“显示色调”的选项。 |
    | <strong>外观</strong> | 向用户显示“外观”屏幕。 |
    | <strong>注册</strong>| 要求用户注册设备。 |
    | <strong>隐私</strong>| 向用户展示“隐私”屏幕。 |
    | <strong>屏幕使用时间</strong>| 为用户显示“屏幕使用时间”屏幕。 |

9. 选择“确定”  。

10. 若要保存配置文件，则选择“创建”。 

## <a name="sync-managed-devices"></a>同步托管设备

Intune 已拥有管理设备的权限，现在可以将 Intune 与 Apple 同步，以在 Azure 门户的 Intune 中查看托管设备。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”  >“macOS”  >“macOS 注册”  >“注册程序令牌”  > 在列表中选择令牌 >“设备”  >“同步”  。![选中“注册计划设备”节点和选中“同步”链接的屏幕截图。](./media/device-enrollment-program-enroll-macos/image06.png)

   为了遵从 Apple 的有关可接受的注册计划流量的条款，Intune 规定了以下限制：
   - 每七天只能运行一次完全同步。 完全同步时，Intune 会提取分配给连接到 Intune 的 Apple MDM 服务器的完整更新序列号列表。 如果已从 Intune 门户删除注册计划设备但未从 DEP 门户的 Apple MDM 服务器取消分配，则该设备不会重新导入到 Intune，除非运行完全同步。   
   - 每 24 小时自动运行一次同步。 用户也可以单击“同步”按钮（不能超过 15 分钟一次）运行同步  。 所有同步请求都在 15 分钟内完成。 在同步完成前，“同步”按钮处于禁用状态  。 此同步将刷新现有设备状态并导入分配到 Apple MDM 服务器的新设备。

## <a name="assign-an-enrollment-profile-to-devices"></a>将注册配置文件分配到设备

必须先向设备分配注册计划配置文件才能注册他们。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “macOS” > “macOS 注册” > “注册计划令牌”> 在列表中选择一个令牌     。
2. 选择“设备”> 在列表中选择设备 >“分配配置文件”。  
3. 在“分配配置文件”下，为设备选择配置文件，然后选择“分配”   。

### <a name="assign-a-default-profile"></a>分配默认配置文件

可以选择一个默认 macOS 和 iOS/iPadOS 配置文件，以将其应用于所有使用特定令牌注册的设备。 

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备” > “macOS” > “macOS 注册” > “注册计划令牌”> 在列表中选择一个令牌     。
2. 选择“设置默认配置文件”，在下拉列表中选择配置文件，然后选择“保存”。   此配置文件将应用于所有使用此令牌注册的设备。

## <a name="distribute-devices"></a>分发设备

已启用 Apple 和 Intune 之间的管理和同步，并分配了配置文件以允许设备注册。 现在可以将设备分配给用户。 具有用户关联的设备需要每个用户都分配有 Intune 许可证。 没有用户关联的设备需要设备许可证。 已激活设备只有擦除后才能应用注册配置文件。

## <a name="renew-a-dep-token"></a>续订 DEP 令牌

1. 转到 deploy.apple.com。  
2. 在“管理服务器”下，选择与想要续订的令牌文件相关的 MDM 服务器  。
3. 选择“生成新令牌”  。

    ![生成新令牌的屏幕截图。](./media/device-enrollment-program-enroll-macos/generatenewtoken.png)

4. 选择“服务器令牌”  。  
5. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备注册”   > “Apple 注册”   > “注册程序令牌”  > 选择令牌。
    ![注册程序令牌屏幕截图](./media/device-enrollment-program-enroll-macos/enrollmentprogramtokens.png)

6. 选择“续订令牌”，然后输入用于创建原始令牌的 Apple ID  。  
    ![生成新令牌的屏幕截图。](./media/device-enrollment-program-enroll-macos/renewtoken.png)

7. 上传新下载的令牌。  
8. 选择“续订令牌”  。 你将看到令牌已续订的确认消息。
    ![确认消息屏幕截图。](./media/device-enrollment-program-enroll-macos/confirmation.png)

## <a name="next-steps"></a>后续步骤

注册 macOS 设备后，可以开始[对其进行管理](../remote-actions/device-management.md)。
