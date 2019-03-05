---
title: 设置移动设备管理机构
titlesuffix: Microsoft Intune
description: 在 Intune 中设置移动设备管理机构。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99b913b23638a507ed9b0a5cb32afff66679a164
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231904"
---
# <a name="set-the-mobile-device-management-authority"></a>设置移动设备管理机构

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

移动设备管理 (MDM) 机构设置决定了管理设备的方式。 作为 IT 管理员，必须先设置 MDM 机构，然后用户才能注册设备来进行管理。

可能的设置包括：

- **Intune 独立版** - 仅限云的管理，可使用 Azure 门户进行配置。 包括 Intune 提供的所有功能。 [在 Intune 控制台中设置 MDM 机构](#set-mdm-authority-to-intune)。

- **Intune 混合版** - 集成了 Intune 云解决方案和 System Center Configuration Manager。 可使用 Configuration Manager 控制台配置 Intune。 [在 Configuration Manager 中设置 MDM 机构](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。 

    > [!Important]
    >在即将发布的版本中将关闭载入新混合 MDM 客户的功能。 有关详细信息，请参阅博客文章[从混合移动设备管理移动到 Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)。

- **Office 365 的移动设备管理** - 集成了 Office 365 和 Intune 云解决方案。 可在 Office 365 管理中心中配置 Intune。 包括 Intune 独立版中提供的部分功能。 在 Office 365 管理中心中设置 MDM 机构。

> [!IMPORTANT]
> 在 Configuration Manager 版本 1610 或更高版本和 Microsoft Intune 版本 1705 中，你将可以更改 MDM 颁发机构，而无需联系 Microsoft 支持部门，并且无需取消注册并重新注册现有的受管理设备。 有关详细信息，请参阅[准备将 MDM 机构更改为 Configuration Manager](mdm-authority-set.md#prepare-to-change-the-mdm-authority-to-configuration-manager)。

## <a name="set-mdm-authority-to-intune"></a>将 MDM 机构设置为 Intune

如果尚未设置 MDM 权限，请执行以下步骤。 若要从一个 MDM 机构更改为另一个，请参阅以下[更改 MDM 机构](#prepare-to-change-the-mdm-authority-to-configuration-manager)部分。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 选择橙色横幅，打开“移动设备管理机构”设置。 如果尚未设置 MDM 机构，则仅显示橙色横幅。
4. 在“移动设备管理机构”下，从以下选项中选择你的 MDM 机构：
   - Intune MDM 机构
   - Configuration Manager MDM 机构
   - **无**

   ![Intune 移动设备管理机构设置屏幕的屏幕截图](media/set-mdm-auth.png)

   将出现一条消息，表明已成功将 MDM 机构设置为 Intune。

### <a name="workflow-of-intune-administration-ui"></a>Intune 管理 UI 的工作流
启用 Android 或 Apple 设备管理后，Intune 将发送设备和用户信息来与这些第三方服务集成，以便管理其各自的设备。

可以同意共享数据的场景包括：
- 启用 Android 工作配置文件。
- 启用并上传 Apple MDM Push Certificate 时。
- 启用任何诸如设备注册计划、School Manager 或批量采购计划等 Apple 服务时。

不论在哪种情况下，该许可都与运行移动设备管理服务密切相关。 例如，确认 IT 管理员已授权 Google 或 Apple 设备注册。 以下位置提供当新的工作流上线时用于查阅共享了哪些信息的文档：
- [Intune 向 Google 发送的数据](https://aka.ms/Data-intune-sends-to-google)
- [Intune 向 Apple 发送的数据](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>重要注意事项
切换到新的 MDM 机构后，在设备签入并与服务同步之前，可能会有一定的过渡时间（最长八小时）。 需要在新的 MDM 机构（混合）中配置设置，以确保注册的设备在更改后将继续受到管理和保护。 
- 设备必须在更改后与服务连接，以便来自新 MDM 机构（Intune 独立版）的设置可替换设备上的现有设置。
- 更改 MDM 机构后，来自先前 MDM 机构 (Intune Standalone) 的一些基本设置（如配置文件）将在设备上最长保留 7 天，或直到设备首次连接到该服务为止。 建议尽快配置新 MDM 机构（混合）中的应用和设置（策略、配置文件、应用等），并将设置部署到包含具有现有已注册设备的用户的用户组。 更改 MDM 机构后，一旦设备连接到服务，它将从新 MDM 机构接收新设置，并防止在管理和保护方面出现空白。
- 当 Intune 和 Configuration Manager 中存在相同的设备类别时，如果切换到新 MDM 机构，设备的任何设备类别分配都不会随之迁移。 当 MDM 机构更改并且设备显示在 Configuration Manager 控制台中时，若要继续使用设备类别，必须将迁移设备手动添加到适当集合。
- 不会将没有关联用户的设备（通常在具有 iOS 设备注册计划或批处理注册方案时）迁移到新的 MDM 机构。 对于这些设备，需要调用支持以获取将它们移动到新 MDM 机构的帮助。

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>准备将 MDM 机构更改为 Configuration Manager

检查以下信息，准备对 MDM 机构的更改：
- 你必须具有 Configuration Manager 版本 1610 或更高版本才能将 MDM 机构更改为可用。
- 更改为新的 MDM 机构后，设备最多可能需要八小时才能连接到服务。
- 创建一个所有用户当前由 Intune Standalone 托管的 Configuration Manager 用户集合，你将在 Configuration Manager 控制台中设置 Intune 订阅时使用该用户集合。 此集合有助于在更改为 MDM 机构后，确保用户及其设备具有在混合环境中分配和管理的 Configuration Manager 许可证。
- 确保 IT 管理员用户也位于此用户集合中。  
- 在更改之前，MDM 机构将在 Intune 管理控制台中显示为“设置为 Microsoft Intune” (Standalone)。
- 在更改 MDM 机构之前，MDM 机构应在 Microsoft Intune 管理控制台中显示“设置为 Microsoft Intune”（Standalone 租户）。
    > [!NOTE]    
    > 如果 MDM 机构显示由 Intune 和 Office 365 托管，则在将 MDM 机构更改为“Configuration Manager”（混合）时，将不再托管 Office 365 托管的 MDM 设备。 我们建议你在更改 MDM 机构之前，许可 Intune 或 Enterprise Mobility Suite 的这些用户。   

- 在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，删除设备注册管理器角色。 有关详细信息，请参阅[从 Intune 删除设备注册管理器](device-enrollment-manager-enroll.md#remove-device-enrollment-manager-permissions)。
- 请关闭任何已配置的设备组映射。 有关详细信息，请参阅[使用 Microsoft Intune 中的设备组映射对设备进行分类](device-group-mapping.md)。
- 更改 MDM 机构期间应不会对最终用户产生明显影响。 但是，你可能需要将此更改传递给用户，以确保其设备已开机，并在更改后立即与服务连接。 此预防措施将确保尽可能多的设备可尽快通过新机构连接并注册服务。
- 在更改 MDM 机构之前，如果你使用 Intune 独立版管理 iOS 设备，则必须确保已续订先前在 Intune 中使用的同一 Apple Push Notification 服务 (APN) 证书，并再次用于在 Configuration Manager（混合）中设置租户。    

    > [!IMPORTANT]  
    > 如果为混合环境使用不同的 APN 证书，则将取消注册所有以前注册的 iOS 设备，用户将不得不通过该过程重新注册它们。 在更改 MDM 机构之前，请确保你准确了解使用何种 APN 证书来管理 Intune 中的 iOS 设备。 找到 Apple Push Certificates 门户 (https://identity.apple.com) 中列出的相同证书，并确保已标识其 Apple ID 用于创建原始 APN 证书的用户，并且可作为新 MDM 机构更改的一部分续订相同的 APN 证书。

## <a name="change-the-mdm-authority-to-configuration-manager"></a>将 MDM 机构更改为 Configuration Manager

1. 在 Configuration Manager 控制台中，转到“管理”&gt;“概述”&gt;“云服务”&gt;“Microsoft Intune订阅”，然后选择添加 Intune 订阅。
2. 登录到你在 Intune 中设置 MDM 机构时最初使用的 Intune 租户，然后单击“下一步”。
3. 选择“将我的 MDM 机构更改为 Configuration Manager”，然后单击“下一步”。
4. 选择将包含所有用户的用户集合，这些用户将继续由新的混合 MDM 机构托管。
5. 单击“下一步”并完成向导。 MDM 现已机构更改为 Configuration Manager。
6. 使用同一 Intune 租户登录 [Microsoft Intune 管理控制台](http://manage.microsoft.com)，并确认 MDM 机构已更改为“设置为 Configuration Manager”。
7. 将 MDM 机构更改为 Configuration Manager 后，可设置 [iOS 注册](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)和 [Android 注册](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android)。
8. 在 Configuration Manager 控制台中，从新的 MDM 机构（混合）中配置和部署新的设置和应用。

下一次设备连接到服务时，它将同步并从新的 MDM 机构接收新的设置。

## <a name="change-mdm-authority-to-office-365"></a>将 MDM 机构更改为 Office 365

要激活 Office 365 MDM 和现有 Intune 服务，请转到 [https://protection.office.com](https://protection.office.com)，选择“数据丢失防护” > “设备安全性策略” > “查看托管设备列表” > “开始”。

有关详细信息，请参阅[在 Office 365 中设置移动设备管理 (MDM)](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)。

如果希望仅由 Office 365 MDM 管理最终用户，请在激活 Office 365 MDM 后删除所有已分配的 Intune 和/或 EMS 许可证。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 证书过期后的移动设备清理

当移动设备与 Intune 服务通信时，将自动续订 MDM 证书。 如果移动设备被擦除，或者它们在一段时间内无法与 Intune 服务通信，则 MDM 证书将不会续订。 MDM 证书过期 180 天后，设备将从 Azure 门户中删除。

## <a name="remove-mdm-authority"></a>删除 MDM 机构

可将 MDM 机构更改回“未知”。 Microsoft 服务器使用 MDM 机构确定已注册设备的目标报告门户（ConfigMGR、Azure Intune、Office 365 MDM）。

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>更改 MDM 机构的预期结果

- 当 Intune 服务检测到租户的 MDM 机构已更改时，它将向所有已注册的设备发送通知消息，以便签入并与服务同步（此通知并非计划的定期签入）。 因此，租户的 MDM 机构从 Intune standalone 更改为混合环境后，开机且联机的所有设备将与服务连接，接收新的 MDM 机构，并且由混合环境托管。 这些设备的管理和保护不会中断。
- 更改 MDM 机构过程中（或在不久之后），即使设备开机且联机，但设备在新的 MDM 机构中注册到该服务之前，将会有最长八小时的延迟（取决于计划的下次定期签入的执行时间）。    

  > [!IMPORTANT]    
  > 在更改 MDM 机构以及将续订的 APN 证书上传到新机构时，iOS 设备的新设备注册和设备签入将失败。 因此，更改 MDM 机构后，请务必尽快查看并将 APN 证书上传到新机构。

- 用户可以通过手动启动从设备到服务的签入来快速更改为新的 MDM 机构。 用户可以通过使用公司门户应用轻松进行此更改，并启动设备符合性检查。
- 更改 MDM 机构后，要验证设备签入并与服务同步后一切工作正常运行，可在 Configuration Manager 控制台中查找设备。 之前由 Intune 托管的设备现在将显示为 Configuration Manager 平台中的托管设备。    
- 在更改 MDM 机构期间设备处于脱机状态时，以及设备签入服务，会存在一个过渡期。 为帮助确保设备在此过渡期间仍然受到保护并可正常运行，以下配置文件将在设备上最多保留七天（或直到设备与新的 MDM 机构连接并接收将覆盖现有设置的新设置为止）：
    - 电子邮件配置文件
    - VPN 配置文件
    - 证书配置文件
    - Wi-Fi 配置文件
    - 配置文件
- 更改为新的 MDM 机构后，Microsoft Intune 管理控制台中的符合性数据可能需要长达一周的时间才能准确报告。 但是，Azure Active Directory 和设备上的符合性状态是准确的，因此，设备仍将受到保护。
- 确保用于覆盖现有设置的新设置与以前的设置具有相同的名称，以确保覆盖旧设置。 否则，设备可能会出现冗余配置文件和策略。    

  > [!TIP]    
  > 作为最佳做法，你应该在 MDM 机构更改完成后立即创建所有管理设置和配置以及部署。 这有助于确保在过渡期间对设备进行保护和主动管理。

-  更改 MDM 机构后，请执行以下步骤来验证新设备是否成功注册到新的机构：   
    - 注册新设备
    - 确保新注册的设备显示在 Configuration Manager 控制台中。
    - 执行一个从管理控制台到设备的操作，如远程锁定。 如果成功，则表示该设备将由新的 MDM 机构管理。
- 如果你对特定设备有疑问，则可以取消注册然后重新注册设备，以使其连接到新的机构并尽快接受管理。

## <a name="next-steps"></a>后续步骤

设置 MDM 机构后即可开始[注册设备](device-enrollment.md)。
