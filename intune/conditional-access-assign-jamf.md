---
title: Jamf 设备的设备符合性策略
titleSuffix: Microsoft Intune
description: 通过将 Microsoft Intune 符合性策略与 Azure Active Directory 条件访问相结合，可确保由 Jamf 管理的设备的安全。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc4fdaea99a0e8fb247ac6a70b853497927cdc04
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "67045212"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>在使用 Jamf Pro 管理的 Mac 上强制实现符合性

适用于：Azure 门户中的 Intune

可以使用 Azure Active Directory 和 Microsoft Intune 的条件访问策略，以确保最终用户符合组织的要求。 可以将这些策略应用到[使用 Jamf Pro 管理](conditional-access-integrate-jamf.md)的 Mac。 这需要能够同时访问 Intune 和 Jamf Pro 控制台。

## <a name="set-up-device-compliance-policies-in-intune"></a>在 Intune 中设置设备符合性策略

1. 打开 Microsoft Azure，然后导航到“Intune”   > “设备符合性”   > “策略”  。 可以为 macOS 创建策略，其中包括针对不符合要求的用户和组选择一系列操作（例如发送警告电子邮件）。
2. 搜索所需的组，然后向其应用策略。

> [!Note]
> Intune 要求全磁盘加密，以符合要求。

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>在 Jamf Pro 中部署适用于 macOS 的公司门户应用

应按照以下过程操作，在 Jamf Pro 中将适用于 macOS 的公司门户应用作为后台安装进行部署：

1. 在 macOS 设备上，下载[适用于 macOS 的公司门户应用](https://go.microsoft.com/fwlink/?linkid=862280)的当前版本。 请勿安装该版本；需要将该应用的副本上传到 Jamf Pro。
2. 打开 Jamf Pro，然后导航到“计算机管理”   > “程序包”  。
3. 在适用于 macOS 的公司门户应用中创建新的程序包，然后单击“保存”  。
4. 打开“计算机”   > “策略”  ，然后选择“新建”  。
5. 使用常规有效负载为策略配置设置  。 这些设置应为：
   - 触发器：选择“注册完成”和“定期签入”  
   - 执行频率：选择“每台计算机一次” 
6. 选择“程序包”  负载，然后单击“配置”  。
7. 单击“添加”  以选择公司门户应用中的程序包。
8. 选择“操作”  弹出菜单中的“安装”  。
9. 配置程序包的设置。
10. 单击“作用域”  选项卡以指定应在哪些计算机上安装公司门户应用。 单击 **“保存”** 。 下次，当计算机上出现所选的触发器并符合“常规”  负载中的条件时，策略将运行作用域内的设备。

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>在 Jamf Pro 中创建策略，让用户在 Azure Active Directory 中注册其设备

> [!NOTE]
> 在继续下一步骤前，需要为 macOS [部署公司门户](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)。  

最终用户需要在 Jamf 自助服务中启动公司门户应用，以使用 Azure AD 将设备注册为由 Jamf Pro 管理的设备。 这需要最终用户采取措施。 建议通过电子邮件、Jamf Pro 通知或任何其他方式[联系最终用户](end-user-educate.md)，通知他们单击 Jamf 自助服务中的按钮。

> [!WARNING]
> 必须从 Jamf 自助服务启动公司门户应用才能开始注册设备。 <br><br>手动启动公司门户应用（例如，从“应用程序”或“下载”文件夹）不会注册设备。 如果最终用户手动启动公司门户，他们会看到一条警告“AccountNotOnboarded”。

1. 在 Jamf Pro 中，导航到“计算机”   > “策略”  ，然后为设备注册创建新策略。
2. 配置“Microsoft Intune 集成”有效负载，其中包括触发器和执行频率  。
3. 单击“作用域”  选项卡，并将策略的作用域设置为所有目标设备。
4. 单击“自助服务”  选项卡以将策略应用到 Jamf 自助服务中。 将策略添加到“设备符合性”  类别中。 单击 **“保存”** 。

## <a name="removing-a-jamf-managed-device-from-intune"></a>从 Intune 删除 Jamf 托管设备

通过在“所有设备”视图中选择“删除”，可从 Intune 控制台中删除 Jamf 托管设备   。 通过选择多个设备并单击“删除”，可启用批量设备删除  。

获取有关如何[在 Jamf Pro 文档中删除 Jamf 托管设备](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)的信息。还可通过 [Jamf 支持](https://www.jamf.com/support/)提交支持票证，获取更多帮助。 

## <a name="next-steps"></a>后续步骤

- [Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Azure Active Directory 中的条件访问入门](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
