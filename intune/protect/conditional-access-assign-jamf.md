---
title: Jamf 设备的设备符合性策略
titleSuffix: Microsoft Intune
description: 通过将 Microsoft Intune 符合性策略与 Azure Active Directory 条件访问相结合，可确保由 Jamf 管理的设备的安全。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b09b30fd32caace9ed3259350c01548d5e5fae15
ms.sourcegitcommit: 93265c2491058afde7168134075bed77031b9311
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/18/2019
ms.locfileid: "74161594"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>在使用 Jamf Pro 管理的 Mac 上强制实现符合性

[将 Jamf Pro 与 Intune 集成](conditional-access-integrate-jamf.md)时，可以使用条件访问策略对 Mac 设备强制实现与组织要求的符合性。  本文将帮助你完成以下任务：  

- 创建条件访问策略。
- 配置 Jamf Pro 以将 Intune 公司门户应用部署到使用 Jamf 管理的设备。
- 配置设备，以在设备用户登录到 Jamf 自助服务应用内启动的公司门户应用时向 Azure AD 注册。 设备注册在 Azure AD 中建立标识，以允许通过条件访问策略来评估设备，以便访问公司资源。  
 
本文中的过程需要访问 Intune 和 Jamf Pro 控制台。

## <a name="set-up-device-compliance-policies-in-intune"></a>在 Intune 中设置设备符合性策略

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备” > “符合性策略”   。 如果使用以前创建的策略，请在控制台中选择该策略，然后转到此过程的下一步。 若要创建新策略，请选择“创建策略”，然后使用 macOS 的平台指定策略的详细信息    。 配置“设置”和“对不合规项的操作”以满足组织要求，然后选择“创建”以保存策略    。

3. 在策略的“概述”窗格上，选择“分配”   。 使用可用选项配置哪些 Azure Active Directory (Azure AD) 用户和安全组接收此策略。 Jamf 与 Intune 的集成不支持针对设备组的符合性策略。

4. 选择“保存”  后，策略将部署到用户。  

部署的策略针对已分配用户使用的设备。 将对这些设备进行符合性评估。 对于 Azure AD 中的设置“需要标记为兼容的设备”  ，兼容设备将标记为兼容。  

> [!NOTE]
> Intune 要求全磁盘加密，以符合要求。

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>在 Jamf Pro 中部署适用于 macOS 的公司门户应用

在 Jamf Pro 中创建策略以部署 Intune 公司门户。 此策略部署公司门户应用，使其在 Jamf 自助服务中可用。 在 Jamf Pro 中为用户创建策略之前创建此策略，以使用户能够向 Azure AD 注册设备。  

若要完成以下过程，需要访问 macOS 设备和 Jamf Pro 门户。 

### <a name="to-deploy-the-company-portal-app"></a>部署公司门户应用  

1. 在 macOS 设备上，下载[适用于 macOS 的公司门户应用](https://go.microsoft.com/fwlink/?linkid=862280)的当前版本，但不安装。 只需应用的副本即可将应用上传到 Jamf Pro。  

2. 打开 Jamf Pro，然后转到“计算机管理”   > “程序包”  。

3. 在适用于 macOS 的公司门户应用中创建新的程序包，然后选择“保存”  。

4. 打开“计算机”   > “策略”  ，然后选择“新建”  。

5. 使用常规有效负载为策略配置设置  。 这些设置应为：
   - 触发器：选择“注册完成”和“定期签入”  
   - 执行频率：选择“每台计算机一次” 

6. 选择“程序包”  负载，然后单击“配置”  。

7. 单击“添加”  以选择公司门户应用中的程序包。

8. 选择“操作”  弹出菜单中的“安装”  。
9. 配置程序包的设置。

10. 选择“作用域”  选项卡以指定应在哪些计算机上安装公司门户应用。 选择“保存”  。 下次，当计算机上出现所选的触发器并符合“常规”  负载中的条件时，策略将运行作用域内的设备。

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>在 Jamf Pro 中创建策略，让用户在 Azure Active Directory 中注册其设备  

通过 Jamf Pro 自助服务为 macOS [部署公司门户](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)后，可以创建向 Azure AD 注册用户设备的 Jamf Pro 策略。 

设备注册要求设备用户从 Jamf 自助服务中手动选择 Intune 公司门户应用。 建议你通过电子邮件、Jamf Pro 通知或组织用来指导他们完成此操作的任何其他方法[联系最终用户](../fundamentals/end-user-educate.md)以注册其设备。 

> [!WARNING]
> 手动启动公司门户应用（例如，从“应用程序”或“下载”文件夹）不会注册设备。 如果设备用户手动启动公司门户，他们会看到一条警告“AccountNotOnboarded”  。

### <a name="to-create-the-registration-policy"></a>创建注册策略  

1. 在 Jamf Pro 中，转到“计算机”   > “策略”  ，然后为设备注册创建新策略。

2. 配置“Microsoft Intune 集成”有效负载，其中包括触发器和执行频率  。

3. 选择“作用域”  选项卡，然后将策略的作用域设置为所有目标设备。

4. 选择“自助服务”  选项卡以将策略应用到 Jamf 自助服务中。 将策略添加到“设备符合性”  类别中。 单击 **“保存”** 。

## <a name="validate-intune-and-jamf-integration"></a>验证 Intune 和 Jamf 集成  

使用 Jamf Pro 控制台确认 Jamf Pro 与 Microsoft Intune 之间的通信是否成功。 

- 在 Jamf Pro 中，转到“设置”   > “全局管理”   > “Microsoft Intune 集成”  ，然后选择“测试”  。

    控制台将显示一条消息，指示连接成功或失败。  

如果从 Jamf Pro 控制台进行的连接测试失败，请查看 Jamf 配置。 


## <a name="removing-a-jamf-managed-device-from-intune"></a>从 Intune 删除 Jamf 托管设备

若要删除 Jamf 管理的设备，请打开 Microsoft 终结点管理器管理中心，选择“设备” > “所有设备”，选择相应设备，然后选择“删除”    。  通过选择多个设备并单击“删除”，可启用批量设备删除  。

获取有关如何[在 Jamf Pro 文档中删除 Jamf 托管设备](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)的信息。还可通过 [Jamf 支持](https://www.jamf.com/support/)提交支持票证，获取更多帮助。 

## <a name="next-steps"></a>后续步骤

- [Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Azure Active Directory 中的条件访问入门](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
