---
title: "使用 MAM 策略保护应用数据"
description: "本主题说明移动应用管理策略如何帮助保护公司数据、防止数据丢失，以及分别保存个人和工作信息。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 23dca24c69cca3c7a2851cb3fa7d9959f31df8e7
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="protect-app-data-using-app-protection-policies-with-microsoft-intune"></a>通过 Microsoft Intune 使用应用保护策略保护应用数据

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>如何保护应用数据
你的员工使用移动设备进行个人任务和工作任务。 既要确保员工高效工作，又希望防止有意和无意的数据丢失。  此外，还希望能够保护员工通过使用不受管理的设备访问的公司数据。

可使用 Intune 应用保护策略帮助保护公司数据。 由于 Intune 应用保护策略可以**独立于任何移动设备管理 (MDM) 解决方案**使用，所以无论是否在设备管理解决方案中注册设备，都可用 MAM 保护公司的数据。 通过实现**应用级别策略**，即可限制对公司资源的访问，并让数据处于 IT 部门的监控范围之内。

可对以下设备上运行的应用配置应用保护策略：

-   **已在 Microsoft Intune 中注册：**此类设备通常是公司自有设备。

-   **已在第三方 MDM 解决方案中注册：**此类设备通常是公司自有设备。

    > [!NOTE]
    > 不建议在第三方移动应用程序管理或安全容器解决方案中使用应用保护策略。

-   **未在任何 MDM 解决方案中注册：**此类设备通常为员工自有设备，且未在 Intune 或其他 MDM 解决方案中管理或注册。

> [!IMPORTANT]
> 可为连接到 Office 365 服务的 Office 移动应用创建应用保护策略。 连接到本地 Exchange、Skype for Business 或 SharePoint 服务的应用不支持应用保护策略。

## <a name="benefits-of-using-app-protection-policies"></a>使用应用保护策略的优点

-   **在应用级别保护公司数据。** 由于移动应用管理不需要设备管理，因此可在受管理和不受管理设备上保护公司数据。 管理以用户标识为中心，因而不再需要设备管理。

-   **不会影响最终用户工作效率，且在个人环境中使用应用时不会应用策略。** 这些策略仅应用于工作环境，能够在不接触个人数据的情况下保护公司数据。

将 MDM 与应用保护策略一起使用还有其他优点，公司可以同时使用 MAM 与 MDM，也可单独使用二者。 例如，员工可能使用公司分发的手机和个人平板电脑。 在这种情况下，公司的手机在 MDM 中注册且受应用保护策略保护，而个人设备仅受应用保护策略保护。

- **MDM 确保设备受到保护。** 例如，你可以要求使用 PIN 以访问设备，或将托管应用部署到设备。 还可通过 MDM 解决方案将应用部署到设备，更好地控制应用管理。

- **应用保护策略确保应用层保护措施到位。** 例如，可设置一个策略，要求在工作环境中使用 PIN 打开应用，防止在应用之间共享数据，防止将公司应用数据保存到个人存储位置。

## <a name="devices-that-support-mam"></a>支持 MAM 的设备
当前支持应用保护策略的设备有：
-   iOS 8.1 或更高版本
-   Android 4 或更高版本

>[!NOTE]
>在无注册方案的情况下，MAM 中不支持 Windows 设备。 但是，使用 Intune 注册 Windows 10 设备时，可以使用 Windows 信息保护，它提供了类似功能。 有关详细信息，请参阅[使用 Windows 信息保护 (WIP) 保护企业数据](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。


##  <a name="how-app-protection-policies-protect-app-data"></a>应用保护策略如何保护应用数据

###  <a name="apps-without-app-protection-policies"></a>不具有应用保护策略的应用

![图像显示在未实施应用保护策略时，数据如何在应用之间自由移动](../media/Apps_without_MAM_policies.png)

在无限制的情况下使用应用时，公司和个人数据可能混合。 公司数据可能最终位于个人存储空间等位置或传输到监控范围之外的应用中，导致数据丢失。 图中的箭头显示了（公司和个人）应用之间和移动到存储位置的无限制数据移动。

### <a name="data-protection-with-app-protection-policies"></a>采用应用保护策略的数据保护

![图像显示在应用应用保护策略时保护公司数据的方式](../media/Apps_with_mobile_app_policies.png)

可以使用应用保护策略来防止将公司数据保存到设备的本地存储器上，并限制将数据移动到不受应用保护策略保护的其他应用中。 应用保护策略设置包括：
- 数据重定位策略，例如**防止另存为**、**限制剪切、复制和粘贴**。
- 访问策略设置，例如**需要简单的 PIN 才能访问**、**阻止在已越狱或取得 root 权限的设备上运行受管理的应用**。

### <a name="data-protection-with-app-protection-on-devices-that-are-managed-by-a-mdm-solution"></a>在由 MDM 解决方案管理的设备上通过应用保护策略保护数据

![图像显示应用保护策略在自有设备 (BYOD) 上的工作原理](../media/MAM_BYOD_November.png)

**对于在 MDM 解决方案中注册的设备**：上图显示 MDM 和应用保护策略一起提供的保护层。

MDM 解决方案：

-   注册设备。

-   将应用部署到设备。

-   提供持续的设备合规性和管理。

**应用保护策略增加价值的原因：**

-   帮助防止公司数据泄露到使用者应用和服务。

-   将限制（另存为、剪贴板、PIN 等）应用到移动应用。

-   从应用中擦除公司数据，而不从设备中删除这些应用。


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>采用上适用于未注册设备的应用保护策略保护数据

![图像显示应用保护策略如何在托管设备上起作用](../media/MAM_ManagedDevices_November.png)

上图显示在未实施 MDM 的情况下数据保护策略在应用级别的工作原理。

对于未在任何 MDM 解决方案中注册的 BYOD 设备，应用保护策略可在应用级别帮助保护公司数据。

但是，有一些限制需要注意，如：

-   无法将应用部署到设备。 用户必须从应用商店获取应用。

-   无法在这些设备上预配证书配置文件。

-   无法在这些设备上设置公司 Wi-Fi 和 VPN 设置。


## <a name="multi-identity"></a>多身份

支持多身份的应用允许用户使用不同的帐户（工作和个人）访问相同的应用，但仅当在工作环境中使用这些应用时，才会应用应用保护策略。  

例如，当用户使用其工作帐户启动 OneDrive 应用时，无法将文件移到个人存储位置。 但是，当用户通过其个人帐户使用 OneDrive 时，可无限制地从个人 OneDrive 复制和移动数据。  

- 了解支持 Intune 的 [MAM 和多身份](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的应用的详细信息。

##  <a name="next-steps"></a>后续步骤
- [准备好配置应用保护策略](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [使用 Microsoft Intune 创建和部署应用保护策略](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
