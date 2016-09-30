---
title: "为订阅设置 Lookout MTP | Microsoft Intune"
description: "本主题详述如何配置 Lookout MTP。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2196ff03975df1f8969e1522f7af459343694d
ms.openlocfilehash: 530a34c7c75a4fa73cbb62873e2d28883b91b57e


---

# 针对 Lookout 移动威胁保护设置订阅
为使订阅可使用 Lookout MTP 服务，Lookout 支持 (enterprisesupport@lookout.com) 需要有关 Azure Active Directory (Azure AD) 订阅的下列信息。 

* **Azure AD 租户 ID**
* 具有 Lookout MTP 控制台**完全**访问权限的 **Azure AD 组对象 ID**
* 具有 Lookout MTP 控制台**受限**访问权限的 **Azure AD 组对象 ID**（可选）

以下部分介绍了如何收集提供给 Lookout 支持团队的信息。  

## 获取 Azure AD 信息
### Azure AD 租户 ID
登录到 [Azure AD 管理门户](https://manage.windowsazure.com)，然后选择订阅。 

![Azure AD 页面的屏幕截图，其中显示了租户名称](../media/mtp/aad_tenant_name.png) 选择订阅名称时，生成的 URL 包括订阅 ID。  如果查找订阅 ID 时遇到任何问题，请参阅 [Microsoft 支持文章](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US)获取有关查找订阅 ID 的提示。   
### 获取 Azure AD 组 ID
Lookout MTP 控制台支持 2 个级别的访问：  
* **完全访问：**Azure AD 管理员可创建具有完全访问权限的用户组，还可创建具有受限访问权限的用户组。  仅这两个组的用户可登录到 **Lookout MTP 控制台**。
* **受限访问：**该组中的用户无法访问 Lookout MTP 控制台的某些配置和注册相关模块，可对 Lookout MTP 控制台的“安全策略”模块进行只读访问。  

有关各种权限的详细信息，请参阅 Lookout 网站上的[这篇文章](https://personal.support.lookout.com/hc/en-us/articles/114094105653)。

“组对象 ID”位于“Azure AD 管理控制台”的组“属性”页。

![突出显示 GroupID 字段的“属性”页截图](../media/mtp/aad_group_object_id.png)

收集此信息后，请联系 Lookout 支持（电子邮件：enterprisesupport@lookout.com）。

Lookout 支持将使用你收集的信息，与主要联系人合作提供订阅并创建 Lookout MTP 企业帐户。


## 为订阅配置 Lookout MTP
### 步骤 1：设置 MTP
Lookout 支持创建 Lookout MTP 企业帐户后，可登录到 Lookout MTP 控制台。   Lookout 将向公司的主要联系人发送电子邮件，附带登录 URL 的链接：https://aad.lookout.com/les?action=consent

首次登录到 Lookout MTP 控制台时，必须使用具有 Azure AD 全局管理员角色的用户帐户，因为 Lookout MTP 需要借助此帐户注册 Azure AD 租户。   后续登录不要求用户具有此级别的 Azure AD 权限。  首次登录时将显示同意页面。 选择“接受”完成注册。

![首次登录 Lookout MTP 控制台时登录页面的屏幕截图](../media/mtp/lookout_mtp_initial_login.png) 接受并同意后，会重定向到 Lookout MTP 控制台。 最初注册后，可使用此 URL 进行后续登录：https://aad.lookout.com

若遇到登录问题，请参阅[疑难解答文章](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)。

下列步骤概述了为完成 Lookout MTP 设置而必须在 [Lookout MTP 控制台](https://aad.lookout.com)内完成的任务。

### 步骤 2：配置 Intune 连接器

1.  在 Lookout MTP 控制台中，转到“系统”模块，选择“连接器”选项卡，再选择“Intune”。

  ![Lookout MTP 控制台的屏幕截图，其中打开了“连接器”选项卡并突出显示了“Intune”选项](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  在连接设置选项中，以分钟为单位配置检测信号频率。  Intune 连接器现已准备就绪。  

  ![连接设置选项卡的屏幕截图，其中显示了已配置信号检测频率](../media/mtp/lookout-mtp-connection-settings.png)

### 步骤 3：配置注册组
在“注册管理”选项中，定义应将其设备注册到 Lookout 的一组用户。 最佳做法是先用一小组用户进行测试，熟悉集成的工作原理。  对测试结果感到满意后，即可将注册扩展到其他成员组。

要开始注册组，请先定义适合作为 Lookout MTP 中首组注册用户的 Azure AD 安全组。 在 Azure AD 中创建组后，在 Lookout MTP 控制台转到“注册管理”选项，然后添加 Azure AD 安全组“显示名称”进行注册。

用户处于注册组时，其所有设备都将进行注册并可在 Lookout MTP 中激活。这些设备由 Azure AD 标识并受其支持。  用户首次在其受支持的设备上打开 Lookout for Work 应用时，将在 Lookout MTP 中激活该设备。
![Intune 连接器注册页面的屏幕截图](../media/mtp/lookout-mtp-enrollment.png)

最佳做法是使用递增时间的默认值（5 分钟）检查新设备。

>[!IMPORTANT]
> 显示名称区分大小写。  使用 Azure 门户安全组中“属性”页面显示的“显示名称”。 请注意，在下图所示的安全组“属性”页中，“显示名称”采用混合大小写。  而标题则全部小写，不应将其输入 Lookout MTP 控制台。
>![Azure 门户 Azure Active Directory 服务属性页的屏幕截图](../media/mtp/aad-group-display-name.png)

当前版本具有以下限制：  
* 无组显示名称验证。  对于 Azure AD 安全组，请确保使用 Azure 门户中所示的“显示名称”字段中的值。
* 目前不支持在组内创建组。  指定的 Azure AD 安全组只能包含用户，不能包含嵌套组。


### 步骤 4：配置状态同步
在“状态同步”选项中，指定要发送到 Intune 的数据类型。  目前，必须同时启用设备状态和威胁状态，Lookout Intune 集成才能正常工作。  默认情况下这些状态都已启用。
### 步骤 5：配置错误报告电子邮件收件人信息
在“错误管理”选项中，输入应接收错误报告的电子邮件地址。

![Intune 连接器错误管理页面屏幕截图](../media/mtp/lookout-mtp-connector-error-notifications.png)

### 步骤 6：配置电子邮件通知
如果希望接收有关威胁的电子邮件警报，请使用要接收通知的用户帐户登录 [Lookout MTP 控制台](https://aad.lookout.com)。 在“系统”模块的“首选项”选项卡上选择所需通知，并将其设置为“开启”。 保存你的更改。

![显示用户帐户的“首选项”页面屏幕截图](../media/mtp/lookout-mtp-email-notifications.png) 如果不再希望收到通知，请将通知设置为“关闭”并保存修改。
### 步骤 7：配置威胁分类
Lookout MTP 将移动威胁分为多种类型。 [Lookout MTP 威胁分类](http://personal.support.lookout.com/hc/en-us/articles/114094130693)关联了默认威胁等级。 可随时对其进行修改，以满足公司需求。

![显示威胁和分类的“策略”页面屏幕截图](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> 此处指定的风险等级是 MTP 的重要方面，因为 Intune 集成将在运行时根据这些风险等级计算设备合规性。 换言之，Intune 管理员在策略中设置规则，使其在设备中存在最低等级为高级、中级或低级的活跃威胁时将设备确定为不合规。 MTP 中的威胁分类策略直接引导 Intune 中的设备合规性计算。

## 监视注册
此步骤完成后，Lookout MTP 将开始轮询 Azure AD，查找与指定注册组相对应的设备。  可在“设备”模块查看有关已注册设备的信息。  设备的初始状态显示为“待定”。  在设备上安装、打开和激活 Lookout for Work 应用后，设备状态将发生改变。  有关如何将 Lookout for Work 应用推送到设备的详细信息，请参阅[配置并部署 Lookout for Work 应用](configure-and-deploy-lookout-for-work-apps.md)主题。
## 后续步骤
[启用 Lookout MTP 连接 Intune](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Sep16_HO3-->


