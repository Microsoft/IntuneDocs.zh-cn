---
title: 在 Microsoft Intune 中设置注册限制
titlesuffix: ''
description: 按平台限制注册，并在 Intune 中设置设备注册限制。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bd282a6b23f33b11cbd046cac4f791d6d675e365
ms.sourcegitcommit: 9739a9aab032ebb2c4b52ccfb454a9e0f78b2ee4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54751206"
---
# <a name="set-enrollment-restrictions"></a>设置注册限制

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

作为 Intune 管理员，可创建和管理注册限制，这些限制可以定义注册接受 Intune 的管理的设备数量和类型。 可创建多个限制并将其应用于不同用户组。 可为不同限制设置[优先级顺序](#change-enrollment-restriction-priority)。

>[!NOTE]
>注册限制不是安全功能。 遭到入侵的设备可能会误报字符。 这些限制是针对非恶意用户的最合适的障碍。

可创建的特定注册限制包括：

- 最大设备注册数。
- 可注册的设备平台：
  - Android
  - Android 工作配置文件
  - iOS
  - macOS
  - Windows
- 适用于 iOS、Android、Android 工作配置文件和 Windows 的平台操作系统版本。 （仅可使用 Windows 10 版本。 如果允许 Windows 8.1，请将此处留空。）
  - 最低版本。
  - 最高版本。
- 限制个人拥有的设备（仅 iOS、Android、Android 工作配置文件、macOS、Windows）。

## <a name="default-restrictions"></a>默认限制

为设备类型和设备限制注册限制自动提供默认限制。 更改默认选项。 默认限制适用于所有用户和无用户注册。 可通过创建优先级更高的新限制来替代这些默认值。

## <a name="create-a-restriction"></a>创建限制

1. 登录到 Azure 门户。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”。
3. 选择“设备注册” > “注册限制”。
4. 选择“创建限制”。
5. 为该限制提供名称和描述。
6. 选择“限制类型”，然后选择“创建”。
7. 针对设备限制，请选择“设备限制”，设置用户可注册的最大设备数。
8. 针对设备类型限制，请选择“平台”和“平台配置”以允许或阻止各种平台和版本。
9. 选择“分配” > “+ 选择组”。
10. 在“选择组”下，选择一个或多个组，然后选择“选择”。 限制仅适用于它分配到的组。 如果连一个组都没有分配限制，则不会产生任何影响。
11. 选择“保存”。
12. 使用高于默认值的优先级创建新限制。 可[更改优先级](#change-enrollment-restriction-priority)。

## <a name="set-device-type-restrictions"></a>设置设备类型限制

通过执行以下步骤可更改设备类型限制的设置。 这些限制不会影响已注册的设备。 无法使用此功能阻止注册了 [Intune PC 代理](manage-windows-pcs-with-microsoft-intune.md)的设备。

1. 登录到 Azure 门户。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”。
3. 选择“设备注册” > “注册限制”。
4. 在“设备类型限制”下，选择想要设置的限制，然后选择“属性” > “选择平台”。 为列出的每个平台选择“允许”或“阻止”。
    ![允许或阻止平台的屏幕截图](media/enrollment-restrictions-set/platform-allow-block.png)
5. 选择“确定”。
6. 选择“配置平台”。
    ![配置平台的屏幕截图](media/enrollment-restrictions-set/configure-platforms.png)
7. 选择所列平台的最低和最高“版本”。 支持的版本格式包括：
    - Android 工作配置文件支持 major.minor.rev.build。
    - iOS 支持 major.minor.rev。操作系统版本不会应用于使用设备注册计划、Apple School Manager 或 Apple Configurator 应用注册的 Apple 设备。
    - Windows 仅对 Windows 10 支持 major.minor.rev.build。
> [!Note]
> Windows 10 注册过程中不提供生成号，因此对于实例，如果输入 10.0.17134.100 而设备是 10.0.17134.174，则在注册过程中将阻止该实例。
8. 选择是否对每个列出的平台“允许”或“阻止”个人拥有的设备。
9. 选择“确定”。

### <a name="blocking-personal-android-devices"></a>阻止个人 Android 设备
- 如果阻止私人拥有的 Android 设备进行注册，私人拥有的 Android 工作配置文件设备仍可注册。
- 默认情况下，Android 工作配置文件设备的设置与 Android 设备的设置相同。 更改 Android 工作配置文件设置后，则不再相同。
- 如果阻止个人 Android 工作配置文件注册，那么仅公司 Android 设备可注册为 Android 工作配置文件。

### <a name="blocking-personal-windows-devices"></a>阻止个人 Windows 设备
如果阻止个人 Windows 设备注册，Intune 将进行检查以确保每个新 Windows 注册请求都已授权为企业注册。 将阻止未经授权的注册。

如果符合以下条件，则视为已授权为 Windows 企业注册：
 - 注册用户使用的是[设备注册管理员帐户]( device-enrollment-manager-enroll.md)。
- 设备通过 [Windows AutoPilot](enrollment-autopilot.md) 进行注册。
- 该设备已在 Windows Autopilot 中注册，但不是 Windows 设置中的仅 MDM 注册选项。
- 设备的 IMEI 号在“设备注册” > “[公司设备标识符](corporate-identifiers-add.md)”中列出。 （不支持 Windows Phone 8.1。）
- 设备通过[批量预配包](windows-bulk-enroll.md)进行注册。
- 设备通过 GPO 或[从 SCCM 自动注册以执行共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md)进行注册。
 
以下注册被 Intune 标记为企业注册，但由于其不提供 Intune 管理员每设备控制而将被阻止：
 - 通过 [Windows 设置过程中的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)实现的[自动 MDM 注册](windows-enroll.md#enable-windows-10-automatic-enrollment)\*。
- 通过 [Windows 设置中的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)实现的[自动 MDM 注册](windows-enroll.md#enable-windows-10-automatic-enrollment)*。
 
以下个人注册方法也将被阻止：
- 通过[从 Windows 设置中添加工作帐户](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)实现的[自动 MDM 注册](windows-enroll.md#enable-windows-10-automatic-enrollment)\*。
- 通过 Windows 设置中的[仅 MDM 注册]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)选项。

\* 如果通过 Autopilot 注册，则不会受到阻止。

## <a name="set-device-limit-restrictions"></a>设置设备限制

通过执行以下步骤可更改设备限制的设置：

1. 登录到 Azure 门户。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”。
3. 选择“设备注册” > “注册限制”。
4. 在“设备限制”下，选择想要设置的限制。
5. 选择“设备限制”，然后在下拉列表中选择用户可注册的最大设备数。
    ![含设备限制的设备限制边栏选项卡](./media/device-restrictions-limit.png)
6. 选择“保存”。


在 BYOD 注册期间，用户会看到一条通知，告知他们何时达到了已注册的设备限制。 例如，iOS 上的通知如下所示：

![iOS 设备限制通知](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>更改注册限制优先级

当用户在分配有限制的多个组中时，则使用优先级。 用户仅遵循其所在组分配到的最高优先级的限制。 例如，Joe 位于优先级为 5 的限制的 A 组，也位于优先级为 2 的限制的 B 组。 Joe 仅受优先级为 2 的限制约束。

创建限制时，将其添加到默认值正上方的列表中。

设备注册同时包括设备类型和设备限制的默认限制。 这两个限制应用于所有用户，除非由更高优先级的限制替代。

可更改任何非默认限制的优先级。

1. 登录到 Azure 门户。
2. 选择“更多服务”，搜索“Intune”，然后选择“Intune”。
3. 选择“设备注册” > “注册限制”。
4. 将鼠标悬停在优先级列表中的限制上。
5. 使用三个垂直点，将优先级拖到列表中的所需位置。
