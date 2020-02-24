---
title: 注册 iOS/iPadOS 设备 - 用户注册
titleSuffix: Microsoft Intune
description: 了解如何设置 iOS/iPadOS 和 iPadOS 用户注册。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
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
ms.openlocfilehash: d22d8d4772754fddbd366610402d64acc28ffc65
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415268"
---
# <a name="set-up-iosipados-and-ipados-user-enrollment-preview"></a>设置 iOS/iPadOS 和 iPadOS 用户注册（预览版）

可以将 Intune 设置为使用 Apple 的用户注册过程注册 iOS/iPadOS 和 iPadOS 设备。 与其他注册方法相比，用户注册为管理员提供部分简化的管理选项。

有关用户注册可用的选项的详细信息，请参阅[用户注册支持的操作、密码和其他选项](ios-user-enrollment-supported-actions.md)。

> [!NOTE]
> Intune 中对 Apple 用户注册的支持目前处于预览状态。

## <a name="prerequisites"></a>必备条件
- [移动设备管理 (MDM) 机构](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- [托管的 Apple ID](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web)。

## <a name="create-a-user-enrollment-profile-in-intune"></a>在 Intune 中创建用户注册配置文件

注册配置文件定义注册时应用于设备组的设置。 

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “iOS”   > “iOS 注册”   > “注册类型(预览)”   > “创建配置文件”   > “iOS/iPadOS”  。 此配置文件将说明 iOS/iPadOS 和 iPadOS 最终用户在未通过公司 Apple 方法注册的设备上的注册体验。 如果你想要进行更改，可以在创建此配置文件后对其进行编辑。

    ![创建 Apple 注册配置文件](./media/ios-user-enrollment/create-profile.png)

2. 在“基本信息”  页上，输入配置文件的“名称”  和“说明”  ，以便于管理。 用户看不到这些详细信息。 可以使用此“名称”字段在 Azure Active Directory 中创建动态组  。 使用配置文件名称定义 enrollmentProfileName 参数，以向设备分配此注册配置文件。 详细了解 [Azure Active Directory 动态组](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices)。

    ![“基本信息”页](./media/ios-user-enrollment/basics-page.png)


3. 选择“下一步”  。

4. 在“设置”  页面中，选择“注册类型”  的下列选项之一：

    ![“设置”页面](./media/ios-user-enrollment/settings-page.png)

    - **设备注册**：此配置文件中的所有用户都将使用设备注册。
    - **用户注册**：此配置文件中的所有用户都将使用用户注册。
    - **基于用户选择进行确定**：将为此组中的所有用户提供要使用的注册类型。 当用户注册其设备时，他们可以在“我拥有此设备”  和“(公司)拥有此设备”  之间看到一个可选择的选项。 如果他们选择了前者，设备将使用设备注册进行注册。 如果用户选择“我拥有此设备”  ，则他们还可以选择保护整个设备或仅保护与工作相关的应用程序和数据。 最终用户选择是否拥有设备确定在其设备上实现哪些注册类型。 此用户选项反映在 Intune 中的“设备所有权”属性中。 若要了解有关用户体验的详细信息，请参阅[设置 iOS/iPadOS 设备对公司资源的访问](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)。
    
5. 选择“下一步”  。

6. 在“分配”  页上，选择包含要为其分配此配置文件的用户的用户组。 可以选择将配置文件分配给所有用户或特定组。 选定组中的所有用户都将使用上面选择的注册类型。 用户注册方案不支持设备组，因为该功能基于用户标识，而不是设备。 可以选择将配置文件分配给所有用户或特定组。

    ![“分配”页](./media/ios-user-enrollment/assignments-page.png)

7. 选择“下一步”  。

8. 在“查看和创建”  页上，查看你的选择，然后选择“创建”  以将配置文件分配给用户。

    ![“分配”页](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>配置文件优先级

创建多个注册类型配置文件后，可以更改应用的优先级顺序。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “iOS”   > “iOS 注册”   > “注册类型(预览)”  。
2. 按你希望应用的顺序拖放列表中的配置文件。

如果任何用户的配置文件之间发生冲突，则会为用户应用较高优先级的配置文件。


