---
title: 教程 - 使用 Apple 商务管理或设备注册计划在 Intune 中注册 iOS 设备
titleSuffix: Microsoft Intune
description: 在本教程中，你将从 ABM 中设置 Apple 的公司设备注册功能以在 Intune 中注册 iOS 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc950f9e60f5549a7a74c2963f33c36369d3ebd3
ms.sourcegitcommit: 5c52879f3653e22bfeba4eef65e2c86025534dab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2019
ms.locfileid: "74126166"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>教程：使用 Apple 商务管理 (ABM) 中的 Apple 公司设备注册功能在 Intune 中注册 iOS 设备
Apple 商务管理中的设备注册功能简化了注册设备过程。 Intune 还支持 Apple 的旧版设备注册计划 (DEP) 门户，但我们鼓励使用 Apple 商务管理重新开始注册。 借助 Microsoft Intune 和 Apple 公司设备注册，设备会在用户第一次打开设备时自动安全地进行注册。 因此可以向许多用户发送设备，而无需单独设置每个设备。 

在本教程中，你将学习如何执行以下操作：
> [!div class="checklist"]
> * 获取 Apple 设备注册令牌
> * 将托管设备同步到 Intune
> * 创建注册配置文件
> * 将注册配置文件分配到设备

如果没有 Intune 订阅，请[注册免费试用帐户](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件
- 在 [Apple 商务管理](https://business.apple.com)或 [Apple 的设备注册计划](http://deploy.apple.com)中购买的设备
- 设置[移动设备管理机构](../fundamentals/mdm-authority-set.md)
- 获取 [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>获取 Apple 设备注册令牌
在使用 Apple 的公司注册功能注册 iOS 设备之前，需要拥有 Apple 设备注册令牌 (.pem) 文件。 此令牌允许 Intune 同步有关公司所拥有的 Apple 设备的信息。 还允许 Intune 将注册配置文件上传至 Apple，并向设备分配这些配置文件。

可以使用 ABM 或 DEP 门户创建设备注册令牌。 还可以使用门户将设备分配到 Intune 以进行管理。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备注册”   > “Apple 注册”   > “注册程序令牌”   > “添加”  。

2. 选择“我同意”，为 Microsoft 授予向 Apple 发送用户和设备信息的权限  。

   ![Apple 证书工作区中用于下载公钥的“注册计划令牌”窗格的屏幕截图。](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. 选择“下载公钥”，将加密密钥 (.pem) 文件下载到本地并保存  。 .pem 文件用于从 ABM 或 DEP 门户请求信任关系证书。

4. 选择“创建 Apple 设备注册计划令牌”，以打开 Apple 部署计划门户，并使用公司 Apple ID 登录  。 可使用此 Apple ID 续订 DEP 令牌。

5. 在 Apple [部署计划门户](https://deploy.apple.com)中，对“设备注册计划”选择“开始”   。 你的注册流程可能与 [Apple 商务管理](https://business.apple.com)中的以下步骤略有不同。

4. 在“管理服务器”  页上，选择“添加 MDM 服务器”  。

5. 对于“MDM 服务器名称”，请输入 TestMDMServer，然后选择“下一步”    。 服务器名称供参考，用于识别移动设备管理 (MDM) 服务器。 它不是 Microsoft Intune 服务器的名称或 URL。

6. “添加&lt;服务器名称&gt;”  对话框随即打开，提示“上传公钥”  。 选择“选择文件…”  以上传 .pem 文件，然后选择“下一步”  。

6. 转到“部署计划” > “设备注册计划” > “托管设备”    。
7. 在“选择设备依据”下，选择“序列号”   。 <!--ask Tiffany about this-->

8. 对于“选择操作”，选择“分配到服务器”，选择为 Microsoft Intune 指定的 &lt;服务器名称&gt;，然后选择“确定”    。 Apple 门户将指定的设备分配到 Intune 服务器以进行管理，然后显示“分配完成”  。

   在 Apple 门户中，转到“部署计划”  &gt;“设备注册计划”  &gt;“查看分配历史记录”  ，以查看设备及其 MDM 服务器分配的列表。

9. 在 Azure 门户的 Intune 中，提供了用于创建此令牌的 Apple ID，以供未来参考。

    ![指定用来创建注册计划令牌的 Apple ID 并浏览到注册计划令牌的屏幕截图。](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. 在“Apple 令牌”框中，浏览到证书 (.pem) 文件，选择“打开”，然后选择“创建”    。 

11. 如果要应用作用域标记来限制可以访问此令牌的管理员，请选择作用域。

## <a name="create-an-apple-enrollment-profile"></a>创建 Apple 注册配置文件
现在你已经安装了令牌，接着可以为公司拥有的 iOS 设备创建注册配置文件。 设备注册配置文件定义注册时应用于设备组的设置。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备注册”   > “Apple 注册”   > “注册程序令牌”  。

2. 选择刚刚安装的令牌，选择“配置文件” > “创建配置文件”   。

3. 在“创建配置文件”下，为“名称”输入 TestDEPProfile，为“说明”输入适用于 iOS 设备的测试 DEP      。 用户看不到这些详细信息。

4. 选择“平台”下的“iOS”   。

5. 确定是否希望自己的设备注册“用户关联”  。 用户关联专为特定用户将使用的设备而设计。 如果用户希望使用公司门户来获取安装应用等服务，请选择“注册用户关联”  。 如果用户不需要公司门户，或者你要为多位用户预配设备，请选择“不注册用户关联”  。

6. 如果选择注册用户关联，请确定是否要使用公司门户或 Apple 设置助理进行身份验证。 如果要使用多重身份验证、允许用户在首次登录时更改密码，或者在注册过程中提示用户重置过期密码，请在“使用公司门户而不是 Apple 设置助理进行身份验证”下选择“是”   。 如果习惯通过 Apple 设置助理使用 Apple 提供的基本 HTTP 身份验证，请选择“否”  。 如果选择“是”  并且希望公司门户应用程序在最终用户的设备上自动更新，请通过 Apple 的批量采购计划 (VPP) 将公司门户作为必需的应用单独部署给这些用户。

7. 如果选择了注册用户关联并使用公司门户进行身份验证，请确定是否要使用 Apple Volume Purchase Program (VPP) 安装公司门户。 如果使用 VPP 令牌安装公司门户，用户在注册期间无需输入 Apple ID 和密码即可从应用商店下载公司门户。 在“使用 VPP 安装公司门户”下选择“使用令牌:”来选择具有可用的公司门户免费许可证的 VPP 令牌   。 如果不想使用 VPP 部署公司门户，请在“使用 VPP 安装公司门户”下选择“不使用 VPP”   。 

8. 如果选择了注册用户关联、使用公司门户进行身份验证以及使用 VPP 安装公司门户，请确定是否要在身份验证前以单应用模式运行公司门户。 此设置使你能够确保用户在完成公司注册之前无法访问其他应用。 如果要在注册完成之前将用户限制在此流，请在“在身份验证前以单应用模式运行公司门户”下选择“是”   。 

9. 选择“设备管理设置”，然后在“已监督”下选择“是”    。 受监督的设备可以提供适用于公司 iOS 设备的大多数管理选项。

10. 在“锁定的注册”下选择“是”以确保用户无法删除公司设备的管理   。 

11. 选择“与计算机同步”下的一个选项以确定 iOS 设备是否能够与计算机同步  。

12. 默认情况下，Apple 将使用设备类型（即 iPad）来命名设备。 如果想提供其他名称模板，请在“应用设备名称模板”下选择“是”   。 输入要应用于设备的名称，字符串 {{SERIAL}} 和 {{DEVICETYPE}} 将替换为每台设备的序列号和设备类型   。 否则，请在“应用设备名称模板”下选择“否”   。

13. 选择“确定”  。

14. 选择“设置助理自定义”，并为“部门名称”输入“教程部门”    。 此字符串是用户在设备激活期间点击“关于配置”时看到的内容  。

15. 在“部门电话”下，输入电话号码  。 在激活期间中，用户点击“需要帮助”按钮时，会显示该号码  。

16. 在设备激活期间，可以“显示”或“隐藏”各种屏幕   。 为了获得最无缝的注册体验，请将所有屏幕设置为“隐藏”  。

17. 选择“确定” > “创建”   。

## <a name="sync-managed-devices-to-intune"></a>将托管设备同步到 Intune

使用 ABM、ASM 或 DEP 门户设置注册计划令牌并将设备分配给 MDM 服务器后，可以等待这些设备同步到 Intune 服务，也可以手动推送同步。如果不执行手动同步，设备可能需要长达 24 小时才能显示在 Azure 门户中。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备注册”   > “Apple 注册”   > “注册程序令牌”  > 在列表中选择令牌 >“设备”   > “同步”  。

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>将注册配置文件分配到 iOS 设备

必须先向设备分配注册计划配置文件才能注册他们。 这些设备是从 Apple 同步到 Intune 的，并且必须已分配给 ABM、ASM 或 DEP 门户中相应的 MDM 服务器令牌。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备注册”   > “Apple 注册”   > “注册程序令牌”  > 在列表中选择令牌。
2. 选择“设备”> 在列表中选择设备 >“分配配置文件”。  
3. 在“分配配置文件”下，为设备选择配置文件，然后选择“分配”   。

## <a name="distribute-devices-to-users"></a>将设备分配给用户

已在 Apple 和 Intune 之间设置了管理和同步，并且分配了注册 DEP 设备所需的配置文件。 现在可以将设备分配给用户。 具有用户关联的设备需要每个用户都分配有 Intune 许可证。

## <a name="next-steps"></a>后续步骤

可以找到有关其他可用于注册 iOS 设备的选项的更多信息。

> [!div class="nextstepaction"]
> [深入了解 iOS DEP 注册文章](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
