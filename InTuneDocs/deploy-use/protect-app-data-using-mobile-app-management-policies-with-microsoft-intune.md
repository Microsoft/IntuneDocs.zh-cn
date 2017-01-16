---
title: "使用 MAM 策略保护应用数据 | Microsoft Docs"
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
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9e208608d50c9b5f7fe66743de0d3c7e741dbfbd
ms.openlocfilehash: c2293306e847148ff7413be3e9eeafb8349e33fe


---

# <a name="protect-app-data-using-mobile-application-management-policies-with-microsoft-intune"></a>通过 Microsoft Intune 使用移动应用管理策略保护应用数据

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>如何保护应用数据
你的员工使用移动设备进行个人任务和工作任务。 既要确保员工高效工作，又希望防止有意和无意的数据丢失。  此外，还希望能够保护员工通过使用不受管理的设备访问的公司数据。

可使用 Intune 移动应用管理 (MAM) 策略帮助保护公司数据。 由于 Intune MAM 策略可**独立于任何移动设备管理 (MDM) 解决方案**使用，因此无论是否在设备管理解决方案中注册设备，都可使用 MAM 来保护公司的数据。 通过实现**应用级别策略**，即可限制对公司资源的访问，并让数据处于 IT 部门的监控范围之内。

可对以下设备上运行的应用配置 MAM 策略：

-   **已在 Microsoft Intune 中注册：**此类设备通常是公司自有设备。

-   **已在第三方 MDM 解决方案中注册：**此类设备通常是公司自有设备。

  > [!NOTE]
  > 不建议在第三方移动应用管理或安全容器解决方案中使用 MAM 策略。

-   **未在任何 MDM 解决方案中注册：**此类设备通常为员工自有设备，且未在 Intune 或其他 MDM 解决方案中管理或注册。

> [!IMPORTANT]
> 可为连接到 Office 365 服务的 Office 移动应用创建移动应用管理策略。 连接到本地 Exchange、Skype for Business 或 SharePoint 服务的应用不支持 MAM 策略。

## <a name="benefits-of-using-mam-policies"></a>使用 MAM 策略的优点

-   **在应用级别保护公司数据。** 由于移动应用管理不需要设备管理，因此可在受管理和不受管理设备上保护公司数据。 管理以用户标识为中心，因而不再需要设备管理。

-   **不会影响最终用户工作效率，且在个人环境中使用应用时不会应用策略。** 这些策略仅应用于工作环境，能够在不接触个人数据的情况下保护公司数据。

将 MDM 与 MAM 策略一起使用还有其他优点，公司可以同时使用 MAM 与 MDM，也可单独使用二者。 例如，员工可能使用公司分发的手机和个人平板电脑。 在这种情况下，公司的手机在 MDM 中注册且受 MAM 策略保护，而个人设备仅受 MAM 策略保护。

- **MDM 确保设备受到保护。** 例如，你可以要求使用 PIN 以访问设备，或将托管应用部署到设备。 还可通过 MDM 解决方案将应用部署到设备，更好地控制应用管理。

- **MAM 策略确保应用层保护措施到位。** 例如，可设置一个策略，要求在工作环境中使用 PIN 打开应用，防止在应用之间共享数据，防止将公司应用数据保存到个人存储位置。

## <a name="devices-that-support-mam"></a>支持 MAM 的设备
当前支持 MAM 策略的设备有：
-   iOS 8.1 或更高版本
-   Android 4 或更高版本

目前不支持 Windows 设备。
##  <a name="how-mam-policies-protect-app-data"></a>MAM 策略如何保护应用数据

###  <a name="apps-without-mam-policies"></a>未实施 MAM 策略的应用

![图像显示当未实施 MAM 策略时数据如何在应用之间自由移动](../media/Apps_without_MAM_policies.png)

在无限制的情况下使用应用时，公司和个人数据可能混合。 公司数据可能最终位于个人存储空间等位置或传输到监控范围之外的应用中，导致数据丢失。 图中的箭头显示了（公司和个人）应用之间和移动到存储位置的无限制数据移动。

### <a name="data-protection-with-mam-policies"></a>通过 MAM 策略保护数据

![图像显示应用 MAM 策略时如何保护公司数据](../media/Apps_with_mobile_app_policies.png)

可使用 MAM 策略防止将公司数据保存到设备的本地存储，并限制将数据移到不受 MAM 策略保护的其他应用中。 MAM 策略设置包括：
- 数据重定位策略，例如**防止另存为**、**限制剪切、复制和粘贴**。
- 访问策略设置，例如**需要简单的 PIN 才能访问**、**阻止在已越狱或取得 root 权限的设备上运行受管理的应用**。

### <a name="data-protection-with-mam-policies-on-devices-that-are-managed-by-a-mdm-solution"></a>在由 MDM 解决方案管理的设备上通过 MDM 策略保护数据

![图像显示 MAM 策略在自有设备 (BYOD) 上的工作原理](../media/MAM_BYOD_November.png)

**对于在 MDM 解决方案中注册的设备**：上图显示 MDM 和 MAM 策略一起提供的保护层。

MDM 解决方案：

-   注册设备。

-   将应用部署到设备。

-   提供持续的设备合规性和管理。

**MAM 策略通过以下功能增添价值：**

-   帮助防止公司数据泄露到使用者应用和服务。

-   将限制（另存为、剪贴板、PIN 等）应用到移动应用。

-   从应用中擦除公司数据，而不从设备中删除这些应用。


### <a name="data-protection-with-mam-policies-for-devices-without-enrollment"></a>用于未注册设备的通过 MAM 策略的数据保护

![显示 MAM 策略如何在托管设备上工作的图像](../media/MAM_ManagedDevices_November.png)

上图显示在未实施 MDM 的情况下数据保护策略在应用级别的工作原理。

对于未在任何 MDM 解决方案中注册的 BYOD 设备，MAM 策略可帮助在应用级别保护公司数据。

但是，有一些限制需要注意，如：

-   无法将应用部署到设备。 用户必须从应用商店获取应用。

-   无法在这些设备上预配证书配置文件。

-   无法在这些设备上设置公司 Wi-Fi 和 VPN 设置。


## <a name="multi-identity"></a>多身份

支持多身份的应用允许用户使用不同的帐户（工作和个人）访问相同的应用，但仅当在工作环境中使用这些应用时，才会应用 MAM 策略。  

例如，当用户使用其工作帐户启动 OneDrive 应用时，无法将文件移到个人存储位置。 但是，当用户通过其个人帐户使用 OneDrive 时，可无限制地从个人 OneDrive 复制和移动数据。  

所有 Office 移动应用都支持多身份访问。

##  <a name="next-steps"></a>后续步骤
- [准备好配置移动应用管理策略](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [使用 Microsoft Intune 创建和部署移动应用管理策略](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


