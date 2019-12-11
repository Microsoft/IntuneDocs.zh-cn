---
title: 设置 Lookout 与 Microsoft Intune 的集成
titleSuffix: Microsoft Intune
description: 了解如何将 Intune 与 Lookout 移动终结点安全相集成，以作为 Mobile Threat Defense 解决方案来控制移动设备对公司资源的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b4661b151493eb68cc6f71a5a77bd023ac27b826
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810221"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>设置 Lookout 移动终结点安全与 Intune 的集成
在满足[先决条件](lookout-mobile-threat-defense-connector.md#prerequisites)的环境中，可以将 Lookout 移动终结点安全与 Intune 相集成。 本文中的信息将指导你设置集成，并指导你在 Lookout 中配置关键设置以与 Intune 结合使用。  

> [!IMPORTANT]
> 未与 Azure AD 租户关联的现有 Lookout Mobile Endpoint Security 租户不能用于 Azure AD 与 Intune 的集成。 请联系 Lookout 支持部门以创建新的 Lookout Mobile Endpoint Security 租户。 请使用新的租户载入 Azure AD 用户。

## <a name="collect-azure-ad-information"></a>收集 Azure AD 信息  
将 Lookout 移动终结点安全租户与 Azure Active Directory (AD) 订阅关联，以将 Lookout 和 Intune 集成。

向 Lookout 支持部门 (enterprisesupport@lookout.com) 提供下列信息，以便可以将 Lookout 移动终结点安全订阅与 Intune 集成：  

- **Azure AD 租户目录 ID**  

- 具有完全 Lookout 移动终结点安全 (MES) 控制台访问权限的组的 Azure AD 组对象 ID   。  
  在 Azure AD 中创建此用户组，来包含具有完全访问权限进而能够登录到 Lookout 控制台的用户。   用户必须是此组或可选受限访问权限组的成员，才能够登录到 Lookout 控制台。  

- 具有 Lookout MES 控制台受限访问权限的组（可选组）的 Azure AD 组对象 ID。    
  在 Azure AD 中创建此可选用户组，来包含不应有权访问 Lookout 控制台的多个与配置和注册相关的模块的用户。 相反，这些用户具有对 Lookout 控制台的“安全策略”模块的只读访问权限。  用户必须是此可选组或完全访问权限必选组的成员，才能够登录到 Lookout 控制台。 

 > [!TIP] 
 > 有关各种权限的详细信息，请参阅 Lookout 网站上的[这篇文章](https://personal.support.lookout.com/hc/articles/114094105653)。

### <a name="collect-information-from-azure-ad"></a>从 Azure AD 收集信息 

1. 使用全局管理员帐户登录 [Azure 门户](https://portal.azure.com)。

2. 转到“Azure Active Directory” > “属性”，然后查找你的“目录 ID”。    。 使用“复制”按钮复制目录 ID，然后将其保存在文本文件中。 

   ![Azure AD 属性](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. 接下来，找到用于向 Azure AD 用户授予 Lookout 控制台访问权限的帐户的 Azure AD 组 ID。 一个组用于完全访问权限，用于受限访问权限的第二个组为可选组。   若要获得“对象 ID”，对各个组执行下面的操作：   
   1. 转到“Azure Active Directory” > “组”，打开“组 - 全部组”窗格。     

   2. 选择为完全访问权限创建的组，打开其“概述”窗格。    

   3. 使用“复制”按钮复制对象 ID，然后将其保存在文本文件中。   

   4. 若要使用该组，请重复用于受限访问权限组的过程。   

      ![Azure AD 组对象 ID](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   收集此信息后，请联系 Lookout 支持人员（电子邮件：enterprisesupport@lookout.com）。 Lookout 支持将使用你提供的信息，与主要联系人合作提供订阅并创建 Lookout 企业帐户。  

## <a name="configure-your-lookout-subscription"></a>配置 Lookout 订阅  

以下步骤将在 Lookout 企业管理控制台中完成，并且将为在 Intune 中注册的设备（通过设备符合性）和在 Intune 中未注册的设备（通过应用保护策略）启用与 Lookout 服务的连接  。

Lookout 支持人员创建 Lookout 企业帐户后，将向公司的主要联系人发送电子邮件，附带登录 URL 的链接： https://aad.lookout.com/les?action=consent 。 

### <a name="initial-sign-in"></a>首次登录  
首次登录到 Lookout MES 控制台时，将显示同意页面 (https://aad.lookout.com/les?action=consent) 。 Azure AD 全局管理员只需登录并“接受”。  后续登录不要求用户具有此级别的 Azure AD 权限。 

 此时会显示同意页。 选择“接受”  完成注册。 
   ![第一次登录到 Lookout 控制台时的登录页面屏幕截图](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

接受并同意后，系统将重定向到 Lookout 控制台。

完成首次登录并授予许可后，系统会将从 https://aad.lookout.com 登录的用户重定向到 MES 控制台。 若尚未授予许可，所有登录尝试均会引发“登录出错”错误。

### <a name="configure-the-intune-connector"></a>配置 Intune 连接器  
下面的过程假设你先前已在 Azure AD 中创建用户组，来用于测试 Lookout 部署。 最佳做法是从一个小型用户组开始，来让 Lookout 和 Intune 管理员熟悉产品集成。 熟悉之后，可以将注册扩展到其他用户组。

1. 登录到 [Lookout MES 控制台](https://aad.lookout.com)，转到“系统” > “连接器”，然后选择“添加连接器”。     选择“Intune”。 

   ![Lookout 控制台的示意图，其中“连接器”选项卡上有“Intune”选项](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. 从“Microsoft Intune”窗格选择“连接设置”，以分钟为单位指定“检测信号频率”。    

   ![连接设置选项卡的示意图，其中已配置信号检测频率](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. 选择“注册管理”，为“使用以下 Azure AD 安全组标识应在 Lookout for Work 中注册的设备”指定要与 Lookout 结合使用的 Azure AD 组的组名称，然后选择“保存更改”。    

    ![Intune 连接器注册页面的屏幕截图](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **关于你所使用的组**：
   - 最佳做法是从一个包含少量用户的 Azure AD 安全组开始，来用于测试 Lookout 集成。
   - 正如 Azure 门户安全组的“属性”中所示，“组名称”区分大小写   。  
   - 为“注册管理”指定的组定义设备要注册到 Lookout 的一组用户。  用户处于注册组时，他们在 Azure AD 中的设备都将进行注册并可在 Lookout MES 中激活。 用户首次从支持的设备打开 Lookout for Work 应用程序时，将提示他们将其激活。 

4. 选择“状态同步”，确保“设备状态”和“威胁状态”均已设置为“启用”。      需同时启用这两个状态，Lookout Intune 集成才能正常工作。  

5. 选择“错误管理”，指定应收到错误的电子邮件地址，然后选择“保存更改”。  
 
   ![Intune 连接器错误管理页面屏幕截图](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. 选择“创建连接器”，完成连接器配置。  如果稍后结果合意，可以将注册扩展到其他用户组。

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>将 Intune 配置为使用 Lookout 作为 Mobile Threat Defense 提供程序
配置 Lookout MES 后，必须[在 Intune 中建立 Lookout 连接](https://docs.microsoft.com/en-us/intune/protect/mtd-connector-enable)。  

## <a name="additional-settings-in-the-lookout-mes-console"></a>Lookout MES 控制台中的其他设置
下面是可在 Lookout MES 控制台中配置的其他设置。  

### <a name="configure-enrollment-settings"></a>配置注册设置
在 Lookout MES 控制台中，选择“系统” > “管理注册” > “注册设置”。     

- 为“断开状态”指定在多少天之后将未连接的设备标记为断开连接。   

  断开连接的设备会被视为不符合，并根据 Intune 条件访问策略，不得访问公司应用程序。 可以指定介于 1 到 90 天之间的值。

  ![系统模块上的 Lookout 注册设置](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>配置电子邮件通知
若要接收有关威胁的电子邮件警报，请使用要接收通知的用户帐户登录 [Lookout MES 控制台](https://aad.lookout.com)。  

- 转到“首选项”，将想要接收的通知设置为“打开”，然后“保存”更改。     

- 如果希望不再收到通知，请将通知设置为“关闭”并保存修改。 

  ![显示用户帐户的“首选项”页面屏幕截图](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)

## <a name="configure-threat-classifications"></a>配置威胁分类  
Lookout 移动终结点安全将移动威胁分为多种类型。 Lookout 威胁分类关联了默认风险等级。 可随时更改这些风险等级以满足公司需求。

有关威胁等级分类以及如何管理与其关联的风险等级的信息，请参阅 [Lookout 威胁参考](https://enterprise.support.lookout.com/hc/articles/360011812974)。

>[!IMPORTANT]
> 风险等级在移动终结点安全中十分重要，因为 Intune 集成将在运行时根据这些风险等级计算设备符合性。  
> 
> Intune 管理员在策略中设置规则，在设备中存在最低等级为高级、中级或低级的活跃威胁时将设备标识为不符合    。 Lookout 移动终结点安全中的威胁分类策略直接引导 Intune 中的设备符合性计算。  

## <a name="monitor-enrollment"></a>监视注册
此步骤完成后，Lookout 移动终结点安全将开始轮询 Azure AD，查找与指定注册组相对应的设备。  可以转到 Lookout MES 控制台中的“设备”，查看已注册设备的相关信息。   
- 设备的初始状态为“待定”。   
- 在设备上安装、打开和激活 Lookout for Work 应用后，设备状态将更新  。

有关如何将 Lookout for Work 应用部署到设备的详细信息，请参阅[使用 Intune 添加 Lookout for Work 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)。 

## <a name="next-steps"></a>后续步骤

- [为已注册的设备设置 Lookout 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [为未注册的设备设置 Lookout 应用](~/protect/mtd-add-apps-unenrolled-devices.md)
