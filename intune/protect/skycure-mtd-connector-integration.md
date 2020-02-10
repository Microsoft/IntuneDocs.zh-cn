---
title: 使用 Microsoft Intune 设置 Symantec 集成
titleSuffix: Microsoft Intune
description: 如何使用 Microsoft Intune 设置 Symantec Endpoint Protection Mobile 解决方案以控制移动设备对公司资源的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19c1bb959212ebeaea40f7089cba5533b6efeb71
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912601"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>设置 Symantec Endpoint Protection Mobile 与 Intune 的集成

完成以下步骤将 Symantec Endpoint Protection Mobile (SEP Mobile) 解决方案与 Intune 集成。 你需要将 SEP Mobile 应用添加到 Azure AD，以具备单一登录功能。

> [!NOTE]
> 未注册的设备不支持此移动威胁防御供应商。

## <a name="before-you-begin"></a>在开始之前

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>用于集成 Intune 和 SEP Mobile 的 Azure AD 帐户

- 在启动 SEP Mobile 基本设置流程前，请务必在 [Symantec Endpoint Protection Mobile 管理控制台](https://aad.skycure.com)中正确配置 Azure AD 帐户。
- Azure AD 帐户必须是全局管理员帐户才能执行集成。
### <a name="network-setup"></a>网络设置

可以参考 Symantec 文章[在安装后配置 SEP 管理器](https://support.symantec.com/us/en/article.HOWTO80819.html)，确保你的网络已正确配置以便与 SEP Mobile 设置集成。

### <a name="full-integration-vs-read-only"></a>完全集成与只读

SEP Mobile 支持与 Intune 集成的两种模式：

- **只读集成(基本设置)：** 仅列出来自 Azure Active Directory 的设备并在 Symantec Endpoint Protection Mobile 管理控制台中对其进行填充。
<br>
  - 如果在 Symantec Endpoint Protection Mobile 管理控制台中未选中“向 Intune 报告设备的运行状况和风险”  和“同时向 Intune 报告安全事件”  框，集成将为只读模式，并因此绝不会更改 Intune 中的设备状态（符合或不符合）。
<br></br>
- **完全集成：** 允许 SEP Mobile 向 Intune 报告设备风险和安全事件详细信息，这将在两个云服务中之间创建双向通信。

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>SEP Mobile 应用如何与 Azure AD 和 Intune 一起使用？

- **iOS 应用：** 允许最终用户使用 iOS 应用登录到 Azure AD。

- **Android 应用：** 允许最终用户使用 Android 应用登录到 Azure AD。

- **管理应用：** 这是 SEP Mobile Azure AD 多租户应用，可实现与 Intune 之间的服务到服务通信。

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>设置 Intune 与 SEP Mobile 之间的只读集成

> [!IMPORTANT]
> SEP Mobile 管理员凭据必须包含属于 Azure Active Directory 中有效用户的电子邮件帐户，否则登录失败。 EP Mobile 使用 Azure Active Directory 对使用单一登录 (SSO) 的管理员进行身份验证。

1. 转至 [Symantec Endpoint Protection Mobile 管理控制台](https://aad.skycure.com)。

2. 输入你的“SEP Mobile 管理员凭据”  ，然后选择“继续”  。

3. 转到“设置”  ，选择“Intune 集成”  下的“基本设置”  。

4. 在  “iOS 应用”旁边，选择  “添加到 Active Directory”。

    ![Symantec Endpoint Protection Mobile 管理控制台的示意图](./media/skycure-mtd-connector-integration/symantec-portal-basic-add.png)

5. 登录页打开后，输入你的 Intune 凭据，然后选择“接受”  。

    ![iOS 应用 Intune 登录提示的图像](./media/skycure-mtd-connector-integration/symantec-portal-basic-accept.png)

6. 将应用添加到 Azure AD 后，你将会看到该应用已成功添加的指示。

    ![iOS 应用完成屏幕的图像](./media/skycure-mtd-connector-integration/symantec-portal-basic-added.png)

7. 对 SEP Mobile Android  和  “管理”应用重复这些步骤。

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>将 Azure AD 安全组添加到 SEP Mobile

需要添加 Azure AD 安全组，其中包含运行 SEP Mobile 的所有设备。

- 输入并选择运行 SEP Mobile 的设备的所有安全组，然后保存更改。

    ![显示 SEP Mobile 应用用户组的图像](./media/skycure-mtd-connector-integration/symantec-portal-basic-groups.png)

SEP Mobile 将运行其移动威胁防御服务的设备与 Azure AD 安全组同步。

![SEP Mobile 管理控制台上的安全组配置的示意图](./media/skycure-mtd-connector-integration/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>设置 Intune 和 SEP Mobile 之间的完全集成

### <a name="retrieve-the-directory-id-in-azure-ad"></a>在 Azure AD 中检索目录 ID

1. 登录到 [Azure 门户](https://portal.azure.com)。

2. 在搜索框中键入“Active Directory”，然后选择 Azure Active Directory  。

3. 选择“属性”  。

4. 在  “目录 ID”旁边，选择复制图标，然后将其粘贴到安全位置。 在稍后的步骤中将需要使用此标识符。

    ![在 Azure 门户中显示目录 ID 的图像](./media/skycure-mtd-connector-integration/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>（可选）为需要运行 SEP Mobile 应用的设备创建专用安全组
1. 在 [Azure 门户](https://portal.azure.com)的  “管理”下，选择“用户和组”  ，然后选择“所有组”  。

2. 选择  “添加”按钮。 键入组“名称”  。 在  “成员资格类型”下，选择“分配”  。

3. 在  “成员”边栏选项卡中，选择组成员，然后选择  “选择”按钮。

4. 在“组”  边栏选项卡中，选择“创建”  。

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>设置 Symantec Endpoint Protection Mobile 与 Intune 之间的集成

1. 转至 [Symantec Endpoint Protection Mobile 管理控制台](https://aad.skycure.com)。

2. 输入你的“SEP Mobile 管理员凭据”  ，然后选择“继续”  。

3. 转至“设置”   >   “集成” >   “Intune” >   “EMM 集成选择”部分。

4. 在  “目录 ID”框中，粘贴你在上一节中从 Azure Active Directory 复制的目录 ID 并保存设置。

    ![在 SEP Mobile 门户中显示目录 ID 的图像](./media/skycure-mtd-connector-integration/symantec-portal-directory-ID.png)

5. 转至“设置”   >   “集成” >   “Intune” >   “基本设置”部分。

6. 在  “iOS 应用”旁边，选择  “添加到 Active Directory”。

    ![显示将 iOS 应用添加到 Active Directory 的图像](./media/skycure-mtd-connector-integration/symantec-portal-basic-add.png)

7. 使用管理目录的 Office 365 帐户的 Azure Active Directory 凭据登录。

8. 选择  “接受”按钮，将 SEP Mobile iOS 应用添加到 Azure Active Directory。

    ![显示接受按钮的图像](./media/skycure-mtd-connector-integration/symantec-portal-basic-accept.png)

9. 对“Android 应用”  和  “管理应用”重复相同的过程。

10. 选择需要运行 SEP Mobile 应用的所有用户组，例如你之前创建的安全组。

    ![显示 SEP Mobile 应用用户组的图像](./media/skycure-mtd-connector-integration/symantec-portal-basic-groups.png)

11. SEP Mobile 会同步所选组中的设备并开始向 Intune 报告信息。 可以在“完全集成”部分查看这些数据。 转至“设置”   >   “集成” >   “Intune” >   “完全集成”部分。

     ![显示已完成的 SEP Mobile 完全集成的图像](./media/skycure-mtd-connector-integration/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>后续步骤

[设置 SEP Mobile 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
