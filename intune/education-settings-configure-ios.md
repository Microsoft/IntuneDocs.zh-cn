---
title: "iOS Classroom 应用的 Intune设置 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解可用于控制 iOS 设备上 Classroom 应用设置的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6f24636687291ff55686277c3f24b2774cfb32f4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---


# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>如何配置 iOS Classroom 应用的 Intune 设置

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="introduction"></a>简介
[Classroom](https://itunes.apple.com/app/id1085319084) 是一款可帮助教师在教室中指导学习及控制学生设备的应用。 例如，教师可以使用此应用执行以下操作：

- 打开学生设备上的应用
- 锁定和解锁 iPad 屏幕
- 查看学生 iPad 的屏幕
- 将学生 iPad 导航到某个书签，或书本的某个章节
- 在 Apple TV 上显示某个学生 iPad 中的屏幕

使用 Intune iOS **Education** 设备配置文件和本主题中的信息可帮助你设置 Classroom 应用及要使用此应用的设备。

## <a name="before-you-start"></a>开始之前

开始配置这些设置前请考虑以下内容：

- 教师和学生 iPad 必须均已在 Intune 中注册
- 确保已在教师设备上安装 [Apple Classroom](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) 应用。 你可以手动执行此操作，也可以使用 [Intune 应用管理](app-management.md)。
- 必须配置证书以对教师和学生设备之间的连接进行身份验证（请参阅步骤 2）
- 教师和学生 iPad 必须处于同一 Wi-Fi 网络覆盖区域内，并且必须均已启用蓝牙
- Classroom 应用在运行 iOS 9.3 或更高版本的受监督 iPad 上运行
- 在此版本中，Intune 支持管理每位学生都拥有自己专用 iPad 的 1:1 情形


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>步骤 1 - 将学校数据导入 Azure Active Directory

使用 Microsoft 的学校数据同步 (SDS) 将现有学生信息系统 (SIS) 中的学校记录导入 Azure Active Directory (Azure AD)。
SDS 将同步 SIS 中的信息并将其存储在 Azure AD 中。 Azure AD 是帮助你组织用户和设备的 Microsoft 管理系统。 使用此数据有助于管理学生和班级。 [了解有关如何部署 SDS 的详细信息](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)。

### <a name="how-to-import-data-using-sds"></a>如何使用 SDS 导入数据？

可以使用以下任一方式将信息导入 SDS：

- [CSV 文件](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) - 手动导出并编译逗号分隔值 (.csv) 文件
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) - 一个 SIS 提供程序，可以简化与 Azure AD 的同步操作
- [Clever API](https://support.office.com/article/Follow-these-steps-f3d92fde-3ad0-48f3-80a1-1ad0ac4a3fae) - 一个身份管理解决方案，可直接与 Azure AD 同步
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) - 一种 CSV 格式，可以导出和转换以用于与 Azure AD 同步

### <a name="find-out-more"></a>查看详细信息

- [详细了解将本地学校数据同步到 Azure AD 的完整体验](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [详细了解 Microsoft 学校数据同步](https://sds.microsoft.com/)
- [详细了解 Azure Active Directory 中的授权](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>步骤 2 - 在 Intune 中创建和分配 iOS 教育配置文件

### <a name="configure-general-settings"></a>配置常规设置

1. 登录到 Azure 门户中。
2. 依次选择“更多服务” > “其他” > “Intune”。
3.    在“Intune”边栏选项卡上，选择“配置设备”。
4.    在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
5.    在配置文件边栏选项卡上，选择“创建配置文件”。
6.    在“创建配置文件”边栏选项卡上，输入 iOS 教育配置文件的“名称”和“说明”。
7.    在“平台”下拉列表中，选择“iOS”。
8.    在“配置文件类型”类型下拉列表中，选择“教育”。
9.    选择“设置” > “配置”。


接下来，需要使用证书在教师和学生 iPad 之间建立信任关系。 证书用于在无提示情况下对设备间的连接进行无缝式身份验证，而无需输入用户名和密码。

>[!IMPORTANT]
>所使用的教师和学生证书必须由不同的证书颁发机构 (CA) 颁发。 必须创建两个新的连接到你的现有证书基础结构的从属 CA；一个用于教师，一个用于学生。

iOS 教育配置文件仅支持 PFX 证书，不支持 SCEP 证书。

除用户身份验证以外，所创建的证书还必须支持服务器身份验证。

### <a name="configure-teacher-certificates"></a>配置教师证书

在“教育”边栏选项卡上，选择“教师证书”。

#### <a name="configure-teacher-root-certificate"></a>配置教师根证书

在“教师根证书”下，选择浏览按钮以选择扩展名为 .cer（DER 或 Base64 编码）或 .P7B（不一定包含完整链路）的教师根证书。

#### <a name="configure-teacher-pkcs12-certificate"></a>配置教师 PKCS#12 证书

在“教师 PKCS#12 证书”下，配置下列值：

- **使用者名称格式** - 对于教师证书，Intune 将自动在证书公用名称上添加前缀“主持人”，对于学生证书则添加“成员”。
- **证书颁发机构** - 在 Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。 
- **证书颁发机构名称** - 输入你的证书颁发机构的名称。
- **证书模板名称** - 输入已添加到发证 CA 的证书模板的名称。 
- **续订阈值(%)** - 指定设备请求证书续订之前剩余的证书有效期限的百分比。
- **证书有效期** - 指定距离证书过期的剩余时间量。
你可以指定比指定证书模板中的有效期小的值，但不能指定较大的值。 例如，证书模板中的证书有效期为 2 年，则你可以指定值 1 年，但不能指定值 5 年。 该值还必须小于发证 CA 证书的剩余有效期。

完成证书配置后，选择“确定”。

### <a name="configure-student-certificates"></a>配置学生证书

1.    在“教育”边栏选项卡上，选择“学生证书”。
2.    在“学生证书”边栏选项卡的“学生设备证书”类型列表中，选择“1:1”。

#### <a name="configure-student-root-certificate"></a>配置学生根证书

在“学生根证书”下，选择浏览按钮以选择扩展名为 .cer（DER 或 Base64 编码）或 .P7B（不一定包含完整链路）的学生根证书。

#### <a name="configure-student-pkcs12-certificate"></a>配置学生 PKCS#12 证书

在“学生 PKCS#12 证书”下，配置下列值：

- **使用者名称格式** - 对于教师证书，Intune 将自动在证书公用名称上添加前缀“主持人”，对于学生证书则添加“成员”。
- **证书颁发机构** - 在 Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。 
- **证书颁发机构名称** - 输入你的证书颁发机构的名称。
- **证书模板名称** - 输入已添加到发证 CA 的证书模板的名称。 
- **续订阈值(%)** - 指定设备请求证书续订之前剩余的证书有效期限的百分比。
- **证书有效期** - 指定距离证书过期的剩余时间量。
你可以指定比指定证书模板中的有效期小的值，但不能指定较大的值。 例如，证书模板中的证书有效期为 2 年，则你可以指定值 1 年，但不能指定值 5 年。 该值还必须小于发证 CA 证书的剩余有效期。

完成证书配置后，选择“确定”。

## <a name="finish-up"></a>完成

1.    在“教育”边栏选项卡上，选择“确定”。
2.    在“创建配置文件”边栏选项卡上，选择“创建”。
    
将创建配置文件并在“配置文件列表”边栏选项卡上显示。

将该配置文件分配给与 Azure AD 同步学校数据时创建的教室组中的学生设备（请参阅[如何分配设备配置文件](device-profile-assign.md)）。

## <a name="next-steps"></a>后续步骤

现在，当教师使用 Classroom 应用时，将具有对学生设备的完全控制权限。

有关 Classroom 应用的详细信息，请参阅 Apple 网站上的 [Classroom 帮助](https://help.apple.com/classroom/ipad/2.0/)。

