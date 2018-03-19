---
title: "使用 Microsoft Intune 设置 Skycure 集成"
titlesuffix: 
description: "如何使用 Microsoft Intune 设置 Skycure 移动威胁防御 (MTD) 解决方案以控制移动设备对公司资源的访问。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a09806afae72f60961a94ab27707b4851006cf0
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="set-up-the-skycure-integration-with-intune"></a>使用 Intune 设置 Skycure 集成

完成以下步骤以将 Skycure 移动威胁防御解决方案与 Intune 相集成。 你需要将 Skycure 应用添加到 Azure AD，以具备单一登录功能。

## <a name="before-you-begin"></a>在开始之前

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>用于集成 Intune 和 Skycure 的 Azure AD 帐户

-   在启动 Skycure 基本设置流程前，请务必在 [Skycure管理控制台](https://aad.skycure.com)中正确配置 Azure AD 帐户。

### <a name="full-integration-vs-read-only"></a>完全集成与只读

Skycure 支持与 Intune 集成的两种模式：

-   **只读集成（基本设置）：**仅列出来自 Azure Active Directory 的设备清单并在 Skycure 控制台中对其进行填充。
<br>
    -   如果在 Skycure 管理控制台中未选中“向 Intune 报告设备的运行状况和风险”和“同时向 Intune 报告安全事件”框，集成将为只读模式，并因此绝不会更改 Intune 中的设备状态（符合或不符合）。
<br></br>
-   **完整集成：**允许 Skycure 向 Intune 报告设备风险和安全事件详细信息，这将在两个云服务中之间创建双向通信。

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>Skycure 应用如何与 Azure AD 和 Intune 一起使用？

-   **iOS 应用：**允许最终用户使用 iOS 应用登录到 Azure AD。

-   **Android 应用：**允许最终用户使用 Android 应用登录到 Azure AD。

-   **管理应用：**这是 Skycure Azure AD 多租户应用，可实现与 Intune 之间的服务到服务通信。

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>在 Intune 和 Skycure 之间设置只读集成

> [!IMPORTANT]
> Skycure 管理员凭据是必须属于 Azure Active Directory 中有效用户的电子邮件，否则登录失败。 Skycure 使用 Azure Active Directory 对使用单一登录 (SSO) 的管理员进行身份验证。

1.  转到 [Skycure 管理控制台](https://aad.skycure.com)。

2.  输入你的“Skycure 管理员凭据”，然后单击“继续”。

3.  转到“设置”，选择“Intune 集成”下的“基本设置”。

4.  在“iOS 应用”标签上，单击“添加到 Active Directory”。

    ![Skycure 管理控制台上的 iOS 应用的图像](./media/skycure-setup-1.png)

5.  登录页打开后，输入你的 Intune 凭据，然后单击“接受”。

    ![iOS 应用 Intune 登录提示的图像](./media/skycure-setup-2.png)

6.  将应用添加到 Azure AD 后，可以看到应用已成功添加到 Skycure 管理控制台上 Azure AD 的提示。

    ![iOS 应用完成屏幕的图像](./media/skycure-setup-3.png)

> [!NOTE]
> 为 **Skycure Android** 应用和**管理**应用重复相同的过程。

### <a name="add-an-azure-ad-security-group-into-skycure"></a>将 Azure AD 安全组添加到 Skycure

需要添加 Azure AD 安全组，其中包含运行 Skycure 的所有设备。

-  输入并选择运行 Skycure 的设备的所有安全组，然后单击“应用更改”。

    ![显示配置安全组 Skycure 管理控制台的位置的图像](./media/skycure-setup-4.png)

Skycure 将运行其移动威胁防御服务的设备与 Azure AD 安全组同步。

![显示 Skycure 管理控制台上已完成的安全组配置的图像](./media/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>在 Intune 和 Skycure 之间设置完全集成

1.  转到 [Skycure 管理控制台](https://aad.skycure.com)。

2.  输入你的“Skycure 管理员凭据”，然后单击“继续”。

3.  转到“设置”，选择“Intune 集成”下的“完全集成”。

4.  检查以下设置：

    a.  向 Intune 报告设备的运行状况和风险

    b.  此外，向 Intune 报告安全事件

5.  单击“应用更改”。

    ![显示已完成的 Skycure 完全集成的图像](./media/skycure-setup-6.png)

## <a name="next-steps"></a>后续步骤

[设置 Skycure 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
