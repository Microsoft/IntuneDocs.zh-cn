---
title: 引导式方案 - 云托管的新式桌面
titleSuffix: Microsoft Intune
description: 在 Microsoft 365 设备管理门户中了解关于设置和配置基本新式桌面的引导式方案。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f78f3696827ebd50084f0e4b012c5f94427eeb35
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164560"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>引导式方案 - 云托管的新式桌面

新式桌面是适用于信息工作者的最先进的生产力平台。 Office 365 专业增强版和 Windows 10 是新式桌面的核心组件，也是适用于 Windows 10 和 Microsoft Defender 高级威胁防护的最新安全基线。 

通过云管理新式桌面，增加在 Internet 范围内远程操作的额外优势。 云管理使用内置的 Windows 移动设备管理策略并且删除了对本地 Active Directory 组策略的依赖。 

如果要在自己的组织中评估云托管的新式桌面，此引导式方案将为基本部署预定义所有必要的配置。 在这一引导式方案中，你将创建一个安全的环境，并在其中试用 Intune 设备管理功能。 

## <a name="prerequisites"></a>必备条件
- [将 MDM 机构设置为 Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) - 移动设备管理 (MDM) 机构设置决定了管理设备的方式。 作为 IT 管理员，必须先设置 MDM 机构，然后用户才能注册设备来进行管理。
- 至少为 M365 E3（或 M365 E5 以获得最佳安全性）
- Windows 10 1903 设备（使用 Windows Autopilot 进行注册以获得最佳的最终用户体验）
- 完成此引导式方案所需的 Intune 管理员权限：
  - 设备配置读取、创建、删除、分配和更新
  - 注册程序读取设备、读取配置文件、创建配置文件、分配配置文件、删除配置文件
  - 移动应用读取、创建、删除、分配和更新
  - 组织读取和更新
  - 安全基线读取、创建、删除、分配和更新
  - 策略集读取、创建、删除、分配和更新

## <a name="step-1---introduction"></a>步骤 1 - 简介

使用此引导式方案，你将设置测试用户，在 Intune 中注册设备，并使用 Intune 建议的设置以及 Windows 10 和 Office 专业增强版部署该设备。 如果选择[在 Intune 中启用此保护](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune)，则还将为设备配置 Microsoft Defender 高级威胁防护。 设置的用户和注册的设备将被添加到一个新的安全组中，并且将使用推荐设置进行配置，以便提高安全性和生产力。 

### <a name="what-you-will-need-to-continue"></a>需要继续执行的操作

必须在此引导式方案中提供测试设备和测试用户。 请确保已完成以下任务：
- 在 Azure Active Directory 中设置测试用户帐户。
- 创建运行 Windows 10 版本 1903 或更高版本的测试设备。
- （可选）[使用 Windows Autopilot 注册测试设备](~/enrollment/enrollment-autopilot.md#add-devices)。
- （可选）允许[为组织的 Azure Active Directory 登录页添加品牌](https://go.microsoft.com/fwlink/?linkid=2102455)。

## <a name="step-2---user"></a>步骤 2 - 用户

选择要在设备上设置的用户。 此人将是设备的主要用户。

如果要将更多用户或设备添加到此配置，只需将用户和设备添加到由向导生成的 AAD 安全组即可。 与其他引导式方案不同，由于该配置不可自定义，因此无需多次运行向导。 只需将更多用户和设备添加到创建的 AAD 组即可。 完成该向导后，你将能够查看使用部署的建议策略生成的组。 

## <a name="step-3---device"></a>步骤 3 - 设备

确保设备运行 Windows 10 版本 1903 或更高版本。  主要用户在收到设备时将需要对其进行设置。 用户可以使用两个设置选项。 

### <a name="option-a--windows-autopilot"></a>选项 A - Windows Autopilot
Windows Autopilot 自动配置新设备，这样用户就可以在无需 IT 人员帮助的情况下立即对其进行设置。 如果设备已使用 Windows Autopilot 注册，请按设备序列号进行选择。 有关使用 Windows Autopilot 的详细信息，请参阅[使用 Windows Autopilot 注册设备（可选）](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional)。

### <a name="option-b--manual-device-enrollment"></a>选项 B - 手动注册设备
用户将在移动设备管理中手动设置并注册其新设备。 完成此方案后，请重置设备并为主要用户提供有关 Windows 设备的注册说明。 有关详细信息，请参阅[在首次运行体验期间将 Windows 10 设备加入 Azure AD](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device)。

## <a name="step-4---review--create"></a>步骤 4 - 查看 + 创建

通过最后一个步骤可以查看配置的设置摘要。 查看你的选择后，请单击“部署”以完成引导式方案  。 引导式方案完成后，系统将显示一个资源表。 可以稍后编辑这些资源，但退出“摘要”视图后，该表将不会保存。

> [!IMPORTANT]
> 引导式方案完成后，系统将显示摘要。 可以稍后修改摘要中列出的资源，但是将不会保存显示这些资源的表。

### <a name="verification"></a>验证
1. 验证所选内容是否为已分配 MDM 用户范围
    - 确保 [MDM 用户作用域](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment)为：
        - 为 **Microsoft Intune** 应用设置为 **“全部”** ，或
        - 设置为“部分”  。 另外，添加此引导式方案创建的用户组。
2. 验证所选用户是否能够将设备加入到 Azure Active Directory。
    - 确保 AAD 加入为：
        - 设置为“全部”，或 
        - 设置为“部分”  。 同时添加此引导式方案创建的用户组。
3. 在设备上按照以下相关步骤将其加入 Azure AD：
    - 使用 Autopilot。 有关详细信息，请参阅 [Windows Autopilot 用户驱动模式](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)。
    - 不使用 Autopilot：有关详细信息，请参阅[在首次运行体验期间将 Windows 10 设备加入 Azure AD](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device)。

### <a name="what-happens-when-i-click-deploy"></a>单击“部署”时会发生什么情况？
用户和设备将被添加到新的安全组。 还将使用 Intune 推荐的设置对用户和设备进行配置，以提高公司或学校的安全性和生产力。 用户将设备加入 Azure AD 后，其他应用和设置将添加到设备中。 若要了解有关这些附加配置的详细信息，请参阅[快速入门：注册 Windows 10 设备](~/enrollment/quickstart-enroll-windows-device.md)。

## <a name="additional-information"></a>其他信息

### <a name="register-device-with-windows-autopilot-optional"></a>使用 Windows Autopilot 注册设备（可选）

可以选择使用已注册的 Autopilot 设备。 对于 Autopilot，此引导式方案将分配 Autopilot 部署配置文件和注册状态页配置文件。 Autopilot 部署配置文件配置如下：
- 用户驱动模式 - 即要求最终用户在 Windows 安装过程中输入用户名和密码。
- Azure AD 联接。
- 自定义 Windows 设置：
  - 隐藏 Microsoft 软件许可条款屏幕
  - 隐藏隐私设置 
  - 在没有本地管理员权限的情况下创建用户的本地配置文件
  - 隐藏公司登录页面上的“更改帐户”选项

“注册状态”页面将配置为只对 Autopilot 相关设备启用，并且不会阻止等待所有要安装的应用。

引导式方案还将用户分配到所选的 Autopilot 设备，以提供个性化的设置体验。

#### <a name="post-requisites"></a>后置条件
用户将设备加入 Azure Active Directory 后，以下配置将应用于该设备：
1. Office 365 专业增强版将自动安装在云托管的电脑上。 其中包括熟悉的应用程序，包括 Access、Excel、OneNote、Outlook、PowerPoint、Publisher、Skype for Business 和 Word。 你可以使用这些应用程序连接到 SharePoint Online、Exchange Online 和 Skype for Business Online 等 Office 365 服务。 与非订阅版本的 Office 不同，Office 365 专业增强版会定期更新新功能。 有关新功能的列表，请参阅 Office 365 中的新增功能。
2. Windows 安全基线将安装在云托管的电脑上。 如果已设置 Microsoft Defender 高级威胁防护，则该引导式方案还将配置 Defender 的基线设置。 Defender 高级威胁防护向 Windows 10 安全堆栈提供了新的泄露后保护层。 结合 Windows 10 中内置的客户端技术和强大的云服务，它将有助于检测已越过其他防御措施的威胁。 

## <a name="next-steps"></a>后续步骤

- 如果使用的是 Microsoft Defender 高级威胁检测，请创建 [Intune 符合性策略](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy)以要求 Defender 威胁分析满足符合性要求。
- 如果设备不满足 Intune 符合性，请创建[基于设备的条件访问策略](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy)以阻止访问。
