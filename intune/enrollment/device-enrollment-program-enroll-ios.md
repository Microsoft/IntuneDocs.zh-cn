---
title: 注册 iOS/iPadOS 设备 - 设备注册计划
titleSuffix: Microsoft Intune
description: 了解如何使用“设备注册计划”注册公司拥有的 iOS/iPadOS 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: adca40b558a75d2c080fe453218f232a37b21daa
ms.sourcegitcommit: cd90650c339795d44702e9dcd0b9679a7b438bb2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473759"
---
# <a name="automatically-enroll-iosipados-devices-with-apples-device-enrollment-program"></a>通过 Apple 设备注册计划自动注册 iOS/iPadOS 设备

可以设置 Intune 以注册通过 Apple [设备注册计划 (DEP)](https://deploy.apple.com) 购买的 iOS/iPadOS 设备。 借助 DEP，可以在不接触设备的情况下注册大量设备。 iPhone、iPad 和 MacBook 等设备可以直接寄送给用户。 用户打开设备时，包含 Apple 产品典型现成体验的“设置助理”将运行预先配置的设置，设备将注册以便进行管理。

若要启用 DEP 注册，请使用 Intune 和 Business Manager (ABM) 或 Apple School Manager (ASM) 门户。 需要序列号列表或购买订单编号，这样才能将设备分配到 Intune 以便在 ABM/ASM 中进行管理。 在 Intune 中创建 DEP 注册配置文件，这些配置文件包含注册过程中应用于设备的设置。 请注意，DEP 注册不能与[设备注册管理器](device-enrollment-manager-enroll.md)帐户共同使用。

> [!NOTE]
> DEP 设置最终用户不一定能删除的设备配置。 因此，在[迁移到 DEP](../fundamentals/migration-guide-considerations.md) 之前，必须擦除设备，使其返回到全新状态。

## <a name="dep-and-the-company-portal"></a>DEP 和公司门户

DEP 注册与 App Store 版公司门户应用不兼容。 可以授权用户访问 DEP 设备上的公司门户应用。 你可能希望提供此访问权限，让用户选择他们想要在其设备上使用的公司应用，或使用新式验证完成注册过程。 

若要允许在注册期间使用新式验证，请使用 DEP 配置文件中的“使用 VPP 安装公司门户”  （VPP 即批量购买计划）将应用推送到设备。 有关详细信息，请参阅[通过 Apple 设备注册计划自动注册 iOS/iPadOS 设备](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)。

若要允许公司门户自动更新，并在已注册到 DEP 的设备上提供公司门户应用，请通过 Intune 将公司门户应用部署为已应用[应用程序配置策略](../apps/app-configuration-policies-use-ios.md)的必需批量购买计划 (VPP) 应用。

## <a name="what-is-supervised-mode"></a>受监督模式简介

Apple 在 iOS/iPadOS 5 中引入了受监督模式。 可对处于监督模式的 iOS/iPadOS 设备进行更多管理和控制，例如阻止屏幕捕获和阻止从 App Store 安装应用。 因此，这种模式对企业拥有的设备特别有用。 在 Apple 设备注册计划 (DEP) 中，Intune 支持将设备配置为受监督模式。

在 iOS/iPadOS 11 中已弃用对未受监督的 DEP 设备的支持。 在 iOS/iPadOS 11 和更高版本中，应始终对 DEP 配置的设备进行监督。 在未来发布的 iOS/iPadOS 版本中将忽略“DEP 受监督”标记。

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
- [移动设备管理 (MDM) 机构](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>获取 Apple DEP 令牌

必须先从 Apple 获得 DEP 令牌 (.p7m) 文件，然后才能通过 DEP 注册 iOS/iPadOS 设备。 此令牌允许 Intune 同步有关公司所拥有的 DEP 设备的信息。 还允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

可以使用 Apple Business Manager 或 Apple School Manager 门户来创建令牌。 还可以使用 ABM/ASM 门户将设备分配到 Intune 进行管理。

> [!NOTE]
> 如果在迁移到 Azure 前从 Intune 经典门户删除了令牌，Intune 可能会还原已删除的 Apple DEP 令牌。 可在 Azure 门户中再次删除 DEP 令牌。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>步骤 1。 下载创建令牌所需的 Intune 公钥证书。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “iOS”   > “iOS 注册”   > “注册计划令牌”   > “添加”  。

    ![获取注册计划令牌。](./media/device-enrollment-program-enroll-ios/image01.png)

2. 选择“我同意”，为 Microsoft 授予向 Apple 发送用户和设备信息的权限  。

> [!NOTE]
> 完成步骤 2 以下载 Intune 公钥证书后，请不要关闭向导或离开此页面。 如果关闭了向导或离开了此页面，则会使已下载的证书失效，你需要再次重复此过程。 如果遇到这种情况，“查看 + 创建”选项卡上的“创建”按钮通常会显示为灰色，并且你无法完成该过程。

   ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. 选择“下载公钥”，将加密密钥 (.pem) 文件下载到本地并保存  。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>步骤 2。 使用密钥从 Apple 下载令牌。

1. 选择“创建 Apple 设备注册计划令牌”，以打开 Apple 部署计划门户，并使用公司 Apple ID 登录  。 可使用此 Apple ID 续订 DEP 令牌。
2. 在 Apple [部署计划门户](https://deploy.apple.com)中，对“设备注册计划”选择“开始”   。

3. 在“管理服务器”  页上，选择“添加 MDM 服务器”  。
4. 输入“MDM 服务器名称”  ，然后选择“下一步”  。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

5. “添加&lt;服务器名称&gt;”  对话框随即打开，提示“上传公钥”  。 选择“选择文件…”  以上传 .pem 文件，然后选择“下一步”  。

6. 转到“部署计划”>“设备注册计划”>“管理设备”。  &gt;  &gt; 
7. 在“选择设备方式”  下，指定如何标识设备：
    - **序列号**
    - **订单号**
    - **上传 CSV 文件**。

   ![指定按序列号选择设备、将“选择操作”设置为“分配到服务器”并选择服务器名称的屏幕截图。](./media/device-enrollment-program-enroll-ios/enrollment-program-token-specify-serial.png)

8. 对于“选择操作”，选择“分配到服务器”，选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后选择“确定”    。 Apple 门户将指定的设备分配到 Intune 服务器以进行管理，然后显示“分配完成”  。

   在 Apple 门户中，转到“部署计划”  &gt;“设备注册计划”  &gt;“查看分配历史记录”  ，以查看设备及其 MDM 服务器分配的列表。

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>步骤 3. 保存用于创建此令牌的 Apple ID。

在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，提供 Apple ID 供将来参考。

![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token-and-choose-scope-tags"></a>步骤 4. 上传令牌并选择作用域标记。

1. 在“Apple 令牌”框中，浏览到证书 (.pem) 文件，选择“打开”   。
2. 如果要将[作用域标记](../fundamentals/scope-tags.md)应用于此 DEP 令牌，则选择“作用域 (标记)”，并选择所需的作用域标记  。 应用于令牌的作用域标记将由添加到此令牌的配置文件和设备继承。
3. 选择“创建”  。

使用 Push Certificate，Intune 可通过将策略推送到已注册的移动设备来注册和管理 iOS/iPadOS 设备。 Intune 会自动与 Apple 同步以查看你的注册计划帐户。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件

已经安装了令牌，现在可以为 DEP 设备创建注册配置文件。 设备注册配置文件定义注册时应用于设备组的设置。 每个 DEP 令牌限制为 100 个注册配置文件。

> [!NOTE]
> 如果 VPP 令牌没有足够的公司门户许可证，或令牌已到期，设备便会遭阻止。 当令牌即将过期或许可证不足时，Intune 将显示警报。
 

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “iOS”   > “iOS 注册”   > “注册计划令牌”  。
2. 选择令牌，再依次选择“配置文件”   > “创建配置文件”   > “iOS”  。

    ![“创建配置文件”的屏幕截图。](./media/device-enrollment-program-enroll-ios/image04.png)

3. 在“基本信息”  页上，输入配置文件的“名称”  和“说明”  ，以便于管理。 用户看不到这些详细信息。 可以使用此“名称”字段在 Azure Active Directory 中创建动态组  。 使用配置文件名称定义 enrollmentProfileName 参数，以向设备分配此注册配置文件。 详细了解 [Azure Active Directory 动态组](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)。

    ![配置文件名称和描述。](./media/device-enrollment-program-enroll-ios/image05.png)

4. 选择“下一步:  设备管理设置”。

5. 对于“用户关联”，选择具有此配置文件的设备是否必须通过已分配的用户进行注册  。
    - 通过用户关联进行注册  - 为属于用户且想要使用公司门户获取服务（如安装应用）的设备选择此选项。 如果使用 ADFS 且注册配置文件的“不使用设置助理而使用公司门户进行身份验证”  设置为“否”  ，则需使用 [WS-Trust 1.3 用户名/混合终结点](https://technet.microsoft.com/library/adfs2-help-endpoints)[了解详细信息](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

    - 不通过用户关联进行注册 - 为不属于单个用户的设备选择此选项  。 此选项适用于不访问本地用户数据的设备。 公司门户等应用将无法运行。

5. 如果选择“注册用户关联”  ，可以让用户通过公司门户（而不是 Apple 设置助理）进行身份验证。

    ![使用公司门户进行身份验证。](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 若要执行以下任何一项操作，请将“选择用户必须进行身份验证的位置”  设置为“公司门户”  。
    >    - 使用多重身份验证
    >    - 提示用户在首次登录时需要更改密码
    >    - 提示用户在注册期间重置过期的密码
    >
    > 使用 Apple 设置助理进行身份验证时，不支持执行这些操作。

6. 如果对“选择用户必须进行身份验证的位置”  选择了“公司门户”  ，可以使用 VPP 令牌在设备上自动安装公司门户。 在这种情况下，用户无需提供 Apple ID。 要使用 VPP 令牌安装公司门户，请在“使用 VPP 安装公司门户”下选择一个令牌  。 要求已将公司门户添加到 VPP 令牌中。 若要确保在注册后继续更新公司门户应用，请确保已在 Intune 中配置了应用部署（“Intune”>“客户端应用”）。 因此，用户交互不是必需的，你很可能希望将公司门户作为 iOS/iPadOS VPP 应用，使其成为必需的应用，并使用设备许可进行分配。 请确保令牌没有过期，并且具有足够公司门户应用使用的设备许可证。 如果令牌到期或许可证用完，Intune 会改为安装 App Store 版公司门户，并提示输入 Apple ID。 

    > [!NOTE]
    > 如果将“选择用户必须进行身份验证的位置”  设置为“公司门户”  ，请务必在将公司门户下载到 DEP 设备的最初 24 小时内执行设备注册流程。 否则，注册可能会失败，需要恢复出厂设置才能注册设备。
    
    ![使用 VPP 安装公司门户的屏幕截图。](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. 如果对“选择用户必须进行身份验证的位置”  选择了“设置助理”  ，但也想在设备上使用条件访问或部署公司应用，必须在设备上安装公司门户。 为此，请对“安装公司门户”  选择“是”  。  如果希望用户接收公司门户，而不需要在 App Store 中进行身份验证，请依次选择“使用 VPP 安装公司门户”  和 VPP 令牌。 请确保令牌没有到期，并且有足够的设备许可证，可供正确部署公司门户应用。

8. 如果对“使用 VPP 安装公司门户”  选择了令牌，可以在设置助理完成后，立即将设备锁定在单应用模式下（具体而言，即公司门户应用）。 针对“在身份验证前以单应用模式运行公司门户”，选择为“是”以设置此选项   。 要使用该设备，用户必须先使用公司门户登录以进行身份验证。

    锁定在单应用模式下的单台设备不支持多重身份验证。 这种限制的存在是因为，设备无法切换到其他应用来完成双重身份验证。 因此，若要在单应用模式设备上进行多重身份验证，必须在其他设备上进行双重身份验证。

    仅 iOS/iPadOS 11.3.1 及更高版本支持此功能。

   ![单应用模式的屏幕截图。](./media/device-enrollment-program-enroll-ios/single-app-mode.png)

9. 若要让使用此配置文件的设备受到监督，请对“已监督”  选择“是”  。

    ![“设备管理设置”屏幕截图。](./media/device-enrollment-program-enroll-ios/supervisedmode.png)

     “受监督”的设备会提供更多的管理选项，并且会默认禁用“激活锁”。 Microsoft 建议使用 DEP 作为监督模式启用机制，尤其是在部署大量 iOS/iPadOS 设备时。

    将通过两种方式通知用户他们的设备受到监督：

   - 锁定屏幕显示：“此 iPhone 由 Contoso 托管”。
   - “设置”   > “常规”   > “关于”  屏幕显示：“此 iPhone 受到监督”。 Contoso 可以监视你的 Internet 流量并找到此设备。”

     > [!NOTE]
     > 不受监督的注册设备只能使用 Apple Configurator 重置为受监督。 以此方式重置设备需要使用 USB 线将 iOS/iPadOS 设备连接到 Mac。 有关详细信息，请参阅 [Apple Configurator 文档](http://help.apple.com/configurator/mac/2.3)。

10. 选择是否要对使用此配置文件的设备进行锁定注册。 “锁定注册”  将禁用允许从“设置”  菜单删除管理配置文件的 iOS/iPadOS 设置。 在设备注册之后，如果不擦除设备，就无法更改此设置。 此类设备必须将“受监督”管理模式设置为“是”。   

11. 选择是否要让使用此配置文件的设备能够“与计算机同步”  。 如果选择“通过证书允许 Apple Configurator”  ，则必须在“Apple Configurator 证书”  下选择证书。

12. 如果在上一步中选择了“通过证书允许 Apple Configurator”，则选择要导入的“Apple Configurator 证书”。 

13. 可以为设备指定命名格式，此格式在设备注册时和每次连续签入时自动应用。 若要创建命名模板，请在“应用设备名称模板”  下选择“是”  。 然后，在“设备名称模板”  框中，输入要用于使用此配置文件的设备的名称模板。 可以指定包含设备类型和序列号的模板格式。 

14. 选择“下一步:  设置助理的自定义项。

15. 在“设置助理的自定义项”  页上，配置以下配置文件设置：![设置助理的自定义项](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)。


    | 部门设置 | 说明 |
    |---|---|
    | <strong>部门名称</strong> | 用户在激活过程中轻点“关于配置”时显示。 |
    |    <strong>部门电话</strong>     | 用户在激活过程中单击“需要帮助”按钮时显示。 |

    可以选择在用户设置期间隐藏设备上的“设置助理”屏幕。
    - 如果选择“隐藏”，设置期间将不会显示该屏幕  。 设置设备之后，用户仍可以进入“设置”菜单来设置此功能  。
    - 如果选择“显示”，设置期间将显示该屏幕  。 用户有时可以跳过该屏幕，无需采取任何操作。 但是，他们可以稍后进入设备的“设置”菜单来设置此功能  。 


    | 设置助理屏幕设置 | 如果选择“显示”，设置期间设备将...  |
    |------------------------------------------|------------------------------------------|
    | <strong>密码</strong> | 提示用户输入密码。 对于不安全的设备，始终要求提供密码，除非以其他方式（如限制设备只能使用一个应用的展台模式）控制访问。 |
    | <strong>位置服务</strong> | 提示用户输入位置。 |
    | <strong>还原</strong> | 显示“应用和数据”屏幕。 设置设备时，此屏幕为用户提供从 iCloud 备份还原或传输数据的选项。 |
    | <strong>iCloud 和 Apple ID</strong> | 让用户能够选择使用 Apple ID 登录并使用 iCloud。                         |
    | <strong>条款和条件</strong> | 要求用户接受 Apple 的条款和条件。 |
    | <strong>Touch ID</strong> | 为用户提供设置设备的指纹识别的选项。 |
    | <strong>Apple Pay</strong> | 为用户提供在设备上设置 Apple Pay 的选项。 |
    | <strong>缩放</strong> | 设置设备时，为用户提供缩放显示内容的选项。 |
    | <strong>Siri</strong> | 为用户提供设置 Siri 的选项。 |
    | <strong>诊断数据</strong> | 向用户显示“诊断”屏幕。 此屏幕为用户提供将诊断数据发送到 Apple 的选项。 |
    | <strong>显示色调</strong> | 为用户提供打开“显示色调”的选项。 |
    | <strong>隐私</strong> | 向用户展示“隐私”屏幕。 |
    | <strong>Android 迁移</strong> | 为用户提供从 Android 设备迁移数据的选项。 |
    | <strong>iMessage 和 FaceTime</strong> | 让用户能够选择设置 iMessage 和 FaceTime。 |
    | <strong>载入</strong> | 显示用户教育的载入信息屏幕，如“封面页”以及“多任务和控制中心”。 |
    | <strong>监视迁移</strong> | 为用户提供从监视设备迁移数据的选项。 |
    | <strong>屏幕使用时间</strong> | 显示“屏幕使用时间”屏幕。 |
    | <strong>软件更新</strong> | 显示强制“软件更新”屏幕。 |
    | <strong>SIM 设置</strong> | 为用户提供添加移动电话计划的选项。 |
    | <strong>外观</strong> | 向用户显示“外观”屏幕。 |
    | <strong>Express 语言</strong>| 向用户显示“Express 语言”屏幕。 |
    | <strong>首选语言</strong> | 让用户能够选择“首选语言”  。 |
    | <strong>设备间迁移</strong> | 让用户能够将数据从旧设备迁移到此设备。|
    

16. 选择“下一步”  ，以转到“查看 + 创建”页  。

17. 若要保存配置文件，则选择“创建”。 

## <a name="sync-managed-devices"></a>同步托管设备
Intune 已拥有管理设备的权限，现在可以将 Intune 与 Apple 同步，以在 Azure 门户的 Intune 中查看托管设备。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”  >“iOS”  >“iOS 注册”  >“注册程序令牌”  > 在列表中选择令牌 >“设备”  >“同步”  。![“注册计划设备”节点和“同步”链接的屏幕截图。](./media/device-enrollment-program-enroll-ios/image06.png)

   为了遵守 Apple 有关可接受注册计划流量的条款，Intune 规定了以下限制：
   - 每七天只能运行一次完全同步。 完全同步时，Intune 会提取分配给连接到 Intune 的 Apple MDM 服务器的完整更新序列号列表。 如果 DEP 设备已从 Intune 门户中删除，应在 DEP 门户中从 Apple MDM 服务器取消对它的分配。 如果未取消分配它，那么它不会重新导入 Intune，除非完全同步运行。   
   - 每 24 小时自动运行一次同步。 用户也可以单击“同步”按钮（不能超过 15 分钟一次）运行同步  。 所有同步请求都在 15 分钟内完成。 在同步完成前，“同步”按钮处于禁用状态  。 此同步将刷新现有设备状态并导入分配到 Apple MDM 服务器的新设备。   


## <a name="assign-an-enrollment-profile-to-devices"></a>将注册配置文件分配到设备
必须先向设备分配注册计划配置文件才能注册他们。

>[!NOTE]
>还可以从“Apple 序列号”  边栏选项卡将序列号分配给配置文件。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “iOS”   > “iOS 注册”   > “注册计划令牌”  > 在列表中选择令牌。
2. 选择“设备”> 在列表中选择设备 >“分配配置文件”。  
3. 在“分配配置文件”下，为设备选择配置文件，然后选择“分配”   。

### <a name="assign-a-default-profile"></a>分配默认配置文件

可以选择一个默认配置文件，以将其应用于所有使用特定令牌注册的设备。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “iOS”   > “iOS 注册”   > “注册计划令牌”  > 在列表中选择令牌。
2. 选择“设置默认配置文件”，在下拉列表中选择配置文件，然后选择“保存”。   此配置文件将应用于所有使用此令牌注册的设备。

## <a name="distribute-devices"></a>分发设备
已经在 Apple 和 Intune 之间启用了管理和同步，并且分配了注册 DEP 设备所需的配置文件。 现在可以将设备分配给用户。 具有用户关联的设备需要每个用户都分配有 Intune 许可证。 没有用户关联的设备需要设备许可证。 已激活设备只有在擦除后，才能应用注册配置文件。

请参阅[通过设备注册计划在 Intune 中注册 iOS/iPadOS 设备](/intune-user-help/enroll-your-device-dep-ios)。

## <a name="renew-a-dep-token"></a>续订 DEP 令牌  
1. 转到 deploy.apple.com。  
2. 在“管理服务器”下，选择与想要续订的令牌文件相关的 MDM 服务器  。
3. 选择“生成新令牌”  。

    ![生成新令牌的屏幕截图。](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. 选择“服务器令牌”  。  
5. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “iOS”   > “iOS 注册”   > “注册计划令牌”  > 选择令牌。
    ![注册程序令牌屏幕截图](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. 选择“续订令牌”，然后输入用于创建原始令牌的 Apple ID  。  
    ![生成新令牌的屏幕截图。](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. 上传新下载的令牌。  
9. 选择“续订令牌”  。 你将看到令牌已续订的确认消息。   
    ![确认消息屏幕截图。](./media/device-enrollment-program-enroll-ios/confirmation.png)
