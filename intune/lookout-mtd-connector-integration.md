---
title: 设置 Lookout 与 Microsoft Intune 的集成 | Microsoft Intune
description: 了解如何将 Intune 与 Lookout Mobile Threat Defense 相集成以控制移动设备对公司资源的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69e9cfa1ffc294ca26f94bab94d8b758611a4ac0
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237565"
---
# <a name="set-up-your-lookout-mobile-threat-defense-integration-with-intune"></a>使用 Intune 设置 Lookout 移动威胁防御集成

以下是设置 Lookout 移动威胁防御订阅所需的步骤：

| #        |步骤  |
| ------------- |:-------------|
| 1 | [收集 Azure AD 信息](#collect-azure-ad-information) |
| 2 | [配置订阅](#configure-your-subscription) |
| 3 | [配置注册组](#configure-enrollment-groups) |
| 4 | [配置状态同步](#configure-state-sync) |
| 5 | [配置错误报告电子邮件收件人信息](#configure-error-report-email-recipient-information) |
| 6 | [配置注册设置](#configure-enrollment-settings) |
| 7 | [配置电子邮件通知](#configure-email-notifications) |
| 8 | [配置威胁分类](#configure-threat-classification) |
| 9 | [监视注册](#watching-enrollment) |

> [!IMPORTANT]
> 未与 Azure AD 租户关联的现有 Lookout Mobile Endpoint Security 租户不能用于 Azure AD 与 Intune 的集成。 请联系 Lookout 支持部门以创建新的 Lookout Mobile Endpoint Security 租户。 请使用新的租户载入 Azure AD 用户。

## <a name="collect-azure-ad-information"></a>收集 Azure AD 信息
Lookout 移动终结点安全租户会与 Azure AD 订阅关联，以将 Lookout 和 Intune 集成。 若要启用 Lookout 移动威胁防御服务订阅，Lookout 支持人员 (enterprisesupport@lookout.com) 需要以下信息：

* **Azure AD 租户 ID**
* Lookout 控制台**完全**访问权限的**Azure AD 组对象 ID**
* 具有 Lookout 控制台**受限**访问权限的 **Azure AD 组对象 ID**（可选）

以下步骤介绍了如何收集提供给 Lookout 支持团队的信息。

1. 登录到 [Azure 门户](https://portal.azure.com)并选择自己的订阅。 

2. 选择订阅名称时，所生成的 URL 包括订阅 ID。  如果查找订阅 ID 时遇到任何问题，请参阅 [Microsoft 支持文章](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b)获取有关查找订阅 ID 的提示。

3. 查找 Azure AD 组 ID。 Lookout 控制台支持 2 个级别的访问：  
   * **完全访问：** Azure AD 管理员可创建具有完全访问权限的用户组，也可选择创建具有受限访问权限的用户组。  仅这两个组的用户可登录到 **Lookout 控制台**。
   * **受限访问：** 该组中的用户无法访问 Lookout 控制台的某些配置和注册相关模块，可对 Lookout 控制台的“安全策略”模块进行只读访问。  

     > [!TIP] 
     > 有关各种权限的详细信息，请参阅 Lookout 网站上的[这篇文章](https://personal.support.lookout.com/hc/articles/114094105653)。

     > [!NOTE] 
     > “组对象 ID”位于“Azure AD 管理门户”中组的“属性”页。

4. 收集此信息后，请联系 Lookout 支持人员（电子邮件：enterprisesupport@lookout.com）。 Lookout 支持将使用你收集的信息，与主要联系人合作提供订阅并创建 Lookout 企业帐户。

## <a name="configure-your-subscription"></a>配置订阅

1. Lookout 支持人员创建 Lookout 企业帐户后，将向公司的主要联系人发送电子邮件，附带登录 URL 的链接：<https://aad.lookout.com/les?action=consent>。

2. 首次登录到 Lookout 控制台时必须使用具有 Azure AD 全局管理员角色的用户帐户，以便注册 Azure AD 租户。 后续登录无需这一级别的 Azure AD 特权。 此时会显示同意页。 选择“接受”完成注册。 接受并同意后，系统将重定向到 Lookout 控制台。

   ![第一次登录到 Lookout 控制台时的登录页面屏幕截图](./media/lookout_mtp_initial_login.png)

3. 在[“Lookout 控制台”](https://aad.lookout.com)中，从“系统”模块选择“连接器”选项卡，然后选择“Intune”。

   ![Lookout 控制台的示意图，其中“连接器”选项卡上有“Intune”选项](./media/lookout_mtp_setup-intune-connector.png)

4. 转到“连接器” > “连接设置”，以分钟为单位指定“检测信号频率”。

   ![连接设置选项卡的示意图，其中已配置信号检测频率](./media/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>配置注册组
1. 最佳做法是在 [Azure AD 管理门户](https://manage.windowsazure.com)中创建一个 Azure AD 安全组，并在其中包含少量用于测试 Lookout 集成的用户。

    > [!NOTE] 
    > Azure AD 注册组中标识并支持的所有受 Lookout 支持并注册了 Intune 的用户设备，都注册了 Lookout MTD 控制台并可在其中激活。

2. 在 [Lookout 控制台](https://aad.lookout.com)的“系统”模块中，选择“连接器”选项卡，然后选择“注册管理”，以定义一组其设备应注册 Lookout 的用户。 添加用于注册的 Azure AD 安全组“显示名称”。

    ![Intune 连接器注册页面的屏幕截图](./media/lookout-mtp-enrollment.png)

    >[!IMPORTANT]
    > 正如 Azure 门户安全组的“属性”中所示，“显示名称”区分大小写。 如下图所示，安全组的“显示名称”为大小写混用，而标题全为小写。 在 Lookout 控制台中，请匹配安全组的“显示名称”的大小写。
    >![Azure 门户、Azure Active Directory 服务属性页的示意图](./media/aad-group-display-name.png)

    >[!NOTE] 
    >最佳做法是使用递增时间的默认值（5 分钟）检查新设备。 当前限制，Lookout 无法验证组显示名称：请确保 Azure 门户中的“显示名称”字段与 Azure AD 安全组完全匹配。 **不支持创建嵌套组：** Lookout 中使用的 Azure AD 安全组仅能包含用户。 不能包含其他组。

3.  添加组后，用户下次在其受支持的设备上打开 Lookout for Work 应用时，将在 Lookout 中激活该设备。

4.  如果结果合意，则将注册扩展到其他用户组。

## <a name="configure-state-sync"></a>配置状态同步
在“状态同步”选项中，指定要发送到 Intune 的数据类型。  需同时启用设备状态和威胁状态，Lookout Intune 集成才能正常工作。 默认情况下，这些设置处于启用状态。

## <a name="configure-error-report-email-recipient-information"></a>配置错误报告电子邮件收件人信息
在“错误管理”选项中，输入应接收错误报告的电子邮件地址。

![Intune 连接器错误管理页面屏幕截图](./media/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>配置注册设置
在“系统”模块中的“连接器”页上，指定在将设备视为已断开连接之前的天数。  断开连接的设备会被视为不符合，并根据 Intune 条件访问策略，不得访问公司应用程序。 可以指定介于 1 到 90 天之间的值。

![系统模块上的 Lookout 注册设置](./media/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>配置电子邮件通知
如果希望接收有关威胁的电子邮件警报，请使用要接收通知的用户帐户登录 [Lookout 控制台](https://aad.lookout.com)。 在“系统”模块“首选项”选项卡上选择通知的威胁级别，并将其设置为“开启”。 保存你的更改。

![显示用户帐户的“首选项”页面屏幕截图](./media/lookout-mtp-email-notifications.png) 如果希望不再收到通知，请将通知设置为“关闭”并保存修改。

### <a name="configure-threat-classification"></a>配置威胁分类
Lookout 移动威胁防御将移动威胁分为多种类型。 [Lookout 威胁分类](https://personal.support.lookout.com/hc/articles/114094130693)关联了默认威胁等级。 可随时对其进行修改，以满足公司需求。

![显示威胁和分类的“策略”页面屏幕截图](./media/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> 风险等级在移动威胁防御中十分重要，因为 Intune 集成将在运行时根据这些风险等级计算设备符合性。 Intune 管理员在策略中设置规则，在设备中存在最低等级为高级、中级或低级的活跃威胁时将设备标识为不符合。 Lookout 移动威胁防御中的威胁分类策略直接引导 Intune 中的设备符合性计算。

## <a name="watching-enrollment"></a>监视注册
此步骤完成后，Lookout 移动威胁防御将开始轮询 Azure AD，查找与指定注册组相对应的设备。  可在“设备”模块查看有关已注册设备的信息。  设备的初始状态显示为“待定”。  在设备上安装、打开和激活 Lookout for Work 应用后，设备状态将发生改变。  有关如何将 Lookout for Work 应用推送到设备的详细信息，请参阅[使用 Intune 添加 Lookout for Work 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)。

## <a name="next-steps"></a>后续步骤

[设置 Lookout 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
