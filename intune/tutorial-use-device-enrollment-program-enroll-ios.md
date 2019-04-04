---
title: 教程 - 使用设备注册计划在 Intune 中注册 iOS 设备
titleSuffix: Microsoft Intune
description: 在本教程中，将设置 Apple 的 DEP 以在 Intune 中注册 iOS 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9cd0eec492f5131e4015aa64eccb4c081c663ee
ms.sourcegitcommit: 8e6f4acb592dbe5de63aa7642ee9487288740714
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58646465"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>教程：使用设备注册计划在 Intune 中注册 iOS 设备
Apple 的设备注册计划 (DEP) 简化了注册设备过程。 借助 Microsoft Intune 和 DEP，设备会在用户第一次打开设备时自动进行注册。 因此可以向许多用户发送设备，而无需单独设置每个设备。 

在本教程中，你将学习如何执行以下操作：
> [!div class="checklist"]
> * 获取 Apple DEP 令牌
> * 创建 Autopilot 设备组
> * 创建 Autopilot 部署配置文件
> * 将 Autopilot 部署配置文件分配到设备组
> * 将 Windows 设备分配给用户

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件
- 通过 [Apple 设备注册计划](http://deploy.apple.com)购买的设备
- 设置[移动设备管理机构](mdm-authority-set.md)
- 获取 [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>获取 Apple DEP 令牌
在使用 DEP 注册 iOS 设备之前，需要 Apple DEP 令牌 (.pem) 文件。 此令牌允许 Intune 同步有关公司所拥有的 DEP 设备的信息。 还允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

可使用 Apple DEP 门户创建 DEP 令牌。 还可以使用 DEP 门户将设备分配到 Intune 进行管理。

1. 在 [Azure 门户的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Apple 注册” > “注册计划令牌” > “添加”。

2. 选择“我同意”，为 Microsoft 授予向 Apple 发送用户和设备信息的权限。

   ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. 选择“下载公钥”，将加密密钥 (.pem) 文件下载到本地并保存。 .pem 文件用于从 Apple 设备注册计划门户请求信任关系证书。

4. 选择“创建 Apple 设备注册计划令牌”，以打开 Apple 部署计划门户，并使用公司 Apple ID 登录。 可使用此 Apple ID 续订 DEP 令牌。

5.  在 Apple [部署计划门户](https://deploy.apple.com)中，对“设备注册计划”选择“开始”。

4. 在“管理服务器”页上，选择“添加 MDM 服务器”。

5. 对于“MDM 服务器名称”，请输入 TestMDMServer，然后选择“下一步” 。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

6. “添加&lt;服务器名称&gt;”对话框随即打开，提示“上传公钥”。 选择“选择文件…” 以上传 .pem 文件，然后选择“下一步”。

6. 转到“部署计划” > “设备注册计划” > “托管设备”。
7. 在“选择设备依据”下，选择“序列号”。 <!--ask Tiffany about this-->

8. 对于“选择操作”，选择“分配到服务器”，选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后选择“确定”。 Apple 门户将指定的设备分配到 Intune 服务器以进行管理，然后显示“分配完成”。

   在 Apple 门户中，转到“部署计划”&gt;“设备注册计划”&gt;“查看分配历史记录”，以查看设备及其 MDM 服务器分配的列表。

9. 在 Azure 门户的 Intune 中，提供了用于创建此令牌的 Apple ID，以供未来参考。

    ![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/device-enrollment-program-enroll-ios/image03.png)

10. 在“Apple 令牌”框中，浏览到证书 (.pem) 文件，选择“打开”，然后选择“创建”。 

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件
已经安装了令牌，现在可以为 DEP 设备创建注册配置文件。 设备注册配置文件定义注册时应用于设备组的设置。

1. 在 Azure 门户中的 Intune 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”。

2. 选择刚刚安装的令牌，选择“配置文件” > “创建配置文件”。

3. 在“创建配置文件”下，为“名称”输入 TestDEPProfile，为“说明”输入适用于 iOS 设备的测试 DEP。 用户看不到这些详细信息。

4. 对于“用户关联”，请选择“注册用户关联”。 此选项适用于属于希望使用公司门户获取安装应用等服务的用户的设备。

5. 在“使用公司门户而不是 Apple 设置助理进行身份验证”下，选择“否”。

6. 选择“设备管理设置”，然后选择“监管”下的“否”。 受监管的设备提供了更多管理选项，但本教程中用不到这些选项。

7. 选择“确定”。

8. 选择“设置助理自定义”，并为“部门名称”输入“教程部门”。 此字符串是用户在设备激活期间点击“关于配置”时看到的内容。

9. 在“部门电话”下，输入电话号码。 在激活期间中，用户点击“需要帮助”按钮时，会显示该号码。

10. 在设备激活期间，可以“显示”或“隐藏”各种屏幕。 对于本教程，请将“密码”设置为“显示”，将所有其他选项设置为“隐藏”。

11. 选择“确定” > “创建”。

## <a name="sync-managed-devices"></a>同步托管设备

现在可以查看为此令牌分配的设备。

1. 在 Azure 门户的 Intune 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”> 在列表中选择令牌 >“设备” > “同步”。

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>将注册配置文件分配到 iOS 设备

必须先向设备分配注册计划配置文件才能注册他们。

1. 在 Azure 门户的 Intune 中，选择“设备注册” > “Apple 注册” > “注册计划令牌”> 在列表中选择令牌。
2. 选择“设备”> 在列表中选择设备 >“分配配置文件”。
3. 在“分配配置文件”下，为设备选择配置文件，然后选择“分配”。

## <a name="distribute-devices-to-users"></a>将设备分配给用户

已在 Apple 和 Intune 之间设置了管理和同步，并且分配了注册 DEP 设备所需的配置文件。 现在可以将设备分配给用户。 具有用户关联的设备需要每个用户都分配有 Intune 许可证。

## <a name="clean-up-resources"></a>清理资源

如果不想再使用 Autopilot 设备，可以将其删除。

- 如果已在 Intune 中注册设备，必须先[从 Azure Active Directory 门户中删除设备](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)。

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>后续步骤

可以找到有关其他可用于注册 iOS 设备的选项的更多信息。

> [!div class="nextstepaction"]
> [深入了解 iOS DEP 注册文章](device-enrollment-program-enroll-ios.md)
