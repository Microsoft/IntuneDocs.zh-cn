---
title: iOS Classroom 应用的 Intune 共享设备设置
titleSuffix: Microsoft Intune
description: 了解可用于控制 iOS 设备上 Classroom 应用设置的 Intune 设置。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86b61f628dc559bf0520dbe16ef58644bd360269
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188454"
---
# <a name="configure-intune-education-settings-for-shared-ipad-devices"></a>为共享 iPad 设备配置 Intune 教育设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

> [!NOTE]
> Intune 目前不支持配置教室应用。 文本仅适用于 Intune 中使用现有 iOS 教育版配置文件的用户。

Intune 支持 iOS Classroom 应用，可帮助教师在课堂上指导学习以及控制学生设备。 此外，对于 Classroom 应用，Apple 支持对学生 iPad 设备进行配置的功能，以便多名学生可以共享单台设备。 本文档指导如何通过 Intune 实现此目标。

有关配置专用 (1:1) iPad 设备以使用 Classroom 应用的信息，请参阅[如何为 iOS Classroom 应用配置 Intune 设置](education-settings-configure-ios.md)。

## <a name="before-you-start"></a>开始之前

使用共享 iPad 功能的先决条件是：

- 安装 [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md) 和[学校数据同步 (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617)。
- 作为 Apple School Manager 安装过程的一部分，为学生配置[托管 Apple ID](http://help.apple.com/schoolmanager/#/tes78b477c81)。 [了解有关托管 Apple ID 的详细信息](https://support.apple.com/HT205918)。
- 针对从 Apple School Manager 同步的设备序列号创建注册配置文件。

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>步骤 1 - 将学校数据导入 Azure Active Directory

使用 Microsoft 的学校数据同步 (SDS) 将现有学生信息系统 (SIS) 中的学校记录导入 Azure Active Directory (Azure AD)。
SDS 将同步 SIS 中的信息并将其存储在 Azure AD 中。 Azure AD 是帮助你组织用户和设备的 Microsoft 管理系统。 使用此数据有助于管理学生和班级。 [了解有关如何部署 SDS 的详细信息](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)。

### <a name="how-to-import-data-using-sds"></a>如何使用 SDS 导入数据

可以使用以下任一方法将信息导入 SDS：

- [CSV 文件](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) - 手动导出并编译逗号分隔值 (.csv) 文件
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) - 一个 SIS 提供程序，可以简化与 Azure AD 的同步操作
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) - 一种 CSV 格式，可以导出和转换以用于与 Azure AD 同步

### <a name="find-out-more"></a>查看详细信息

- [详细了解将本地学校数据同步到 Azure AD 的完整体验](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [详细了解 Microsoft 学校数据同步](https://sds.microsoft.com/)
- [详细了解 Azure Active Directory 中的授权](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)


## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>步骤 2 - 在 Intune 中创建和分配 iOS 教育配置文件

### <a name="configure-general-settings"></a>配置常规设置

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格上，选择“设备配置”   。
2. 在“管理”部分的“设备配置”窗格上，选择“配置文件”    。
5. 在“配置文件”窗格上，选择“创建配置文件”  。
6. 在“创建配置文件”窗格上，输入 iOS 教育配置文件的“名称”和“说明”    。
7. 在“平台”  下拉列表中，选择“iOS”  。
8. 在“配置文件类型”  下拉列表中，选择“教育”  。
9. 选择“设置”   > “配置”  。

接下来，需要使用证书在教师和学生 iPad 之间建立信任关系。 证书用于在无提示情况下对设备间的连接进行无缝式身份验证，而无需输入用户名和密码。

>[!Important]
>所使用的教师和学生证书必须由不同的证书颁发机构 (CA) 颁发。 必须创建两个新的连接到你的现有证书基础结构的从属 CA；一个用于教师，一个用于学生。

iOS 教育配置文件仅支持 PFX 证书。 不支持 SCEP 证书。

除用户身份验证以外，所创建的证书还必须支持服务器身份验证。

### <a name="configure-teacher-certificates"></a>配置教师证书

在“教育”  窗格上，选择“教师证书”  。

#### <a name="configure-teacher-root-certificate"></a>配置教师根证书

在“教师根证书”  下，选择浏览按钮以选择扩展名为 .cer（DER 或 Base64 编码）或 .P7B（不一定包含完整链路）的教师根证书。

#### <a name="configure-teacher-pkcs12-certificate"></a>配置教师 PKCS#12 证书

在“教师 PKCS#12 证书”  下，配置下列值：

- **使用者名称格式** - 对于教师证书，Intune 将自动在证书公用名称上添加前缀“主持人”  ，对于学生证书则添加“成员”  。
- **证书颁发机构** - 在 Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。
- **证书颁发机构名称** - 输入你的证书颁发机构的名称。
- **证书模板名称** - 输入已添加到发证 CA 的证书模板的名称。
- **续订阈值(%)** - 指定设备请求证书续订之前剩余的证书有效期限的百分比。
- **证书有效期** - 指定距离证书过期的剩余时间量。 你可以指定比指定证书模板中的有效期小的值，但不能指定较大的值。 例如，证书模板中的证书有效期为 2 年，则你可以指定值 1 年，但不能指定值 5 年。 该值还必须小于发证 CA 证书的剩余有效期。

完成教师证书配置后，选择“确定”  。

### <a name="configure-student-certificates"></a>配置学生证书

1. 在“教育”  窗格上，选择“学生证书”  。
2. 在“学生证书”  窗格的“学生设备证书类型”  列表中，选择“共享 iPad”  。

#### <a name="configure-student-root-certificate"></a>配置学生根证书

在“设备根证书”  下，选择浏览按钮以选择扩展名为 .cer（DER 或 Base64 编码）或 .P7B（不一定包含完整链路）的学生根证书。

#### <a name="configure-device-pkcs12-certificate"></a>配置设备 PKCS#12 证书

在“学生 PKCS#12 证书”  下，配置下列值：

- **使用者名称格式** - 对于教师证书，Intune 将自动在证书公用名称上添加前缀“主持人”，对于设备证书则添加“成员”。
- 证书颁发机构  - Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。
- **证书颁发机构名称** - 输入你的证书颁发机构的名称。
- **证书模板名称** - 输入已添加到发证 CA 的证书模板的名称。
- **续订阈值(%)** - 指定设备请求证书续订之前剩余的证书有效期限的百分比。
- **证书有效期** - 指定距离证书过期的剩余时间量。 你可以指定比指定证书模板中的有效期小的值，但不能指定较大的值。 例如，证书模板中的证书有效期为 2 年，则你可以指定值 1 年，但不能指定值 5 年。 该值还必须小于发证 CA 证书的剩余有效期。

完成证书配置后，选择“确定”  。

### <a name="complete-certificate-setup"></a>完成证书设置

1. 在“教育”  窗格上，选择“确定”  。
2. 在“创建配置文件”  窗格上，选择“创建”  。

配置文件随即创建并显示在“配置文件列表”窗格中。

## <a name="step-3---create-a-device-category"></a>步骤 3 - 创建设备类别

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”  窗格上，选择“设备注册”  。
4. 在“设备注册 - 概述”窗格中，选择“设备类别”   。
5. 在“设备注册 - 设备类别”  窗格上，选择“创建”  。
6. 在“创建设备类别”  窗格上，输入类别的“名称”  和“说明”  。
7. 在“创建设备类别”  窗格上，选择“创建”  。

设备类别创建在“注册 – 设备类别”  窗格中。

## <a name="step-4--create-a-dynamic-group"></a>步骤 4 – 创建动态组

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格上，选择“组”   。
4. 在“用户和组 - 所有组”  窗格上，选择“新建组”  。
5. 在“组”窗格上，选择“组类型”，然后输入组的“名称”和“说明”     。
6. 从“成员身份类型”  下拉列表中，选择“动态设备”  。
7. 选择“动态设备成员”  ，创建成员身份规则。
8. 在“动态成员身份规则”  窗格上：
1. 从“添加设备位置”  下拉列表中选择“deviceCategory”  。
2. 选择“等于”  。
3. 在空白的文本框中输入创建的设备类别。
9. 在“动态成员身份规则”  窗格上，选择“添加查询”  。
10. 在“组”  窗格上，选择“创建”  。

动态组创建在“用户和组 - 所有组”  窗格中。

## <a name="step-5--assign-a-device-to-a-category-carts"></a>步骤 5 - 将设备分配到类别 (Cart)

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格上，选择“设备”   。
4. 在“设备”窗格上，选择“所有设备”   。
5. 在“设备 - 所有设备”  窗格上，选择一台设备。
6. 在“设备”窗格上，选择“属性”  。
7. 访问设备的属性窗格，在“设备类别”  文本框中输入设备类别。
8. 在“设备”窗格上，选择“保存”  。

设备现已关联到设备类别。 请对所有希望关联到创建的设备类别的设备重复此过程。

## <a name="step-6--create-classroom-profiles"></a>步骤 6 – 创建 Classroom 配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格上，选择“设备配置”   。
4. 在“设备配置”  窗格上，选择“管理”   > “Cart 配置文件”  。
5. 在“配置文件”窗格上，选择“创建配置文件”  。
6. 在“创建关联”  窗格上，输入“名称”  和“说明”  。
7. 选择“选择类”   > “配置”  ，将组关联到 Cart 配置文件。
8. 选择要包括到 Cart 配置文件的类，然后选择“选择”  。 
9. 选择“选择 Cart”   > “配置”  ，将组关联到 Cart 配置文件。
10. 选择要包括到 Cart 配置文件的组，然后选择“选择”  。
11. 在“创建关联”  窗格上，选择“保存”  以保存 Cart 配置文件。

配置文件随即创建并显示在“配置文件列表”窗格中。

## <a name="step-7---assign-the-cart-profile-to-classes"></a>步骤 7 - 将 Cart 配置文件分配到类

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格上，选择“设备配置”   。
4. 在“设备配置”  窗格上，选择“监视”   > “分配状态”  。
5. 在“分配状态”  窗格上，选择所创建的“Cart 配置文件”  。
6. 在“Cart 配置文件”  窗格上，选择“分配”  ，然后在“包括”  下选中“选择要包括的组”  。
7. 选择希望作为 Cart 配置文件目标的类（请勿选择组），然后选择“选择”  。 
8. 完成后，请选择“保存”  。

分配完成，Intune 会基于教室分配将 Classroom 配置文件部署到目标设备。

## <a name="next-steps"></a>后续步骤

现在学生之间可以共享设备，并且可以在教室里拿起任何 iPad，使用 PIN 登录并根据自己的内容进行个性化设置。 有关共享 iPad 的详细信息，请参阅 [Apple 网站](https://www.apple.com/education/it/)。
